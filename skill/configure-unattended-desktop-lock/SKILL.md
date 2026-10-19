---
name: configure-unattended-desktop-lock
description: "Configure a bounded native idle-lock policy for an existing Mac or Windows desktop account, distinguish the inactivity trigger from authentication-on-return, and verify a user-controlled return to the same session. Use for unattended-session locking, not password enrollment, device recovery, remote-session policy, fleet administration or full device-security certification."
---

# Make an unattended desktop require authentication on return

Deliver the requested local idle-lock behavior and a short, evidenced settings receipt. Connect the correct computer and account, the inactivity trigger, any authentication grace period, the observed locked state, and the owner's safe return. A dark monitor, decorative screen saver or saved timeout alone is not evidence that the desktop requires authentication.

Use an existing signed-in account on a personal Mac or Windows computer with a working, owner-controlled unlock method. This is a native settings workflow, not an account-recovery procedure or a way to lock out another person. Do not enroll credentials, change passwords, enable automatic login, alter disk encryption or implement a script that simulates locking.

[Sleep diagnosis](../diagnose-desktop-sleep-prevention/SKILL.md) establishes system sleep and wake behavior and explicitly excludes lock/password changes. [Standard-user setup](../create-standard-desktop-user/SKILL.md) creates a separate identity. [Device-handoff records](../prepare-device-handoff-record/SKILL.md) document a transfer; locking a session does not prepare a computer for transfer or remove its accounts.

## Resolve the target behavior

Use the request and visible settings to establish only what changes the decision:

- Exact computer, installed OS/version, ordinary signed-in account, and whether local or remote controls are being observed
- Desired inactivity interval and whether it applies on battery, external power or both
- Whether authentication should be required immediately when the trigger occurs or after a deliberately selected grace period
- Existing unlock methods and a person able to use them locally without revealing secrets
- Relevant managed settings, current display/screen-saver/sleep timings, and work that must continue
- Whether the request is explanation, configuration only, or configuration plus an observed idle-return check
- The available observation window and requested final session state

Ask about a missing time interval rather than silently choosing a security standard for the user. A simple request with an exact interval does not need a broad security interview. Distinguish “lock after five idle minutes” from “turn the screen off after five minutes” and “ask for a password five minutes after the display turns off.” These specify different transitions.

If the user needs a guaranteed maximum exposure interval across presentations, media playback, remote-control activity and hardware presence detection, do not promise it from one consumer idle setting. Establish the precise condition that can be configured and checked. Managed enforcement and security certification belong to the responsible administrator.

## 1. Capture the small baseline and recovery route

Inspect the native settings for this account on this computer. Record current trigger intervals, sign-in/grace behavior, power-source differences and visible management restrictions. Include an existing automatic-unlock feature only when it affects interpreting the check. Do not collect biometrics, password hints, recovery details or unrelated users' settings.

Keep these states separate:

| State | What it establishes | What it does not establish |
| --- | --- | --- |
| Screen saver is visible | A visual idle action occurred | Authentication is required to return |
| Display is off | The display is not presenting the desktop | Session lock or system sleep |
| System slept | A power transition occurred | The configured sign-in requirement was enforced |
| Native lock/sign-in boundary is observed | A locked-session boundary was reached | Automatic inactivity was its cause |
| Owner unlocks and returns | This owner could resume this session | Every unattended condition will lock on time |

Save work before the trial and check for calls, presentations, remote assistance, transfers or applications whose operation may be interrupted. A screen lock is not a promise that every background job continues normally. Do not close apps or cancel work to manufacture a clean idle period without the relevant authority.

Arrange the supported local return path before changing a timeout. If locking may remove the assistant's only connection, an available local owner and supported handoff are prerequisites for a live trial. Do not create remote access, weaken authentication or leave a password in an automation to solve that problem. Configuration can be prepared without a trial when no safe local return is available.

The owner must already have a usable unlock method. If they are unsure of it, resolve that prerequisite through their ordinary secure route before locking; do not test guessed passwords, reset credentials or create a replacement account. Existing accessibility and keyboard-input needs at the lock screen must remain usable.

## 2. Approve the exact security-setting change

Changing authentication-on-return or the idle-lock security policy requires the applicable action-time confirmation. State the computer/account, previous and proposed relevant values, any grace interval, and the expected interruption/return method. A request to inspect the settings does not authorize changing them. Bundle the foreseeable security changes and trial so the user can decide once on the actual plan.

An ordinary display timer and a sign-in requirement can appear in neighboring controls but are not the same permission decision. Include the security effect when a timer change is being used to change lock timing. Do not conceal a longer unlocked interval as a cosmetic preference or treat a more restrictive setting as exempt from confirmation.

Protected credential entry and submission remain with the owner through the supported secure handoff. Never ask for a password or PIN in chat, record it, or use another user's administrator credential to demonstrate the result. If a changed flow introduces an additional security choice, hold that choice rather than accepting it automatically.

Respect a managed or unavailable control. Do not change Group Policy, registry values, configuration profiles or account-management enrollment to reveal a missing setting. Installing a lock utility, pairing a new phone, enabling presence sensors or changing biometric enrollment is outside this bounded workflow.

## 3. Apply the supported native route

Use current official guidance matched to the installed release. Sources below were inspected on 2026-10-19; documentation may default to a newer release than the selected computer. Follow the visible supported interface rather than forcing a remembered path. Apply only the relevant platform branch and retain unrelated settings.

### macOS: pair an idle trigger with the return requirement

Open System Settings → Lock Screen. Read the applicable battery and power-adapter display-off intervals. Apple's [Lock Screen settings reference](https://support.apple.com/en-euro/guide/mac-help/mh11784/27/mac/27) documents these controls separately from the authentication delay. Set only the approved trigger and power-source scope.

Use the return-authentication control to set the approved delay following screen-saver activation or display-off. [Apple's password-after-wake guide](https://support.apple.com/guide/mac-help/require-a-password-after-waking-your-mac-mchlp2270/mac) describes this delay. An immediate requirement after the trigger avoids adding a separate grace interval; a nonzero delay must be included in the result, not hidden behind the display-off time.

If the chosen trigger is a screen saver instead of display-off, use its actual inactivity control for the installed release. [Apple's current screen-saver reference](https://support.apple.com/en-ie/guide/mac-help/mchlp1227/27/mac/27) places its controls under Wallpaper → Screen Saver; other releases can differ. Keep the existing safe visual choice when possible. Do not select a personal-photo collection or download decorative content as part of setting a lock interval.

Reason from the earliest applicable enabled trigger and its actual return requirement. Do not simply add a screen-saver interval to a display-off interval: they are alternative events, not necessarily consecutive timers. Conversely, a delay after the trigger is additional exposure in the configured model. Treat that model as a proposed expectation until the actual inactivity path is observed.

If the return setting is unavailable, inspect the visible reason and relevant official guidance. Apple's [automatic-login article](https://support.apple.com/en-au/102316) notes a restriction when iPhone Mirroring is configured for automatic authentication. Do not disable that feature, remove a device association or alter another authentication arrangement to unlock this control without a separate exact decision.

### Windows: configure an explicit idle-lock path

For a supported screen-saver-based idle lock, use Settings → Personalization → Lock screen → Screen saver. Choose an existing built-in saver, set the approved Wait interval, enable the resume sign-in checkbox, then save. [Microsoft's screen-saver instructions](https://support.microsoft.com/en-us/windows/configure-a-screen-saver-in-windows-a9dc2a0c-dc8e-9161-d270-aaccc252082a) document the separate timer and resume requirement. A selected saver without that requirement does not meet this task. Preview is not an idle-lock check.

Inspect existing display/sleep timing and the applicable wake sign-in setting rather than assuming this new path covers every earlier power transition. If the computer sleeps before the saver can trigger, verify the wake-authentication path too or report the uncovered condition. Do not disable sleep or lengthen every power timeout merely to make the saver easier to observe. Microsoft's [device-security guidance](https://support.microsoft.com/en-us/security/securing-your-device) describes sleep and return sign-in together; use the settings actually offered on this device.

Windows configurations differ. If an appropriate return control is missing or managed, report that boundary instead of changing Windows Hello, removing a PIN or enabling password login to make the UI match a tutorial.

Dynamic lock is a different trigger. [Microsoft's sign-in-options reference](https://support.microsoft.com/en-gb/accounts-billing/security/sign-in-options-in-windows) describes locking after a paired phone leaves Bluetooth range, with a possible delay of up to about a minute after that range condition. That is not an inactivity deadline or immediate detection of someone leaving a chair. Do not introduce it as a replacement for the requested timed lock, or claim that leaving the phone beside the computer satisfies its trigger. Preserve an existing setting unless its exact change is authorized.

### Read back before trial

Reopen the relevant controls and verify the retained values for the correct account and power source. Compare only the intended delta with the baseline. If a save timed out, inspect current values before trying again. Do not repeatedly toggle controls or overwrite a concurrent user/administrator change.

Readback can establish configuration. It cannot establish enforcement. Keep an interrupted save, missing return control or conflicting managed value explicit.

## 4. Observe an actual idle boundary and safe return

A manual lock can establish the owner-controlled return route when requested, but it does not verify the timer. On Mac, Apple's [lock-screen guide](https://support.apple.com/guide/mac-help/lock-the-screen-of-your-mac-mchl8e8b6a34/mac) documents the Apple-menu lock action and existing unlock methods. On Windows, use the supported native lock action for the selected session. Do not substitute logout, restart, closing the lid or disconnecting a remote window.

For the authorized inactivity check:

1. Reconfirm work is saved, the power source and account are correct, and the local owner is ready to resume
2. Record the final intentional input time, the saved trigger/grace values and a reasonable observation window covering those values
3. Stop automated mouse/keyboard input. Do not continuously click, poll with UI actions or send keepalive keystrokes during the idle interval
4. Observe or obtain the owner's attributed report of the visual transition without treating it alone as proof of lock
5. After the relevant interval, have the owner attempt an ordinary return and establish the native authentication boundary before completing their existing unlock method
6. Verify return to the same account/session and that the agreed work remains available; reopen settings to confirm the retained configuration

Record observer effects. Remote input, a presentation or an app preventing the expected visual transition can make a trial inconclusive. Keep the original condition visible rather than stopping everything and claiming a general fix. Investigate an evidenced blocker only within its separately authorized scope.

Automatic biometric or wearable unlock can make a password field unnecessary. A desktop that reappears while the authorized owner is present is therefore ambiguous by itself. Use the native locked-state/unlock indication and the owner's observation to distinguish authentication from an unlocked resume. Do not disable an existing unlock method merely to force a password prompt. If the boundary cannot be observed reliably, report that limit instead of declaring success or failure.

Test each requested power condition only when it is safe and practical. An AC-only observation does not verify battery behavior. A temporary short timeout, if separately approved, establishes only that temporary condition; restore and read back the intended value, leaving its full interval unverified until observed. Do not invent a successful five-minute result from a one-minute demonstration.

Do not prolong observation indefinitely. Stop at the requested evidenced condition, an unavailable local return route, a managed boundary, or a specific additional decision. If a return fails, let the owner use their established recovery method; do not reboot, reset authentication or unlock as another account.

## Recovery and final receipt

- **Display dims but desktop returns without authentication:** distinguish an unexpired grace period, absent return requirement and automatic authorized unlock before changing anything
- **Idle trigger never occurs:** record the original condition and possible observer/app interference; do not simulate input cessation by terminating work or disabling services
- **Settings revert:** report the actual retained value and visible management/concurrent-change evidence; do not fight it with repeated writes
- **Control or release differs from the source:** consult the matching official version and hold unsupported steps
- **Owner cannot resume or observation is lost:** stop input until the active session and supported owner recovery path are established
- **User rejects the resulting timing:** propose a specific revised interval; weakening the lock requirement or restoring a less restrictive security value needs its applicable confirmation too

Undo only the precise authorized delta after comparing with current state. Do not restore a whole settings panel over intervening changes. A failed verification does not automatically authorize turning off authentication. If rollback would make the unattended session accessible, explain that effect before seeking the required approval.

Return a compact receipt: computer/account, trigger and interval by relevant power source, authentication delay, previous/final values, observed or reported idle/lock/return evidence, final session state, and any blocker. Keep secrets and unrelated lock-screen content out of the record.

Use **configured; idle enforcement unverified** when only settings were read back. Use **verified for the checked condition** only when the actual idle path reached the authentication boundary and the owner resumed the intended session. Do not claim disk encryption, theft protection, notification privacy, logout, account isolation, or reliable operation in every app state from this check.

## Fictional, unexecuted illustration

A fictional Mac user wants authentication after five minutes away while plugged in, without changing battery behavior. The supplied settings show display-off after five minutes but a further fifteen-minute authentication delay. No earlier screen saver is enabled.

The proposed interpretation is that the existing setting does not mean authentication after five idle minutes. The workflow would preserve the display trigger, propose immediate authentication after that trigger, obtain the exact security-setting confirmation, and arrange a local owner-controlled trial. It would not shorten the display timeout to compensate for a misunderstood delay or change battery settings.

If a later hypothetical observation showed the display turning off at the expected time, that alone would remain insufficient. A native locked-state indication followed by the owner's existing unlock and return to the same work would support the bounded result. If an Apple Watch unlocked too quickly to establish the boundary, the receipt would explain the unresolved observation without disabling the watch feature.

This illustration is invented and was not executed. No computer, settings, session, credentials, timer, lock, unlock or recovery operation was accessed or tested for it. The checks above describe later authorized work, not completed live validation.
