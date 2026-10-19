---
name: recover-unresponsive-desktop-app
description: "Recover use of one unresponsive desktop application through state preservation, exact process identification, a scoped normal or approved forced exit, and a safe reopening check. Distinguish restored responsiveness from recovered work or a fixed underlying fault."
---

# Recover use of a frozen desktop application

Use when one existing macOS or Windows desktop app no longer responds and the user wants to resume work. Deliver a usable application session and an honest account of work preserved, recovered or still uncertain, or a precise blocker that leaves the remaining state intact.

This is immediate session recovery, not a performance optimization, forensic investigation or software repair. It excludes system-wide freezes, operating-system services, installers, firmware operations, disk repair, security software and processes owned by another user. A frozen browser tab should use its browser's supported tab-specific recovery rather than terminating every browser window. Do not turn this into a reboot, reset, reinstall or broad process-killing recipe.

For retrieving document contents from recovery candidates, use [recover unsaved editor work](../recover-unsaved-editor-work/SKILL.md). For a repeatable correctness investigation after the session is safe, use [bug reproduction triage](../bug-reproduction-triage/SKILL.md). Neither an application reopening nor a recovered draft establishes that the original fault is repaired.

## Establish the target and what could be lost

Inspect available state and ask only for consequential unknowns:

- Exact computer, OS, app and existing installation; local, virtual-machine or remote session
- Affected window and account/workspace, whether other windows in the same app respond, and whether the rest of the desktop responds
- Last action and elapsed time, visible progress or a pending dialog, and whether the symptom is directly observed or user-reported
- Unsaved work, background exports, uploads, calls, database writes or other tasks owned by this app
- Existing saved copy or recovery state, without assuming autosave covers the latest work
- Whether the request permits a normal close/reopen, a forced termination accepting specified loss, or inspection only
- A permitted local destination if preserving a copy is possible, and an observable safe action that would demonstrate a usable session

Identify the user-visible goal: opening a saved project, returning to a selected document, or accessing an app's ordinary workspace. “The process disappeared” is not enough. Do not demand an elaborate incident form before preserving a live buffer.

Computer access must be through an actually available authorized route. Do not substitute an action on another machine. If this app supplies the sole remote-control connection or necessary assistive interface, stop before closing it and obtain a supported recovery route. A planned reconnection is not evidence that it will work.

## 1. Separate a hang from a blocked or busy interface

Observe before sending more input. Repeated clicks, shortcuts and launches can queue duplicate work that executes if the app recovers.

1. Confirm the intended window is active and inspect existing window previews or the app's window list for a modal dialog. An obscured Save, login or file-picker dialog can block its parent window. Bring a confirmed dialog into view without accepting, dismissing or submitting it blindly.
2. Check whether the desktop and another already-open ordinary app respond. Do not create new work solely to test this. If the whole session is inaccessible, report the wider failure boundary rather than applying a one-app procedure.
3. Look for meaningful progress: an increasing completed-item count, a changing export indicator or the app's documented operation status. Resource use is supporting context, not proof that useful work is progressing or safe to interrupt. High CPU alone does not diagnose a hang; low CPU alone does not prove inactivity.
4. If an operation is progressing, preserve it and wait according to that operation and the user's needs. If status is static, use a reasonable observation interval grounded in the task and report uncertainty; there is no universal delay that proves a deadlock. Do not interrupt an update or storage operation under this guide.
5. If a responsive app-owned cancel command is available, determine what it cancels and whether cancellation is within scope. Cancel one operation only when its consequences are understood. Do not treat Escape or closing a dialog as a harmless diagnostic when it could discard input.

If resolving a pending dialog restores control, verify the intended work and stop. A forced exit is not required to complete this skill. If work recovers spontaneously, preserve it promptly rather than reproducing the hang.

## 2. Preserve reachable work and identify the closure scope

Save reachable work through a supported non-overwriting route before closing anything. Prefer a separate native-format copy when the original must be retained. Confirm its actual location and content; a disabled save control or an attempted shortcut is not evidence of preservation. Do not copy a live application database and call it a consistent backup.

For an inaccessible buffer, state that preservation is unavailable. Do not promise that autosave, a temporary file or reopening will recover it. Avoid debugger attachment, process memory dumps and broad diagnostic bundles: these can expose document content, credentials and unrelated activity and are not needed for this workflow.

Inspect the native process view only to resolve the exact target and closure impact. Match the application/window, current user, installation identity and relevant process instance where available. A familiar name, icon or historical process ID is insufficient. Distinguish the main application from helpers and shared services. A group can contain several windows or tasks; closing that group may affect all of them.

Preserve a small private record: app/window identity, unsaved-work status, known background tasks, time and proposed action. Do not retain unrelated process lists, full screen captures, account identifiers or document titles when neutral labels suffice. If identity or impact remains ambiguous, stop at that ambiguity rather than selecting the first matching process.

## 3. Attempt a normal exit before escalation

Use the app's own supported Quit or Close command when authorized and responsive. Recheck the active target before a shortcut. Handle each resulting Save or Discard decision according to the user's instructions; do not silently choose Discard to finish the exit. A normal close can still affect multiple documents or background work.

On macOS, Apple's [normal and forced quit guidance](https://support.apple.com/en-us/102586) identifies Command-Q or the app's Quit menu for normal exit, and the Apple menu's Force Quit window or Option-Command-Escape for forced exit. First inspect the selected application in that window. Do not follow the article's later machine-restart steps automatically.

Apple's [Activity Monitor process-exit guidance](https://support.apple.com/guide/activity-monitor/quit-a-process-actmntr1002/mac) distinguishes Quit from Force Quit: a normal quit may decline when unsafe, while a forced exit is immediate and can lose open work or affect dependent processes. Use that distinction; do not repeatedly issue Quit and interpret refusal as permission to force it.

On Windows, Microsoft's [Task Manager guidance](https://support.microsoft.com/en-au/accessibility/windows/use-a-screen-reader-to-navigate-windows-support-tools) documents opening Task Manager with Ctrl-Shift-Esc, process categories and End Task. Treat End Task as termination with potential loss, not as the equivalent of saving and closing normally. Use the actual visible app/process selection; do not enable extra taskbar controls or use command-line wildcard termination to make the action easier.

These official starting points were checked on 2026-10-19. Recheck current product guidance if the actual interface differs. A vendor article explains mechanics; it does not authorize interruption, privilege elevation or unrelated repair.

## 4. Gate and perform one scoped forced exit

If normal exit fails, establish whether the user's existing approval covers this exact application and the now-known consequences. If it does not, ask a concrete question naming the app, all affected windows/tasks and the unsaved-work uncertainty. For example: “May I force-close this application and reopen it? Both of its document windows will close, and the unsaved changes in the second window may be lost.” Continue read-only preparation while awaiting that decision.

Approval to diagnose does not approve termination. Do not add a redundant approval when the user already explicitly authorized the same action and loss risk. If a previously unknown transfer or additional unsaved window appears, resolve the changed scope first. Required platform warnings and authorization rules still apply.

Immediately before acting:

1. Re-identify the live target; processes and selections can change while waiting for permission.
2. Recheck preservation and background-operation state. If the app has recovered, use the normal path instead.
3. Confirm that the selected control affects only the agreed scope. Do not end a process tree, all matching names, other users' sessions or a shared helper on inference.
4. Use the native control once. Observe the result before retrying. A tool response or closed dialog alone does not prove termination; check the selected app's window/process state.

If the process remains, a privilege prompt appears, the selected identity changes or the operation affects more than expected, stop and report the actual state. Do not escalate to administrator access, repeated termination, service changes or forced power-off. Forced exit cannot be undone; reopening is not a rollback of unsaved work.

## 5. Reopen without replaying the failure blindly

After termination is evidenced, reopen the same existing app within the authorized scope. Avoid repeatedly launching copies. Before reopening, consider whether startup automatically restores the failing project, resumes an external submission, runs project scripts or activates macros. If safe startup cannot be established, leave the app closed and ask for the specific next decision rather than execute unknown work.

Keep any recovery choice open until useful candidates are saved separately and inspected. Do not clear recovery data, delete preferences, remove lock files, reset a profile or overwrite a saved project. Recovery candidates may differ; a latest timestamp alone does not establish completeness. Follow the linked unsaved-work guide if content recovery is needed.

Verify the user-relevant path with a harmless, authorized action. Opening the expected workspace and navigating a saved document can establish responsiveness. A new empty window proves less than a usable original project. Do not repeat a destructive export, transaction, message submission or code execution merely to test recovery. Where such an operation was in progress, inspect its existing status before any separately authorized retry to avoid duplicates.

Check the saved/recovered work against recognizable content and required structure, and distinguish verified content from uncertain unsaved changes. Check that unrelated essential windows and the access route remain available. If the same hang immediately returns, preserve the new observation and stop the restart loop. Prepare the narrow next investigation with app/version, trigger and preserved-work status; do not claim a root cause or apply resets speculatively.

## Acceptance and final report

Finish at one of these evidenced outcomes:

- **Session usable:** the intended app/workspace responds to the relevant safe check; report separately what content was preserved and what remains unknown
- **App closed; reopening blocked:** termination was confirmed, but recovery choices, startup side effects or access prevent a safe next step
- **Partially recovered:** some work is usable while specific content or the original operation remains unresolved
- **Blocked without termination:** target identity, loss approval, protected activity or available access is insufficient; remaining state is preserved as far as observed

Return the app and affected scope, action actually taken, direct observations versus user reports, preserved/recovered work, the verification limit and the smallest next decision. Do not call a session recovery a permanent fix or promise future stability. Instructions prepared without operating the machine must be labeled unexecuted.

There is no automatic cleanup. Retain recovery candidates and existing settings. A new crash report, software update, support upload, reboot or persistent configuration change requires its own appropriate scope. Any diagnostic material intended for a third party must be minimized and authorized for that recipient before transmission.

## Fictional illustration — unexecuted

A fictional user reports that a drawing application froze while arranging a saved diagram. One document window has a separately saved copy; a second untitled window may contain unsaved work. The desktop still responds, no progress is visible, and a normal Quit attempt is reported unsuccessful.

The planned workflow would first inspect for an obscured dialog and confirm that the two windows belong to the same application instance. If the second window's content cannot be preserved, it would disclose that uncertainty before asking for a forced exit affecting both windows. It would not assume that selecting the first window limits termination to that window.

With the exact action approved, the next steps would recheck the live target, terminate it once, confirm closure and assess safe reopening. If the app offers two recovery candidates, both would remain available until useful content is separately saved and compared. A responsive blank window would be reported as an app reopening, not as recovery of the diagram or untitled work.

All events and outcomes here are invented. No computer, app, process, document, termination, recovery or verification was operated for this illustration.
