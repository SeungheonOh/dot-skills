---
name: diagnose-external-drive-access
description: "Diagnose why an existing directly attached data drive is missing or unreadable, separate device detection, volume recognition, unlocking, mounting and file access, and verify an authorized narrow correction while preserving existing data. Use for external-drive access, not formatting, filesystem repair, deleted-file recovery, disk imaging or a hardware-health certification."
---

# Find where access to an external drive stops

Return an evidence-backed explanation and, when authorized and safe, a working route to the selected existing files. Preserve the drive's existing layout and contents. A light, connected USB device, recognized disk, mounted volume and readable file establish different boundaries; none proves the entire drive healthy.

Use this workflow for one existing, directly attached ordinary USB or Thunderbolt data drive on macOS or Windows. Keep startup/system disks, storage pools, RAID members, dynamic multi-disk volumes, forensic acquisition and failing-media recovery outside its operating scope. An unfamiliar drive or found USB device is not a suitable diagnostic input. Do not connect or execute its contents merely to identify its owner.

[External-drive preparation](../format-external-data-drive/SKILL.md) starts with an intentionally replaceable layout; this workflow starts with files that must remain. [Network-share connection](../connect-network-file-share/SKILL.md) addresses a remote server, [local-file search diagnosis](../diagnose-local-file-search/SKILL.md) assumes a file's underlying storage can be reached, and [backup restore checking](../backup-restore-spot-check/SKILL.md) retrieves a separately retained version. Do not substitute one for another just because the same folder appears in the file browser.

## Establish the device, symptom and preservation need

Resolve only inputs that affect the next step:

- The actual computer, OS/version and normal user session; the physical drive, its connection path and intended owner
- The exact failure: absent icon, absent disk, unlock prompt, mount error, missing folder, read failure or only a rejected write
- When this drive last worked, on which computer, any known format/encryption, and relevant changes such as a new cable, dock or enclosure
- Whether valuable files are expected, whether this is their only copy, and any physical damage, abnormal sounds, repeated disconnects or earlier I/O errors
- Whether the request is diagnosis only or permits a specific ordinary access correction; which existing harmless folder/file may be read for acceptance
- A private place outside the affected drive for the short result and any selected error evidence

Use available observations before asking questions. A screenshot showing an empty sidebar cannot answer whether the OS sees the physical device. If computer access is unavailable, produce a source-backed diagnostic plan from supplied evidence and label all unobserved states; do not claim to have inspected the drive.

Ask about valuable data before proposing any operation that assumes it is disposable. A missing backup does not prevent looking at already available metadata; it does change whether further access attempts are appropriate when corruption or instability appears. Keep the goal concrete, such as opening an existing reference folder, rather than restoring every possible disk feature.

## 1. Apply preservation stops before probing

Stop ordinary troubleshooting when the user reports impact/liquid damage, new grinding or repeated clicking, overheating, persistent disconnections, wrong or changing reported capacity, or repeated I/O failures. Do not stress the device with full reads, surface tests, benchmarks, repeated power cycles or a recursive hash inventory. Record the existing evidence and recommend a recovery/service decision before more activity. Do not open an enclosure, swap internal electronics, freeze a drive or try mechanical remedies.

Cancel or dismiss offers to initialize, erase, format, create a volume, convert a filesystem or repair automatically. An expected data drive shown as RAW, unallocated or not initialized is not established to be empty. Microsoft's [new-disk instructions](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/initialize-new-disks) explicitly concern disks without existing data and warn about data loss when initializing an in-use disk.

This workflow does not run First Aid, a repairing filesystem checker, partition reconstruction, a recovery scanner or a disk-imaging job. Those operations have different preservation and resource requirements. Apple's [repair guidance](https://support.apple.com/en-us/102611) requires a current backup and describes a procedure that can change filesystem structures; it is not a neutral preliminary read. A vendor page suggesting eventual formatting does not authorize it here.

Ordinary connection, unlocking and mounting are not forensic write-blocked acquisition. Even if no document is edited, do not promise the medium remained byte-for-byte unchanged. When the request requires untouched evidence, or a damaged drive contains the only important copy, hold normal mounting and file reads for a suitable preservation/recovery workflow. Do not configure a purported write blocker or low-level mount policy by improvisation.

For a stable known drive, inspect metadata through existing native tools. Do not install drivers or repair utilities, disable security software, change device policies, reset the controller, grant broad disk access, or elevate past a denied boundary. If an authorized native operation needs an administrator interaction, use the supported user handoff. Keep passwords, recovery keys and full hardware identifiers out of chat, screenshots and reports.

## 2. Bind observations to the same physical drive

Match the physical label/model, available distinguishing serial suffix, connection, reported capacity and current OS disk identity. Then map its partitions, containers and volumes to the current mount points or drive letters. A volume label is not a unique hardware identity. A USB bridge can identify the enclosure rather than the enclosed medium; retain ambiguity instead of treating its serial as definitive.

Recheck this mapping after a reconnect, computer change or refreshed device inventory. Disk numbers and mount paths can change. Do not operate on the first similarly named disk or reuse an old disk number after the device topology changes.

Record only the relevant hierarchy and observed status, for example:

```text
Physical device / connection / distinguishing evidence
Current OS disk reference / reported capacity / partition-map visibility
Selected partition or container / selected volume / reported filesystem
Lock state / mount state / current path or letter
Observation time / exact error / evidence source
```

Use the platform branch in [native observations and source limits](references/native-observations.md). On macOS, distinguish System Information's interface device from Disk Utility's physical disk and child volumes. On Windows, distinguish Device Manager's device from Disk Management's disk, partition/volume and path assignment. Missing access to one observer means that boundary is unknown, not absent.

Exclude other connected disks from actions. A parent device may have several mounted volumes; an apparently unused selected volume does not make physical disconnection safe for its siblings. Do not unplug an active backup or close unrelated work to simplify the inventory.

## 3. Locate the first unsupported transition

Collect the smallest observations that discriminate the likely causes. Do not run every row as a checklist once the relevant boundary is clear.

| Observed state | Useful interpretation and next bounded check |
| --- | --- |
| No matching device in the interface inventory | The computer has not evidenced detection through this connection; inspect the known cable, port, dock and required power before discussing filesystems |
| Interface device exists, but no matching disk is exposed | Detection stops before a usable disk object; a connected bridge does not prove accessible media. Preserve any device-status error and stop short of initialization |
| Disk exists, expected volume structure is absent/unrecognized | Record layout and lock evidence; consider documented hardware encryption or unsupported format before concluding corruption. Hold writes and repair |
| Expected supported volume exists but is locked | Establish the existing encryption product and intended owner; use its already available authorized unlock route with user-controlled secret entry |
| Supported unlocked volume exists but has no usable mount/path | Investigate native mount state or an absent Windows drive letter; a narrow correction may be sufficient if the drive is otherwise stable |
| Volume opens directly but is absent from the sidebar/desktop | This is a presentation issue; inspect the relevant visibility setting without rebuilding indexes or changing the filesystem |
| Directory opens, but selected file is denied or unreadable | Separate file-level permission, unsupported content and I/O failure. Do not change the disk layout or broaden permissions |
| Files read, but writes fail | Read access is established. Check documented filesystem capability and reported read-only state; do not remove protection or format as a diagnostic shortcut |

A listed device without a reported disk does not identify whether the cable, bridge, media or host is at fault. One successful alternate connection narrows the failing path; it does not prove a particular component defective. Report “worked through this route” rather than inventing a component diagnosis.

For a stable device without damage symptoms, an already-authorized ordinary connection check can compare one relevant alternative at a time: an appropriate known-good data cable, a compatible direct port, or the documented power arrangement. Preserve work and use supported safe removal first wherever the device is active. Ask the user to perform physical steps when needed. Do not substitute an arbitrary power supply or make repeated replugging the default response to errors.

Use another computer only when the user has authorized that computer and any exposure of the drive's data there. A drive mounting elsewhere can trigger background services or application prompts; a public/shared computer is not a neutral test bench. Do not download the drive's contents, enable sync or enroll it in backup during the comparison. Stop when the connection result settles the next decision or instability appears.

## 4. Distinguish locking and compatibility from corruption

Preserve exact status text and consult current official guidance for the known device/OS. “Unrecognized” describes the observing system's result, not a universal finding about the bytes.

A hardware-encrypted enclosure can withhold its data volume until unlocked. For example, Seagate documents that a locked, security-enabled [One Touch with Hub of 12 TB or larger can appear uninitialized](https://www.seagate.com/support/kb/one-touch-with-hub-is-not-listed-in-explorer-or-finder-and-appears-to-be-uninitialized/). This is a model-specific branch, not a reason to assume every unallocated disk is encrypted. Keep the original enclosure and existing lock state; changing hardware or resetting security is outside this task.

If the user requests access to an already protected volume, identify the existing supported unlock interface and the intended volume before handoff. The user enters and submits any password or recovery key through the secure route; do not retrieve, type, copy or retain those secrets. Do not enable automatic unlock, save credentials, remove encryption or reset a forgotten password. If the supported tool is absent or unlock fails, report that prerequisite rather than cycling guesses or initializing the locked device.

Check filesystem support for the actual OS and intended operation. Apple's [file-copy guidance](https://support.apple.com/guide/mac-help/mchlp1770/mac) notes native NTFS read-only behavior on Mac. A successful read with an unsupported write capability is not a failure to mount. An unsupported filesystem may be intact but unusable through this native consumer; do not call it corrupt or install a filesystem driver without a separate decision.

For a mounted volume with a file-level access denial, report the account, target and native denial without exposing private content. Do not take ownership, recursively change permissions, choose “ignore ownership,” add privacy grants or switch to an administrator account to bypass it. A usable folder with one missing file may need search or recovery work; it does not justify remounting the whole disk.

## 5. Perform only a supported narrow access correction

A diagnosis request authorizes investigation, not persistent changes. Carry out a correction when the user has requested the specific effect and the prerequisites above hold. Explain the actual missing permission or choice rather than asking to approve the entire investigation again.

Before a correction, retain its old state, selected volume identity, expected effect and recovery route outside the drive. Recheck identity immediately before acting. Hold if the tool proposes a broader action or reports a warning whose consequences were not approved. Accepting an “are you sure” warning needs its applicable confirmation.

### macOS: mount or show the existing volume

For a stable, recognized, supported and unlocked volume that is simply unmounted, use Disk Utility's native Mount action on that exact child volume when requested. Apple's [mount instructions](https://support.apple.com/guide/disk-utility/mount-a-volume-thats-been-ejected-dskutl1027/mac) describe making an ejected volume available again. Select the volume, not an erase/restore operation on its physical parent. One failed ordinary attempt supplies an error to classify; do not loop or force-mount it.

If the volume is already mounted and directly accessible, leave that state alone. When the user wants its icon shown, change only the relevant Finder General or Sidebar visibility control, preserving the old value. These are presentation controls; they do not fix a failed disk mount. Read back the chosen setting and the actual icon/target afterward.

### Windows: add a missing ordinary data-volume letter

Consider this only for the identified, online, recognized, unlocked ordinary data volume that lacks a usable assigned path and has no instability indicators. Exclude Windows/app volumes, EFI/recovery partitions, foreign/dynamic disks, offline-policy conflicts and storage-pool members. A “Healthy” status is not a complete hardware test.

Use Disk Management's Change Drive Letter and Paths route to add the authorized available letter. Preserve existing mount paths, other volumes' letters and disconnected network mappings; do not steal the user's preferred letter. Microsoft's [letter-assignment guidance](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-a-drive-letter) explains the required privileges and warns about application dependencies. A missing or disabled control is a blocker to explain, not a cue to create a new volume.

Do not globally enable automount, clear disk read-only attributes, change disk signatures, import foreign disks or bring an unexplained offline disk online as an incidental fix. These states need their actual cause and a separately scoped decision. If the intended existing drive already has a working path, use it rather than changing a letter just to match an old shortcut.

### Inspect an uncertain result before another action

Submit the selected correction once and observe the actual state. If a control tool times out, inspect the current mount/path and whether the operation remains active before doing anything else. An absent response does not establish failure. Stop on a new layout, unexpected volume, I/O error or instability. Do not run repair because the first correction did not work.

## 6. Verify access through the intended route

Reidentify the same physical drive and selected volume. Record the current filesystem/lock/mount state and path, then navigate directly to the authorized folder in the normal user session. Do not rely on a cached Recent Items entry, thumbnail or a same-named local folder.

Read one or a few selected ordinary files through an existing safe, nonexecuting method. Avoid launching programs, macros, scripts, external links or applications that autosave, create sidecars or alter a managed library. If safe read-only inspection is unavailable, leave the file-read check unverified. For a small text file, actual decoding is useful evidence; a full-drive checksum is unnecessary and may be harmful on suspect media.

Keep outcomes separate:

- Device detected: the observed device identity is present
- Volume recognized/unlocked/mounted: each state is independently evidenced
- Folder listed: the selected directory is accessible at this time
- Selected files read: only the named sample was actually readable
- Original route restored: the user's requested Finder/Explorer access now reaches the same selected volume

This diagnostic workflow does not create write probes. Reading files does not establish write support, byte integrity against an unavailable baseline, recovery of missing files or future reliability. If the user needs write acceptance or a preservation copy, define that separate exact operation and destination rather than silently editing the source.

Do not force a reconnect to complete a cosmetic checklist. If normal reconnection is part of the user's acceptance requirement, wait for a safe opportunity, confirm that all volumes on the physical device are idle, use supported eject, and ask for the physical reconnect. Reidentify the device before repeating the same bounded read. A busy-device warning is a stop, not permission to kill applications or pull the cable. A reconnect not observed remains unverified.

## Recovery and handoff

If a presentation change was ineffective, restore only that recorded setting when within the agreed recovery scope. If an added drive letter must be removed, first establish that no application or later user work now depends on it and obtain any needed permission; use the native path-removal control, never Delete Volume. An authorized mount can be reversed with a normal safe unmount once all dependent work is closed. None of these reversals can promise to undo incidental OS activity or erase prior data exposure.

For unresolved cases, return the last established boundary, exact error, relevant version/device identity, observations already made and the smallest next decision. A recovery provider, device manufacturer or administrator may need a different subset of that evidence. Prepare a minimized handoff; do not upload diagnostic bundles, send serial numbers or contact support without authorization for the recipient and data.

Acceptance for diagnosis is a supported boundary and actionable next step, including an honest unresolved result when evidence cannot separate causes. Acceptance for a requested correction additionally requires the intended volume and original access route to work to the agreed read scope, unrelated disk mappings preserved, and all remaining limitations stated. Stop at that result or at a concrete access, preservation or authorization blocker. Never call an initialized empty drive a successful recovery of the user's original files.

## Fictional, unexecuted illustration

A fictional user asks why their existing external project drive does not appear in Windows File Explorer. The paper scenario shows a stable matching physical device, an online basic disk, a recognized unlocked data volume with no drive letter, and no I/O warnings. The preferred letter belongs to a disconnected network mapping. The user permits an available alternative and reading one plain-text reference file; no formatting or write check is requested.

The workflow would preserve the network mapping, add only the approved alternative letter to the existing volume, verify that Explorer reaches the same volume and read the selected text file. Its result would be restored access to that sample, with whole-drive integrity and future reliability untested. If the same scenario instead showed RAW/unallocated storage with expected files, the letter-assignment branch would stop; initialization would not be an acceptable substitute.

This illustration is fictional and unexecuted. No device was attached, unlocked, mounted, formatted, repaired, read or written; no setting, permission, credential or drive letter was changed.
