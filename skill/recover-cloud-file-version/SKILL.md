---
name: recover-cloud-file-version
description: "Retrieve a selected historical version of an active cloud file as a separate copy, or restore its contents in place when authorized, preserving current work and distinguishing content recovery from history, permissions, publication and device synchronization."
---

# Recover earlier cloud-file contents without losing today's work

Use when an existing cloud document or uploaded file still exists, but a wanted passage, sheet, slide or earlier complete version has been replaced. Deliver the identified historical contents and, only when requested, make that version current on the same cloud object. A date in a history panel is a candidate locator, not proof that the wanted work is present.

This is item-level historical-content recovery, not [undeleting cloud files](../restore-deleted-cloud-files/SKILL.md), [retrieving an existing backup](../backup-restore-spot-check/SKILL.md), or [recovering an unsaved buffer](../recover-unsaved-editor-work/SKILL.md). Use [cloud-file conflict resolution](../resolve-cloud-file-conflicts/SKILL.md) for divergent saved copies and [document reconciliation](../document-revision-reconciliation/SKILL.md) when the result must combine selected old and new edits. Do not rewind an account, restore a whole library, repair malware damage or infer legal acceptance from a historical version.

## Establish the requested recovery

Resolve the following from the request and available evidence; ask only about a gap that changes the result:

- Exact service/account, active file ID or verified link, native file type and relevant drive/site/library
- Wanted version or missing-work anchors, with any known time interval and timezone
- Whether the user wants to locate, compare, recover a separate copy, recover selected content, or replace the active file's entire contents
- Current edits that must remain, required native features, and whether comments or detailed edit history are important
- Approved destination and audience for copies, and the existing audience/publication state if restoring in place

“Get the old paragraph back” does not necessarily mean replace every page with yesterday's document. If the requested scope is clear, follow it; if not, show the consequential choice between a separate historical copy, a targeted merge and whole-version replacement. Do not require an exhaustive inventory for one known paragraph.

An explicit request to restore a named version to the named active file can authorize that ordinary replacement when its effects are understood. Do not ask again merely because inspection is complete. It does not authorize unexpected irreversible history loss, broader disclosure, new permissions, disabling safeguards, or replacing other files. A comparison request ends with evidence, not a cloud write.

## 1. Bind history to the right active object

Use an existing connected tool if it actually supports the needed history, version-content retrieval and restoration. Otherwise use the provider's supported interface in an authorized browser. A tool that reads today's document is not necessarily able to retrieve an old revision. Do not invent a revision endpoint, register an application or expand credentials to fill a capability gap.

Record the active item ID, type, location, current revision evidence and observation time. Separate a shortcut, exported copy or same-named replacement from the original object. If the object is deleted, inaccessible or in a different account, resolve that state before searching the wrong history.

Inspect the relevant version interval, including available pagination and grouped history entries. Record version IDs where exposed; otherwise retain the native history locator, timestamp, editor/name evidence and distinguishing content. An editor name does not establish who approved the contents. A named version is a label, not an independent backup.

Do not conclude that a version never existed from an incomplete listing. Google's [Drive revision guide](https://developers.google.com/workspace/drive/api/guides/manage-revisions) warns that its API can omit older revisions even when the interface shows more. Use the supported history interface when that difference matters, without bypassing an access restriction. If the requested entry remains unavailable, report the scope inspected and the nearest evidenced alternatives; do not substitute one silently.

## 2. Inspect the wanted contents before choosing a replacement

Preview or retrieve the selected historical version without changing the active file. Compare the actual content against the missing-work anchors, not only the timestamp, editor or file size. Distinguish an exact known string from the user's approximate recollection.

For a small document, inspect the complete candidate. For a larger one, inspect the needed section and the surrounding structure, then state the limits of the comparison. Check properties that affect the user's goal: sheets and formulas rather than displayed totals alone, slide order and notes rather than a thumbnail, or tables and linked figures rather than extracted prose alone. History change highlighting can omit unchanged content; inspect the whole relevant region.

Classify the result before acting:

| Finding | Result or next step |
| --- | --- |
| Wanted material exists in one identified version | Recover that content through the requested copy or replacement route |
| Several versions contain different needed parts | Preserve those candidates and use the authorized merge scope; no automatic “latest wins” |
| Old version contains the missing section but lacks useful later edits | Offer or prepare the requested targeted reconciliation rather than silently discarding newer work |
| Only a metadata entry is accessible | Version located; contents unverified |
| Available version lacks some remembered work | Partial recovery; do not reconstruct guessed material and call it recovered |
| Needed history is absent or inaccessible | State the bounded coverage and supported blocker; enabling versioning now cannot recreate old versions |

Do not enable macros, refresh external data, run embedded scripts, or bypass protection to inspect a recovered file. If the only available viewer would do so, keep the recoverable copy separate and disclose the inspection limitation. A static export may recover wording while losing native functions; it is not a complete native-version restoration.

## 3. Choose the provider's actual version operation

These official starting points were checked on 2026-10-20. Use only the branch that matches the file and account, and recheck current documentation when the available controls differ.

### Google Docs, Sheets and Slides

Use the document's Version history to select the earlier entry. The supported **Make a copy** operation creates a separate historical candidate; verify the destination and do not select sharing with the same people unless that audience is approved. **Restore this version** changes the existing document instead. History viewing requires edit access. See [Google's native-document history guidance](https://support.google.com/docs/answer/190843?hl=en).

That same guidance warns that restoring an earlier spreadsheet version clears prior cell-by-cell edit history. If that history must remain, keep the original unchanged and recover a copy instead; do not claim the copy itself carries the original cell history. Before any in-place operation with this documented loss, explain the effect and obtain the required action-time confirmation. A generic request to recover contents is not enough to silently discard history. Do not delete or trim version history as cleanup.

### Uploaded files in Google Drive

Drive's file-version controls are distinct from native Docs history. Use **Manage versions** for the selected uploaded object. The documented download flow pins the chosen historical version with **Keep forever**, then downloads it; **Upload new version** replaces the selected object's current bytes. See [Drive file-version guidance](https://support.google.com/drive/answer/2409045?hl=en).

Pinning is a retention change, not a read-only preview. Confirm it when not already within the user's authorized recovery scope, and record it rather than silently changing retention. The [Drive revision API guide](https://developers.google.com/workspace/drive/api/guides/manage-revisions) says blob-revision downloads require this setting, retained revisions consume storage, and unpinned old revisions can be purged. Do not promise availability for a fixed period, automatically unpin afterward, or assume a native document follows these blob rules.

If the approved result is in-place recovery, first obtain and verify the selected historical bytes, then use the existing object's supported new-version upload route. Do not delete/reupload under the same name or create a duplicate and call it the original. This is a new current revision containing older bytes, not a return of the old timestamp.

### OneDrive and SharePoint files

Select the exact file and its **Version history**, inspect the wanted entry, and use its Restore command only for an authorized in-place recovery. [Microsoft's OneDrive guidance](https://support.microsoft.com/en-us/onedrive/restore-a-previous-version-of-a-file-stored-in-onedrive) says the selected contents become current and the former current version remains in history. Availability depends on the actual account and versioning configuration; do not project one retention rule onto every library.

[SharePoint's restore guidance](https://support.microsoft.com/en-US/SharePoint/documents-and-library/restore-a-previous-version-of-an-item-or-file-in-sharepoint) describes creating a new latest version from the selected older one. If an existing connector exposes [Microsoft Graph's restoreVersion operation](https://learn.microsoft.com/en-us/graph/api/driveitemversion-restoreversion?view=graph-rest-1.0), its success response has no content body: fresh item/content readback is still necessary. Do not install an SDK or request broader access merely to use that alternative.

If only a separate copy is requested, use an available historical download or supported read-only old-version view with Save a Copy. Do not temporarily restore over the live file just to export the old contents, then attempt to undo it. That exposes an intermediate change to collaborators.

For another provider, establish the same distinctions from its current official documentation: selected version retrieval, copy versus replacement, retained history, incidental metadata and required permissions. A similarly labeled button is not a cross-provider contract.

## 4. Preserve current work and check the replacement's effects

For a copy-only recovery, keep the active source unchanged. Save to a new, noncolliding authorized destination and check its actual access. Do not automatically carry the source's collaborators into the copy or put private historical content in a shared recovery folder. A native copy or export can omit comments, edit history or other structure; disclose those limits.

Before an in-place restoration:

1. Preserve the current cloud contents through an available supported copy/export or verified retained-version route appropriate to the required properties. Record how they can be retrieved afterward. If a separate preservation destination is needed but not authorized, ask for that destination rather than choosing a newly shared location.
2. Identify known unsaved or unsynced work on relevant open editors. Preserve it separately before replacement; today's cloud revision does not necessarily include it. Do not close editors, sign out or reset sync to force an apparently clean state.
3. Compare the historical candidate with the current file enough to identify later material that whole-version replacement would remove. An instruction to restore the complete named version need not become a new editorial approval round, but a newly discovered conflict with “keep today's changes” requires a choice.
4. Check the current access and relevant publication/automation effects. Older contents may include material removed for today's readers. Restoring content does not establish that historical permissions, approval status, published output or external dependencies were restored too. Hold an unexpected audience exposure or consequential publishing effect until authorized.
5. Establish any required preservation of comments, audit/edit history, signatures, metadata and native structure separately from main content. An unchanged file ID and recoverable bytes cannot prove those other properties survived.

Use [shared-link access verification](../shared-link-access-verification/SKILL.md) when the audience needs deeper inspection. Do not change permissions, stop an integration, republish, check in, approve or notify collaborators as an incidental recovery step. If one is necessary, identify that specific dependency and obtain missing authority.

Do not make a universal claim that “version restore is reversible.” Provider history may preserve content without preserving every kind of editing evidence. When an operation would permanently remove data, use a nondestructive alternative or obtain the applicable action-time confirmation before that exact operation, even if that data is not needed for the recovery.

## 5. Apply one current operation, then read the result independently

Refresh the active revision and selected history entry immediately before replacement. If the active file advanced, preserve and assess the new changes; do not apply a stale recovery plan over another person's work. A quiet-looking history panel is not a lock.

Use a revision-conditional restore only if the actual provider operation and available tool document that support. Do not attach an invented conditional field or assume a condition supported for ordinary uploads also applies to restoration. Without atomic protection, use the supported native flow, inspect current activity and disclose the remaining race when material. If the user's required no-overwrite guarantee cannot be met, recover separately and hold the in-place step. Do not revoke editors or acquire a lock beyond the approved scope.

Perform the exact selected copy or restoration once. Inspect any new warning under the applicable confirmation rules; an approval for ordinary recovery does not cover an unanticipated destructive effect. Keep sources and preserved candidates intact.

After a timeout or ambiguous result, inspect the same item, current revision, content and operation state before retrying. A restored version can have a new revision ID and present-day timestamp. Do not treat those as failure, nor equality with the old revision ID as the only success criterion. Repeating a restore may create another version or overwrite intervening edits.

Read the final destination independently of the history preview or editing buffer:

- Match the original active item ID for in-place work, or the new copy ID and approved destination for copy-only work
- Verify the selected historical contents and required structure using the same anchors used to choose the version
- Check the current revision and history evidence, including the recorded route to the pre-action contents
- Check the intended source-preservation and access properties; leave unavailable evidence explicitly unknown
- If the user needs a particular device, inspect that device's item-specific synchronized result separately. Cloud readback cannot certify an offline editor or local copy

When only part of a document was recovered, compare the candidate against the current baseline and verify that unrelated later material remains. Route a substantive merge through the reconciliation workflow instead of describing it as a whole-version restore.

## Recovery, delivery and stopping

If the wrong contents became current, preserve the observed post-action state and recheck for intervening edits before proposing correction. Restoring the pre-action version is another live replacement, not a harmless local Undo. Use it only within the actual recovery authority and after its effects are checked. Do not delete new history entries to hide a mistake or restore an entire old permission list.

Return the recovered copy or verified original link, chosen historical locator, actual current revision, what wanted material was verified, what current work was preserved, and any history/structure/access limits. Keep private document excerpts and temporary download URLs out of broadly shared reports. State the outcome accurately: located, compared, separately recovered, restored and read back, partial, or unknown.

Finish when the requested result has its corresponding evidence. A separate copy completes copy-only recovery but not a requested in-place restoration. A success response without readable contents remains unverified. Stop dependent writes when the version cannot be identified, safe preservation is unavailable, a required property would be lost, concurrent changes violate the agreed constraint, or a specific approval/capability is missing. Deliver usable partial recovery without claiming unavailable material is permanently lost.

## Fictional illustration, unexecuted

A fictional user asks to recover a deleted worksheet from an active shared spreadsheet while keeping today's revised budget and the original cell edit history. The earlier whole-file version contains the worksheet but predates the budget edits.

The workflow would reject whole-version restoration as conflicting with both preservation requirements. It would recover a separate historical copy in the approved private folder, verify the worksheet and its required formulas there, and keep the original unchanged. If the user also requests reintegration, the next step would be a scoped merge with dependency checks, not a blind tab copy or a claim that the old version is now current.

Suppose instead that a different user explicitly requests complete replacement of a selected uploaded file. If the supported upload times out, the result would remain unknown until the exact object's current bytes and revision can be read. A matching readback would avoid an unnecessary second upload; an unavailable readback would not justify claiming success. These are invented decision examples. No cloud file, version history, browser, API restoration, upload, merge, device synchronization or live workflow was exercised for this guide.
