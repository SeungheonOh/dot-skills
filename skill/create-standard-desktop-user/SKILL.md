---
name: create-standard-desktop-user
description: "Create one standard local user on an existing personal Mac or Windows PC, preserve the original users and work, and verify the new account's identity, role and retained home/profile through a user-controlled sign-in. Use for a separate everyday desktop workspace, not cloud accounts, profile migration, child controls, remote access, administrator provisioning or security certification."
---

# Give another desktop user a workspace that persists

Deliver one deliberately created standard local OS account and a short sign-in/use handoff. Keep the account record, the loaded user session, the home/profile holding its files, its actual privileges and any disk-unlock capability distinct. A new name in the account list is not proof that a usable persistent workspace exists.

Use this for an additional everyday user on an already configured personal computer with an available authorized administrator. Do not use it to evade organization policy, repair a corrupted profile by replacement, recover a locked account, create a service identity, hide an account or turn a borrowed computer into an access route. It does not set up family monitoring or accounts for children. A separate standard user is not a virtual machine, a privacy guarantee against administrators or a safe place to run untrusted software.

[Mail-account setup](../add-desktop-mail-account/SKILL.md) connects a client to an existing mailbox. [Passkey enrollment](../enroll-account-passkey/SKILL.md) adds a credential to an existing service account. This workflow instead creates a persistent OS identity and its local working space. Use [device-handoff preparation](../prepare-device-handoff-record/SKILL.md) when the real task is transferring the whole computer rather than sharing its use.

## Establish the account contract

Resolve from the request and authorized settings:

- Exact computer, operating system/version and current local administrator; whether the device is personally controlled or managed
- Intended account owner, approved display name and local login name; distinguish a person's name from an email address or an existing cloud identity
- Whether the request covers preparation only, actual creation, or creation plus the bounded usability check below
- A persistent standard local account, with no cloud-account attachment or new remote-login permission
- One already installed ordinary application and local save location that will demonstrate the intended use
- Existing users, unsaved work and background activity that must survive; a workable route back to the original administrator
- Any essential accessibility/input needs at the sign-in screen, and the requested final session state

Ask only for a material missing choice. A request for another browser profile may not require an OS account. A request for a full computer wipe requires a different workflow. If a managed device or organization account controls local-user creation, stop at its established administrator route rather than applying the personal-computer procedure.

Use the selected computer through an authorized native interface. A cloud service connector or an account list from another machine cannot establish this computer's local state. The prospective user must be able to perform protected credential steps and, where required, take over at the local sign-in screen. If the available control session cannot survive user switching, arrange that supported handoff first; do not create extra remote-control access for the new account.

## 1. Check existing identities and exposure before creation

Inspect the native account list without opening other users' personal files. Distinguish ordinary local users, administrators, guest/built-in identities and any network or organization users. Reconcile a matching name with its type and account context. Never repurpose an existing account, reset its password or claim its home directory because its display name looks convenient.

If a prior setup may already have created the requested account, inspect that exact record and supported status before retrying. A folder with the desired name may belong to retained or migrated work. Leave it intact; do not attach a new user to it, rename it or delete it to clear a naming conflict. Choose a fresh approved local name if appropriate, without impersonating an existing user.

Keep a known administrator available. Do not demote the current administrator, enable a hidden built-in administrator, change automatic login or remove existing users. Record only enough non-secret account metadata to distinguish the new result later. Do not export the account database, password hashes, keychains or full user-directory contents.

Identify material access that account creation would confer through existing machine settings. Look at relevant sharing/group settings and owner-provided information, not a broad search through private documents. Public/shared folders, machine-wide services and already broad access rules can become available to another local user even when that user is standard. [Apple's local-sharing guidance](https://support.apple.com/en-ie/guide/mac-help/mchlp1122/27/mac/27) describes Public and Shared folders as readable by other local users under its documented defaults. Do not use those folders for a supposedly private probe or promise that every existing folder is inaccessible.

Where new-user exposure conflicts with the request, pause before creating the account. State the affected resource and access consequence privately. Changing permissions, relocating somebody else's files or disabling a service requires its own scoped decision; silently hardening the whole machine is not part of adding a user. If a privacy requirement depends on access that cannot be established, return that unresolved prerequisite rather than an isolation claim.

### Treat disk unlock as a separate capability

On a FileVault Mac, an account's ordinary login and its ability to unlock the startup disk are different questions. Account creation can itself affect this boundary. Apple's [earlier FileVault deployment guidance](https://support.apple.com/en-nz/guide/deployment/dep0a2cb7686/web) documents automatic secure-token grants when a secure-token-enabled administrator creates additional local users through Users & Groups. Its current [secure-token and volume-ownership reference](https://support.apple.com/guide/deployment/use-secure-and-bootstrap-tokens-dep24dbdcf9e/web) describes key creation at several account-lifecycle stages and explains that a standard user can also be a volume owner. Do not equate “not administrator” with “cannot unlock the disk” or promise that adding a user has no encryption-access effect.

Determine the relevant behavior for the actual Mac/version before confirmation. Include any resulting disk-unlock access in the creation decision. If the user requires a boundary that the supported creation route cannot establish, hold rather than scripting token suppression or editing authentication records. This guide does not turn encryption on/off, add/remove disk-unlock users separately, rotate recovery keys or modify startup security.

Keep encrypted-disk startup evidence separate from ordinary sign-in later. [Apple's FileVault user guide](https://support.apple.com/guide/mac-help/protect-data-on-your-mac-with-filevault-mh11785/mac) describes an Enable Users step where it is offered. A successful login after someone else unlocked the disk does not prove independent startup unlock. Do not restart merely to collect that evidence when the requested use only needs a local session.

## 2. Confirm the new access and leave secrets to the user

Creating a local account creates persistent access. Obtain action-time confirmation for the exact computer, intended person/local identity, standard role, relevant existing shared access and any established disk-unlock effect. A general request to make the computer easier to share or an already unlocked administrator session is not that confirmation. If actual capabilities differ from the approved contract, stop before creation.

Use a supported secure user handoff before entering or changing credentials. The administrator performs protected authorization; the new account owner controls the new password, verification, recovery answers and final credential-bearing submission. Do not invent a temporary password, choose blank credentials, send a password in chat, save it in a script, or use an assistant-controlled credential store. Keep password hints and security-question answers out of notes and screenshots too. No secret is needed in the setup report.

Do not add biometrics, a PIN, recovery contact, cloud account, synchronization, device-management enrollment or automatic sign-in as incidental setup. Each additional access or privacy choice needs its own applicable authority. If the native flow presents a new legal agreement, disclose the actual agreement through its verified link and follow the required acceptance rule. An unexpected security prompt is a decision boundary, not a button to accept to make progress.

If the credential owner is unavailable or secure handoff is unsupported, finish the non-secret proposal and precise next step. Do not create a usable account whose credentials will be handed over later through an unsafe channel.

## 3. Create one account through the native route

Match official instructions to the installed OS version. The references below were inspected on 2026-10-18; a changed label or unavailable control calls for current product guidance, not an alternate command-line provisioning method.

### macOS

[Apple's account-creation route](https://support.apple.com/guide/mac-help/add-a-user-or-group-mchl3e281fc9/mac) begins in System Settings → Users & Groups → Add User. Select Standard, reconcile the approved full name and account name, then hand the password and Create User step to the user. Sharing Only cannot provide an ordinary desktop login. Standard users may install apps and change their own settings; do not describe the role as an application-installation ban.

Check the local account name before submission. Apple's [new-user settings reference](https://support.apple.com/guide/mac-help/new-user-or-group-setup-mh15191/mac) connects that short name to the home-folder name and login. Treat later renaming as a separate coordinated operation, not a cosmetic correction. Do not edit an existing home-folder path or use Advanced Options as a shortcut.

After creation, reopen the exact user's details and verify that the account is Standard and the administration option is not enabled. Preserve the original users and automatic-login state. Do not turn on Apple Account password reset, Touch ID, file sharing or remote management merely because the page offers them.

### Windows

[Microsoft's account-management route](https://support.microsoft.com/en-us/windows/security/identity-signin/manage-user-accounts-in-windows) uses Settings → Accounts → Other users → Add account. For the deliberately selected local route, use “I don't have this person's sign-in information,” then “Add a user without a Microsoft account.” Keep the intended local username and have the user complete password/recovery fields and submission privately. Do not use Email & accounts or Access work or school as substitutes.

Reopen that account's supported account-type view and verify Standard User. Do not infer the role from a successful ordinary application launch, a missing shield icon or the presence of a UAC prompt. [Microsoft's UAC explanation](https://learn.microsoft.com/en-us/windows-server/security/user-account-control/how-user-account-control-works) distinguishes a standard account from an administrator running with a filtered token. Do not promote the user to make an app work, enable a built-in account or change UAC policy.

If the local route is unavailable under the installed configuration, stop at that supported-capability or policy gap. Do not use OOBE bypasses, registry edits, a different tenant or shell commands to evade it. This is an additional account on an existing installation, not initial Windows setup.

For either OS, an ambiguous timeout requires inspecting the same account list before another creation attempt. Record whether the account exists, its role is verified and its first session is still pending. Do not delete a partial result as automatic rollback.

## 4. Establish the new session and its actual home/profile

Save the original user's work before any planned sign-out. Prefer the existing supported user-switching route when it preserves needed work; do not enable new switching features or terminate another person's session merely for convenience. Apple's [fast-user-switching reference](https://support.apple.com/en-ie/guide/mac-help/mchlp2439/27/mac/27) describes concurrently logged-in accounts. Microsoft's [account-access guide](https://support.microsoft.com/en-us/accounts-billing/security/user-account-access-in-windows) distinguishes switching, locking and signing out. A switch or lock can leave the previous session running; it does not demonstrate that session ended.

At the native login screen, the intended user completes sign-in. Establish which computer and local account are now active before opening apps or typing content. A new wallpaper, familiar avatar or successful credential prompt is insufficient identity evidence by itself. If required, use the supported account view and the current user's home/profile location, collecting only these narrow non-secret facts.

Complete only ordinary first-use choices covered by the request. Hold cloud sign-in, restoring another profile, adding payment details, sharing diagnostics or granting permissions outside the existing scope. If an optional step can be skipped through the supported interface, use that route without claiming its feature is configured. A compulsory prerequisite that changes the contract must be raised explicitly.

Verify that the session is using a persistent home/profile belonging to the new account. Do not assume its disk path equals the display name. On Mac, [Apple's account-identity guidance](https://support.apple.com/en-gb/guide/mac-help/mchlp1520/mac) uses Finder → Go → Home to inspect the current home. On Windows, use the actual signed-in account and profile location, not another user's similarly named directory or a cloud shortcut in the sidebar.

Stop if Windows reports a temporary profile or cannot load the intended profile. [Microsoft warns](https://support.microsoft.com/en-us/windows/security/identity-signin/we-can-t-sign-in-to-your-account-error-message) that work created in a temporary profile can be lost at sign-out. Preserve any already-created work through an approved safe copy before ending that session. Do not proceed with the routine persistence check, disable security services or repair profile registry records under this setup task.

Open the agreed already-installed application without borrowing the administrator's app login, copying its profile or silently activating a license. Some apps may need their own supported setup or entitlement. Report that dependency; the solution is not promotion to administrator or importing the old user's browser, mail, cloud storage or credential data.

## 5. Verify useful work across a real session boundary

Agree on a harmless local acceptance item, such as a small uniquely named text file with an expected short sentence. Use a known location inside the new user's persistent home/profile, outside shared/public, removable, redirected or cloud-synchronized locations. If the actual destination cannot be established, stop the save rather than guessing from a generic Documents label.

When the requested check is authorized and observable:

1. Confirm the current account identity and saved Standard role without changing privileges
2. Create and save the agreed local item in the identified new-user location, then close and reopen it to verify the exact content
3. Save any other new-session work and perform a normal sign-out of this new account only
4. Have the user sign in to that same account again, establish the home/profile identity and reopen the same file
5. Read back the requested account state and finish in the agreed session: new account open, locked or signed out, or original account resumed

A lock/unlock or fast switch back to a still-running session is useful access evidence but does not satisfy the fresh-session persistence check. A copied file in a shared folder does not prove that the new account has a retained home. Reaching a login screen proves neither successful sign-in nor usable application access.

Do not test separation by trying to open another person's private files, approving elevation, executing an installer or modifying protected settings. Read the role and relevant access settings instead. If a stronger privacy/access assessment is required, it is a separately scoped task with specific resources and permissions, not an automatic acceptance probe.

Keep the evidence levels separate: created record, standard role observed, intended session observed, persistent home established, agreed app usable, saved work reopened after sign-out, and any independent startup-unlock check. Attribute user-reported observations when the protected screen cannot be seen. An unrun step remains unrun; a task limited to creation need not manufacture a broader test.

## Recover without replacing identities or losing work

- **Name collision or unexpected prior account:** preserve the account and home; resolve the intended identity before proceeding
- **Created account, first login unavailable:** keep the verified account record and report the exact credential, policy or local-handoff blocker; do not create another user
- **Wrong privilege or unexpected access:** stop ordinary use and identify the exact mismatch. Any correction needs its applicable security approval; do not silently alter unrelated memberships or security settings
- **Missing app or entitlement:** retain the functioning local session and distinguish that app prerequisite from failed account creation
- **Wrong or temporary home/profile:** preserve new work before any sign-out and stop profile-changing operations. Do not force a directory association or delete a profile to try again
- **Lost observation while switching:** re-establish the active account before sending input. Never repeat credential or account-creation actions blindly
- **New user absent from encrypted startup screen:** distinguish disk unlock from ordinary local login. Do not weaken encryption, reset a password or grant unlock access as an incidental fix

Deleting and recreating an account is not identity-preserving rollback. Microsoft's [SID reference](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-identifiers) explains that a new Windows account receives a different security identifier even when the name is reused. Existing ownership and access associations cannot be assumed to follow it. Account removal can also remove local data; preserve the result and obtain separate exact-target authority before any deletion. Do not remove the probe automatically if its ownership or recovery behavior is uncertain.

Stop when the requested setup and checks are accounted for, an unsupported prerequisite is established, or a user-controlled action/new permission is needed. A repeated identical login failure is not a reason to keep guessing. Do not reset credentials, reboot other users' sessions or broaden access to collect a successful check.

## Deliver the bounded result

Return a concise private record containing:

- Computer and intended local account, with display/login-name distinction where relevant
- Actual account type and observed home/profile location
- Creation, sign-in, application and fresh-session file evidence, separately marked observed, user-reported, unrun or blocked
- Relevant shared-access or disk-unlock scope and any unresolved requirement
- How to select the account, save work locally and return to the original user; distinguish switch, lock and sign-out
- Final active/session state, harmless probe location and any remaining exact action

Keep credentials, recovery answers, unrelated users' data and full security inventories out of the handoff. Acceptance requires the right new identity and Standard role, preserved original users/work, no unapproved access expansion, and evidence for the particular usability level requested. Do not call this a backup, profile migration, computer-security audit or proof of isolation from the machine's administrator.

## Fictional, unexecuted illustration

A fictional adult household member needs a persistent local Windows workspace for writing in an already-installed editor. The owner approves one Standard local account with a new login name; existing accounts, cloud services and shared-file settings must remain. A same-named folder already exists from earlier work.

The proposed workflow leaves that folder untouched, resolves a fresh approved login name and obtains the exact persistent-access confirmation. The user privately completes credential setup. After the new record appears, its type still needs readback, and its first login must establish the actual new profile. A paper observation reading “temporary profile” would stop the process before any routine sign-out, with any new work preserved through an approved copy.

If the correct persistent profile instead loads, a harmless local file could be saved, reopened, and checked again after normal sign-out and a new sign-in. A switch back to a session left running would not satisfy that last step. If the editor requested an administrator login, the proposal would retain the standard role and report the app dependency rather than escalating it.

This example is original, fictional and unexecuted. No computer, OS account, profile, credential, permission, application, file, login, sign-out or recovery procedure was accessed, created, changed or tested for the illustration. These are instructions for later authorized work, not reported validation.
