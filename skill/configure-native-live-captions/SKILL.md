---
name: configure-native-live-captions
description: "Make native desktop live captions usable for following a chosen computer-audio or explicitly authorized microphone source, checking recognition mode, readable placement, source ownership and stopping. Use for an everyday real-time caption setup, not a saved transcript, authored subtitle track, dictation or meeting recording."
---

# Follow desktop audio with native live captions

Deliver a usable live-caption setup for the named audio path, a short start/source/stop reference and an honest record of what was observed. If access or a required decision is missing, deliver the applicable setup plan with the unrun check. A caption window appearing is not evidence that the intended audio is being captioned.

Use [caption-delivery-pass](../caption-delivery-pass/SKILL.md) for SRT/WebVTT files and [transcribe-recorded-audio](../transcribe-recorded-audio/SKILL.md) for a durable transcript. [configure-desktop-dictation](../configure-desktop-dictation/SKILL.md) inserts speech into a document; this workflow displays incoming speech for reading. [meeting-device-troubleshooting](../meeting-device-troubleshooting/SKILL.md) repairs capture/playback paths. Do not turn a caption request into call recording, a translation service subscription, hearing-device fitting or an accessibility certification.

## Establish the listening task

Collect only details that change the next step:

- Actual computer, operating-system version and native feature, plus any remote-session boundary
- Target app and audio source: a computer's playback, a particular call's incoming audio, or deliberate nearby speech through a microphone
- Spoken language, desired displayed language, and whether original-language recognition or translation is required
- An existing harmless speech sample and the target output device, or a brief intentional user-spoken sample if microphone use is authorized
- Whether the request is instructions, ordinary configuration, or configuration with a bounded live check
- Existing caption/accessibility preferences, current screen sharing and the requested ending state

Do not ask why the user needs captions or infer a disability. Let them judge readability and usefulness. Inspect available settings before asking for information already visible. A source-matched plan remains useful without device access; do not operate another computer and report it as this computer's setup.

Identify which caption layer is visible: the OS window, the application's own generated captions, an embedded subtitle track or a browser feature. These can coexist. Preserve existing aids and distinguish their outputs before judging a change. Turning on ordinary closed-caption preferences does not establish that speech without a supplied caption track will receive real-time recognition.

### Keep the source and exposure bounded

Confirm the source may be processed and displayed through this feature. A request to caption a selected video does not authorize listening to ambient conversation, joining a meeting, capturing other participants for a recording or starting an unrelated transcription service. Microphone activation and new microphone/privacy permission need their own applicable authority. Keep the microphone excluded for a computer-audio-only task.

Use a harmless sample instead of private calls, credentials or sensitive recordings. Captions can expose words visually to nearby people or through an existing screen share even when audio processing is local. Do not assume an overlay is excluded from capture. If screen-sharing exposure matters, obtain a specific authorized preview or recipient-side observation; otherwise mark it unverified. Do not start a new sharing session just to test this.

Separate permission to change ordinary caption settings from permission to download language components, enable cloud services, broaden device access, install software or change managed settings. Inspect first-use effects before activation, including automatic downloads without a separate prompt. Stop at an unapproved effect or managed restriction; do not bypass it with another speech engine.

Retain only the small setup record. Do not continuously scrape caption text, record the screen, save other speakers' words or export a diagnostic recording as routine evidence. On-device recognition describes that processing stage, not the privacy behavior of the source app or screen-sharing software.

## 1. Match the feature to the installed platform

Use current official documentation for the actual version. Record compatibility limits rather than upgrading the OS or switching products as an incidental fix.

**Windows:** Microsoft's [live-caption guide](https://support.microsoft.com/en-us/accessibility/windows/use-live-captions-to-better-understand-audio) documents Windows 11 22H2 or later; translation has separate Copilot+ PC/version requirements. Start through Accessibility > Captions or Windows+Ctrl+L. Initial setup requests processing consent and language files. Recognition runs locally, and generated captions are not retained as a transcript. Captioning follows the default sound-output device. Microphone inclusion starts off; when included, computer audio takes precedence. Supported translation can activate automatically for certain output-language choices. Inspect the selected mode rather than treating displayed English as proof of English source speech.

**macOS:** Apple's [Live Captions guide for macOS Tahoe](https://support.apple.com/en-gb/guide/mac-help/mchldd11f4fd/26/mac/26) describes local processing, first-use language-data download, and selection between computer audio and microphone input. A hidden window can reflect absent audio; it does not prove the feature is off. Pause and full deactivation are different states. Match the guide's version selector to the actual Mac before following controls.

Apple's [Live Captions settings reference](https://support.apple.com/en-gb/guide/mac-help/mchla0b36db8/mac) limits availability to Apple silicon and supported languages/regions. It separates Live Captions from general Captions preferences, provides language and appearance controls, and describes a FaceTime-only option. Check its actual state when the requested source is another app. Apple cautions against relying on automated captions in emergencies or other high-risk situations.

For another platform, obtain that native feature's official source first. Do not extrapolate Windows microphone precedence, Mac source switching or either platform's retention behavior to a different implementation. If the requested language or source is unsupported, return that specific mismatch rather than changing the entire system language or enabling translation without agreement.

## 2. Prepare one recoverable caption path

Record only affected before values: feature state, source/microphone inclusion, selected recognition/output language, translation mode if exposed, target app/output route and appearance/position. Keep permissions separate from preferences. Reuse installed language resources where suitable; a missing component is a setup decision, not evidence of a defective audio device.

Map the path explicitly: source app or microphone → host that processes audio → caption feature → visible window/display. A remote application's sound may be redirected to another host. Do not enable captions on both machines or change remote audio policy to see what happens. Establish which host receives the intended audio and which host's controls are authorized.

Choose one source at a time for the initial check. Do not use speaker playback picked up by an open microphone as proof of computer-audio captioning. Likewise, seeing another person's words during a call does not establish that the local microphone path works. If source ownership cannot be isolated without interrupting unrelated work, retain that uncertainty.

Apply authorized settings narrowly and read them back. Use a visible menu route when a shortcut is ambiguous or intercepted. Identify a reliable stop control before the sample begins. Never test unknown shortcuts in a live call or consequential form. Preserve the user's established keyboard and assistive setup.

Adjust placement and text only as needed for the requested application. Keep the caption area readable while leaving playback controls and important content usable. Check the actual display and full-screen arrangement when those are part of the task; a windowed preview cannot establish that captions remain usable in full-screen mode. Do not change resolution, display scaling or all accessibility preferences merely to enlarge this window.

## 3. Observe source speech becoming readable captions

Use a short approved speech segment with known wording, preferably including a meaningful number and a negation. The reference words are a comparison target; typing them into a window or displaying a prepared screenshot cannot substitute for recognition.

1. Confirm the selected source, ready state, language/mode and microphone exclusion or inclusion. Verify that the intended sample app is producing the chosen audio; a moving player time alone is insufficient.
2. Play the bounded sample or ask the user to speak deliberately through the approved microphone. Record whether audio was actually heard, only reported by the user, or unavailable to the observation tool. Do not invent acoustic verification from a meter.
3. Observe new text arriving in the native caption window. Keep it distinct from a pre-existing subtitle track and from old caption text. Relate a distinctive phrase to the sample interval to support source ownership.
4. Compare wording and order with the known sample. Note omitted negation, altered quantities, missing phrases or excessive delay. If the tool can see captions but cannot hear the source, label the comparison as against supplied wording, not newly audio-verified.
5. Let the user confirm that the placement, reading pace and text size work in the named app. Do not equate a screenshot's legibility to their comfort or accessibility needs.
6. Stop the sample and use the feature's supported pause/stop control as appropriate. Inspect its reported state. Remaining old text, an automatically hidden panel or silence alone does not prove capture stopped.

If resuming is part of normal use, run one brief continuation after the explicit restart and confirm that fresh text arrives from the intended source. Do not claim words spoken during a paused interval were recovered unless observed. Use a single evidence row per meaningful state change rather than retaining a full caption stream.

For a requested microphone path, check it separately from computer playback and stop it before moving to private discussion. Do not capture both merely to make a demonstration more comprehensive. A successful computer-audio check can finish a computer-audio-only request without any microphone test.

When translation is requested, retain spoken-language recognition and displayed-language meaning as separate evidence questions. Seeing fluent output cannot establish an accurate translation. If qualified comparison is unavailable, report display working with translation accuracy unverified. Never treat an automated caption as authoritative for a consequential number, medical instruction, legal commitment or emergency communication; use the original speaker or a suitable verified written source to resolve critical content.

## 4. Diagnose the failing boundary

| Observation | Next discriminating check | Avoid |
| --- | --- | --- |
| Window opens but no words arrive | Readiness, supported language, actual speech, correct source and pause state | Repeated toggles or a microphone grant for a playback-only request |
| Call audio is audible but captions stay blank | Effective app output and the caption feature's documented audio route | Globally changing sound defaults without checking effects on other work |
| Captions match nearby speech instead of the selected video | Source selection and microphone state | Claiming the video path works because some text appeared |
| Only one app is captioned | App-specific caption layer, app restriction, actual audio route | Installing an extension before identifying the current feature |
| Displayed language differs from speech | Recognition/output language and translation mode | Changing desktop language or calling fluent translation verbatim text |
| Delays or dropped phrases occur during heavy use | Compare the same sample in the relevant workload; inspect applicable performance guidance | Closing unsaved apps, ending calls or promising whole-session reliability from a brief pass |
| Words persist after a pause | New versus old text and explicit processing state | Treating old text as evidence of continued listening or deletion |
| Setup download fails | Exact error, language component and managed deployment requirements | Unofficial package downloads, security changes or circumventing management |

Microsoft's [setup troubleshooting reference](https://support.microsoft.com/en-us/accessibility/windows/voice-access/troubleshooting-live-captions-or-voice-access-setup-issues) provides a separate route for language-component failures, including administrator involvement on managed devices. Reading that route does not authorize installation or external support submission.

Change one evidenced in-scope value and repeat the relevant short sample. Preserve the failed observation and check whether the changed value had the intended effect. If a global default-audio change would interrupt a meeting or another app, pause for the specific decision. Do not add virtual audio drivers, disable protections, reset all sound settings or remove existing speech resources as generic troubleshooting.

If offline use is required, distinguish documented on-device behavior, completed resource installation and a genuinely observed offline check. Do not disconnect the computer or alter its network security just to prove the claim without authorization. Mark a missing offline check honestly while still delivering the documented setup.

Stop at a usable requested path, a precise incompatibility, or a named missing approval/access requirement. A successful local sample does not prove every future call, source language or workload will work. Do not start unattended monitoring of captions.

## Handoff and ending state

Return a concise result with:

- Computer/OS, native feature, intended app/source, language and recognition/translation mode
- Applied/read-back settings or an unapplied plan, plus affected prior values and recovery route
- Actual sample outcome: source ownership, wording limits, readability, pause/stop and any resumption result
- Directly observed, user-reported and unrun checks clearly separated
- Start/source/stop instructions matched to the installed interface, and the exact remaining blocker if any

Accept the live setup only for the path checked: fresh speech reached the intended caption layer, consequential mismatches are acknowledged, the display is usable for the requested activity, and stopping is understood. An enabled setting alone is configuration evidence. Do not promise a saved transcript or subtitle export from an ephemeral caption window.

Leave the feature in the agreed state. End temporary microphone capture and temporary checks; do not disable an established aid or remove installed language resources as cleanup. Before reversing a temporary setting, inspect current state so a later user change is not overwritten. Do not share sample captions or contact support unless separately requested.

## Fictional, unexecuted illustration

A fictional user wants captions while watching a training video through an existing headset. They approve a short harmless playback sample and ordinary caption settings, but no microphone use, new components or system-wide sound changes. Supplied fictional state shows a ready caption window with no text while the app sends audio to a headset different from the system default output.

The proposed next step is to inspect the feature's documented audio route and the app/default endpoint mismatch. Opening the microphone to hear the headset indirectly would violate the requested source boundary. If changing the route affects other work, the operator would ask for that specific change. Until new text is observed from the sample, the setup remains incomplete.

In a hypothetical continuation after an authorized route correction, the sample says “Do not move fifteen boxes,” while the displayed caption omits “not.” That supports a functioning recognition path with a material wording error, not an exact pass. The handoff would retain the mismatch and the user's readability judgment, identify any next useful language check, and preserve microphone exclusion.

This is original authored material, not an observed test. No app, audio source, microphone, caption engine, setting, permission, download, screen share or live workflow was operated for this illustration.
