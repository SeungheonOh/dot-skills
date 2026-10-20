---
name: configure-mail-search-view
description: "Create or revise a saved Outlook Search Folder or Apple Mail Smart Mailbox that gathers matching mail without filing it. Verify message predicates, account/folder scope and persistence while preserving source messages; distinguish removing the view from deleting its contents."
---

# Save a useful mail view without refiling messages

Deliver a reusable native view for a recurring question, such as flagged project mail across selected folders, with its actual scope and checked membership. The result is a saved retrieval definition, not a second mailbox copy, archive, task register or rule that processes incoming messages.

Use [email filing rules](../configure-email-filing-rules/SKILL.md) when messages should acquire labels or move, [inbox triage](../inbox-action-triage/SKILL.md) when the user needs decisions and commitments extracted, and [local mail archives](../open-local-mail-archive/SKILL.md) when historical mail must first become accessible. [Work-tracker views](../configure-work-tracker-view/SKILL.md) handle issue/task records, not mailbox-specific view behavior. Do not replace a view request with automatic filing or reminders.

## Establish the recurring question and destination

Identify the selected app/version, profile, account or local data file, and whether the request creates a view or changes an existing one. Distinguish new Outlook, classic Outlook and Mail on Mac. Inspect existing views first so that a similar name does not cause an overwrite or duplicate.

Recover the intended membership from the request and a few known messages:

- Which accounts, folders and subfolders belong, including any local archive
- Whether Sent, Trash/Deleted Items and Junk belong
- Which message fields and states matter, with explicit any/all logic
- Fixed dates versus a moving window, and which date property is intended
- Whether the user needs the result only in this client or also on another device

A request to configure this view can authorize its ordinary settings change. A request merely to find a message does not authorize saving a persistent view. Ask only about ambiguity that changes membership or save scope. Keep the configuration small: one view normally needs a name, target identity, scope, conditions and a few checked examples, not a mailbox export.

Use the supported native route in the authorized environment. A connector's successful search does not establish that it can create the client's saved view. If configuration access is absent, provide the exact proposed settings and missing step, labeled unexecuted. Do not install another client, add an account, grant new access or buy a subscription to complete the view implicitly.

## Translate the question without changing the messages

Write the membership rule in plain language before entering its controls. For example, “unread messages in these two work folders, including their subfolders” is different from “all unread messages in all accounts.” Bind folder/account choices to their real identities, not duplicate display names.

Keep individual-message matching separate from conversation display. A visible thread can contain other messages; inspect the relevant member rather than concluding that every reply satisfies the condition. Compare identities and original locations rather than treating thread totals as message counts.

Make the important semantics explicit:

- A sender display name is not an exact address or authenticated identity. Use the supported field that actually expresses the user's request.
- Contains, equality, prefix and whole-word matching differ. Do not silently replace an unavailable comparison with a broader one.
- “Unread OR flagged” is not “unread AND flagged.” If arbitrary grouping is unavailable, keep the unsupported expression visible instead of dropping a condition.
- A rolling date window changes membership as time passes. An unread or flagged condition changes as the user works. Neither is a permanent record of outstanding obligations.
- An excluded folder cannot contribute a match even when the message's subject satisfies the other conditions.

Do not add categories, flags or labels to source messages merely to make a convenient view possible. Do not move messages into a new real folder as an approximation. If the predicate cannot be represented faithfully, return the precise limitation and a supported alternative for the user's choice.

## Use the actual client's saved-view feature

Check current official guidance against the installed version. These routes are for saved virtual views, not generic New Folder controls.

### Outlook Search Folders

[Microsoft's Search Folder guide](https://support.microsoft.com/en-us/outlook/mail/use-search-folders-to-find-messages-or-other-outlook-items) distinguishes predefined criteria in new Outlook from advanced custom Search Folders in classic Outlook. A Search Folder cannot span multiple PST files. Do not promise a combined archive view that the product cannot supply.

In new Outlook, use Mail → Search folders in Settings or the mailbox's Search Folders creation control; choose the supported type, selected folders and subfolder option. In classic Outlook, use Folder → New Search Folder; custom definitions expose Criteria and Browse for source folders. Match the selected account and supported comparison, not just the view's name. Microsoft's word-list matching uses prefixes, so it is not exact-word matching.

Keep the distinction between removing a Search Folder and deleting selected result messages: the former removes the view, while the latter deletes mail. A normal folder is not covered by the virtual-folder deletion guarantee.

### Apple Mail Smart Mailboxes

[Apple's Smart Mailbox guide](https://support.apple.com/guide/mail/automatically-sort-incoming-emails-mlhlp1190/mac) describes Mailbox → New Smart Mailbox, native conditions, any/all matching and separate Sent/Trash inclusion choices. Use those controls to express the requested population; record the actual account/mailbox restrictions rather than assuming the current Inbox selection supplies them.

Save the named definition and select it from Smart Mailboxes. To inspect or revise it, use Edit Smart Mailbox. Apple states that deleting the Smart Mailbox itself does not delete the listed emails. This is not permission to delete messages displayed inside it.

For either client, do not claim cross-device availability from a successful local save. Inspect the actual supported synchronization behavior only when that is part of the request. Keep feature availability, definition persistence and source-mail synchronization separate; a missing menu is not authority to migrate the account.

## Save and check membership without manufacturing mail

Capture the existing view's definition before editing it. Preserve unrelated views, source folders, filing rules, read state and flags. Check for concurrent user edits before replacing settings. Creating a new view is preferable to overwriting an unrelated one only when that new object is within the request.

Save the intended definition, then leave and reopen it through native navigation. Read back its criteria, account/folder scope and relevant inclusion options. A screenshot of a temporary search or a visible name alone is not persistence evidence.

Compare a small useful set of existing authorized messages:

1. A known match in each materially different included location
2. A near-match failing one decisive condition
3. A matching-content message outside the chosen scope
4. A meaningful state/date boundary if the view uses one

Use only cases actually available; report an unchecked boundary instead of creating messages to fill a matrix. Keep private subjects, addresses and query text out of public searches and support posts. Prefer metadata or already-read messages. If the UI necessarily changes read state, resolve that side effect before opening an unread target. Do not load remote images, send receipts or open attachments to verify membership.

Verify the selected results against their original account/folder and message identity through a supported read-only route. Preserve the evidence distinction between a message being located, the saved view including it, and all eligible messages being covered. A few examples establish sample correctness, not complete historical coverage or future refresh behavior.

If membership is wrong, isolate the layer before changing anything: saved condition, folder/subfolder scope, temporary filter, collapsed conversation, local availability or indexing progress. Do not immediately rebuild indexes, reimport an archive, reconnect accounts or reset the client. For a known item, first establish whether it is directly accessible in the intended source. An inaccessible source is not an empty matching population.

If checking an unread view appears to remove a result, inspect the message's current read state and original location before calling it deleted. Do not toggle it back solely to preserve an earlier count. Similarly, a newly arrived message can legitimately change totals during setup.

## Recover and hand back the usable view

After an uncertain save, inspect existing definitions before retrying. Resolve partial edits on the exact view rather than creating several similarly named objects. If the definition changed concurrently, preserve the newer user work instead of restoring a stale snapshot.

An authorized rollback should restore only the changed definition, after checking its current state. Removing a duplicate or unwanted view still needs the applicable deletion authority. Verify that the selected object is the virtual view, not a source folder, and do not select all result messages as a cleanup shortcut. Removing a view does not reverse any message edits already performed through it; those require their own evidenced recovery scope.

Return the opening route, saved view name/identity, plain-language membership rule, relevant exclusions and actual verification result. Distinguish proposed settings, saved/read-back definition, sample membership checked, and any unresolved source or cross-device limitation. Do not invent a shareable link when the client only offers native navigation.

Finish when the requested view and immediate checks are complete, or a specific unsupported predicate, unavailable client or access decision blocks them. Do not start ongoing inbox monitoring or interpret the displayed messages as obligations without a separate request.

## Fictional illustration, unexecuted

A fictional user wants a reusable unread-mail view across the work Inbox and its project subfolders, while excluding a personal account and local historical archive. Three invented records are W-1, unread in the work Inbox; W-2, already read in a work project folder; and P-1, unread in the personal Inbox.

The intended sample membership is W-1 only. W-2 checks the unread condition; P-1 checks the account boundary. If the selected native feature cannot restrict the population as required, the result remains a proposal rather than a broader all-account view. A later authorized save would need definition readback and actual message-level checks. No synthetic message needs to be sent or marked unread to demonstrate the idea.

No mailbox, app, search, view, message state or synchronization was accessed, changed or tested for this illustration. Its records and expected membership are fictional, not observed results.
