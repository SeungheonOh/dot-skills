---
name: resolve-cloud-file-conflicts
description: "Preserve and reconcile selected conflicting or unsynced files in an existing cloud-drive client, distinguish local edits from cloud revisions and placeholders, and verify an authorized resolution without resetting sync or discarding competing work."
---

# Resolve a cloud-file conflict without losing either side

Deliver preserved versions, a supported resolution for the named file, and separate evidence for saved content and cloud synchronization. A green client icon, the newest timestamp or a filename containing “conflicted copy” cannot decide which edits the user wants to keep.

Use when an established cloud-drive workflow reports conflicting copies, cannot save local edits to an original, or shows different contents across selected devices. [Build a folder synchronizer](../build-folder-synchronizer/SKILL.md) creates or repairs a repeatable two-folder mechanism; this guide uses the existing provider's file identities, history and conflict controls. [Document revision reconciliation](../document-revision-reconciliation/SKILL.md) handles substantive content merging once safe copies exist. Do not build a replacement sync engine, migrate accounts or clean up an entire drive.

## Establish the exact conflict and preservation boundary

Resolve the provider, account/organization, client version, affected device(s), local path and cloud object ID or verified link. Include the relevant folder owner, sharing context, sync mode, error text and last observed successful state where available. Display names and identical paths across accounts are not stable identity.

Find the user's requested result: compare only, recover local work separately, keep both, merge a candidate, or replace a particular cloud object with an accepted version. Identify the safe output location and any allowed upload, overwrite or deletion. “Fix sync” does not choose a content winner or authorize removing conflicting copies.

Inspect only selected files and their relevant history. Preserve privacy in filenames, revision authors and screenshots. Do not send source files or diagnostic logs to a new service, support portal or collaborator without authority. If the provider or source is inaccessible, preserve the available side and describe the missing comparison; do not infer that the unavailable side is empty.

## 1. Preserve work before troubleshooting the client

Determine which work exists only in an open editor, a local unsynced file, a provider recovery location, or a cloud revision. For a read-only comparison, inspect stable existing versions without creating unnecessary copies. Before any operation that could replace or discard work, preserve the competing versions. Do not close or restart the editor/client, sign out, unlink the account, clear caches, reinstall, or invoke reset before the relevant unsynced work is preserved. Those steps can remove the only recoverable content.

Use the application's supported Save a Copy/export or provider download for the actual file type, within the authorized destination. Copy rather than move the source out of a sync folder: moving can propagate disappearance to the cloud or collaborators. Keep recovery copies outside the affected sync population and outside an unapproved shared/auto-uploaded folder. Verify the destination's actual location, available capacity and account before copying.

Give each distinct preserved version a new, noncolliding destination. Check for an existing file before saving, use supported no-overwrite creation where available, and never replace an earlier recovery copy. After an uncertain copy result, inspect that destination before retrying; an earlier existence check alone does not prevent a concurrent collision.

Distinguish these objects:

- An ordinary fully available local file contains usable bytes that can be preserved without editing its source
- An online-only placeholder, shortcut or cloud-native document pointer is not an independent content backup
- An actively changing package, database or application library may need a supported consistent export; copying its visible folder is not automatically safe preservation
- An editor buffer can be newer than both the disk file and cloud history; capture it separately without overwriting either

Opening a placeholder may download data and requires available storage/network within the task's authority. For cloud-native documents, use the supported native copy or export, disclosing any lost comments, history or native features. If a complete safe copy cannot be made, state that preservation is incomplete and hold risky client operations.

Reopen each preserved copy safely, without macros, external links or automatic execution. Check the content anchors that represent the disputed work and relevant structure. For stable ordinary files, supported byte comparison can establish copy fidelity; it cannot establish that every unsaved edit was included. Record source identity/revision, observation time, copy location and known gaps.

Provider-specific cautions must come from current official guidance. [Google's Drive for desktop troubleshooting](https://support.google.com/drive/answer/2565956?hl=en) warns that disconnecting an account deletes its Lost & Found contents, so any selected recoverable work there must first be copied to a safe location. Use the recovery location supplied by the client; do not sweep other accounts' caches or edit internal sync databases.

## 2. Separate divergence from a delivery failure

Build a short version map for the selected file. For each observed side, record cloud object identity, native revision if available, device/local path, known editor state, residency, relevant content difference and provider status. Keep all timestamps with timezone and treat clock differences as uncertainty.

Compare the actual bytes or native contents through nonexecuting readers. Identical names, sizes or modification times do not prove equal contents; different export bytes do not necessarily mean different native content. A common baseline must come from real history or explicit evidence, never an inferred oldest-looking copy.

Classify the case before choosing a remedy:

| Observation | Next meaningful step |
| --- | --- |
| Both copies contain distinct useful edits | Preserve both; prepare a format-aware merge or request the substantive choice |
| Local edits exist, cloud is older and upload is blocked | Preserve local work; inspect the exact reported upload blocker before any replacement |
| Same accepted content, different displayed status | Check object identity, upload acknowledgement and the selected client state; avoid unnecessary rewriting |
| Original was moved, deleted or unshared | Preserve local work; establish its current identity/access and whether restoration or a new destination is authorized |
| Folder-name collision or selective-sync issue | Inspect both populations and provider semantics; do not treat it as two versions of one document |
| Required side or history is unavailable | Keep unresolved; do not adopt the visible version as authoritative |

[Dropbox's conflicted-copy guidance](https://help.dropbox.com/organize/conflicted-copy) describes concurrent/offline edits and recommends comparing the versions. The conflict label identifies a collision, not editorial approval. For a folder labeled “selective sync conflict,” use the distinct [folder-conflict guidance](https://help.dropbox.com/sync/selective-sync-conflict); inspect membership before any consolidation.

A quota, unsupported filename, permission error or offline device can coexist with different edits. Resolve the evidenced blocker through the supported route only within authority. Do not buy storage, alter security settings, grant permissions, rename broad populations or switch accounts as an incidental repair.

## 3. Prepare the content decision separately from upload

When a candidate is requested, use the accepted baseline and user instructions to produce it separately. Without a proven common baseline, use a labeled pairwise comparison rather than pretending to distinguish additions from deletions. Compatible edits may be combined when the request permits that operation. Preserve conflicting values, deletion-versus-edit choices and unsupported native structure for review. Do not choose “latest wins” or treat a provider's default button as the user's decision. A compare-only request ends with the supported differences and choices, without preparing or uploading a merged file.

For binary or complex native formats without a safe merger, retain both copies and ask which specific version should become the working file, or hand off a comparison in the native app. Do not concatenate opaque files, flatten a workbook to CSV or strip comments merely to make the conflict disappear.

Verify the candidate against both preserved versions: required edits, protected wording, formulas/links and applicable structure must survive. Keep unknown coverage explicit. The merge result is still a local or saved candidate until the accepted destination and upload/replacement operation are established.

Before publishing, name the exact cloud object or new-file destination, whether the existing identity/history will be retained, which audience already has access, and the effect on collaborators. Uploading to a shared folder can expose all candidate content to its existing audience. If the candidate introduces new private data or a new audience, obtain the necessary approval. A request to save a separate recovery copy does not authorize overwriting the shared original.

## 4. Resolve through the existing provider, with current versions

Coordinate writes only as needed. If the user's affected editor or sync client must be paused temporarily, record the exact scope and restoration condition and obtain any missing authority. Pausing one device does not stop other writers or cloud-side changes. Do not contact collaborators or lock shared content without authorization.

Immediately before the authorized write, read the target object/revision again. If it advanced, compare the new changes before proceeding. Prefer a supported revision-conditional update or the provider's own conflict-resolution flow. Without a condition, use a deliberate quiet editing interval and disclose its weaker protection; a last-second read is not a lock.

Apply one selected resolution. Preserve object identity when the request is to update the existing item; deleting and reuploading can break links, history or access semantics. Do not rename conflict files into an occupied path, delete the original to remove an error, or upload repeatedly until an icon changes.

After an uncertain outcome, inspect the exact cloud object, relevant revision and local copy before retrying. A timeout may follow a successful upload. If a new conflict appears, preserve the newly divergent work and revisit the version map rather than replaying the accepted candidate over it.

## 5. Verify content, synchronization and remaining devices separately

If normal synchronization was temporarily paused for this operation, restore its recorded prior state once the agreed safety conditions are met, and read that state back. Do not start a previously paused unrelated client or leave the affected client silently paused. If resuming would propagate unresolved work, keep it held and state that exact blocker.

Read the accepted cloud object through an authorized provider route independent of the editing buffer. Verify its identity/revision, required contents and relevant sharing state. Then inspect the affected client's status for that item and reopen the local result without modifying it. A client-wide “up to date” indicator alone does not prove the selected version reached the intended object.

Where the task includes another connected device, check that selected device's observed version and contents after its normal synchronization. Do not wake or reconfigure an unavailable device or claim convergence there from the first device's success. An offline editor can later upload old work; record that remaining risk and the safe reconciliation instruction for its return.

Retain preserved sources and unresolved copies. “Keep both” may satisfy the task even though two visible files remain. Deleting superseded conflict copies, emptying Trash or changing version retention is separate from resolving the working version. When cleanup is specifically authorized, verify that each selected copy's needed content is retained and that recovery semantics meet the request before acting.

## Output, acceptance and recovery

Return the file identity, preserved versions, accepted content decision, saved candidate or verified cloud link/revision, per-device observations and any unresolved writes. State whether the outcome is preserved only, compared, candidate prepared, uploaded/read back, or observed across the requested devices. Avoid exposing full private paths in a broadly shared report.

For a read-only comparison, acceptance means the selected versions and supported differences are identified with unavailable portions visible. For a live resolution, acceptance requires readable preservation of competing work and evidence that the requested content reached the intended destination. It also requires the original conflict's relevant sync state to be checked. A cleared error with missing edits is failure; a verified candidate awaiting requested upload is partial completion.

If the published result is wrong, preserve the current post-action revision before considering recovery. Use the provider's supported prior-version or copy flow only under the restoration authority, check for intervening edits and read back the result. Do not restore over a collaborator's newer work or assume that undoing a local rename undoes cloud effects. Stop on an unresolved content choice, unavailable side, unsupported preservation or denied action, and report the exact boundary.

## Fictional illustration — unexecuted

A fictional user sees two workshop-plan files after editing offline. One has a revised venue paragraph; the other has an updated equipment list. The cloud original has the equipment list, and a local conflict copy has the venue change. Neither timestamp establishes approval for the other section.

The proposed workflow would preserve both in an authorized non-synced location, verify those copies, and prepare a separate merged candidate if combining the sections is authorized. Before updating the existing shared object, it would recheck its revision and approved audience. The cloud object and affected local copy would then need independent readback; an offline second laptop would remain explicitly unverified. No files, clients, accounts or cloud revisions were accessed or changed for this illustration.
