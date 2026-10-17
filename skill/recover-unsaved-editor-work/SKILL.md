---
name: recover-unsaved-editor-work
description: "Recover a selected unsaved text or document-editing session from a live buffer, app recovery state, or local history into a separate verified copy, preserving existing files and reporting unrecovered changes honestly."
---

# Recover Unsaved Editor Work Without Replacing the Original

Use when recent work exists only in an open editor, disappears after a crash/closure, or conflicts with an older saved file. Prioritize preserving the most fragile available content, then identify and verify a recovered candidate. Produce separately saved work and a short recovery record; a recovery-pane entry or recent timestamp alone is not proof that the missing edits survived.

This workflow covers a selected text/code or word-processing document. It does not perform disk forensics, decrypt protected files, repair arbitrary application databases, merge a whole project, or recover browser form submissions. For retrieving known files from an established backup, use [backup-restore-spot-check](../backup-restore-spot-check/SKILL.md). For reconciling competing saved revisions after recovery, use [document-revision-reconciliation](../document-revision-reconciliation/SKILL.md).

## Establish what is at risk

Ask only what the current state cannot establish:

- Authorized computer, application/version, active profile/workspace, and local versus remote session
- Document identity/path or untitled-buffer label; whether it was ever saved; relevant file format
- Current state: responsive with visible work, unresponsive, already closed, reopened with recovery choices, or showing an older file
- Last known save, crash/closure sequence, and any explicit discard or subsequent restart/cleanup
- The missing work's recognizable anchors, such as a recent heading or paragraph, and whether their wording is certain or remembered approximately
- Existing local/cloud copies and autosave/recovery state already enabled, without assuming that a toggle guarantees coverage
- Approved private output location, enough storage, and whether that destination syncs or is shared

If no output location is established, offer a separate local recovery folder and obtain the needed choice. Do not default to a cloud-synced Desktop/Documents folder. A recovery request authorizes preserving the selected work within its permitted destination; it does not authorize overwriting the source, restoring a shared document in place, changing retention, or uploading drafts to a recovery service.

## 1. Stabilize before searching

Do not close tabs, select Discard/Don't Save, restart the app or machine, update/reinstall software, clean temporary folders, or change autosave settings to test a recovery theory. Do not repeatedly launch the app if recovery state may be changing. Leave existing recovery choices available until the useful candidates are safely saved and checked.

If the app is still responsive and the missing work is visible, preserve that buffer first; do not spend the next step searching disk for an older copy. If an in-flight save visibly progresses, avoid overlapping save/restore operations and record its eventual result. If the app is unresponsive, distinguish that from a confirmed crash. Observe available status and ask before a force quit that could destroy the only remaining copy. Do not attach a debugger, dump process memory, or alter live recovery files under this workflow.

For documents that may run macros, external links, project tasks, or save hooks, use a supported nonexecuting viewing/export route. Do not enable active content, trust a workspace, run code, or weaken protection to recover text. A plain-text salvage can be useful when richer recovery is blocked, but must be labeled with its losses.

## 2. Preserve the strongest available candidate

### A. The current buffer is available

1. Record the original document identity and whether the current buffer is unsaved or differs from disk. An unsaved-change indicator is evidence of state, not the complete change history.
2. Use the application's supported Save a Copy, Duplicate, or Save As into a new, noncolliding file in the approved destination, selecting the native format when structure matters. Inspect what the actual command does: some change the active document's identity. Never use a blind Save shortcut when that would overwrite the existing file.
3. Check the selected path and format before committing. If an unexpected upload, overwrite, format-loss, credential, or security prompt appears, stop and resolve that boundary. Do not accept it merely to finish the recovery.
4. Verify the saved candidate independently before closing the only live buffer. If the safe native route is unavailable, extract supported text into a fresh local file when authorized. Preserve characters and line boundaries, and explicitly list omitted formatting, images, comments, tracked changes, or other structures. Protect irreplaceable clipboard contents if copying is part of this fallback.

Do not use a long Undo sequence to search for missing text before preserving the current buffer. New edits can destroy a redo path, and a live buffer may contain work absent from every recovery candidate. If disk and buffer differ, keep both; do not choose the “newer” one solely from its timestamp.

### B. The app already closed or offers recovery

Use its supported recovery UI for the correct profile/workspace and selected document. Capture candidate labels/times and inspect their content without restoring over the current file. Save each materially distinct plausible candidate under a separate name. Do not dismiss other candidates as duplicates merely because their names match.

If opening the app is necessary for its supported recovery flow, establish that it is already closed and that startup will not invoke unapproved tasks or active content. Use the existing installation and relevant workspace/profile; do not create a new profile or reset state. A startup failure is a blocker to diagnose, not a reason to delete the recovery folder.

### C. Only recovery files or history remain

Locate the relevant recovery store through the app's current official documentation or its actual configured location. Standard-install paths may not apply to a portable build, remote editor, alternate profile, or redirected home directory. Search only the selected document and relevant store, not all user profiles or unrelated documents.

Prefer the app's supported preview/export. If direct copying of recovery files is needed, preserve source bytes and metadata in an approved separate location before attempting interpretation. Do not rename, edit, delete, or inject files inside the live recovery store. If a source is actively changing, use a supported consistent snapshot or wait for a stable completed candidate; do not claim that an arbitrary filesystem copy is an application-consistent recovery.

Record candidate provenance, source identity, observed timestamp with timezone, size, and a digest when applicable. A digest can bind a copied file to captured bytes; it does not establish that those bytes contain the latest edits. A lock file, journal fragment, or metadata record is not necessarily a recoverable document. If its format is undocumented or parsing would require execution, preserve it and escalate rather than improvising a repair.

## 3. Use the actual application's recovery model

These official starting points were checked on 2026-10-17. Recheck current product/version behavior if the visible UI differs. Do not change settings now and claim they protected work created earlier.

- **Visual Studio Code:** Hot Exit preserves unsaved work according to its configuration and exit context. Inspect the current state; do not close a live unsaved window to test the feature. The official documentation lists standard-install backup locations, which must be matched to the actual installation before use. See [VS Code saving and Hot Exit](https://code.visualstudio.com/docs/editing/codebasics#_hot-exit).
- **VS Code Local History:** Timeline can expose saved-file snapshots, with settings for retention, exclusions, size, and merging entries. Inspect/compare the relevant entry before any restore. Local History is not evidence that every unsaved keystroke was recorded, and a source-control commit is another distinct historical source. See [VS Code Timeline and local file history](https://code.visualstudio.com/docs/editing/getting-started/userinterface#_timeline-view).
- **Word recovery:** After an unexpected closure, Document Recovery may offer candidates. Review the available versions and save useful copies before editing or dismissing them. Microsoft's macOS guidance warns that choosing Don't Save can remove the AutoRecover file, so do not use a discard action as cleanup. See [Word recovery guidance](https://support.microsoft.com/en-us/word/recover-your-word-files-and-documents).
- **Word for Windows:** Where available, File → Info → Manage Document → Recover Unsaved Documents opens candidates that can be saved using Save As. The related Restore action for an earlier saved version overwrites the saved version; it is not a harmless preview. Prefer opening/comparing and saving a separate copy. See [recovering earlier or unsaved Word files](https://support.microsoft.com/en-us/word/recover-an-earlier-version-of-a-word-file).
- **Office AutoSave versus AutoRecover:** AutoSave can continually save changes to a OneDrive/SharePoint file; AutoRecover is a different crash-recovery mechanism. “I never clicked Save” does not prove the original stayed unchanged. Inspect actual file/version state without enabling cloud sync or moving the document. See [Microsoft's AutoSave explanation](https://support.microsoft.com/en-us/office/collab-files/what-is-autosave).

For another editor, use its vendor's current supported recovery workflow. Do not project VS Code's backup structure or Word's retention rules onto it.

## 4. Compare candidates against the missing work

Create a small candidate record only as needed:

```text
candidate: original path or neutral label
origin: live buffer / recovery entry / local history / saved file
source identity and observed time: ...
separate saved copy: ...
known missing-work anchors present/absent: ...
structure or content gaps: ...
verification and remaining uncertainty: ...
```

Compare known recent passages, beginning/end, significant sections, and document structure. For text/code, compare full text when practical without executing it; preserve encoding and line endings or disclose conversions. For rich documents, reopen the native copy and inspect required pages, tables, images, comments, or tracked changes. A successful open does not establish complete recovery.

If two candidates contain different useful edits, keep both and explain the difference. Do not silently merge, overwrite a collaborator's version, or choose a version from timestamps alone. Ask for the consequential selection when evidence does not resolve it. A user's approximate recollection is a search clue, not an exact checksum.

If only an older version survives, deliver it as partial recovery and identify the known gap. If the missing content cannot be independently specified, say that the candidate opens and contains the inspected material, while completeness remains unknown. Never reconstruct guessed prose and label it recovered text.

## 5. Verify the copy and close the loop

Read back the saved candidate from its final location, independently of an in-memory editor tab. Confirm path/identity, format, content anchors, and relevant structure. Reopening must remain nonexecuting; do not enable macros or links. For raw recovery-file copies, compare bytes to the preserved source when stable and supported, then separately verify the interpreted document.

Keep the original and recovery store untouched. If the source changed due to preexisting autosave or concurrent edits, report that evidence rather than claiming preservation. Do not delete older candidates, clear recovery panes, or apply an in-place restoration as automatic cleanup. Report remaining open buffers or recovery choices the user should retain.

Finish when a verified usable copy is delivered with its known coverage, the available candidates have been checked and the remaining content is unsupported, or the next meaningful step requires unavailable access/authorization. A frozen app awaiting a force-quit decision, encrypted candidate, denied directory, unstable store, or missing safe destination is a concrete blocker. State the exact blocker and preserve the current state; do not bypass it or promise complete recovery.

The final answer should identify the recovered file(s), which edits were verified, anything missing or uncertain, whether the original changed, and the next user decision if any. A procedure prepared from documentation must be labeled unexecuted. Prevention changes such as enabling autosave or a new backup service are separate from the recovery task.

## Fictional worked example — unexecuted

This invented scenario is a planning illustration. No editor, document, recovery store, or file was accessed or changed for this example.

Request: “My editor crashed after I added a section to an existing draft. Recover it separately; don't replace the saved file.”

Suppose a fictional recovery pane offers a 14:18 candidate and a 14:24 candidate, while the saved file is from 14:10. The missing section's known heading appears in the 14:24 candidate, but its final paragraph is absent. The user remembers writing that paragraph after 14:24.

The planned workflow would save both distinct candidates into the approved local folder, reopen the later copy safely, and compare its section with the known anchors. The result would be partial recovery through the inspected content, with the final paragraph still missing and the saved original retained. It would not treat the latest timestamp as proof of complete recovery or invent the missing paragraph. These are hypothetical outcomes, not executed checks.
