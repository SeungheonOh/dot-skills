---
name: configure-mac-ups-shutdown
description: "Configure native UPS-triggered shutdown for one personal Mac desktop with an already installed USB UPS, reconcile its reported power state and shutdown conditions, and verify the saved policy. Use for local outage-response setup, not UPS installation, battery testing, server orchestration, electrical work or a guaranteed recovery certification."
---

# Configure a Mac's response to UPS battery power

Deliver a saved native shutdown policy for the intended Mac and UPS, with a short record of the enabled conditions, observed device state and remaining verification limits. Keep electrical backup, USB communication, saved shutdown settings, an actual shutdown and successful later startup as separate claims. A UPS appearing in a USB list does not prove that it supplies the Mac's power or that the Mac will finish shutting down before the battery is exhausted.

Use this for one personal Mac desktop whose UPS is already installed and whose model supports the native route. Do not extend the workflow to a Mac laptop, Windows/Linux policy, a network UPS service, multiple-host shutdown, virtual-machine sequencing, managed servers or an unattended production system. [Apple's UPS guide](https://support.apple.com/en-za/guide/mac-help/mchlp2987/26/mac/26) describes the desktop USB route and notes that some UPS units simply run until their batteries are exhausted. Establish the actual capability rather than assuming every unit can signal shutdown.

Use [battery-runtime diagnosis](../diagnose-laptop-battery-runtime/SKILL.md) for a laptop's active-use endurance, [sleep-prevention diagnosis](../diagnose-desktop-sleep-prevention/SKILL.md) for sleep/wake behavior, and [versioned backup setup](../configure-versioned-file-backup/SKILL.md) for retained file history. A shutdown policy does not create a backup, and a backup does not establish an outage response.

## Establish the intended policy and its limits

Resolve only what affects the setup:

- Exact physical Mac, macOS version and intended user context; distinguish it from a remote session or guest system
- UPS make/model, the existing USB data connection, and the owner's confirmation of which installed battery-backed outlets supply the Mac and required storage
- Native UPS recognition, current power-source state, available charge/runtime fields and any visible fault or service indication
- Existing shutdown conditions and whether vendor software, a script or another service already owns the outage response
- Desired behavior during a short outage versus a sustained outage, accepted interruption of open work, and the selected conditions or the decision still needed
- Whether the request covers advice, saving/activating the policy, or separately reviewing existing outage evidence
- A local person and normal startup/sign-in route if an interruption occurs, plus the requested final state

Use available settings and the user's existing plan before asking. Do not require a full equipment inventory for a known single-desktop setup. Ask a focused question if the desired shutdown timing is unsettled; changing when unsaved work may be interrupted is not merely a cosmetic preference. A request to inspect does not authorize activating a new policy. An explicit setup request can authorize the stated ordinary settings without an extra generic approval round.

This workflow does not move power cables, open equipment, disconnect mains, operate a breaker, change UPS output groups, run a self-test, drain a battery or install software. Leave physical commissioning to the owner and applicable model instructions. If reported heat, swelling, leakage, smoke, damage, overload or other concerning conditions arise, stop setup and use the manufacturer's safety/support route. Do not seek extra runtime measurements from suspect equipment.

## 1. Bind the communication and power paths

Inspect the native System Information USB listing and the UPS-related settings. Record a minimal stable identity sufficient to distinguish the device; avoid putting full serial numbers or unrelated USB devices in a public report. [Schneider Electric's native-shutdown guidance](https://www.se.com/es/es/faqs/FA159690/) uses the USB report to establish communication for supported Back-UPS/Smart-UPS models. Treat that as communication evidence, not a battery-capacity or electrical-installation check.

Keep the two paths explicit:

1. The installed electrical path supplies the Mac and any dependent powered storage during an outage, based on owner/model evidence
2. The USB data path exposes the intended UPS to this Mac's power management

An unrelated USB charging port, a same-named unit or a device assigned to a guest must not stand in for the intended host connection. Do not reconnect or detach devices to discover identity when that could interrupt storage or another shutdown owner. Ask for the missing local observation instead.

Read the currently reported source state before editing. If the system is already on UPS battery power, preserve the current protection and the user's work; do not start an experiment or relax thresholds to keep the session alive. Pause configuration until stable input power is evidenced, unless a separately authorized urgent response is already defined. Do not infer normal mains from a lit screen or from the remote connection still working.

If native UPS options are absent, distinguish unavailable support, no data connection, ambiguous identity and management restrictions. Check the exact model and OS documentation, then stop at the evidenced boundary. Do not force hidden preferences, modify a driver or install a second power manager merely to expose the controls. If an existing vendor service owns shutdown, leave it intact and resolve whether a native-policy change is appropriate before proceeding.

## 2. Translate the request into distinct shutdown conditions

Read the actual controls and retain each condition's enabled state, numerical value and units. Do not equate these three meanings:

| Condition | Meaning to preserve | Decision it cannot settle alone |
| --- | --- | --- |
| Time already running on UPS battery | Elapsed battery-use duration before shutdown is triggered | How much reserve remains at that point |
| Estimated time remaining on the UPS | A threshold applied to a reported runtime estimate | A guaranteed amount of time for apps and storage to finish |
| UPS battery charge level | A reported percentage threshold | Minutes remaining or the capacity of the battery when new |

[Apple's published pmset manual](https://github.com/apple-oss-distributions/PowerManagement/blob/main/pmset/pmset.1), particularly its UPS-specific section, documents these separate conditions. Match any labels and supported readings to the installed OS; the published manual is not a substitute for current device support. An unavailable runtime field is unknown, not zero or infinite. Do not derive a runtime guarantee from nominal VA, a charge percentage or a previous low-load episode.

When multiple conditions are enabled, the first reached triggers shutdown; they are not an all-conditions requirement. Review inherited enabled conditions along with the one the user wants changed. Explain an earlier competing trigger before enabling a seemingly later one. Preserve unrelated power settings and resolve whether any existing condition should change rather than silently disabling it. This first-condition behavior is documented in [Apple's UPS setup instructions](https://support.apple.com/en-za/guide/mac-help/mchlp2987/26/mac/26).

Choose values from the user's intended response and applicable model guidance, considering known shutdown needs and reserve uncertainty. Do not prescribe a universal five-minute delay, ten-percent threshold or full-discharge calibration. A low reserve, stale estimate or unknown shutdown duration may prevent supporting the requested delay. Return a proposed policy with that gap rather than claiming it is safe. If the user only wants an already specified supported value saved, keep this proportional; do not demand a discharge test first.

For each condition, write one concise before/proposed row, including why it is changing or staying unchanged. Keep a disabled condition distinct from an enabled condition with a displayed value. Do not infer the meaning of zero, a slider endpoint or a command-line sentinel from another setting. Use the native enabled control and actual labels.

Startup after an outage is a separate setting and acceptance requirement. [Apple's desktop Energy reference](https://support.apple.com/en-za/guide/mac-help/mchlp1168/26/mac/26) lists startup behavior separately from UPS options and notes hardware-dependent availability. Preserve the existing restart/startup policy. Do not promise that enabling UPS shutdown will also restore power to peripherals, start the Mac or unlock the user's session.

## 3. Save only the intended native change

Recheck device identity, stable power, current conditions and active work immediately before saving. Keep the captured baseline available for a bounded reversal. Explain that the saved conditions govern future outages and can interrupt work; any deliberate test or immediate shutdown remains a separate action.

Open the version-appropriate native Energy or Energy Saver pane, then UPS Options. Use the actual interface to set the accepted condition values and enabled states. Do not change sleep, wake-for-network, automatic startup, lock, encryption, remote access or an unrelated battery setting along the way. An unavailable or managed control is a blocker, not a reason to edit preference files directly.

If authentication is required, have the owner complete the protected prompt. Never collect or place an administrator password in chat, a command or the receipt. New privilege, unexpected permissions, software installation or access expansion is not included in a routine threshold edit. Stop and identify the exact additional action instead of working around a denial.

Save using the supported control, close the pane and reopen it. Compare every relevant enabled state and value with the accepted policy. A closed dialog or absence of an error is not readback. If a value is rounded or constrained, report the actual supported setting; do not claim the requested number was retained. Do not repeatedly toggle controls when the resulting state is uncertain.

## 4. Verify configuration without manufacturing an outage

Verify the smallest sufficient result for a configuration request:

- The same Mac recognizes the intended UPS and exposes usable native policy controls
- The current power-source observation belongs to that UPS and is timestamped
- The saved enabled conditions and values match the accepted policy after reopening
- The interpretation accounts for every enabled condition, including an earlier inherited trigger
- The receipt identifies who can normally start/sign in to the Mac after an interruption and what remains unobserved

When an authorized terminal is already available, the installed manual can support additional read-only corroboration: pmset -g ups displays UPS thresholds, and pmset -g batt displays power-source status. These are distinct queries; do not substitute general power settings for UPS threshold evidence. Check the installed documentation and inspect the returned fields rather than assuming every device supplies every value. No elevation, shell write command, continuous logger or state-changing pmset option is required for this corroboration. The published manual also describes settings as system-wide and persistent, so do not present the change as applying only to the currently signed-in person's work.

Keep observed, owner-reported and unavailable evidence separate. USB enumeration plus saved thresholds supports configuration, not end-to-end shutdown. A normal manual shutdown would exercise a different trigger. Lost network access could reflect a router losing power rather than the Mac shutting down. A device self-test does not, by itself, establish the host's actual response.

Do not induce a power failure, invoke shutdown, cut an outlet or run down the UPS to improve the receipt. If the user requires a live outage-response exercise, return the missing scope and request a separately planned, model-specific owner-led procedure with a safe recovery route. Do not silently substitute configuration readback for that requested acceptance. Existing independently supplied outage records can be reviewed without recreating the event: match the Mac/UPS, policy version, source transition, triggering condition and observed host result. Keep unsupported links in that chain explicit.

## Recovery and completion

- **Device present but no usable policy or telemetry:** report recognition separately; preserve protection and resolve exact model/OS support rather than calling setup complete
- **Conflicting native and vendor ownership:** hold the change; do not stop or uninstall an existing shutdown service under this request
- **Saved values differ or change back:** inspect current authority and management; restore only the recorded changed fields when still authorized, without overwriting a later user decision
- **A real outage starts during setup:** stop configuration, preserve work through the owner's established response and avoid defeating the existing shutdown protection
- **Connection disappears or startup is unavailable:** retain the last known state; obtain local observation rather than issuing blind power actions or claiming success
- **User rejects the proposed interruption behavior:** leave the original policy intact and return the unresolved choice

Restoring previous settings does not undo an interruption or recover unsaved work. Do not use Reset Defaults, remove all protection, enable remote startup or suppress alarms as a rollback. Continue only while a supported next read or authorized correction can resolve the configuration; stop at a new hardware, management, permission or live-test boundary.

Return a concise private handoff containing the Mac/OS and minimal UPS identity; relevant power/data-path evidence; before/final enabled conditions and units; first-trigger interpretation; time and outcome of readback; unchanged separate startup behavior; the exact verification limit; and how to revisit the same native controls. Save a requested receipt to the approved location and read it back. Do not upload hardware inventories or diagnostics to a vendor without authorization.

Use **prepared; not applied** for a proposal, **configured; outage response unobserved** for supported saved/read-back settings, and **blocked** for unresolved identity, support or authority. If existing evidence establishes a real event, describe that particular event and its limitations rather than certifying future reliability, battery health, electrical safety or recovery of all work.

## Original fictional illustration, unexecuted

A fictional owner has a personal Mac desktop and an already installed USB UPS. They request an elapsed-battery-time condition of eight minutes while retaining an existing thirty-percent charge condition. These numbers are invented user choices, not recommendations. A supplied snapshot hypothetically shows a recognised UPS and normal input power.

The prepared interpretation would say that the retained charge condition can trigger shutdown before eight minutes. It would not promise eight minutes of continued work or infer a remaining duration from thirty-percent charge. If that earlier response is incompatible with the owner's intent, the policy decision remains open; the workflow would not silently disable the retained condition.

Suppose a later hypothetical readback shows both accepted conditions saved. That would support configuration only. With no outage or host-transition evidence, the result would be “configured; outage response unobserved.” A missing runtime estimate would stay unavailable. Automatic startup would remain a separate, unchanged question.

All people, devices, values and observations in this illustration are fictional. No computer, UPS, application, command, setting, power interruption or shutdown was accessed, executed or tested for it. The operational steps describe later authorized work, not completed runtime validation.
