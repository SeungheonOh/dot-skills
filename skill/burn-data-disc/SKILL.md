---
name: burn-data-disc
description: "Burn a bounded ordinary-file collection to one blank CD or DVD through macOS Finder, reconcile its live aliases with the intended payload, and verify the written disc after reinsertion. Use for a usable optical data copy, not audio/video disc authoring, boot media, disc imaging, app-library backup or erasing rewritable media."
---

# Burn a data disc whose actual contents are known

Deliver one identified written disc and a short file/readback record. Keep the selected source version, Finder's pending burn selection and the actual optical medium connected throughout. A burn folder is a reference collection; it is not yet a saved copy of its targets. A successful burn indication also does not establish that another computer can read the requested files.

Use an already available compatible optical writer and Finder's native data-disc route on the selected Mac. Keep this task to one blank disc and an agreed ordinary-file collection. Do not append to a used disc, erase rewritable media, author audio tracks or a playable DVD-Video, burn an operating-system image, clone a disc, or turn an app's live library into an ordinary folder copy. An existing approved ZIP may be a payload file, but preparing a dependency-preserving archive belongs to [project packaging](../portable-project-handoff/SKILL.md). A requirement for continuing capture and retained history belongs to [versioned backup setup](../configure-versioned-file-backup/SKILL.md).

## Set the disc and content contract

Resolve what changes the outcome, using the request and accessible source evidence first:

- The source Mac and installed macOS version, connected writer, selected blank disc type and physical disc identity
- Exact files/folders and saved revisions, recursive membership and exclusions; whether the user needs readable copies or a complete byte comparison
- Intended receiving computer/reader and application, especially when Windows, legacy equipment or a device other than a computer is involved
- Disc label and desired on-disc paths; any exact naming, metadata, file-size or confidentiality requirement
- Whether to prepare instructions, prepare a selection, or actually consume a blank disc; number of permitted attempts and available time
- Approved private staging/readback locations and whether an actual second-reader check is available and required

An ordinary small file set needs only a compact selection record. Do not invent an elaborate catalog or require cryptographic hashing when readable copies are sufficient. If “burn a DVD” means a disc for a living-room player, resolve that before using Finder: a video file stored as data does not itself establish DVD-Video playback. Apple's [disc-type troubleshooting](https://support.apple.com/en-az/guide/mac-help/mchlp2397/27/mac/27) likewise distinguishes a Finder data CD containing MP3 files from an audio CD.

Creating this copy does not authorize giving it to another person. Before any recipient-facing transfer, settle the exact files/data and audience. Preserve confidential paths in the private record rather than a public-facing label. Do not promise that source-folder permissions protect files on the disc. If encryption is required, hold until an explicitly approved, supported encrypted-payload workflow and recipient access path exist; do not invent a password field in Finder's burn dialog. Credentials, keys and recovery material are outside this ordinary-file workflow.

## 1. Establish the writer, blank medium and working capacity

Read the current official instructions for the actual system. Apple exposes supported optical writing formats through General > About > System Report > Disc Burning; inspect the particular connected device rather than assuming a reader is also a writer. See [identify disc-burning support](https://support.apple.com/guide/mac-help/mchlp1351/mac). Match the disc's marked format with that support and the intended reader's documentation. A drive's support for one DVD format does not establish every format or layer count.

Have the user identify and insert the intended blank medium when physical action is needed. Record a simple case label or other practical distinguishing mark; do not invent a unique hardware serial for a disc. If several writers are present, bind the operation to the intended writer and inserted medium. Treat a disc with existing content, an unfamiliar session or uncertain blank status as a hold. This guide does not erase or reclaim it.

Inspect the actual offered disc capacity and the Mac's available working space. Apple's [burning troubleshooting guidance](https://support.apple.com/en-il/guide/mac-help/mchlp2619/mac) separates disc free space from internal temporary-space needs. Account for any local staging copy as well. Use the selected medium and current UI's capacity result, not a filename total or marketing size alone. Do not claim an exact fit until the native route accepts the collection; directory and format overhead can matter.

If the collection does not fit, return the size mismatch and the smallest needed choice: a suitable available medium, a separately approved selection, or a different deliverable. Do not silently omit files, lower media quality, split one file or span several discs. New hardware/software, purchases, downloads, unexpected permissions and security changes need their own authorization. Leave a managed restriction intact rather than trying another writer utility to bypass it.

## 2. Bind the intended payload before creating aliases

Make an independent list of the selected relative paths and source locations. Include nested content when folders are selected, distinguish repeated names in different directories, and retain exclusions. A visible folder icon does not enumerate the files that will be copied. Inspect object types and references without following them into unselected locations.

Separate ordinary resident files from cloud placeholders, Finder aliases, symbolic links, application packages and other special objects. Confirm saved versions without discarding unsaved edits. Bring a requested cloud file local only through an authorized scoped download; do not hydrate an entire collection as an incidental burn preparation. Native libraries, actively written databases and packages need a supported export or a different workflow.

Pay particular attention to aliases inside selected folders. Apple's [Finder burn procedure](https://support.apple.com/guide/mac-help/mchl8addfd95/mac) says their targets are included too. This can bring in content outside the visible folder. Inventory each relevant alias and its target identity within the permitted read scope; do not assume its small alias-file size is its burn size. Hold broken, ambiguous or out-of-scope targets. Treat symbolic links separately instead of applying Finder-alias behavior to every link type. If required link semantics cannot be established, hold that object or use an approved plain-file package.

Choose a proportionate stable source:

- For a few closed ordinary files, retain their current identity/version and keep them unchanged until the operation is finished
- For a collection likely to change, prepare a new bounded local staging copy when authorized, outside synced/shared destinations and outside application watch folders. Reconcile it against the chosen source before using it
- For concurrent writers that cannot be paused safely or a native collection without a consistent export, stop at that source rather than calling a live directory a snapshot

Do not silently dereference links while staging. Include only approved targets, and record any deliberate change from a link to a regular file. Preserve originals. When exact bytes are required, retain a baseline digest and byte count for each ordinary payload file outside the disc; a later hash of the disc alone cannot prove agreement with the intended pre-burn source. Use [checksum-manifest verification](../verify-checksum-manifest/SKILL.md) if a supplied baseline needs format-aware interpretation.

## 3. Prepare the native selection and inspect its real targets

Use one of Finder's supported entry points, not a combination of unrelated burning tools:

- Insert the blank medium, choose Open Finder if prompted, and add the selected files to its window
- Or create File > New Burn Folder in the approved local location, name it, and add the selection there

The first route is documented in Apple's [data-disc procedure](https://support.apple.com/guide/mac-help/mchl8addfd95/mac); the second in [burn-folder creation](https://support.apple.com/guide/mac-help/create-a-burn-folder-mac-hold-files-cd-dvd-mchlp2806/27/mac/27). The latter command may be unavailable without a connected writer. Do not interpret its absence as a reason to install software or change system security. For this one-time operation, leave future blank-disc defaults unchanged; [Apple's blank-disc choices](https://support.apple.com/en-kw/guide/mac-help/mchlp2712/mac) distinguish the immediate choice from saving a default.

Review the actual pending collection, including names, hierarchy, source targets and resolved total. Finder's entries refer to originals; moving them into this window is not evidence of a completed copy. A moved, replaced or edited source can change what those entries represent. Revalidate targets immediately before burning, particularly when a prepared folder was reopened later.

Apply only requested naming/layout changes within the pending collection or approved staging copy. Resolve collisions without selecting an arbitrary winner. Preserve meaningful relative references; a renamed document plus unchanged links is not necessarily usable. If a project needs structural changes, finish the separate packaging work first rather than changing source files during the burn.

Keep an independent expected list outside the burn folder. Reconcile it with the actual selection so a missing alias cannot quietly shrink the denominator. If a checksum list is included as an approved support file, distinguish it from payload and retain its own baseline externally; do not require it to contain its own hash. Keep private diagnostic paths and exclusion notes off the disc unless requested.

## 4. Burn once and preserve the actual operation state

Recheck the source version, collection, writer, blank medium, label and native fit result. Confirm that actual burning and consuming this medium are within the request. Obtain any required confirmation for a newly encountered warning or broader effect before accepting it. A request to prepare a folder does not authorize the burn. Erasing an existing disc or deleting originals is never an incidental step here.

Start through the selected Finder burn control and follow its current prompts. Use a supported speed offered for this drive/media rather than forcing an undocumented setting. Keep the connection and power stable without changing sleep or power policy as an unrequested workaround. Do not eject, disconnect or move the drive while the write is active.

If Finder cannot resolve an alias, it may offer to continue without the item. Cancel this incomplete selection and repair its mapping before proceeding; do not accept a partial disc as the full requested set. Apple's [burn-folder guidance](https://support.apple.com/guide/mac-help/create-a-burn-folder-mac-hold-files-cd-dvd-mchlp2806/27/mac/27) describes that pre-burn choice and the empty-disc result of cancelling there. Do not generalize that result to cancellation after writing has begun.

Observe the terminal native result, including any validation phase, warnings and errors. A completed data counter or closed window is not enough. Retain the exact indication the tool supplies; do not claim a separately observed finalization, raw-sector scan or verification phase when the interface exposes none.

If the control session times out, inspect whether the original burn is still running before acting again. Do not queue a second attempt or pull the disc to test whether the first succeeded. When its state cannot be established remotely, hold and ask for local observation. After an interrupted write, treat the medium as potentially consumed and incomplete until inspected; do not promise that a write-once disc can be reset.

## 5. Verify from the reinserted optical copy

Once the writer is finished, close only the task's disc readers and use the supported eject control. Apple's [ejection guide](https://support.apple.com/guide/mac-help/mchl2f6b0645/mac) documents Finder ejection and busy-disc causes. Do not force removal, terminate unrelated applications or restart another person's session. A restart or logout suggested by troubleshooting is a separate interruption decision.

Reinsert the same physical disc and locate its mounted contents. Confirm the path is on that optical volume, not the pending burn folder, staging directory, recent-file entry or original file. A preview from a source alias cannot establish disc readability. Carry out the checks agreed for this task:

1. **Selection:** Reconcile the complete requested path list against the reinserted volume. Account for missing, renamed, duplicate-looking and unexpected payloads; separate documented filesystem support metadata from user files
2. **Readable bytes:** Read the required files from the optical medium. If full byte identity is required, compare every payload's observed size/digest with the pre-burn baseline and retain read failures. A sample or matching name/size remains narrower evidence
3. **Usability:** Open the requested representative documents with existing safe viewers, or verify a supplied plain-file package through its authorized extraction workflow. Do not run installers, scripts, macros or active document content just to demonstrate a successful burn
4. **Target compatibility:** When required and available, check the same disc on the named receiving computer/reader, recording the actual platform and file/app checks. The writer reading its own disc does not establish another reader's acceptance
5. **Source preservation:** Confirm the intended source/staging versions remain available and unchanged to the checked scope. The new disc does not authorize removing them

Do not compare the whole optical volume's bytes to a concatenation of file hashes: filesystem structures differ from payload contents. Do not equate preserved primary file bytes with preserved permissions, resource forks, tags, dates or link relationships. For an explicit non-byte requirement, use [metadata-transfer review](../audit-file-metadata-transfer/SKILL.md), or report the unsupported property. Successful reads today are not a longevity, archival-retention or damage-resistance guarantee.

Keep direct observations, user-reported second-reader results and documentation-backed expectations separate. If the requested target is unavailable, return the observed local result and leave target acceptance open. Do not call the handoff universally compatible from a generic vendor statement.

## Recover without hiding an incomplete disc

- **Selection prepared but no burn started:** retain the record and the current source bindings. A saved burn folder alone is not a backup. Recheck it when resumed
- **Capacity or unresolved-alias failure before writing:** correct only the accepted selection or supported prerequisite, then recheck the native state. Do not remove required items to obtain success
- **Write failure or uncertain ending:** preserve error evidence and the disc's incomplete status. A replacement blank requires a fresh identity and must fit the agreed attempt/material budget; do not repeatedly consume media without a changed cause
- **Reinserted contents missing or mismatched:** identify whether the expected source changed, the pending selection was wrong, or the read failed. Preserve the rejected result instead of adjusting expected hashes or relabeling the disc as correct
- **Works in the writer but not the intended reader:** retain the local result, check the exact reader/media support and observed error, and hold target acceptance. Do not erase, change region settings, install drivers or author a different disc format automatically
- **Unexpected private content burned:** stop distribution and report the precise known scope. Retain the disc under the user's control; this guide cannot recall it, delete a single written item or certify safe destruction

Corrected content normally means a new reviewed collection and a new blank disc in this workflow. Keep failed and replacement disc identities distinct. Retry only after identifying a supported correction, within the authorized budget; stop on recurring I/O failure, uncertain source/device identity or a new access boundary. Never delete source or staging files as an automatic cleanup step.

## Deliver the physical result and its limits

Return the disc label/identifier, source selection/version, on-disc entry point, writer/media type and actual burn/readback results. Include any intentionally changed names, membership exceptions, performed byte checks, second-reader result and remaining blocker. A short message can suffice for a small successful task; retain detailed private evidence only when it helps acceptance or recovery.

Distinguish `selection prepared`, `burn reported complete; readback pending`, `reinserted contents checked on the writing Mac`, and `requested receiving-reader check completed`. Acceptance requires the intended file set and the evidence actually requested, not simply a terminal burn indication. Leave the medium safely ejected when that is the agreed ending and give its physical location through the user. Shipping, recipient contact, source deletion, repeated copies and future backup schedules remain separate actions.

## Fictional, unexecuted illustration

A fictional user requests one data DVD containing a saved PDF guide and a folder of six ordinary image files. They want all seven payload files preserved exactly and readable on a named second computer. The selected folder also contains an alias to an unrelated private folder, and one image is still a cloud placeholder.

The proposed workflow would hold that selection before burning. It would not follow the private alias or count the placeholder as captured bytes. After the user approves excluding the unrelated alias and the requested image is available through an authorized download, the seven-file baseline would be bound to a new plain-file staging copy. The pending burn entries would then be checked against that copy.

Suppose the paper scenario later says Finder reported completion and all seven files matched their baseline after ejection and reinsertion, but the second computer was unavailable. The result would establish that local readback scope and keep receiving-reader acceptance open. The burn folder would remain distinct from the actual written disc, and no original would be deleted. If a file were missing, the result would remain incomplete even when the other six opened.

This original illustration is fictional and unexecuted. No computer, drive, disc, file, application, download, burn operation, readback or recipient transfer was accessed or performed for it. The guide describes later authorized work and supplies no runtime evidence.
