---
name: configure-mailbox-delegation
description: "Prepare or configure a named person's native access to an existing mailbox or selected mail folders, separating content rights, sending identity, activation and removal. Use for a mailbox access relationship, not shared-inbox operating rules, calendar delegation, forwarding, account provisioning or sending mail."
---

# Give a colleague the mailbox access the task actually needs

Deliver a private access map and, when specifically confirmed, a saved native delegation or folder-sharing change with a usable entry route. Keep permission to read, change, delete and send distinct. A delegate appearing in settings, accepting an invitation, opening a mailbox and sending successfully are different observations.

Use [shared-inbox setup](../configure-shared-inbox-workflow/SKILL.md) for how existing operators claim and handle common work, [work-absence handoff](../prepare-work-absence-handoff/SKILL.md) for duties and decision limits, and [connected-app review](../review-connected-app-access/SKILL.md) for software grants. This workflow establishes or removes a person's access relationship. It does not create an assistant account, migrate mail, change organization policy or authorize the colleague's substantive decisions.

## Establish the exact relationship and exposure

Resolve from the request and current authorized records:

- Provider, organization, mailbox's primary address and stable identity, account type, and actual client/version
- Named delegate's verified account identity and organization; distinguish a person from an alias, group or similarly named contact
- Work that needs access, exact mailbox or existing folder scope, and required capabilities: read, create, edit, delete, send as the owner or send visibly on the owner's behalf
- Historical and future information the recipient may access, any excluded material, and whether the provider can enforce that boundary
- Proposal, new grant, adjustment or removal; existing rights that must remain, and any requested end date
- Available owner/admin interface, recipient-side evidence, expected invitation notifications and requested verification depth

Do not turn “help with my inbox” into authority to expose the whole account. Ask about a missing scope or sending decision before granting access. A named mailbox may contain confidential or sensitive material unrelated to the work; a task description alone does not approve that broader disclosure. Determine suitability from settings and minimal authorized context rather than reading the entire mailbox.

Separate technical capability from agreed work. “Do not delete anything” is a working instruction, not a read-only access control if the chosen role permits deletion. Likewise, asking someone to check one label does not confine their access to that label. If the provider cannot express a material exclusion, stop at a proposal and explain the mismatch. Do not relocate private messages, create forwarding rules or make sanitized mailbox copies as an unrequested workaround.

For time-limited cover, inspect whether the actual grant supports automatic expiry. A return date in a handoff is not an expiry control. If expiry is unsupported, identify the required manual removal and its owner; obtain agreement to that limitation before creating an otherwise indefinite relationship. Do not silently create a recurring access audit or promise future removal without an authorized, supported arrangement.

## Inspect existing routes before choosing a grant

Use a connected permission interface when it exposes the needed resource and rights; otherwise use the supported provider interface in the authorized environment. Mail-reading access does not imply delegation-management capability. Do not create OAuth consent, a service account, domain-wide authority, new credentials or an administrator role to make this workflow possible.

Record the existing target-specific rights and relevant dependencies before proposing changes. Include direct mailbox rights, folder ACLs and their parent navigation requirements, sending grants, existing delegate entries, and applicable group routes when visible. Keep hidden membership or inaccessible settings unknown. The absence of a person from one panel is not proof that they have no other access.

Bind each proposed delta to the granting resource and recipient. A compact record can contain: mailbox/folder identity, delegate, right, existing value, proposed value, information exposed, notification effect, activation evidence and removal route. Preserve the prior values of fields that will change; do not export message contents or credentials for rollback.

Distinguish a personal navigation shortcut from a server permission. Adding a mailbox to an authorized person's view can help them find existing access; removing it from that view does not revoke their rights. An account owner's own successful opening provides no evidence that the proposed delegate can open it.

## Select the smallest supported access model

Consult the current official documentation for the actual account and client. The following routes were checked on 2026-10-17; labels and availability can change. Do not substitute a different product or broader permission merely because the expected control is absent.

### Selected Outlook mail folders

When only selected existing folders need to be read or edited, assess folder sharing before mailbox-wide delegation. Microsoft's [folder-sharing guide](https://support.microsoft.com/en-us/outlook/sharing/share-and-access-another-person-s-mailbox-or-folder-in-outlook) distinguishes content permissions from parent-folder visibility. Reviewer reads items; Editor also creates, changes and deletes them. Folder visible permits navigation without reading parent contents. In new Outlook and Outlook on the web, use the exact folder's Sharing and permissions controls and inspect the capabilities behind the role.

Parent visibility can be added automatically, and removing a child grant can leave those parent entries behind. Include this dependency in both the proposed change and removal plan. Do not grant read access to Inbox or mailbox root simply to expose a nested folder. Existing parent rights may support another shared folder and must not be indiscriminately removed.

Folder sharing by itself is not authority to send under the owner's identity. Check the actual interface's notification behavior before saving; the official page contains differing descriptions across its overview and steps, so do not promise that a change is silent. Do not treat one shared folder as proof of access to its siblings or descendants: verify the exact requested scope and provider behavior.

### Outlook delegation and Exchange mailbox rights

For actual on-behalf sending, [Microsoft's delegate instructions](https://support.microsoft.com/en-us/outlook/sharing/allow-messages-to-be-sent-on-your-behalf-when-sharing-a-folder-or-mailbox) describe classic Outlook's File → Info → Account Settings → Delegate Access route. Their documented new-Outlook/web mail-delegation setup still relies on classic Outlook. If that required client is unavailable, return the precise prerequisite rather than switching products, installing software or asking for an admin workaround without authorization.

The delegate dialog can grant on-behalf sending even when Calendar, Tasks, Inbox, Contacts and Notes are all set to None. Therefore it is unsuitable for a read-only request. Inspect every folder choice, meeting-request option and private-item control. For a new mail-only relationship, leave unrelated capabilities ungranted; for an existing delegate, preserve unrelated rights unless their removal is expressly requested. Do not apply new-delegate defaults over an established calendar arrangement.

If the task uses an existing authorized Exchange administrator route, [Exchange's permissions reference](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-permissions-for-recipients) separates Full Access from Send As and Send on Behalf. Full Access permits content management but not sending; either sending grant alone does not grant reading. Send As conceals delegation in the visible sender presentation, while Send on Behalf identifies it. With both rights present, Send As takes precedence. Do not add both “to be safe.”

For that route, select only the exact mailbox under Recipients → Mailboxes → Mailbox delegation and the approved permission's individual edit control. Avoid bulk selections. Auto-mapping is a client-discovery behavior, not a separate proof of effective access; its behavior can differ for individual and group grants. Record a hidden-address-list or organization restriction as a blocker rather than changing that setting incidentally. A full-mailbox role is not an acceptable substitute for folder-only requirements.

### Gmail native delegation

[Google's Gmail guidance](https://support.google.com/mail/answer/138350?hl=en) describes a bundled ability to read, send and delete mail. Setup uses the computer interface: Settings → See all settings → Accounts and Import/Accounts → Grant access to your account → Add another account. Verify the primary account identities before the invitation. An alias is not a separate delegatable Google Account, and work/school eligibility is organization-bound.

Google's [Exchange-migration guidance](https://support.google.com/workspacemigrate/answer/9762324?hl=en) explicitly notes that Gmail delegation does not support folder-level or read-only access. Thus “read this one label, without sending or deletion” must remain unsupported rather than becoming whole-inbox delegation. Calendar permissions are separate. Do not turn on organization-wide delegation, change sender-disclosure policy or convert an account to meet a narrower request.

The native invitation requires acceptance, expires after a week and may take time to become usable. Keep invitation, acceptance and successful access separate. Give the delegate the supported account-switcher route to the account marked Delegated, rather than a copied inbox URL. Do not accept an invitation using someone else's session.

Existing API capability does not necessarily have the same invitation semantics. Google's [delegate-create reference](https://developers.google.com/workspace/gmail/api/reference/rest/v1/users.settings.delegates/create) documents a domain-wide-authorized service-account method that creates an accepted grant without verification mail. Do not present that as a pending invitation or introduce that authority to bypass the native flow. Record the actual supported route and its activation effect before requesting approval.

## Confirm the exact access change, then apply it

Every grant or material expansion of persistent mailbox access requires action-time user confirmation before the operation, even when the initial request asks for setup. The confirmation must identify the mailbox/folders, verified person, actual native capabilities, historical/future information exposed, sending identity, any unavoidable notification and any absence of automatic expiry. A generic assistant-work request, administrator role or approved handoff document does not supply this confirmation.

Bundle the foreseeable linked changes in one exact approval when possible: for example, the selected folder's read role and only the required parent visibility. If the interface reveals broader reach, a different person, additional sending rights or a changed security effect, pause and resolve that change. Merely reaching a provider's Confirm button does not establish user approval.

Use the provider's supported login/identity-verification flow. Keep passwords, tokens and recovery material out of chat and artifacts; hand credential entry to the user when required. Do not disable authentication controls or reuse the owner's credentials in the delegate's client. This workflow grants native rights to an existing identity, not account impersonation by password sharing.

Immediately before writing, recheck the target, current rights and confirmed delta. Apply only those fields, then reopen the exact permission record. A multi-panel setup is not atomic. Retain each component as saved, absent, pending, blocked or unknown rather than treating a partially applied relationship as complete.

The approved provider invitation may occur as part of the grant. A separate announcement, reminder, test message, draft, real reply, message move or deletion needs its own actual authority. Granting a colleague sending capability does not authorize the assistant to send mail or establish standing permission for arbitrary communication.

## Verify the configured relationship and hand it over

Check the requested result in separate layers:

1. **Configuration:** the exact person and resource have the approved rights; unrelated delegates, folder roles and calendar/private-item options remain as intended
2. **Activation:** invitation or provider verification state supports the claimed status; a pending or expired invitation is not active access
3. **Usability:** a supported effective-access view or existing authorized recipient evidence establishes the exact required capability; otherwise mark recipient use untested
4. **Sending behavior, only if requested and authorized:** evidence from a specific benign exchange shows the intended From/on-behalf presentation and recipients; configuration alone does not prove delivery

Do not enter a colleague's account, create a test identity, read excluded messages or exercise deletion to manufacture evidence. If a live sending test is requested, resolve its sender, recipient, approved content and expected side effects first. A read check cannot establish sending, and an internal test does not prove external delivery. Preserve unread state where the supported route permits; resolve unavoidable read-state changes before a test that would affect actual work.

If activation is delayed, preserve the grant and consult the matching provider's propagation guidance. Repeated deletion/re-creation is not a refresh operation. Check only through the requested observation scope. A configured result can be handed over with recipient acceptance pending; if the requested outcome is working access, continue the authorized checks until it works or a specific recipient action, missing authority or provider constraint blocks progress. State that dependency clearly.

Return the private access map, actual changes and readback time, invitation/activation state, the delegate's supported opening route, the level of verification achieved and any expiration/removal responsibility. Include a short instruction to check the active mailbox identity before acting. Do not publish the account's access inventory or claim that a grant means the colleague accepted the work.

## Remove or recover the relationship without widening it

For requested removal, identify exactly which rights must end and which must remain. Obtain the applicable action-time confirmation for account-security changes before revoking them. Removing reading access can leave independent sending rights; removing sending can leave content access. A direct grant's removal does not resolve a separate group or folder route. Inspect those routes before claiming all access ended, but do not alter group membership under a single-mailbox request.

Use the exact delegate/permission removal control and read the same resource back. In Gmail, inspect the specified account's delegation entry. In Exchange, reconcile the applicable Full Access, Send As and Send on Behalf entries separately. In Outlook folder sharing, account for parent navigation entries and other remaining folder dependencies. Removing a shortcut, changing a display name or closing a browser tab is not revocation.

After a timeout, inspect before retrying. If a grant exists with the intended rights, do not send another invitation. If only part of a multi-step change succeeded, finish only the still-authorized delta with current preconditions. Never restore an entire old ACL or remove every delegate as a cleanup shortcut.

Rollback can itself create access: restoring a removed grant or broadening a narrowed role needs its own current action-time confirmation. Preserve concurrent legitimate edits, and do not keep credentials or mail copies as recovery material. For an unintended recipient or overbroad grant, stop dependent actions, report the exact discrepancy and obtain the required authority for targeted containment. Do not claim removal retracts previously delivered mail, exports or cached copies, or proves every active client has refreshed.

Stop when the requested proposal, confirmed configuration or removal and its bounded evidence are delivered, or when the exact required decision is exposed. Ongoing mailbox handling, calendar delegation and future access monitoring remain separate work.

## Fictional, unexecuted illustration

An invented user wants a verified colleague to read an existing Project Cedar mail folder during a short absence. The colleague must not send on the user's behalf, edit messages or view the rest of the mailbox. The selected work account exposes Outlook folder permissions.

The proposed record selects Reviewer on that exact folder, inventories existing parent visibility and independent sending rights, and leaves the Delegate Access dialog unused. It includes any necessary navigation-only parent change in the action-time approval request. If a preexisting Send on Behalf grant is found, the desired no-sending boundary remains unresolved until its removal is specifically confirmed; adding Reviewer does not cancel it. The return date is recorded as a manual-removal responsibility unless real expiry support is established.

For the same narrow request in Gmail, the result would instead be a blocked setup proposal because bundled delegation exceeds the requested rights. Neither result would claim working access from the owner's view. All people, folders, dates and settings are fictional. No account, permission, invitation, message, client or recipient session was accessed, changed or tested for this illustration.
