---
name: prepare-offline-email-draft
description: "Package approved email content and selected attachments into a local reviewable EML file, preserving MIME structure and decoded bytes while separating file creation from mailbox import or sending. Use when a portable message artifact is requested, not for ordinary wording edits or extracting received attachments."
---

# Prepare an offline email draft for review

Produce the actual `.eml` file and a short readable review of its headers, body and attachments. This is useful when a message must be reviewed or moved between tools as one portable artifact. The hard part is preserving recipients, text alternatives and exact attachment bytes without creating a misleading sent-message record or accidentally opening a delivery path.

Use [professional-message drafting](../draft-professional-message/SKILL.md) when wording is the main task. Use [email-attachment handoff](../email-attachment-handoff/SKILL.md) to extract files from received messages. A normal request for a draft in chat does not need an EML export; use this workflow when the user requests the file or the chosen handoff needs it.

## Establish what belongs in the message

Resolve from the request and supplied material:

- Approved body and subject, sender identity, intended To/Cc recipients, and any separately authorized Bcc routing
- New message versus reply, with the exact source message/thread if threading is required
- Exact attachment files/revisions and permitted filenames; inline resources only when needed by an approved HTML body
- Private output location, review audience and target mail client when interoperability matters
- Whether the task is local preparation only, saving a draft in a specific mailbox, or a separately authorized send

Use an explicit content/attachment selection. Do not attach a whole folder, original private thread or extra “helpful” evidence merely because it is nearby. Inspect attachment sizes and source digests before packaging. Resolve ambiguous revisions rather than choosing whichever file has “final” in its name.

Preparation can proceed without a target client, but claim only a standards-oriented review file until actual client behavior is checked. If sender or recipient identity remains unresolved, keep the supported text and manifest, ask the smallest needed question, and do not invent an address. An intentionally incomplete EML draft must be labeled incomplete, not transport-ready.

Treat the EML itself as potentially sensitive: it contains readable addresses, body text and attachment payloads. Bcc names embedded in a file are visible to anyone who can inspect that file. For a review copy, omit Bcc by default and keep any authorized routing note in the user's private review context. If Bcc must be embedded, verify that the file's audience is permitted to see it.

## Construct semantic parts before serialized bytes

Use a mature MIME/message library with structured header APIs rather than assembling headers through string concatenation. Reject unexpected CR/LF or control characters in supplied single-line header inputs; never let a subject, display name or filename create an extra header. Let the library encode and fold supported Unicode header values. See [RFC 2047](https://www.rfc-editor.org/rfc/rfc2047.html) for encoded words, and the library's current address/header APIs for their valid contexts.

Build only the message the user approved:

- Plain text alone is sufficient when no HTML version was requested
- When both are required, put equivalent plain and HTML bodies in `multipart/alternative`, plain first and HTML last
- For ordinary attachments, place the body or alternative container first inside `multipart/mixed`, followed by the selected attachment parts
- Use `multipart/related` and matching Content-IDs only when approved embedded resources actually require them; do not treat every logo as a separate downloadable attachment

[RFC 2046](https://www.rfc-editor.org/rfc/rfc2046.html#section-5.1) defines multipart relationships and alternative ordering. Avoid treating two body alternatives as two unrelated attachments. Recheck that both alternatives preserve the same important commitments, dates and links, without adding information to only one version.

For HTML, use the approved minimal content and escape inserted text appropriately. Do not add scripts, forms, tracking pixels or remote images. Do not fetch remote content while rendering a review. If the supplied HTML includes those dependencies, hold the affected rendering or prepare an explicitly described sanitized copy within the user's permitted transformations; do not claim a changed copy is byte-identical to the source.

Read attachments as bytes. Assign a suitable media type and attachment disposition, and encode through the MIME library without text-mode newline conversion. Retain source/display filename mappings, but use only safe basenames as attachment names, never absolute paths or home-directory details. Filename parameter encoding is separate from body encoding; do not paste an encoded-word string into arbitrary parameter syntax. [RFC 2183](https://www.rfc-editor.org/rfc/rfc2183.html) describes disposition and filename handling, while [RFC 2045](https://www.rfc-editor.org/rfc/rfc2045.html) describes MIME content transfer encodings.

If the serialized file exceeds the user's or verified target's size limit, report the actual candidate size and options. Encoding increases size; do not silently drop attachments, replace them with cloud links or upload them elsewhere.

## Preserve message identity without inventing history

Keep a new draft's identity distinct from a received message. Never copy `Received`, `Return-Path`, authentication results or a DKIM signature into a newly authored draft as if it had traversed the original delivery route. Do not claim a generated Message-ID authenticates the sender.

For a reply, derive `In-Reply-To` and `References` only from the verified source headers and intended thread. Do not reuse the source message's own Message-ID for the new message. A matching subject alone is not enough to invent thread metadata.

Record when the artifact was prepared in the companion review. If generating a complete message with a `Date` header, use the actual time it was finalized for this artifact and explain that no send occurred; let the sending client set or update origination metadata when the user finalizes the message for sending. Do not backdate the message or use `Date` as a delivery receipt. [RFC 5322](https://www.rfc-editor.org/rfc/rfc5322.html#section-3.6) defines originator, date and reply-identification fields.

Do not promise that an `.eml` extension or an `X-Unsent` header makes every client open a compose window. Check the chosen client's documented import/open-as-draft workflow when that behavior matters. Keep incomplete draft headers and client-specific additions explicitly identified, rather than claiming universal compatibility.

Internationalized mailbox addresses need deliberate target support. Do not transliterate the local part or silently substitute an address. If such addresses are needed, check [RFC 6532](https://www.rfc-editor.org/rfc/rfc6532.html) and the actual consumer's support; otherwise hold that compatibility claim while preserving the user's exact address.

## Save and read back the exact artifact

Serialize to bytes in a fresh file outside mail-client spool, outbox, watched-import and synced/shared folders unless that destination is explicitly authorized. Use the library's email-compatible serialization policy; for Python, [the `SMTP` policy](https://docs.python.org/3/library/email.policy.html) supplies CRLF line endings. A serialization policy named SMTP does not itself authorize or perform a network send.

Python's [EmailMessage API](https://docs.python.org/3/library/email.message.html) supports body alternatives, attachments and byte serialization. Use the installed version's documented interfaces. Do not copy documentation examples that also send mail into a local-only task. No SMTP connection, mail-client launch, `mailto:` action or provider draft creation is needed to write a review file.

Reopen the written bytes using a MIME-aware byte parser, with defects surfaced and an explicit parsing policy. The [Python parser documentation](https://docs.python.org/3/library/email.parser.html) describes the byte APIs; comparable safe libraries are suitable. Reconcile the parsed result against the pre-serialization plan:

1. Sender, To/Cc, subject and any approved threading metadata decode to the intended values, with no duplicate singleton headers or unexpected Bcc disclosure
2. Body content and Unicode survive, including important punctuation, links and plain/HTML equivalence; disclose any deliberate newline normalization
3. MIME nesting distinguishes body alternatives, related resources and attachments, with no extra parts or broken Content-ID references
4. Each selected attachment decodes to the exact source byte length and digest, with the intended filename and disposition
5. The output size, source revision checks and any unresolved parser defects are recorded

An independent reader can strengthen the check when available. Re-parsing with the same library still provides useful readback, but is not independent conformance validation. If parsing or rendering cannot run, report static inspection only; do not infer successful client import from source text.

Use an isolated offline viewer only when its effects are known and within scope. Prevent remote-resource loading and do not automatically open the EML in the user's configured mail application. Client testing should use synthetic material and a safe local context; saving or importing into a live mailbox is an external state change that needs the corresponding authority.

## Recover and hand over

If a decoded attachment differs, identify the affected part and rebuild it from the selected source bytes. If source files change during preparation, refresh those selections and regenerate a new candidate. Do not overwrite the source files or silently accept a malformed MIME recovery as faithful output.

For a missing body alternative, broken inline reference or client-specific incompatibility, correct the precise structure within scope and read it back again. Do not send a test message, upload the file or create a live mailbox draft merely to resolve an offline validation problem.

Return the actual EML file, readable recipient/subject/body summary, attachment list and exact verification level. State “prepared locally, not imported or sent” when that is the completed scope. If a later authorized import is uncertain, inspect mailbox state before retrying to avoid duplicate drafts. Preparation success is never evidence of delivery or recipient receipt.

## Fictional example, not executed

A fictional user requests a local review copy of an approved workshop handoff email, with a plain-text body and exactly two selected files: `setup-notes.txt` and `room-plan.pdf`. Both addresses use the reserved `example.invalid` domain in this illustration. No Bcc, HTML, inline logo or thread metadata is requested.

The proposed MIME structure is:

```text
multipart/mixed
  text/plain; charset=utf-8
  text/plain; disposition=attachment; filename=setup-notes.txt
  application/pdf; disposition=attachment; filename=room-plan.pdf
```

The planned acceptance check compares both decoded attachment hashes with their inputs and checks the decoded recipient and subject. The proposed deliverables are `workshop-handoff-review.eml` and a short private review note. This is an unexecuted design example: no message file was serialized, parsed, imported, sent or delivered, and no attachment bytes or test results are supplied by the example.
