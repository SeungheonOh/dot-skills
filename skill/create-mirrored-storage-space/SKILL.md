---
name: create-mirrored-storage-space
description: "Create a new Windows two-way mirrored Storage Space from explicitly replaceable data disks, verify pool membership, capacity and ordinary file use, and leave a safe operating handoff. Use for a new local redundant data volume, not backup setup, existing-pool expansion or repair, boot-drive mirroring or failure testing."
---

# Create a mirrored Windows data volume

Deliver one new local Storage Spaces pool containing only the approved physical disks, one two-way mirrored space, and a usable formatted volume. Establish the configuration and bounded file-read/write evidence separately. A successful file save does not establish the redundancy layout; a healthy mirror status does not prove recoverability after every kind of failure.

This guide covers initial setup on a standalone Windows desktop using its existing native Storage Spaces interface. It does not operate on an existing pool, dynamic-disk mirror, hardware RAID, clustered storage, Storage Spaces Direct, startup/system disk or damaged drive. It does not purchase hardware, migrate the user's files, configure encryption or sharing, replace a failed member, upgrade pool metadata, or deliberately disconnect a member to simulate failure.

[Ordinary drive formatting](../format-external-data-drive/SKILL.md) prepares a single device and excludes pools. [Backup coverage planning](../plan-file-backup-coverage/SKILL.md) and [versioned backup setup](../configure-versioned-file-backup/SKILL.md) address retained copies and history. A mirror maintains current data across disks; it does not provide an independently retained historical version after an unwanted overwrite or deletion. If the actual requirement is recovering yesterday's file, route to backup rather than creating a pool.

## Establish the intended result

Resolve the inputs that change setup:

- The selected computer, Windows version/build, normal user session and authorized administrator route
- The physical disks the user intends to dedicate, their current ownership and contents, and the evidence distinguishing them from other connected storage
- Whether the task is a plan or actual creation, the required usable capacity and intended ordinary-file workload
- Any data that must survive elsewhere, the separate retained location and the agreed preservation evidence
- Pool, space and volume names, an available drive letter, and a supported filesystem suitable for the applications
- A small non-sensitive file-check scope, a private result location outside the target disks, and whether a normal later restart is part of acceptance

Do not infer permission to erase a disk from its being new to this computer, absent from Explorer, uninitialized or marked eligible for pooling. If preservation is unresolved, complete only the read-only inventory and plan. If computer access is unavailable, label the result as a plan; do not fabricate observed hardware, controls or completion.

## 1. Establish physical identity and eligibility

Inspect the native disk inventory and existing Storage Spaces configuration before opening a creation flow. For each candidate, record model, reported size with units, connection/enclosure, distinguishing hardware identity where available, current OS locator, partitions/volumes, and whether it already belongs to another pool or array. Keep full serials and private paths only in the authorized private record; masked suffixes can distinguish disks in a brief report.

Map the actual physical media, not only drive letters. Two different volume letters can be partitions on one disk. Two identical models may be separate disks but indistinguishable by model alone. A USB bridge can expose an enclosure identifier rather than the media's serial. When the mapping cannot establish which physical disks will be affected, stop for identification instead of selecting by capacity or list position.

Check exclusions before writes:

- Windows, boot, recovery, pagefile or other active system storage
- Existing pool/array members, shared storage, virtual disk images, unfamiliar encrypted devices or disks owned by someone else
- Devices with expected files but unrecognized layouts, I/O errors, unstable connections or signs of physical failure
- Devices whose individual identity is hidden by an enclosure or whose eligibility is unsupported

Do not initialize, reset, clean, convert or format a candidate merely to make it eligible. Existing-data problems belong in [drive-access diagnosis](../diagnose-external-drive-access/SKILL.md) or a separately authorized recovery workflow. A disk offered by the wizard is a possible target, not evidence that its contents are disposable.

Microsoft's [desktop Storage Spaces guidance](https://support.microsoft.com/en-us/windows/experience/storage-filemanagement/storage-spaces-in-windows) specifies extra disks beyond the Windows disk and explains that enclosure behavior can prevent USB eligibility. An ordinary Explorer volume is insufficient evidence of eligibility. Inspect the actual native selection and current hardware documentation; do not bypass a rejection with registry changes, controller reconfiguration or a disk-reset command.

When read-only inspection through the installed Storage module is appropriate, Microsoft's [Get-StoragePool](https://learn.microsoft.com/en-us/powershell/module/storage/get-storagepool), [Get-PhysicalDisk](https://learn.microsoft.com/en-us/powershell/module/storage/get-physicaldisk), and [Get-VirtualDisk](https://learn.microsoft.com/en-us/powershell/module/storage/get-virtualdisk) references describe pool, member and virtual-disk associations. Use those associations to resolve ambiguity, not an unfiltered list of every eligible disk as an automatic creation input. Confirm the commands are available on the actual computer; these references are not permission to install modules or administer a remote server.

## 2. Preserve data before dedicating disks

Make a disposition for every selected disk, including hidden or unmounted volumes: either the user confirms no contents require retention, or the required contents have a separately retained copy with the agreed evidence. Do not treat a blank label or a newly purchased enclosure as a no-data declaration.

A copy on another selected disk will also be at risk. Preserve required data outside all prospective members before setup. Use separately authorized copy/restore work when necessary; do not upload files, copy private material to a shared drive, or erase an older backup to make room without the required authority. Keep retained originals and backups after setup. A small marker-file test is not a reason to retire them.

Save the disk mapping, preservation disposition and proposed layout outside the new pool. Creation can destroy prior data structures and does not offer dependable normal undo. A screenshot of the old layout cannot restore its contents. If one candidate contains the only copy of valuable files, hold creation rather than promising that mirroring will preserve it in place.

## 3. Settle redundancy and capacity before committing

Keep the layers distinct:

1. Physical disks are the actual members being dedicated
2. The storage pool is the aggregate managed capacity
3. The storage space is the virtual disk with its own resiliency and size
4. The formatted volume supplies the filesystem and path used by applications

Choose **two-way mirror** explicitly. Microsoft's linked desktop guidance describes two copies and tolerance of one drive failure, with at least two disks. This documented design property is not a test result for the user's hardware. Do not silently select Simple to gain capacity, or substitute parity/three-way mirroring when a two-way configuration is unavailable.

Record separately the physical pool size, already allocated pool capacity, proposed logical space size, and formatted volume's reported usable/free space. State units. Do not advertise the sum of drive labels as writable mirrored capacity. For two equal-sized dedicated members, two copies imply a planning ceiling near one member's capacity before metadata and filesystem overhead; this is a sizing estimate, not an observed allocation. Unequal members or more complex layouts need the native capacity evidence rather than a guessed formula.

Keep the requested size within current physical backing after mirroring and overhead. Do not provision a larger logical size on the assumption that the user will buy disks later. Microsoft's [standalone Storage Spaces deployment reference](https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/deploy-standalone-storage-spaces) explains that thin provisioning allocates on demand and can over-allocate. That source describes server tools; use its capacity distinction without copying server UI or cluster instructions into a desktop procedure. Record the actual provisioning mode when exposed. A large free-space figure in Explorer does not independently establish free physical pool capacity.

If native controls do not reveal enough to justify the proposed size, resolve the read-only capacity evidence before creation. Do not fill a pool experimentally to discover its limit. Preserve headroom appropriate to the user's stated workload rather than inventing a universal percentage or performance promise. If the capacity goal cannot be met by the available eligible disks, report the mismatch and stop before writes.

Choose a filesystem offered and supported on the actual Windows edition and by the intended applications. Keep suitable ordinary defaults; do not promise ReFS availability or introduce Dev Drive, tiering, custom stripe parameters or unsupported tuning to follow an example. An encryption requirement cannot be silently dropped: its separate user-controlled setup must be resolved before real private data is placed there.

## 4. Confirm each destructive boundary and create once

Before the action that dedicates physical disks, present the exact disk identities, every affected existing volume, the accepted preservation disposition, intended new pool/mirror/volume, and loss of normal recovery for existing contents. Obtain per-action confirmation immediately before irreversible changes. General setup approval or the word “new” is insufficient. Handle any later destructive formatting boundary with its own applicable confirmation based on the actual selected virtual disk and current state.

Recheck identity immediately before submitting. Replugging, sleep, a utility restart or another attached device can change disk numbers and selection. If the observed scope differs from the approval, pause; do not apply stale permission to a same-numbered disk. Do not use “select all.” Administrative prompts need the authorized secure user interaction; never collect passwords in chat or weaken storage/security policy to proceed.

Use the observed native interface and current official procedure. In the documented desktop sequence, opening Storage Spaces leads through adding a named pool and selected disks, creating the named space with resiliency and size, and creating/formatting its volume. Exact controls differ by build. Treat this as three state transitions, not a blind sequence of clicks:

- **Pool commitment:** verify only the approved physical disks and the new pool's name; keep any existing pool untouched
- **Space commitment:** verify this new pool, the intended name, two-way mirroring and the accepted logical size
- **Volume commitment:** verify the resulting virtual disk, accepted label/filesystem/size and an actually available letter

Preserve existing local letters and disconnected network mappings. If the requested letter conflicts, use an approved alternative rather than reassigning another volume. Do not manually initialize an underlying pool member in Disk Management when a new volume is not yet visible.

Submit each operation once and observe its completion or failure. If the controlling tool times out, inspect the current native state before retrying. A pool may exist even when the response was lost. A created pool without a space is a partial result; repeating pool creation or deleting everything to start over is not a safe retry.

## 5. Verify layout and bounded ordinary use

Read back the associations from the intended volume through its space and pool to the physical members. Compare actual versus approved disk membership, names, two-way resiliency, logical size, filesystem and letter. Check reported health and operational status at each relevant layer and whether storage work remains in progress. Do not declare ready while a member is missing, the layout is ambiguous or warnings are unresolved.

This configuration readback establishes what Windows reports. It does not certify full media health, the ability to survive an actual failure, hardware independence, speed or universal application compatibility. Two members sharing a power supply, controller or enclosure can share failure causes. Do not unplug a disk, disable a controller, force a shutdown or deliberately degrade the new pool to strengthen the claim.

Within the approved check scope, create a uniquely named folder on the new volume with small synthetic ordinary files. Keep their exact expected text or digests outside the pool. Confirm the target path reaches the new volume rather than a fallback local folder. Save, close and reopen the files, comparing their contents to the independent baseline. If the task includes a particular application, use an authorized non-sensitive sample and its supported save/reopen path; do not run executable content merely as a storage check.

Record configuration evidence and file evidence separately. Leave check files unless cleanup was authorized. Do not migrate a photo library, redirect Documents, enable sharing or start a backup job as a verification shortcut.

If persistence across restart was requested, coordinate a normal restart only after the user has saved unrelated work and authorized the interruption. Reidentify the pool/volume and reread the same sample afterward. Otherwise report restart behavior untested. Never eject an individual member to apply a single-external-drive remount checklist to this multi-disk volume.

## Recover from incomplete setup without erasing evidence

| Observed boundary | Next safe action |
| --- | --- |
| A disk is absent or ineligible before creation | Preserve existing layout; clarify hardware identity/eligibility. Do not clean it or change enclosure modes to force selection |
| A pool exists but no space was created | Inspect exact membership and remaining capacity; resume only the approved supported next step if prerequisites still hold |
| A space exists but volume creation failed | Record the space and error; do not recreate the pool or format its physical members. Resolve the exact volume step and any fresh destructive confirmation |
| Completion is uncertain | Inspect active work and current objects before another submission. Avoid overlapping creation, forced removal or power cycling |
| A member is missing, unhealthy or shows I/O errors | Hold new data writes and preserve evidence. Existing-pool recovery/replacement requires a separate scope; do not remove/reset the member or run repair automatically |
| Capacity differs materially from the plan | Separate units/overhead from a real mismatch; hold real data placement. Do not switch resiliency, over-provision or buy storage silently |
| Wrong disk or unexpected existing contents discovered | Stop further changes through a supported safe control, explain known effects and preserve state for a recovery decision. Recreating old partitions is not an undo |

Deleting a space or pool can destroy the new data and does not restore the former disk contents. Do not label teardown “rollback” or use it as automatic cleanup. Any requested teardown needs current inventory, preservation and action-time confirmation. Retain any new work created since setup; it is not disposable because the volume was originally a test target.

## Handoff and acceptance

Return a compact private record with physical members, pool/space/volume associations, accepted versus observed configuration, capacity figures and units, preservation status, operation outcomes, sample-file results and unresolved limits. State the native route for inspecting pool capacity and health. Explain that member disks must remain connected during use and are not independently removable copies of the files.

Do not promise unattended monitoring, automatic repair, unlimited growth or an established backup. If the user needs a notification, independent backup or future expansion, identify that separate decision without configuring it incidentally.

Acceptance requires the correct member set, intended two-way layout and volume, no unresolved reported setup fault, bounded successful save/readback, and any expressly requested restart evidence. Use honest intermediate labels: plan only, pool created without a usable volume, volume created but unverified, or verified for the stated ordinary-file check. Stop at acceptance or the precise preservation, hardware, access or capacity blocker.

## Fictional, unexecuted illustration

A fictional user wants one mirrored project volume on a Windows desktop using two equal-sized spare disks. The intended devices have distinct observed identities in the imagined inventory. One holds an old folder that the user still wants; another connected disk is an active backup destination. The requested usable size is larger than one spare disk's capacity.

Following this guide would hold creation for two reasons: the old folder lacks an agreed separately retained copy, and the requested capacity cannot be backed by those two members with two copies. The backup disk would remain excluded even if the wizard offered it. After separately resolving preservation and approving a smaller supported size, the workflow would still require exact-disk destructive confirmation, native creation, membership/resiliency readback and a small save/reopen check. A “Healthy” indicator alone would not replace the content check, and the agent would not unplug a member to demonstrate resilience.

This is a fictional, unexecuted decision walkthrough. No disks were inspected or erased, no pool or volume was created, no files were copied, no restart occurred and no reliability or failure-recovery result was observed.
