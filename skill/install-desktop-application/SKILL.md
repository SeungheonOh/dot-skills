---
name: install-desktop-application
description: "Install one selected ordinary macOS or Windows application from its official source, preserve existing copies and user data, and verify launch from the installed location plus one useful activity. Use for a new native application setup, not upgrades, fleet deployment, system drivers or browser extensions."
---

# Install the intended desktop application and prove it is usable

Deliver the selected application at a durable installed location, with its actual version, account scope, first-run choices and a bounded demonstration of the requested function. A downloaded installer, store receipt, desktop shortcut or successful launch from a mounted disk image is not a completed installation.

Keep this workflow to one ordinary user-selected native application on macOS or Windows. Product selection, paid purchasing, version upgrades, repair installs, migration of existing libraries, unattended deployment, portable-app packaging and system-level software are separate decisions. Exclude drivers, security agents, VPN clients, remote-control services and device-management tools; their access and recovery requirements are different.

[Browser extension setup](../install-browser-extension/SKILL.md) handles browser-specific grants and site scope. [OS updating](../update-desktop-operating-system/SKILL.md) carries a system release through restart. [Application removal](../uninstall-desktop-application/SKILL.md) preserves work through an uninstall. None establishes the acquisition-to-installed-launch chain covered here.

## Establish the small installation contract

Resolve from the request, native inventory and official product guidance:

- The intended computer, operating system/version, processor architecture and user account
- Exact product, publisher, edition and release/channel, with a verified official download or store listing
- Existing copies, vendor managers and relevant licenses, including whether a same-named app is already usable
- Supported installation method and destination, current-user versus machine-wide scope, required disk space and prerequisites
- Whether authority includes download, install, first launch and a small harmless output or demonstration
- One concrete function to verify, its approved input and output location
- Any expected account, payment, new agreement, restart, privileged helper or privacy-permission dependency

Ask only for a missing choice that changes the operation. If the app is already installed and satisfies the request, verify the relevant function instead of reinstalling it. If the request means upgrading or replacing an existing version, identify that changed scope before continuing; do not treat overwrite as a new installation.

When desktop access is unavailable, deliver a source-verified preparation result with the remaining owner action. Do not claim a successful local installation from a browser download response or from work on another computer.

## 1. Resolve source, artifact and installation identity

Follow the publisher's verified product page to its official distribution route, or use the operating system's official store. Check the listing's publisher and product identifier as well as its display name. A matching logo, high search rank or a sponsored download link does not establish identity. Do not choose a mirror, repackaged installer or similarly named product to bypass an unavailable official source.

Confirm the selected build supports the actual OS and architecture and includes the needed function. A free download may still require a paid plan, trial enrollment or activation. Preserve the user's edition/channel choice; do not pick a preview build or an emulated architecture merely because it downloads first. If a compatibility layer or runtime is required, identify it as an additional software dependency and obtain missing installation authority.

Record the official source URL, requested release and available artifact identity. For a standalone download, use the publisher's authenticated checksum/signature information when available, matching the exact artifact and architecture. A locally computed hash identifies bytes but does not establish their publisher. A valid signature or store presence is not proof that the app is harmless or meets the user's privacy requirements.

Inspect the downloaded item without executing it first. Distinguish an installer package, disk image, archive, application bundle, web shortcut and documentation file. Confirm the download completed and that the file type and publisher evidence fit the chosen route. Do not rename an unexpected executable to make it resemble the expected package, disable scanning, or run a browser's suggested “repair” tool.

Use current official instructions for the product and operating-system release. [Apple's external-app installation guide](https://support.apple.com/guide/mac-help/install-and-uninstall-other-apps-mh35835/mac) distinguishes opening a disk image or installer package. [Microsoft's online-install guidance](https://support.microsoft.com/en-au/windows/apps/how-to-install-programs-from-online-sources-on-windows) directs users to trusted sources. These are entry points; they do not authorize every linked workaround or every action in an installer.

## 2. Preserve the current state and choose the destination

Inspect the relevant native app inventory and intended destination. Record a compact baseline of matching existing versions and their actual locations. A shortcut may point to another drive or old copy; follow the target through supported inspection rather than judging by its name.

For a new application, choose the publisher-supported durable destination and requested user scope. An empty-looking destination can still be a linked path or shared/synced folder. Do not overwrite a same-named bundle, merge into an existing program folder or move a prior copy out of the way without resolving its ownership and preservation needs.

Save any work that must close before installation. If an installer wants to terminate another application, explain and resolve the interruption first; do not force-close it. A machine-wide installer can affect other users, shared components and future launches, so keep that scope visible. Do not switch from per-user to all-user installation just because the narrower route failed.

Keep user documents and libraries separate from application binaries. Do not use the only copy of an existing library for first-run acceptance if opening it could convert or migrate its format. Choose an original synthetic sample or an approved copy. If existing preferences or account state are discovered during first launch, preserve them and check whether this is actually a returning installation rather than a clean setup.

Review space on the actual target volume and the product's current requirements. If insufficient, report the prerequisite; do not delete downloads, caches, backups or an earlier version automatically. Do not promise a perfect rollback from keeping the installer alone: installation and first launch can modify settings or user data outside the program directory.

## 3. Apply approval at the actual installation boundary

A request to install the named reputable app from its official source covers its ordinary scoped installation. Preparation or comparison alone does not. Confirm an unapproved installer, source or additional component before execution; software from an unrecognized source requires its own action-time approval and is outside this ordinary official-source path.

Carry separate gates through both installer and first launch:

- Disclose and link a new explicit license or service agreement before accepting it, and obtain the required approval. Record an agreement actually accepted without copying account details
- Resolve payments, recurring plans and trial enrollment with their provider, total, billing commitment and relevant terms. Do not start a trial as a shortcut to acceptance
- Hand password, PIN, product-key or other protected credential entry and submission to the user through the supported secure route. Elevation does not authorize a broader installation
- Ask for unexpected app permissions. New persistent access to sensitive data or security-critical resources requires its specific action-time confirmation. Do not grant Full Disk Access, accessibility control, screen recording or account access merely to clear onboarding
- Treat account creation, sign-in, cloud synchronization, document upload and optional analytics submission as separate effects with their applicable authority. Never use private files as test inputs without the required data-sharing approval
- Resolve an unapproved restart, removal of another version, shared-component replacement or permanent data loss before proceeding. A new-app request does not authorize these effects automatically

Read every meaningful optional component choice. Leave unrelated browser integrations, search/default-handler changes, startup enrollment, promotional software and notification subscriptions unselected unless requested. Distinguish mandatory supported prerequisites from optional bundles. If a mandatory component conflicts with the approved scope, hold the install and explain that exact dependency.

Respect OS, browser and organization restrictions. Apple's [safe-opening guidance](https://support.apple.com/en-us/102445) distinguishes ordinary first-open confirmation from alerts about unverified, damaged or malicious software. Do not use “Open Anyway,” remove quarantine attributes, weaken Gatekeeper or bypass Windows protection to make this workflow finish. Preserve the precise alert and seek a supported source or owner decision; a documentation page describing an override is not permission to use it.

## 4. Install through one supported route

Recheck the target computer, source identity, destination, scope and selected components immediately before commitment. Use one installation operation. If a tool times out, inspect the existing installer/native inventory before repeating it; do not start concurrent installers.

### Official store route

Use the exact verified listing in the intended computer/account context. Follow the native acquisition/install control and observe its result. [Apple's App Store installation guide](https://support.apple.com/guide/app-store/install-and-uninstall-purchased-apps-fir0fb69db23/mac) and [Microsoft's Store guide](https://support.microsoft.com/en-us/accounts-billing/get-trusted-apps-and-games-from-microsoft-store) describe their supported routes. Their account and purchase relationships differ; do not assume an existing license belongs to the currently selected account.

Do not switch store accounts, enroll sharing, change region or authorize a purchase just to make an unavailable install button work. A cloud/library entry can establish entitlement or availability without proving that the app is installed on this machine. Read the local installation state after completion.

### macOS standalone route

Follow the actual publisher-provided package instructions. For a disk image containing an app intended for copying, inspect the destination and copy that exact bundle through the supported route before launching the installed copy. Do not interpret opening the image as installing it. A disk image can instead contain an installer package; use its documented process rather than dragging arbitrary contents into Applications.

For an installer package, inspect its destination, components, required privileges and final result. Do not approve an unexpected helper or system extension automatically. Record the resulting application location and version; a package receipt alone does not demonstrate successful use.

When an image was mounted for this task, quit any app still running from it normally, then eject only that verified installer image when safe. Do not force-eject a busy volume or remove a physical disk. Launch the installed bundle after ejection to eliminate dependence on the temporary source. Preserve the downloaded installer until any requested cleanup is separately authorized.

### Windows standalone route

Use the product's official installer and documented interactive choices. Verify the publisher shown by the system against the expected publisher before continuing; a display name alone is insufficient. Keep the selected installation scope and component choices consistent with the request.

Do not assume a downloaded EXE is a self-contained installer: it may retrieve additional components. Inspect the documented acquisition behavior and stop if the required source or payload materially changes. Avoid silent flags copied from an unrelated package, registry edits or manual extraction into Program Files as installation substitutes.

At completion, inspect the actual installed entry and destination through supported native/product controls. If restart is required, keep completion pending until an authorized restart and readback. Do not restart solely because an installer offers the option, and do not call a staged installation fully usable before its required activation step.

## 5. Verify the installed copy and one meaningful function

Open the app from its verified installed location or native installed entry. Avoid an old Dock/taskbar shortcut, recent-file association or installer “Launch” button until its target is known. Confirm the app's reported product/version against the selected release and the observed installed location.

Handle first-run screens without broadening scope. Decline optional enrollment or hold a mandatory unapproved dependency. A welcome window is not evidence that the requested function is usable. If a login or activation is essential, complete it only through the authorized secure flow and report its unresolved state honestly when blocked.

Use the agreed harmless activity. For a document editor, this might be creating a tiny original sample, saving it to an approved absent path, closing it and reopening that exact file from the new app. For a viewer, opening an approved sample and checking its expected rendering may be enough. For a converter, inspect both the saved result and its content rather than accepting a completion toast.

Keep checks proportionate and separate:

1. Acquisition came from the verified source and the intended artifact/edition was selected
2. Native readback establishes installation at the correct scope and durable location
3. Launch reaches that installed copy and reports the intended version
4. The requested function works on the approved input, with a meaningful inspected result
5. A normal quit/relaunch works independently of temporary installation media when relevant
6. Existing copies, documents and unrelated defaults remain preserved; any unverified dependency is explicit

Do not change default file associations merely to open a sample. Open it from within the selected app or use a one-time supported open action. Do not upload it to a service, connect a personal library or install optional plugins just to produce a stronger demonstration.

If the app upgrades itself during first launch, record the actual version and effects rather than reporting the download's version as final. Resolve any new terms, changed scope or compatibility concern before claiming the requested release was delivered. Do not change ongoing update policy as incidental cleanup.

## Recovery and stopping

- **Existing installation or destination collision:** stop the new-install route and resolve reuse, side-by-side support or a separately authorized upgrade. Do not overwrite silently
- **Unsupported architecture/release:** preserve the downloaded artifact and report the exact compatibility gap; do not install an unrelated build or weaken OS controls
- **Installer failed or disconnected:** inspect partial state and the native result before retrying. Retain a sanitized error; do not assume failure means no changes occurred
- **App launches from installer media or a stale shortcut:** quit normally, establish the actual installed target and relaunch it. Do not duplicate installation before resolving the path
- **Mandatory sign-in, permission or paid feature blocks the activity:** report installed-but-unverified state and the exact decision; do not enroll automatically
- **Requested output fails:** preserve the sample and original input, identify whether the cause is installation, first-run setup, unsupported feature or file handling, and correct only the authorized cause
- **The user wants reversal:** use the separately scoped supported removal route after checking new user data and shared components. Do not delete a program directory or clear every publisher preference folder

Restoring an app's binaries does not necessarily reverse a library migration, account grant or changed default. Preserve those distinctions in the recovery plan. Permanent data deletion remains an exact-target action-time decision. Do not upload logs or contact support without authorization.

Stop when the intended installed copy and agreed activity are verified, or at a precise missing prerequisite/approval. Keep a still-running native install pending until its outcome is established; do not abandon it because the progress bar is unchanged. Conversely, do not repeat a terminal failure without new evidence or broaden to whole-computer repair.

## Deliver a concise setup receipt

Return product/publisher, official source, actual installed version and location/account scope, accepted terms if any, relevant first-run choices and the verified activity. Include pending restart, activation or permissions and the supported removal/recovery route with its limits. Keep credentials, device serials and unrelated app inventories out of the receipt.

Distinguish prepared, downloaded, installed, first launch completed and function verified. A finished download cannot stand in for a usable application. Do not claim security certification, exhaustive compatibility or ongoing maintenance from this bounded check.

## Fictional, unexecuted illustration

A fictional user wants the invented “Meadow Sketch” drawing app on one Mac, with no account connection or default-handler change. Its official distribution is a disk image containing a copy-install app. A similarly named old bundle already exists in the shared Applications folder, and the downloaded image can launch a working window.

The proposed workflow pauses at the destination collision. It does not replace the old bundle or call the running image-installed window success. After a supported distinct destination is chosen with the required authority, the plan copies the intended app, verifies its version, quits any image-hosted instance and ejects only the installer image.

Expected acceptance is a launch from the durable destination, a tiny original drawing saved to a new approved path, normal quit/relaunch and reopening that drawing. If first launch demands a subscription to save, the result remains installed with the requested function blocked; a trial is not started. The original bundle and file associations remain unchanged.

This is an original fictional decision walkthrough. No software was downloaded or installed, image mounted, account accessed, permission granted, application launched or file created for this illustration.
