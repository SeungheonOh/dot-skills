# Native observations and source limits

Read the relevant platform section while diagnosing the selected existing external drive. These are source-backed distinctions, not instructions to run every linked procedure. Official pages can include destructive, repairing or broader operations that this workflow deliberately does not perform. Recheck applicability to the actual OS, model and visible tool state.

## macOS

Use the existing native observers to answer different questions:

1. System Information's relevant hardware interface can show whether a matching USB/Thunderbolt device is detected. A bridge entry alone does not establish that its disk media is available
2. Disk Utility's View > Show All Devices exposes the device/container/volume hierarchy. A simplified volumes-only view can conceal the parent structure needed to interpret the result
3. The selected volume's information and current mount state establish which filesystem, lock state and mount path the tool actually reports
4. Finder can directly access an already mounted volume even when the user's desktop/sidebar visibility choices hide its icon

Record exact available values without treating an absent field as a failed condition. Do not launch First Aid from the information view, change an encryption setting or open an unrelated volume to complete the record.

Primary references:

- [Apple: View all devices or only volumes](https://support.apple.com/guide/disk-utility/view-all-devices-or-only-volumes-dskud6b39edb/mac) supports the hierarchy/view distinction
- [Apple: Mount a volume that has been ejected](https://support.apple.com/guide/disk-utility/mount-a-volume-thats-been-ejected-dskutl1027/mac) supports the selected-volume Mount route, not a promise that any unreadable volume can be safely mounted
- [Apple: See the devices connected to your Mac](https://support.apple.com/en-ng/guide/mac-help/mchlp1039/mac) supports separate Finder General and Sidebar display choices
- [Apple: If you cannot move or copy an item](https://support.apple.com/guide/mac-help/mchlp1770/mac) supports native NTFS read-only behavior and distinguishes file-access considerations; its suggested permission changes are outside this diagnostic workflow
- [Apple: Repair a storage device](https://support.apple.com/en-us/102611) describes First Aid and the need for a current backup. The page's later erase suggestion is not a recovery authorization

## Windows

Use Device Manager for the matching device and any device-status error, then Disk Management for the current disk/volume layout. Preserve the relationship between the device and the displayed disk number; a later reconnect can change the locator.

Keep these observations separate: disk online/offline, recognized partition layout, reported filesystem, encryption/lock evidence, volume status, and assigned drive letter or mount path. Disk Management's “Healthy” label is not evidence that every sector or file has been read. An Explorer omission is not proof that no partition exists.

Only the normal missing-letter case is an in-scope Disk Management correction. The user must have the required authorized privilege route. If an existing application/OS volume, protected partition, missing disk, foreign/dynamic layout or unexplained offline state is involved, return the relevant evidence rather than copying a generic internet repair sequence.

Primary references:

- [Microsoft: Change a drive letter](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-a-drive-letter) documents the native assignment route, privileges, unsupported target types and application dependency warning
- [Microsoft: Initialize new disks](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/initialize-new-disks) scopes initialization to new disks without data and warns about initialization of in-use disks
- [Microsoft: Troubleshoot Disk Management](https://learn.microsoft.com/en-us/troubleshoot/windows-server/backup-and-storage/troubleshoot-disk-management) distinguishes missing, unreadable, offline and failed states. It includes advanced operations outside this workflow; status names alone do not authorize them
- [Microsoft: Manage disks](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/manage-disks) documents online/offline behavior, including ordinary newly discovered disks coming online with read/write access. Thus this workflow must not claim forensic no-write preservation merely because it did not edit a document

## Device-specific caveats

[Seagate's USB external troubleshooter](https://www.seagate.com/support/kb/usb-external-troubleshooter-003581en/) distinguishes interface detection, OS disk visibility and access. It discusses cable/port/power comparisons and a separate data-recovery decision when expected contents cannot be accessed. Use only applicable observations and bounded connection checks here. Do not import its driver-removal, reset, repair or formatting branches into the task.

[Seagate's One Touch with Hub explanation](https://www.seagate.com/support/kb/one-touch-with-hub-is-not-listed-in-explorer-or-finder-and-appears-to-be-uninitialized/) documents a specific locked-device presentation for security-enabled models of 12 TB or larger: the disk can appear uninitialized until unlocked. Confirm model, capacity and existing security state before using that explanation. It neither proves that another disk is encrypted nor authorizes security reset, credential retrieval or initialization.

When an observed status has several plausible causes, preserve the ambiguity. A manufacturer troubleshooting sequence is supporting evidence, not a causal test already performed on this device. A successful file read is evidence for that file and route, not a certification of the entire storage system.
