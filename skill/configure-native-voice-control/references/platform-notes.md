# Native voice-control setup notes

Read only the section for the selected platform, plus the targeting notes if overlays are needed. Check the official page's version selector and the actual installed controls before giving commands. These sources document product behavior; they do not grant permission to capture speech, install components, accept agreements or perform an action reached by voice.

## macOS Voice Control

Apple's [activation guide](https://support.apple.com/guide/mac-help/turn-voice-control-on-or-off-mchl63d14732/mac) places the feature under System Settings > Accessibility > Voice Control. First activation requires an internet-connected component download; after it finishes, the feature can operate without an internet connection. Its readiness indicator changes to listening. Establish download and microphone authority before enabling it, rather than assuming activation is a passive settings inspection.

Apple's [customization guide](https://support.apple.com/guide/mac-help/customize-voice-control-mchl9899c8a5/mac) documents recognition-language and microphone choices, including an automatic input selection, overlay preferences and enabled/disabled standard commands. Check relevant pre-existing custom commands without changing them. A standard phrase that has been disabled is different from a recognition failure; importing commands or running shortcuts is outside the ordinary setup here.

Apple's [command guide](https://support.apple.com/guide/mac-help/use-voice-control-commands-mh40719/mac) documents command-only interpretation, contextual command help, item-name/number overlays and spatial grids. It also distinguishes pausing from turning the feature off. English examples include “Command mode,” “Show commands,” “Show numbers,” “Stop listening” and “Start listening”; verify the selected language's actual phrases. While Voice Control is enabled, standard macOS Dictation is unavailable. Preserve an existing dictation workflow when deciding whether to enable this broader feature.

For a grid, inspect its current depth before saying another number: at the final refinement, Apple's guide says an unframed number triggers a click rather than further narrowing. Treat that as an action boundary. The same guide recommends headphones when using VoiceOver with Voice Control, to reduce the chance of synthesized output being interpreted as user commands. Adapt that advice to the user's available, authorized audio route.

## Windows Voice Access

Microsoft's [setup guide](https://support.microsoft.com/en-us/accessibility/windows/voice-access/set-up-voice-access) covers Windows 11 Voice Access, distinct from Windows+H voice typing and older speech-recognition tools. The supported route is Settings > Accessibility > Speech. Initial language-file setup needs a network; subsequent recognition is on-device. Supported language choices and the welcome flow can change. Read the actual first-run notices and any agreement before proceeding. A chosen language may need its own download even when another model is installed. Preserve the separate before/after-sign-in startup choices.

Microsoft's [getting-started guide](https://support.microsoft.com/en-us/accessibility/windows/voice-access/get-started-with-voice-access) distinguishes listening, sleep and microphone-off states. Sleep still accepts its wake command; microphone-off resumption requires a supported nonvoice action. The interface exposes recognition text separately from execution feedback. It also distinguishes command-only, dictation-only and combined/default interpretation. English examples include “Commands mode,” “Voice access sleep” and “Voice access wake up.” Verify their availability and the displayed mode on the target version. Do not confuse the command-only setting with capture being stopped, or the dictation-only setting with command availability.

Use the installed help or tutorial to learn only the required actions. An existing voice feature does not authorize new microphone privacy permissions. Do not widen desktop-app microphone access or change sign-in behavior to eliminate a setup warning.

## Item overlays and pointer grids

Microsoft's [item-interaction guide](https://support.microsoft.com/en-us/accessibility/windows/voice-access/use-voice-to-interact-with-items-on-the-screen) distinguishes activation from moving focus, supports name-based matching and shows numbered alternatives when several items match. It documents automatic overlay dismissal after certain successful commands or mouse/keyboard input. Reacquire labels after such changes; do not treat them as stable control IDs. Check monitor support in the installed version instead of changing the primary display to make an overlay work.

Microsoft's [mouse-control guide](https://support.microsoft.com/en-us/accessibility/windows/voice-access/use-the-mouse-with-voice) describes a grid number moving the pointer and refining the grid, followed by a separate click operation. Check pointer position and the harmless target before clicking. Its grid-reversal command is contextual; it must not be treated as a general rollback of document or external changes. Use only the bounded pointer method the task needs, not continuous movement or drag-and-drop as an unnecessary trial.

These notes are source-based preparation, not a record of operating either platform. No application, speech recognition, microphone, download or device check was executed for this material.
