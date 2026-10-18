# Match the evidence to the power model

Read only the branch for the actual computer. These are diagnostic starting points, not a command batch or permission to operate a device. Recheck current official guidance and the installed tool's help when a version or supported option differs. All commands below are illustrative and unexecuted.

## macOS

Use [Apple's sleep-setting guide](https://support.apple.com/guide/mac-help/set-sleep-and-wake-settings-mchle41a6ccd/mac) for the current model/release. Laptop and desktop controls differ; inspect the active power-source setting and any option that keeps the computer awake while its display is off. Do not change network wake or shared services incidentally.

[Activity Monitor's Energy pane](https://support.apple.com/guide/activity-monitor/view-energy-consumption-actmntr43697/mac) provides a Preventing Sleep field. Its Energy Impact measure is relative, so do not present that number as measured watts or use high consumption alone to name the sleep blocker. Match the app/process and observation time.

Apple's archived [app power-efficiency guidance](https://developer.apple.com/library/archive/documentation/Performance/Conceptual/power_efficiency_guidelines_osx/PrioritizeWorkAtTheAppLevel.html) documents `pmset -g assertions` for current assertions and their owning processes. Preserve the assertion type: idle-system-sleep prevention is not the same as display-sleep prevention. Treat an app-supplied reason string as a clue about its activity, not independent proof that a job is still running. The article is archived; do not copy its older menu labels as a current UI guarantee.

For historical transitions, use available native evidence and the installed system's documented read-only logging options. Limit extracted history to the requested interval; record the original event names, timestamps and coverage. A present assertion snapshot cannot reconstruct last night's timeline, and a background wake record does not establish that the user-facing desktop stayed active.

[Apple's unexpected sleep/wake troubleshooting](https://support.apple.com/en-in/guide/mac-help/-mchlp2995/mac) identifies shared-resource activity, indexing, input and attached devices as possible influences. Use those as hypotheses supported by this machine's evidence. Do not automatically stop indexing, disable sharing, reset a controller, restart, update or unplug storage simply because the article includes that possibility.

## Windows

[Microsoft's powercfg reference](https://learn.microsoft.com/en-us/windows-hardware/design/device-experiences/powercfg-command-line-options) distinguishes queries, generated reports and mutating options. The relevant inspection vocabulary is:

| Inspection | What it supplies |
| --- | --- |
| `powercfg /a` | Available sleep states and reported unavailability reasons |
| `powercfg /requests` | Current application/driver power requests |
| `powercfg /lastwake` | Information about the last sleep exit |
| `powercfg /waketimers` | Active wake timers |
| `powercfg /devicequery wake_armed` | Devices currently configured to wake the system |
| `powercfg /systemsleepdiagnostics` | A saved report of user-absence intervals and whether sleep occurred |

The last command writes a report and requires elevation; use its documented output option with a new approved local filename. Inspect permission requirements before each selected command. Missing privilege is a blocker, not permission to elevate. Avoid collecting every report by default.

Do not run adjacent mutation options such as request overrides, device wake changes or hibernation changes as diagnostics. The `/energy` mode also has idle/no-open-program prerequisites; it is not a passive historical explanation of an active export. Prefer the observations that answer the actual symptom.

For a new ordinary timeout, use the current native controls documented in [Power settings in Windows 11](https://support.microsoft.com/en-gb/windows/experience/power-battery/power-settings-in-windows-11). Preserve separate screen-off and sleep values, and inspect battery versus plugged-in context rather than applying an entire energy-recommendation bundle.

### Modern Standby reports

Use [SleepStudy](https://learn.microsoft.com/en-us/windows-hardware/design/device-experiences/modern-standby-sleepstudy) only on a supported Modern Standby system. Report generation writes HTML and requires an Administrator command prompt; use the documented output path and smallest useful duration. An existing supplied report may suffice without generating another.

For applicable newer reports, follow their Active, Screen Off and Sleep segments. Bind the session to its local start time, power source and coverage before using component-activity or exit details. Microsoft warns that short sessions may lack detailed or overall reporting; its guidance calls for overall sessions longer than ten minutes for standby measurement. Read the actual report's coverage rather than treating a short missing session as a failure. A top-activity entry is an investigative lead, not proof that disabling that component is appropriate. Avoid copying the report's color into a blanket pass/fail verdict.

A sleep-behavior trial does not need a battery-drain experiment. Do not extrapolate short-sample discharge to overnight life, manufacture a percentage target, or compare AC and battery observations as equivalent conditions.

### Resume and the return path

[Microsoft's sleep/hibernate guide](https://support.microsoft.com/en-us/windows/experience/power-battery/shut-down-sleep-or-hibernate-your-pc) describes configurable lid/button actions and model-dependent wake methods. Establish the actual supported method before a trial; a power-button press can have a different effect under a different configuration. Preserve the user's existing security settings and return to the same saved work.

## Reading results conservatively

Keep four questions separate: what policy was configured, which request existed at capture time, which state transition occurred, and whether the user's work resumed. No single query answers all four. Correlate only observations from the same computer and relevant interval; retain unknowns where the tools lack coverage. Source documentation explains the tools, while the user's actual evidence determines the result.
