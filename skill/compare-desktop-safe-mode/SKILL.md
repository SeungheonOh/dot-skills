---
name: compare-desktop-safe-mode
description: "Compare one desktop symptom in normal startup, an explicitly verified Safe Mode session, and normal startup again. Use for a bounded macOS or Windows startup-software investigation with a safe test and a return path, not repairs, security bypasses or proof of a specific culprit."
---

# Compare a desktop symptom in Safe Mode

Deliver a small, interpretable comparison of one symptom across startup modes, then return the computer to its intended normal session. The useful result is evidence about where the symptom occurs, including whether the comparison was valid. Entering Safe Mode is an intermediate step, not a repair or a successful diagnosis by itself.

Use when the user wants to narrow an ordinary desktop problem that may depend on startup-loaded software. This workflow changes the temporary boot environment without intentionally removing applications or disabling a list of services. It does not identify a culprit by elimination, perform a clean boot, investigate compromise, recover deleted work, repair disks, reinstall an OS or modify persistent boot configuration.

Route a request to stop a named app opening at login to [startup preferences](../configure-desktop-startup-apps/SKILL.md). Use [frozen-app recovery](../recover-unresponsive-desktop-app/SKILL.md) to preserve a live application session before considering wider interruption. [System Restore](../restore-windows-system-state/SKILL.md) changes historical Windows configuration; it is not the same as observing a restricted startup session.

## Decide whether this comparison can answer the question

Resolve the following from available evidence; ask only for missing facts that affect safety or interpretation:

- Exact computer, OS version, user account and startup installation; Apple silicon versus Intel for a Mac
- Specific symptom, trigger, expected result, frequency and recent directly observed occurrence
- A harmless repeatable action that demonstrates it, plus the input file or device it needs
- Whether that action depends on network access, specialized graphics, audio, third-party fonts, device drivers, assistive technology or a background service
- Whether normal startup is usable and whether a normal restart alone has already been tried, with its result
- Authority for the diagnostic startup transitions and the chosen check, including interruption of current work
- Other users, active transfers/jobs, reliable power and a realistic local sign-in/observation route
- Whether the machine is managed, and any owner restriction on diagnostic startup

Do not run a destructive failing operation merely to obtain a baseline. A payment, message send, upload, firmware change or destructive export is not a harmless probe. Choose a noncommitting observation if it meaningfully exercises the symptom; otherwise report why a Safe Mode comparison cannot safely answer this request.

Consider validity before rebooting. If the complaint is that a USB audio interface fails during recording, a mode in which that interface is unavailable cannot demonstrate recovery. If the symptom needs a remote service, an offline failure is not a useful comparison. A symptom that appears once a month cannot be ruled out by a minute without it. Agree a task-relevant observation opportunity and keep non-reproduction narrower than a claim of absence.

A simpler already-authorized normal restart may provide a useful baseline. Do not add one automatically when preserving a transient condition matters or another interruption is costly. Record whether the baseline is direct, owner-reported or unavailable. Without a credible normal-mode occurrence, the outcome can still document startup access but cannot establish a mode-dependent difference.

## 1. Prepare the return path before changing startup mode

Save reachable work through the application's ordinary route, confirm its destination and stop only approved interruptible activity. Avoid treating autosave, an open tab or a reconnecting terminal as proof that the current session will survive. Check other signed-in users and do not interrupt their work under a single-user request.

Arrange local attendance or an actually available out-of-band observation route. Do not assume the existing remote-control app, network, keyboard helper or accessibility service will work after diagnostic startup. An owner can report the visible state, but label that evidence accordingly. If the sole access route is at risk and nobody can operate the computer locally, stop at a prepared plan. Do not install another remote agent to work around this boundary.

Keep credentials owner-controlled. Microsoft's [Safe Mode sign-in guidance](https://support.microsoft.com/en-us/windows/security/identity-signin/troubleshoot-problems-signing-in-to-windows) says that a password is required for this sign-in route; PIN and biometric options are unavailable. Confirm the owner has a usable supported sign-in method without asking them to reveal it. A PIN that works today is not sufficient readiness evidence. Do not reset an account, disable Windows Hello or change authentication policy as preparation.

For an encrypted Windows device, ensure the owner can retrieve and enter the appropriate recovery key if prompted. Do not collect, photograph, store or type a password or recovery key. Keep sign-in and protected recovery entry with the owner. Do not disable encryption, Secure Boot, firmware protection or endpoint security to make the trial possible. Managed-device restrictions are an escalation to the responsible owner, not an obstacle to bypass.

Read the current official route for the observed system. Diagnostic startup can alter the environment; it is not a forensic read-only snapshot. On macOS in particular, [Apple documents](https://support.apple.com/en-us/116946) startup checks and cache clearing as well as restricted loading. Explain those effects if they matter to preserving evidence. Stop for a separate investigation when a pristine incident state is required.

Use existing approval when it covers the same machine, transitions and diagnostic effects. Obtain the missing decision when interruption, scope or a security-sensitive action changes. Inspect unexpected warnings before continuing and follow applicable action-time confirmation requirements. Merely requesting troubleshooting does not authorize every control adjacent to Safe Mode.

## 2. Record a compact baseline and test plan

Keep a private note with these fields, not a complete system inventory:

| Stage | Boot evidence | Probe and dependencies | Result | Limit |
| --- | --- | --- | --- | --- |
| Normal before | How normal startup was established | Exact safe trigger and input | Symptom or no symptom | Direct, reported or historical |
| Safe Mode | Native evidence for the actual mode | Same probe, or why unavailable | Symptom, no symptom or not testable | Changed dependencies and duration |
| Normal after | Return-session evidence | Original probe again | Symptom or no symptom | Remaining uncertainty |

Define the symptom in observable terms, such as “the selected ordinary app closes before showing its empty workspace.” Avoid “computer broken” or “seems faster.” Record enough version and peripheral context to identify a changed condition without retaining unrelated software lists or personal document contents.

Keep the comparison narrow. Do not update an app, unplug its required device, delete caches manually, change the test document and switch boot mode together. If any condition must change, record it and decide whether the remaining result still addresses the original question. A newly appearing installer, migration dialog or access request is a blocker, not a test step to accept automatically.

## 3. Enter the intended diagnostic mode

### Windows

Use a normal documented entry into Windows RE. Microsoft's [recovery-environment page](https://support.microsoft.com/en-us/windows/experience/backup-recovery/windows-recovery-environment) describes Advanced startup from Recovery settings and Shift while selecting Restart. These routes interrupt the current session. Prefer the available supported route or an already visible recovery screen; this guide does not force repeated power interruptions or boot external media.

Follow [Windows Startup Settings](https://support.microsoft.com/en-us/windows/experience/startup-boot/windows-startup-settings): Troubleshoot > Advanced options > Startup Settings > Restart, then select the visibly identified Safe Mode option. Basic Safe Mode uses a restricted driver/service set; the Networking variant adds networking components. Choose only the variant justified by the agreed probe. Networking does not establish that this machine's remote access or required service will work.

Do not select debugging, command-prompt mode, driver-signature bypass or anti-malware disabling. If Startup Settings is missing, the selected installation is uncertain or the screen differs materially, stop and research that actual state. Do not substitute Startup Repair or System Restore.

After owner sign-in, confirm visible Safe Mode labeling and the intended installation/account. If the mode cannot be established, classify entry as unverified rather than infer it from a low-resolution display. Never send blind keystrokes across an unseen boot screen.

### macOS

Use [Apple's model-specific startup instructions](https://support.apple.com/guide/mac-help/start-up-your-mac-in-safe-mode-mh21245/mac). Identify the hardware first; do not guess from the laptop's appearance.

- Apple silicon: shut down normally, then hold the power button until startup options load. Select the intended startup volume, hold Shift and choose Continue in Safe Mode
- Intel: start or restart normally and immediately hold Shift until the login window

Let the owner handle any login, including a repeated login request. Do not choose another volume merely because its name resembles the intended one. A boot picker or Recovery utility window is not yet the diagnostic desktop.

Apple's [Safe Mode article](https://support.apple.com/en-us/116946) gives a stronger check than appearance: open System Information using Option with the Apple menu, select Software and inspect Boot Mode for Safe. An Intel firmware password can prevent Safe Mode entry; do not remove it. Some graphics, audio, sharing, network, accessibility and connected-device behavior can differ in this mode, so classify probe availability before interpreting its result.

If startup stalls, sign-in fails or observation is lost, preserve the last visible stage and obtain local observation. A remote timeout does not prove a hang or successful entry. Do not force power off, repeat blind startup gestures or change credentials to complete the comparison. If a normal supported exit is available, use it within the agreed scope; otherwise report the current access blocker and obtain the specific recovery decision.

## 4. Perform only the bounded comparison

Once entry is evidenced, inspect whether the required app, local input and dependency are available. Do not repair their absence during this trial. If the needed function is missing, mark the probe **not testable**, preserve the reason and proceed to normal-mode return when safe.

Perform the agreed safe trigger using the same account, app copy and input where possible. Record exactly what occurred and the observation window. Distinguish the original symptom from a different diagnostic-mode limitation. A missing font that changes a page layout, for example, is not proof that the original layout fault was repaired.

Do not use the session for unrelated browsing, account enrollment, installation or normal productivity. Safe Mode is not a sandbox and does not authorize running suspicious software. Do not dismiss a security alert or bypass a licensing requirement to get a cleaner comparison. If the probe unexpectedly writes data or resumes a submission, stop before proceeding and resolve the new effect.

Capture the smallest useful evidence: native mode, trigger, result and relevant limitation. Avoid full desktop recordings, account pages, recovery screens, crash dumps and broad logs. Obtain appropriate approval before transmitting diagnostic material to support or another recipient.

## 5. Return to normal startup and repeat the meaningful check

Save any authorized work created during the trial. Use a normal restart without the diagnostic-entry gesture or selection. Both vendors document a normal restart as the ordinary exit route. Confirm the intended account and installation after owner sign-in, then establish normal-mode evidence and needed access before calling the trial complete. On a Mac, Boot Mode in System Information can distinguish the return state; on Windows inspect the returned session and whether Safe Mode labeling persists rather than rely on remote reconnection alone.

If Windows continues entering Safe Mode, do not repeatedly restart or apply boot-editing recipes. Record the current state and investigate whether a pre-existing persistent boot selection is involved. This workflow did not authorize editing System Configuration, the boot database, registry or security settings. Return the exact blocker and the separate decision needed. Similarly, an unexpected boot-volume selection or recovery screen on a Mac is not normal return.

When normal startup is established, repeat the original safe probe under its original conditions. If the user must defer that probe, keep return-to-normal and symptom verification as separate statuses. Do not leave the user in diagnostic mode merely because the first probe looked successful.

## Interpret without overclaiming

| Evidence | Supported conclusion | Unsupported leap |
| --- | --- | --- |
| Original symptom occurs in normal mode, not in a valid Safe Mode probe, and returns afterward | Behavior differs across the observed startup conditions; investigate startup-dependent components next | A particular login item or driver is proven guilty |
| Original symptom occurs in both valid probes | This restricted startup did not remove the observed symptom | Hardware failure is established, or OS reinstallation is required |
| Safe Mode cannot exercise the original function | Comparison is inconclusive for that function | The absence of the original error is a pass |
| Symptom disappears in Safe Mode and remains absent after return | Currently not reproduced under the checked conditions | Permanent repair or a specific cache/driver cause is established |
| No reliable initial occurrence or insufficient observation opportunity | Evidence is limited to the sessions actually observed | Safe Mode disproved an intermittent fault |

These are conservative diagnostic interpretations, not vendor guarantees of causal isolation. Startup mode changes many conditions at once, and a restart itself can change transient state. Select the next investigation from the observed difference, not from the name of an unfamiliar startup component.

## Finish with the result and remaining decision

Return the target system, safe-mode variant, mode evidence, probe results for each stage, confounders, owner-reported versus direct observations and verified final startup state. Use a clear status: **prepared; not started**, **comparison completed; normal session restored**, **comparison inconclusive; normal session restored**, or **interrupted/blocked at the named stage**. A pending return is not completion.

If further work is warranted, propose one bounded step: inspect the relevant ordinary login registration, build a reproducible app report, or ask the managed-device owner about the restricted component. Do not automatically disable half the services, uninstall software, create a new account, clear caches, update drivers or reinstall the OS. A diagnostic result does not authorize remediation.

## Fictional illustration — not executed

A fictional personal laptop has a notes application that closes before its blank workspace appears in normal startup. The user permits a diagnostic restart and a normal return; the probe needs no network or special device. The owner can operate sign-in locally. The proposed comparison records the app identity and uses its blank workspace rather than a private notebook.

Suppose invented observations are: the failure occurs before the trial, the app opens in an explicitly confirmed Safe Mode session, and the failure returns after a verified normal restart. The appropriate result is a startup-condition-dependent difference, with the normal session restored. It does not identify the recently installed tray helper as the cause and does not authorize removing it.

For a second hypothetical input, the complaint instead concerns recording through an external audio device that is unavailable in Safe Mode. The same workflow would label that probe untestable and return normally. It would not count the missing recording error as success or install a driver during the comparison.

These examples are original hypothetical reasoning. No device was accessed, restarted, signed into, tested or repaired. Primary sources were checked on 2026-10-20; actual UI navigation, mode transitions and functional results require later authorized use.
