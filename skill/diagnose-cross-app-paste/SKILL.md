---
name: diagnose-cross-app-paste
description: "Isolate a failed or altered paste between applications by comparing source selection, clipboard transfer, destination acceptance, and format conversion, then verify a scoped remedy without exposing clipboard contents or clearing history."
---

# Diagnose a Paste Between Applications

Use when copied material does not arrive, arrives as an older item, loses required structure, or changes meaning in another application. Produce a small reproduction matrix and a verified transfer method or precise unresolved boundary. This is a source-to-destination transfer problem; a plain-text paste succeeding does not prove that a rich document, table, image, or formula was preserved.

Keep the task to the affected app pair and content class. For garbled characters already present in the original file, use [text-encoding-recovery](../text-encoding-recovery/SKILL.md). For a website failing more broadly in one profile, use [isolate-browser-profile-failures](../isolate-browser-profile-failures/SKILL.md). Clipboard sync, remote-desktop redirection, device pairing, and organization data-loss-prevention changes are separate workflows when those boundaries are implicated.

## Identify the transfer contract

Resolve from the request and visible state:

- Authorized computer and OS; source/destination applications, their desktop/web variants, and relevant versions
- Source selection type: text range, table cells, image pixels, file object, drawing, or app-specific object
- Intended destination field/object and whether it is editable, focused, or protected
- Actual copy and paste actions: menu, keyboard shortcut, toolbar, drag-and-drop, or history selection
- Expected preservation: exact text, whitespace, hyperlinks, formatting, editable objects, table shape, formulas, or values
- Symptom and scope: no insertion, stale item, wrong representation, partial content, or changed values
- Whether both applications run in the same OS session or cross a browser, virtual machine, remote desktop, or another device

Use a small sanitized sample with the same relevant structure. Do not require the user's entire document or clipboard history. If exact content cannot be shared, a synthetic fixture can narrow the transfer mechanism; label the real-content path unverified.

## Preserve before copying

Copying a test item replaces the active clipboard. First determine whether it holds the only copy of important work. Let the user preserve that work, or use an authorized local save/export appropriate to its content. A text-only clipboard snapshot cannot preserve every rich representation. Do not promise complete restoration from it. If preservation is uncertain, inspect menus/settings without replacing the clipboard.

Use Copy, not Cut. Create disposable test documents in already-authorized local destinations, without autosaving into a shared or cloud location. Do not paste tests into chat composers, terminals, search boxes, production forms, or spreadsheet cells that could execute/submit/transform them. For an actual-content test, confirm the destination and audience are within the user's authorization; existing clipboard sync or a browser app may transmit copied/pasted data.

Do not dump clipboard payloads, enumerate unrelated history items, enable history/sync, install a clipboard utility, clear history, restart clipboard services, or kill either app as first-line diagnostics. Avoid copying passwords, authentication codes, payment data, or other secrets into test surfaces. Preserve unsaved work before any approved restart. Do not bypass protected copy/paste, enterprise policy, or remote-session restrictions.

## 1. Separate selection and focus from transfer

Inspect the exact source selection and the source app's Copy menu state. An object frame being selected is different from text inside that object. A copy toolbar button may be app-specific. Confirm that the destination is the intended editable region, not a search field, navigation pane, read-only preview, or selected object.

Compare the application's visible menu action with the reported shortcut using synthetic content. If menu copy/paste works while the shortcut fails, investigate focus or the app's actual shortcut assignment before changing the clipboard subsystem. Do not rewrite system shortcuts or disable utilities merely because a key combination fails.

On macOS, applications determine which items can be copied/pasted and where; disabled menu items indicate the action is unavailable in that context. Apple distinguishes Paste from Paste and Match Style, which adopts surrounding style. Do not assume the latter is a universal plain-text conversion or that its shortcut is supported by every app. See [Apple's copy/paste guidance](https://support.apple.com/en-us/102553).

## 2. Use paired controls to localize the boundary

Choose an already-available neutral local text editor N, plus disposable scratch surfaces in source S and target T where supported. Use a unique harmless marker, such as `paste-probe-42`, and visibly distinguish each new copy from an older item. Do not construct scratch surfaces by editing a real document.

Perform only the comparisons needed to discriminate the symptom. Keep a compact record: source/sample, copy action, target, paste action, expected result, actual result, and any changed condition.

| Controlled result | Supported interpretation and next step |
| --- | --- |
| N → N fails with the marker | Recheck selection, menu action, and focus; the basic local path is not established |
| N → N works; N → T fails | Investigate target editability, supported content, field limits, or its paste command |
| N → T works; S → N fails | Investigate source selection/export or a boundary crossed by S; the target accepts ordinary text |
| S → N works; S → T fails | Investigate the S/T representation interaction; N may have consumed a different representation |
| S → S works; cross-app transfers fail | App-internal behavior works, but interoperable formats or a cross-app policy remain unresolved |
| Menu action works; shortcut does not | Focus/shortcut handling is implicated, not proof of a broken clipboard service |
| A previous marker arrives | Current copy may not have occurred, or another component may have replaced the clipboard; inspect sequence rather than repeatedly pasting |

A simple marker tests ordinary text only. After that path is understood, use a small synthetic sample of the failing class: a two-cell table, a short styled passage with a harmless hyperlink, or a small image. Keep source and destination sessions, content, timing, and selected paste mode comparable. Record differences when exact controls are impossible.

If another application or clipboard manager changes the active item, identify that observation with a synthetic marker; do not inspect unrelated content. A temporal association alone does not establish the component responsible. Do not disable security or management tools to obtain a cleaner result.

## 3. Test representation, not just appearance

On Windows, one copy can expose several clipboard formats, and the receiving application chooses a representation it supports. A plain-text intermediary therefore changes the transfer, rather than transparently testing the original rich paste. See [Microsoft's clipboard-format explanation](https://learn.microsoft.com/en-gb/windows/desktop/dataxchg/clipboard-formats).

Inspect the destination's supported one-time paste choices before changing global defaults. Compare ordinary paste with a named alternative on the synthetic fixture. Verify the property the user needs:

- **Text:** exact characters, line breaks, whitespace and end-of-selection completeness; inspect actual text when display alone is ambiguous
- **Links:** visible label and destination, without following the link; matching labels can hide changed targets
- **Tables/data:** row/column shape, leading zeros, dates, formulas versus displayed values, and whether a linked object became a static copy
- **Images/objects:** pixel/image content versus a file reference, editability, clipping, and whether required structure survived
- **Formatting:** headings, list numbering, emphasis, and directionality where relevant; a similar screenshot is not a semantic comparison

Word's Keep Text Only deliberately discards formatting and nontext elements and converts tables to paragraphs. It can be appropriate for a text-only goal but cannot satisfy a requirement to preserve an editable table or picture. Use the one-time option for comparison rather than changing all future pastes. See [Microsoft's Word paste options](https://support.microsoft.com/en-us/word/control-the-formatting-when-you-paste-text).

If a browser toolbar action fails but a normal user-initiated paste works, record the exact UI difference. Inspect the current app/browser documentation and existing permission state before attributing it to clipboard permission. Do not automatically grant site clipboard access, install a copy/paste extension, or disable browser safeguards.

## 4. Apply the smallest authorized remedy

Choose a remedy supported by the comparisons: correct the selected source region, focus the intended destination, use the app's supported menu action, or select a one-time representation that satisfies the transfer contract. If a file-based export/import is needed to preserve structure, explain the new file, destination, possible conversion loss, and any upload involved before proceeding beyond existing authorization.

Do not silently accept lossy conversion. If text-only is the only working path and the user needs rich structure, deliver that finding and the remaining choice. A successful alternative is a workaround unless the original copy/paste path was repaired and retested.

Persistent settings changes, app restarts, and software changes require the applicable permission and preservation plan. Record prior values, change one justified variable, and restore failed temporary changes. Do not reboot as an evidence-gathering step: Windows clipboard history normally loses unpinned entries at restart, and history/sync is a separate feature from the current paste operation. See [Microsoft's clipboard guidance](https://support.microsoft.com/en-US/Windows/Apps/using-the-clipboard).

Repeat the original requested transfer with a safe representative sample, then with the intended content only if authorized. Check the actual destination result against the preservation contract. Stop when the requested path passes, a useful diagnosis is established, or the next discriminating step needs unavailable access/permission. Unchanged tests without a new hypothesis are not progress.

## Report and failure handling

Deliver the affected app pair, reproduction steps, smallest useful test matrix, supported boundary, and working method or precise blocker. State whether actual content or only a synthetic fixture was checked. Include remaining format loss, current clipboard limitations, changed/restored settings, and any disposable files left behind. Do not delete saved files or history as automatic cleanup.

- **Policy/protected-content message:** Preserve the exact sanitized message and escalate through the authorized owner; do not use an intermediary to evade the restriction
- **Remote/device boundary:** Identify where local transfer succeeds and redirection fails; leave pairing, sync, credentials, and remote policy unchanged
- **Unpreserved work or clipboard:** Pause destructive/overwriting tests and report the safe next preservation step
- **Intermittent replacement:** Preserve the marker sequence and observations; do not name a culprit without evidence
- **No safe scratch target:** Provide a reproducible procedure and mark it unexecuted rather than testing in a live submission surface

## Fictional worked example — unexecuted

This is an invented illustration. No clipboard, app, document, or setting was accessed or changed for the example.

Request: “A small table copied from my notes app becomes one paragraph in my report. I need the table to stay editable.”

Suppose fictional controls show plain text copying normally in both directions. A synthetic two-row table arrives flattened under Keep Text Only, while the destination's ordinary rich paste preserves both rows and columns. Inspection of a hypothetical saved copy confirms the cells remain editable.

That evidence would support a paste-mode mismatch for this app pair. The proposed result would recommend the one-time rich paste and verify the real table only after the user authorizes its destination. It would not claim clipboard corruption, change global paste defaults, or call a flattened text workaround a successful table transfer. All results here are hypothetical.
