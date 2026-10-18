---
name: configure-separate-browser-profile
description: "Set up one retained local Chrome profile for a bounded everyday browsing workflow, preserve the original context, and verify profile selection, permitted retained state and return navigation. Use for continuing work/personal or multi-account context separation, not troubleshooting, browser migration, managed enrollment or security isolation."
---

# Establish a browser context the user can return to

Deliver one deliberately identified, retained browser profile with a usable selection route and evidence that the agreed browsing state survives closing and reopening its window. Preserve the original profile and its live work. A differently colored window, an account avatar or a newly opened tab is not the complete result.

This guide's implementation is an additional local profile in already-installed desktop Chrome, without browser-account attachment or import. It can include specifically requested website access through the normal protected sign-in route. It does not create a new website account, provision an employer identity or configure browser sync. If a different browser is requested, establish its actual separation and propagation behavior before proposing an equivalent; do not silently switch products.

## Choose this outcome rather than an adjacent task

[Profile-failure diagnosis](../isolate-browser-profile-failures/SKILL.md) may create a fresh profile as a comparison control. Its result is an explanation of a failure; this guide instead owns the new profile's continuing purpose, retained state, selection instructions and preservation of the old context. Do not replace a failing profile to avoid diagnosing it.

Use [bookmark migration](../bookmark-migration-rehearsal/SKILL.md) for moving a collection, [tab-workspace recovery](../recover-browser-tab-workspace/SKILL.md) for lost browsing, [desktop-link routing](../trace-desktop-link-routing/SKILL.md) for links opened by other apps, and [extension setup](../install-browser-extension/SKILL.md) for adding an extension. None is an automatic part of this setup. [Virtual desktops](../organize-virtual-desktop-workspaces/SKILL.md) organize windows rather than browser data. [A separate OS user](../create-standard-desktop-user/SKILL.md) is a different access decision when another person needs their own computer login.

Profiles help the same person keep contexts distinct; they are not a security boundary against someone using that OS session. Google explicitly warns that someone with device access can switch Chrome profiles. Do not promise anonymity, protection from administrators, separate network identity, separate filesystem permissions or invisibility during screen sharing. Downloaded files and system resources remain subject to the computer's existing access rules.

## 1. Establish the retained-use contract

Resolve from the request and visible settings, asking only for a missing material choice:

- The authorized computer, installed browser/version and current OS session; identify whose browser will be operated
- Intended purpose and a distinct non-sensitive profile label, such as Research or Client Work
- Existing profiles and whether a suitable one already exists; distinguish a requested new profile from resuming an existing one
- Browser-account identity and account-saving/sync state, separately from the account and workspace inside each required website
- The requested final state: preparation only, local profile ready, or profile ready with named website access
- One harmless useful page and retained item to check, such as an approved public reference bookmark in the new profile
- Original windows, unsaved forms, calls, downloads and other work that must remain; a safe time to close only the new window for the check

Do not inspect unrelated browsing history or other people's accounts to fill out a checklist. A same-named existing profile is a collision to resolve, not an empty slot to overwrite. If a prior attempt may have succeeded, inspect the native profile list before creating anything again.

If the real requirement is that another person cannot see the user's browsing, explain that a browser profile does not meet it. Pause setup until the intended access boundary is resolved. Do not create an OS account or change computer security as an incidental substitute.

Use the authorized computer's supported browser interface. A cloud-browser session or connector account elsewhere cannot establish local profile state on this computer. If the actual profile controls are inaccessible, deliver preparation and the precise missing capability; do not claim creation or persistence from instructions alone.

## 2. Resolve sharing and permissions before creating state

Inspect the relevant browser UI for management indicators and available local-profile creation. A new local profile does not exempt the device or browser from organization policy. If the route requires managed sign-in, enrollment, a locked setting or a policy override, hold it for the responsible administrator. Do not remove policies, disable security extensions or use a different browser to evade a restriction.

### Keep Chrome sign-in and data saving distinct

[Google's profile documentation](https://support.google.com/chrome/answer/2364824?hl=en) describes native creation, selection and removal. [Chrome sign-in guidance](https://support.google.com/chrome/answer/185277) distinguishes a Google website login from optional sign-in to Chrome. A site login prompt is not permission to attach the browser to that account.

[Google's account-data guidance](https://support.google.com/chrome/answer/165139) explains that signed-in Chrome can save information in the Google Account, with history/tab controls separate from other categories. Do not equate a visible “sync off” label with a guarantee that all browsing information stays local. Read the actual account-saving state. Local-profile setup here leaves browser-account sign-in, account uploads, import and sync unrequested and unperformed.

Local browser storage is not a promise of no network activity: visiting a website contacts that service, and existing OS services, policies or tools may still apply. If the user's requirement is stronger than the controls can establish, state the gap before collecting real work in the profile.

### Do not generalize this route to Safari

[Apple's Safari profile guidance](https://support.apple.com/en-us/105100) documents separate history and website data but shared bookmarks, AutoFill/password information and several settings. A separate Favorites folder changes presentation, not bookmark access. Existing Safari-in-iCloud use can automatically propagate profiles among eligible devices on the same Apple Account. Initial profile creation also assigns existing browsing to a default profile.

Therefore this Chrome-local route is not a local-only Safari recipe. For a Safari request, first inspect the version, existing iCloud state and required separation. Explain the relevant shared data and propagation before creation and obtain missing data-sharing authority. If local-only operation or separate credentials are essential, leave the request blocked unless a supported, authorized arrangement meets it. Do not disable iCloud, sign out of the Apple Account or alter shared password access as a shortcut. Safari execution needs a separately established product-specific plan; this guide does not claim to implement it.

### Apply the exact action boundaries

A clear request to create this local profile authorizes the ordinary native profile creation and requested identifying preferences. Advice or diagnosis alone does not. An empty local browsing context is distinct from establishing ongoing access to an account.

- Website sign-in needs approval for that service and intended account; use the supported secure login route and leave credential entry and submission to the user where handoff is required. Never copy cookies, tokens, passwords or an existing profile directory to avoid sign-in.
- A new OAuth grant, remembered service connection or other creation/material expansion of persistent access needs action-time confirmation identifying the service, account, granted scope and exposure. A general request to separate work browsing does not approve it.
- Browser-account attachment and changes that expose data to a service or other devices are outside the local-only contract. Before separately proceeding, identify the specific account, data categories, receiving service, relevant propagation and applicable persistent-access confirmation. Do not click an import/save-in-account/enable-sync prompt first and explain afterward.
- Transmitting personal information requires the specific data, recipient and purpose to be authorized. Use a non-sensitive public page for the setup check; do not make private content a demonstration sample. Credentials and other highly sensitive values require the protected handoff, never a chat request or receipt.
- Unexpected permissions, CAPTCHA, new terms and security warnings retain their own approval or handoff requirements. Never accept them merely to finish setup. Do not save credentials or payment information as a convenience.

Keep names, captures and handoff notes minimal. A profile name may appear in screenshots or account interfaces; do not embed confidential client details in it. If the screen is being shared, resolve exposure before revealing profile/account menus.

## 3. Create one context without importing the old one

Match the visible interface to current official documentation for the installed version. The linked Google and Apple pages were inspected on 2026-10-18; product labels can change.

1. Identify the current original profile and a reliable route back to its existing window. Preserve that window without closing, reloading or signing it out. Do not export the user's history or credentials as a supposed backup.
2. In Chrome's profile menu, use Add Chrome profile. Choose the available route that continues without Chrome account sign-in. If that route is absent or a required prompt changes the agreed scope, stop before committing further.
3. Use the approved unique name and a readily distinguishable native color/icon. Decline optional import, browser-account attachment and extra components. Do not modify the original profile's name or startup behavior to make the new one look primary.
4. Read back the new native profile entry and its active-window identity. Inspect its browser-account state rather than assuming the skipped invitation proves the final state. Check visible management indicators; unexpected enforced settings remain in place.
5. Open only the agreed harmless page and save the agreed small retained item in this profile through the native interface. Record its safe label and location. Do not import a collection, copy private tabs or configure a download folder merely to populate the profile.

A label is a navigation aid, not proof of a distinct website identity. Before entering any requested service, establish both the active browser profile and the website's actual account/workspace. If sign-in is requested, complete only that authorized step, then inspect the site's account indicator without exposing secrets. Decline an optional browser-sign-in offer. If SSO, a managed redirect or an existing grant selects the wrong account, stop before changing or submitting content; do not sign the original profile out to force a different result.

After a timeout, re-read the profile list and active window before retrying. Retain a partially created profile and report its state; duplicate creation is not recovery.

## 4. Verify selection, retention and return

The direct selection route is the browser's native profile menu, not a generic taskbar/Dock browser icon and not a link from another app. Verify the route the user can deliberately repeat. Do not create launcher scripts or alter OS defaults. A requested desktop shortcut or external-app routing rule is a separate scoped addition.

For the agreed local-profile acceptance check:

1. In the new profile, read its identity and open the harmless retained item. Confirm its expected page rather than a similarly titled error or sign-in page.
2. Safely close only this new profile's test window after ensuring it holds no unsaved work or active operation. Do not use Quit, kill processes, close the original window or restart the computer.
3. From the remaining browser's native profile menu, deliberately select the new profile again. Confirm the new window belongs to that same entry, then locate and open the retained item.
4. Return to the original profile's existing window. Confirm its identity and continued presence of the relevant work without reloading forms or inspecting unrelated private content.
5. Return once more to the new profile if that is the requested final state. Read back browser-account status and account-saving state, and account for any pending sign-in or permission prompt.

Closing and reopening a profile window verifies that window-selection path and observed retained state. Chrome may keep processes running; this check does not prove survival across a full browser restart, OS restart, profile deletion or device loss. Do not call it a backup. If a stronger restart check is explicitly required, arrange preservation and authority separately; otherwise report it as unrun.

For requested authenticated use, inspect the named website account/workspace after reopening and make one harmless read-only check of the intended feature. A public page proves neither authentication nor account separation. If the site requests sign-in again, report that observed behavior and the remaining requirement; do not weaken security or promise permanent login retention. Do not inspect raw storage to prove which cookie persisted.

## 5. Recover and leave an honest handoff

- **Wrong window selected:** stop input, identify the actual profile and return through the native selector. Do not move the user's tabs between profiles to conceal the mistake.
- **Retained item missing:** check profile identity, its native saved-item location and whether saving was observed. Do not import the old collection, repeat setup blindly or enable sync as repair.
- **Unexpected browser-account attachment or propagation:** stop new input and identify what actually changed. Explain potential exposure without claiming deletion or sign-out can retract it. Obtain the applicable authority for a narrowly scoped correction; preserve original sessions.
- **Original work appears missing:** inspect existing windows/minimized state first. Do not relaunch repeatedly or create a replacement profile. Use the recovery workflow if work was actually closed.
- **Unsupported policy, login or access dependency:** preserve the partial result and report the exact next decision or owner action. A usable local profile can be complete while optional website access remains pending, but cannot complete a request that required that access.

The new profile is meant to remain. Do not delete it as cleanup, even if verification is blocked. Profile removal can erase local data; browser-account removal and server-side data deletion have different consequences. Any later removal needs exact-target authority, preservation of new work and action-time confirmation for irreversible deletion. Never clear all browsing data or delete the original profile to reverse this setup.

Return a short private handoff:

- Computer/browser and new profile label; purpose and direct native selection route
- Local profile created or reused, actual browser-account state, and website identity/access only if checked
- Retained item and precise close/reopen evidence; stronger persistence checks unrun
- Original context return check and any work left pending
- Shared-data/propagation limits relevant to the actual product and state
- Final open context, remaining partial state and smallest next action

Completion means the requested context is deliberately selectable, its permitted retained state passed the agreed check, original work remains available, and every required website-access check passed. If required access is pending, report partial completion. Preparation, profile creation, website access and persistence evidence are separate statuses. No screenshot or private URL is required merely to prove work happened.

## Fictional illustration, unexecuted

A fictional user asks for a local Chrome Research profile with one public reference bookmark, leaving their current Personal window and unsaved form untouched. They do not request browser sign-in, imports or website credentials.

The proposed workflow would inspect whether Research already exists, create it only if needed through the unsigned-in native route, save the agreed reference bookmark, and close only its harmless new window. Reopening Research through the profile selector and finding that bookmark would establish the stated retention check. Returning to the still-open Personal window would check continuity without reloading its form. A generic browser icon opening Personal would not invalidate the direct-selection result or justify changing defaults.

If the new profile instead requires employer enrollment, the proposed result is a held setup with that prerequisite. If the bookmark is present but a separately requested website login remains blocked, the handoff would distinguish local readiness from the unfinished authenticated workflow. Neither case justifies deleting the partial profile.

This is an original decision illustration, not observed evidence. No browser, computer, profile, bookmark, account, credential, setting, session or recovery action was operated for this example. No execution or test result is claimed.
