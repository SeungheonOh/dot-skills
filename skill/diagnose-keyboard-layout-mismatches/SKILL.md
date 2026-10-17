---
name: diagnose-keyboard-layout-mismatches
description: "Explain why physical keys produce unexpected characters by separating keyboard geometry, active input source, composition/modifier state and app or remote-session behavior, then verify a narrowly authorized layout correction without resetting language or accessibility preferences."
---

# Find why the keys type the wrong characters

Produce a small physical-key-to-character comparison and an evidenced correction or precise unresolved boundary. The legend printed on a key, the selected input source and the character inserted into an application are different things. A keyboard layout mismatch is not established merely because a symbol looks unfamiliar.

Use for swapped punctuation, unexpected letters, apparent dead keys, or text that changes with the selected language/input source. [diagnose-cross-app-paste](../diagnose-cross-app-paste/SKILL.md) addresses transferred clipboard representations; [text-encoding-recovery](../text-encoding-recovery/SKILL.md) addresses characters already garbled in files. [specify-keyboard-interactions](../specify-keyboard-interactions/SKILL.md) is a web-component design contract. This workflow does not redesign shortcuts, repair hardware, install remapping tools, capture raw keystrokes or bypass remote-session policy.

## Establish the exact mismatch

Use current evidence before asking for missing details:

- Authorized computer and OS/version, affected application/field, and desktop/web/remote variant
- Physical keyboard identity and layout/geometry where known; built-in versus external keyboard, with a few relevant key positions or legends
- Intended input source/layout and whether the user deliberately works in more than one language
- Actual selected input source at the moment of failure, including any composition/input-method mode
- Small, harmless expected-versus-actual examples with the exact physical key sequence and modifiers
- Whether the problem affects one key, a class of symbols, one app/document, one keyboard or only a remote session
- Existing authorized changes, unsaved work, accessibility preferences and any already-installed relevant remapping utility

Describe a physical key by position/legend and modifier separately from the expected character. “The at-sign key fails” is ambiguous when the active layout places that character elsewhere. Do not request a full keyboard serial number or photograph of the user's whole desk when a few key descriptions suffice.

If live device access is absent, use supplied observations and the official layout reference to narrow the hypothesis. Keep proposed comparisons unrun; screenshots of an input menu do not prove what was selected while an earlier character was typed.

## Protect text and input access

Test only a short synthetic sequence in an already-authorized local scratch document or safe field. Confirm focus before every sequence. Do not type probes into terminals, command palettes, password boxes, messages, search boxes or live forms where keys may execute, transmit or submit. Do not use a real password to demonstrate a mismatch, reveal credentials, or retry authentication to test a layout. A sign-in-only issue belongs with the user's secure sign-in flow.

The physical keyboard is part of the question. If a tool inserts text programmatically or simulates a different keyboard, label that evidence separately; it cannot establish the user's physical-key mapping. Ask the user to press the bounded harmless sequence when the tools cannot observe the required path. Do not install a key logger or request Input Monitoring, Accessibility, administrator or remote-control permissions just to diagnose text entry.

Preserve drafts and unfinished input-method composition before changing sources or switching apps. Do not use Copy as a test substitute, replace clipboard contents, collect typing history, or export learned dictionaries. A scratch document should not autosave to an unapproved shared destination.

An explicit correction request can authorize an ordinary in-scope layout selection. If the task is diagnosis only, propose the change first. Adding/removing input sources, downloading language features, changing global switching shortcuts, device remapping, accessibility controls or remote-session settings needs authority for that exact scope. Never remove the user's other languages as a cleanup step. Keep a usable input and pointer route throughout.

## 1. Record the input path before changing it

Trace only the observable layers:

```text
physical keyboard + key position
  → modifier/lock state and any known device mapping
  → active OS input source/layout and composition mode
  → local or remote-session translation
  → focused application's input handling or text substitution
  → inserted characters
```

For each relevant edge, keep observation separate from assumption. Record a key sequence as presses/releases, any visible composition/pre-edit text, and the final committed result. A dead key or input method may wait for another keystroke before committing text; no immediate character is not by itself a failure.

Inspect the active source while the affected field is focused. Recheck after switching apps or windows rather than assuming a source is global and unchanged. Note visible Caps Lock, Num Lock, modifier or input-method state without toggling them automatically. Preserve intentional accessibility behavior; a delayed or latched key is a hypothesis to inspect, not permission to disable an aid.

Use the current platform's reference for the observed layout. [Apple's input-source guidance](https://support.apple.com/en-om/guide/mac-help/-mchlp1406/mac) distinguishes input sources from the physical keyboard and provides selection through the Input menu. [Apple's Keyboard Viewer](https://support.apple.com/en-my/guide/mac-help/mchlp1015/mac) can show the selected layout and modifier-dependent characters. A viewer's rendered labels describe that source; they do not prove that a physical key reaches it correctly.

On Windows, [Microsoft's language and keyboard-layout guide](https://support.microsoft.com/en-US/Windows/Hardware/Input-Devices/manage-the-language-and-keyboard-input-layout-settings-in-windows) separates keyboard layout from display language and documents selecting installed layouts through the input-language control. Use a deliberate visible selection for a comparison rather than cycling through layouts without checking which one became active. Do not change the system display language to repair a punctuation mismatch.

## 2. Choose discriminating, harmless comparisons

Use the minimum comparisons that separate the suspected layers. Keep the physical device, active source, modifier sequence and test text matched where possible; state unmatched variables.

| Comparison | Useful interpretation and limit |
| --- | --- |
| Same physical sequence, same source, two safe local apps | If one differs, app/field handling or substitution is implicated; do not reset the system layout |
| Same app and keyboard, currently selected source versus the intended already-installed source | A repeatable result change supports a source/layout explanation; it does not establish persistence or hardware health |
| Physical key versus a supported onscreen-key action, with the same visible source | A difference narrows physical/modifier/remapping handling; onscreen success is not proof of a broken keyboard |
| Built-in versus already-available external keyboard, with matched source and app | A device-specific difference is useful; geometry or per-device mapping may differ, so hardware failure remains unproved |
| Safe local field versus the remote session, with each side's source recorded | A remote-only difference implicates that boundary; local success does not verify host translation |
| Characters are correct immediately but change after another key or word boundary | Inspect supported composition, autocorrection or text replacement before attributing the change to the physical layout |

Choose two or three discriminating symbols/letters plus an ordinary unaffected key. Test unmodified and the relevant modified sequence separately. Do not run a keyboard-wide shortcut sweep: combinations can close windows, submit work or invoke system actions. For composition-based input, use a meaningful short sequence and explicitly distinguish pre-edit state from the committed character. If the expected sequence is unclear, consult the exact input method's official reference rather than pressing arbitrary keys to flush it.

A display glyph can be misleading. If available through a safe existing inspection method, distinguish the inserted character from font rendering without copying private content or creating new code. For a synthetic sample, a supplied character value or code point can resolve lookalikes. If the character is correct but shown incorrectly, retain that result and investigate rendering/font coverage separately.

## 3. Apply only the evidenced correction

If the current source is visibly wrong and selecting the intended installed source is authorized, record the prior source, choose the intended one, read it back while the target field is focused, and repeat the same physical sequence. Use visible selection rather than an uncertain language-toggle shortcut. Do not simultaneously change keyboard type, global language, remapping and app autocorrection.

If the required source is absent, identify its exact name and the platform's supported addition path. Explain any download, language-list side effect or broader setting before obtaining the necessary authority. A layout name similar to the user's language is not a substitute for the required variant. Preserve all existing sources and their order unless the user explicitly requests a change.

For a known remapping utility, inspect only the relevant existing device/rule scope. Do not disable the utility globally, bypass managed rules or edit low-level mappings as an automatic extension of this task. For a remote-only mismatch, retain the local working configuration and report the specific host/client boundary; avoid changing both sides until their roles are established.

If the text is transformed by a particular app, inspect its named local rule or per-document setting. A one-time workaround can be useful, but document whether it bypasses the original path. Entering a character through a symbol picker is not a repaired physical-key mapping. Any lasting app setting change should be requested or specifically approved, with the old value preserved.

## 4. Retest the original context and preserve other languages

Repeat the affected physical key sequence in the same safe target app/field. Check the source immediately before typing, the final inserted characters, relevant modifiers/composition and an unaffected key. For an app-switch-dependent problem, switch away and back only after saving work and repeat the comparison; do not claim a permanent fix from a single successful sample.

If the request includes multilingual switching, verify the other requested source remains available and that a deliberate return to the intended source works. Do not log out, restart the OS or test the lock screen merely to extend coverage. Startup and sign-in persistence stay untested unless separately needed and safely authorized.

Restore a failed temporary selection to its recorded prior value and verify it in the relevant context. Leave a successful lasting change only within the user's authorization. If a setting write or source selection has an uncertain result, inspect it before repeating; do not stack new sources or keep cycling.

## Deliverable, acceptance and failure handling

Return the affected keyboard/app/context, exact expected and observed synthetic sequence, comparison results, supported input-path boundary, and the change or proposed remedy. Include old/final source values, restored temporary state, the physical versus simulated nature of the evidence, and any missing host/device observation.

Acceptance requires the intended source to be evidenced in the original context and the representative physical sequence to produce the expected committed characters, with relevant existing input modes preserved. If only an onscreen keyboard or injected text was tested, the physical path remains unverified. If only supplied observations were reviewed, label the result a diagnosis from that evidence.

Stop when the requested mapping is checked, a useful diagnosis-only finding is established, or the next discriminating step needs new permission, secure sign-in, unsupported hardware inspection or unavailable physical-key input. Do not respond to inconclusive results with factory resets, driver reinstalls, dictionary deletion or accessibility changes. Keep unresolved hardware, device mapping and remote-session possibilities explicit in a support handoff.

## Fictional example — unexecuted

A fictional user supplies a UK-labeled physical keyboard, a Windows input control showing US, and two safe local-app observations: Shift with the physical 2 key inserts `@`, while the intended result is the double-quote character. The same mismatch in both apps and the selected source support a layout hypothesis; they do not prove a hardware defect.

The proposed check is to select the user's already-installed United Kingdom layout, if authorized, and repeat the same physical sequence plus an unaffected letter in the original app. A later success would support that correction only after actual observation. Selecting a display language, deleting US, or typing a password is unnecessary. If only programmatically inserted text is available, the physical sequence remains untested.

This is an authored illustration. No keys, input methods, keyboard tools, applications, settings or remote sessions were exercised for this example.
