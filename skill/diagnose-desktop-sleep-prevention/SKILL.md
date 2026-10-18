---
name: diagnose-desktop-sleep-prevention
description: "Diagnose why an existing desktop or laptop stays awake or wakes again when it should sleep, connect power-state evidence to the responsible setting or activity, and verify an authorized narrow correction. Use for sleep entry and unwanted wake behavior, not battery-health assessment, hardware repair, scheduled power automation or changing the machine's sleep architecture."
---

# Find what keeps a computer awake

Return an evidenced explanation and, when requested and permitted, a working sleep configuration checked through the relevant idle or manual-sleep path and a safe return to work. Distinguish a computer that never entered sleep from one that slept and then woke. A dark display, disconnected remote session or quiet fan alone does not settle either question.

Use this for one existing macOS or Windows computer and a bounded reported interval or reproducible situation. Exclude servers, fleet policy, firmware modification, physical power faults, battery replacement, crash diagnosis and failure to resume. Stop a trial if it exposes those problems; do not convert sleep troubleshooting into a destructive repair. If the user only wants a different ordinary timeout, make that scoped setting change without manufacturing a fault investigation.

Read the relevant part of [platform evidence](references/platform-evidence.md) before collecting OS-specific diagnostics. It explains which observations answer which questions and why some report types do not apply to every computer.

## Establish the intended behavior and a recoverable session

Resolve only inputs that affect the next step:

- The exact computer and OS; distinguish the physical host from a virtual machine or remote session
- The symptom and approximate local time with timezone: never sleeps after inactivity, manual sleep returns immediately, or wakes later without the user intending it
- The required condition: battery or external power, lid position, dock/external display, connected peripherals, and local or remote use
- Current sleep/display settings, relevant management restrictions, and any recent change supported by evidence
- Whether the request covers diagnosis only, a named app action, ordinary power-setting correction, or a sleep/wake trial
- Open work, transfers, recordings, calls, updates, backups, shared resources and other users that must not be interrupted
- A permitted observation window, a supported local wake method, someone able to use it, and the desired final state

Use visible settings and supplied observations before asking. “The monitor turns off after five minutes” is evidence about the display policy, not necessarily the requested system-sleep interval. “It was awake this morning” does not establish that it was awake all night. Resolve that distinction before selecting a remedy.

Save relevant work before a trial and establish how the same user session can be recovered. Never start a sleep trial on the only remotely reachable computer without a permitted way to wake it locally or through an already established route. Do not enable remote wake, automatic sign-in or persistent access to obtain a recovery path. Protected sign-in remains owner-controlled; keep passwords, PINs and recovery secrets out of records.

If local observation is unavailable, continue with settings and existing reports. Return a diagnosis or prepared comparison with the actual sleep transition unverified. Do not substitute a trial on the assistant's computer or infer sleep from lost connectivity.

## 1. Classify the failed transition

Build a short chronology for the reported episode, rather than listing all power settings:

| Evidence | Supported interpretation | Next discriminating check |
| --- | --- | --- |
| Display became dark, but no system-state evidence exists | Display-off observed; system state unknown | Inspect applicable transition evidence for that interval |
| Relevant idle policy is Never or explicitly keeps the system awake | Configuration can explain absent automatic sleep | Reconcile the setting with the user's intended work before changing it |
| A current app or driver reports a sleep-related request | An identified activity requests wakefulness now | Check its purpose and whether it overlaps the failed interval |
| Sleep entry followed by a matching exit is recorded | A wake problem, rather than only failure to enter sleep | Inspect the exit reason and its actual owner |
| An authorized manual sleep succeeds, but inactivity does not | Manual entry worked in that condition | Examine idle policy, activity and observation interference |
| The machine restarts or cannot resume | A different failure boundary is exposed | Preserve the last state and hand off the new problem |

Mark each observation direct, user-reported or inferred. Record missing intervals and unsupported states instead of forcing every episode into one cause. Do not treat lock, screen saver, display sleep, system sleep, hibernation and shutdown as interchangeable remedies. A successful manual sleep is not proof that automatic idle sleep is fixed.

On Windows, establish the supported power model before interpreting reports. [Microsoft distinguishes Modern Standby from S3](https://learn.microsoft.com/en-us/windows-hardware/design/device-experiences/modern-standby-vs-s3): Modern Standby stays in S0 and permits some background activity. S0 in a report therefore does not by itself mean ordinary active desktop use. Retain the native state names and observed transitions instead of demanding S3 on a machine that does not support it.

## 2. Join configuration, requests and history

Capture the smallest relevant baseline before closing apps or changing settings:

1. Read the active display and system-sleep policy for the actual power source, including a relevant keep-awake, lid or power-button setting. Record the shown value and whether it is managed. A battery timeout does not explain an AC-only report.
2. Inspect current power requests/assertions in the applicable native tool. Retain request type, owning app/process/device, stated purpose if available, and capture time. An empty snapshot does not prove that no earlier request existed.
3. Inspect transition history covering the reported interval when available. Match the correct machine, date, timezone, power source and entry/exit pair. Keep a last-wake result attached to its last transition, not to an earlier unexplained night.
4. Relate a request to real activity: an unfinished export, media playback, a call, a backup or a deliberately enabled keep-awake feature. Record what is known about the activity's owner and completion. A request can be protecting legitimate work.
5. For a recorded unexpected wake, compare the reported reason with a specific device, scheduled activity or user action. A device capable of waking the machine, or a timer that exists now, is only a candidate unless its timing and event evidence match.

Resolve identities before acting. A process display name may represent several instances or a helper used by multiple apps. A driver label is not a safe termination target. If the owner or purpose is unclear, preserve that gap and collect a narrower observation rather than killing a process with a familiar name.

Keep reports local at the approved destination. Power diagnostics can contain device names, application paths and activity history. Extract the relevant interval and fields for the user-facing summary; do not upload a full diagnostic bundle or contact support without authorization. A failed read or absent field remains unavailable evidence, not a zero result.

Account for the observer. Remote-control activity, synthetic input, a recording or a diagnostic loop may alter the very condition being checked. Stop unrelated automated input during an agreed idle trial, and record unavoidable observer effects. Do not disable management or accessibility services, close a needed assistive app, or remove the only connection simply to obtain a cleaner sample.

## 3. Choose one explanation to test

Write the proposed comparison in one short row: suspected cause, evidence, one changed condition, expected observation, interruption risk and restoration. Choose the least disruptive supported comparison:

- **Intentional work owns the request:** wait for the already-running activity to finish when that fits the task, then inspect again. If the user needs it stopped, use the app's supported pause/stop only within the authorized scope and preserve its resume state. Completion is preferable to defeating the request.
- **An idle app retains a request:** save its work, confirm which instance owns it, and propose or perform an authorized normal quit/reopen. Compare request state and the original sleep path afterward. Do not force-quit or uninstall it as the first experiment.
- **An ordinary policy conflicts with the requested behavior:** preserve the prior value, change only the relevant power-source setting when authorized, and read it back. Keep display timeout, system sleep and lid behavior distinct. A request to diagnose does not authorize an inferred preferred timeout.
- **A peripheral is an evidenced candidate:** inspect its identity and the user's essential input/output dependencies. A permitted temporary disconnection can isolate it, but safely eject storage and finish related I/O first. Leave an essential keyboard, assistive device or sole wake path available. Reconnect after the comparison and distinguish isolation from repair.
- **A wake event has an identified scheduled or shared-service owner:** explain that relationship and its trade-off. Do not disable backup, maintenance, update, network, sharing or wake permissions just because the event interrupted sleep. Prepare the narrow owner-specific decision if it needs separate authority.
- **Evidence does not distinguish the candidates:** collect the missing interval or owner fact, or return a bounded unresolved result. Do not apply a bundle of “power fixes.”

A native request override can conceal a legitimate reason to stay awake. This workflow does not install overrides, switch sleep architecture, enable/disable hibernation, edit power-policy registries, reset all power plans, change firmware or disable device power management. It also does not change lock/password requirements, encryption, network access or organization policy. Escalating suggestions in a vendor article are not permission to perform them.

Honor existing authorization without adding a redundant approval round. Ask for the specific missing action when it would stop protected work, change an unrequested setting, disconnect an important device, require new privilege or cross an access/security boundary. An approved comparison includes its stated restoration, but not reversal of a later independent user change.

## 4. Verify the original path, then resume safely

Before each trial, recheck the actual power source, current settings, important work and local recovery route. Discard a stale plan if a new recording, update, call or transfer has begun. Use a supported native sleep action only for an authorized manual-entry check. Do not send blind power-button keystrokes or assume closing a lid means sleep under every configuration.

For an idle-sleep claim, leave the computer inactive under the original condition for a window justified by its configured timeout and the symptom. Agree a shorter temporary timeout only if changing it is authorized; record that the result then applies to the temporary setting. A ten-minute comparison cannot establish that a machine remains asleep overnight. Avoid a universal “wait two minutes” rule: the selected report must have enough coverage to represent the interval.

Collect the before/after request state and transition evidence without continuously stimulating the machine. If a local person observes it, label their report accordingly. Record:

- Last intentional input and the beginning/end of the observation window
- Whether system sleep entry is evidenced, with native state and source
- Whether a subsequent wake occurred inside the window, and its supported reason or uncertainty
- The deliberately initiated recovery wake and time, so it is not mistaken for the unwanted event
- Return to the same session and a small check that the preserved work and required input/display remain usable

An authorized wake is part of finishing the comparison. Use the previously established device-specific route; a password prompt is handled by the owner. Do not keep pressing buttons, restart or cut power because the remote connection has not returned. If resume fails, stop the sleep experiment and preserve the last directly observed state for a separate recovery decision.

Read back any retained setting change. Restore temporary changes and disconnected nonessential peripherals as agreed, then verify the resulting state. If the final retained configuration differs from the one exercised, say which behavior remains untested. Do not claim that an app reopening, a dock reconnecting or a switch to battery preserved the result without checking that condition when it is part of acceptance.

Do not repeat an unchanged failing trial indefinitely. Continue while the original request still has an authorized discriminating next step; stop at its supported outcome, a meaningful access/permission gap, an unavailable observation window or a new failure outside scope. Ongoing overnight observation needs the user's requested window and stopping condition, not a background schedule invented by the assistant.

## Acceptance, recovery and deliverable

Return a concise private receipt with supporting evidence only where useful:

1. **Finding:** idle policy, active request, recorded wake, no failure reproduced, or unresolved boundary, with the evidence that supports it
2. **Conditions:** computer/OS, power source, relevant peripherals/lid/remote state and bounded interval
3. **Changes:** exact prior/final values or app/device actions, what was restored, and any recovery limitation
4. **Checks:** configuration readback, request-state comparison, actual sleep/wake evidence and resumed-work result, each marked observed, reported or unrun
5. **Next action:** the smallest missing observation or owner decision; no generic reset checklist

Call a correction **verified for the checked condition** only when the original failure path was exercised, relevant sleep behavior was evidenced for the agreed window, the user could resume, and required work was preserved. A changed timeout is **configured; transition unverified** until observed. A closed app with no remaining request is **request cleared; sleep unverified** if the transition was not checked. One successful cycle does not establish future reliability or battery savings.

If a correction fails, keep its observation and restore only its recorded reversible change where still appropriate. If a request reappears, identify the new owner/activity instead of repeatedly closing processes. If the report is unsupported, incomplete or covers the wrong interval, return that limitation and use an applicable source; do not interpret missing rows as successful sleep. If a managed setting or unknown driver is implicated, provide a minimized support handoff and leave the protected state intact.

## Original fictional illustration, unexecuted

A fictional user reports that a Windows laptop's screen becomes dark on AC power but its export keeps running. The user wants automatic sleep once the export finishes and permits inspection plus a later local sleep/wake comparison. They do not authorize cancelling the export, changing power policy or interrupting a backup.

Invented observations show that the active AC sleep timeout is fifteen minutes and the exporting app owns a system-related power request. The workflow would identify the active export, preserve it, and avoid applying an override merely to make the request disappear. A listed wake-capable mouse would not explain this no-entry episode by itself.

Suppose the export later completes and a new supplied snapshot shows its request absent. That hypothetical evidence would support “request cleared,” not “sleep fixed.” The next permitted comparison would retain AC power and the same settings, stop unnecessary input, allow the configured idle interval, and use applicable transition evidence. A person would then wake the machine through the agreed route and check the saved export and work session. If only the screen-off event could be established, the result would remain unverified for system sleep.

All people, circumstances and observations in this illustration are invented. No computer, power setting, application, command, report, sleep transition or recovery action was operated or tested for it. The guide's operational checks describe later authorized work, not completed validation.
