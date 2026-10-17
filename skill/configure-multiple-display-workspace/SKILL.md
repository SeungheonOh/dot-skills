---
name: configure-multiple-display-workspace
description: "Set up already-connected displays for the intended extended or mirrored workspace, reconciling physical identity, arrangement, primary display and readable scaling with a visibility-preserving rollback. Use for desktop layout, not driver repair, casting setup or color calibration."
---

# Make a multi-display workspace usable

Deliver the requested screen arrangement and readable presentation, with before/after settings and an actual task-level check. Two illuminated screens do not establish that the pointer crosses the expected edge, windows remain reachable, or text is usable.

Use this for reversed screen order, unwanted mirroring, the wrong main display, uncomfortable text size or windows stranded after a display change. [meeting-device-troubleshooting](../meeting-device-troubleshooting/SKILL.md) covers microphone, speaker and camera paths; this workflow concerns desktop topology and per-display presentation. Missing hardware, cable bandwidth, driver faults, wireless casting, remote-access setup and calibrated color require their own investigation.

## Identify the intended workspace

Resolve from the request and visible state:

- Authorized computer and OS/version, local versus remote session, and any virtual displays
- Physical screen labels, left/right/above/below positions, orientations and dock/connection path when known
- Intended use: separate workspaces, mirrored presentation, one chosen main display, or an explicit mixed arrangement
- Which screen and app have the readability problem, plus current per-display resolution, scale or display-mode labels and relevant app zoom
- Work that must remain visible, unsaved documents, active calls/presentations, and the user's existing accessibility preferences
- Whether the request authorizes ordinary settings changes or asks for a plan only

Ask for physical positions or identity confirmation when they cannot be observed. OS numbers are identifiers, not a reliable description of left-to-right order. Identical monitor names and a screenshot of one desktop cannot establish which physical panel is which. Record missing information rather than rearranging screens by guesswork.

Use the actual version's supported controls. If the intended monitor is absent from settings, finish the visible inventory and investigate the documented detection/connection path within scope. Arrangement changes cannot enable an unsupported number of displays. Do not install drivers, update dock firmware or promise that a particular adapter supports a mode without evidence for the exact hardware.

## Protect visibility, privacy and work first

An explicit request to configure this workspace covers ordinary, in-scope reversible display preferences. A diagnosis-only request does not. Record old values and the affected physical screen before every change. Obtain any missing authorization when the proposal affects another user's session, active presentation, sharing target, or a broader preference than requested.

Mirroring can expose the whole desktop to a room, TV or remote viewer; an extended screen can also reveal windows moved there. Verify the audience and intended display before moving private content or enabling a mirrored mode. Use a blank or harmless local window for checks. Do not initiate casting, screen sharing or another remote connection merely to test the layout. Keep screenshots limited to settings and harmless test content.

Preserve unsaved work. Avoid logout, sleep, disconnecting a dock, closing the laptop lid, changing the only working output or restarting graphics/system services as first-line steps. Dock disconnection can also interrupt storage, network or audio. Read-only inspection can continue while a safe window for disruptive work is pending.

Before any change that could hide the interface, establish a specific recovery route: an independently usable screen and its controls, an available local observer, or the platform's documented revert behavior for that exact change. A remote-control screenshot does not guarantee that a local panel remains readable. If losing the only control path would leave no verified recovery, stop at a proposal. Never approve an unseen confirmation dialog or keep a mode solely because an automation reported a successful click.

## 1. Map physical screens to settings

Create a small map with physical label/location, current OS label, connected/virtual status, mode, orientation, main-display role, resolution/scale, and how identity was established. Include only fields relevant to this task.

Use a supported Identify control or a harmless visible window with the user's confirmation when appropriate. On Windows, [Microsoft's multi-monitor instructions](https://support.microsoft.com/en-us/windows/hardware/display-graphics/how-to-use-multiple-monitors-in-windows) document Identify and dragging display tiles to match the intended arrangement. On macOS, [Apple's Displays settings reference](https://support.apple.com/en-nz/guide/mac-help/-mh40768/mac) describes Arrange and Use as for position and main/extended/mirrored roles, with options depending on the display/model.

Distinguish the coordinate map from the physical panel dimensions. Different logical resolutions or scaling can create unequal desktop edges even when the panels have similar physical sizes. Record the desired alignment, such as shared top edge or a convenient central crossing, instead of assuming equal-sized tiles.

For a remote session, identify whether the settings belong to the host's physical displays, remote virtual displays, or the viewer's local screens. Changing viewer zoom or window size is not the same as changing the host workspace. Do not modify the host's local-user layout to solve a viewer-only scaling problem.

## 2. Choose the smallest control that meets the goal

Separate these decisions rather than changing them together:

| Symptom or goal | Relevant control and check |
| --- | --- |
| Both screens show the same workspace but independent work is wanted | Extended versus mirrored mode; verify each screen can show a distinct harmless window |
| Pointer exits the wrong edge or cannot cross at the expected height | Arrangement and alignment; verify the specific adjoining edge in both directions |
| Main controls or newly opened work appear on the wrong display | Main-display role and, if relevant, the application's own placement behavior |
| Text is too small throughout one display | That display's scale/display mode; keep the other display unchanged |
| Only one app/page is too small | Its existing zoom/text settings before changing the entire desktop |
| Everything is magnified or only part of the desktop is visible | Inspect existing accessibility zoom or app mode before assuming resolution is wrong |
| Window is outside the current visible area | Supported window-move/recovery controls; preserve the document rather than closing the app |

Do not turn off an accessibility aid as a generic correction. A current value may be intentional. Preserve it unless the user requests a change or agrees to the specific proposal.

On Windows, [Microsoft's scale/resolution guide](https://support.microsoft.com/en-us/windows/hardware/display-graphics/change-your-screen-resolution-and-layout-in-windows) treats Scale and Display resolution as separate controls and recommends selecting the intended display first. Prefer the recommended/native resolution when appropriate and adjust scaling for readability; lowering resolution can affect sharpness. On macOS, [Apple's resolution guide](https://support.apple.com/en-ie/guide/mac-help/mchl86d72b76/27/mac/27) explains its default and scaled choices and warns that some windows may no longer fit. Do not transplant a Windows percentage into a Mac control or assume an app's 100% zoom equals physical actual size.

Keep color profile, HDR, refresh rate, custom timings and monitor firmware unchanged unless those are the actual authorized task. Those controls are not necessary merely to fix pointer direction or text size.

## 3. Apply one scoped change and inspect it

Start with an arrangement or mode correction supported by the evidence, then adjust readability if requested. Write the physical target, old value, proposed value, intended effect and recovery action. Apply through the supported settings UI and read back the actual value.

If the system offers a timed Keep/Revert prompt, inspect all affected screens before keeping the change. Verify the timer/revert behavior rather than assuming every control has one. Apple's resolution guidance describes waiting for automatic recovery and then using Escape when a resolution change leaves no picture; consult that exact platform procedure in advance. It does not justify a blind key sequence in an unknown dialog or an automatic safe-mode restart.

After topology, scaling or resolution changes, obtain a fresh view of the UI. Screen coordinates and window positions may have moved. Do not reuse old click locations. Confirm the settings window and an independent recovery control are still reachable before making another change.

If an attempted mode is unreadable, revert through the established route and verify the previous working state. If visibility or control is lost, stop remote actions and use the agreed local recovery/handoff. Do not compound an uncertain state with more display toggles.

For a stranded window, use the application's or OS's documented move-to-screen command when available. Avoid blind keyboard sequences that might edit or submit the document. If recovery would require a risky application restart, report the remaining window and preservation requirement instead of closing it.

## 4. Check the user's actual work pattern

Validate the changed properties without exposing private content:

1. Match each settings label with its intended physical display and confirm the requested extended/mirrored grouping
2. Move the pointer across each relevant shared edge in both directions, including the height the user normally uses; a corner touch is not an adequate crossing
3. Move a harmless window between screens and verify its title bar, controls and complete useful area remain reachable
4. Inspect representative text and controls on the affected display at the intended app zoom; distinguish the assistant's rendered view from the user's report of physical readability
5. Check the main-display role or app placement if requested, without assuming every application follows the system main display
6. Read back final settings and reconcile each temporary change as restored or intentionally retained

Different scale factors can change a window's apparent size when moved. A readable settings pane alone does not prove the user's affected application behaves well. If one app remains blurry or clipped, record that app-specific result instead of repeatedly changing both screens.

A reconnect or sleep/wake check is needed only when persistence across that event is part of the request. Plan its interruption and obtain the necessary authority first. Until performed, label persistence untested; do not claim the arrangement survived docking merely because settings readback succeeded.

## Deliver and recover

Return the physical-to-OS map, exact changed/restored values, final layout, completed task checks and remaining limits. Distinguish `settings applied`, `workspace checked`, and `physical readability confirmed by user`. A remote screenshot can support layout observations without establishing viewing-distance comfort or physical color.

Stop when the requested workspace is usable with evidence, a plan-only deliverable is ready, or progress needs missing display identity, a local recovery route, hardware capability evidence or authorization. If a change's outcome is uncertain, inspect state before retrying. If rollback failed, report the current known state and the one affected screen rather than claiming the original arrangement was restored.

## Fictional example — unexecuted

A fictional user has an already-connected laptop to the left of an external monitor. Supplied settings show the external display logically left of the laptop, both extended. The user wants the pointer to move right from laptop to monitor and larger text only on the monitor.

The proposed sequence identifies both screens, records existing values and recovery access, corrects the tile order, checks crossings, then adjusts only the external display's supported scaling choice. It leaves the laptop and existing accessibility settings unchanged. A harmless window and the affected app would be checked afterward; docking persistence would remain untested unless requested and safely exercised.

No display, computer, remote session, settings control or application was operated for this authored illustration.
