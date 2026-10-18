---
name: configure-native-screen-reader
description: "Set up an existing desktop's native screen reader for a bounded reading and keyboard-navigation task, preserving assistive preferences and verifying speech, focus, activation and recovery in the chosen app. Use for a usable VoiceOver or Narrator setup, not dictation, document remediation, a full accessibility audit or installing assistive hardware."
---

# Make a native screen reader usable for the intended task

Deliver a working, recoverable screen-reader configuration and a short command reference for the user's actual application, or a source-matched setup plan with the unrun checks identified. Hearing a welcome message establishes neither successful navigation nor usable access to the target content. Keep the spoken description, reader position, keyboard focus and resulting application action connected throughout the task.

Use [configure-desktop-dictation](../configure-desktop-dictation/SKILL.md) for speech-to-text input and [repair-document-accessibility](../repair-document-accessibility/SKILL.md) for changing an inaccessible document. [keyboard-form-completion-check](../keyboard-form-completion-check/SKILL.md) checks a web form's keyboard journey; it does not configure the user's everyday reading environment. This workflow covers native desktop speech and keyboard use, not voice commands, braille-device setup, replacing an established assistive tool, or certifying an application.

## Establish the useful task and preserve access

Find only the inputs that affect setup:

- The actual computer, OS/version, native reader, chosen app/version and any browser or remote-session boundary
- The reading or navigation task, such as locating a section, reading its instructions, moving to a named control and returning to the document
- Existing reader experience, preferred language, installed voice, acceptable speech rate and intended audio endpoint, where the user has expressed a preference
- Existing assistive settings or tools that must remain usable, including modifier choices, keyboard layout, magnification and input aids
- Whether the request is instructions only, a scoped configuration, or configuration plus an authorized harmless interaction
- The approved sample content and destination, and whether the final state should retain the reader or restore a temporary trial

Do not ask for a diagnosis or infer a disability from this request. Let the user choose a comfortable pace and whether they want coaching; a setup check is not an assessment of their abilities. Reuse visible settings instead of conducting a long preference interview.

Check the available input and observation tools. An automation API that clicks an accessibility node can help inspect the interface, but it does not demonstrate keyboard access. A screenshot, accessibility tree or speech-caption panel cannot establish that audio was heard through the intended endpoint. If hearing or physical-key evidence requires the user, request a short specific check and label it user-reported. Without target-device access, finish the plan rather than operating a different computer and claiming a result for this one.

Keep a recovery route available before activation. The user must be able to reach the stop/help control by their usable input method; do not rely solely on a visual menu or on a key combination their keyboard cannot send. A pointer can assist setup when appropriate, but pointer rescue does not count as a successful keyboard-only path. Never turn off an existing aid merely to simplify observation.

### Bound speech, content and setting changes

Screen-reader speech can expose window titles, notifications and document contents to nearby people or a call's shared system audio. Use an agreed private listening route and a harmless local sample. Preserve open work; do not close private windows, change notification rules or disconnect a meeting without authority. If unintended private content is spoken, stop the sample through the established route and resolve the exposure before continuing.

A request to configure this reader covers ordinary settings within that scope. Keep additional downloads, extensions, network-assisted descriptions, diagnostic sharing, global key remapping, new privacy/accessibility permissions, startup-before-sign-in behavior and changes affecting other users separate. Inspect first-use effects before activation when they can occur without a prompt. Do not accept a managed restriction, unavailable feature or missing permission as an invitation to install a replacement or bypass policy.

Do not use credentials, private messages or consequential live forms as practice material. Do not capture speech history, export accessibility profiles or record the desktop merely to prove setup. If a recording or diagnostic upload is requested, establish its content and destination separately. Keyboard navigation does not authorize sending, deleting, purchasing or submitting anything reached by it.

## 1. Match the reader, command scheme and startup effects

Read official guidance for the installed platform and inspect its actual settings. Confirm that the feature is the full native screen reader rather than an application's Read Aloud button, selected-text speech or a voice-input feature. Keep the OS input layout distinct from the reader's command layout and modifier key.

**macOS VoiceOver:** Apple's [start/stop guidance](https://support.apple.com/guide/voiceover/turn-voiceover-on-or-off-vo2682/mac) documents Command-F5 and System Settings > Accessibility > VoiceOver. It distinguishes turning the reader off from pausing speech with Control; another Control press resumes paused speech, and cursor movement can also restart it. Account for the actual keyboard's function-key behavior and welcome dialog. Do not treat silence as evidence that VoiceOver has exited.

**Windows Narrator:** Microsoft's [introduction](https://support.microsoft.com/en-us/accessibility/windows/narrator/chapter-1-introducing-narrator) documents Windows+Ctrl+Enter for start/stop and Windows+Ctrl+N for settings. Confirm that the start shortcut is enabled. Narrator Home offers QuickStart, while automatic startup is a separate choice. Do not change pre-sign-in or all-user behavior for a current-session request.

Before starting Narrator, inspect the installed version's extension and service settings. Microsoft's [customization guide](https://support.microsoft.com/en-us/accessibility/windows/narrator/chapter-7-customizing-narrator) describes extension execution and automatic extension downloads at startup, as well as diagnostic and web-information options. An existing native reader does not guarantee an activation without downloads. If those effects conflict with the requested scope, hold activation for the specific decision; do not silently change the policy or rely on a later prompt.

Record only relevant before values: enabled state, voice/language, speech rate and volume, output selection, command layout/modifier, and the navigation or echo settings the task may change. Preserve customized commands. Where the current settings cannot be inspected, use a supported settings route or report the gap instead of resetting to defaults. Activate once through the verified route; inspect uncertain results before repeating a toggle.

## 2. Establish intelligible output and safe command learning

Use the reader's own tutorial or a small approved local text sample. Confirm that speech is intelligible through the intended output. If the available tool cannot hear it, get the user's observation; a moving volume meter is insufficient.

Prefer an already-installed suitable voice. Adjust one relevant setting at a time and let the user judge comfort. Apple's [voice settings](https://support.apple.com/guide/voiceover/change-the-voiceover-voice-unac009/mac) distinguish choosing installed voices, adjusting rate/pitch/volume and downloading another voice. Record a missing voice as a bounded availability issue. Do not change the desktop language or install a voice package without the needed authority.

For Narrator, use its own output and verbosity controls where appropriate rather than changing all system sound. The [customization reference](https://support.microsoft.com/en-us/accessibility/windows/narrator/chapter-7-customizing-narrator) also distinguishes typing echo, audio ducking, cursor synchronization and command layout. Preserve cues the user relies on; reducing speech until controls lose their role or state is not an improvement. Record old and final affected values and read them back.

Teach only the commands needed for this task, including help and recovery:

- **VoiceOver:** In Apple's [getting-started guide](https://support.apple.com/guide/voiceover/get-started-with-voiceover-vo4be8816d70/mac), VO means the configured modifier, with Control-Option or Caps Lock available by default. VO-K starts or stops Keyboard Help. VO-Left/Right Arrow moves the reader cursor, VO-Space performs an item's default action, and VO-Shift-Down/Up Arrow enters/exits a group. Confirm the actual bindings before use, especially on a customized profile
- **Narrator:** Microsoft's [basics](https://support.microsoft.com/en-us/accessibility/windows/narrator/chapter-2-narrator-basics) documents Narrator+1 for Input Learning and Ctrl to stop current reading. The Narrator modifier is configurable; Caps Lock and Insert are common defaults, with documented keyboard-specific exceptions. Match the current Standard or Legacy command scheme instead of assuming a memorized shortcut applies

Practice the short help-mode entry and exit first. Confirm it has exited before testing application commands; spoken descriptions of keys in a learning mode are not evidence that those commands ran. Do not sweep arbitrary shortcuts, enable a locked modifier unexpectedly or alter existing assistive shortcuts to make the sample easier.

## 3. Carry position and mode into the target application

Choose one small task in the real target, with a known start, harmless actions and an observable result. For a reading task, locate a named section and read a supported detail. If interaction is requested, add a harmless control action, a short scratch-text edit or a reversible dialog visit. Do not add editing or activation solely to make a read-only request more comprehensive.

Track three separate positions where relevant: the reader's current item, the application's keyboard focus and the text insertion point/selection. Hearing a field's label does not prove that typing will enter that field. Apple's [cursor-tracking guidance](https://support.apple.com/guide/voiceover/cursor-tracking-and-wrapping-vo15534/mac) explains that VoiceOver and keyboard focus can track one another or operate independently. Inspect the actual behavior; do not enable global tracking simply because one sample is confusing.

Keep navigation modes explicit:

- In VoiceOver, establish whether the reader is outside or inside a group. Enter the intended group, move to the required item and deliberately leave it. A boundary sound need not mean the app is frozen. Preserve the user's existing Quick Nav or interaction preferences and consult their version's commands if those change the route
- In Narrator, [scan mode](https://support.microsoft.com/en-us/accessibility/windows/narrator/chapter-3-using-scan-mode) changes how navigation keys are interpreted and is toggled with Narrator+Spacebar. It can activate automatically in supported apps and switch off for edit fields. Establish the actual mode before letters are used as navigation or text. Do not infer a broken keyboard from a key moving to a heading instead of entering a character

For the selected interaction:

1. Identify the target window/document without relying only on its screen position. Hear or otherwise verify the current item and relevant control role/state
2. Navigate using the intended reader/keyboard route. Record the meaningful announcement and target reached, not every keypress
3. Before activation or typing, establish focus, selection and action scope. Use only the agreed harmless target. If the announced identity is ambiguous, stop instead of guessing from visual position
4. Perform the bounded action and check the resulting application state. Speech announcing a button name is not evidence that it activated; typed-character echo is not evidence that the text landed in the intended document
5. Leave the control, group or dialog through its supported route and recover the intended reading context. Check a brief return to the same task if that transition is part of normal use

A direct tool click, injected text or copied plaintext may help diagnose a failure, but cannot replace the failed reader path in the acceptance record. Use actual output to confirm any relevant label, state or saved text. Do not manufacture headings, add custom labels or turn on recognition services to conceal an inaccessible source. OCR or generated descriptions require their own scope and do not prove native semantics.

## 4. Diagnose the boundary without dismantling the setup

| Observation | Smallest useful next check | Limit or recovery |
| --- | --- | --- |
| Reader appears enabled but nothing is heard | Speech pause/mute, selected voice, reader output, intended endpoint and system volume | Inspect before toggling repeatedly; preserve other audio and established access |
| Keys are described but nothing activates | Learning mode, configured modifier, command scheme | Exit the known help mode and repeat the one harmless action |
| Navigation stays within a small region | Current group, dialog or scan/navigation mode | Use the documented exit; do not close the app or reset navigation globally |
| A navigation letter appears as text, or typing navigates | Current field focus and reader mode | Stop typing, inspect the scratch result, restore only the affected sample when authorized |
| Reader announces one item but typing changes another | Reader cursor, keyboard focus, insertion point and tracking behavior | Preserve unintended work; resolve positions before any retry |
| Tutorial works but the target does not | Target app, content semantics, mode and exact missing control | Retain the working baseline; report target access as blocked, not a broken reader |
| Captions show speech but the user hears none | Physical output path and mute state | Caption evidence supports generated text only; acoustic delivery remains unresolved |
| A remote session differs from local use | Which host owns the reader, key interception and audio redirection | Do not enable readers on both hosts or change remote policy by trial and error |

Change only the evidenced in-scope value, then repeat the relevant task under comparable conditions. Keep a failed observation when it explains the remaining limitation. Restore a failed temporary setting to its recorded prior value after checking that the user has not changed it meanwhile. Avoid resets, driver changes, new extensions, profile replacement or disabling protections as generic recovery.

If the user loses their usable input or speech route, pause further exploration and use the pre-established recovery method. Do not turn off the reader if that removes their only access, and do not repeatedly activate controls without reliable feedback. Return a specific support handoff if the next meaningful step requires unavailable access, new permission or target-app repair. A tutorial pass is still useful, but it cannot close that target-app blocker.

## Acceptance and handoff

Return a concise record with the computer/OS, reader and command scheme, target app/task, affected old-to-new settings, usable command reference, observed outcomes and remaining limits. Separate these evidence levels:

- **Prepared:** applicable instructions and checks, with no claimed configuration or interaction
- **Applied/read back:** requested settings saved and inspected
- **Output confirmed:** actual speech heard through the named endpoint, identifying direct or user-reported evidence
- **Task checked:** intended content/control reached, required meaning or state understood, authorized action observed and recovery completed through the requested input route

Accept a live setup only to the requested task's scope. A reading-only request can complete without editing; an interaction request remains partial if a required control cannot be reached or identified. Do not call an app accessible, all content readable or the setup permanently reliable from this bounded check. A saved sample, if requested, needs its own reopen check; it does not establish the audio path.

Leave the reader and affected settings in the agreed ending state. Do not disable speech as routine cleanup, enable automatic startup as a convenience, or leave a temporary learning mode active. Provide the command reference in a format the user can actually access, with full key names and the resolved modifier rather than only unexplained abbreviations. If a capability remains unverified, say exactly what observation would settle it.

## Fictional, unexecuted illustration

A fictional user requests Narrator for reading a local help document and editing a scratch note. They want an existing voice through an already-connected headset, no new components, and no startup change. Supplied fictional settings show automatic extension downloads enabled. The proposed procedure would first hold activation for a decision about that possible download effect rather than promise a no-install trial.

In a separate hypothetical continuation after that boundary is resolved, the supplied observations say the user hears the tutorial and can identify its controls. In the target app, a letter intended for the scratch note instead moves to a heading. That supports investigating focus and scan mode; it does not establish a faulty keyboard or justify disabling all reader commands. The operator would identify the actual edit field, verify mode, repeat a short harmless entry and check the document's resulting text. Until that action and the return to reading are observed, the target editing path remains incomplete.

If only a speech-caption panel were available, the generated announcement could be recorded while headset delivery stayed unverified. If the user wanted the reader retained, a successful ending would preserve it rather than shut it down merely because setup finished.

This is original authored material. No screen reader, keyboard, application, audio device, setting, permission, download, document edit or live check was operated for this illustration.
