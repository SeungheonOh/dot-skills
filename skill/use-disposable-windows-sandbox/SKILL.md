---
name: use-disposable-windows-sandbox
description: "Prepare and use one disposable Windows Sandbox session for an approved ordinary application activity, with explicit host access, a verified output route and deliberate disposal. Use for temporary clean desktop work, not a persistent VM, development container, malware analysis or a guarantee that downloaded software is safe."
---

# Complete temporary Windows work without losing the result

Deliver one bounded clean-desktop session, its meaningful activity result and an honest record of what was retained outside it. The central decision is what may cross the host/session boundary and what must be saved before the session ends. A window opening is not the completed task, and closing it is not a rollback of everything done during the session.

Keep this workflow to Windows Sandbox on a supported, already prepared Windows computer. It does not enable virtualization, install the optional Windows feature, change firmware, enroll an Insider build, analyze malware, disable protections or execute an unknown attachment. Missing host prerequisites produce a preparation handoff. A separate authorized setup can establish them before returning here.

[Create a local virtual machine](../create-local-virtual-machine/SKILL.md) when the guest operating system, installed applications and guest files must survive closing and restarting the machine. [Configure a development container](../configure-development-container/SKILL.md) for a project's repeatable toolchain and workspace lifecycle. [Install a desktop application](../install-desktop-application/SKILL.md) for a durable host installation. This workflow instead produces a deliberately temporary Windows activity and, where requested, a narrow retained result.

## Establish the session contract

Resolve the following from the request and available native state; ask only for missing choices that affect execution or retention:

- The selected computer, Windows edition/build, architecture and existing Sandbox availability
- One ordinary activity, its expected result and whether the request authorizes actual execution or only preparation
- Exact application/source/version and approved sample inputs; distinguish publisher-provided software from unverified binaries
- Whether networking is needed, which destinations are necessary and whether an entirely offline activity is feasible
- Host data and devices that the activity requires, including any output destination that must survive closing
- Existing Sandbox work, host work that must remain uninterrupted and an agreed final state: session left open or disposed

Do not create an interview for a simple offline preview. A named reputable application, synthetic input, no host integration and a visual result may be enough. Conversely, “try this in a sandbox” does not establish permission to execute unrecognized software, access private files or accept a license.

Microsoft's [Sandbox overview](https://learn.microsoft.com/en-us/windows/security/application-security/application-isolation/windows-sandbox/) describes a disposable environment: closing removes its internal software, files and state, while a restart inside supported recent versions can preserve the current session. It also says host applications are not automatically installed inside, only one instance can run at once, and Windows Home is unsupported. Establish the actual version rather than interpreting every restart as a fresh environment or assuming an installed host editor will be available.

## 1. Check readiness without altering the host

Inspect the relevant installed feature and existing running session through native controls. Do not launch a default session just to see whether the feature exists: first settle the access configuration below. If a session is already open, ask whether it belongs to this task and contains work. Never close another session to free the single-instance slot.

Consult the current [installation prerequisites](https://learn.microsoft.com/en-us/windows/security/application-security/application-isolation/windows-sandbox/windows-sandbox-install) for the actual host. Microsoft lists supported architecture, enabled virtualization and minimum memory, disk and CPU resources. A computer meeting a published minimum may still lack capacity for the requested app alongside current host work. Identify resource constraints without terminating other workloads or cleaning unrelated storage.

The installation page currently notes missing inbox Store apps in Sandbox beginning with Windows 11 24H2. Check the actual session's available tools before promising a Notepad-based acceptance test. If an additional viewer or editor is required, name its official source and installation requirement instead of silently fetching a substitute.

When readiness is absent, return the precise prerequisite and the selected activity/configuration plan. Do not run feature-enablement commands, alter BIOS/UEFI, enable nested virtualization, change host virtualization services or join a preview channel as recovery. Such host changes have their own authorization, restart and recovery requirements. If readiness is uncertain because access is unavailable, label it unverified rather than unsupported.

## 2. Design the host boundary before opening the session

Make a short access plan tied to the activity. Prefer no network, no device input, no shared clipboard and no host-folder mapping when they are unnecessary. Where input is required, stage only the approved copies in a dedicated folder; do not map Downloads, the home directory, a source checkout with credentials or a whole drive for convenience. Inspect that folder's actual contents and location, including whether it is synced, before approving exposure.

Microsoft's [configuration reference](https://learn.microsoft.com/en-us/windows/security/application-security/application-isolation/windows-sandbox/windows-sandbox-configure-using-wsb-file) documents XML `.wsb` launch files. Its default launch enables networking, microphone input and clipboard sharing. Mappings require existing host folders; their read-only setting defaults to false, and writable mapped changes survive disposal. Treat these defaults as reasons to inspect explicit configuration, not as a protection guarantee.

Choose the smallest meaningful transfer design:

| Activity | Proposed arrangement | Retention decision |
| --- | --- | --- |
| Observe an app using synthetic guest-local work | No mapping; approved installation route only | Record the observation outside the session; no file export required |
| Read an approved host sample | Dedicated input-only mapping, explicitly read-only | Original remains on the host; guest-created results remain temporary |
| Produce a file that must survive | Separate input and narrowly scoped writable output location | Verify the host copy before considering disposal |
| Work requires accounts, live services or broad host integration | Resolve exact access and purpose first | Do not treat disposable local state as reversing external actions |

A writable output location is a host-write capability, not a harmless “save” convenience. Keep it initially empty or verify every existing item that must be protected. Do not reuse an important output directory whose contents an application might replace. Read-only input still exposes its contents to the guest; it is not a confidentiality boundary. If network access is also allowed, consider the approved input's transmission requirements before loading it.

Obtain required action-time approval before changing security-sensitive network or host-integration configuration. Resolve file-sharing authority for exact paths and read/write scope. Device access, persistent grants, sign-in, purchases and new terms remain separate boundaries. Protected credential entry belongs in the supported owner-controlled flow; never put credentials in a launch file, command, clipboard or report.

For a simple offline session, specify explicit disabled values for `Networking`, `ClipboardRedirection`, `AudioInput`, `VideoInput`, `PrinterRedirection` and `vGPU`. Consider supported `ProtectedClient` behavior against the transfer requirement; do not turn it off automatically when a transfer fails. Omit automatic logon commands. The configuration reference documents these controls and notes that Protected Client can restrict file copy/paste. Any required exception needs a reason and authorization before launch.

## 3. Prepare and inspect the exact launch file

Use a plain-text editor to create a uniquely named `.wsb` file at an approved host location. Do not overwrite an existing configuration. Use the documented `Configuration` root and current documented element/value spellings; supply only settings supported by the selected Windows version. Keep the file free of secrets, startup scripts and unexplained copied configuration.

Where mappings are necessary, use fully resolved absolute host and guest paths, explicit read/write mode and separate input/output destinations. Microsoft's [sample configurations](https://learn.microsoft.com/en-us/windows/security/application-security/application-isolation/windows-sandbox/windows-sandbox-sample-configuration) illustrate mapping structure and differing read-only modes; adapt only the required fields, not their automatic execution or broad example folders. Escape XML-sensitive characters correctly. Check the real file extension so a hidden `.txt` suffix does not leave a text document masquerading as a launch file. Read the saved bytes back and compare them with the agreed access plan. Preparation means this configuration was reviewed; it does not establish that Windows applied it.

Treat an existing third-party `.wsb` file as actionable configuration, not as a passive document. Inspect every mapping and startup action before opening it. A friendly filename or a clean-looking desktop cannot establish what a logon command executed or which host folders were exposed. Do not approve execution merely because the file is text or came with documentation.

When actual session use is authorized and required approvals are in place, launch this exact reviewed file through its supported native open action. Do not substitute the generic Start-menu shortcut, which may use different settings. Record which configuration and computer launched the session. After a tool disconnect or ambiguous response, inspect the existing session before retrying; never dispose it to make the next attempt look clean.

## 4. Perform only the approved activity inside the guest

Before running the selected app, establish which visible window is the Sandbox and which controls belong to the host. Keep the environment distinguishable while moving files or accepting dialogs. An installer selected in host File Explorer is not automatically running in the guest. Match the approved artifact, location and publisher before execution and resolve any unexpected host elevation prompt rather than approving it.

Use the same source and installation boundaries as an ordinary application task. A sandbox does not waive the action-time requirement for software from an unrecognized source. It does not authorize disabling reputation checks, bypassing a security warning or opening a suspicious attachment. Stay with the ordinary, previously selected activity; security testing and malware handling are outside this guide.

Check the requested boundary before loading private input or doing meaningful work. Inspect the selected mappings and relevant available native state. If the requested disabled network or integration behavior cannot be established, leave that part unverified and hold dependent activity. Do not probe private hosts, upload a sample, install a packet capture tool or exercise a hostile file to demonstrate isolation. Configuration review and narrow observations are not proof against escape or compromise.

Run the agreed harmless activity with approved data. Record the app's actual version and the result that matters: a rendered page, an exported sample, an opened supported file or another bounded output. Separate application readiness from functional success. If a required component is absent, decide whether an authorized official installation fits the existing access plan; do not enable networking or widen mappings without resolving that new boundary.

If an installer requires a guest restart, establish current support and preserve the activity's state before using that route. Do not replace an in-guest restart with closing the Sandbox window. If closing is necessary, treat it as disposal and follow the retention gate below. Do not promise the environment can be restored from its launch file: the file defines configuration, not a backup of installed software or unsaved work.

## 5. Retain the result before deciding to close

Classify the useful result while the session is still observable:

1. **Observation only:** capture a concise factual result through the existing authorized observation route, avoiding secrets and unrelated screen contents
2. **Guest-local file:** identify the exact file and size/content expectation; it remains at risk until an approved host-side copy is verified
3. **Writable mapped output:** inspect the corresponding host location directly; a guest save dialog alone does not prove the intended retained result
4. **External action or data:** record its actual service-side state separately; closing the local session cannot be used as an undo plan

For a retained file, verify its host path, identity, completeness and intended format using a safe read method. Do not execute an exported application or enable macros merely to check that it exists. Preserve provenance: a file produced in a temporary environment is still subject to normal content-safety review. Do not mark an export “clean” because Sandbox created it.

If no approved export path exists, keep the session open and report the exact retention decision needed. Do not improvise email, cloud upload, clipboard sharing or a broad writable map. Editing a launch file is not evidence that the current running session acquired the new setting. Do not close to relaunch with a new output path while the only useful copy remains inside.

Once retention is established, ask for action-time confirmation immediately before disposal because closing permanently removes the remaining internal state. Identify the session, what has been preserved and what will be lost. A general request to use a disposable environment is not a substitute for this final check. If the user chooses to leave it open, report that state and the remaining loss risk without silently scheduling closure.

Use the native close/discard flow only after confirmation, then observe that the session ended. Do not force-kill it as routine cleanup. Keep the launch file, approved inputs and retained outputs unless their deletion is separately authorized. Do not disable the host feature to “undo” the session.

## Recover at the actual failed stage

- **Feature unavailable or host unsupported:** return readiness evidence and the exact prerequisite; do not install unofficial enablement scripts
- **Configuration rejected:** preserve the candidate, inspect documented syntax and version support, and correct only the evidenced issue. Do not fall back to default settings to obtain a launch
- **Mapping missing:** verify the exact existing path and permission; do not map its parent or grant broader host rights
- **Application fails under restricted access:** identify the missing dependency. Offer an explicitly scoped exception or retain the limitation; do not silently relax protections
- **Session response lost:** regain observation through the already authorized route before a destructive decision; a timeout does not establish disposal
- **Output cannot leave:** keep the guest alive if possible, name the missing approved transfer capability and avoid further changes that risk its only copy
- **Session already closed:** inspect only previously approved retained destinations. Do not claim that rerunning the activity recovers the same unsaved result
- **Unexpected host or service change:** stop affected activity, preserve evidence and report the exact change; disposal is not a rollback for exposed resources

Retry only after an evidenced correction within scope. Stop at an unsupported prerequisite, a new authority boundary or a terminal failure without a safe correction. A failure to verify the boundary is a reason to stop dependent work, not a reason to promise that all isolation is intact.

## Deliver and accept the bounded result

Return the selected computer and version, reviewed launch-file location, app/activity, relevant access settings, retained output location and actual final session state. Distinguish configuration inspection, observed launch, activity completion, verified host retention and observed disposal. Record user-performed steps separately from directly observed ones. Leave unavailable evidence visible.

Completion requires the approved activity or an explicit blocked-stage report, preservation of required outputs, and the user's requested ending with the appropriate disposal decision. A configured file alone supports “prepared”; a running desktop supports “launched”; a saved host result supports “retained.” None establishes that arbitrary software is safe, that the host is unaffected in every respect or that all remote actions were reversed.

## Fictional, unexecuted illustration

A fictional user wants to inspect a reputable document converter's export behavior in a temporary Windows session using a synthetic sample. The host feature is already ready. The proposed launch uses a dedicated read-only input folder and a separate empty output folder with the specifically approved write scope. The input folder contains no personal files, and the activity requires no network access.

An invented intermediate observation says the app wrote a report under its guest-local Documents folder rather than the mapped output folder. The workflow would keep the session open, locate the exact report, use only the already approved output path and inspect the retained host file. It would not close because the app displayed “Export complete.” If no permitted transfer route worked, retention would remain blocked.

After the fictional host copy was verified, the operator would ask before discarding the remaining session. Any writes to the mapped output would remain and would not be described as rolled back. The result would distinguish the tested conversion from any untested installation or security claims.

This is an original paper walkthrough, not a performed trial. No feature, session, application, configuration, mapping, network setting, account, transfer or disposal was operated for this illustration. All operational steps above are for later authorized work.
