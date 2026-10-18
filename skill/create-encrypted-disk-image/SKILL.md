---
name: create-encrypted-disk-image
description: "Create a new password-protected working disk image on macOS, bind its backing file to the mounted volume, and verify bounded file storage through eject and user-controlled reopening. Use for a local encrypted container, not whole-drive encryption, secure erasure, password recovery, cloud sharing or opening received images."
---

# Create an encrypted working container

Deliver a new encrypted disk image that the user can reopen and use for the stated ordinary-file task, with a small private record of its location, contents, opening behavior and verification limits. Keep the image file, the mounted volume and any original plaintext files distinct throughout the work. A password dialog alone does not establish that the intended files are inside the intended image.

This workflow uses the Mac's existing Disk Utility and a new local destination. It does not encrypt an existing physical device, enable FileVault, convert an existing image, create a password vault, recover a password or inspect an image received from someone else. Keep live databases, application libraries, executables and authentication material outside this ordinary-file setup. A requirement for Windows access, automatic unlocking, synchronized multi-device editing or a managed security policy needs a separately established supported route.

[Drive preparation](../format-external-data-drive/SKILL.md) changes a physical data volume. [Privacy-checked document copies](../privacy-checked-document-copy/SKILL.md) remove information from a recipient's document. This workflow does neither. Use [backup coverage planning](../plan-file-backup-coverage/SKILL.md) when the user needs protection against file loss; an encrypted container on the same disk is not an independent backup.

## Establish the working boundary

Resolve the inputs that change the result:

- The actual Mac, account, macOS version and installed Disk Utility; any other Mac that must open the result
- Whether the request is a plan, an empty reusable container or a container populated with an exact selected file set
- A new backing-file location, a distinct mounted-volume name, a capacity budget and expected growth
- Existing source identities, required bytes or metadata, exclusions and the intended permitted reader applications
- The desired password-storage/opening behavior and the user's availability for secret entry and reopening
- Allowed harmless write/read checks, required target-Mac evidence and the final mounted or ejected state

Default to leaving the completed container ejected when it is not needed for an ongoing user task. Do not reinterpret a request for password-gated opening as permission to remember the password automatically. If only a plan is possible, supply the exact unresolved decisions without inventing a created image or live check.

Use an already authorized private local folder outside cloud-sync, shared and watched locations. Inspect the actual location rather than assuming Desktop or Documents is local-only. If its transmission or access scope is unclear, hold file creation there and resolve the destination. Do not disable sync or alter folder permissions as an incidental solution. A neutral image filename avoids putting sensitive descriptions in an ordinary directory listing; encryption does not make the backing filename private.

## 1. Separate protection, retention and permissions

Explain the actual boundary before setup. Apple's [encrypted-image overview](https://support.apple.com/guide/security/digital-signing-and-encryption-secd0da50a09/web) describes AES-encrypted images that become ordinary usable volumes when mounted. For this workflow, protection at rest must not be presented as protection from an application or person already able to use the unlocked session. The same workflow also does not establish that previews, clipboard data, application caches, backups or earlier plaintext copies are absent.

Creation is copy-preserving: retain selected originals unchanged, including their existing access and backup state. Do not move them into the image, replace them with aliases, trash them, empty Trash or promise secure erasure. If the user's desired outcome requires removing all plaintext copies, explain that this guide can create the container but cannot establish that broader result. Never turn source deletion into a mandatory final step merely because a vendor tutorial mentions it.

Before committing the new protection, identify the exact new image and obtain the applicable action-time approval for the security configuration. Hand control to the user before password creation or entry; the user chooses, enters, confirms and submits the secret through the supported secure interface. Keep passwords and recovery material out of chat, commands, logs, screenshots, file manifests and examples. Do not read a password manager or keychain to complete the check.

Apple's [creation guidance](https://support.apple.com/guide/disk-utility/create-a-disk-image-dskutl11888/mac) warns that forgetting the image password prevents opening its files. Ask the user to retain it privately by their chosen approved method; never record it alongside the image. Saving credentials, configuring automatic access, changing existing credential storage or granting a new application permission requires its own applicable authority. Stop if the secure interaction is unavailable. Continue only the non-secret preparation.

## 2. Plan the container and copied contents

Keep these identities in a compact private record:

| Object | What must be established |
| --- | --- |
| Host storage | Actual local backing location, available space and existing access/sync boundary |
| Image | New exact file path, observed image format, encryption selection and requested logical capacity |
| Mounted volume | Name, filesystem and current mount identity correlated to that image |
| Selected payload | Source-to-destination relative paths, stable source version and verification scope |

Do not treat the filesystem, image format and encryption control as synonyms. [Apple's filesystem reference](https://support.apple.com/guide/disk-utility/file-system-formats-dsku19ed921c/mac) distinguishes APFS from its case-sensitive variant. For ordinary compatible Mac-only work, avoid introducing case sensitivity without a requirement. The filesystem inside an image does not by itself establish that another operating system can unlock and mount the surrounding encrypted format.

Use a writable image type documented for the installed OS and all required target Macs. Do not silently substitute a sparse format, compressed read-only image or newer format because its label sounds more efficient. If sparse storage is actually needed, verify its documented compatibility and whether the backing artifact is one file or a bundle before accepting that different choice. Keep logical volume capacity, current host allocation and remaining host free space separate. A logical capacity setting is not a promise that the host can supply all future writes.

For a populated container, inventory only the selected ordinary resident files. Preserve relative paths and useful subfolders. Resolve same-name/case collisions before copying; keep outside links, cloud placeholders and unreadable inputs held rather than following or downloading them automatically. Use a stable source observation and appropriate size/content baselines for the agreed check scope. If metadata matters, add [metadata-transfer review](../audit-file-metadata-transfer/SKILL.md); matching payload bytes alone cannot prove that property.

Reserve host space for the new image and retained originals, plus filesystem overhead and agreed working headroom. Do not guess a universal overhead percentage or fill a volume to discover its limit. If the chosen image type's allocation behavior is uncertain, hold sizing or choose an already supported alternative with the user. Keep the backing image outside the selected source tree and never copy it into its own mounted volume.

## 3. Create one new image through the native route

Consult the version-matched [Disk Utility instructions](https://support.apple.com/guide/disk-utility/create-a-disk-image-dskutl11888/mac). The native route starts at File > New Image > Blank Image. Set the new backing filename/location, mounted name, capacity, compatible filesystem, encryption and writable image format. The password step belongs to the user. Review the non-secret settings again after handback, then finish only the approved creation. Disk Utility normally creates and mounts the image.

These are route landmarks, not a fixed script. If the actual controls differ from the documentation, resolve the installed-version behavior before proceeding. Do not select a physical disk's Erase or Restore action to obtain the desired container. Decline replacement of an existing file; use a genuinely new approved destination. Do not grant broad disk access, install tools or bypass management restrictions to continue.

Submit once. After a timeout or disconnected control session, inspect the native operation and exact destination before considering a retry. A response failure does not mean no file was created. Do not overwrite an existing candidate or create a second same-named mounted image to clear uncertainty.

Read back the backing-file identity, available non-secret format/encryption evidence and its actual mounted volume. Use supported image information and the observed create/open relationship, not a matching display name alone. If encryption cannot be established, keep it a candidate and do not copy the user's files into it. An unexplained automatic opening is a separate opening-behavior question, not proof that encryption is absent.

## 4. Establish write and payload evidence

Use a tiny, non-sensitive, uniquely named marker inside the verified mounted volume. Save, close and reread its expected content from that volume rather than from a Recent Items entry. For a reusable working container, update this marker once and reread the changed content; do not edit a real source document to manufacture write evidence. The marker belongs in the membership record and stays unless its cleanup was approved.

If population was requested, copy only the reviewed selection after the initial write/read succeeds. Preserve originals and do not flatten subfolders. Wait for copying to settle, reconcile every required source identity to its target and distinguish completed, held and partial files. Check the agreed bytes against their stable source baseline. A changing source is a version mismatch to resolve, not a reason to overwrite the source or silently accept whichever content arrived.

Keep application usability separate from byte agreement. Where a selected file must open in an application, use the existing approved safe consumer with macros, scripts and external refresh inactive. Record any app behavior that saves elsewhere or creates sidecars. Do not run bundled content, change the default save location globally, add the volume to sync or upload a diagnostic sample to prove readability. If the requested application cannot be checked without additional effects, report that exact limit.

## 5. Eject, reopen and verify the same saved result

Finish writers and close the selected documents through normal save/close controls. Eject the exact mounted image and confirm it is no longer mounted; a closed Finder window is insufficient. Apple's [busy-disk guidance](https://support.apple.com/en-au/guide/mac-help/mh27076/mac) identifies open applications or documents as reasons ejection can fail. Preserve unsaved work, close only the relevant authorized consumer and try normal ejection again. Do not force-unmount, kill unrelated processes or restart the Mac just to complete this check.

Reopen the exact backing file. For a manual-password requirement, observe its unlock prompt and cancel once without entering a password; confirm that this attempt did not mount the volume. Then reopen and let the user enter and submit the secret. Do not deliberately guess a wrong password. If it opens without that interaction, report the observed behavior and hold the manual-gate claim; do not delete keychain entries or change credential settings to manufacture a pass.

Rebind the newly mounted volume to the same backing file; paths can change when names conflict. Read the updated marker and the agreed payload from this reopened volume, then compare the expected content again. This distinguishes a usable retained result from a cached preview or an earlier mount. Any required second-Mac check must use that actual authorized Mac and an approved transfer route. If unavailable, state that target compatibility is documented or untested, never observed.

Eject again if that is the agreed final state. Keep the result open if the user explicitly needs to continue working, and plainly report that its files remain available in the mounted session. Do not claim it is locked while the volume is still mounted. Any optional image digest must be taken only after a successful eject and identified as a point-in-time byte fingerprint; later legitimate writes can change it, and it is not proof of encryption strength.

## Recovery and stopping conditions

- **Creation incomplete or uncertain:** retain the candidate's identity and actual state; inspect before retrying. Do not erase it or overwrite a same-named file. Any new attempt needs a distinct destination and still-valid authority
- **Capacity or copy failure:** preserve source and partial target; account for what copied and hold completeness. Do not resize, compact, convert or delete other storage as an incidental retry
- **Password unavailable or reopening fails:** retain the backing image and plaintext originals. Let the user resolve their own secret through an appropriate secure route; do not brute-force, reset or promise recovery
- **Image mounted but cannot eject:** report the open boundary immediately and preserve the work. Resolve the identified consumer or ask for the needed user action; do not call the container closed
- **Wrong image, path or unexpected sharing discovered:** stop further copying, identify what may already exist and request the specific containment decision. Unmounting does not remove copied data or reverse exposure
- **Readback mismatch or application incompatibility:** keep the failure evidence, leave originals untouched and return the precise failed boundary. Do not replace a failed verification with a narrower claim without naming the limitation

If the user abandons setup, leave the candidate and originals identifiable. Removing a created image is a separate deletion decision, especially if it acquired later user edits. Reversal of setup is not proof that caches, copies or prior exposure disappeared.

## Deliver the usable handoff

Return the image location and mapped volume name, actual format/encryption evidence, selected-copy accounting, marker location, observed password/eject/reopen behavior and final mount state. Include concise opening, saving and closing directions that match the observed setup, plus any untested Mac/application and the remaining originals. Keep private source paths and file details out of a wider-facing summary.

Accept a working setup only when the intended image is encrypted by the checked native configuration, the requested content survives reopening, requested writing works, the opening behavior meets the user's requirement and the agreed final state is observed. Separate an empty verified container, a partially populated candidate and a complete checked selection. None is a security certification, secure-erasure result or verified backup.

The [fictional illustration](example.md) shows how an automatic reopen and an unresolved ejection change the conclusion. It is unexecuted and supplies no device or application result.
