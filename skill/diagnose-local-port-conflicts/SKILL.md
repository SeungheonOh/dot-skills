---
name: diagnose-local-port-conflicts
description: "Diagnose local address-in-use and wrong-service problems by identifying the exact socket, process instance, network context, and authorized recovery path before stopping services or changing ports."
---

# Diagnose Local Port Conflicts

## Trigger and scope

Use this skill when a development server cannot bind its local endpoint, a local
port appears occupied, or a request reaches a different local application.
Return an evidence-backed diagnosis and, when authorized, a scoped recovery
with the original failing action checked again.

Do not treat every connection refusal, timeout, DNS error, or HTTP failure as a
port collision. Remote availability, firewall administration, and broad network
scanning are separate tasks. Begin with the failing operation and its endpoint.

## Required inputs

- Exact error, timestamp with timezone, launch command, and relevant startup log
- Intended transport, local address, port, and address family, if configured
- Where the application runs and where the client runs: host, container, VM,
  WSL distribution, remote development host, or forwarded local browser
- Expected application identity and the documented way it is started or stopped
- Whether the request permits inspection only, restarting a named development
  service, or changing this application's local configuration

Read logs and configuration before asking. Clarify uncertainty that changes the
target machine, disruption risk, or permitted recovery. Preserve unknown values;
do not substitute the assistant's environment for the user's.

## Execution workflow

### 1. Classify the operation before inspecting ports

Write the failing operation as `bind/listen`, `connect`, or `unknown`, with both
local and remote endpoints when relevant. A remote destination port in a client
error is not evidence that a local server owns that port.

For a bind failure, distinguish address-in-use from an unavailable local address
and insufficient permission. For a connect failure, inspect the destination and
any explicitly bound source address. On Linux, automatic ephemeral-port
allocation can fail during connect; binding port zero can also exhaust available
ephemeral ports. Those cases need allocation evidence, not an arbitrary process
termination. Consult the platform's error definitions rather than interpreting
an errno without its operation. See [bind(2)](https://man7.org/linux/man-pages/man2/bind.2.html)
and [connect(2)](https://man7.org/linux/man-pages/man2/connect.2.html).

Record whether an application silently retried a different port. A successful
startup message on another port does not resolve the original endpoint contract.

### 2. Locate the network context

Draw only the relevant path, such as browser on host → host published port →
container port. Name each machine or namespace explicitly. The same numeric
port in different network namespaces is not by itself a collision.

Inspect the relevant host publication and the application-side listener
separately. A container's internal port can be free while its requested host
mapping conflicts. Conversely, changing the internal port need not release the
host port. Record the actual configured mapping, container identity, and runtime
context; do not assume the current runtime client targets the local machine.
Docker's [port-publishing documentation](https://docs.docker.com/engine/network/port-publishing/)
explains host-to-container mappings and host-address exposure.

Do not enter another VM, namespace, or remote host merely because it might help.
Use an already authorized environment or report the precise missing visibility.

### 3. Capture socket ownership without changing it

Use an installed read-only tool appropriate to that context. Replace example
port `4317` with the observed target. These examples do not authorize launching
the application or installing tools.

- Linux TCP: `ss -ltnp 'sport = :4317'`; retain the local endpoint and process
  information. If family matters, inspect with `-4` and `-6` separately
- Linux UDP: `ss -uanp 'sport = :4317'`; inspect bound endpoints rather than
  demanding a TCP `LISTEN` state. Options are documented in [ss(8)](https://man7.org/linux/man-pages/man8/ss.8.html)
- macOS with lsof: `lsof -nP -iTCP:4317 -sTCP:LISTEN`; for UDP use
  `lsof -nP -iUDP:4317` and inspect the local endpoint. `-nP` preserves numeric
  addresses and ports. See the [upstream lsof manual](https://github.com/lsof-org/lsof/blob/master/Lsof.8)
- Windows PowerShell: `Get-NetTCPConnection -LocalPort 4317 -State Listen`
  exposes matching TCP records; retain `LocalAddress`, `LocalPort`, `State`,
  and `OwningProcess`. Use `Get-NetUDPEndpoint -LocalPort 4317` for UDP.
  See [TCP connection inspection](https://learn.microsoft.com/en-us/powershell/module/nettcpip/get-nettcpconnection)
  and [UDP endpoint inspection](https://learn.microsoft.com/en-us/powershell/module/nettcpip/get-netudpendpoint)

Build one record per relevant socket, not just a list of process names:
```text
observed_at_and_timezone:
machine_runtime_and_network_context:
transport_and_address_family:
local_address_and_port:
socket_state:
pid_and_process_start_time:
executable_path_and_owner:
parent_or_supervisor_identity:
application_or_project_identity:
evidence_source_and_visibility_limits:
```

Resolve each PID immediately to its process instance; replace example PID 2814
below with the freshly observed PID. On Linux,
`ps -p 2814 -o pid,ppid,lstart,comm` supplies process and start-time fields;
the `/proc/2814/exe` link can identify its executable when readable. A short
command name is not the executable path. See [ps(1)](https://man7.org/linux/man-pages/man1/ps.1.html)
and [proc_pid_exe(5)](https://man7.org/linux/man-pages/man5/proc_pid_exe.5.html).
On Windows, inspect the observed PID with `Get-Process -Id 2814` and retain its
`StartTime` and `Path` properties when accessible; see [Get-Process](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-process).
On other systems, use their process inspector and document unavailable fields.

Do not dump complete process environments or unrelated command lines. Arguments
can contain credentials; retain only the project-identifying portion needed.
An inaccessible owner field means ownership is unverified, not that no owner
exists. Keep socket and process observations timestamped because they can race.

### 4. Decide whether the endpoints actually overlap

Compare transport, network context, family, address, and port together:
- TCP and UDP are different transports; the same number alone proves nothing
- `127.0.0.1` and `::1` are loopback addresses for different address families
- `0.0.0.0` is an IPv4 bind wildcard; a wildcard listener may overlap a specific
  local IPv4 address. It is not a client URL to recommend. See [ip(7)](https://man7.org/linux/man-pages/man7/ip.7.html)
- An IPv6 wildcard socket's interaction with IPv4 depends on platform and
  socket configuration. Inspect rather than assuming IPv6-only behavior;
  Linux documents the relevant option in [IPV6_V6ONLY](https://man7.org/linux/man-pages/man2/IPV6_V6ONLY.2const.html)
- `localhost` is a name. Record the actual address the failing client selected
- A connection to the wrong application requires application-identity evidence,
  not merely a successful TCP handshake or HTTP status

If no listener appears, inspect other relevant socket states and bound-but-not-
listening sockets with tools supported by the installed platform. A snapshot
with no matches is not a reservation or proof that the next bind will succeed.
Check for short-lived owners, a different context, incomplete visibility, and
the exact failed address. Do not label `TIME_WAIT` as a running listener to kill
or tune reuse settings without evidence of the application's binding behavior.

### 5. Identify the lifecycle owner and choose a recovery

Map the process to its terminal session, development watcher, service manager,
container, or VM launcher. A replacement PID with a later start time can indicate
supervised restart; do not chase it with repeated termination attempts.
Socket activation can also make the manager own a socket passed to a service.
Inspect the specific socket/service relationship; see [systemd socket documentation](https://github.com/systemd/systemd/blob/main/man/systemd.socket.xml).

Choose the least disruptive option supported by the evidence:
1. Reuse the existing instance if its project, revision, configuration, and
   readiness match the user's intended application
2. Stop an authorized obsolete instance through its documented lifecycle owner,
   accounting for a watcher, restart policy, or activation socket
3. Change only the requested application's local port when that change is
   permitted; identify affected client URLs, callbacks, proxy targets, and tests
4. Leave an unrelated or shared owner running and request a scope decision

Before a stop, re-read the socket and process start time, executable, and
supervisor. A PID may have been reused. If identity changed or cannot be
established, discard the earlier stop target and investigate again. Sequential
reads reduce stale-target risk but are not an atomic identity guarantee.

For a port change, preserve the intended interface and exposure. Moving from
loopback to a wildcard address is a security-relevant change, not a routine fix.
Record the exact old value and rollback before editing. Check an alternative
endpoint close to startup, but recognize that only the application's successful
bind establishes ownership; a separate probe cannot reserve it for later use.

## Permission boundaries

- Inspection does not authorize stopping an unrelated process, restarting a
  shared service, changing a system setting, or launching repository code
- Act within existing authorization for the named application and environment;
  ask about a new target or disruption instead of duplicating valid approval
- Never use broad process-name kills, kill-all commands, or automatic
  listener-to-termination pipelines. Do not default to forced termination
- A graceful stop may still lose work or interrupt clients. Name those effects
  when requesting missing authorization and stop only the verified instance
- Do not change firewall rules, security software, OS port reservations,
  privilege settings, or socket-reuse policy to make a diagnostic check pass
- Do not elevate privileges, bypass denied access, install a utility, or disable
  a supervisor without the permission that action requires

## Verification

When permitted, repeat the original launch or client action in the same context.
Capture fresh evidence; otherwise deliver these checks unrun.

- The intended application owns the intended transport/address/port, with a
  fresh PID/start-time identity or a verified lifecycle-manager relationship
- Startup no longer reports the original bind failure or silently selects an
  unintended endpoint
- A documented non-mutating readiness check reaches the intended application
  from the actual client context; do not send credentials to an unknown owner
- The observed bind address preserves the approved exposure
- The application remains ready through its documented startup/watch cycle;
  choose the observation window from that lifecycle rather than an arbitrary wait
- Any affected local client configuration works, and unrelated owners remain
  running when preservation was part of the recovery

If only a socket check was possible, report socket ownership as verified and
application behavior as unchecked. Do not claim the fix survived a restart that
was not performed.

## Deliverables

Return the classified failure, exact endpoint/context, timestamped ownership
record, confidence and gaps, chosen recovery with its authorization, and before/
after evidence. Include changed local values and rollback if applicable.
Separate observed results, proposed actions, and unrun checks. End with the
smallest remaining decision or an evidence-supported completion statement.

## Failure handling

- Tool unavailable: use an installed read-only equivalent; otherwise request
  the specific socket/process output needed without claiming ownership
- Access denied: preserve partial evidence and identify the blocked field or
  context. Do not work around a denied boundary
- Owner disappears or restarts: refresh the whole identity record; investigate
  supervision before any further mutation
- Approved recovery fails: retain its result, stop repeating it blindly, and
  inspect the new error. Roll back only within the authorized recovery plan
- No collision established: report that finding and route the actual symptom,
  such as unavailable bind address or wrong client destination, to its next check

## Original fictional worked example, authored and unexecuted

This example was written for this skill. All names, times, PIDs, observations,
and outcomes below are invented; no commands or application tests were run.

Scenario: Mira's Lantern preview cannot bind `127.0.0.1:4317` on her Linux
laptop. She permits inspection and changing Lantern's temporary local port,
but wants her inventory demo container left running.

The fictional evidence record shows TCP/IPv4 `0.0.0.0:4317` at 09:20 UTC,
PID 2814, start time 08:55 UTC, executable `/usr/bin/docker-proxy`. The verified
runtime mapping connects host port 4317 to inventory container port 8080.
Lantern runs on the host; checking port 4317 inside the inventory container
would answer the wrong question. The wildcard host binding overlaps Lantern's
requested IPv4 loopback endpoint.

Proposed recovery: leave the inventory owner untouched, preserve Lantern's
loopback binding, and choose an available alternative such as 4318 after a
fresh inspection. Update its temporary launch configuration and local preview
URL together; restore those two values if recovery fails. Do not broaden the
binding, change Docker's publication, or terminate PID 2814.

Expected verification, still unrun: Lantern owns `127.0.0.1:4318`, its known
readiness response identifies Lantern, the preview opens through the new URL,
and the inventory mapping remains unchanged. The proper report is a supported
diagnosis plus an authorized recovery plan, not a claim that the recovery worked.
