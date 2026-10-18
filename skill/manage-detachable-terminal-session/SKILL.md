---
name: manage-detachable-terminal-session
description: "Prepare or resume an identified tmux workspace so an authorized terminal task can continue while its client is detached, then return to the same work without restarting it. Use for session lifecycle and safe reattachment, not SSH provisioning, job scheduling, service supervision or reboot recovery."
---

# Manage a detachable terminal session

Give the user a named terminal workspace, a reliable way back to it, and an accurate account of what is still running. Detaching the display and completing the work are different outcomes. A session can remain available while its command has failed, and a command can finish while nobody is watching.

Use an already installed tmux on the intended Unix-like host. The [upstream getting-started guide](https://github.com/tmux/tmux/wiki/Getting-Started) describes its server, sessions, windows, panes and attached clients. This workflow manages those objects for one user and one bounded task. It does not turn a terminal job into an automatically restarted service, schedule recurring runs, preserve processes through host reboot, or recover an ordinary shell that already died before tmux was started.

Use [existing SSH connection](../connect-existing-ssh-session/SKILL.md) for the remote access prerequisite, [manual editor tasks](../configure-vscode-manual-tasks/SKILL.md) for a named editor launcher, and [terminal application development](../develop-terminal-application/SKILL.md) to implement an interactive program. Here the program already exists; the missing outcome is retaining and revisiting its terminal context.

## Establish the host, task and ending

Resolve only the inputs that affect the next action:

- Intended host and account, local or remote, installed tmux version, available terminal access and whether the current shell is already nested inside a multiplexer
- Existing server/socket choice and session to resume, or a unique name and working directory for a new workspace
- Approved command, inputs, outputs and side effects, if running a command is requested; an empty ready shell is also a valid deliverable
- Other clients or jobs to preserve, required observation level, and whether the user wants the session left attached, detached, or deliberately ended

Distinguish the terminal on the user's laptop from the machine that runs tmux. For a remote task, tmux must run on the intended remote host. A local multiplexer containing an SSH client does not by itself make the remote shell survive a broken SSH connection. Reconcile host/account context before sending a command.

Ask for an unknown target or ambiguous session. If the target computer, approved connection, tmux installation or interactive terminal is unavailable, deliver the scoped command plan and prerequisite instead of pretending to create a live workspace. Do not install tmux, add a new remote identity, switch accounts or use a different host as an incidental repair.

Permission to manage a session does not authorize its workload. Inspect the intended command and relevant startup behavior before execution; a script named check can still publish, install or overwrite. Obtain any separate authority its effects require. This workflow does not authorize network/security changes, socket sharing, elevated execution, credential retention or account provisioning. Keep secret values out of commands, screenshots, pane captures and the handoff.

## Inspect without disturbing existing work

Read the installed-version manual and relevant configuration as text before starting a new server. Configuration, sourced files, plugins, hooks and shell startup files can execute commands. Do not evaluate unfamiliar configuration merely to discover its effects. Preserve existing configuration and do not reload a global file into a running server for this task.

For an existing server, inspect only the selected user's relevant session/client metadata, using supported list and option commands. Do not capture every pane's contents or dump the full environment. Establish the effective prefix/detach binding and lifecycle settings. In particular, a nondefault destroy-unattached or exit-unattached policy can conflict with the requested persistence. Before creating a session on either a new or existing server, inspect effective default-command and default-shell: omitting a workload argument does not guarantee an idle shell if default-command starts a program. Confirm the selected shell's startup behavior is approved. Check hooks associated with creation, attachment and detachment before triggering those actions. If a managed policy prevents the desired lifecycle, report the conflict rather than bypassing it with a clean configuration or another socket.

The [tmux manual](https://man.openbsd.org/tmux.1) documents configuration loading, socket selection, command targets and lifecycle options. Use the installed version's behavior when it differs. Keep server identity in every later command: an approved -L socket name or -S socket path, if used, must also appear in the resume instructions. Do not change socket permissions, move socket files, or attach to another account's server.

Determine whether the requested session already exists. Use a selected server's list-sessions output and exact identity, not a fuzzy name or the most recently used session. If no server responds, distinguish absent server from wrong socket, account, host or inaccessible path before creating anything. Do not use a catch-all attach-or-create command for recovery: it can conceal a missing session by opening an empty replacement.

If another client is attached, identify whether it is the user's own intended client and whether shared interaction is authorized. An ordinary attach may expose and alter the same workspace. Hold an unexpected concurrent attachment; do not force-detach the other client or assume that a read-only view is safe to share. Preserve linked windows and unrelated sessions.

## Create or resume one deliberate workspace

These are schematic shell commands for later authorized use, not a script to run as a batch. Replace uppercase placeholders with reviewed values, quote them for the actual shell, and include the established socket selector where applicable. Use a simple unique session name without tmux target separators or shell metacharacters.

1. For a new workspace, use the installed version's new-session form, such as `tmux new-session -s SESSION_NAME -c WORK_DIRECTORY`, only after confirming its effective default-command/default-shell will start the intended approved shell. Otherwise hold creation or obtain authority for a supported session-scoped invocation; do not rewrite shared defaults. Create one shell first; do not append a workload to creation until its effects and startup context are understood. If creation reports a collision, inspect it rather than killing or replacing the existing session.
2. For resuming, use `tmux attach-session -t '=SESSION_NAME'` after confirming that exact existing name. The equals prefix requires an exact target match. Do not add -d to evict another client or use an untargeted attach.
3. Observe the actual session, active pane and prompt. Establish the expected working directory and required non-secret runtime selection inside the pane. An existing session may retain an old shell environment; reattachment is not a fresh login or proof that a recently changed runtime is active. Do not globally replace tmux's environment to fix one job.
4. If the user requested a workload, inspect its input/output contract and current output state, then invoke it once in the confirmed pane. Prefer direct deliberate terminal input to automated send-keys into an unknown foreground application. Before any Enter or control key, verify which program owns the input.

Use a single pane unless more are useful. If additional windows or splits are requested, give each a purpose and preserve stable pane/window identities for subsequent actions. A window title, pane position or selected tab can change. Never synchronize input across panes for this workflow, and do not link an unrelated existing window into the new workspace.

Leave application logs where the application's approved contract puts them. tmux scrollback is not a durable run record or proof of exit status. If completion evidence matters, decide an approved log/result location before the run without silently redirecting over an existing file or enabling full-session logging that could capture secrets. Do not wrap the workload in automatic retries or relaunch it because output has stopped moving.

## Detach and return to the same work

Before detaching, record the host/account reference, server selector, exact session name and useful pane identity without private output. Note whether the workload is still running, finished, failed or unknown based on actual evidence. Establish that the effective lifecycle configuration will retain this session when its last client detaches.

Use the verified detach binding. With the default binding, press Ctrl-b, release it, then d. Check the return to the known outer shell and the reported detached session; do not confuse exiting a shell with detaching a client. Do not send exit, Ctrl-c or a terminal-close operation to an unknown foreground program to simulate detachment.

For a remote workspace, an approved SSH exit can follow only after the tmux client has detached and the outer remote shell is identified. Leave unrelated connections alone. Do not test by disrupting the machine's network, suspending the host or forcibly closing transport. Host sleep, logout policies, quotas and server shutdown can still prevent progress; explain relevant known limits instead of promising uninterrupted execution.

When a detach/reattach check is authorized, return through the same host, account and server selector and attach to the exact existing session. Compare the recorded session/pane identity and retained task context. An unchanged title alone is insufficient. For a ready-shell task, retained working directory and a harmless agreed shell-local marker can demonstrate continuity; no long-running synthetic job is required. For real work, inspect its approved status/result rather than restarting it for a prettier demonstration.

A session visible in list-sessions establishes existence, not task completion. A prompt after a command may establish that control returned, not that its output is correct. Record the command's actual completion evidence and inspect the expected artifact when that is in scope. If the task's result was not observed, retain unknown status.

## End or recover without destroying the wrong work

If the requested ending is detached, leave it detached and give the exact resume route. Do not kill it as cleanup. If termination was requested, first reconcile every affected pane, active job, unsaved editor and linked window. Use the application's supported save/finish/quit sequence before exiting its shell. A session-level termination can destroy multiple panes; require scope and authority for those effects. Never use kill-server to close one task.

Handle a failure at its actual boundary:

- **No session found:** check the recorded host, account and socket once through the authorized route. Do not create a same-named substitute or rerun a possibly completed command. If the server truly ended, report terminal continuity lost and inspect preserved outputs before considering a restart
- **Disconnected during launch:** recover observation first. The command may already have started; lack of client feedback is not permission for a second invocation
- **Session exists but the job failed:** retain diagnostics and partial output; repair or retry only under the workload's own permitted recovery contract
- **Detach would destroy the session:** keep the current client attached while explaining the policy conflict. A scoped settings change needs its own authority; do not change a shared server for convenience
- **Input or display is confusing:** stop typing, identify nesting and active program using safe observations, and use verified bindings. Do not blast reset, interrupts or exit into an unknown pane
- **Socket missing or permission denied:** preserve the evidence and ask the owner for the supported recovery route. Do not delete sockets, send signals to guessed processes, weaken permissions or restart a shared server

Session termination is not rollback of a workload's files, messages or remote effects. Reversal of those effects is separate work. Stop at a precise blocker when identity, authority or saved-state evidence is missing.

## Deliver and accept

Return a short private handoff: host/account by safe reference, tmux version, server selector, exact session name, active work and its evidenced status, requested ending, resume/detach instructions, output locations when approved, and any limitations. Distinguish prepared only, created, attached, detached, reattached to the same work, and intentionally ended.

Acceptance requires the intended host and user-owned session, preserved unrelated work and configuration, no duplicate workload launch, correct input destination and the agreed final client/session state. Claim continuity checked only when the same workspace was actually revisited. Claim job completion only from its result evidence. A prepared note or static command review establishes neither.

## Fictional, unexecuted illustration

A fictional user has an installed tmux on an already authorized development host. They want a workspace named draft-review, in a directory called /home/example/draft, left detached so they can return later. They have not requested any build or conversion command.

The proposed workflow would inspect the existing server's relevant configuration, confirm the name is unused, create one shell in the specified directory, and check its context. If a continuity check is allowed, a harmless agreed shell-local marker would be set, the client detached, and the exact session reattached to inspect the retained marker and directory. The client would then be detached again. No workload would be invented to prove usefulness.

If inspection instead found draft-review already attached to an unexpected client, creation or takeover would be held for clarification. If the exact session disappeared after detachment, the handoff would report continuity unverified or lost, rather than create a new draft-review and call that recovery.

This illustration is original, fictional and unexecuted. No host was contacted, session created, configuration changed, process launched, client detached or persistence tested for it. The commands and checks above describe later authorized use.
