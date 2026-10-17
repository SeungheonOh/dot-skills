---
name: uninstall-desktop-application
description: "Remove one selected desktop application through its supported installation-specific route, preserving required local work and verifying the resulting installation state. Use for a bounded native uninstall, not file cleanup, subscription cancellation, account deletion, malware removal or removing managed/security software."
---

# Uninstall the intended application without discarding its work

Deliver the requested application removal, or a precise held/pending result, with a short record of the installation removed, retained data and remaining checks. The app's shortcut disappearing is not evidence that its installation was removed. An uninstall completion message is not proof that every related file, service, account grant or billing commitment disappeared.

This workflow covers an ordinary user-selected application on macOS or Windows. Keep [storage cleanup](../storage-cleanup-accounting/SKILL.md), [subscription cancellation](../cancel-service-subscription/SKILL.md), [tool-switch planning](../plan-tool-switch/SKILL.md) and [device handoff preparation](../prepare-device-handoff-record/SKILL.md) separate. Removing a desktop app is a local software-lifecycle action; it does not establish data erasure, account closure, license release or a working replacement.

Exclude OS components, device drivers, endpoint protection, VPN/network security clients, management agents and organization-mandated software. If the selected product turns out to control those functions, stop this ordinary removal path and identify its responsible owner and supported process. Do not disable safeguards to make an uninstall succeed.

## Establish the bounded removal

Resolve only the inputs that affect the operation:

- The computer, OS/version and account; distinguish this desktop from a remote session or another person's machine
- The exact product, publisher, version/edition and installation location or native installation identity when available
- Whether the request is preparation only or actual removal, and whether one version or every specifically named copy is selected
- Required documents, local databases, presets, plugins, downloads or unsynced work to retain
- Existing installer/store/vendor-manager route, any other apps sharing its components, and management restrictions
- Whether closing the app, interrupting its jobs or restarting the machine is already acceptable

An explicit instruction to uninstall the identified ordinary app authorizes its scoped supported removal, subject to the action-specific gates below. A request to investigate a problem, reduce storage use or prepare a plan does not authorize uninstalling it. Do not add a replacement, reinstall it, deactivate its license or cancel its plan unless that action was also requested.

If the app is already absent, verify the relevant installation scope and report that finding rather than deleting vaguely related files. If several versions or publishers match, resolve the intended installation before changing anything. Ask only the question that changes the next action.

## 1. Bind the request to an actual installation

Inspect the relevant native app list, vendor manager or Finder location. Record enough evidence to distinguish the target: product/publisher, version, account versus shared installation, and path or package identity when exposed. Keep the original record for the final readback.

Distinguish an installed application from its shortcut, downloaded installer, mounted installer image, browser-installed web app, portable copy and suite manager. They can have the same display name but require different removal routes. Do not delete an installer and call the installed program removed. Do not treat uninstalling a suite manager as uninstalling one product it manages.

Use current official guidance for the exact product and installation channel. A store installation, standalone package and vendor-managed edition may use different ownership and uninstall mechanisms. Where available, prefer the already-installed supported uninstaller over a newly downloaded utility. A filename containing “uninstall” does not establish its provenance or its target.

Inspect scope before proceeding. A shared installation can affect other users on the machine; a suite removal can affect other products. If that effect was not part of the request, explain the exact additional scope and obtain the missing decision. Do not switch to an all-user operation simply because a current-user action failed. For a managed device, use the owner's approved route and respect disabled controls.

## 2. Preserve work that removal can strand or destroy

Check the selected app's open documents, pending saves, exports, queued jobs and visible synchronization state. Save existing work through its normal mechanism when authorized and quit normally. Do not force-quit merely because the uninstaller says the app is busy. If the only copy is an unsaved buffer, resolve preservation before removal; [unsaved-work recovery](../recover-unsaved-editor-work/SKILL.md) is a separate recovery route when needed.

Separate these data classes when they are relevant:

| Class | What to establish before removal |
| --- | --- |
| Ordinary documents outside the installation | Their actual locations and whether the user still has a way to read required formats |
| App-managed libraries/databases | Whether the selected uninstall removes them, and the supported backup/export needed to preserve them |
| Preferences, presets and plugins | The meaning of the uninstaller's keep/remove choice, including whether another installed version shares them |
| Cloud or synced work | Which required changes reached the service and which remain local; cloud-looking placeholders are not independent local copies |
| Downloaded content/caches | Whether they can actually be reacquired and whether any selected item is the sole usable copy |

Do not assume that a successful sync badge proves all historical data is retained, that reinstalling reconstructs a local database, or that an app's data folder is disposable because it is named “cache.” Check only the bounded data needed for this request rather than inventorying every user's files.

Preserve an existing approved copy or use the product's supported export/backup when the user has authorized the data and destination. Reopen a representative export or obtain the relevant native recovery evidence before relying on it. A copied live database can be incomplete; use its supported consistency procedure. If required preservation cannot be established, hold removal and name the missing step. Do not silently upload a library or broaden a backup job.

When the user requires continued readability after removal, establish that separately before uninstalling the only available reader. An export may preserve visible content while losing editability or history. Resolve the needed property rather than declaring that any PDF or screenshot is an equivalent backup.

For later recovery, record the available official reinstall source and known version/license limits without collecting a product key or credential. Do not promise that an old release remains downloadable or that retaining preferences preserves an activation. If a vendor requires deactivation first, treat that as a separate account/license action with its own scope and authority.

## 3. Select the supported route and inspect its effects

Use the actual OS and product interface; labels can change. The following are entry points, not permission to follow every linked cleanup or troubleshooting step.

### macOS

Locate the exact app in Finder, including whether it is in the shared Applications folder or the user's own Applications folder. [Apple's removal guidance](https://support.apple.com/en-us/102610) recommends an app's supplied uninstall feature when available because it can handle associated components. Otherwise the supported ordinary route is moving the selected app to Trash. Preserve its original location for reversal.

Do not substitute a Dock-item removal for application removal. Treat moving an app to Trash and permanently emptying Trash as different operations. A Trash move retains recoverable bytes; do not claim that it reclaimed that payload's storage. Do not empty Trash, which may contain unrelated work, to finish a routine uninstall. Any requested permanent deletion needs its own exact scope and required action-time confirmation.

If the app cannot be removed because it is required by macOS, stop. If it is in use, preserve and close its work normally before retrying. A restart or Safe Mode procedure is not an automatic next step; establish its necessity and permission first. Never delete protected system paths or weaken protection to force the operation.

### Windows

Identify the exact installed entry, then use its supported native uninstall control. [Microsoft's removal guidance](https://support.microsoft.com/en-us/windows/uninstall-or-remove-apps-and-programs-in-windows-4b55f974-2cc6-2d2b-d092-5905080eaf98) describes Settings > Apps > Installed apps and, for programs requiring it, Control Panel > Programs > Programs and Features. Inspect the presented action: a combined Uninstall/Change entry can lead to maintenance choices rather than immediately remove the product.

Choose removal for the identified installation, preserving other versions and shared components unless their removal is explicitly part of the approved scope. Do not remove a program by deleting its Program Files directory, editing installation records or clearing registry keys. If a built-in app has no supported uninstall route, do not invent one by changing system permissions or running a bulk removal command.

### Vendor-managed applications

Use the correct product entry in its existing official manager, not an unrelated generic cleanup tool. Inspect each retention choice. For example, [Adobe's Creative Cloud uninstall guidance](https://helpx.adobe.com/creative-cloud/apps/manage-apps/creative-cloud-apps/uninstall-or-remove-apps.html) distinguishes keeping from removing app preferences and plugins. That is an app-specific choice, not a universal promise about documents or every other vendor's uninstaller.

Choose a supported keep-data/preferences option when it fits the user's retention requirement. An option called “clean removal,” “reset,” “remove all data” or “all users” needs its actual effects resolved before acceptance. If the UI cannot preserve required data, cancel before the destructive step and report the conflict.

## 4. Apply the action gates at the real boundary

Carry forward the user's exact removal approval. Do not ask again solely because the normal supported path has another navigation screen. Pause for a changed effect or a permission that the earlier request did not supply:

- **Permanent user-data loss:** Obtain the required action-time confirmation for the exact data and operation. A general uninstall request is insufficient for irrecoverable libraries, preferences, projects or Trash purges. If an uninstaller's destructive scope is unclear, stop instead of treating it as a benign default.
- **Credentials or elevation:** Hand over password/PIN entry and submission through the supported secure flow. Do not request, record or enter administrator credentials yourself. An elevation prompt does not expand the approved target or authorize security changes.
- **Additional software or access:** A new cleanup utility, replacement app, driver, persistent grant or permission requires its applicable authorization. Do not grant broad disk access to make removal convenient.
- **Interruption or collateral effects:** Resolve an unapproved restart, closure of other users' work, removal of shared components, changed default handlers or loss of another app's function before proceeding.
- **External/account effects:** Uploading diagnostic logs, sending support messages, signing out of multiple products, deactivating licenses, revoking access, accepting new terms and deleting accounts are separate actions. Do not submit an optional exit survey or invent a cancellation reason.

Review third-party warnings against the same scope and obtain required confirmation when not already covered. A warning about losing the selected installation is different from one that also deletes user content. Never bypass a browser or OS security warning.

Immediately before commitment, recheck the installation identity and retention selections. Cancel if the target, version, scope or current work changed. Perform one supported removal operation and retain its result or minimal error text. Do not start several uninstallers in parallel or retry a timed-out removal before inspecting the current state.

## 5. Verify the resulting state without relaunching or reinstalling it

Refresh or reopen the native installation view or vendor manager for the same account and scope. On a Finder route, inspect the original app location and the exact Trash item. Use the baseline identity, not just a fuzzy name search.

Reconcile separate observations:

1. **Removal operation:** completed, failed, pending restart, cancelled or uncertain, supported by the native result
2. **Installation:** selected registered entry/bundle absent from its original location, retained in Trash where applicable, or still present
3. **In-scope components:** any app-specific helper or extension identified by the supported procedure has the expected state; unresolved components remain explicit
4. **Required data:** retained locations or preservation artifacts remain present and satisfy the agreed checks
5. **Unaffected scope:** other selected-to-keep versions/products remain in their native inventory; report any unverified functional dependency honestly

Use narrow read-only inspection of a remaining helper when necessary. A running process can mean the operation is incomplete, a documented reboot is pending, or a component belongs to another retained product. Resolve its identity before proposing another action. Do not kill all similarly named processes, remove services or delete an entire publisher folder.

A stale shortcut, search result, installer download or retained preferences directory does not alone prove the app is still installed. Conversely, absence from one list does not establish that a portable or per-user second copy is gone. Only report the inspected scope. Do not launch a stale shortcut to “check absence” when it might reinstall the app, open a store or run another copy.

If restart is required to complete removal, report that intermediate state. Restart only when authorized and after preserving other work; after it, repeat the relevant installation/component checks. If restart must wait, keep final removal verification pending rather than declaring full completion.

Do not calculate reclaimed bytes from the app's advertised size. If the user also requested a storage result, measure the same volume before and after through the storage workflow and disclose attribution limits. Retained files are not an error when retention was required. This operation does not certify secure erasure or absence of every trace.

## Failure handling and recovery

- **Uninstall hangs or times out:** check whether the same operation is still active and inspect its native status. Avoid a second concurrent operation, forced shutdown or deleting its working files. Preserve the last observation and use the official product-specific recovery path when within authority.
- **Installer reports a missing package or broken uninstall:** retain the exact product/version and error, then consult its official support route. Reinstallation to repair uninstall, a troubleshooter or cleanup tool is a new consequential action; inspect its effects and obtain missing approval first. Do not erase the installation record merely to hide the entry.
- **Partial removal:** list what changed and what remains. Preserve data and logs privately, stop destructive retries, and identify the supported next step. An error is not proof that nothing changed.
- **Required data is unexpectedly missing:** stop further removal and cleanup. Preserve remaining recovery locations and investigate the precise retained copy or supported restore route. Do not overwrite surviving data with an older export automatically.
- **The user asks to reverse:** for a recoverable Trash move, confirm the original path is free and restore only the identified app when authorized. For a completed native uninstall, use the approved official reinstall route if requested, then restore retained data through the supported mechanism. Reinstalling software alone does not prove that preferences, licensing or documents were restored.

Do not run a whole-machine cleaner, remove all apps from a publisher, disable device management or clear shared caches as escalation. Finish at a truthful terminal result or pause at a precise missing approval, owner action or capability. A pending native operation remains pending until it completes or the user changes the stopping condition.

## Acceptance and handoff

For preparation-only work, return the exact target, supported route, preservation requirements, expected effects and remaining approvals, labeled **prepared; no removal performed**.

For actual removal, completion requires the identity-bound operation and appropriate native readback, preservation of required work, and resolution of any completion-blocking restart or helper state. A recoverable Finder removal can be reported as **moved to Trash; not permanently deleted**. Keep partial, blocked, failed and outcome-unverified results separate from complete.

Return a compact private receipt:

- Product/version, computer/account scope and installation identity
- Removal route and actual operation result, with observation time
- Native readback and any pending restart or component check
- Data/preferences retained and exact recovery limitations
- Unchanged subscription/account/license obligations when relevant to the request
- The specific next action if anything remains

Include only useful identifiers; avoid secrets, broad directory inventories and screenshots of unrelated accounts. Save a requested receipt to the approved destination and read it back. Do not publish logs or contact support merely to close the record.

## Fictional, unexecuted illustration

A fictional user asks to uninstall Meadow Diagram 4 from their Windows desktop while keeping Meadow Diagram 3 and their reusable templates. The invented vendor manager shows both versions and one shared template directory. Version 4's removal dialog offers to keep or remove preferences and templates; its default is removal. One unsaved drawing is open.

The proposed path first saves the drawing to the user's approved project location and verifies that copy. It identifies only version 4, changes the retention choice to keep, and checks the actual scope before committing. If the dialog instead says it will remove the shared directory regardless of that choice, the operation is held for preservation and a decision; version 3 is not removed to simplify matters.

Suppose the fictional uninstaller then reports that a restart is required. The receipt would say that removal was submitted and completion verification awaits an authorized restart. A later absence from the manager, expected helper state and preserved template directory would support the final bounded result. A leftover desktop shortcut would not justify deleting the templates or running a cleaner. No subscription or license cancellation would be inferred.

All products, states and observations above are invented. This is an authored decision illustration, not an executed uninstall or application test. No software, account, device, file collection or restart was operated for it.
