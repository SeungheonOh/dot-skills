---
name: add-desktop-mail-account
description: "Connect an existing personal or work mailbox to a chosen desktop mail client, preserving account identity, synchronization scope and existing local work, then verify native access and clearly bounded sending evidence. Use for client-side account setup, not creating mailboxes, migration, delegation, forwarding or organization-wide authentication changes."
---

# Add an existing mailbox without losing its boundaries

Deliver a usable account connection in the requested desktop client, with a short private setup record explaining what is connected, where data can reside, what was checked and what remains pending. Keep successful sign-in, saved account configuration, readable mail, complete synchronization and outbound delivery separate.

Use [mailbox delegation](../configure-mailbox-delegation/SKILL.md) for another person's access, [tool-switch planning](../plan-tool-switch/SKILL.md) for a broader migration, and [email-delivery tracing](../trace-email-delivery/SKILL.md) for a particular missing message. Adding an account gives the client a route to an existing service; it does not transfer local archives, create an address, configure an alias, import contacts or replace the user's other clients.

## Establish the account, client and intended use

Recover from the request and authorized settings:

- Exact computer, OS user, installed mail application and version; distinguish new and classic Outlook, and separate application profiles
- Existing mailbox's full address, actual provider and personal/work/school boundary; distinguish sign-in identity, primary mailbox, alias and shared mailbox
- Whether the account is absent, already present but disabled, partially configured or connected through the OS account store
- Mail-only use or explicitly requested calendar/contact integration; any required server folders, historical mail or offline availability
- Whether the result is a setup proposal, a configured client, or working send/receive with a specifically approved exchange
- Existing accounts, default sender, local-only data, drafts and queued outbound work that must remain intact

Do not assume the domain after the @ sign identifies the hosting service. A custom domain can use a separate authentication provider. Resolve an uncertain provider through trusted account records or its official setup guidance before submitting the address or credentials anywhere. An address selected from a suggestion is still a target to verify.

Use the user's chosen client and authorized environment. A mailbox-reading connector can establish source evidence but does not prove that the desktop app is configured. If native access is unavailable, deliver the supported setup path and precise missing capability; do not substitute webmail and report the desktop task complete. App installation, paid licensing and switching products are separate decisions.

Inspect the account list before opening an add-account wizard. An account already configured through Internet Accounts or another app may need an existing Mail switch rather than a duplicate record. A shared mailbox normally uses its established delegation route, not a new direct login with the shared address. An alias is not automatically a separate authenticatable mailbox.

Keep the preparation compact. One account normally needs a few before/after settings and a bounded check record, not an export of the whole mailbox or every device's configuration.

## Choose the supported connection and its data boundary

Read the current official guidance for the actual client, provider and account type. Provider-specific sign-in, Exchange and manually configured IMAP are not interchangeable labels. Preserve native capabilities the request needs; do not select a generic protocol merely because its form is easier to fill.

Prefer the provider's supported modern sign-in route when available. For Gmail, [Google's current client guidance](https://support.google.com/mail/answer/7126229?hl=en) directs users to Sign in with Google. Personal Gmail no longer has an enable/disable IMAP switch. Do not send the user searching for that obsolete control or apply the personal-account statement to an organization's policy. A managed account can require its administrator's approved route; denial is a blocker, not a reason to choose another protocol or tenant.

For a manual setup, obtain incoming and outgoing server names, account type, port, encryption and authentication requirements from the actual provider or verified administrator instructions. Keep the non-secret values in the setup record. Do not invent hostnames from the email domain, copy settings from a different provider or weaken TLS to make a connection succeed. Incoming access and the outgoing sending service need their own supported bindings.

Do not silently fall back to POP. Microsoft's [POP retention guidance](https://support.microsoft.com/en-us/outlook/read-pop3-email-messages-on-multiple-computers) documents that retrieval can remove server copies depending on the client's settings. A request to add the same mailbox on another device does not authorize moving its only copy there. If POP is explicitly required, resolve server-retention behavior, local storage and the effect on other clients before the first retrieval; otherwise keep that route on hold. Changing an existing POP account to a different protocol is a migration with local-data questions, not a safe in-place toggle.

Determine the actual processing path before enabling access:

- Which client or OS account service receives authority, and whether it is device-specific or reused across apps
- What information and capabilities the consent screen includes: historical and future mail, attachments, sending, modification/deletion, calendar or contacts
- Whether the client connects to the provider directly or synchronizes account data through an additional vendor's cloud
- Which local caches, attachment downloads and date/folder limits are configurable, and what the requested offline behavior requires

For example, [Microsoft's cloud-sync description](https://support.microsoft.com/en-us/outlook/getstarted/sync-your-account-in-outlook-to-the-microsoft-cloud) states that supported non-Microsoft Outlook connections can synchronize copies of email, calendar and contacts with Microsoft data centers. Check the actual account/client combination and consent screen. Do not describe this as local-only access, infer that hiding Calendar prevents its data being transferred, or silently broaden a mail-only request to a bundled data set. If the chosen route cannot meet a material boundary, expose that choice before continuing.

A mail client's write/send permissions may be broader than the user's intended reading activity. A promise not to click Delete is not a read-only grant. Identify that difference and obtain the required decision rather than labeling the setup read-only.

## Confirm access before completing sign-in

Creating or materially expanding persistent account access requires action-time confirmation, even when the user requested account setup. State the exact mailbox, client/device, real capabilities and information exposed, any additional cloud recipient, and the intended continuing sign-in. Resolve any missing permission to retain authentication information in that specific app. A general permission to help with email does not approve a new app grant.

Keep passwords, app passwords, tokens, recovery material and security answers out of chat, screenshots and artifacts. Use the supported secure authentication flow or user handoff; hand credential entry to the user wherever required. Never retrieve saved credentials, inspect a token cache or put secrets into a configuration file. A remembered browser session does not establish that the right account is selected: verify the identity before consent.

If the provider requires an app password or new credential, stop for its separate access-creation approval and secure user-controlled entry rather than generating or copying it as routine troubleshooting. Do not disable multifactor authentication, enable legacy sign-in, bypass a certificate warning or grant administrator access. A client asking for device registration, organization management or an unexpected permission presents a new security decision; do not accept it incidentally.

Disclose any newly presented agreement through its official link before the acceptance step and follow the applicable approval or handoff requirement. After an authorized new acceptance, report it with the link. A setup guide does not itself authorize legal acceptance, new subscriptions or account creation.

Before bringing an existing partial account online, inspect for pending outbox work and other relevant automatic effects through the supported interface. Reconnection can resume work that the user did not ask to send now. Do not send, cancel, delete or edit a queued message to clear the setup path. Resolve that specific dependency first.

Likewise, inspect a wizard's test options before committing. An automatic test message is an external communication, not merely validation of text fields. Obtain any missing sender, recipient and purpose authority before a step that sends it. A separate greeting, real reply or test to a colleague is never implied by account setup.

## Add or enable the exact account

The following official routes were inspected on 2026-10-17. Match the installed version's documentation and actual controls; do not force a remembered click sequence onto a different product.

### Apple Mail on Mac

[Apple's account guide](https://support.apple.com/guide/mail/add-and-manage-email-accounts-mail35803/mac) uses Mail → Add Account for a new connection. When the account already exists in Internet Accounts, inspect that exact record and its Mail service instead of creating a duplicate. Preserve existing Calendar, Contacts, Notes and other service selections; for a newly added account, enable only the approved services the interface can actually separate.

Use [Apple's provider-selection guidance](https://support.apple.com/en-us/102088) when the account type is unclear. Its provider choices can differ between Mac and mobile devices; for example, Outlook.com addresses use Microsoft Exchange on Mac. Do not copy an iPhone choice into a Mac setup. A provider choice that was wrong may require removing a partial account, but only after the removal safeguards below establish what would be lost.

Complete the confirmed sign-in and service selection. Reopen Mail → Settings → Accounts and verify the selected account's address, enabled state and supported account information. Inspect its own mailbox subtree rather than a unified All Inboxes view that may show messages from a different account.

### Outlook for Windows

[Microsoft's account instructions](https://support.microsoft.com/en-us/outlook/getstarted/add-an-email-account-to-outlook-for-windows) distinguish new Outlook's Settings → Accounts → Your accounts → Add Account from classic Outlook's File → Add Account. Use the chosen profile and exact address. Complete only the confirmed provider sign-in and permitted synchronization route.

Keep adding an account separate from making it primary, changing the default sender or importing another client's settings. Preserve those values unless requested. A familiar account suggestion or successful Microsoft sign-in is not evidence that the desired mailbox has been added.

For modern authentication in classic Outlook, use its built-in account flow. Microsoft's [profile documentation](https://support.microsoft.com/en-us/outlook/edit-an-outlook-profile) says the Control Panel Mail applet cannot add accounts that require modern authentication. Do not use that older route as an authentication workaround or switch profiles while unsaved work could be lost.

For another already-selected desktop client, apply the same identity, access and preservation gates using that client's current official documentation. Do not claim these menu paths apply to it.

## Reconcile synchronization and special folders

Once authorization is complete, inspect the saved account and its initial progress. Record any loading, offline, authentication, policy or quota state. A successful sign-in can precede message synchronization, while an old cached inbox can remain visible after access fails.

Check a small representative set tied to the user's need: one identifiable recent message, one older message if history matters, and a required folder or label. Use already-authorized server/webmail evidence or a user-supplied known message to distinguish an empty source from an incomplete client. Record account, folder and available message identity; similar subjects or conversation totals are insufficient. Do not download every attachment or export headers simply to prove the connection.

Reconcile mismatches before changing data. Date-limited caching, folder subscription, filtering, conversation grouping and provider label semantics can make client counts differ. A message appearing under two labels is not a duplicate to delete. Missing mail in a partial local view is not a reason to import a second copy. If the server record is absent too, this becomes a delivery or source-history question rather than client setup.

Inspect the account's mappings for Drafts, Sent, Archive, Junk and Trash where exposed. Verify that requested cross-device work targets the correct account's supported server folders rather than a similarly named folder in another account or a local-only store. [Apple's Mailbox Behaviors reference](https://support.apple.com/guide/mail/change-mailbox-behaviors-settings-cpmlprefacctmbox/mac) distinguishes server mailboxes from On My Mac storage and warns that deletion/erasure choices have separate effects. Follow provider-specific mappings; do not create new special folders, move old mail or enable automatic purging to tidy the sidebar.

Check who creates sent copies before adding a second saving rule. [Google's IMAP settings guidance](https://support.google.com/mail/answer/78892) notes that Gmail automatically retains sent messages for its SMTP path. Treat that as provider-specific behavior to reconcile with the actual client, not a universal instruction to disable sent-copy storage across all accounts. Correct a confirmed mapping only within its authorized scope.

For an offline requirement, establish the actual cache window and attachment behavior separately. A subject list or online-opened message does not prove offline readability. Use a supported account-specific offline route and an approved representative message if available; do not disconnect the whole computer, remove another app's network access or disturb queued sends as an incidental test. If offline use was not requested, do not expand setup into a full mailbox download or backup.

## Verify the requested result without manufacturing evidence

Separate acceptance into observable layers:

1. **Configured:** the exact account is present once in the intended profile, with approved service/access scope and saved account settings
2. **Reading observed:** the selected native client retrieves the identified message or folder content for that account, with current connection evidence rather than only a stale cache
3. **Synchronization observed, if requested:** a specifically authorized benign state change is reflected in the intended other view; record the exact property and direction actually exercised
4. **Sending observed, if authorized:** one approved message uses the intended From address and recipients, reaches the named destination with evidence, and has the expected sent-copy placement
5. **Offline use observed, if requested:** the selected content actually opens without its network dependency under a supported, non-disruptive check

Prefer already-read, ordinary messages for reading checks. Preserve unread state through a supported read-only route; if opening a message necessarily changes it, resolve that side effect before proceeding. Do not load blocked remote content, send a receipt, open executable attachments or use confidential mail as test material.

A synchronization check needs authority for the actual state edit. Do not create a draft, flag, move or delete a message just to get a green check. Where an approved benign draft or flag is used, identify its owner/account, allowed contents, expected server effect and cleanup in advance. A created draft may synchronize immediately. Cleanup is another edit and must not remove a concurrent user change.

If the user requests working send/receive, obtain the smallest missing authority for a benign exchange. Verify the full recipient address, content, From identity and any attachment before sending. Observe destination evidence only in an authorized account or supplied recipient record. An Outbox disappearance, Sent copy or successful outgoing-server check does not alone prove receipt; use [delivery tracing](../trace-email-delivery/SKILL.md) if the boundary remains uncertain. Do not retry the send until the first attempt's outcome is established.

Reopen the account settings and return to its native mailbox after the check. Confirm that unrelated accounts, default sender, existing service selections and pending work remain as intended. If the requested outcome is a usable connection and synchronization is still progressing, continue the relevant authorized observation until usable, failed or blocked by a specific user/provider action. Do not promise an arbitrary completion time or create unrelated monitoring.

## Recover a partial setup without deleting the only copy

After a timeout or closed sign-in window, inspect the account list, enabled services and provider consent state before retrying. The grant and account record can have completed independently. Reuse the identified partial state where supported; do not repeatedly create account entries, new app passwords or permission grants.

For repeated authentication failures, establish the account identity, chosen provider type and supported sign-in route. Preserve the exact non-secret error and check current official guidance. Avoid password guessing and repeated prompts that can trigger lockout. A blocked managed account needs the provider/admin decision; client resets and alternate protocols do not bypass that boundary.

For slow or incomplete loading, inspect connection/progress state, requested cache window, folder visibility and available storage. Use a narrow supported correction when authorized. Do not rebuild the entire mail database, delete caches, clear the OS account store, disable antivirus or erase profiles as a first response. A smaller local download window can be proposed, but must not silently invalidate requested history or offline coverage.

Removal is not a harmless reset. Before removing a partial account, inventory unsent messages, local-only drafts, archives and any items that have not reached the server. Verify their preservation through a supported route and obtain the required permission for any copy/export. If there is no proven surviving copy or safe preservation path, leave the account intact and report the blocker. Never assume an account cache is disposable because most mail is normally server-backed.

Identify the exact removal scope. Apple's account guide explains that removing a Mail account removes its messages from the Mac; shared Internet Accounts can also serve other apps. Microsoft's Outlook guide distinguishes device removal from removal across devices and warns that the latter can lose items held only in Microsoft Cloud. Preserve other app/device dependencies. Do not choose all-device removal, delete a profile or accept a permanent-data-loss warning as a convenient retry. Apply the required deletion confirmation, and leave unsupported destructive recovery to the user.

Disabling local use, removing a client account, revoking a provider grant and deleting the mailbox are different actions. For a requested withdrawal, state which route is ending and which copies or access routes remain. Follow [connected-app review](../review-connected-app-access/SKILL.md) when provider-grant revocation is needed; obtain applicable security confirmation rather than assuming local removal revokes it. Reauthorization also creates access and needs current approval. Never save credentials as rollback material.

If the wrong account or broader data scope was connected, stop dependent tests, report the exact discrepancy, and perform only authorized targeted containment. Removing a connection cannot retract data already copied to a device or cloud service. Preserve current legitimate changes rather than restoring a stale whole-profile snapshot.

## Deliver and stop

Return the account and client identity privately, actual connection type and processing path, enabled services, relevant special-folder/cache choices, and the evidence level achieved. Include only the useful opening route, any user action still needed, and the supported disable/removal route with its preservation caveat. Keep secrets, full headers and unrelated message contents out of the handoff.

A proposal-only result must identify the precise consent, provider, client or data-scope decision blocking activation. A configured result with untested sending must say so. Do not call a sample message a complete historical-sync audit, a synchronized mailbox a backup, or a successful desktop setup proof that every other device works.

Finish at the requested setup and bounded verification. Message migration, ongoing inbox handling, additional devices, default-client changes, automatic filing, forwarding and account closure remain separate work.

## Fictional, unexecuted illustration

An invented user asks to read an existing work mailbox in Apple Mail on a particular Mac. The mailbox already appears in Internet Accounts for Calendar, but Mail is disabled. Existing calendar use must continue, an unrelated personal mailbox must remain the default sender, and no test email is requested.

The preparation would identify that existing account rather than creating a second entry. It would establish the required Mail access and obtain action-time confirmation for the new persistent capability. The proposed change would enable Mail on that account while preserving Calendar and the personal sender default. A later authorized check could compare one already-read, ordinary message with the same account's server record and inspect its requested server folder. Until those steps actually occurred, the status would remain prepared, not connected or verified. Outbound delivery would remain untested.

If the same request instead encountered an Outlook cloud-sync consent including unapproved calendar/contact data, the dependent activation would remain blocked until that exposure decision was resolved. Hiding those views would not satisfy a mail-only transfer requirement.

All account circumstances and outcomes above are fictional. No device, mailbox, credential, consent screen, client, message or application was accessed, changed or tested for this illustration.
