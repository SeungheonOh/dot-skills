---
name: recover-deleted-email-messages
description: "Locate and recover selected retained email messages through native Trash, Deleted Items or supported second-stage recovery. Preserve message-versus-conversation scope, distinguish intermediate recovery from the intended mailbox destination, and verify contents without resending, importing an archive or restoring an entire account."
---

# Recover the selected messages, not the whole mailbox

Return identified deleted mail to its intended accessible mailbox location, or establish what the available recovery route cannot recover. A conversation reappearing is not proof that every requested message returned. An item leaving a recovery list is not proof that it reached the Inbox.

Use [mistaken-send recovery](../recover-mistaken-email-send/SKILL.md) to stop or recall an outbound send, [local archive opening](../open-local-mail-archive/SKILL.md) to browse an existing PST or MBOX, and [inbox triage](../inbox-action-triage/SKILL.md) to classify active mail. Calendar items need [calendar-event recovery](../recover-deleted-calendar-events/SKILL.md). This workflow does not perform account-wide rollback, recover erased disk sectors, change retention, repair a mail database or reconstruct messages from quoted replies.

## Establish the wanted mail and its destination

Use the request and scoped account evidence to identify:

- The underlying mail service, account, client edition and relevant personal or delegated mailbox
- Individual messages, a complete conversation, or an explicitly bounded deleted set
- Sender/recipient, approximate sent or received interval, and useful subject or attachment anchors
- Locate-only versus restore, and the intended destination within that mailbox
- Any exclusions, live copies, known previous recovery attempt or local-only requirement

Ask only when the answer changes the selection or operation. One identifiable receipt does not need a mailbox recovery inventory. A date of receipt is not necessarily a date of deletion; keep both distinct when searching retained items.

A clear request to restore the identified mail to its established mailbox location authorizes that narrow recovery. Do not ask again just because it was found. Resolve a different account, newly shared destination, wider conversation or folder, or account-wide restore before acting. Permission to find a missing message does not authorize moving it. Recovery does not authorize a reply, forward, read receipt, attachment upload or contact with an administrator.

## Locate before undeleting

Prefer available service tools that actually expose deleted-state search and the needed restore operation. A normal Inbox search is not a complete mailbox search, and a connector that can read mail may not expose second-stage recovery. Use the supported account interface when necessary, without creating credentials or expanding permissions to make it work.

Inspect the narrow active and retained populations relevant to the target. Distinguish:

| Finding | Appropriate result or next action |
| --- | --- |
| Message active in Archive, another folder, or under another label | Return its verified location; do not claim an undelete occurred |
| Message hidden by a view, category or synchronization issue | Check that view/device separately rather than creating a replacement |
| Message in Spam/Junk | Identify that state; do not silently report Not spam, trust a sender or change filtering |
| Exact message in Trash/Deleted Items | Establish the selected message scope and return destination |
| Exact message in a supported second-stage recovery list | Establish the intermediate and final recovery steps |
| Only a forwarded copy, quote or old archive survives | Describe it as a separate copy, not the retained original |
| No candidate in the inspected scope | Report coverage and remaining supported routes; do not declare permanent loss from an empty search |

Use native IDs and mailbox provenance where exposed, alongside headers and content anchors. A Message-ID header or subject alone is not a unique account item: duplicates, forwarded material and multiple stored copies can coexist. Preserve any provider-returned ID mapping across a move rather than requiring an old identifier to keep working.

Inspect only enough content to settle identity and the requested properties. Avoid loading remote images, following embedded links, opening attachments, or sending receipts. Prefer non-mutating views; if a required UI read changes flags, establish permission for that side effect instead of silently treating it as read-only.

## Use the account's real recovery mechanism

These official starting points were checked on 2026-10-21. Use the route for the actual service and edition, not the branding of a desktop client connected to it.

### Gmail

[Google's recovery instructions](https://support.google.com/mail/answer/7401?hl=en) describe Trash retention of up to 30 days and the Trash → select → Move to route. Manually permanently deleted messages are not recoverable through this ordinary route. Discarded drafts do not enter Trash. Do not promise draft recovery or extend retention by changing a setting after deletion.

For a missing message, [Google's search guidance](https://support.google.com/mail/answer/7015314?hl=en) uses the Mail & Spam & Trash search scope. Search the bounded target there rather than relying on an Inbox-only query. Identify the exact matching messages before selecting a conversation row or using a thread-level operation. A restore request for one message is not authority to activate every deleted message grouped with it.

### Outlook

[Microsoft's recovery guide](https://support.microsoft.com/en-us/outlook/mail/recover-and-restore-deleted-items-in-outlook) has separate new Outlook, classic Outlook and web routes. In Deleted Items, move selected mail to the intended mail folder. Where supported, use Recoverable Items for mail no longer there; missing controls can reflect account capability, not a need to install an add-in.

Classic Outlook's Recover Deleted Items From Server returns recovered items to Deleted Items before a further move. Do not stop at that intermediate state. Inspect the actual return location for the selected edition instead of assuming every Restore control means Inbox.

In the classic recovery list, Deleted On can mean removal from Deleted Items or a permanent-delete action, not receipt or the first deletion. Envelope icons also represent non-mail items. Select actual messages, not appointments or contacts sharing the same icon. Retention is account/policy dependent; do not impose one universal period. A recoverable deleted folder may include all its mail, so do not restore the folder merely to retrieve one message.

### Apple Mail

[Apple's Mail guidance](https://support.apple.com/en-gb/guide/mail/mlhlp1001/mac) describes moving retained messages from the account's Bin/Trash into another mailbox. Availability depends on mailbox behavior and whether the messages have been erased; a setting of None does not provide a Trash copy. Inspect the correct account's actual retained mail rather than changing its future deletion settings.

Check whether the destination is server-backed or On My Mac. Moving into another account can transmit mail there, while a local destination may not meet a request for access on other devices. Do not choose either silently. A unified Trash view is not one account.

## Fix the selection before mutation

For one message, retain a short identity and destination note. For a set, keep a private per-message list with source state, account/item identity, selected action, expected intermediate destination if any, final destination and outcome. Do not copy full message bodies into this record unnecessarily.

Check whether the UI or operation acts on a message, a conversation, all current results, all matching results across pages, or a whole folder. Expand or inspect the actual selection when needed. If the available operation cannot respect an exclusion, hold that selection and explain the exact limitation. Do not recover everything and delete the extra mail afterward as a workaround.

For a complete conversation, establish the requested message set from available evidence. A retained list proves which messages are currently recoverable, not that it contains every message ever exchanged. Do not infer completeness from a subject match or conversation count. Preserve live messages and their existing labels, folders and flags unless changing them is part of the request.

Recheck the selected messages immediately before restoring. Another client or delegate may already have moved them. If a known active rule or process would immediately remove returned mail, resolve that specific effect before repeated recovery; do not disable all rules, disconnect accounts or revoke integrations under recovery-only authority.

Use the smallest supported operation once. Do not empty Trash, purge recoverable items, send a test message, or reimport an old archive to make the folder look populated. If the restore reaches an intermediate folder, complete the already-authorized move to the intended final location and preserve the identity mapping between stages.

## Verify the message, content and placement separately

Use a fresh native lookup or mailbox view after recovery, not only a toast or the now-empty selection. For each requested message, check:

1. The correct account and matching original message or evidenced returned identity
2. The final mailbox folder/labels and absence from the deleted state applicable to that message
3. Required sender/recipient, date, subject and available body content
4. Required attachment presence, distinguishing a filename from accessible retained payload and a linked cloud document from an embedded attachment
5. Preserved unrelated messages and relevant flags, labels or exclusions

Inspect attachment metadata or payload safely only as needed; do not execute it or fetch a third-party linked file merely to certify recovery. An encrypted body can be retained but unreadable with the current credentials. A message can be restored while an external image or linked file remains unavailable. Report these as separate properties rather than deleting and retrying the recovery.

When a particular device is part of the request, check its ordinary synchronized view if available. Server-side recovery does not establish that an offline phone has updated. Do not clear caches or remove/re-add accounts to improve a completion claim.

## Handle uncertainty and unrecoverable targets

After a timeout or lost response, inspect the original retained entry, any intermediate folder and the final destination before retrying. A missing old ID can reflect a move, not failure. Reconcile partially completed batches per message; do not repeat an entire conversation or folder operation because one message remains absent. If the state cannot be determined, keep the outcome unknown and stop dependent writes.

If a message returns to Trash again, distinguish a fresh deletion from a stale display with current account evidence. Do not get into a restore loop or modify filtering without authority. Report the repeated effect and the specific decision needed.

Where ordinary recovery is exhausted, preserve the searched account, bounded interval, identifying metadata and observed limitation. An administrator or official service recovery route may have different eligibility or broader effects. Explain that possible next route without initiating a mailbox-wide restore, acquiring administrative access or promising success. A support request, archive import or recovery from someone else's copy is separate work with its own audience and data-sharing authority.

Deliver a concise result per requested target: already active, located only, restored and read back, intermediate recovery only, partial contents, held, unavailable through inspected routes, or outcome unknown. Include verified message links when supported, actual destination, coverage limits and the smallest remaining decision. Stop when the requested messages and required properties are verified or a specific capability, retention, access or scope boundary prevents further authorized progress. Do not turn a one-time recovery into recurring mailbox monitoring.

## Fictional illustration, unexecuted

A user wants one deleted workshop receipt returned to the same account's Inbox, leaving an older message with the same subject deleted. Suppose the native view groups both into one conversation. The appropriate plan identifies the receipt by its own sender, date and attachment anchors, then uses a supported individual-message selection. If only a whole-conversation action is available, recovery is held rather than broadening the request.

In an independent classic Outlook example, suppose a second-stage recovery succeeds but the selected mail is now in Deleted Items. The task would remain unfinished until the intended Inbox move and message readback. A lost move response would call for locating the same message in both places before a retry, not recovering every remaining item.

These are authored decision illustrations, not observations. No mailbox, message, recovery control, client, attachment, synchronization process, repository test or live workflow was exercised for this guide.
