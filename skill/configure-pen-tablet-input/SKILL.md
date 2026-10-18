---
name: configure-pen-tablet-input
description: "Configure an existing screenless pen tablet for a chosen desktop drawing application, reconcile its display mapping and pressure-input path, and verify physical strokes, pen release and retained settings. Use for a usable drawing-input setup, not artwork creation, Bluetooth pairing, pen-display calibration, driver replacement or systemwide input remapping."
---

# Make a pen tablet work in the intended drawing app

Deliver a usable physical pen-to-canvas setup and a short record of how to return to it. Keep tablet detection, pointer positioning, pressure events and the brush's response separate. Moving the cursor or drawing a uniform line does not establish pressure-sensitive input; a saved picture cannot establish how its strokes were made.

Use this for one existing screenless drawing tablet, its compatible pen, an established USB connection and an installed supported driver and drawing application. Resolve a wrong monitor, distorted movement, missing pressure or an unsuitable response through the relevant existing controls. Keep display-equipped pen tablets, touch-only styluses, handwriting recognition, signature capture, firmware servicing and hardware repair outside this bounded workflow.

[Multiple-display setup](../configure-multiple-display-workspace/SKILL.md) handles the desktop arrangement itself. [Application shortcuts](../configure-application-shortcuts/SKILL.md) handles command bindings. [Visual asset creation](../create-visual-asset/SKILL.md) handles finished artwork. None substitutes for proving this physical coordinate-and-pressure input path.

## Establish the drawing task and available control

Resolve only what changes the next step:

- The physical tablet model, compatible pen, actual connection and computer; OS, installed tablet driver and drawing-app versions when relevant
- The intended physical display, current desktop arrangement and whether the tablet should control one screen, several screens or a supported smaller region
- Desired absolute pen positioning or an intentionally chosen relative mode, and any existing orientation or limited active area the user wants preserved
- The actual app, brush/tool and pressure-driven property needed, such as line width; include tilt, eraser or buttons only when requested and supported
- Existing tablet/application profiles, other pens and working settings that must survive
- A person who can move the actual pen, judge its response and confirm the physical screen; an independently working mouse or trackpad for recovery
- Setup proposal versus authorized configuration, and whether later app restart or reconnection is part of acceptance

Do not infer the pen's compatibility from its shape or assume every model supports tilt, an eraser or touch. Match the device and installed software to current manufacturer instructions. A missing supported driver is a prerequisite to resolve, not evidence that changing the app's pressure curve will help. Identify required installation, restart or permissions without silently performing them.

Establish where the tablet is attached and where the app runs. Ordinary remote pointer forwarding may not establish a supported pressure-event path. If the app is remote, document the actual supported input route or keep that boundary unverified; do not enable USB redirection or change remote-session policy under this task.

If no physical observer or device access is available, prepare the exact supported setup candidate and pending checks. Mouse automation, generated pointer events and a brush preview are not a physical-pen check.

## Preserve work and the input boundary

Use a harmless scratch canvas in the intended application, protecting open documents and existing brush presets. Do not draw a signature, use a private artwork as a test, or overwrite the user's template. Save a sample only when useful or requested, to an authorized location whose synchronization/sharing behavior is understood.

An explicit setup request covers ordinary in-scope tablet and app preferences. It does not authorize driver installation or replacement, device enrollment, account creation, cloud settings backup, security changes or unexpected app permissions. New Accessibility/Input Monitoring access and other materially expanded persistent access require their applicable action-time confirmation. Handle credentials through the supported secure handoff. Stop at managed restrictions rather than disabling protections.

Keep an independent pointer route to settings before changing mapping or pen-tip behavior. Record the affected device, component, application scope, old value and proposed value. A global tablet preference, app-specific driver profile, application-wide pressure curve and brush preset have different reach. Do not reset all preferences to obtain a clean comparison.

The person should use ordinary comfortable pen pressure. Do not ask them to press harder and harder to reach a diagnostic maximum, disassemble the pen, remove a nib or alter hardware for this setup. Stop the physical trial if there is damage, unusual resistance or discomfort; a successful software check would not establish hardware condition or ergonomic suitability.

## 1. Bind the controls to the actual tablet, pen and application

Inspect the existing native tablet utility and identify the connected device and selected pen/component. If several entries are present, resolve the physical match before editing. Inspect whether the current values belong to all applications, the target app, or another saved profile. Retain only relevant non-secret labels and values; do not collect device serial numbers or unrelated application lists by default.

For Wacom, the [application-specific settings guide](https://101.wacom.com/UserHelp/en/AppSpecificSettings_Full.htm) describes selecting a device and component, adding the installed application's executable if needed, then editing that application's settings. Adding an app changes the general entry to All other applications. Two programs with the same executable filename can share customization. Check the actual installed version and effective scope rather than trusting a familiar icon. Do not assume every mapping or orientation control can be app-specific merely because pen buttons can.

Prefer the existing correct profile. If a new app-scoped entry is needed, retain the previous general behavior and identify which values are inherited or copied. Read back the selected scope before each change. Removing an application entry can remove its custom settings; it is not a harmless way to refresh detection.

Establish the existing pen-tip action before testing. [Wacom's pen settings guidance](https://101.wacom.com/userhelp/en/Pen_Pro_Full.htm) notes that most graphics apps need the tip assigned to Click, and distinguishes tip sensitivity from optional eraser settings. Preserve intentional assignments unless the requested drawing setup requires an agreed correction. Do not test unrelated side buttons or assign a macro merely to confirm the pen is detected.

## 2. Reconcile the tablet-to-screen coordinate map

Identify the physical screen through a supported display-identification route or the local person's observation. A display number does not reliably mean left, right or the drawing monitor. Keep OS arrangement, resolution and scaling unchanged when they are not the task; if they change during work, revisit the tablet mapping before interpreting later observations.

For Wacom's documented [Pen and Mouse modes](https://101.wacom.com/UserHelp/en/MappingAdvanced_Full.htm), Pen mode gives an absolute correspondence between tablet and screen points. Mouse mode retains the cursor position when the pen is lifted and uses relative movement. Select the intended behavior deliberately; an unfamiliar absolute jump is not automatically a defect. Do not change system mouse acceleration to correct a Pen-mode mapping problem.

On that Wacom route, Pen mode is required for display/active-area mapping. If relative Mouse mode is intentional, preserve it and skip the absolute-mapping steps below; verify the relative movement and pressure path instead. If the request also requires confinement to a particular display, resolve that mode choice before changing anything rather than promising both behaviors.

Use the selected device's supported mapping controls to reconcile:

1. The screen region the pen should reach
2. The tablet's active region supplying that movement
3. The physical tablet orientation and its corresponding software setting, where supported
4. The proportional relationship between those two regions

Wacom's [mapping reference](https://101.wacom.com/UserHelp/en/Mapping_Full.htm) supports choosing one display from a multi-display setup and, under supported advanced controls, choosing smaller screen or tablet regions. Its current Wacom Center route selects the device, then Mapping; Select one display chooses the target. Older utilities can use different labels. Prefer the whole intended screen and existing tablet area unless a smaller region serves the user's actual need. Re-read the resulting area rather than treating Apply as sufficient.

The [Force proportions reference](https://101.wacom.com/UserHelp/en/ForceProportions_Full.htm) explains that proportional mapping can leave part of the tablet inactive. Show or describe that resulting active boundary before testing. Do not treat a deliberately excluded strip as a dead sensor or stretch the mapping merely to make every physical edge active. Mapping controls do not resize the canvas or change the artwork's pixel aspect.

With the scratch canvas safely visible and the independent mouse available, have the person move the pen over the intended active area toward its corners and center. Prefer hover where supported to avoid clicking controls. Check that motion reaches the expected screen region and direction; do not demand contact at the tablet's outer plastic edge. Use a few simple loops and crosswise strokes to judge usability, but do not claim a freehand circle proves calibrated geometric accuracy. Record the user's physical observation separately from a remote screenshot.

## 3. Separate pressure delivery from brush interpretation

Trace the selected path:

physical pen and tablet → installed driver/OS pen route → target application's tablet input → chosen tool and brush response

When pressure is missing, compare the earliest supported observation first. [Wacom's pen diagnostics](https://101.wacom.com/UserHelp/en/TestingPen_Full.htm) expose movement, pressure and supported pen features for the selected device. A bounded comfortable press/release can establish that values change at that point; it does not establish the application's response. Observe release as well as contact. Do not reproduce maximum-force or every-feature diagnostics when a smaller observation answers the task.

If the driver sees pressure but the target app does not, inspect the app's supported input route before changing sensitivity. In Krita on Windows, [Tablet Settings](https://docs.krita.org/en/reference_manual/preferences/tablet_settings.html) distinguishes WinTab from Windows 8+ Pointer Input, whose use depends on driver Windows Ink support. Use the route documented for this device/app combination, preserve both previous settings, and apply any required app restart only after safeguarding work. Do not repeatedly toggle APIs without a comparison or install another tablet driver as an experiment.

Krita's same reference documents its Tablet Tester: red traces represent mouse events, while blue traces represent tablet events. Its output is raw input and does not include Krita's global pressure-curve adjustments. Inspect pressure values as well as event presence. A mouse trace alone is not pressure evidence; a tablet trace alone does not show that the chosen brush uses pressure.

For the actual drawing check, choose an existing simple brush whose documented settings use pressure for the requested property. Inspect the current sensor assignment rather than assuming every preset changes width. [Krita's brush-settings guide](https://docs.krita.org/en/user_manual/loading_saving_brushes.html) illustrates separate pressure controls for size, opacity and flow. Keep the original preset intact; a temporary comparison must not become an overwritten favorite brush.

If events arrive but the response feels wrong, compare the affected layers one at a time: driver sensitivity, app-wide curve, then brush-specific sensor/curve. Keep unrelated brushes and global defaults unchanged where a narrower correction works. [Wacom's advanced pen settings](https://101.wacom.com/UserHelp/en/AdvancedPenEraser_Con_Full.htm) also distinguish advanced pressure controls and double-tap behavior; some simpler sensitivity adjustments override advanced pressure settings. Read the applicable control's effect before using it. Do not flatten every curve or remove stroke smoothing to manufacture a dramatic demonstration.

## 4. Verify a small real drawing interaction

Use the intended app, target display, selected profile and harmless canvas. Have the local person perform a short agreed sequence:

- Move to several separated canvas locations and begin strokes where expected
- Draw light-to-moderate strokes with ordinary comfortable force using the identified pressure-sensitive brush
- Lift fully between separate strokes and move to another location; verify that pen-up movement does not continue drawing
- Draw a few short marks and longer curves to check usable starts, stops and control without changing zoom or brush halfway through
- Exercise a requested supported eraser or button only after checking its assignment and harmless target

Keep smoothing, brush size, canvas zoom and selected preset stable while comparing a change. A tapered image alone could come from a brush's time/distance rule; connect the visible result to the physical input observation and relevant sensor setting. Do not invent a pressure-resolution, latency or accuracy measurement from a visual trial. A person's report that the response is comfortable is useful acceptance evidence, not a medical or performance certification.

If app-specific behavior matters, leave the target app for a harmless already-open context, then return and repeat the small required action. Inspect whether the correct profile resumes without replacing unrelated app settings. A profile shown in the utility is saved-state evidence; this context switch supplies a different, bounded observation of its effect.

Read back final affected settings. A restart/reconnect check is required only when requested or necessary to apply the chosen change. Protect work and the shared connection, then reidentify the device/profile and repeat the physical check after that actual event. Reopening a saved stroke sample proves the file's content remains, not that live pressure input still works. Do not restart, sleep or unplug a shared dock solely to fill a checklist.

## Recovery and stopping conditions

Use the observed failure boundary:

| Result | Narrow next action |
| --- | --- |
| Tablet utility cannot identify the intended device | Check the exact supported connection and device/driver compatibility; hold installation or hardware work |
| Pointer reaches the wrong screen everywhere | Recheck device identity, mode, orientation and screen/active-area mapping |
| Pointer works elsewhere but the canvas is offset | Inspect the app's input/coordinate settings and actual display context; do not rearrange the whole desktop speculatively |
| Driver sees pressure; app sees only mouse events | Check the supported driver-to-app API and existing access boundary |
| App sees varying pressure; brush remains uniform | Inspect the selected tool and that preset's pressure sensor before changing driver settings |
| Marks continue after lifting or controls fire unexpectedly | Stop drawing, use the independent mouse, inspect contact/button state and the actual effect before retrying |
| No useful difference after one scoped comparison | Restore that change when safe, preserve evidence and choose a different evidenced boundary rather than cycling the same toggle |

Restore only affected temporary values, comparing current state with the recorded before state so later user edits survive. A driver reset, preference-file deletion, driver uninstall or removal of an app profile can discard unrelated customization; none is an automatic recovery step. Retain the requested successful setup and close only the diagnostic views opened for this work. Do not delete samples or logs without the appropriate authority.

Stop when the requested stage and needed physical checks are evidenced, the setup proposal is delivered, or a specific compatibility, permission, physical-observation or control-recovery prerequisite blocks progress. A working cursor with pressure unverified is a partial result. A successful current session does not establish behavior in every app or after an unobserved restart.

## Deliver the usable setup

Return a compact private handoff:

- Tablet/pen and connection → intended display/active area → app/input route and checked brush
- Final changed values, scope and the supported way to restore those changes
- Physical mapping, pressure response and pen-up checks observed, distinguishing direct evidence from the local person's report
- Any requested saved sample or profile, with what was actually reopened or read back
- Remaining requirement, exact blocker and smallest useful next check

Use precise status such as prepared only, mapping checked with pressure unresolved, or physical drawing checked under the stated conditions. Configuration readback, raw-event evidence, live drawing and retained sample content support different claims.

## Fictional, unexecuted illustration

An invented user wants an existing screenless tablet to draw only on the right-hand monitor. Hypothetical settings map it across both screens, and a brush produces a constant-width line even though a supplied diagnostic observation shows varying pressure.

The proposed sequence would first bind the tablet to the identified right-hand screen and review the proportional active area. It would then inspect the actual brush's sensor settings: a fixed-width preset would not justify reinstalling the driver. A separate existing pressure-sensitive brush would supply the bounded comparison, with physical light-to-moderate strokes and lifts still awaiting observation. Success would require the intended screen mapping, visible pressure-driven behavior and clean pen-up movement in that app; a saved image alone would leave the live input claim unsupported.

This is an original decision illustration, not a completed setup. No tablet, pen, driver, application, setting, canvas, stroke, diagnostic, restart or reconnection was operated or tested for it.
