---
name: diagnose-laptop-battery-runtime
description: "Explain short laptop battery runtime by separating available charge, reported capacity and workload demand, then verify a narrowly authorized power-use correction under comparable conditions. Use for a bounded macOS or Windows battery-runtime diagnosis, not sleep/wake repair, battery replacement, forced calibration, charger repair or a battery-safety certification."
---

# Find what shortened a laptop's time on battery

Deliver an evidence-backed explanation of the user's short-runtime problem and, when requested and permitted, a checked power-use adjustment that preserves the work they need to do. Keep three questions separate: how much charge the session started with, how much the battery reports it can hold, and how quickly the selected workload uses it. A high charge percentage, low cycle count or reassuring condition label cannot answer all three.

Use this for one identified Mac or Windows laptop and a bounded active-use interval. A useful result may establish a lower starting charge, a reduced capacity estimate, a workload-dependent drain, several contributing factors, or a precise unresolved boundary. Do not promise a replacement diagnosis or a particular number of future operating hours from one report.

Use [sleep-prevention diagnosis](../diagnose-desktop-sleep-prevention/SKILL.md) when the primary complaint is overnight loss, failure to sleep or repeated waking. This guide can classify such an interval, but does not repair sleep behavior. Keep battery/charger disassembly, firmware resets, charging-circuit repair, replacement purchases, warranty eligibility, OS updates and invasive diagnostics outside this workflow. Read the applicable [platform evidence reference](references/platform-evidence.md) before interpreting native fields.

## Establish the symptom and a safe observation boundary

Find only the facts that change the next step:

- Exact computer, OS release and relevant model; distinguish the physical laptop from a remote session or VM
- What “short” means: the observed start/end times and charge readings, the required task, and the comparison the user is making
- Whether the symptom occurs during active use, sleep, while connected to external power, or when power is removed
- Starting charge, visible charging/limit state, power mode, display brightness and relevant external display, dock or peripheral use
- Main work during the interval, including exports, calls, games, background transfers or recently started maintenance
- Available battery condition/capacity/cycle evidence, its date, and any known battery replacement or OS change
- Authority for inspection, local report creation, a specific ordinary setting/app action, and any unplugged comparison
- Work that must remain uninterrupted, a local person when physical action is needed, available charging, and the desired final state

Use existing settings and records before asking for a new run. A remembered “all day last year” is useful context but not a matched baseline. A percentage estimate shown today is not evidence of yesterday's workload or start charge. Ask for one missing observation when it would distinguish the explanations; do not require a complete hardware survey before reading an obvious charge-limit message.

If swelling, leakage, smoke, a burning smell, enclosure deformation or other concerning physical symptoms are reported, stop the runtime experiment. Do not ask the user to press on, open, charge, discharge or keep using the battery to produce evidence. Follow the model's official safety/support route and retain only existing safe observations. Microsoft's [battery-care guidance](https://support.microsoft.com/en-us/windows/experience/power-battery/caring-for-your-battery-in-windows) specifically says to stop using a device when its battery expands beyond the enclosure. Ordinary capacity wear and a service recommendation are different from a physical safety finding; neither a report nor this workflow certifies safety.

Do not deliberately run the battery empty, repeatedly charge/discharge it, perform a stress test, disable low-battery protections or prescribe calibration as generic troubleshooting. Save important work before an approved power-source change. Keep charging available and establish a stopping point comfortably before the user's low-charge reserve. If safe local observation or the requested evidence is unavailable, finish the supported diagnosis without manufacturing a live comparison.

## 1. Separate charging state from storage capacity

Capture the native fields with their labels, units, source and time. Preserve absent values as unavailable. Avoid collecting full serial numbers or unrelated account information when a neutral battery/device label is sufficient.

| Observation | What it answers | What it does not establish |
| --- | --- | --- |
| Current charge percentage and power-source state | Reported charge now and whether the system reports external power | Original capacity, prior drain or successful charging throughout an earlier interval |
| Charging on hold, charge limit or Smart charging indication | A supported charging policy may explain the current ceiling | A worn-out battery or permission to remove the policy |
| Native maximum-capacity value, or full-charge/design-capacity pair | The system's current capacity estimate relative to its reference | Exact chemical condition, guaranteed runtime or remaining service life |
| Cycle count | Reported accumulated cycling under that platform's definition | Number of plug-ins, a complete history, or a universal replacement deadline |
| Native condition/service message | The platform's reported condition or service recommendation | The cause of every runtime complaint or a physical inspection |

On macOS, record Battery Health and relevant System Information fields as exposed on that model. Apple's [battery-health explanation](https://support.apple.com/en-us/102589) defines maximum capacity relative to when the battery was new and notes that the estimate can recalibrate after an update. Keep a changed reported estimate separate from a directly established loss of stored energy. Do not apply Apple-silicon-specific behavior indiscriminately to Intel models.

On Windows, use an existing report or generate an authorized local battery report through the supported route. Read the installed-battery identities and available usage/capacity sections. Generating a report writes a file; choose a new private filename, preserve earlier reports, and do not describe it as a no-write operation. Use the reference for report options and privilege boundaries.

When both capacity fields are valid, positive and comparable, calculate reported capacity percentage as full-charge capacity divided by design capacity, multiplied by 100. Retain the original values and units. This is a description of the reported estimate, not a universal health threshold or service entitlement. Do not divide by zero, substitute a missing cycle count with zero, clamp a value above 100% without explanation, or label a missing capacity as failed hardware.

Compare like quantities. Do not divide mAh by mWh, treat a relative score as energy, or use a voltage assumption merely to make incompatible fields comparable. Preserve each pack separately on a multi-battery device. Only form an aggregate capacity ratio when the same included packs and compatible energy units support both sums; divide the summed full-charge energy by summed design energy rather than averaging percentages. If pack membership or timing is uncertain, leave the aggregate unresolved. A replaced battery starts a separate capacity history.

Read the actual charging-policy state before attributing an 80% ceiling to wear. [Apple documents](https://support.apple.com/en-us/102338) Optimized Battery Charging separately from the Charge Limit available on supported Apple-silicon systems. [Microsoft explains](https://support.microsoft.com/en-us/windows/experience/power-battery/use-smart-charging-in-windows) that Smart charging behavior depends on the manufacturer. Preserve the existing longevity choice unless the user requests a change. A one-time need for more starting charge is a different decision from disabling a lasting protection.

## 2. Reconstruct the interval that consumed the charge

Make a short chronology from the supplied episode and available native history. Record the actual date, timezone and report-generation time. Keep the report's coverage separate from the period requested; a fresh report does not prove that every earlier interval was retained.

1. Identify start and end observations for the same computer and battery set. Distinguish direct evidence, user reports and inference.
2. Split at observed charging/external-power changes, sleep, restart, battery replacement or docking changes that alter the load. Do not call a mixed eight-hour window eight hours of active battery use.
3. Establish the work and relevant conditions in each usable segment. Include the display, network use, peripherals, power mode and meaningful background activity when evidenced.
4. Identify gaps, estimated endpoints and clock discontinuities. Matching timestamps around a gap do not prove uninterrupted battery-only operation.
5. Compare with a prior segment only if its identity, state, work and measurements are sufficiently comparable. Otherwise explain the mismatch instead of inventing a before/after improvement.

The icon “plugged in” does not prove that the battery gained charge. Conversely, removing one charger may leave a dock or display supplying power. Reconcile the operating system's source/charging state with the actual connection. If it loses charge on external power or switches off as soon as power is removed, stop treating it as an ordinary active-runtime comparison. Preserve that observation and use model-specific official support; do not repeatedly unplug it, swap unverified chargers or infer a failed battery alone.

Use simple arithmetic only where the observations support it:

- **Percentage-point drain:** subtract end charge from start charge over a verified battery-only segment. Divide by elapsed hours to describe percentage points per hour for that segment. A fall from 80% to 70% is ten percentage points, not necessarily ten percent of original design capacity.
- **Energy drain:** if compatible start/end energy readings belong to the same battery set and uninterrupted discharge segment, subtract them in Wh and divide by elapsed hours for average battery-energy use in W. Convert mWh to Wh by dividing by 1,000. State that the readings are estimates and keep source precision.
- **No valid segment:** retain the observations without a rate. Charging, pack changes, hidden state transitions or incomparable measurements can invalidate subtraction. Do not report a negative drain as an efficiency gain.

Do not turn a short percentage slope into a full-to-empty runtime promise. Rounded readings, changing loads, available-capacity estimates and later low-charge behavior limit extrapolation. A zero displayed change over a short interval can mean insufficient resolution. Report measured duration and task completion directly when available; leave unsupported endurance estimates out.

## 3. Connect consumption to useful work

Inspect the app/activity evidence for the relevant window. Read the actual column definitions and selected range, not merely a sorted list. [Activity Monitor's Energy pane](https://support.apple.com/en-ca/guide/activity-monitor/actmntr43697/mac) distinguishes a relative current Energy Impact from the average 12 hr Power. Neither is a watt reading. On Windows, preserve the selected Power & battery usage period and foreground/background information where available; an app's reported usage share is not automatically the number of battery-charge percentage points it consumed.

Join a candidate app to its purpose and time. A video editor can legitimately be the largest consumer during an export. A browser process label alone may not identify the responsible tab or task. A high historical share can remain after the activity has stopped. A low current reading cannot clear an app from an earlier episode. Do not add relative scores across unlike sources or compare overlapping rolling windows as independent trials.

Classify what the evidence supports:

- **Less charge available at departure:** the recorded starting charge or supported charge limit differs, with the capacity and demand contribution still separately assessed
- **Lower reported capacity:** the same identified battery has a lower applicable estimate, without claiming that this explains the entire runtime change
- **Higher demand under the reported work:** relevant activity and a usable discharge segment are consistent with increased consumption
- **Mixed causes:** more than one factor is supported; retain each instead of choosing a single convenient culprit
- **Different failure boundary:** sleep loss, external-power charging behavior, abrupt shutdown or a service/physical concern needs its own route
- **Insufficient evidence:** identify the missing interval, measurement or activity relationship that would change the conclusion

A diagnosis can finish here if the request was explanatory. Do not make an unrequested preferred brightness, performance trade-off or app shutdown part of the answer.

## 4. Make one authorized comparison that preserves the task

When a correction or comparison is requested, choose one plausible, reversible change and state its expected effect and cost. Examples include lowering a display setting to a level the user can still read, using an existing supported lower-power mode that keeps the required task usable, or normally closing a confirmed unnecessary app after its work is saved. Record the prior value and intended final state first.

Do not disable backups, sync, updates, security or assistive services just to lower a graph. Do not terminate an unknown process, clear history, reinstall a driver, reset power plans or change firmware as a battery experiment. New software, privilege, protected credentials, a restart, an unapproved interruption or a security/access change remains a separate permission boundary. Honor already authorized ordinary changes without inserting another generic approval round.

Define the comparison before starting:

- Same laptop and battery set, no unaccounted external power, and comparable starting charge/thermal conditions
- A bounded representative task, comparable workload and completion quality, with relevant display/peripheral/network conditions held steady
- Baseline and candidate observation windows long enough for the available measurement resolution, within the user's available time and charge reserve
- The single changed setting/activity, relevant remaining background work, and unavoidable observer effects such as remote control or screen recording
- The stop condition, charging/recovery route, and what will be restored or retained

Use an existing suitable baseline when possible. Do not require a full charge, empty battery or several repeated cycles. If the user needs to keep working, observe a permitted normal session and mark uncontrolled differences instead of pretending it is a laboratory comparison. A lower-power mode can slow work; compare completion and usability as well as drain per minute. Finishing less work with a lower rate is not automatically a better result for the user's task.

For each window, record start/end time, relevant state, charge/energy readings, task progress and interruptions. Stop at the agreed reserve, unexpected heat or instability, a new essential task, loss of the recovery route, or an invalidating power-state change. Preserve work and return to the agreed safe state. Do not continue discharging merely to obtain a larger numerical difference.

## 5. Verify the result and leave a usable setup

Read back any retained setting and confirm that the user's required activity still works. Compare the same kind of evidence over the declared windows, including a failed or inconclusive comparison. Keep background histories with overlapping periods distinct from new window-specific observations.

A lower relative app score supports only that score's observed change. A supported lower discharge rate under comparable conditions supports a bounded consumption result. Neither means battery capacity was repaired. If the candidate's work output, conditions or readings differ materially, report the trade-off or inconclusive comparison instead of a percentage improvement.

Restore temporary changes within their agreed scope, checking that another user action has not superseded the old setting. Do not restore stale values over new preferences. Return the computer to the requested power connection and work state when that action is safe and authorized. Readback after restoration is separate from a trial performed with the temporary setting; identify which state was actually exercised.

If a change fails, preserve the result and reverse its recorded reversible effect when appropriate. Continue only while there is an authorized next comparison that could distinguish the remaining explanations. An unsupported report, noisy short interval, unavailable local observation or service-needed condition is a valid stopping point with a precise next step. Do not turn a one-time diagnosis into recurring monitoring or repeatedly run the same drain trial.

## Acceptance and handoff

Return a concise private result, with a small supporting record only when useful:

1. **Finding:** what explains the observed runtime and what remains unresolved
2. **Evidence:** computer/battery identity, report dates, capacity/charge-policy observations, the usable interval and its units/conditions
3. **Action:** exact before/after settings or app action, authority, task trade-off and restoration/final state
4. **Checks:** direct observations, user-reported results and unrun checks, including whether the required work remained usable
5. **Next step:** one missing observation or the exact official service route; no unsupported replacement or warranty verdict

Call the outcome **diagnosis supported** when the stated explanation follows from the scoped observations. Use **configured; runtime effect unverified** when only a setting was saved, **lower consumption observed in this comparison** for comparable measured evidence, and **inconclusive** when resolution or conditions do not support a difference. A service indicator may justify professional evaluation without establishing the fault or cost. Save a requested receipt to the approved private location and read it back; keep full reports, identifiers and activity history out of public sharing or support uploads unless separately authorized.

## Original fictional illustration, unexecuted

A fictional Windows laptop report lists design capacity of 60,000 mWh and full-charge capacity of 48,000 mWh for the same battery. The reported capacity ratio is therefore 80%; that is unrelated to the user's separate observation that a manufacturer charging limit often stops at 80% charge. Neither observation alone identifies a defective battery or a warranty entitlement.

An invented active-use interval starts at 38,400 mWh and ends at 32,400 mWh one hour later, with no charging or sleep and a video export running throughout. That arithmetic describes 6 Wh consumed, or an estimated 6 W average for that interval. The export being the largest app consumer is consistent with the work; it is not proof of waste. A later light-writing interval would not be a matched improvement even if its drain were lower.

The user permits checking one ordinary power-mode change but needs the export to finish. The proposed comparison would preserve the export, choose a later matched task, record both consumption and task completion, and stop before the agreed charge reserve. If the only later evidence were a saved power-mode switch and a lower current app score, the result would remain configured with runtime effect unverified. No full-to-empty test or promise of eight-hour endurance would follow.

All people, readings, circumstances and calculations in this illustration are authored fictional material. No laptop, battery, report command, app, setting, charging action or runtime comparison was operated or tested for it. The guide describes later authorized work, not completed device validation.
