---
name: update-desktop-operating-system
description: "Apply a bounded in-place desktop OS update through its native supported updater, preserving existing work and carrying exact release identity through restart and usability checks. Use for an existing macOS or Windows installation, not clean installation, fleet deployment, firmware servicing, recovery reinstallation or changing update policy."
---

# Update an existing desktop system through a verified restart

Deliver the requested operating-system update on one identified computer, or its precise pending/blocked state, with a short before-and-after record. Keep the selected update, affected installation, restart and usable post-update session connected. A downloaded package, completed preparation phase or visible sign-in screen is not the same as an activated and usable updated system.

Use the existing native updater for an ordinary supported macOS or Windows installation. Preserve the user's release/channel choice. Do not turn a maintenance update into an unrequested major upgrade. Exclude beta enrollment, unsupported hardware workarounds, edition or architecture conversion, dual-boot changes, standalone firmware flashing, managed-fleet policy, reset, erase, clean installation and recovery reinstallation. An OS update may include vendor-supplied system components; inspect disclosed bundle effects instead of promising that only one visible version string changes.

[Installer-media preparation](../create-bootable-installation-media/SKILL.md) produces a separate bootable device. [Dependency-upgrade planning](../dependency-upgrade-plan/SKILL.md) assesses an application's package change. Neither establishes that this existing desktop has completed its update. Use [backup coverage planning](../plan-file-backup-coverage/SKILL.md) if required data protection is unresolved; do not silently add a whole-computer backup project.

## Establish the bounded update

Resolve only facts that change the route or acceptance:

- Computer and currently running installation, OS edition/release/build, hardware model and architecture where relevant; distinguish the local host from a remote desktop or VM
- Whether the request covers advice, downloading/preparing, installation, or installation plus the required restart and checks
- Intended target: one named update, a selected major release, or supported stable maintenance updates within the current release; record exclusions such as previews and optional drivers
- Current updater state, including already-running work, an existing pending restart, failures and organization control
- Important open work and applications/peripherals that must remain usable; choose a small concrete acceptance activity
- Existing recovery evidence for required data, owner-controlled sign-in/recovery access, power/network readiness and available startup-volume space
- Permitted interruption window, other signed-in users or active jobs, local assistance during startup, and the final state the user needs

Use the request and available observations instead of a mandatory interview. Ask when “update my computer” leaves a material choice, such as staying on the current major release versus accepting the next one. If the intended update is already installed, verify that exact identity and requested usability rather than installing another release merely to perform an action.

For remote work, establish how observation can resume after restart and who can handle startup prompts. The current connection may end before the installation finishes. Do not enable remote access, automatic login or a new persistent account grant to keep control. When no permitted post-startup observation is available, distinguish a preparation-only result from a request that must wait for local help.

## 1. Bind the baseline, offered update and compatibility evidence

Read the OS's native version information and the updater's current state before starting another check or installation. On Windows, [Settings > System > About](https://support.microsoft.com/en-us/windows/experience/find-information-about-your-windows-device) provides edition, version and device information. On macOS, [About This Mac](https://support.apple.com/en-us/109033) shows the release; clicking its version reveals the build. Record the exact reported identifiers where available, without copying full device serials or unrelated account details into the handoff.

Distinguish four identities:

1. Running baseline release/build
2. Update offered or already staged, including a Windows KB identifier when shown
3. Intended target and any required prerequisite sequence
4. Actual running result after installation and restart

A release name is insufficient if several revisions share it. A successful older update-history entry does not identify today's pending update. Keep a pre-existing pending restart separate from the update the user just selected; determine what it will activate before treating it as a harmless preliminary restart.

Check current official release and compatibility information for the exact target and important dependencies. An update being offered is useful eligibility evidence, but does not prove that every required application, plug-in, peripheral or organization service works with it. Use the software/device publisher's relevant support statement for essential compatibility constraints. Do not remove an incompatible app or update a driver as an incidental prerequisite without resolving its scope and authority.

Use the native supported offer as the normal route. [Apple Software Update](https://support.apple.com/en-us/108382) selects updates compatible with the Mac model. If a specifically requested release is not offered, establish why or hold that target; do not substitute an arbitrary downloaded installer. Microsoft's [Windows installation guidance](https://support.microsoft.com/en-us/windows/deployment/install-upgrade/ways-to-install-windows-11) recommends waiting for the Windows Update offer when moving to Windows 11. A missing offer can reflect eligibility, readiness or a compatibility issue; it is not by itself proof of any one cause.

Respect [Windows safeguard holds](https://learn.microsoft.com/en-us/windows/deployment/update/safeguard-holds). They can withhold a feature update because of known issues. Do not opt out, change registry policy, use installation media to evade the hold, or present a forced update as ordinary troubleshooting. Preserve the displayed message and any available hold identity, and identify the owner or documented resolution. Check current support status for the actual edition/channel; a broadly worded support page does not settle a special servicing entitlement.

## 2. Preserve work and establish a usable recovery boundary

Save open work through each application's normal mechanism and verify the relevant saved result. Resolve unsaved buffers, in-progress exports, synchronization conflicts and active long-running jobs before their interruption. Check other signed-in sessions when the interface exposes them; a clear desktop is not proof that nobody else has unsaved work. Do not force-close another user's session.

Establish protection proportionate to the selected update and required work. Read existing backup completion/coverage evidence and its date; identify work changed since that point. An enabled backup switch, a current cloud folder or an unexamined restore point is not a verified recovery copy. If fresh capture or a restore spot check is required, use its separately scoped authorization and approved destination. Keep any protection gap explicit; hold installation when it conflicts with the user's retention requirement. Never upload private files or collect credential stores just to satisfy a checklist.

Confirm reliable power, a permitted connection and enough space on the actual startup volume for the documented route. Use current target-specific requirements and the updater's own result, not a universal free-space number. If space is insufficient, stop at that prerequisite. Do not erase old installations, delete backups, alter partitions or run a cleanup utility automatically. Those operations may remove the very recovery material the user is relying on.

Have the owner confirm they can complete sign-in and any device-encryption recovery through a route available while this computer is unavailable. Do not inspect, copy, transmit or include passwords, PINs or recovery keys in chat, screenshots or records. Microsoft's [BitLocker recovery guidance](https://support.microsoft.com/en-us/windows/security/encryption/find-your-bitlocker-recovery-key) explains that startup changes can lead to recovery and that the correct key may belong to a personal or organizational account. Keep only the readiness or blocker, and hand protected retrieval/entry/submission to the owner. Do not test readiness by deliberately triggering recovery.

Keep security and management settings intact. Do not suspend encryption, clear the TPM, disable Secure Boot, turn off endpoint protection or remove a management profile as generic update preparation. If the documented route requires such a change, stop for a separate supported decision with its required permission.

Do not promise a universal undo. Before a major version change, establish the available supported recovery route and its limits. Microsoft's [Go back guidance](https://support.microsoft.com/en-us/windows/deployment/install-upgrade/go-back-to-the-previous-version-of-windows) describes a limited window, usually ten days, and requirements for retained previous-installation files. It also warns that post-upgrade apps, drivers and settings can be affected. Inspect actual availability rather than deriving a guaranteed deadline from the calendar alone. Do not apply that Windows mechanism to macOS or assume an ordinary file backup is a bootable rollback. Preserve recovery material; performing a rollback or restore is a separate action.

## 3. Select the update without changing future policy

Open the updater for the identified installation and inspect each offered item and control. Separate stable OS maintenance, a major/feature upgrade, optional preview, driver/firmware update, application update and a repair/reinstall offer. Several may appear together. Select only the authorized target and its understood dependencies. If the updater exposes an inseparable broader bundle that conflicts with the request, explain that boundary instead of clicking Install all.

Keep advice-only inspection passive. A button labeled Check for updates can lead into downloading or installing under current settings; do not treat every refresh control as a read-only lookup. Use current displayed state and official documentation first, then invoke a check within the authorized operational scope. Record what actually starts, including existing automatic activity, without claiming the assistant caused all activity visible afterward.

For **Windows**, Microsoft's [native installation procedure](https://support.microsoft.com/en-us/windows/deployment/updates-lifecycle/install-windows-updates) uses Settings > Windows Update, the available download/install control and a restart when required. Follow the actual version's interface. Before selecting a feature upgrade, inspect its target and any license step. Do not switch to Installation Assistant, media-based setup or a repair installation merely because the ordinary offer is missing or slow.

Preserve existing update preferences. The [get-updates-early setting](https://support.microsoft.com/en-us/windows/deployment/updates-lifecycle/get-windows-updates-as-soon-as-they-re-available-for-your-device) affects future non-security and feature-update delivery. It is not a one-time install button. Do not enable it, join an Insider channel, change active hours, remove a pause or alter metered-connection policy unless that settings change is part of the request. Selecting one restart time, when explicitly requested, is different from changing the computer's ongoing update policy.

For **macOS**, use System Settings > General > Software Update or the supported equivalent for that release. Reconcile the displayed update/upgrade target before selecting its action. Apple's [update procedure](https://support.apple.com/en-us/108382) includes administrator authentication and possible repeated restart/progress screens. Hand authentication to the owner through the supported secure flow; do not request the password in a message or enter it in a command.

Ordinary updates do not need an invented extra approval round when already permitted. Pause at an actual new boundary: an unapproved interruption, different release or bundle, unexpected permission, protected credential step, new explicit license agreement, permanent data loss, security-setting change or expanded access. Disclose and link new applicable terms before acceptance and obtain the required approval; report an agreement actually accepted. An update request does not authorize a paid support plan, optional service enrollment, telemetry upload or account migration.

Immediately before committing installation/restart, recheck the selected computer, target, saved-work state and allowed window. A user starting a new call or a changed update offer can invalidate earlier readiness. Where third-party warnings require confirmation, carry forward applicable approval and ask only for missing or changed effects.

## 4. Carry the same operation through restart

Start one native operation and observe its real stage. Keep downloading, preparing, installing, awaiting restart, startup processing, sign-in required and final verification distinct. Retain minimal timestamps, update identifiers and error text. Do not run a second updater or launch another installation because a control response times out.

If the updater permits a download-only or scheduled-restart state, report exactly what it saved and what could still happen automatically. Do not promise that the computer cannot restart based only on a visible scheduling field. A request that forbids interruption must stay within a supported route whose actual effects satisfy that constraint; otherwise hold before the action that can cross it.

Restart only within the accepted interruption scope after saving work. Prefer the updater's supported restart action so it can finish its own sequence. Do not repeatedly restart, choose a different startup disk or boot external media to accelerate it. Keep power connected and follow the vendor's installation conditions. Apple explicitly advises leaving the lid open and avoiding sleep while its update completes.

Loss of the desktop connection is expected during some restarts, but it is not proof of either success or failure. Resume observation of the same computer when it becomes available. Have the owner report the visible local state if needed, distinguishing their report from direct observation. Do not send blind keystrokes to an unseen sign-in, recovery or setup screen.

A slowly changing progress bar alone does not justify a power cut. Apple's [startup-progress guidance](https://support.apple.com/en-us/102535) notes that update progress can pause for long periods. Use elapsed time, actual messages and version-specific official guidance to distinguish an active installation from a terminal error or genuinely stalled state. Never invent a universal timeout after which forced shutdown is safe.

Keep pending work open when completion is still observable and authorized. If observation is lost or the user cannot provide the required local step, report the exact last state and blocker. Do not claim a completed update merely because the maintenance window ended, and do not interrupt an active system write to meet that window.

## 5. Verify the activated result and the user's required work

After startup and owner-controlled sign-in, verify the same computer and normal user environment. Do not mistake a temporary account, recovery environment, another startup volume or a different remote machine for the expected session. Handle new optional setup offers without enrolling accounts or changing privacy choices merely to reach the desktop.

Read the native running OS version/build and compare it with the selected target. On Windows, also inspect the relevant Update history entry and current restart/error state; Microsoft documents the [history location](https://support.microsoft.com/en-us/windows/deployment/updates-lifecycle/get-windows-updates-as-soon-as-they-re-available-for-your-device). A history entry and a running-build observation answer different questions. If one update does not change the displayed main OS build, use its official identity and native installation evidence rather than inventing a build mismatch.

Reconcile each requested target as active, failed, automatically rolled back, still pending, superseded with supporting evidence, or unresolved. An “up to date” banner is scoped to that updater and device; it does not prove that a specific unoffered release is installed or that every product is patched. If the resulting version differs, read the actual outcome before retrying. Do not silently accept a major version outside the request.

Perform the agreed small usability check using preserved work or a separate disposable sample:

1. Open the required application and a representative existing file without overwriting or converting the sole original
2. Confirm the specific needed interaction, such as reading and saving a separate local copy, using a selected display, or reaching an already authorized service
3. Reopen any saved sample and check the expected content when persistence matters
4. Check that the essential dependency identified before the update still works, and record unrelated pre-existing failures separately

Do not let opening a library silently migrate its only copy to a new format; use an approved copy or hold at the conversion prompt. A successful login or app launch alone does not prove the user's actual workflow works. Conversely, a network-service outage or an already-broken printer should not automatically be attributed to the OS change. Compare the baseline and localize the failure before recommending recovery.

Finish against the original target. If prerequisites legitimately require another update/restart cycle, confirm that the next item belongs to the authorized sequence and repeat the relevant checks. Do not chase newly released updates indefinitely or install optional extras to make the page empty. If the user requested “fully current,” define the release/channel, included categories and observation cutoff before treating that phrase as an unlimited sequence.

## Recover without expanding the operation

- **Offer unavailable or blocked:** retain the exact target and message, check applicable official guidance and stop at eligibility/management constraints; do not bypass them
- **Insufficient space, power or connection:** preserve the current stage and solve only an authorized prerequisite; do not clear recovery files or substitute a new network destination
- **Download/preparation error:** inspect the existing operation and native error first; retry through the supported route only after an evidenced correction and within the agreed time/resource budget
- **Restart pending:** preserve the actual pending state and arrange the already-authorized next step; do not report activation from download or preparation success
- **Credential or recovery screen:** stop blind operation, hand protected entry to the authorized owner and retain only the nonsecret state
- **Automatic rollback:** verify the running result and record the failed target; returning to the desktop does not make the attempted update successful
- **Post-update app/data issue:** preserve originals and current work, compare the baseline, then prepare the narrow supported remedy; uninstalling updates, restoring a backup, reinstalling the OS or reverting the release needs its own scope and permission
- **Uncertain or stalled startup:** seek local observation and the exact official recovery procedure before any potentially lossy action; do not reset, erase, repair volumes or force power off as an automatic retry

Read troubleshooting instructions for their effects before using them. A vendor page can contain escalating repair, service-reset, driver-removal or security-disable suggestions; their publication does not authorize them. Stop at a new security, deletion, credential, management or recovery boundary. Retain minimal private evidence for the next decision; do not upload diagnostic logs or contact support without the relevant approval.

## Acceptance and handoff

For preparation-only work, return the selected target, supported route, readiness evidence, restart requirement, recovery limits and unresolved decisions, labeled **prepared; no update initiated**. If an existing automatic operation was already active, disclose that separately.

For actual completion, require:

- The intended installation and target remain identified through the operation
- Required preservation and interruption conditions were met
- Native results establish installation and any required restart/activation, with no unresolved target-specific failure or pending step
- Requested basic usability checks have their real outcomes and coverage limits

Return a concise private receipt: baseline and final versions/builds; selected update identifiers and route; observed completion/restart times; accepted terms if applicable; checks observed, user-reported or unrun; any remaining issue; and the available recovery decision with its limits. Use **downloaded**, **awaiting restart**, **installed; usability check pending**, **completed within checked scope**, **rolled back**, or the precise blocked state as supported. Save a requested receipt to the approved location and read it back.

Do not claim that a small acceptance check certifies every file, peripheral, security fix or future stability. Do not delete previous-installation files, remove backups, enroll future monitoring or change ongoing update policy to tidy up after completion. Those are separate decisions.

## Fictional, unexecuted illustration

A fictional user requests a supported maintenance update on one Windows laptop, staying within its current feature release. A drawing must remain readable in an existing app. The updater shows both a cumulative update and an optional preview; it also shows a pending restart from earlier activity. The user has not yet agreed to interrupt a running export.

The proposed workflow identifies what the pending restart will activate, preserves the drawing and resolves the export's interruption before proceeding. It leaves the preview and the get-updates-early setting alone. Suppose an invented intermediate observation says “installation complete; restart required” while the running build remains the baseline. The result would remain pending activation. A disappearance of the remote connection would not close that gap.

After an authorized restart, a hypothetical new build and matching history entry would establish the selected update's running state. Opening a separate copy of the drawing and completing the agreed save/reopen activity would add bounded usability evidence. If the machine instead returned to its baseline after an automatic rollback, the receipt would identify the failed target and preserved current state, without immediately starting a second attempt or deleting rollback files.

This illustration is original, fictional and unexecuted. No computer, account, application, update, file, restart, backup or recovery operation was accessed or performed for it. All operational checks in this guide are instructions for later authorized work, not claims of completed validation.
