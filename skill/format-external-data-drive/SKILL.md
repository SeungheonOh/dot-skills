---
name: format-external-data-drive
description: "Prepare a new or intentionally repurposed external data drive with a supported partition layout and filesystem, exact-device destructive-action gates and verified write/remount behavior. Use for a usable data volume, not storage cleanup, damaged-drive recovery, boot media, live partition resizing or secure sanitization."
---

# Prepare an external drive for its actual use

Deliver the identified external drive as a usable data volume for the named computers and workload, with a short record of its layout, format, write/read checks and remaining limits. A formatting-success dialog establishes less than a mounted volume, and a mounted volume establishes less than files that remain readable after a safe reconnect.

This workflow covers a directly attached ordinary data drive that is new or deliberately being repurposed. It uses existing supported operating-system tools. It does not resize a live partition, preserve files through an in-place conversion, prepare a startup installer, operate a storage pool/RAID, repair a failing device or certify secure erasure. Memory cards and disks for cameras, recorders, consoles or other appliances need the manufacturer's device-specific preparation procedure.

Use [backup coverage planning](../plan-file-backup-coverage/SKILL.md) when retained data and recovery needs are undecided, [backup restore checking](../backup-restore-spot-check/SKILL.md) for an actual recovery sample, and [versioned backup setup](../configure-versioned-file-backup/SKILL.md) after the destination is prepared. Formatting creates no backup and does not configure future capture.

## Establish the target and acceptance requirement

Resolve the few inputs that change the operation:

- The exact computer/OS, connected external device and owner; enough physical identity to distinguish same-model drives
- Whether the request is a preparation plan or actual initialization/reformatting
- Whether the whole selected device may be replaced, or only a particular existing volume; do not expand a volume request to the parent device
- The computers and applications that must read and write it, expected largest files, required metadata and any stated encryption requirement
- The intended usable capacity, volume name and any required partition scheme or mount location
- What existing data must survive elsewhere, where its retained copy is, and what evidence the user requires before erasure
- The allowed small check files, target-computer checks and private result location

Prefer one user data volume for a simple whole-drive request unless an actual requirement says otherwise. The native tool may also create documented supporting partitions or an APFS container; those are not extra user data volumes. A multi-volume redesign or an ambiguous partial-drive request needs its own explicit layout decision before writes.

Do not choose an unencrypted format to satisfy cross-platform access when the user requires encryption. Report the conflict and identify the missing supported route. This ordinary formatting workflow does not configure encryption, enter passwords or recovery keys, remove protection, change security policy or install filesystem drivers. Credential entry and any new security configuration require their applicable user-controlled steps. Leave unexpected management or access restrictions intact.

## 1. Identify the physical device and all affected storage

Use a supported read-only disk inventory or the native disk utility. Record the external connection, manufacturer/model, available serial or hardware identity, reported capacity, current partition scheme, contained partitions/containers/volumes and current mount points. Keep full identifiers private; a masked suffix is sufficient for an audience-facing report when it still distinguishes the device.

Understand the hierarchy before selecting an operation:

- A physical device can contain several partitions and volumes; erasing its partition map can affect all of them
- A filesystem belongs to a volume or partition, while a partition scheme describes the device's layout
- APFS volumes can share a container's capacity; one volume's display is not an independent physical disk
- A drive letter, volume name, disk number or mount path is a current locator, not a durable hardware identity

Correlate the user's physical drive with the OS observation. When identity is still ambiguous, ask the user to identify the device or perform a safe connect/disconnect comparison after any active work has finished. Never pull an active drive, disconnect an unrelated backup, or identify a target by “the largest disk” or a remembered disk number. An adapter can expose its own identity instead of a unique media serial; retain that uncertainty rather than manufacturing a unique match.

Inspect every volume that the proposed operation would affect, using metadata first. Include hidden or unmounted partitions in the layout record. A drive absent from the file browser is not necessarily empty. “RAW,” “not initialized,” an unreadable filesystem or a format prompt is not evidence that no valuable data exists. Microsoft's [initialization guidance](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/initialize-new-disks) is for a new disk without existing data and directs problematic existing disks toward troubleshooting. If the user expected files, stop preparation and preserve the device for a separate recovery decision; do not initialize it as a diagnostic experiment.

Exclude startup/system/recovery disks, mounted disk images, shared production storage and devices belonging to a storage pool or array. If the identity or excluded-device status cannot be established, deliver the read-only findings and hold all layout changes.

## 2. Settle preservation before erasure

For a genuinely new drive, record the user's no-retention decision alongside the observed layout; do not invent a backup result. For a reused drive, account for the material the user wants kept and its separately retained location. A copy on another partition of the same physical device will not survive a whole-device erase. A shortcut, cloud placeholder or backup-success badge alone does not establish that the required payload can be retrieved.

Use existing suitable evidence or a separately authorized copy/restore check. At minimum, distinguish “user confirms no contents need retaining,” “retained copies verified to the agreed scope,” and “preservation unresolved.” Copying private files to another drive, shared folder or service needs the appropriate data/destination authority. Do not start a broad backup or silently retire historical backup versions just to clear this gate.

Save the device/layout record and the retained-copy evidence outside the target. Formatting can remove filenames and filesystem structures without offering normal Trash recovery. Treat data loss as irreversible for this workflow even when specialist recovery might sometimes be possible. There is no dependable undo button, and a picture of the old partition layout is not a backup.

## 3. Choose a filesystem and layout from the consumer requirements

Consult current official guidance for the actual OS versions and intended application. Record the chosen scheme, filesystem, case-sensitivity/encryption state, volume size/name and any nondefault allocation setting. Keep defaults that meet the requirement; do not change allocation units, partition offsets or access settings for an unmeasured performance claim.

Use the smallest applicable decision:

- **Mac-only ordinary data:** check that the intended macOS versions and application support the selected APFS variant. Ordinary APFS and case-sensitive APFS have different name behavior; do not introduce case sensitivity incidentally
- **Windows-only ordinary data:** choose a supported Windows filesystem that meets the application's requirements. NTFS and exFAT differ in retained features; a familiar name is not enough to choose between them
- **Ordinary files exchanged between supported Macs and Windows PCs:** exFAT can be an appropriate choice after checking both target systems and the required file properties; it is not a promise that native app libraries or every appliance can use the drive
- **Legacy or special requirement:** retain the actual consumer's documented constraint. Do not assume a format offered by the current computer is supported by the receiving device

Apple's [filesystem reference](https://support.apple.com/guide/disk-utility/file-system-formats-dsku19ed921c/mac) describes APFS variants, shared container space and Windows-compatible FAT/exFAT choices. Microsoft's [filesystem comparison](https://learn.microsoft.com/en-us/windows/win32/fileio/filesystem-functionality-comparison) distinguishes file-size limits and features such as hard links, named streams and ACLs. For example, a required 6 GiB single file rules out FAT32; an exFAT volume does not natively preserve NTFS ACLs or named streams. Do not call a drive suitable for a metadata-dependent replica merely because it stores the main file bytes. Use [metadata-transfer review](../audit-file-metadata-transfer/SKILL.md) when a later transfer must prove specific properties.

Choose the partition scheme separately from the filesystem. Apple's [scheme reference](https://support.apple.com/guide/disk-utility/partition-schemes-dsku1c614201/mac) distinguishes GUID Partition Map, Master Boot Record and old Apple Partition Map. Modern data-drive requirements commonly support GPT/GUID, but legacy consumers can require something else. Verify the named targets instead of selecting MBR merely because Windows is involved or inferring boot compatibility from successful data mounting.

If the existing healthy layout already meets the requirement, report that formatting may be unnecessary. Do not erase a working drive just to give it a new label or letter. A requested format change is not permission to shrink adjacent volumes or convert a disk type in place.

## 4. Review and confirm the exact destructive operation

Before any initialization, partition deletion, whole-device erase or destructive volume format, show the actual target and effects in plain language. Identify the hardware with distinguishing evidence, the selected parent/volume, every affected existing volume, the intended replacement layout and filesystem, the preservation decision and the loss of normal file recovery. Obtain the required per-action confirmation immediately before the irreversible action; a general “set up this drive” request or earlier planning approval is insufficient.

Do not imply that formatting securely sanitizes old information. Microsoft's [Disk Management guidance](https://support.microsoft.com/en-us/windows/experience/storage-filemanagement/disk-management-in-windows) says quick format creates a new file table without fully overwriting the volume. A successful quick format, empty directory or ordinary full-format result is not a media-sanitization certification. Secure disposal is a separate task with media-specific requirements.

Recheck the device identity and current hierarchy after confirmation and immediately before submission. A replug, sleep/resume, utility restart or new connected disk can invalidate a selection. Stop on a changed layout or identity rather than applying the old approval to a same-numbered device. Keep a final review dialog open while resolving a missing decision, and do not accept a warning that describes a broader scope than the approved one.

Use the OS's existing supported utility and the authorized privilege route. Do not weaken write protection, force-unmount active users, kill applications, elevate without authority or install partition software to get past a blocked operation. Save or close affected work through an approved normal workflow first. If administrative credentials are required, use the supported secure user handoff rather than asking for them in chat.

## 5. Perform only the approved native preparation

Read the actual utility state and current official steps; do not paste a remembered disk identifier into a destructive command. Prefer the visible native workflow for this bounded task. The following are route distinctions, not unattended command recipes.

### macOS Disk Utility

Apple's [erase/reformat instructions](https://support.apple.com/guide/disk-utility/erase-and-reformat-a-storage-device-dskutl14079/mac) use View > Show All Devices to expose the hierarchy. For an approved whole-device operation, the selected physical device determines the scheme control; selecting a child volume is a different scope. Reconfirm the selected device, approved scheme, filesystem variant and name in the final dialog before the confirmed erase.

If the user approved only one existing volume, do not move selection to its parent simply because the Scheme control is unavailable. Resolve whether a scoped native volume operation meets the requirement or the requested layout needs a new decision. Do not use Restore, partition deletion or a startup-disk recovery route as an equivalent shortcut.

### Windows Disk Management

Separate three states: a genuinely new uninitialized disk, allocated space containing an existing volume, and unallocated space. The native routes are respectively initialization, formatting the selected volume, or creating and formatting a new simple volume in the approved unallocated region. Some USB devices do not use a separate initialization step. Follow Microsoft's linked [new-disk guidance](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/initialize-new-disks) and [volume-management procedure](https://support.microsoft.com/en-us/windows/experience/storage-filemanagement/disk-management-in-windows) for the actual state.

Review the extent/size, filesystem, label, allocation choice and drive-letter assignment before the final action. A whole-drive replacement can require separately destructive steps; obtain the required action-time confirmation for each, based on the current target. Do not delete protected or unfamiliar partitions, use a blanket disk-clean command, change another volume's letter or convert to dynamic storage as an incidental workaround. If the supported simple-volume path cannot accomplish the accepted plan, stop at the exact blocker rather than broadening it.

### Observe completion

Submit once, retain the utility's completion or error state, and wait for the actual operation to settle. Do not start a second format because a control tool timed out. A disconnected UI or missing dialog is not evidence that the disk operation failed. Reinspect the target's current layout and filesystem before considering any retry.

## 6. Verify the resulting volume through actual use

Read back the resulting device identity, partition/container layout, filesystem and variant, volume name, mount location and capacity. Compare them with the approved plan. Report raw bytes or clearly labeled units when available; vendor capacity, filesystem overhead and displayed binary/decimal units need not match exactly. Unexplained missing capacity or an unexpected extra data volume remains a discrepancy, not something to fix by erasing again.

Use a small, explicitly authorized, non-sensitive check set in a uniquely named folder on the new volume. It can be newly authored text and a selected ordinary file relevant to the workload. Do not fill the drive, generate a huge file or copy private content merely to test a file-size boundary. If a required large-file check cannot be performed within the approved size/time budget, report it as untested.

For each check file, retain expected size and a content digest or exact small-text baseline outside the drive. Close the writer, reopen the saved file from the actual target and compare content. Check that the file was not saved to a fallback local path with the same folder name. A file-browser preview alone is weak evidence when it might be cached.

After all writers have completed, use the supported safe-eject/unmount control. If the OS reports the drive busy, preserve the state and resolve only the known authorized writer; do not force removal. Ask the user to reconnect when physical action is needed. Reidentify the physical device, locate the resulting volume even if its letter or path changed, and reread the same files against the external baseline. Record any automatic mounting limitation.

When cross-computer read/write use is part of acceptance, perform the bounded check on each named target that is actually available and authorized. Reading one file on the second machine does not establish its write support: save a separate approved marker there and read it back, then verify its persistence after a safe reconnect when required. Keep first-machine, second-machine and untested-target results separate. Documentation-supported compatibility is useful but is not an observed target test.

Leave check files in place unless their specific cleanup was authorized. Do not move the user's real collection onto the drive or erase retained copies after these checks. A tiny read/write sample is not a full-surface test, verified physical-capacity claim, reliability guarantee, speed benchmark or proof that every future application will work.

## Recover from partial or unexpected results

- **No operation started:** preserve the existing layout; resolve the exact identity, preservation or compatibility decision before proceeding
- **Operation response uncertain:** inspect whether the original operation is active and read current target state. Do not queue another erase or disconnect active storage
- **Layout changed but formatting incomplete:** record what exists now and what failed. Continue only a supported operation within the approved target after any required fresh destructive-action confirmation; never assume the original data is intact
- **Unexpected data or wrong device discovered:** stop further writes through the supported safe control if possible, preserve the observed state, and tell the user what is known. Do not try to recreate partitions, run repair or copy new data onto the device as an improvised undo
- **Readback, remount or I/O failure:** retain the failure evidence and hold use. Check identity and the reported connection state without repeatedly formatting; failing or damaged storage needs a separate recovery/support decision
- **Wrong filesystem, scope or unresolved target compatibility:** report the mismatch and remaining decision. Another format is a new destructive action, not a harmless retry

Formatting is not reversible by restoring the old label. If the user wants retained files restored afterward, use the separate authorized restore/copy scope, preserve the retained source and verify the result. Do not present that later copy as recovery of data that was never preserved.

## Deliver and stop

Return the exact device and volume references, approved versus observed layout/format, preservation status, operation result and per-target check evidence. Include the check-folder location, safe-removal route and the specific limitations that affect the intended use. Keep full hardware IDs and retained-copy paths out of any wider-facing report.

Acceptance requires the intended target and scope, the approved layout/filesystem, successful mounted write/read behavior, and the requested reconnect or second-computer evidence. Label intermediate results honestly: plan prepared, formatting completed but unverified, verified on one target, or ready for the stated checked use. Stop after that bounded result or a concrete blocker. This does not enable backup, grant sharing, change encryption, migrate a library or authorize disposal of old copies.

## Fictional, unexecuted illustration

A fictional user wants a reused 1 TB external drive for ordinary project files shared between two supported desktop systems. They need one 6 GiB video file and have verified their retained copies elsewhere. The drive currently contains two volumes, while the initial request names only one of them.

The workflow would hold a whole-device erase until the user resolves that scope. If the user then chooses the entire identified device, a supported scheme and exFAT for ordinary-file interchange, the final destructive confirmation would list both affected volumes. A FAT32 candidate would not meet the stated single-file requirement. The retained-copy record would remain outside the target.

Suppose the paper scenario later reports successful formatting and a small-file reconnect check on the first system, but the second computer is unavailable. The result would be verified only on the first system, with second-system read/write behavior and the large-file check untested. It would not claim universal compatibility or that the drive is safe to use as the only copy.

This is an invented, unexecuted illustration. No device, filesystem, account, application, disk utility, format operation, check file, reconnect or data transfer was accessed or performed for it.
