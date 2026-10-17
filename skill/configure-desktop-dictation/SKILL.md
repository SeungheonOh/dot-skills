---
name: configure-desktop-dictation
description: "Prepare or configure native desktop dictation for a named application, preserving microphone, language and processing choices and verifying live speech insertion, correction and stopping. Use for a reusable speech-to-text input setup, not transcribing recordings, voice-controlled computer navigation or installing a speech service."
---

# Set up dictation for everyday writing

Make the user's chosen native dictation feature usable in their actual writing application. Deliver the working configuration or an unapplied setup plan, a short start/stop/correction reference, and an honest record of the speech-to-text path checked. An enabled switch, moving microphone meter or successfully typed sample does not establish that spoken words reach the intended document.

Use [transcribe-recorded-audio](../transcribe-recorded-audio/SKILL.md) for an existing recording and [meeting-device-troubleshooting](../meeting-device-troubleshooting/SKILL.md) for call audio. [diagnose-keyboard-layout-mismatches](../diagnose-keyboard-layout-mismatches/SKILL.md) covers physical-key character errors; [configure-application-shortcuts](../configure-application-shortcuts/SKILL.md) covers a broader binding change. This workflow establishes live text input, not hands-free computer control, assistant activation, voice identification, transcription uploads or an accuracy benchmark.

## Establish the writing context and authority

Find only what changes the setup:

- The actual computer, OS/version, existing native speech feature and target app/field, including any browser or remote-session boundary
- The language and regional variant the user will speak, whether they switch languages, and whether exact wording or assisted cleanup is intended
- The intended already-available microphone and ordinary working conditions, such as a docked headset
- Whether network-dependent speech processing is acceptable, whether offline operation is required, and any managed-device restrictions
- The requested stage: instructions only, an ordinary in-scope configuration, or configuration plus a short live check
- The authorized harmless sample destination and whether the user can supply a brief spoken phrase through that computer's microphone

Inspect available settings and documentation before asking for facts already visible. If live microphone or application access is absent, finish a source-matched plan with unrun checks. Do not imply that a remote assistant conversation, injected text or an unrelated cloud computer exercises the user's microphone.

Keep speech activation and data transmission within their actual authorization. Before a live check, identify what will listen, where speech will be processed when known, the synthetic phrase or bounded sample, and its receiving document. Ask for missing microphone activation, capture, permission or destination approval; do not treat a settings-only request as permission to listen. New microphone/privacy access, cloud processing, language/model downloads or a broader accessibility grant may need a separate decision even when ordinary dictation settings are in scope. A declined or managed restriction is a stopping boundary.

Use only the user's intentional sample speech. Do not record ambient conversations, play a private recording into the microphone, store voiceprints or turn a short setup task into continuous listening. Avoid secrets, authentication fields, real customer data and sensitive personal material. Do not opt into optional audio retention, product-improvement sharing or new cloud services as part of setup. Existing privacy choices remain unchanged unless the user specifically authorizes a change.

Prepare a safe local scratch document or an expressly approved unsent draft. Verify its actual storage and sharing context: a document visible on the desktop can still autosave to a shared service. Do not test in a terminal, search box, chat composer with send-on-enter, live form or command palette. A dictation formatting command can have a consequential meaning in the wrong field. Keep a reliable pointer/keyboard route to stop listening and correct text throughout.

## 1. Identify the speech engine and its processing boundary

Read the feature's displayed name and applicable official guidance. A microphone icon may belong to the OS, an application, a website, an assistant or a voice-control system. Select the requested engine deliberately; do not enable several and infer which one produced the text. Record the chosen invocation route, listening indicator and stop control before activation.

Check the current platform rather than treating every desktop as equivalent:

- **macOS Dictation:** Apple's [Dictation guide](https://support.apple.com/guide/mac-help/dictate-messages-and-documents-mh40584/mac) places setup in Keyboard settings, including language, microphone and shortcut choices. Its displayed processing notice describes whether general text dictation is on-device; that statement excludes search-box dictation. Voice Control replaces standard Dictation while active. Do not disable an existing assistive workflow merely to expose this feature. Use its documented start/stop controls and the selected language's supported punctuation behavior.
- **Windows voice typing:** Microsoft's [voice-typing guide](https://support.microsoft.com/en-us/accessibility/windows/use-voice-typing-to-talk-instead-of-type-on-your-pc) documents online recognition, an internet requirement, a focused text box and Windows+H activation. Launching voice typing starts listening; supported PCs may also begin a background cleanup-model download. Check those first-use effects before invocation rather than relying on a prompt to gate them. Language follows the selected input language. Available settings include microphone and punctuation choices. On supported PCs, optional or default cleanup features can transform wording; inspect their actual state rather than assuming literal transcription. On-device cleanup does not establish that the preceding speech-recognition path is offline.

These are entry points, not a guarantee for every OS release, language or hardware model. Recheck version-specific controls, processing notices and command vocabulary when the visible target differs. For another native feature, obtain its own official guidance before writing operational steps. Do not silently substitute a browser service or full voice-control product for a missing feature.

Distinguish the recognition destination from the text destination. On-device recognition does not make a cloud document local, and a local document does not make cloud recognition local. Record unsupported or unknown processing behavior explicitly. If offline-only use is required and the chosen feature's documented route needs a network, stop that route and present the mismatch. Do not disconnect networking to discover this at the cost of other work or promise privacy from a successful offline-looking screen.

## 2. Prepare the smallest recoverable configuration

Record only the affected before state: feature enabled/disabled, recognition language/region, microphone selection, invocation, punctuation/cleanup settings and any relevant input-language state. Keep configuration values separate from permissions. Do not export the whole speech profile, learned vocabulary or account history for a small setup.

Resolve these choices before changing them:

1. **Language:** Match the spoken language and region to a supported installed choice. Keep the OS display language, keyboard input language, document proofing language and recognition language distinct, even where the product links some of them. Preserve other installed languages. A missing language is a specific installation or availability question, not a reason to switch the whole desktop language.
2. **Microphone:** Select the intended endpoint where the feature supports it. Note whether the selection is feature-specific or changes a system default used by other apps. Do not silently change meeting or recording routes. If the feature exposes only an automatic/default selection, retain that uncertainty until the actual capture path is checked.
3. **Invocation:** Prefer an existing supported key or menu route. Inspect a proposed shortcut's effect on language switching and existing accessibility controls. Do not install a remapper or request broad input monitoring to make one key work.
4. **Text transformations:** Preserve the user's requested distinction between literal words, punctuation assistance and rewritten prose. Inspect automatic punctuation, cleanup and target-app autocorrection separately. Do not attribute every changed word to recognition or enable rewriting because it appears convenient.

Apply only the already-authorized subset through native controls. Read back the saved values before starting speech. If a prompt would install components, change privacy access, enroll a service or enable a broader listening mode, hold at that prompt and identify the exact decision. Preserve current work before any required app restart; an OS restart is not a default setup step.

Keep a narrow reversal: restore the specific previous value or disable only the feature newly enabled for this task, as authorized. Recheck current state before restoration so later user changes are not overwritten. Do not reset all language, speech, accessibility or sound settings. If a write has an uncertain outcome, inspect before retrying rather than toggling repeatedly.

## 3. Check live insertion in a harmless document

Use a short sample chosen for the requested language and writing task. Include an ordinary sentence, one meaningful number or negation, and a simple punctuation or paragraph action if needed. Keep it small enough to compare manually. The expected text is a review reference, not text to inject as a substitute for speech.

1. Open the approved scratch document and confirm the actual focused editable field. Preserve any existing text. Place the caret at a known insertion point with no unintended selection; use synthetic surrounding text if insertion location matters.
2. Invoke the selected engine through its intended route. Observe its actual ready/listening state before the user speaks. A toolbar opening alone is not capture evidence.
3. Have the user speak the bounded sample through the intended microphone. If the tools cannot observe that path, request the short user action and retain the observation as user-reported where appropriate. Do not claim an acoustic check from a tool that simply enters text.
4. Wait for the current utterance to settle according to the feature's visible state. Inspect the committed text, its insertion location and surrounding text. Keep partial/provisional words distinct from the final result; do not immediately repeat a phrase while an earlier result may still arrive.
5. Stop through the known control and confirm the feature reports it is no longer listening before moving to another field or discussing private material. Do not rely on silence, loss of focus or another application's mute button as the stop method.
6. Compare the final sample with the intended words. Note substitutions, missing or repeated spans, numeric formatting and punctuation separately. Keep recognition errors distinct from a documented cleanup mode or later app autocorrection. Do not silently fix the sample and then call the initial recognition exact.

Check correction without risking other text: while listening is stopped, use the application's normal selection/editing route on a small part of the synthetic sample, then verify the resulting words and unchanged surroundings. Resume at a deliberately placed caret for one short continuation if restart is part of the intended workflow. Speech-editing commands are optional; use only documented commands for the chosen feature/language and establish their selection scope first. Never try an unknown delete or submit command on real work.

If a menu invocation works but the requested shortcut does not, report the speech path and the invocation failure separately. If text works in a safe native control but not the actual target app, do not call the target ready. A comparison app is useful evidence, not a replacement chosen without the user.

## 4. Resolve the evidenced boundary, then retest once it changes

Choose the next check from the observed failure instead of cycling through global resets:

| Observation | Next useful boundary | Preserve or stop condition |
| --- | --- | --- |
| Feature does not start | Selected engine, supported invocation, existing permission or managed restriction | Do not enable a different listening system or bypass policy |
| Listening state appears but no text follows | Chosen microphone, intentional speech reaching it, recognition language, service readiness and field support | A meter alone is not intelligibility or text-insertion evidence |
| Text appears in another field or replaces text | Focus, caret/selection and delayed result ownership | Stop listening; preserve unintended text and inspect before undoing |
| Words change after first appearing | Provisional recognition, speech cleanup or app transformation | Separate the stages before changing settings |
| Punctuation words appear literally | Selected language and that feature's command vocabulary | Use supported manual punctuation; do not invent commands |
| A repeated phrase arrives twice | Pending result followed by a premature retry | Stop and inspect committed text before another attempt |
| Works until a headset or app changes | Effective input endpoint and target context after the change | Preserve the known working setup; do not infer permanent hardware failure |

Microsoft's [voice-typing troubleshooting guide](https://support.microsoft.com/en-us/accessibility/windows/voice-typing-isn-t-working-in-windows) separates microphone selection/access, supported language and missing or incorrect text. Use the actual error and matching current guidance; a microphone permission suggestion is not authorization to grant it. For basic capture failure, use the device workflow rather than expanding into driver installation or device replacement here.

Change one evidenced ordinary setting within scope, read it back, and repeat the same relevant sample under comparable conditions. Retain a useful failed observation as well as the eventual result. Do not manufacture an accuracy percentage from a few sentences, infer a person's speaking ability or promise performance in other languages, rooms or applications.

For an offline requirement, establish only the evidence the task permits. A supported offline procedure and a separately authorized network-isolated check can establish the observed scenario; neither certifies that no unrelated data is ever transmitted. Do not modify firewalls, VPNs or system security to test dictation. If an interruption is not authorized, mark offline behavior untested and preserve the documented limitation.

Stop when the requested app path is usable with the agreed correction route, a precise incompatibility is established, or the next useful check needs missing access or approval. Do not leave an indefinite service wait or retry loop. If a service is temporarily unavailable, return its observed state and the exact check to resume; do not repeatedly activate capture or change privacy settings.

## Deliver the setup and its limits

Return a compact handoff containing:

- **Scope:** computer/OS, native feature, target app/field and tested language/region
- **Working state or candidate:** affected settings, actual microphone selection and recognition/text destinations, with unknowns visible
- **Use reference:** how to start, recognize readiness, stop, correct text and deliberately resume; include only supported commands needed for this task
- **Evidence:** sample comparison, actual insertion/correction/stop results and whether directly observed, user-reported or unrun
- **Recovery:** old-to-new values, temporary settings restored, persistent settings intentionally retained and any precise blocker

Accept live setup only when intentional speech has produced usable committed text in the named target, relevant wording changes are understood, correction and stopping are checked, and unrelated text/settings remain intact. When saving a sample is requested, reopen the exact saved document and distinguish that persistence check from the live recognition check. A configuration-only request can finish with a supported plan and explicit unrun checks.

Confirm listening is stopped at handoff. Do not send the dictated text, share the sample, subscribe to a service or enable automatic/background listening merely to demonstrate success. Keep any final result limited to the contexts actually checked.

## Fictional, unexecuted illustration

A fictional user wants native dictation in a local notes app using an already-connected headset and an installed English input language. They authorize ordinary feature settings and a short synthetic sample, but do not approve new microphone permissions or optional recording retention. The proposed sample contains the words “Do not order sixteen folders” followed by a separately specified paragraph action.

Supplied fictional observations show the listening indicator, text inserted at the correct caret, and a final sample containing “Do not order sixty folders.” That establishes some live insertion in the described scenario, not correct recognition of the quantity. The operator would stop listening, record the mismatch, check the selected language and microphone, and use the ordinary correction route on the synthetic number. A resumed phrase would be checked for duplication and insertion location. An unsupported paragraph command would remain a limitation, not be reinterpreted as a successful formatting action.

If an unexpected microphone permission prompt appeared, the live check would pause for that decision. If only a programmatically entered sample were available, the setup would remain unverified for speech. A later checked correction could make the writing workflow usable without turning the original recognition result into an exact pass.

This is original authored material. No microphone, speech engine, application, setting, permission, network change, recording, text sample or live test was operated for this illustration.
