---
name: create-bootable-installation-media
description: "Create a dedicated USB operating-system installer through the vendor's supported media-creation route, bind the destructive write to the intended device, and verify media completion and any authorized target startup. Use for installation-media preparation, not installing an OS, creating a running external system, restoring a backup or bypassing startup security."
---

# Prepare an installer that the intended computer can start

Deliver one identified removable USB installer and a short, version-bound use record. Carry the intended operating system and target hardware through source selection, media creation and a bounded startup check. A downloaded installer, a mounted USB volume, a creation-success message and a target that reaches the installer are separate results.

This workflow covers ordinary vendor-supported installation media on a dedicated removable drive. It does not install, upgrade, reset or repair the target OS; make a multiboot drive; clone a system; prepare an unattended deployment; inject drivers; modify firmware; or create a fully installed external operating system. It does not handle a drive containing partitions that must remain in use. A request for emergency recovery may need a different deliverable before any storage is erased.

Use [external data-drive preparation](../format-external-data-drive/SKILL.md) for ordinary storage, [backup coverage planning](../plan-file-backup-coverage/SKILL.md) when retention is unsettled, and [backup restore checking](../backup-restore-spot-check/SKILL.md) when the result must be recovered personal files. A bootable installer is not a backup of the target computer.

## Resolve the media contract

Establish the few facts that affect the result:

- Whether the user wants a plan, actual USB creation, or creation plus a startup check
- The exact OS family, required release/channel, architecture, language and edition constraints; whether the vendor's current release is acceptable or a specific version is required
- The maker computer and its current OS, separately from each intended target's model, architecture and supported OS requirements
- The dedicated USB device, physical identifying evidence, current contents and retention decision
- Approved download/work location, available space, connection and time budget, and existing supported creation tools
- Whether the target is available, authorized for a restart and under local observation; the agreed maintenance window and how the user will return to the existing system
- Any known management restrictions, startup-security restrictions, encryption/recovery prerequisites and the owner who can handle them
- The evidence and handoff destination, including which targets actually need to be checked

Do not infer the target architecture from the maker computer. A USB made on one machine can be intended for another. Do not choose an older release merely because a cached installer is available, or substitute a newer release for an exact-version request. If the official route cannot supply the requested combination, prepare the supported choices and hold creation.

Keep the artifact type explicit. Microsoft's [Recovery Drive](https://support.microsoft.com/en-us/windows/experience/backup-recovery/recovery-drive) captures system recovery material for the device it was created for and excludes personal files. That is different from vendor installation media. Apple's [external startup-disk workflow](https://support.apple.com/en-lk/111336) installs a working OS on an external drive, another distinct result. Resolve an ambiguous “recovery USB” request before selecting a tool.

## 1. Establish a supported source and creation route

Start from the OS vendor's official download/support page, then the target manufacturer's model-specific guidance where needed. Record the selected release, architecture, language, tool identity and source URL. Use the actual current prerequisites rather than a remembered capacity requirement or an old tutorial. Availability and support status are part of the selection; successful downloading does not make an unsupported target supported.

For a supplied installer, establish its provenance and whether the official tool accepts that form. A filename, familiar icon or locally computed hash identifies less than an authenticated source. If the vendor publishes a checksum for the exact image, compare against that exact release/architecture/language entry and retain its source. Do not compare an installer application, a USB's transformed contents or an older image with the hash of a different ISO. Keep source provenance, byte checks and hardware compatibility separate.

Choose one supported route and keep its boundaries:

- **Windows installation USB:** Microsoft's [installation-media overview](https://support.microsoft.com/en-us/windows/deployment/install-upgrade/create-installation-media-for-windows) directs users to its download site and media-creation utility. The [Windows 11 download page](https://www.microsoft.com/en-us/software-download/windows11) currently distinguishes the media-creation route from Installation Assistant and ISO download. Its media-creation tool produces x64 media, not Arm media. Check this limitation against the target before downloading or running it; an Arm image's availability does not establish a supported USB-making route on the maker computer
- **macOS installation USB:** Apple's [bootable-installer procedure](https://support.apple.com/en-us/101578) uses a full installer application and its bundled createinstallmedia utility. Download through Apple's [supported installer routes](https://support.apple.com/en-gb/102662). A disk-image/package download may need the documented preparation that yields the installer application; copying the download file to USB is not the creation step
- **Other OS or OEM-specific request:** use that vendor's exact documented image, target requirements and creation utility. If the available evidence only covers a generic image download, leave the write procedure unresolved rather than inventing disk-writing commands or treating this guide as a universal image flasher

Downloading, executing a creation utility and accepting its agreement are different actions. Obtain any required execution permission and disclose a new explicit license acceptance before accepting it. Use the vendor's reviewed flow; do not acquire an alternate flashing utility simply because the first route is unavailable. Do not bypass a browser security warning, an OS trust failure or a managed-device restriction. Keep authentication and administrator credentials in a supported user-controlled entry flow, never in chat, scripts or the result record.

If an automatic installer opens after download, stop at its initial screen and quit through the supported control; do not advance an OS-installation flow. Keep the full downloaded source until the media and handoff have their agreed result. Cleanup is separate from creation.

## 2. Bind the target to a physical removable device

Inspect the available disk hierarchy before writing. Match the user-selected drive to its external connection, model, capacity, available hardware identifier and contained volumes. A drive letter or mount path is a current locator; it can change. A volume label is not unique, and an adapter's identity may not uniquely identify the inserted media.

Resolve ambiguity through a user-confirmed physical identity or a safe connect/disconnect comparison when there are no active writers. Do not unplug a busy drive or identify the target only by “Disk 2,” “the empty drive” or “the smallest disk.” Exclude the maker's startup disk, the intended computer's internal disks, backup repositories and storage belonging to an array. A drive not visible in the file browser can still contain valuable partitions.

Inspect all contents affected by the proposed operation. “Unformatted,” “RAW” and a tool's erase prompt do not mean empty. If files were expected but cannot be read, stop preparation and preserve the device for a recovery decision. If any partition must remain, this dedicated-media workflow is not the right route; do not expand the request to erase it.

Record one supported retention state: the user confirms nothing needs keeping, required copies have been retained elsewhere to the agreed evidence standard, or retention remains unresolved. A copy on another partition of the same device cannot be relied on for a device-wide rewrite. Do not copy private files to a new service or shared destination to clear this gate without the necessary data/destination authorization.

Keep the source download, device record and retained-copy evidence outside the USB. Do not preformat automatically. Media-creation tools can perform their own preparation, and an extra manual format adds another destructive action without proving bootability. The exact utility determines which volume or whole-device structures it changes; do not promise preservation based on a generic tool category.

## 3. Confirm the exact destructive write

Immediately before the irreversible creation step, show the distinguishing USB identity, current locator and affected contents, selected OS/media route, preservation decision and expected loss of ordinary file recovery. Obtain the required per-action confirmation. “Make an installer” or a prior planning approval is not sufficient confirmation of an unidentified erase.

Recheck the selected device after approval and before submission. A reconnect, utility restart, new disk or changed layout can invalidate the selection. If the tool's warning describes a broader target than approved, hold it. Do not accept a warning simply because it is customary for that utility.

The confirmation applies to this media operation, not to the computer's internal drive or a subsequent OS installation. A vendor wizard can place creation, installation and recovery choices close together; compare the actual action text with the approved result. Do not suppress erase prompts, feed unattended confirmation input or substitute a blanket disk-clean command.

If administrative authentication is needed, pause for the supported secure user handoff. Explain any removable-storage permission prompt by application and scope before granting an unanticipated permission. Do not grant broad disk access, change protection settings or force-unmount unrelated work to make the write proceed.

## 4. Create the media and retain its actual completion state

Follow only the selected vendor's current procedure. Use a stable direct connection where the vendor requires it and avoid moving the drive while it is in use. Read the real selected destination, not a remembered screenshot.

### Windows media-creation route

Within the official tool, select creation for the intended target rather than upgrading the maker PC. Reconcile language/edition/architecture with the contract; defaults based on the maker may be wrong for another computer. Select USB output, then the reidentified target. An ISO-only result is a different deliverable and remains a downloaded-image result until a supported media-creation step is completed. Microsoft's [download instructions](https://www.microsoft.com/en-us/software-download/windows11) describe the administrative requirement, license step and USB/ISO choices; apply the separate authorization and erasure gates above.

### macOS createinstallmedia route

Confirm the full installer application's name/location and select Apple's matching version-specific command. Resolve its volume argument to the approved physical USB before execution; do not paste a generic example with an unresolved placeholder. If renaming the volume is needed, confirm the intended change and reidentify it afterward. The [official procedure](https://support.apple.com/en-us/101578) requires administrator authentication, confirms erasure, reports media availability and can change the resulting volume name. Do not add prompt-suppressing options or treat the new label as a different physical device.

### Observe once, then inspect

Retain the selected source/tool identity and its completion or error result. Keep download, erase, copying and finalization states separate when the tool exposes them. A progress value at 100% can precede finalization; wait for the tool's actual terminal result.

If the control connection times out, first determine whether the creation utility is still active. Do not launch another writer, eject the drive or repeat a destructive command because the remote response is missing. Resume observing the existing operation when possible. If its state cannot be established, report the uncertain write and require local inspection before another action.

Record the resulting device and visible media identity through a supported read-only view. Tool-generated partitions or a renamed volume can be expected; reconcile them with the route instead of “repairing” an unfamiliar boot layout. Do not change files, run the OS installer from the mounted media, or add check files merely to prove that ordinary writes work.

Safe-eject after the creator has finished, reconnect when permitted, and confirm the same physical media can be enumerated. Retain a native verification result if the tool provides one, identifying what it checked. Visible files and remount success do not prove target startup. Conversely, media need not present every boot partition as an ordinary file-browser volume.

## 5. Check target startup only when authorized and observable

A startup check executes the selected vendor environment and interrupts the target's running session. Establish the restart window, saved-work state, physical support and a return path before beginning. If remote access disappears during boot and no authorized local observer can report the state, mark startup untested. Do not promise a remote-control connection will survive firmware menus or the installer environment.

Confirm the user can independently handle any required encryption/recovery authentication before restarting. Microsoft's [BitLocker recovery guidance](https://support.microsoft.com/en-us/windows/security/encryption/find-your-bitlocker-recovery-key) notes that startup security or hardware changes can trigger recovery. Record only that the owner has an available recovery route, never the key or password. Do not disable encryption, suspend protection, reset the TPM or retrieve secrets into the working record as preparation for this check.

Use the target manufacturer's documented one-time startup selector when available. A temporary selection avoids an unnecessary persistent boot-order change. Verify which entry belongs to the new USB; do not select a same-named internal recovery partition and call that a media test. If the route would require a persistent startup/security change, stop at the boundary and obtain a separate decision rather than treating it as incidental setup.

On Macs, the supported startup route depends on Apple silicon versus Intel hardware. Apple's [installer procedure](https://support.apple.com/en-us/101578) describes both and warns that model-specific information can still require internet access; this USB is not an offline-installation guarantee. Apple's [T2 security reference](https://support.apple.com/en-ca/102522) also distinguishes external-media permission from Secure Boot. A denied boot is not permission to lower either setting. Leave restrictions intact and report the precise documented requirement.

Define the endpoint before selecting the USB: observe the first identifiable installer or installation-utilities interface, then exit through its supported quit/restart/shutdown control. Record target identity, selected boot entry, visible environment and observation time. Stop before starting Install, Reset, Recover, partition editing, disk erasure, internal-volume repair or setup customization. A language-selection screen may be sufficient evidence that the selected media launched; keep any unseen OS version or target support unverified.

Do not infer that the internal disk was unchanged at the byte level merely because no install action was selected. State the narrower observed boundary: the installer environment started and no installation/recovery operation was intentionally initiated. Do not browse personal files or unlock internal volumes to strengthen a startup check.

Return to the existing system through the agreed route, disconnecting the media only after supported shutdown/ejection. Verify the original system starts when that check is available. If the target was already nonfunctional, its failure to start without the USB is not a new media defect; preserve that baseline and report only the observed installer launch. Boot success establishes neither installation completion, license activation, full driver support nor personal-file recoverability.

## Recover or stop without compounding an uncertain write

- **Download/source incomplete:** keep the candidate distinct; reobtain the exact supported source within the approved download budget. A different release needs a new selection, not a renamed file
- **Source authenticity or compatibility unresolved:** hold execution and creation. Do not remove verification, patch the image or bypass hardware checks
- **Media tool fails before writing:** record the error and confirm the unchanged target state where observable. Resolve the supported prerequisite before a bounded retry
- **Write interrupted or completion uncertain:** inspect the original utility and target first. Mark the medium incomplete until supported recreation or verification succeeds; never call its previous contents preserved
- **Recreation requires erasure:** reidentify the current device/layout and obtain fresh action-time destructive confirmation. Do not assume an earlier confirmation covers an indefinite rewrite loop
- **Insufficient capacity or repeated I/O error:** stop with the tool's evidence. A different drive requires its own identity, retention and destructive-action gates; do not shrink or delete unrelated partitions
- **USB absent from startup options:** distinguish creation evidence, port/connection evidence, target compatibility and boot-policy restrictions. Do not repeatedly reformat, flash firmware, enable legacy mode or disable Secure Boot as trial-and-error fixes
- **Credential, firmware-lock or management prompt:** pause for the authorized owner/support route. Never bypass it or solicit credentials in the report
- **Wrong device or unintended operation discovered:** stop further actions through the supported safe control when possible, preserve the actual state and immediately report what is known. Do not improvise a partition repair or run recovery/install tools as an undo

Before retrying, identify a specific corrected prerequisite and a finite attempt/time budget appropriate to the task. Stop on repeated failure without new evidence, unresolved device identity, exhausted budget or a new permission boundary. Retain a partially completed medium as incomplete; erasing it for reuse is a separate action. There is no reliable undo for overwritten USB contents.

## Deliver the media and its limits

Return a compact record containing:

- Media device identifier/label, creation date and intended OS release/channel, language, architecture and edition constraints
- Official source and creation tool, source-integrity evidence when available, exact completed operation and any errors or retries
- Preservation decision, affected storage scope and actual completion/readback results
- Per-target compatibility basis and observed startup result, including unavailable targets and baseline problems
- The supported one-time boot reference, the defined stop-before-installation point and any owner-controlled prerequisite
- Current disposition of the drive, source download and evidence; unresolved next decision

Use minimal hardware identifiers in a wider-facing sheet. Keep private paths, full serials, account identities and credential-related information out of labels and shared instructions. Do not upload the installer, distribute licensed media, ship the USB or share the record with a third party unless that separate action is authorized.

Report `plan prepared`, `source obtained`, `media creation completed; startup untested`, `installer startup observed on [target]`, or the specific blocked state. Acceptance requires the correct supported source and physical target, resolved preservation/erasure scope, terminal creation success and the requested readback/startup evidence. A documentation-backed compatibility statement must not replace an unavailable requested target check. Stop at this result; OS installation remains a separate task with a new internal-disk preservation and authorization boundary.

## Fictional, unexecuted illustration

A fictional user requests a Windows installation USB for a named x64 laptop using a spare dedicated drive. The maker computer offers its own language as the default, but the intended target requires another language. Two connected USB devices have the same display name; one contains retained project files.

The workflow would resolve physical identity first, leave the retained-data device alone and bind the chosen language to the intended target. Creation would wait for exact-device erasure confirmation. If the paper scenario then reports native creation success and a reconnect, but no target restart is available, the handoff would say that media creation completed and target startup is untested. Merely listing installer files would not close that gap.

If an otherwise similar request names an Arm target, the x64-only media-creation route would be held before writing; a same-sized USB does not solve the architecture mismatch. If a later authorized startup attempt reaches a security restriction, that result would be reported without relaxing the restriction or proceeding to OS installation.

This illustration is original, fictional and unexecuted. No installer, download, account, disk, application, media-creation command, restart, firmware setting or operating-system installation was accessed or performed for it.
