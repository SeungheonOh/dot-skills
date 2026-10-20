---
name: recover-damaged-office-file
description: "Recover a selected damaged saved Word document or Excel workbook into separate repair or salvage candidates, preserve the original bytes, and verify retained content and lost behavior before calling a copy usable."
---

# Recover a damaged saved file without replacing it

Use when an existing Word document or Excel workbook cannot open normally, reports unreadable content, or loses required structure during opening. Deliver the strongest supported separate copy and a concise account of what survived. A repair message, readable first page or familiar total is not evidence of complete recovery.

This workflow repairs or salvages an already-saved file. For newer edits in a live buffer or recovery store, first use [recover-unsaved-editor-work](../recover-unsaved-editor-work/SKILL.md). Use [backup-restore-spot-check](../backup-restore-spot-check/SKILL.md) to retrieve an existing historical copy, and [repair-spreadsheet-formulas](../repair-spreadsheet-formulas/SKILL.md) when the workbook is structurally usable but its calculation is wrong. Disk recovery, password removal, application reinstallation and arbitrary binary/XML surgery are outside this workflow.

## Establish the file and the minimum useful recovery

Inspect the supplied file and available context before asking questions. Identify:

- Exact file/version, its source, actual format, size and observed failure
- Authorized computer and existing application/version; a Windows recovery command is not evidence of a Mac or web equivalent
- Whether a more recent live buffer, autosave candidate, previous version or separate copy already exists
- Required content or behavior: for example, a final section, all worksheets, formulas, review markup or editable tables
- Independently known anchors or comparison material, such as a prior revision, approved PDF or source totals
- Permitted separate output location and whether it is private, synced or shared

A request to recover the selected file authorizes ordinary preservation and repair attempts on separate copies within the established destination. It does not authorize replacing the original, uploading it to a recovery service, enabling active content or changing access/security settings. Ask only about a missing destination, required property or scope decision that changes the work. Do not make a long questionnaire a prerequisite to preserving fragile content.

## 1. Distinguish damaged content from an unavailable file

Record the exact error and the point at which it occurs. Do not diagnose corruption from the filename or a generic “cannot open” message alone.

Separate incomplete downloads or cloud placeholders, an unavailable network path, access denial, encryption, unsupported format/version, and an application failure from evidence of damaged file contents. Inspect existing file/provider status and product support information. Use an already-authorized complete local copy when available; do not bypass permissions, rename an extension to force a parser, or clear a security warning.

If only this file fails while an already-open comparable file works, that supports a file-specific investigation, not a proven cause. Do not open unrelated private documents as probes. Repeated read errors or an unstable/disconnecting drive are reasons to stop ordinary repair attempts and preserve available evidence, not to run filesystem repair or repeatedly stress the device.

If more recent work is still visible in an editor, preserve that first through the linked unsaved-work workflow. Do not close it or reopen the damaged saved version over it. Keep current readable content even if a later repair might be more complete.

## 2. Preserve a baseline and separate the attempts

Keep the original untouched. Capture its identity, size and a content digest when supported. Make a stable, non-overwriting preservation copy in the approved destination and verify that it matches the captured bytes. For a cloud file, pin the retrieved revision; an unstable download is not a fixed repair baseline.

Start each materially different repair method from a fresh working copy of that preserved baseline. Name outputs so native repair, text/data salvage and historical restoration cannot be confused. Do not chain conversions through the only surviving candidate. Keep useful failed or partial candidates until the user chooses what to retain.

Before opening a working copy, inspect the available application route and known active-content risks. Do not enable macros, add-ins, external data, linked-object updates or a trusted location to make it open. Preserve existing security protections and file-origin markings. A repair request does not approve a protection bypass; if the supported repair route cannot run within the available boundary, hold that attempt.

Do not change shared calculation settings, reset templates, close unrelated documents, run vendor example macros or install a repair utility incidentally. These can affect work beyond the selected file. The official articles describe possible remedies, not blanket permission to perform all of them.

## 3. Attempt native repair before lossy salvage

Use the installed application's supported command and inspect the actual prompt. Microsoft's [Open and Repair guidance](https://support.microsoft.com/en-gb/word/open-a-document-after-a-file-corruption-error) directs supported desktop users through File → Open → Browse, then the Open button's menu; the Recent list does not provide that dialog. Select the working copy, not the preserved original. Recheck current guidance when the product or visible controls differ.

Record the chosen operation, application/version, input copy and actual result. Retain any repair or removed-content report privately. Follow its named affected parts into the candidate rather than treating “repaired” as a completeness claim. Absence of a report is not evidence that nothing changed.

If the candidate opens, save it under a new identity in a suitable native format, then verify it before trying another method. Do not overwrite the damaged source or silently switch to a format that drops required features. A format warning must be resolved against the recovery goal, not dismissed as routine.

For Excel, [Microsoft's workbook recovery guidance](https://support.microsoft.com/en-us/excel/repair-a-corrupted-workbook) distinguishes Repair from Extract Data. Try Repair for the native candidate; use Extract Data as a separate salvage route if repair does not recover the needed data. Values and formulas recovered through that route do not establish preservation of the complete workbook model.

If the app hangs, stop issuing repeated open commands. Preserve its state and use [recover-unresponsive-desktop-app](../recover-unresponsive-desktop-app/SKILL.md) for any needed closure decision. Do not force-close all Office processes as part of a file-repair loop.

## 4. Salvage only what the evidence supports

When a native candidate is insufficient, choose the next route by what the user needs:

| Needed outcome | Candidate and limitation |
| --- | --- |
| A previously intact revision | Retrieve it separately through an already-authorized version/backup route; identify its actual revision and missing later changes |
| Readable Word text | Use an available supported text-recovery converter on a fresh working copy; deliver text salvage, not a structurally restored document |
| Workbook values or expressions | Use supported data extraction; preserve worksheet/cell identity where recoverable and distinguish literals, formulas and cached results |
| A required feature absent from every supported candidate | Report it as unrecovered; do not invent its contents or claim a different format is equivalent |

Microsoft's [Word damaged-document guidance](https://learn.microsoft.com/en-us/previous-versions/troubleshoot/microsoft-365/microsoft-365-apps/word/damaged-documents-in-word) documents that Recover Text from Any File loses formatting and non-text objects; some field, header and note content becomes plain text. It can also leave uninterpreted material. Match that method to the installed version and retain the raw salvage separately before removing clearly identified debris. Do not delete unfamiliar text merely because it looks odd, infer reading order from a flat extraction, or recreate missing wording and call it recovered.

For workbook salvage, keep unavailable cells distinct from empty cells and zero. A displayed or cached total is not its missing formula, and matching that total does not restore dependencies. Do not fill damaged regions, copy neighboring formulas or refresh external sources to create an apparently complete workbook. Those are separate reconstruction decisions requiring source evidence and appropriate scope.

An older intact copy and a newer partial salvage may each contain useful content. Keep both and identify their differences; do not silently merge them or relabel the older revision as the latest. Stop escalating when remaining methods require unsupported tooling, protection bypasses or a wider task. Repeating the same failed conversion without new evidence is not additional recovery.

## 5. Verify content and behavior separately

Reopen the exact saved candidate, within the same safe execution boundary, rather than relying on the repair session's in-memory view. Check that it no longer needs the same repair simply to reopen, but do not equate that with complete recovery.

Compare against available source evidence and the minimum useful recovery:

- **Word:** inspect beginning/end, required sections, tables and their cell relationships, headers/footers, images, notes, comments and tracked changes when needed. Check section order and significant text, not just page count. Distinguish surviving displayed field text from an intact editable field.
- **Excel:** account for expected sheets, including required hidden sheets, and affected ranges. Inspect formulas versus literals, names, tables, cross-sheet references, key input types and required charts or validation. Follow every known repair/removal notice into its affected features.
- **Both:** compare recognizable recent edits and any independent source material. A prior version is evidence for its own contents, not proof that later changes never existed.

Use the expected population when it is known. Otherwise report observed sheets/sections and coverage without claiming completeness. Sampled checks establish only their inspected scope. Readable content can be a useful deliverable even while its original structure remains unrecovered.

Keep calculation separate from recovery. Inspect formulas and cached values without claiming recalculation. If an authorized compatible calculation route is available, use the calculation-boundary guidance in the linked formula-repair workflow and compare relevant outputs to independent inputs/rules. Otherwise state that calculation behavior remains unchecked. Do not turn a recovered values-only sheet into a calculation-ready model.

Verify source preservation and saved output identity. If the source revision changed or a save outcome is uncertain, inspect actual state before retrying. Do not undo someone else's changes or overwrite another candidate to conceal a failed attempt.

## Deliver the usable result and its limits

Return the selected copy or useful alternatives, along with:

- Original identity and whether preservation was verified
- Method and actual saved candidate for each useful result
- Content/behavior checked, repair-reported removals and known missing material
- What remains uncertain, including newer edits, calculation or unsupported features
- The one next decision or capability needed, if recovery is blocked

Use precise outcomes: “native repair candidate; inspected sections retained,” “text/data salvage only,” “historical revision recovered,” or “no usable candidate from the attempted supported routes.” Do not call a copy fully restored solely because it opens.

Stop when the requested usable copy and meaningful available checks are delivered, or the next supported recovery step requires missing evidence, access or permission. Do not delete the original, clear version history, enable a backup service or upload diagnostics as automatic cleanup. Instructions prepared without handling the file remain an unexecuted recovery plan.

## Fictional illustration, not executed

A fictional workbook's user needs three named sheets and an editable total formula. Native repair produces a copy that reopens, but its repair report identifies removed formulas on the totals sheet. The visible total matches an older PDF.

That agreement supports only the observed displayed number. The candidate does not yet satisfy the editable-formula requirement. A separate historical copy may supply an earlier formula, but it cannot establish the intended formula after later layout changes. The useful result is the preserved original, the readable repair candidate and the exact unresolved calculation, not a claim that the workbook was restored. Any source-backed formula reconstruction is a separate scoped step.

No file, application, repair command, recovery store or calculation was exercised for this illustration. The workflow was drafted from source inspection; it has not been demonstrated on a damaged document.
