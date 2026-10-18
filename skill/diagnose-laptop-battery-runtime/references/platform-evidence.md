# Native evidence for a bounded battery-runtime diagnosis

These are official documentation starting points reviewed on 18 October 2026. Match the actual OS, hardware and displayed fields before using them. The references support platform behavior; the workflow's interval accounting and comparison rules are an original diagnostic method, not a manufacturer certification. No command or device procedure was executed for this document.

## macOS

### Capacity, condition and cycle count

- [Apple: About battery health management in Mac laptops with Apple silicon](https://support.apple.com/en-us/102589) defines maximum capacity relative to the battery when new, describes health-management effects, and notes possible maximum-capacity recalibration after an update. Its applicability is explicitly Apple silicon. Record the observed estimate without treating a single change as measured chemical damage.
- [Apple: Determine battery cycle count for Mac laptops](https://support.apple.com/en-us/102888) explains that a cycle accumulates use equivalent to the battery's capacity rather than counting each connection to power. It shows the System Information > Hardware > Power route and lists model-specific maximum cycle counts. Match the exact model; do not apply one threshold to every laptop or infer a remaining number of months from cycles.

Use the native Battery Health condition and capacity information where the selected release exposes them. A condition label, capacity estimate and cycle count are separate observations. An unavailable value stays unavailable; do not install a third-party monitor merely to fill a field.

### Charging policy

[Apple: About Optimized Battery Charging and Charge Limit on Mac](https://support.apple.com/en-us/102338) distinguishes adaptive delayed charging from an explicit charge limit. The documented Charge Limit requires macOS Tahoe 26.4 or later and Apple silicon; the available setting is 80–100%. The battery menu distinguishes a hold from a reached limit, and a supported one-time Charge to Full Now action may be available. Inspect the actual version's UI rather than assuming every Mac has the same controls. A diagnostic request alone does not authorize changing these settings.

### Activity and history

[Apple: View energy consumption in Activity Monitor](https://support.apple.com/en-ca/guide/activity-monitor/actmntr43697/mac) defines Energy Impact as relative current app consumption and 12 hr Power as average impact over the past twelve hours or since startup. Record that window when comparing evidence. The pane also exposes battery and power-source information depending on hardware. Do not convert these relative values to W or Wh, mistake an app's Preventing Sleep flag for a measured active-use drain, or treat a historical average as an instantaneous reading.

## Windows

### Existing battery information and report creation

[Microsoft: Caring for your battery in Windows](https://support.microsoft.com/en-us/windows/experience/power-battery/caring-for-your-battery-in-windows) describes the native battery-report route, including elevation, a locally saved HTML file and relevant installed-battery/usage sections. It also warns against frequent deep discharges and directs users to stop using a device whose battery expands beyond its enclosure. Do not bypass a denied elevation or collect an administrator credential. Existing visible information or an owner-generated report may still support part of the diagnosis.

[Microsoft: Powercfg command-line options](https://learn.microsoft.com/en-us/windows-hardware/design/device-experiences/powercfg-command-line-options#batteryreport) documents `powercfg /batteryreport`, an optional `/output file_name`, an XML output form and a `/duration days` form. This report command writes an artifact; it does not itself perform a controlled discharge. Choose a fresh absolute output filename in the approved private folder, check that it does not already exist, and verify the returned location and file identity before reading it. Keep the literal chosen path quoted correctly for the current shell. A report command supplied as documentation is not evidence it ran.

Read the report's actual range and retained sections. Requesting a duration does not justify claiming that missing historical observations exist. Preserve blank capacity/cycle values and gaps. Separate Installed batteries, Recent usage, Battery usage, capacity history and life estimates according to the fields actually present. Do not turn a generated report or an extrapolated life-estimate table into a completed endurance trial.

Do not substitute `powercfg /energy` for a matched workload comparison. The same Microsoft reference states that its energy analysis should run with the computer idle and without open programs/documents. A report intended for that condition does not establish the energy used by the user's active export or meeting. This guide does not require that command, request overrides, power-plan resets or a trace collection.

### Capacity arithmetic and charging policy

[Microsoft: Check Surface battery capacity](https://support.microsoft.com/en-us/surface/battery/how-to-check-your-surface-battery-capacity) uses full-charge capacity divided by design capacity for the reported remaining-capacity percentage. Its tools, model applicability and replacement guidance concern Surface. The arithmetic is useful when equivalent fields and units are available; do not generalize Surface service thresholds, install its utilities on another brand, or infer replacement eligibility from a generic Windows report.

[Microsoft: Use Smart charging in Windows](https://support.microsoft.com/en-us/windows/experience/power-battery/use-smart-charging-in-windows) explains that a supported device may stop short of 100% and that implementation depends on its manufacturer. Match the manufacturer's existing installed controls and documentation. Do not promise a universal Windows charge-limit switch or overwrite a deliberate limit to make a diagnostic graph look fuller.

For current app/battery-use views, inspect Settings > System > Power & battery where supported and read the selected time range. [Microsoft: Battery saving tips](https://support.microsoft.com/en-us/windows/experience/power-battery/battery-saving-tips-for-windows) describes supported energy-saving, display and app-background choices. Those choices can change functionality; apply only the specific change the user wants and retain the task's completion/usability check. Do not equate a top-ranked app's historical usage share with waste or with a number of charge percentage points.

## Source and observation limits

- A model support page establishes a documented interpretation, not the selected machine's observed condition
- The current capacity estimate, current charge and a permitted charging ceiling are different quantities, even when all display the same percentage
- A report's missing field is not zero, a future timestamp is not a valid baseline, and history for a replaced pack must not silently continue into its successor
- Keep raw diagnostics local and preserve minimal field/interval evidence in the handoff; full reports can expose device identity and activity history
- For inaccessible or unsupported evidence, return the exact limitation and the next supported observation rather than installing a utility or running an unrelated diagnostic suite
