---
name: open-local-mail-archive
description: "Make a selected existing MBOX or PST mail archive browsable in the chosen desktop client while preserving the original and keeping historical messages out of live mailboxes. Distinguish attaching a data file, importing a local copy and uploading mail; verify the actual archive view and search scope."
---

# Open old mail without silently moving it into an account

Deliver a usable local archive view and a short account of what was preserved and checked. Opening a PST as a separate data file, importing MBOX messages into a local store, and importing mail into an online account have different effects. A readable archive does not establish that its original mailbox was completely exported.

Use [account export audit](../account-export-audit/SKILL.md) for source completeness, [desktop mail account setup](../add-desktop-mail-account/SKILL.md) for a new service connection, and [tool-switch planning](../plan-tool-switch/SKILL.md) for a broader migration. This workflow opens existing historical mail. It does not convert arbitrary mailbox databases, repair corruption, merge accounts, restore account settings or upload messages to a server.

## Establish the archive and the actual destination

Identify the selected archive or package, its originating app/export if known, and the computer, OS user, installed mail client and version that should display it. Distinguish classic Outlook from new Outlook, and an actual MBOX export from an app's live mail-store folder. A filename extension alone does not establish compatibility.

Resolve whether the user wants to browse the entire selected archive, find particular historical messages, or have the archive available for ongoing local search. Ask only about choices that change the operation. If the request instead requires the old messages on a phone or in webmail, explain that local access does not satisfy it; establish the intended account and upload scope separately.

Check the intended local storage location and capacity. Include space for a working copy, the consumer's imported store and indexing where relevant; do not invent a universal size multiplier. Confirm that the chosen path is not a cloud-synced or shared folder when the user requires local-only storage. A folder called Documents is not necessarily local-only.

Respect work-data restrictions and the approved device. Do not upload an archive to a converter, support portal or assistant-side service to make it easier to inspect. Installing software, adding an account, granting access, accepting new terms or paying for a prerequisite is not incidental archive opening. If the chosen client cannot perform the requested local operation, report the exact missing capability instead of silently switching clients or importing into an account.

## Preserve the source before connecting it to a client

Keep the supplied original untouched and use a distinctly named working copy in the approved location. Copy the complete selected package, not only its visible message file. Confirm that the copy finished and that its bytes or package members match the stable source using available supported checks. Record the source/copy locations and a digest when available; a matching digest proves copy identity, not export completeness or trustworthy contents.

Do not copy a mail database while another application is actively writing it and call that a consistent archive. Obtain a stable, supported export or a safely closed source first. Preserve unsaved work before any requested closure. An online-only file or incomplete download is not an available archive merely because its filename appears.

Keep the source copy separate from the working store. Attaching a data file is not a promise that the client will leave every byte unchanged, and imported read flags or other local state may change during use. Do not require a writable client store to remain byte-identical after opening; instead retain the original and compare the content properties the user needs.

Inspect the selected format without executing attachments or following message links. For a compressed delivery, use [archive extraction planning](../review-archive-extraction-plan/SKILL.md) before unpacking it. Do not overwrite an existing archive, replace a client profile, copy files into undocumented internal database paths or rename an unsupported format to `.pst` or `.mbox`.

## Choose local access, not an account import

Consult current official documentation for the installed version and inspect the actual operation before committing. Preserve unrelated accounts, default delivery locations, special-folder mappings, rules and queued outbound work. If launching or reconnecting the selected client would release known pending messages, resolve that effect first; do not send or delete them as part of opening an archive.

### MBOX or Apple Mail exports in Mail on Mac

[Apple's import instructions](https://support.apple.com/guide/mail/import-or-export-mailboxes-mlhlp1030/mac) distinguish Apple Mail exports from messages supplied in MBOX format. Use File → Import Mailboxes and select the source type matching the supplied material. Apple documents a resulting Import mailbox; identify the actual new mailbox rather than assuming an older mailbox with that name belongs to this operation.

Verify that the result is in the intended local store. [Apple distinguishes On My Mac storage from server mailboxes](https://support.apple.com/guide/mail/change-mailbox-behaviors-settings-cpmlprefacctmbox/mac). Do not drag the result into an IMAP, Exchange or other account mailbox to tidy the sidebar: that changes the destination and can transfer historical messages to that service. Leave a clearly identified local import in place unless further organization is requested.

MBOX has implementation-specific variations. [RFC 4155](https://www.rfc-editor.org/rfc/rfc4155.html#section-2) describes differing separators, escaping and encodings; it is not evidence that every file named MBOX is interchangeable. Do not count messages by splitting text at every `From ` line, concatenate archives, or globally rewrite separators to force an import. If the native importer rejects the source, retain its error and determine the source format before proposing a separate conversion.

### PST archives in Outlook for Windows

[Microsoft explicitly distinguishes opening a PST from importing its contents into a mailbox](https://support.microsoft.com/en-us/outlook/import-email-contacts-and-calendar-from-an-outlook-pst-file). For local browsing, attach the preserved working copy as a separate data file. Do not choose a mailbox account in an import wizard or drag messages into its folders.

In classic Outlook, the documented route is File → Open & Export → Open Outlook Data File. In new Outlook, use its supported Add file route under Outlook Data Files when available. [Microsoft's opening guide](https://support.microsoft.com/en-us/outlook/open-and-find-items-in-an-outlook-data-file-pst) gives version-dependent prerequisites; inspect those and the installed build rather than assuming every Outlook app, architecture or subscription supports the same operation. Do not install or replace Office, purchase a subscription or weaken settings to resolve a prerequisite without the corresponding authority.

Match the attached store to its actual working-file path, not only its display name. Several files can appear with similar labels. Do not make the archive the default store for new mail or alter existing account delivery settings. Opening the selected PST may expose non-mail folders it already contains; do not import or activate contacts, tasks, calendars, reminders or old draft items as a side task.

If a protected file requests a password, use the supported secure entry or user handoff. Never ask for it in a report or try to defeat protection. An OST, partial cache or unsupported database remains outside this PST route; do not assume an export can be reconstructed merely by changing its extension.

## Verify the archive view before relying on search

Record the source-to-view mapping: selected source, working copy, application/profile, attached data-file path or new local mailbox, and the folders included or excluded. For a small archive, one short note is enough.

After the operation completes, navigate the archive directly rather than relying on a unified Inbox or global search. Check the requested folders and identifiable messages against source evidence where available. Useful anchors include a known older message, a recent boundary message and a message with an attachment or non-ASCII body when those properties matter. Preserve source timestamps and distinguish the original header value from the client's local-time display.

Inspect bodies through a route that does not load remote content, send read receipts, follow links or execute attachments. Do not enable blocked content to make a preview look complete. If existing viewer settings cannot meet that boundary, use an already-supported safe view or hold that check pending the specific permitted change. Local message content can be present even when an external image or linked document is unavailable; record those separately.

For required attachments, verify that the payload is present, not only its filename. When exact fidelity matters and the source exposes comparable decoded bytes, compare size and digest through a nonexecuting reader. Do not open a program, enable macros or import cryptographic keys as an attachment check. An encrypted message can be preserved but unreadable in this client; keep that distinction rather than claiming content loss or successful recovery.

Reconcile meaningful source and destination counts when both are available. Identify whether each count means messages, conversations, unread items, folders or non-mail objects. Matching totals do not prove that the same messages arrived. Use message identifiers together with folder/source provenance and relevant content; do not delete apparent duplicates based only on subject, date or Message-ID. If complete source enumeration is unavailable, report sample coverage rather than declaring a lossless import.

Then check the intended search. Search within the actual archive or its supported scope for a known message that direct navigation already located. Microsoft notes that classic Outlook search scope can omit additional data files. Separate an incorrect scope or still-incomplete index from missing imported content. Do not reimport the archive, rebuild every mailbox or reset the whole search index because the first query returns nothing.

If search is part of the requested result and indexing is still active, continue the relevant supported observation until it completes, fails or requires a specific decision. State what is already browsable and what remains unverified. Avoid claiming that every historical message is searchable from one successful query.

## Recover partial or uncertain results without duplicating the archive

- **Interrupted import or unclear completion:** inspect the exact new local mailbox/store, operation status and available folder/message evidence before retrying. Preserve the source and partial result. Do not import the entire file again into the same population merely because a progress window disappeared.
- **Only some folders are present:** check the selected source and subfolder scope, importer errors and format compatibility. Keep unaffected usable content, but label coverage partial. A new isolated import may be appropriate only after its purpose and duplicate/cleanup effects are established.
- **Wrong store attached:** use the documented close/detach operation on that exact store where safe. [Microsoft's close-file guidance](https://support.microsoft.com/en-us/outlook/open-and-close-outlook-data-files-pst) distinguishes closing a PST from deleting its disk file. Verify the path before any correction.
- **Wrong local import created:** do not treat removing the mailbox as equivalent to closing a PST. Establish exactly what it contains, whether it has acquired later work, its surviving copy and the applicable deletion authority before removing anything.
- **Corruption, unsupported format or missing protection material:** preserve the original and report the precise unsupported operation. Repair, conversion or credential recovery requires a separate scoped plan; do not repeatedly mutate the only source.
- **Unexpected server transfer:** stop further transfers, identify the actual account and affected population, and report it promptly. Do not erase server messages as an assumed rollback or claim removal would retract every downstream copy.

Keep recovery copies and the usable working archive. Do not compact, deduplicate, delete originals or remove old accounts as automatic cleanup. If later work requires moving the attached PST, first use the client's supported close/reopen route and preserve any new local changes.

## Deliver and stop

Return the precise local opening route, source/working-copy identity, folder coverage, observed readability and search result, and any unavailable messages or properties. Keep private message excerpts and full addresses out of unnecessary reports. State whether the result is prepared, attached/imported locally, partially readable, browsable with search pending, or verified for the requested local use.

Finish when the selected historical mail is accessible in the intended local store with the requested checks, or when a specific capability, protection requirement or unresolved outcome blocks that result. Do not call local archive access a full mailbox restore, cloud synchronization or a substitute for a backup.

## Fictional illustration, unexecuted

A fictional user wants to search a PST of an old project on a Windows laptop but does not want that mail added to a current work account. The proposed route preserves the source, attaches a working copy as a separate Outlook data file, and verifies its file path and project folders. A known message appears by direct navigation, but a query in the current mailbox returns nothing.

That result would call for checking the archive search scope and index state, not importing the same PST into the work account. If the client instead offers only a mailbox destination and has no supported local opening route, the task would remain blocked at that capability choice.

This is an invented decision example. No archive, client, profile, message, importer, index, parser or attachment was opened, modified or tested for this guide.
