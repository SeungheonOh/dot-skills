---
name: restore-deleted-cloud-files
description: "Restore selected deleted cloud files or folders through native Trash or Recycle Bin, reconciling retained item identities, ancestor and descendant effects, destination collisions and returned access. Use for bounded undelete operations, not historical-version replacement, backup recovery, sync repair or whole-account rollback."
---

# Restore the selected deleted items, with their actual scope

Return the requested retained cloud objects to usable active locations and account for every selected item. Establish which deletion is being reversed, what the native restore operation brings back, and what other people can access afterward. A folder reappearing does not establish that its required contents returned; a same-named replacement does not establish that the original was recovered.

This workflow uses an existing provider's item-level recovery state. It does not recover permanently erased bytes, choose earlier contents of an active file, recreate records from memory, or rewind an account. Use [backup restore spot checking](../backup-restore-spot-check/SKILL.md) for an identified backup, [unsaved-editor recovery](../recover-unsaved-editor-work/SKILL.md) for a buffer or crash candidate, and [cloud-file conflict resolution](../resolve-cloud-file-conflicts/SKILL.md) for competing saved copies.

## Establish the selection and intended return

Resolve from the request and available evidence:

- Service, account/organization and exact personal drive, shared drive or site/library
- Selected item links or identifiers, original names/locations, and any known owner or deletion interval with timezone
- Whether the selection is named files, one folder as it existed before a particular deletion, or an explicitly identified set of descendants
- Required result: locate only, prepare a recovery plan, or restore the selected retained items
- Intended return location and audience; whether the original folder remains suitable
- Useful content anchors, an independent expected-item list if completeness matters, and known replacements or unsynced edits that must remain

Do not turn “restore this folder” into “restore everything ever deleted below this path.” Earlier individually deleted contents can belong to a different deletion episode. When the intended set is ambiguous, show the small relevant difference and ask; continue locating independent named items.

An explicit request to restore identified items to an established location authorizes that ordinary restoration within its known effects. Do not repeat the same approval. Resolve any additional audience exposure, unrelated descendants, overwrite, new destination or administrative operation before proceeding. A locate-only request does not authorize restoration. Keep private paths, filenames and deletion activity out of broadly shared reports.

## 1. Prove that the target is deleted, and locate its retained object

Use an available connected service tool when it exposes the relevant deleted-state listing, item lookup and restoration. Otherwise use the provider's supported interface through an authorized browser. Reading live files is not evidence that the connector can list Trash or restore an item. Do not invent unsupported methods, provision an app, or broaden credentials to fill a missing capability.

Match a candidate by the strongest available combination of service identity, original item ID, deletion-entry ID, original parent/path, owner, type and observed deletion time. Distinguish a recycle-bin entry's identity from the file identity it represents. A title and date can narrow candidates but do not settle two same-named objects. Use only the minimum preview needed for a remaining identity question.

Check the actual lifecycle before changing it:

| Observed state | Appropriate next step |
| --- | --- |
| Exact object is active but moved or renamed | Return its verified location; use an authorized filing workflow if relocation is wanted |
| Shortcut or shared-list entry disappeared, but its target exists | Distinguish the entry from the target; do not undelete or copy the target unnecessarily |
| Object cannot be opened because access was removed | Report the access boundary; a restore request does not grant another owner's rights |
| Selected object is in the relevant native bin | Record its retained identity and available restore control/capability |
| Selected object is absent from the inspected bin | Check the correct account/site, relevant pagination and supported second-stage location before concluding it is unavailable |
| Only an old local copy or backup exists | Preserve that as separate evidence; it is not the retained cloud object |

Missing search results are not proof of deletion. [Google's lost-file guidance](https://support.google.com/drive/answer/15701190) distinguishes wrong accounts, changed shared access and files that lost their original folder. Follow the relevant branch instead of treating all missing files as Trash candidates.

Record coverage of the bounded search and any inaccessible bin or page. If a second-stage bin requires a site administrator, prepare the exact item/site/deletion references for that person; do not acquire administrative access or contact them without authority. Keep official support recovery separate from an ordinary native restore, with no guarantee that it will recover an absent item.

Treat remaining retention as time-sensitive evidence, not a promise. Use observed deletion time and the selected account's current policy where available; an uncertain date cannot yield an exact expiry. Do not empty bins, change retention or buy an upgrade. If a requested item is available now, avoid unrelated account-wide investigation before its already-authorized restoration.

## 2. Work out the operation's real item and folder effects

Before restoring a folder, determine what the provider will restore with it. Separate the selected parent, descendants affected by that parent's deletion, descendants independently deleted earlier, and any active objects now occupying the former path. Build a small dependency map only when ancestors or multiple items make it useful.

Check whether a missing ancestor is an ordinary folder, a library or another container with different restore behavior. Restoring an ancestor can bring back additional records; restoring a child may instead recreate only the necessary path. Use documented behavior and the actual retained structure, not a universal parent-first rule. Do not restore an entire library to recover one file unless that broader effect is authorized.

For every affected branch, establish:

1. Which objects this one operation is expected to activate, including automatic descendants or recreated containers
2. Which required objects need their own restore and which excluded objects must remain untouched
3. Whether the original parent exists and whether the destination preserves the intended ownership and audience
4. How the service handles an occupied path, including auto-renaming, failure or a possible overwrite prompt
5. Which properties can be verified afterward: identity, native content, location, required history or links, and access

A retained-bin inventory defines the objects currently visible for recovery, not everything present before deletion. To claim an entire folder is complete, compare with independent pre-deletion membership evidence or the user's explicit expected set. If that evidence does not exist, restore the supported selection and describe historical completeness as unknown. Do not demand a full historical inventory for a straightforward named-file restore.

Check existing destination items by identity. A new file at the old name is separate work, even if it looks similar. Do not remove, rename or overwrite it to make room. If the provider creates a suffixed recovered name, preserve the returned mapping and verify both objects. If the available behavior conflicts with the user's naming or preservation requirement, hold that row for a choice.

## 3. Use the provider's actual recovery controls

These official starting points were checked on 2026-10-17. Recheck account-specific behavior when the visible controls differ. They are alternative routes, not a checklist to run across every service.

- **Google Drive:** In the correct account, open Trash, identify the selected item using its details and Trashed date, then use its Restore command. Google documents a 30-day Trash period. See [Drive recovery](https://support.google.com/drive/answer/1716222?co=GENIE.Platform%3DDesktop&hl=en). An already available Drive API route restores a selected ID with the `trashed` field set to false; shared-drive calls need supported shared-drive handling. The `explicitlyTrashed` field distinguishes direct trashing from a parent's effect, and `capabilities.canUntrash` reports the current user's restore capability. Inspect these where the tool exposes them, and verify affected descendants rather than assuming their resulting state. Google also notes that other users may retain access to an owner's trashed file: Trash is not an access-isolation boundary. See [Drive's deletion and recovery model](https://developers.google.com/workspace/drive/api/guides/delete).
- **OneDrive:** In the correct personal or work/school account's web interface, open Recycle bin, select the exact rows and choose Restore. Microsoft's current guidance describes 30 days for personal accounts and 93 days for work/school accounts unless the administrator changed retention. It also distinguishes the user's own OneDrive from content shared by someone else. Cloud-deleted and online-only files may be absent from the computer's bin; inspect the web bin rather than declaring them lost. See [OneDrive item recovery](https://support.microsoft.com/en-us/onedrive/restore-your-onedrive-files).
- **SharePoint or Teams channel files:** Locate the backing SharePoint site and its Recycle bin, select the intended entries and choose Restore. A missing item may require the site collection bin, subject to existing authority. The documented 93-day retention runs from original deletion across the two stages; moving to the second stage does not restart it. A deleted library must return before its file can, and restoring that library brings back its contents. Restoring an item from a deleted ordinary folder recreates its path without restoring all siblings. An occupied path can produce a numbered name. See [SharePoint's recovery and ancestor rules](https://support.microsoft.com/en-us/sharepoint/admin/restore-items-in-the-recycle-bin-that-were-deleted-from-sharepoint-or-teams).

Never substitute a drive-wide rewind for selected-item restoration. [Microsoft's whole-OneDrive restore](https://support.microsoft.com/en-us/onedrive/restore-your-onedrive) reverses a wider sequence of actions and sends later-created files to the bin. A similarly named Restore button can therefore have a materially different scope.

## 4. Confirm the returned access boundary, then restore narrowly

Inspect the item's retained permissions where available and the current destination's effective access. Include inherited, direct and link-based routes relevant to this return. Historical folder names or familiar people in a sharing pane do not prove that today's audience is unchanged. Use [shared-link access verification](../shared-link-access-verification/SKILL.md) if the access evidence requires deeper inspection.

If the instruction already identifies the items, destination and intended audience, proceed within that authorization. If restoration would expose content to a different or unresolved audience, state that effect and obtain the needed decision first. Sensitive content needs the specific recipient/destination approval applicable to it. Do not make the item public, regrant removed access, change inheritance or move it into a new shared folder to complete recovery. An owner's successful open later cannot establish another person's access.

For one clear item, a short before/after record suffices. For multiple items, retain a private operation list containing source/delete-entry identity, selected scope, destination, expected incidental containers, existing collisions, authority, preconditions and outcome. Recheck those preconditions immediately before each restore. If another person already restored or changed the item, inspect its current state instead of replaying an old action.

Apply the smallest supported restore to the selected objects. Prefer an exact-ID operation or deliberately checked native selection. Do not use Select all on a filtered bin whose hidden or paginated selection semantics are unknown. Do not implement undelete as download, reupload and deletion: that creates a different object and can lose native relationships.

Do not pause all clients, disconnect sync or alter automation to conduct a routine restore. If known unsynced work, an active deletion process or a monitored destination could immediately undo or consume the recovered item, hold that affected branch and resolve the specific operational boundary. A request to restore files does not authorize executing their contents, restarting jobs or notifying collaborators.

## 5. Read back recovery, location and membership separately

Read the result through a fresh service view or lookup independent of the selected Trash rows. A success toast and disappearance from the bin are not enough. For each selected item:

- Establish its active identity and bind it to the retained item; record any provider-created ID mapping rather than assuming identity survived
- Verify the actual parent, final name and usable returned link, including auto-renamed collisions or recreated folders
- Inspect the necessary native content and required structure without enabling macros, scripts or external refresh; distinguish unavailable preview from confirmed missing content
- Verify required history or relationships only when requested and observable; an opening file does not prove all versions or links survived
- Check current access against the authorized return, and distinguish inspected permission state from a recipient's observed use

For a folder or dependent set, reconcile expected selected identities against the restored membership. Check missing children and unexpected activations separately; matching counts can hide a substitution. Leave earlier excluded deletions alone. Verify that known live replacements remain intact. Do not claim the whole old folder was recovered when only the container or named subset was checked.

Cloud restoration and local synchronization are different results. If the user needs the recovered file on a particular connected device, inspect its item-specific state there after ordinary synchronization. Do not claim an offline device has caught up, force a placeholder download solely to improve a status report, or resolve a new sync conflict by discarding either copy.

## Uncertain operations, recovery and completion

If the restore response is lost or delayed, look up the exact retained and active identities, inspect the destination, and use any available operation status before retrying. Partial batches need per-item outcomes. Do not repeat a folder restore because one child is missing or select all remaining bin entries as a retry. If the state remains unknown, preserve that uncertainty and stop dependent writes while independent clearly scoped items continue.

If an unexpected item or audience returned, stop further restores and report the exact effect. Do not automatically delete the recovered item or remove permissions as rollback: collaborators may have edited it, and returning a file to Trash may not revoke access. Any authorized correction must first recheck the current identity, contents, audience and intervening activity. Retain the operation record and distinguish an attempted reversal from verified recovery.

Deliver the verified file/folder links and a concise accounting: requested items, identified retained objects, restored/read-back items, already-active items, held choices and unavailable or uncertain outcomes. State actual destinations, collision mappings, incidental containers, access checks, content or membership limits, and any device state requested but unobserved. If only a plan was prepared, say that no restoration occurred.

Acceptance for a named-item restore requires the intended retained objects active and usable at the authorized destinations, with required properties checked and no unexplained extra effects. A complete-folder claim additionally requires the expected membership to reconcile. Stop when those conditions are met, when all accessible supported recovery routes for the bounded selection are exhausted, or when a specific missing permission, scope decision or provider capability blocks further action. Deliver partial recoveries without calling unresolved items complete or permanently lost without evidence.

## Fictional illustration, unexecuted

A fictional user asks to restore two handouts deleted from a shared workshop folder, leaving an older discarded draft and a newly created same-named replacement alone. Suppose the native bin identifies the two handouts and shows that their ordinary parent folder was also deleted. The provider's documented child-restore route would recreate that folder without its other deleted contents; one restored handout would receive a numbered name because its former path is occupied.

The planned action would restore only those two identified handouts after verifying the returned audience. Readback would need to establish both content identities, the recreated path, the numbered-name mapping and preservation of the live replacement. The older discarded draft would remain excluded. If only the folder appeared after an uncertain response, the result would stay pending until the two exact children could be located, not count as two recovered files. No account, bin, file, restoration or application was accessed or executed for this illustration.
