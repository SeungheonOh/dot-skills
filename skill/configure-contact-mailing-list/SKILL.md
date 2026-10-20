---
name: configure-contact-mailing-list
description: "Create or update a private native contact list for a defined email audience, preserving exact member addresses and verifying saved membership. Use for personal recipient shortcuts, not shared distribution-group administration, contact merging, bulk marketing or sending messages."
---

# Configure a contact mailing list without changing its audience

Deliver a reusable recipient list in the intended account, with the requested members and email choices, or a precise preparation-only result when the client cannot represent them. A list name and a matching member count do not establish the right recipients. Separate contact membership, selected email addresses and actual message recipients.

[Address-book reconciliation](../reconcile-address-book-contacts/SKILL.md) handles duplicate people and field consolidation. [Mail merge](../prepare-mail-merge-batch/SKILL.md) produces personalized documents. [Shared-inbox setup](../configure-shared-inbox-workflow/SKILL.md) handles team message ownership and history. This workflow creates a private native recipient shortcut, not a new mailbox, shared group or permission boundary.

## Identify the list and its intended use

Establish the owning account, contacts/mail application and version, new or existing list, authoritative member source, and required email address for each member. For an update, distinguish adding named members, removing named members and replacing the whole membership. Do not interpret “add these three people” as permission to remove everyone else.

Inspect relevant existing records before asking. Resolve consequential ambiguities such as two same-named contacts or work versus personal email. Do not infer membership from everyone in an old thread, search result or organization directory unless that population is the user's specified source. Keep unresolved people outside an applied subset and disclose that subset; if the user needs an exact complete list, hold activation until its membership is resolved.

Confirm the actual object type. A personal Contacts label, Outlook contact list or Apple Contacts list is different from a Google Group, Microsoft 365 Group, shared mailbox or administrator-managed distribution group. If setup offers invitations, a shared address, shared files or access permissions, stop and identify that mismatch. Do not provision a collaborative group merely because its button is more prominent.

Use existing authorized access. Store only needed names, identifiers and addresses in the intended private account. A list request does not authorize copying a whole address book to another account, installing an add-in, changing synchronization, subscribing people, sharing membership or sending test mail. Obtain any missing authority for new contact creation or data transfer instead of treating it as incidental list setup. Existing delegation can also affect who can see or manage the account; do not promise exclusive visibility without evidence.

## Map people to exact addresses

Prepare a compact private member map: source identity, exact selected email, current membership and proposed add/remove/retain/hold action. For existing records, retain their owning account and stable contact ID where available. A display name, list label or autocomplete chip alone is insufficient identity evidence.

- Keep distinct people with the same name separate. If two people intentionally share one mailbox, preserve that relationship in the plan rather than inventing two unique delivery endpoints.
- Preserve supplied email values. Do not strip plus-tags or dots, guess a domain, or select the first address because it is convenient.
- Do not include all of a person's addresses when only one was requested. Conversely, a person count is not the address count when multiple addresses were expressly requested.
- Hold contacts with no usable email and conflicting address choices. Do not enrich them through public searches or contact them to ask for details without authorization.
- Inspect nested lists and rule-based lists before using them. Their displayed membership may not enumerate their eventual recipients. Prefer an explicit static list for a fixed roster; do not introduce dynamic rules that can silently expand it later.

For an existing list, record its full relevant membership before editing, including entries not present in the new source. If access or pagination is incomplete, hold replacement and removal decisions that depend on completeness. Never merge or delete contacts simply to make the list look tidy.

## Use the supported native route

Check the current official instructions and actual interface for the chosen client; the routes below are not interchangeable. Apply only the authorized membership delta. Preserve other lists, contact fields, default account and mail settings.

### Google Contacts labels

In the intended Google account, use Contacts → Labels → Create label for a new list, then select the intended contacts and use Manage labels → the exact label → Apply. For removal, deselect that label on the selected members rather than deleting the contacts. [Google's grouping guidance](https://support.google.com/contacts/answer/30970?co=GENIE.Platform%3DDesktop&hl=en) states that a label group uses only a contact's default email when several exist.

Therefore, a correct work roster may still address someone's personal mailbox. Inspect the default address. Do not change a contact-wide default merely to fix this one list without authorization for that wider effect. If the requested address set cannot be represented by the existing records, hold that part and explain the choice; do not create duplicate contacts as a hidden workaround. A Contacts label is not a new independently addressable Google Group.

### Outlook contact lists or contact groups

Match [Microsoft's instructions](https://support.microsoft.com/en-us/office/create-edit-or-delete-a-contact-list-or-contact-group-in-outlook-88ff6c60-0a1d-4b54-8c9d-9e1a71bc3023) to the client. In new Outlook or the web app, use People and the contact-list controls; an existing list is under All contact lists → Edit. In classic Outlook, use People → New Contact Group, or open the existing contact group and change its members. Save through that client's list editor.

Select the intended private contacts location and inspect each stored email, including manually entered addresses and directory suggestions. Do not assume that a later change to a contact card will update every saved list entry. Reopen the list and inspect its current values. A Microsoft 365 Group with shared resources is not a substitute for a personal contact list. If a required control is absent, report the exact client/account limitation rather than switching accounts or creating a different object.

### Apple Contacts lists

Use the intended account in Contacts and create a static list or select the existing one. [Apple's list guidance](https://support.apple.com/guide/contacts/create-and-change-lists-adrb3280fe91/mac) warns that creating from All Contacts uses the default account, and selected contacts must belong to the same account. Do not move or copy them across accounts to bypass that boundary. Exchange folder membership has different behavior; do not assume it behaves like an ordinary multi-list label.

For a member with several emails, use Edit → Edit Distribution List, select the list and Email column, then select the intended address and save. [Apple documents this list-specific address choice](https://support.apple.com/en-euro/guide/contacts/adrbk1513/mac). For removing membership, use Remove From List, not Delete Contact. Read the actual dialog before confirming; removing a recipient shortcut must not remove the underlying person.

## Read back membership before claiming completion

Reopen the saved list in the owning account. Compare actual member identities and selected email addresses with the approved map, not only counts. Check all members of a small list; for larger lists, use a complete supported readback rather than claiming completeness from a visible first page. Confirm removed members are absent from this list while their underlying contacts and unrelated memberships remain intact.

Report contact count and unique address count separately when they differ. Account for held members and unsupported selections. A saved label with the wrong default address is not a fully configured mailing audience.

Composition verification is a separate optional step. If creating a mailbox draft is authorized, open a new dedicated draft in the intended sender account, expand the list and inspect every actual address and its To/Cc/Bcc placement without sending. [Apple Mail exposes Expand Group](https://support.apple.com/en-euro/guide/contacts/adrb475c5d8d/mac); other clients have their own supported recipient inspection. Do not use an existing user's draft as a test surface or assume closing a composer discards its saved draft. Retain or remove that test draft only within the authorized scope.

A collapsed group chip does not establish that recipient addresses are hidden. For a later send, resolve the intended recipient-visibility choice and verify the actual message fields. Bcc is a composition choice, not a property guaranteed by the saved list. List creation does not authorize any future message, and list readback does not prove delivery. If composition was not authorized or supported, state that mail-client expansion remains untested; native membership verification can still complete the requested setup.

## Recover narrowly and hand off

After a timeout, inspect the exact account and list before retrying. Search for the just-created list by its identity and creation context, not name alone, so a lost response does not produce duplicate lists. Re-read changed membership before repeating an add or remove. Preserve unrelated concurrent edits; do not restore an entire stale roster automatically.

If readback shows the wrong address, correct only the supported authorized selection. If a contact default, source card or nested list needs a broader change, explain that dependency and hold it. Do not send a message to find out whether the address works. Removing a member later does not retract messages already sent or alter recipients already resolved into an existing draft.

Return the owning account and list location, confirmed membership/address choices, held entries and checks actually performed. Keep the full roster private. Distinguish prepared, saved and read back, composition-expanded, and sent; this workflow normally ends at saved and read back. Do not start recurring membership audits or add automatic sending.

## Fictional illustration, not executed

The user wants an existing private Google Contacts label to add two named colleagues, using work email only, while retaining its current members. One colleague has a single work address. The other has both work and personal addresses, with personal set as default. The request excludes changing contacts and creating mail drafts.

The plan retains existing members and marks the second colleague held because label membership alone would select the wrong address. It does not change the contact default, duplicate the card, delete prior members or open Gmail Compose. If the user permits a partial update, the first colleague can be added and verified, with the list explicitly reported incomplete; otherwise the update remains prepared. Completion of the exact requested audience requires a supported address choice and any necessary additional authorization.

This is an unexecuted illustration, not evidence of account access, list creation, contact editing, a saved draft or a delivered message.
