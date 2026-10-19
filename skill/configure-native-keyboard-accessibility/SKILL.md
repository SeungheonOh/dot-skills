---
name: configure-native-keyboard-accessibility
description: "Configure native keyboard timing and sequential-modifier aids for a bounded typing task, distinguishing initial acceptance, repeated presses, held-key repeat and modifier state. Use for Sticky Keys and Slow/Filter Keys with physical-input verification, not layout correction, shortcut remapping, hardware repair or a medical assessment."
---

# Make intended keystrokes usable without losing control

Deliver a small, recoverable native keyboard configuration for the user's actual typing or command task, with a usable release/return route and evidence that intended input survives the chosen settings. Suppressing extra letters is insufficient if the same settings also discard intended double letters or leave a modifier active for the next action.

Use [diagnose-keyboard-layout-mismatches](../diagnose-keyboard-layout-mismatches/SKILL.md) when keys produce the wrong characters, and [configure-application-shortcuts](../configure-application-shortcuts/SKILL.md) when commands need different bindings. [configure-native-screen-reader](../configure-native-screen-reader/SKILL.md) handles reader modes and navigation; [configure-desktop-dictation](../configure-desktop-dictation/SKILL.md) establishes speech input. This workflow changes how native keyboard input is accepted or combined, without changing what a key means or installing input-interception software.

## Establish the intended input, not a diagnosis

Resolve only what changes the next decision:

- Actual computer, OS/version, physical keyboard and target application/field
- Local or remote input path, selected language/layout, and existing assistive tools that must stay usable
- Desired behavior: one-key-at-a-time combinations, rejection of brief touches, fewer unintended repeated presses, or a more usable held-key repeat
- A small task that should remain possible, including intentional repeated letters, correction and any necessary command
- Current relevant settings, whether the task is a plan, temporary trial or retained change, and the agreed ending state
- A usable way to reach settings and recover if typing becomes too slow, keys stop being accepted or a modifier stays active

Ask about observed input and preferences, not health history. Do not infer disability, prescribe a threshold or label the user's typing abnormal. Let the user choose a comfortable pace. A setting that helps one task may impede another; the desired tradeoff belongs to them.

Inspect existing state before toggling anything. A delayed key or sequential modifier may be intentional. For a request to undo an accidental setting, establish which feature changed rather than turning off all accessibility aids. If ordinary typing suddenly changed only in one app, check its focus/mode and visible input state before applying a system-wide filter.

If target-device access or physical input is unavailable, finish a source-matched plan and mark the interaction checks unrun. Programmatically inserted text, clipboard paste and direct app commands bypass parts of the path under examination. They cannot prove that a brief physical press was accepted or that a held key repeated as intended.

## Keep a dependable route back

An explicit setup request covers ordinary settings within that named scope. A diagnosis-only request does not authorize changing them. Keep new software, input-monitoring/accessibility permissions, registry/API changes, all-user or sign-in behavior, remote policy and device firmware outside this workflow. Respect managed restrictions. Do not install a key logger or export typing history to measure a few keystrokes.

Before the first change, establish an independent usable settings route. It may be a pointer, an existing assistive method or an agreed helper; do not assume the user can use a mouse or perform the very combination they want to avoid. A keyboard-only recovery route must remain feasible with the proposed timing and modifier settings. If none is available, hold the live trial rather than risk removing their only access.

Use an authorized disposable local text surface with no live submission behavior. Check focus and storage/sharing context. Avoid terminals, password fields, command palettes, browser search, message composers and real forms. A latched Control, Command, Alt or Windows key can turn an ordinary letter into an action. Do not try a consequential shortcut simply because its keys are easy to demonstrate.

Preserve open work. Record the affected before values, not the entire user profile. Keep existing reader, voice-control and magnification preferences intact. Permission to configure a keyboard aid does not authorize switching those aids off, changing languages or removing a remapper by trial and error.

## 1. Separate the mechanisms before choosing a control

Use the current official guidance and actual controls for the installed release:

- **Windows:** [Microsoft's input-device guide](https://support.microsoft.com/en-gb/accessibility/windows/make-your-mouse-keyboard-and-other-input-devices-easier-to-use) places Windows 11 keyboard accessibility controls in Settings > Accessibility > Keyboard. Sticky Keys allows sequential multi-key commands; Filter Keys can ignore brief or repeated input. Toggle Keys supplies lock-key sound feedback and is not an input filter. The same page has a separate Windows 10 route; do not copy its settings labels into another release.
- **macOS:** [Apple's accessibility Keyboard reference](https://support.apple.com/en-gb/guide/mac-help/mchlae61a6de/27/mac/27) documents System Settings > Accessibility > Keyboard, with Sticky Keys for sequential modifiers and Slow Keys for acceptance delay. Relevant options include modifier feedback/display and Slow Keys click sounds. Match the page's version selector to the installed OS. Full Keyboard Access and the onscreen Accessibility Keyboard are different features, not prerequisites to enable automatically.

Choose the mechanism from the input event the user describes:

| Desired change | Relevant distinction | Countercheck that must survive |
| --- | --- | --- |
| Enter an existing combination one key at a time | Sequential modifier state, rather than a new command binding | Subsequent ordinary typing must not inherit an unwanted modifier |
| Ignore a short touch but accept a deliberate held press | Initial acceptance delay | Ordinary intentional letters remain practical to enter |
| Ignore an extra press of the same key after its release | Same-key reacceptance/bounce interval | Intentional repeated letters can still be entered at the user's chosen pace |
| Delay or slow repeated input while a key remains down | Held-key repeat onset and repeat rate | The first intended press is still accepted, and release stops repetition |

[Microsoft's FilterKeys reference](https://learn.microsoft.com/en-us/windows/win32/api/winuser/ns-winuser-filterkeys) distinguishes hold-before-acceptance, hold-before-repeat, repeat interval and the interval after release before accepting the same key again. These are different mechanisms. Its documented native model also couples some choices: BounceKeys and the SlowKeys/RepeatKeys group are alternatives there. Do not assume every visible option can be combined independently; read back the effective controls after changing a mode. This reference explains semantics, not permission to call an API or edit the registry.

On macOS, [Apple's response-speed guide](https://support.apple.com/en-ie/guide/mac-help/mchlp2264/27/mac/27) separates Slow Keys acceptance delay from the delay before held-key repetition. Do not treat a repeat-rate adjustment as a fix for rejected short presses. An app may handle a held key specially; compare the actual intended control rather than assuming every letter repeats identically.

If the symptom is a wrong character, composition waiting for another key, reader navigation instead of typing, or a device-specific failure, preserve that boundary and use the relevant diagnosis. A filter can hide a symptom without proving its cause or repairing hardware.

## 2. Prepare one recoverable change

Record feature on/off state and the relevant subordinate choices: timing values with their displayed units, sequential-modifier behavior, feedback, activation shortcut and any automatic deactivation setting. Preserve unrelated values and startup behavior. A feature switch being off does not mean its saved preferences can be discarded.

Choose one candidate that addresses the observed event. Start from the user's existing baseline and preference, not a universal numeric recommendation. If they need only sequential combinations, do not also enable filtering. If a filtering mode implicitly changes other values, identify that coupled change and its impact before retaining it.

Decide activation shortcuts deliberately. Repeated Shift presses or a long Shift hold can be feature controls when enabled, so they are poor neutral practice gestures. Prefer visible settings for initial configuration and read their shortcut options. Do not turn off an established shortcut merely to prevent a hypothetical accident. If accidental activation is the reported problem, changing that shortcut option is a separate, bounded part of the requested remedy.

Apply the authorized setting through native controls. Read back the feature and its affected suboptions before testing. If the save result is uncertain, inspect rather than toggling again. Do not compensate for an inaccessible option with unsupported command-line configuration.

Keep a precise reversal: which value changed and what it was before. Check for intervening user edits before restoration. Do not reset all accessibility or keyboard settings, log out or restart to discover whether a small setting took effect.

## 3. Check sequential modifiers and their release

Use this branch only when sequential combinations are part of the request. First inspect the feature's supported latch/lock behavior and current feedback. A one-use modifier, a locked modifier, physically holding a key and the feature's enabled state are separate facts.

[Microsoft's StickyKeys reference](https://learn.microsoft.com/en-us/windows/win32/api/winuser/ns-winuser-stickykeys) documents optional modifier locking and automatic turn-off behavior, alongside activation and feedback options. Do not assume those options are enabled or transfer their exact behavior to macOS. Use the installed platform's actual help and observable state to establish the release method before trying a command.

1. Place focus in the harmless sample with no unintended selection. Verify the current layout and modifier/lock state
2. Ask the user to press and release the relevant modifier, then the intended key, following the documented sequential path. A layout-appropriate Shift-plus-letter sample can demonstrate a simple combination without invoking a command
3. Inspect the resulting character and modifier feedback. Confirm the intended state after the sequence, rather than counting a sound as proof of text entry
4. Through the established release route, return modifiers to the intended neutral state. Enter one ordinary unmodified sample and check that it is ordinary text
5. If a particular app command is required, test only an already-authorized harmless command in a disposable context, then return to ordinary typing. Do not invent a new shortcut or change its binding here

Modifier locking need not be exercised when the user only wants one-use combinations. If it is required, demonstrate its supported entry and release with the same bounded safeguards. Do not keep pressing a modifier randomly to discover a state cycle; repeated presses can have other configured meanings.

If an unexpected command fires, stop input and inspect its effects. Clear the modifier through the known recovery route before moving to other windows. Do not blindly issue Undo: it may target another action or fail to reverse an external effect. Recover only the affected sample within authority.

## 4. Tune timing against both intended and unwanted input

Use this branch only for the requested timing behavior. Agree on a short harmless comparison the user can comfortably perform. Do not demand rapid tapping or an endurance test.

Keep first-press acceptance, release and the next press explicit. For an acceptance-delay adjustment, compare a brief contact with an intentional longer press where feasible. For reacceptance filtering, compare a released-and-pressed-again key with an intentional double letter at a usable pace. For held-repeat tuning, observe a bounded hold and its release in a safe control. These comparisons are different; do not substitute one for another.

Observe:

- Whether the intended initial input appears once, at the expected caret
- Whether unwanted extra input is reduced in the specific observed sequence
- Whether a legitimate repeated character or correction remains possible
- Whether release ends any ongoing repeat and an ordinary different key still works
- Whether the user finds the resulting pace usable for the chosen task

Use displayed timings as configuration evidence, not measured physical latency. Do not claim millisecond precision from screen observation or calculate an error rate from a few words. Separate direct observations from the user's report. Native feedback can help distinguish a press from acceptance, but output text still needs inspection.

Change one relevant value or supported coupled mode at a time and repeat the same short comparison. If a larger rejection interval suppresses legitimate double letters, that tradeoff is a failed requirement, not an automatic improvement. Offer the previous value or another supported modest adjustment; let the user decide whether the compromise fits their work.

After the isolated check, repeat a small representative task in the actual target app. Use synthetic text, including an intended repeated letter if relevant, and a bounded correction. If both modifier and timing aids are requested, check their combined path after each works separately. Do not imply success in a remote host from a local sample; identify where physical input and filtering are applied before testing that boundary.

## Diagnose the first failed boundary

| Observation | Next useful distinction | Stop or recovery |
| --- | --- | --- |
| Short presses vanish but longer holds work | Acceptance delay versus disconnection | Restore the affected trial value if it prevents usable input |
| Extra presses decrease but intended double letters vanish | Reacceptance interval versus held-key repeat | Retune the relevant mode, preserving first-press behavior |
| A held key repeats unexpectedly | Effective repeat mode, app handling and release evidence | Release and inspect; do not infer that bounce filtering covers this |
| Ordinary letters activate commands | Latched/locked modifier, physical modifier state or reader mode | Stop typing; use the established release/recovery route |
| Feature turns off during a combination | Actual automatic-off option and physical versus sequential input | Inspect state before enabling it again |
| Only one app or remote session fails | App mode, focus, host ownership and key forwarding | Preserve the working local baseline; do not change both hosts |
| One physical keyboard behaves differently | Device path and known existing mapping | Record a device-specific result; do not mask it with stronger global filtering |

Finish when the bounded task and recovery work, the user elects to retain the prior setup, or a precise access/permission/product limitation blocks the next useful check. Avoid indefinite tuning. Stop immediately if the user loses their usable input route or finds the interaction uncomfortable.

## Acceptance and handoff

Return the computer/platform, input path, target task, retained features and affected old-to-new values. Include a short practical reference: how to enter the intended combination or timed press, recognize modifier state, release it, and reach the recovery control. Use full key names and actual configured controls.

Separate prepared instructions, saved/read-back configuration, physically exercised input and user-reported usability. Accept live setup only when intended input reaches the correct sample, relevant legitimate repeats/ordinary typing are preserved, and recovery works through an available method. A screenshot of an enabled switch supports configuration only.

Leave the agreed ending state. Do not switch off an aid as cleanup, retain an unwanted experimental delay, or leave a modifier locked for the next application. If the result is partial, identify the exact remaining physical-input or app check. No hardware-health claim, accessibility certification, login-persistence claim or long-session comfort claim follows from this bounded setup.
