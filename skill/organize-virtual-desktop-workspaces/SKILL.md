---
name: organize-virtual-desktop-workspaces
description: "Organize selected open windows into native virtual desktops or macOS Spaces, preserving live work and verifying navigation, window identity and app-wide assignment effects. Use for task separation within one logged-in session, not physical monitor setup, browser-session recovery or security isolation."
---

# Put open work into navigable desktop workspaces

Help the user switch between a few coherent groups of open work without closing documents, losing drafts or accidentally moving every window of an application. Deliver an actual checked workspace arrangement when the authorized computer is accessible, or a precise placement plan when it is not. Creating several empty desktops alone does not satisfy the task.

This guide changes the organization of existing windows in one session. Use [configure-multiple-display-workspace](../configure-multiple-display-workspace/SKILL.md) for physical display order, mirroring and scaling; [recover-browser-tab-workspace](../recover-browser-tab-workspace/SKILL.md) for lost tabs; and [prepare-offline-work-session](../prepare-offline-work-session/SKILL.md) for making files usable without connectivity. A virtual desktop is neither a new user account nor a virtual machine. It does not create a separate browser profile, protect documents from another person using the same session, or guarantee privacy during screen sharing.

## Establish the useful grouping

Resolve the following from the request and current interface before asking questions:

- The authorized computer, operating system/version and logged-in session; distinguish a remote host from the computer displaying its viewer
- Existing virtual desktops, selected windows, their application/profile identities and any full-screen or tiled groups
- Desired work groups and a concrete switching pattern, such as comparing research while drafting, then returning to communications
- Windows that must remain together, remain available everywhere, or remain untouched
- Unsaved work, modal dialogs, active calls, recording or screen-sharing sessions, and an accessible way back to the starting workspace
- Whether the request permits actual organization or only a plan

Keep a simple request simple. Two groups can be enough; do not create a desktop per application by default. Group the windows the user needs together, not the categories an app launcher happens to supply. If two identical-looking browser windows belong to different profiles or projects, resolve their identities before moving either. Record safe labels rather than copying private page titles into an unnecessary report.

Use only capabilities actually available on the selected computer. If the window-management interface is not accessible, return a plan and the missing capability. Do not claim dot can directly manipulate a desktop merely because its screen is visible. Do not install a window manager, enable accessibility/control permissions or change account access to complete an ordinary organization request without the applicable approval.

## Preserve the session and avoid false privacy promises

An explicit request to organize the selected workspaces authorizes the ordinary reversible window moves and desktop creation needed for that arrangement. A diagnosis or advice request does not. Persistent app assignments and global switching preferences require that scope to be clear; ask if they would materially broaden a request to move a single window.

Do not close apps, browser windows or desktops as a shortcut to organizing them. Do not restart the shell, log out or relaunch an app to make a window appear on the preferred desktop. A window may hold unsaved text, a pending upload, an active terminal job or a call even when its title looks ordinary. Save or export only when authorized and appropriate; moving a window is not permission to publish a cloud document or submit a form.

Virtual desktop separation changes visibility, not access control. Notifications, task-switcher previews, pinned windows and screen-sharing behavior can still expose content. Before opening an overview that reveals all window thumbnails, establish that no unintended audience is viewing the screen. If a presentation or share is active, pause the organization until the user has safely ended/paused that share or explicitly authorized the relevant exposure. Do not start a live share to test privacy. Do not promise that a window on another desktop is excluded from a recording or shared display.

Preserve existing accessibility preferences, keyboard remappings and display topology. Use the visible overview controls when shortcut routing is uncertain. In a remote viewer, a shortcut may reach the viewer's OS rather than its host; identify its actual destination with a harmless action before relying on it. Never send blind key sequences into a focused document or terminal.

## 1. Inventory windows by identity, not just application

Take a minimal baseline: desktop order/labels, current desktop, selected window identities, current membership, any all-desktop visibility or app assignment, and relevant switching preferences. Include untouched windows only as needed to verify they stay where they were. A few private notes are usually sufficient; a full screenshot archive of the session is not.

Distinguish:

- A window from a tab inside that window: moving the browser window carries its tabs; splitting tabs is a separate change
- A single selected window from every window belonging to its application
- A minimized window from a closed one; reveal it only when needed and restore its state if that is part of the request
- An ordinary desktop from a full-screen application space or existing split-view group
- A physical monitor from a virtual desktop; their arrangements and switching relationships are different

Do not deduplicate similar titles. Record enough private identity to tell the two occurrences apart, such as profile and a harmless distinctive tab or document label. If identification requires reading unrelated sensitive content, ask the user to identify the window instead.

Draw a small before-to-after placement map. Include the original desktop and any assignment that would override a manual move. Mark each selected window as move, keep, available everywhere, or held. The map is also the rollback route; desktop numbers alone may become misleading after insertion or reordering.

## 2. Select the native operation with the correct scope

Consult current official instructions for the installed version. [Microsoft's desktop guidance](https://support.microsoft.com/en-us/windows/experience/configure-multiple-desktops-in-windows) documents creation and renaming in Task View, and separate settings controlling whether the taskbar and Alt+Tab show windows from only the current desktop or all desktops. These visibility preferences do not themselves move the windows. Change them only when the requested navigation experience needs it.

[Microsoft's multitasking guide](https://support.microsoft.com/en-us/windows/how-to-multitask-in-windows-b4fa0333-98f8-ef43-e25c-06d4fb1d6960) describes using Task View's window menu to move an application window to a chosen desktop. Inspect the selected thumbnail and destination, rather than using an app-wide command for a one-window request. If the installed interface offers all-desktop visibility choices, distinguish one-window visibility from all windows of the application before selecting one.

[Apple's Spaces guidance](https://support.apple.com/guide/mac-help/work-in-multiple-spaces-mh14112/mac) describes creating Spaces in Mission Control, moving an individual window through its overview, and assigning an application through its Dock options. Assignment is an app-level choice, unlike dragging one window. Full-screen and Split View items have their own presentation in the Spaces bar; do not treat them as empty ordinary desktops.

Choose the smallest action that meets the map:

- Move one window when only that document belongs elsewhere
- Create a new desktop only when an existing one does not already serve the group
- Use an app assignment only when the user wants that application's broader opening behavior
- Change task-switcher visibility only when navigation across the arranged groups requires it
- Leave an existing full-screen or split group intact unless changing that group is requested

Do not infer Windows options exist on macOS or the reverse. On a different desktop environment, verify its own supported controls and semantics first. If labels or behavior differ from the instructions, inspect the live UI and official version guidance; do not emulate a guessed feature using scripts or undocumented configuration files.

## 3. Move a small group and check the result

Start with an existing harmless selected window, or a permitted neutral test window if needed. Identify the source and destination in the overview, perform one native operation, then exit the overview and inspect the result. Verify that the selected window moved and a similar unselected window did not. Inspect the source too; visibility in the destination alone cannot distinguish a move from an all-desktop pin.

Continue with the remaining mapped windows only after the first operation's scope is clear. Refresh the interface after each change; thumbnails, desktop order and screen coordinates can shift. On uncertain completion, inspect the current membership before retrying. Do not create duplicate desktops or reopen documents because a click's result was delayed.

For macOS app assignments, record the previous assignment before changing it and inspect the application's other existing windows afterward. Apple's documentation also describes an application-switching preference that can take the user to a Space containing that app's windows. Diagnose an unexpected jump by checking assignment and switching behavior separately; repeated dragging is not a substitute for understanding the cause. Avoid changing a global preference to solve a single app's layout unless the user agrees to that broader behavior.

If a dialog follows its parent window, keep their relationship intact. If a window cannot move while a modal operation, full-screen state or application-specific layout is active, leave it held and identify the narrow prerequisite. Do not dismiss a warning, cancel an upload or exit a presentation blindly. A partial arrangement with one accurately described held window is preferable to losing its live state.

Keep the original desktop available until all selected windows are accounted for. Extra empty desktops need not be removed to claim successful placement. If consolidation/removal is requested, inspect where remaining windows will go under the actual platform's documented behavior, move them deliberately first, and verify the result. Removing a desktop is not the same action as closing its application windows; do not click a thumbnail's close control without knowing which object it targets.

## 4. Validate the user's switching pattern

Exercise the intended journey without editing document contents or navigating active web pages:

1. Start on the agreed primary workspace and locate its required windows
2. Switch to the second group through an available supported control, then return
3. Verify every selected window's identity and intended membership; inspect whether any appears everywhere unexpectedly
4. Check that same-application windows remain distinct and that an unselected window was not moved or pinned
5. Use the intended task-switcher or app-selection route and observe whether it stays in the group or jumps elsewhere as agreed
6. Confirm selected unsaved documents and live activities remain present, without claiming their contents were saved merely because their windows remain open
7. Reconcile final desktop order, app assignments and any changed global preferences with the placement map

Check physical-monitor behavior only as far as relevant to this session. A successful switch on one screen does not prove how the other screen behaved. Do not alter monitor settings or disconnect a dock to make the result uniform. Report any difference that affects the user's route.

Launching new application windows, rebooting, signing out and docking are separate persistence tests with possible side effects. Do not perform them just to obtain a stronger completion label. If future opening behavior matters, use a separately safe, authorized test and identify precisely what was observed. A current-session arrangement does not establish that document placement survives restart or that unsaved work will reopen.

## Recovery and delivery

If a move was wrong, use the baseline identity map to return that specific window through the supported overview. Restore changed assignments/preferences to their recorded values only when rollback is appropriate and no later user changes would be overwritten. If the user has reorganized the desktop during the task, reconcile their latest state before undoing anything.

If a window appears missing, inspect all existing desktops, minimized state, full-screen groups and current assignments without closing or reopening the app. If it is actually closed, stop this layout workflow and use the relevant recovery route. Do not imply that recreating an empty window restores its draft or terminal process.

Deliver a concise summary of the actual groups and how to switch between them, changed persistent preferences, held windows and the scope of verification. Keep private window titles out of a broader report. Useful statuses are `placement plan ready`, `windows arranged and current-session navigation checked`, or `partially arranged with named holds`. Avoid claiming privacy isolation, memory savings, notification suppression or restart persistence from a placement check.

Stop when the agreed arrangement and round-trip navigation are verified, the plan-only deliverable is complete, or an exact identity, control, exposure or permission boundary blocks progress. Leave original work open. Do not add automation, third-party window-management software, background monitoring or workspace cleanup as an unrequested extension.

## Fictional example: unexecuted

A fictional user has two browser windows and a note editor on one desktop. They want the research browser and editor together, while the other browser window stays with communications. Both browsers use the same application, and one contains an unsaved form. No screen sharing is active in the invented scenario.

The plan identifies the two windows separately, keeps the form window untouched, creates one additional native desktop and moves only the research window plus editor. It avoids an all-windows-of-this-app assignment. Acceptance would require a round trip between desktops, exact window membership, continued presence of the form and unchanged app-wide preferences. If activating the browser jumps to the other desktop, that behavior would be investigated separately rather than solved by moving both windows.

This is an authored decision example, not an observed result. No computer, window, desktop, account, document or preference was accessed or changed to produce it.
