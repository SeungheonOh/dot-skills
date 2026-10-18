---
name: configure-startup-disk-protection
description: "Enable FileVault for an existing personal Mac startup installation, preserve working data and unlock access, and verify the actual protection state with owner-controlled recovery custody. Use for native startup-storage protection, not encrypted containers, external-drive formatting, managed deployment, credential recovery or security certification."
---

# Protect an existing Mac startup installation

Deliver FileVault protection for the identified existing startup installation, with a secret-free receipt separating setup, active protection, recovery readiness and ordinary startup/use evidence. If a prerequisite or protected user step prevents completion, deliver that exact prepared, pending or blocked state. Do not replace the requested result with a generic security checklist.

Use this guide for one personally controlled Mac with a supported macOS installation and the native FileVault interface already available. It does not provision a new computer, encrypt external or alternate startup devices, redesign partitions, handle organizational key escrow, rotate existing recovery credentials or recover an inaccessible account. Windows and fleet deployment require their own established procedures; do not translate these controls into another platform's commands.

[Encrypted disk images](../create-encrypted-disk-image/SKILL.md) protect a selected file container. [External-drive preparation](../format-external-data-drive/SKILL.md) changes a data drive's layout. [Standard-user creation](../create-standard-desktop-user/SKILL.md) creates another local identity. Here the result is protection of an existing startup installation while retaining its data and users; none of those other outcomes establishes it.

## Establish the intended result

Resolve material inputs from the request and authorized native observations:

- Exact Mac, installed macOS version, hardware family and currently running internal startup installation
- Personal control versus management, the available authorized administrator and existing users who need independent startup unlock
- Whether the user wants preparation, actual activation, or activation plus a normal startup/use check
- Current FileVault state and any operation, deferred setup or restart already pending
- Important working data, current backup evidence, unsaved work and other signed-in sessions to preserve
- Owner-selected recovery route and custody requirements, including whether any cloud storage or synchronization is acceptable
- Owner availability for protected steps, local access before login, an acceptable interruption window and the supported way to reconnect afterward
- One ordinary app/file check if requested, the final session state, and a private destination only if a saved receipt is wanted

Ask only for missing choices that change safety or acceptance. Do not ask the owner to reveal a password, recovery key or account recovery answer. If the target is not available through an authorized computer interface, finish the plan; information from a different machine cannot establish this one's state. A remote desktop connection after login is not a usable preboot-control path. Arrange owner participation before proceeding if the available connection cannot reach that boundary; do not install remote access to solve it.

## 1. Identify the startup target and baseline

Use read-only native system and storage views to correlate the running installation, its internal device and the relevant startup volume or APFS volume group. A volume's familiar display name alone is insufficient where several installations or similarly named disks exist. Record only enough non-secret identity to reidentify the same target after a restart; avoid copying full serials and unrelated storage inventories.

Do not interpret every APFS volume as a separate user-selected encryption job. Apple's [FileVault architecture reference](https://support.apple.com/guide/security/volume-encryption-with-filevault-sec4c6dc1b6e/web) distinguishes the signed system volume from the encrypted data volume on newer macOS releases. Use the startup installation's supported FileVault setting rather than trying to encrypt each auxiliary volume manually.

Open its native FileVault status without pressing an action control. Record the displayed state, pending requirement or error and observation time. Keep these questions separate:

| Question | Evidence needed |
| --- | --- |
| Is storage encrypted by the hardware/platform? | Model-specific supported behavior; insufficient alone for FileVault acceptance |
| Is FileVault protection active? | Current native FileVault state on this installation |
| Is a conversion or setup step unfinished? | Actual progress, deferred step, error or required restart shown by the supported route |
| Can the owner retain access? | Established unlock identities and owner-confirmed independent recovery readiness |
| Has normal startup/use been checked? | An actual bounded event, or an explicit unrun/user-reported label |

On Apple silicon and T2 Macs, hardware encryption can exist with FileVault off; later activation can be immediate because the data is already encrypted. Other supported Macs can require conversion. These distinctions are documented in the [architecture reference](https://support.apple.com/guide/security/volume-encryption-with-filevault-sec4c6dc1b6e/web). Never substitute an encrypted filesystem label, a password-protected login or elapsed time for the actual protection state. Do not require an invented progress percentage on a route that does not expose one.

If FileVault is already on, preserve it and verify the requested existing state. Do not toggle it off and on to recreate setup or generate a new key. If setup/conversion is already underway, establish its origin and current stage before proposing any continuation. If the disk is decrypting, the target is unclear, management controls the setting or a storage fault is evident, stop changes and report the specific prerequisite. Do not bypass policy, repair the disk or weaken startup security.

## 2. Preserve work and settle recovery custody before activation

Keep all files, accounts, existing unlock capabilities, backups and storage layout intact. Save relevant unsaved work normally and identify other sessions or active jobs before an interruption. Do not force-quit users or start a restart while their preservation state is unresolved.

Read existing backup coverage/completion evidence and its date; identify any important changes since it was made. A backup setting is not a demonstrated usable copy. Use [backup planning](../plan-file-backup-coverage/SKILL.md) or an independently authorized [restore spot check](../backup-restore-spot-check/SKILL.md) if the retention requirement needs it. Do not upload private files, change backup destinations or delete old versions to clear this prerequisite. Hold activation where preservation is unresolved against the user's requirement. FileVault is not a backup or a guarantee of recovery from failed storage.

Choose the offered recovery route deliberately. Apple's [FileVault setup instructions](https://support.apple.com/guide/mac-help/protect-data-on-your-mac-with-filevault-mh11785/mac) describe an account-based route and a recovery-key route. A locally retained key must remain available somewhere other than the protected startup disk and apart from the Mac. Loss of the necessary login and recovery access can make the data unavailable. Explain that consequence before proceeding.

For a key route, the owner must privately capture and check the actual key, retain it in their selected safe location, and confirm they can retrieve it without this Mac working. Record only the custody class and their confirmation, such as “owner confirms separate offline custody”; never record the key, fragments, a hash of it or a precise hiding place. For an offered account route, have the owner privately confirm control of the intended existing account and access from an independent device. A currently signed-in Mac is not sufficient evidence. Do not create an account, reset credentials or add recovery contacts under this task.

Check installed-version behavior before promising local-only custody. Apple's current [recovery architecture section](https://support.apple.com/guide/security/volume-encryption-with-filevault-sec4c6dc1b6e/web) describes key retrieval/storage and synchronization behavior associated with iCloud Keychain. A choice labeled recovery key does not justify a blanket “never stored in the cloud” claim. Resolve actual automatic storage/sync destinations with the owner before activation. If the required custody boundary cannot be established, hold; do not change sync/security settings or copy a key into a different service as an incidental fix.

Recovery readiness here is the owner's private confirmation, not an observed recovery exercise. Do not reveal or enter a key to strengthen the report, deliberately forget/reset a password, trigger recovery, boot external media or run a guessed-password test. A future actual recovery incident needs its own supported owner-controlled procedure.

## 3. Confirm the security change and protect secret steps

Obtain per-action confirmation immediately before enabling FileVault on the exact Mac and startup installation. Include the selected recovery route and understood storage destinations, intended startup-unlock identities, preservation status, expected interruption and the loss-of-access consequence. Also disclose the native login/wake consequences for the installed version: Apple's [behavior guide](https://support.apple.com/guide/mac-help/how-does-filevault-work-on-a-mac-flvlt001/mac) describes requiring a password after sleep or the screen saver when FileVault is enabled. If that conflicts with the user's access or accessibility needs, resolve the decision before activation rather than weakening the resulting protection. Creating a recovery credential and establishing its access path are security-sensitive actions; an earlier general request to secure a laptop does not replace action-time confirmation. If these are one inseparable native activation, the confirmation must explicitly cover that combined effect. A materially different route, destination or access scope needs a fresh decision.

Hand control to the owner before any credential entry, key display/capture or secret-bearing submission. The owner performs authentication, recovery-material generation/capture and any credential-bearing confirmation through a supported private interface. Do not collect secrets in chat, clipboard, shell arguments, logs, screenshots, screen recordings, artifacts or an assistant credential store. Do not inspect Passwords or Keychain to prove custody. Stop automated screen capture before the flow can reveal a key and resume only after the owner has dismissed the secret-bearing view. If the tool cannot keep the secret interaction private, stop at preparation.

Any transmission of a highly sensitive password or recovery key requires owner handoff; permission to enable FileVault does not authorize the assistant to type, paste, upload, email or store it. Saving authentication material needs the specific storage authority as well. New credentials, new recovery access or a material expansion of persistent access require their own applicable action-time confirmation; do not hide them inside a convenience step.

Treat enabling an additional disk-unlock user as a separate persistent-access/security change. Resolve the exact existing identity and obtain action-time approval before that step, with its password interaction left to the owner. Do not enable all listed users automatically or assume the administrator role equals startup-unlock permission. Preserve existing accounts; creating, promoting, removing or resetting a user is outside this workflow. If required access cannot be established by the supported route, hold activation or report the unresolved access requirement rather than modifying token records.

## 4. Use the native activation route once

Follow the version-matched [Apple setup procedure](https://support.apple.com/guide/mac-help/protect-data-on-your-mac-with-filevault-mh11785/mac). The current route is System Settings → Privacy & Security → FileVault. Review the target and confirmation before the activation control, then leave protected steps to the owner. Continue only the selected recovery route. If an Enable Users control appears, apply the separate exact-user gate above.

These are landmarks, not blind clicks. Resolve differences between the installed version and current documentation before acting. Do not substitute Disk Utility encryption, command-line provisioning, a configuration profile, new management enrollment or another startup volume. Do not disable Secure Boot, change firmware protections, alter FileVault policy, rotate keys or decrypt the installation to obtain a cleaner workflow.

After handback, read the non-secret result. Keep “owner completed the dialog,” “native setting on,” “conversion in progress,” “waiting for another step” and “protection verified” distinct. Submit once. A control timeout or lost connection does not prove the operation failed; inspect the same native state before considering a retry. Never toggle protection to recover from an uncertain UI response.

Follow the actual native progress and documented conditions for that Mac. Keep reliable power available and respect any displayed power or restart requirement. Do not disable sleep, change power policy, force shutdown or promise a universal completion time. Recheck at sensible intervals while the operation remains active and observable. If it remains pending, retain that status rather than relabeling a started process as complete. If observation or owner participation becomes unavailable, report the last evidenced state and exact next step without claiming completion.

## 5. Verify protection, then bounded normal use

Reopen the native FileVault page on the same running installation after the operation settles. Establish active protection and whether any setup, conversion, error or required activation step remains. Keep a short secret-free description of the observed result. Do not expose a recovery-key reveal control or capture the entire security pane when text is sufficient. If current observations conflict or the interface cannot establish completion, retain the uncertainty and consult the version-specific official route; do not manufacture a pass with a login test.

For a requested normal startup check, first confirm that the owner can act locally at startup, knows the intended unlock identity, has independently accessible recovery custody and has saved relevant work. Restart only in the approved interruption window using normal supported controls. Do not restart merely because a checklist needs another check when the user authorized status-only work. A pending unrelated update or a changed session state must be resolved before interruption.

The owner performs startup authentication privately. After return, reidentify the same Mac, startup installation and intended user, then reread FileVault state. A successful remote reconnect alone proves none of those. Record an observed startup boundary only if it was actually observed; an owner's account of it remains user-reported. Do not send blind input to a disconnected preboot screen.

Apple's [unlock behavior explanation](https://support.apple.com/guide/mac-help/how-does-filevault-work-on-a-mac-flvlt001/mac) distinguishes a user who can start/unlock the Mac from one who can log in after somebody else has unlocked it. Do not claim independent startup unlock for every account from one successful login. Where more users' access is essential, establish each required capability through available native evidence or an agreed owner-controlled check; state what remains unverified rather than conducting unnecessary restart cycles.

Perform the agreed small ordinary-use check, such as reopening one previously saved local document in its existing application. Use its actual location, without overwriting, conversion, external refresh or new cloud sign-in. If a write check is required, save a separate approved harmless item and reopen it; do not modify the sole original. This establishes only that bounded use. It does not verify every file, authenticate a recovery key, prove resistance to attack or certify the whole machine.

Leave the requested final session state. Do not call an unlocked working session inaccessible to its apps simply because FileVault is on. Do not alter lock timing, remove users, delete check files/backups or change future security policy as cleanup.

## Failure and recovery decisions

- **Approval, administrator or private handoff unavailable:** leave the setting unchanged and return the exact prepared step
- **Custody unresolved before activation:** hold activation; do not create recovery material that the owner cannot retain safely
- **Custody uncertain after a partial setup:** preserve the current working session and protection state, avoid elective restart/sign-out, and have the owner resolve private custody through the supported route; do not reveal or rotate a key yourself
- **Operation pending or response lost:** reidentify the same target and inspect native state before another action; retain progress and the next required observation
- **Unexpected unlock membership or account change:** stop expansion, report the discrepancy and seek the specific supported correction; do not remove access automatically
- **Startup authentication or recovery screen:** stop automation and hand the protected step to the owner; do not guess, reset, erase or repeatedly restart
- **Storage errors, failed conversion or conflicting status:** preserve work and evidence, hold completion and use the official support path for the exact symptom; repair/restore and diagnostic uploads need separate scope and permission
- **User abandons setup:** distinguish no change, active protection and an unfinished operation. Turning FileVault off is a new security change, not a harmless rollback or required cleanup

There is no promised one-click restoration of the original state. Preserve existing backups and access routes. Do not erase, repartition, reinstall or weaken security to make the acceptance check succeed.

## Acceptance and private handoff

Return a concise receipt with:

- Target Mac/startup identity, macOS version and baseline FileVault state
- Approved route and actual current state, including any pending step or error
- Observed unlock identities and any requested membership still unresolved
- Owner-confirmed custody class and independent availability, with no secret or location detail
- Preservation evidence and its limits
- Startup/use checks separately labeled observed, user-reported, unrun or blocked
- Final session state and a precise remaining owner action, if any

Use **prepared; no activation initiated**, **activation pending**, **active protection verified; startup check unrun**, **active protection verified with bounded startup/use evidence**, or the exact blocked state. If FileVault was already active, say so rather than claiming new activation. Do not accept the complete requested outcome while required custody, protection completion or essential unlock access remains unresolved. A saved receipt, if requested, belongs in its approved private destination and needs readback; sharing it is separate.

Keep the scope explicit: this protects the selected startup installation at rest within the native FileVault boundary. It does not establish backup encryption, protection of external copies, secure erasure of historical data, safety of an unlocked session or successful disaster recovery. Stop after the requested outcome is evidenced or a concrete dependency requires the owner's action.

## Fictional, unexecuted illustration

A fictional owner requests protection of a personal Apple silicon laptop's existing internal startup installation. The paper baseline says FileVault is off, even though the platform already encrypts storage. The owner requires independently accessible recovery custody and continued use by two existing adults; only one account's startup-unlock capability is established. A document export is still running.

The proposed workflow would resolve the recovery storage/sync behavior and second account's required access before activation, then obtain exact security and access confirmations. It would not treat the hardware encryption as a completed result or interrupt the export. The owner would perform all protected steps privately.

Suppose a later invented observation says FileVault is on, custody is owner-confirmed and the required account access is established, but no restart was authorized. The receipt would say active protection verified with the normal startup check unrun. If instead the status showed a pending step, the result would remain activation pending. Neither branch would claim a recovery exercise or an encrypted backup.

This illustration is original, fictional and unexecuted. No computer, account, secret, file, setting, encryption operation, restart, recovery flow or live acceptance check was accessed or performed for it. All operational steps above are instructions for later authorized work, not validation results.
