---
name: install-browser-extension
description: "Install or activate one selected desktop browser extension through its official marketplace, reconcile its initial and ongoing permissions with the intended browsing scope, and verify the requested feature. Use for a usable extension setup, not choosing products, developing extensions, bypassing browser policy or reviewing unrelated account grants."
---

# Make the selected browser extension usable at the intended scope

Deliver the identified extension in the intended browser context, with the requested feature demonstrated and a small record of its actual access and recovery route. Keep installation, enablement, site permission and successful use separate. A toolbar icon proves none of the other three.

This workflow covers an ordinary user-selected extension from the browser's official marketplace. It does not develop or sideload an extension, migrate a browser profile, deploy organization policy, or install password managers, wallet connectors, remote-control tools, security agents or network/VPN extensions. Those products need their own credential, security or system-integration workflow. A request to install an extension is not permission to let it process every page the user has open.

[Browser-profile diagnosis](../isolate-browser-profile-failures/SKILL.md) isolates an existing failure. [Connected-app access review](../review-connected-app-access/SKILL.md) examines account grants. [Desktop application removal](../uninstall-desktop-application/SKILL.md) handles a containing application's lifecycle. None replaces the extension-specific join between store identity, browser context, initial grants, ongoing site access and the feature the user needs.

## Establish the small setup contract

Resolve from the request and the current interface; ask only for a missing choice that changes the next action:

- The computer, browser family/version and intended profile or supported equivalent; identify whose browser is being used
- The selected extension, publisher and verified official listing, or enough information to resolve that exact listing
- The feature to make usable and a harmless example that demonstrates it
- Intended websites, normal versus private browsing, and any explicit restriction on page content, local files or external processing
- Existing installation/enablement, relevant sync or cross-device settings, and managed-browser restrictions
- Whether the request is preparation only, new installation or activation/configuration of an existing copy

Keep the browser's account/sync identity separate from accounts signed into websites and from any account the extension itself may request. A familiar profile label or avatar does not establish that they match. If the environment cannot expose enough current state to distinguish them, return a preparation result rather than guessing the destination.

Define an observable feature result, such as applying a selected reading layout to an approved public article. Avoid a success criterion that requires submitting private content, making a purchase, changing an account or sending a message. If the required feature inherently has those effects, identify the separate action and authorization before planning its demonstration.

## 1. Bind the request to a real extension

Reach the listing through the browser's official marketplace and, when needed, the publisher's verified product page. Resolve its browser-specific listing identifier, displayed publisher, supported browser and current listing/version evidence. Names, logos and search rank alone do not distinguish similarly named products. Keep a direct listing link in the receipt; do not substitute a sponsored download, repackaged file or forum attachment.

Read only what materially affects the requested setup: feature support, required permissions, relevant data-processing explanation, account or paid-plan dependency, and known browser/version limits. A marketplace listing is a distribution identity, not a security audit or a guarantee that every advertised feature is available. Do not install several alternatives to discover which one the user meant. Product selection remains a separate decision.

Inspect the native extension manager before installing. Distinguish these states:

| Current state | Bounded next step |
| --- | --- |
| Intended extension already enabled | Inspect its effective access and demonstrate the requested feature; do not reinstall |
| Intended extension installed but disabled | Establish why it is disabled and whether activation is authorized |
| Different publisher, edition or listing | Preserve its identity; resolve the intended product before adding or replacing anything |
| No matching installation | Continue with the exact official listing |
| Blocked, unsupported or organization-managed | Respect the restriction and return the precise supported owner action |

An extension disabled for a security or compatibility reason is not an ordinary unchecked box to fix. Do not enable obsolete packages, turn on developer mode, change experimental settings, edit a browser database, weaken signing checks or bypass a store/browser warning. Do not switch profiles, browsers or stores to evade an identified policy restriction.

Record a compact baseline: browser/profile, extension identity and state, relevant permissions, existing preferences needed for recovery and the intended sites. Inspect only the selected extension and relevant controls; a full browser inventory, history export or collection of other users' profiles is unnecessary.

## 2. Resolve what access is granted, and when

Read the actual installation or activation prompt before committing. Reconcile it with the requested feature and the supported post-install controls. Separate these layers rather than reducing everything to “website access”:

| Layer | Decision needed |
| --- | --- |
| Initial required permissions | What the browser grants at installation/activation, including any access before later settings can be changed |
| Site permissions | Exact sites or patterns, action-triggered versus continuing access, and what the browser actually lets this extension restrict |
| Other browser capabilities | Separately requested access such as tabs, bookmarks, downloads, clipboard or browser settings |
| Additional contexts | Private windows, local-file URLs, other profiles or devices, where applicable |
| Extension/service relationship | Any sign-in, account authorization, upload, cloud processing or continuing service connection |

Keep the browser's exact permission wording alongside a short practical explanation. Do not infer that a site control restricts unrelated browser capabilities, or that an extension runs locally because its button is in the browser. Use the publisher's relevant documentation for processing claims; label unknown behavior unknown. A promise in a product description is not observed proof of where data goes.

Resolve origin boundaries accurately. A single page, a host, its subdomains and a broad wildcard are different scopes. Use the browser's displayed effective pattern rather than assuming that entering one URL restricts access to that document. If the smallest supported boundary is wider than the user's requirement, hold that choice and explain the actual difference. Do not silently convert a single-site request into access to all sites.

Treat initial and final access separately. If installation necessarily grants broad page access before a later restriction can be applied, disclose that initial exposure and obtain the required exact approval first. “I will narrow it afterward” does not authorize the intervening grant. If the user does not accept the initial scope, stop before installation; do not claim that closing tabs makes a broad continuing grant narrow.

Check whether the initial operation could expose already-open work. Preserve unsaved drafts and pending operations before any necessary tab closure, reload or restart. Do not inspect private page contents merely to inventory risk, and do not close the user's windows without the needed authority. An approved harmless sample limits the demonstration's input; it does not by itself limit an extension's browser-wide privileges.

Read relevant sync/cross-device state without changing it. If the operation can affect contexts beyond the requested one, establish the supported boundary and the user's intended scope before proceeding. Do not enable sync, sign into a browser account or create an extra profile as an incidental setup step. If propagation cannot be bounded, report that limit rather than promising a local-only installation.

## 3. Apply permission gates at the actual boundary

A clear request to install the selected ordinary extension authorizes the scoped software-installation task. It does not remove separate confirmation requirements for persistent access, sensitive-data exposure, account security, payment or new terms. Reading the listing and preparing the setup plan may continue while an approval is pending.

- Before granting new persistent browser/account access or materially expanding it, obtain the required action-time confirmation for the exact extension, browser/profile, permissions, sites and material exposure. Bundle visible related grants where supported; do not obtain vague permission to accept whatever appears later.
- For an optional permission or new site request, compare it with the approved scope. Ask for missing authority at that point, and retain previously working scope while waiting. A runtime “Allow” button is not merely another installation screen.
- For data transmission, identify the actual data, recipient/service and purpose. Do not use private documents, clipboard contents, browsing history or authenticated account pages as convenient setup samples. Highly sensitive material remains a user handoff; never collect credentials or tokens in the receipt.
- Use the supported secure sign-in flow if a specifically authorized account step is needed. Hand off password or other credential entry and submission. Do not export sessions, save credentials or create an account to make a free feature work without the applicable request and approval.
- Resolve any purchase, subscription or explicit new agreement separately, with its provider, terms and cost. A free marketplace download does not establish that the requested feature is free. Do not accept a trial merely to complete the demonstration.
- Respect management denials and security warnings. Do not override them, grant broad disk access, install a native helper or change security settings as a workaround. A required helper is a new component with its own identity, effects and authorization.

Record approvals as scope, not secrets. Do not paste a sensitive permission screenshot or a private URL into a public report. If the exact requested access remains unclear, stop at that grant and ask the smallest necessary question.

## 4. Install and configure through the native route

Reconfirm the active browser context and selected listing immediately before commitment. Use one supported installation operation, inspect the result and then read the native extension manager. If a download or installation times out, inspect current state before retrying. Do not add a second copy or choose another listing because a success toast was missed.

Match labels and capabilities to the actual browser/version. These official references are entry points, not permission to follow every linked troubleshooting or override procedure:

### Chrome

[Google's extension guide](https://support.google.com/chrome/answer/2664769?hl=en) documents Chrome Web Store installation, native management and site-access choices. Installation is unavailable in guest or Incognito browsing. Where supported, use action-triggered access or an exact approved site list; inspect the actual control rather than relying on a remembered label. Pinning controls visibility, not enablement. Google's site-access controls affect matching host permissions and do not constrain lower-level VPN/proxy access; those extensions are excluded here. Leave private-browsing access unchanged unless specifically required and authorized.

### Firefox

Use the official [Firefox add-on installation route](https://support.mozilla.org/en-US/kb/find-and-install-add-ons-add-features-to-firefox) and the full Add-ons Manager for readback. The toolbar panel is not a complete installation inventory: pinned and disabled extensions can be absent. Mozilla's [extensions-button guide](https://support.mozilla.org/en-US/kb/extensions-button) identifies its per-site permission controls as applying to Manifest V3 extensions. Do not promise those controls for every installed add-on.

Inspect required versus [optional permissions](https://support.mozilla.org/en-US/kb/manage-optional-permissions-extensions) separately; optional grants can be requested later. [Private-window permission](https://support.mozilla.org/en-US/kb/extensions-private-browsing) is also a separate context. Keep unrequested optional and private access ungranted. If a site is [restricted by Mozilla](https://support.mozilla.org/en-US/kb/quarantined-domains), preserve that restriction; do not use the documentation's override route to finish this task.

### Safari on Mac

[Apple's extension guide](https://support.apple.com/guide/safari/get-extensions-sfri32508/mac) routes marketplace discovery through Safari Extensions and manages installed extensions in Safari Settings. Distinguish obtaining a containing app, enabling its extension and granting website access. Consult [Extensions settings](https://support.apple.com/guide/safari/sfri32153/mac) for the actual installation and cross-device state; an extension listed on another device is not evidence that it is installed on this Mac. Do not turn on cross-device sharing as part of a one-computer request.

Safari removal may involve the containing app. If that app supplies other functions or extensions, prefer a specifically authorized extension disablement when suitable; do not delete the whole app to reverse one feature without resolving the broader scope. Establish profile-specific behavior from the actual version before promising profile isolation.

### Finish the bounded setup

Apply only approved settings needed for the feature. Leave unrelated search, homepage, notification, telemetry, data-sharing and account choices unchanged or decline optional enrollment. If the product makes an unapproved choice mandatory, hold that dependency. Do not install a companion program or another extension merely because an onboarding page recommends it.

Read back the resulting identity/version, enablement, required and optional permissions, actual site scope and private/local-file settings where present. Record any control the browser does not expose. A missing toggle is not evidence of no access. Do not read extension databases or token storage to fill a gap.

If a requested toolbar pin or simple ordinary preference makes the feature usable, apply it within the task's authority. Do not treat pinning as activation or an absent icon as an installation failure. Keep all unrelated pre-existing extensions and their state untouched.

## 5. Demonstrate the requested feature without expanding access

Use an approved harmless page in the intended normal/private context, matching the actual site scope. Prefer public non-sensitive content or a supported local synthetic sample only when local-file access is already authorized; do not grant file access just to manufacture a test. Check that the page belongs to the intended site after redirects. Browser-internal, store or protected pages may not be eligible demonstration targets.

1. Establish the page's relevant baseline and expected result. Avoid account-changing controls and preserve any real work before a reload.
2. Invoke the extension in its documented way. For action-triggered access, distinguish clicking its button from granting continuing site permission. Inspect any new prompt before accepting it.
3. Observe the actual requested feature, not merely the popup opening. For an export feature, check the specifically authorized saved output; for an on-page feature, inspect the changed page and required interactions. A different feature succeeding is not completion.
4. Reopen or reload only the harmless sample as needed to establish the promised behavior. If use is action-triggered, explain any required repeat invocation; do not convert it to automatic access just to avoid an extra click.
5. Read back the final scope after the demonstration. When the user required exclusion from another context/site, inspect its native permission state. A harmless second-page check can supplement that evidence if authorized and meaningful, but an unchanged page does not prove that the extension had no access or performed no background work.
6. Leave only the intended final configuration. Close disposable sample tabs only when safe, preserve any requested output, and list any newly installed but disabled component or other remaining state.

Separate **installed**, **enabled**, **configured at the agreed scope**, and **feature observed**. A permission screen establishes configuration, not the absence of data collection. A successful public-page demonstration does not prove private-account compatibility, behavior on every website, or future permission/update behavior. Record the browser and extension version observed; do not disable updates or promise that the permission state can never change.

If the feature requires an unapproved account, paid plan, native helper or additional grant, stop that dependency and return the usable setup evidence plus the exact missing decision. Do not call the feature verified. For a preparation-only task, no installation or live demonstration is necessary; clearly label all such checks pending.

## Failure handling and reversal

- **Installed but unavailable in the expected window:** recheck browser/profile, normal/private context, enablement and actual site permission. Do not reinstall before resolving identity.
- **Works on the sample but not the target:** compare page eligibility, redirects, supported feature and account requirements. Do not broaden to every site or remove a browser restriction as a diagnostic shortcut.
- **A permission is denied or unavailable:** preserve the denial and the scope that remains usable. Offer the specific narrower supported operation or report the blocker; never search for a route around the restriction.
- **The extension reports an error or a page breaks:** preserve current work, stop repeated invocation and use the authorized narrow disablement/recovery. A separate controlled profile diagnosis may be appropriate, but disabling other extensions is not part of this setup by default.
- **Installation/activation outcome is uncertain:** reread the exact native entry and relevant prompts. Report partial or unknown state rather than treating an error as proof nothing changed.
- **The user wants reversal:** first identify the exact new installation or settings change and any user-created extension data. Restore recorded prior settings only with the required authority; reverting to a broader previous grant can itself expand access. Disable or remove only the approved target through its supported control. Do not clear all browser data or delete a profile.

Before removal, resolve any loss of extension-local notes, rules, saved work or settings. Keep a supported authorized export when required; do not assume reinstalling recreates them. Irrecoverable user-data deletion retains its separate action-time gate. Reinstallation, renewed permission grants and account reconnection are not automatic rollback steps.

Read back disablement/removal and recheck the harmless page when appropriate. Existing page changes or externally saved output may require their own recovery; do not promise that uninstalling undoes them. Likewise, removing an extension does not prove deletion of data previously sent to its service, revoke every independent account grant, or cancel its subscription. Do not trigger those separate actions without authority.

## Acceptance and handoff

A completed setup requires the exact intended extension in the intended browser context, native readback of the agreed access, an observed result for the requested feature, and no unresolved required setup dependency. Report a partial installation, configuration-only result or blocked demonstration honestly.

Return a short private receipt:

- Extension/publisher and official listing; observed version and browser context
- Installed or already present; enabled state; actual site and additional-context access
- What feature was observed, on what harmless input, and what remains untested
- Any additional account/service relationship actually created, with no credentials
- Exact reversal route, preservation needs and material limits
- Any pending decision, disabled component or uncertain outcome

Save a receipt or sample only when requested or useful at an approved destination, then read it back. Do not publish private browsing details, submit a review, report the publisher, contact support or enable ongoing monitoring just to finish setup.

## Fictional, unexecuted illustration

A fictional user wants the invented “Page Margin Helper” extension in their Work browser profile, solely to make public reference articles easier to read on docs.example. The listing identity is assumed known for this illustration. The user has not authorized other websites, private windows or cloud processing.

Suppose its install prompt requires continuing access to every website, while a later settings page offers a single-site control. The proposed workflow stops before installation and explains the initial broad grant. It does not install first and call the later restriction sufficient. If the user declines that initial access, the result is a held setup with the exact reason; no alternative product is installed silently.

Alternatively, suppose the native route allows the approved limited grant and the required action-time confirmation is supplied. The proposed demonstration would open a harmless article on the approved host, invoke the feature and inspect its layout. A hidden toolbar icon would not justify reinstalling the extension. A later request for private-window access would remain unapproved, and a successful layout change would not establish that the extension never communicates with a service.

Every name, site, prompt and result above is invented. No browser, extension, account, permission, page or recovery action was operated for this illustration; it is an authored decision example, not an executed test.
