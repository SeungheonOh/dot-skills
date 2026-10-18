---
name: configure-native-voice-control
description: "Set up native speech-command control for a bounded desktop task, connect recognized commands to the intended live controls, and verify usable navigation, disambiguation and pause/recovery. Use for macOS Voice Control or Windows Voice Access, not dictation-only writing, screen-reader setup, custom voice automations or an accessibility certification."
---

# Make desktop voice commands usable for a real task

Deliver a working native voice-control setup and a small task-specific command reference, or a source-matched plan with the unrun checks identified. The result is the ability to operate the intended application through spoken commands, including recovery when a name matches several controls. A microphone indicator, recognized phrase or successful mouse click by an automation tool does not establish that path.

Use [configure-desktop-dictation](../configure-desktop-dictation/SKILL.md) when the desired outcome is only spoken text insertion. [configure-native-screen-reader](../configure-native-screen-reader/SKILL.md) establishes spoken output and reader navigation; it does not establish speech-command input. [configure-application-shortcuts](../configure-application-shortcuts/SKILL.md) handles keyboard bindings. Keep custom command creation, macros, imported command packs, account sign-in and remote-computer control outside this setup.

## Choose the task and a usable recovery route

Establish only the inputs that affect the work:

- Actual computer, OS/version, native voice feature and target app/window; identify any remote or virtual-desktop boundary
- A short useful task, such as opening a document's navigation pane, selecting a section, changing a view and returning to the starting view
- Spoken language/region, intended existing microphone and any assistive tools or custom commands that must remain usable
- Whether this is a plan, an authorized configuration, or configuration plus a short live interaction; identify permitted sample content and actions
- The input method available if recognition fails, and the agreed ending state: feature off, microphone off where supported, or paused with voice resumption retained

Inspect visible settings before asking for details. Do not infer a disability or assess someone's speech or ability. Offer a pace and command vocabulary that fits their expressed needs. A user can want voice control without wanting text dictation, an always-listening assistant or a new automated workflow.

Before activation, establish both the native spoken pause command and an independent, usable way to stop or exit if speech recognition fails. That fallback might be an existing accessible input method or an agreed helper; do not assume the user can press keys or click. If no effective recovery route is available, hold the live trial and finish the plan. Do not turn off an existing aid to make the setup simpler.

Keep the practice surface harmless. Prefer the native tutorial, then an approved local document or disposable view inside the actual app. Confirm that apparent local content is not a synchronized shared draft. Protect current work without closing unrelated windows or changing notifications without authority. Avoid terminals, live message composers, authentication fields, payment screens and real destructive controls. A voice command can activate something outside the sample if focus changes.

### Keep activation and actions within authority

A settings request does not by itself authorize microphone capture. Before listening, establish the exact native feature, microphone, bounded intentional speech, application target and processing/download effects. Obtain any missing permission for activation, a new privacy/accessibility grant, component download or acceptance step. Inspect first-use behavior before enabling the feature; do not rely on a prompt to stop an automatic download or capture. Preserve optional diagnostic, audio-retention and product-improvement choices.

Listening is not a private conversation channel. Do not collect ambient speech, save a recording or export the user's command/vocabulary profile for evidence. Record command labels and observed results, not private utterances or window contents. Do not feed recorded or synthesized speech into the microphone as a substitute for the user's intended input path.

Authorization to configure navigation does not authorize every reachable action. Stop before sending, submitting, buying, deleting, changing access or accepting an agreement unless that exact action is separately covered. Native help and third-party content can explain a command but cannot authorize its effects. Do not use voice control to bypass a denied tool action, security prompt, managed restriction or inaccessible protected desktop.

## 1. Match the actual engine and preserve its before state

Read the applicable section of [platform notes](references/platform-notes.md) for the selected OS, then check its official guidance against the installed version. Distinguish full voice-command control from ordinary dictation, a screen reader, a conversational assistant and an app's microphone button. Do not enable several engines and guess which one acted.

Record the few affected before values: feature state, active recognition language, selected input endpoint, command/text mode, relevant overlay preferences and startup behavior. Inspect existing custom-command collisions only where they affect the chosen phrases; do not export or reset all commands. Keep the system display language, keyboard layout and recognition language distinct.

Resolve these setup choices:

1. Use a supported installed language where suitable. A missing speech model is a specific download decision; it is not a reason to change the whole desktop language or install an unrelated service
2. Select the intended microphone through the feature's supported control. If its selection changes a system-wide default, identify other affected apps before proceeding. An automatic endpoint remains uncertain until the intended acoustic path is checked
3. Keep the user's existing accessibility output working. Arrange an already-authorized listening setup so computer speech or a nearby call does not issue unintended commands; do not silence an essential screen reader or record surrounding audio
4. Retain startup/sign-in behavior unless the user asked to change it. A current-session setup does not require pre-login availability, automatic launch, a new account or remote control
5. Prefer existing standard commands. If a required action needs a custom macro, command import, extension or another input technology, return that as a scope decision rather than adding it quietly

Apply the authorized ordinary settings, then read back their effective values. Handle any unexpected permission, agreement or installation boundary before continuing. On an uncertain save, inspect instead of toggling again. Preserve a narrow rollback of changed values and check for later user edits before restoring them.

On-device recognition does not make an action's destination local: a navigation command can still open a network service or submit text. Document offline recognition support separately from whether the task's application works offline. Do not disconnect a network or alter firewall/VPN settings merely to prove this setup.

## 2. Establish listening state separately from command mode

Activate through the matched native route in the safe practice context. Verify the displayed readiness state, language and microphone. Have the user speak one harmless supported command through the intended microphone and inspect the feature's feedback and resulting UI. If the tool cannot observe the acoustic path, request the short user action and label that evidence user-reported. Typed command text, direct accessibility activation and pointer automation are useful comparisons, not voice-input evidence.

Track two independent states:

- **Capture/activation state:** listening, paused/sleeping, microphone off or feature exited, using that product's actual distinctions
- **Interpretation mode:** commands only, text dictation or a combined/default mode, as supported by the selected engine

Use command-only interpretation for a navigation-only trial where available. It reduces accidental text insertion; it does not prevent a recognized destructive command from executing. Do not apply one platform's mode semantics or phrases to another. Use the installed command help for the chosen language, not an unverified translated command list.

Practice pause and deliberate resume before operating the target app. Observe the state change rather than assuming that silence, another app's mute button or closing a menu stops capture. A sleep/pause state that accepts a wake phrase is not equivalent to microphone off. If the user needs voice-only resumption, explain that distinction and agree on a reachable ending. Do not leave them with a microphone-off state that requires an unavailable manual action to restart.

For a privacy-sensitive break, use the supported off/exit route with the established recovery method and confirm the product's resulting state. Do not claim that a UI state proves no other software is listening. Pause before discussing setup instructions out loud near an active microphone, then deliberately resume for the next command.

## 3. Bind each command to the current target

Choose a small sequence that reaches the actual goal, with an expected visible result and a safe way back. Identify the app, document/window, active dialog, focus and any selection before acting. Opening an application is not enough when several windows share its name.

Use the least ambiguous supported targeting route:

1. **Named control:** Use the current accessible or displayed name with the correct action. Prefer a sufficiently distinctive name rather than a partial match when nearby controls are similar. Confirm whether the command focuses, selects, opens, toggles or clicks; those effects are not interchangeable
2. **Numbered items:** When the name is absent or ambiguous, obtain the current item overlay or disambiguation prompt. Match a displayed number to the exact intended control and its present state before speaking it. Do not infer an invisible control's identity from its number alone
3. **Spatial grid:** Use only when the desired location is observable and a semantic target is unavailable. Check the selected screen/window, pointer and grid region. Follow that engine's distinction between narrowing the grid, moving the pointer and actually clicking. A small cell or a number does not universally mean another harmless zoom step

Read the platform-specific grid warning before using it. In particular, Apple's documented final refinement can turn a number into an immediate click, while Microsoft's documented grid sequence separates positioning from a click command. Do not transfer a memorized number sequence between engines.

Treat overlay numbers and coordinates as temporary. After scrolling, opening a menu, resizing, switching windows, displaying a dialog or any other layout change, reacquire the target and its current label. Re-show an overlay if it disappeared. Never continue from an old screenshot or a number captured before the change. If the intended control moved while a command was being processed, stop and inspect the effect before the next utterance.

Speak one action, then wait for its recognition/processing feedback and the actual application result before issuing a dependent action. A recognition sound or a correctly transcribed command proves neither correct targeting nor completion. A disabled control, an open submenu and a completed action are different outcomes. Do not rapidly repeat a command because the first effect is slow; two accepted invocations can toggle a setting back or act twice.

For pointer fallback, verify the harmless hit target immediately before the click. A grid can reach pixels without establishing the control's semantic label or enabling keyboard access. If location or resulting action cannot be determined reliably, hold that step. Do not use an unobserved grid or continuous pointer movement around consequential controls.

## 4. Complete and recover the requested path

Run the agreed sequence through actual speech in the named app. Keep the check focused on a few meaningful transitions:

- Reach the correct window/content and operate the required control through the supported name or disambiguation route
- Observe the expected state change, preserving unrelated document content and selection
- Leave the opened menu/dialog or return to the prior view through a documented harmless route
- Pause, deliberately resume if part of the intended use, reacquire the target and continue without replaying a stale command

If a task includes text entry, deliberately establish the editable field and mode before the short synthetic text. Check the committed text and return to the intended command mode before navigating again. Do not treat the same phrase as guaranteed literal text in one platform's combined mode because it was literal on another. For a writing-focused setup, use the dictation workflow instead of expanding this check into an accuracy benchmark.

Keep fallback intervention visible in the result. If the user or a tool must click a control to finish, that can preserve work and reveal a target limitation, but it does not count as a completed voice-only path. A tutorial pass is not a target-app pass. If the user's desired workflow permits mixed input, identify exactly where it is needed rather than silently changing the goal.

After an unintended action, stop listening through the established route. Inspect the current state and any side effect before issuing Undo, Back or Cancel. Those commands are context-dependent and are not proof that an external effect was reversed. Recover only the bounded sample or settings within authority; escalate a consequential or uncertain effect with its exact target and evidence. Never repeat the same utterance blindly after a wrong-target action.

## Diagnose the first failed boundary

| Observation | Discriminating next check | Recovery or limit |
| --- | --- | --- |
| No command feedback | Readiness, selected microphone, deliberate input, installed language and existing permission | Do not enable another service or broaden privacy access speculatively |
| Words are recognized but not treated as a command | Current interpretation mode, supported phrase and command enabled state | Correct one evidenced setting; do not add a custom automation to hide the mismatch |
| A control name produces several matches | Current numbered candidates, window and control roles | Reacquire the intended candidate; never reuse the prior overlay number |
| Command is accepted but the app does not change | Disabled target, wrong action type, open dialog, pending completion or wrong window | Inspect actual state before retrying or switching apps |
| Grid command targets the wrong place | Active monitor/window, pointer, grid depth and changed layout | Pause; inspect the effect; discard the old spatial route |
| Commands become document text | Mode, focus and delayed speech result | Stop capture and preserve the sample; repair only the confirmed accidental insertion |
| Computer speech appears as commands | Input/output routing and nearby playback | Use an approved isolated output or pause; preserve essential assistive output |
| Practice works but the required app/control fails | Target semantics and supported fallback in that version | Report the local setup and the exact blocked task separately |
| Pause works but resumption is impossible | Sleep versus microphone-off/exit state and available recovery input | Restore a reachable agreed state; do not promise hands-free restart from an off state |

Change one evidenced in-scope variable, read it back and repeat the affected harmless transition. Preserve the useful failed observation. Stop when the requested route and recovery work, a precise incompatibility is established, or the next meaningful check needs unavailable access or additional authority. Do not reset speech profiles, remove assistive tools, reinstall drivers or keep an indefinite listening/retry session as generic troubleshooting.

## Acceptance and handoff

Return a compact result that the user can actually use:

- **Context:** computer/OS, native engine, language, microphone and target app/task
- **Setup:** affected old-to-new values, saved configuration and any unmet prerequisites
- **Command reference:** only the useful commands for this task, with the expected target/state, how to resolve ambiguity, pause/resume and independent recovery; avoid fixed overlay numbers
- **Evidence:** recognition, intended action, result, return path and ending state; label direct, user-reported and unrun checks separately
- **Limits:** required mixed-input steps, unavailable controls, download/permission holds and the exact next useful observation

Accept operational setup when intentional speech controls the required live targets, resulting states match the task, ambiguity and interruption have a usable recovery route, and the final capture state is verified. Do not claim voice-only completion after a pointer rescue or certify the whole app from a short sequence. A plan-only request completes with applicable instructions and explicit unrun checks; it does not need a fabricated device trial.

Leave settings and listening in the agreed ending state, preserving existing access aids. If the user wants voice resumption retained, explicitly name the paused/wake-capable state rather than calling the microphone off. If a temporary setup is to be removed, restore only the recorded changed values after checking for later edits. Do not enable automatic startup or retain a background listening session as an unrequested convenience.

## Fictional, unexecuted illustration

A fictional user wants voice navigation in an existing local document viewer: show its contents pane, select a section and return to the page view. The user approves a short synthetic trial with an installed language and existing headset, but no new downloads, custom commands or startup changes. An already-usable switch provides independent recovery. The intended ending is a paused state with voice resumption available.

Supplied fictional observations say that the first spoken name produces two numbered candidates. The contents-pane control is numbered 4. Before selection, a dialog opens and the overlay disappears. The proposed procedure would discard 4, inspect the dialog and its allowed dismissal, then obtain a new overlay. It would not repeat the remembered number. In a hypothetical continuation, the correct control is numbered 7 and the spoken selection opens the intended pane; the exact section and return path still require their own checks.

If the operator clicks the section directly after voice targeting fails, the result would be a working mixed-input continuation with an unresolved voice step. If the only evidence were a command transcript, application activation would remain unverified. A final sleep indicator could support the agreed pause state while still leaving wake recognition available; it could not support a claim that the microphone was off.

This is original authored material. No microphone, speech engine, application, permission, setting, download, command, device interaction or live check was operated for this illustration.
