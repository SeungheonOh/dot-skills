---
name: export-date-only-milestones
description: Export bounded date-only milestones or projected charge dates as an iCalendar file without inventing clock times, recurrence rules, reminders or calendar updates.
---

# Export date-only milestones

## When to use

Use when a reviewed list of calendar dates should become a portable calendar file. Examples include renewal reviews, project checkpoints and document-expiry lists. This workflow creates a file; it does not book time, send invitations or import into an account.

## Required inputs

- Validated dates and labels, with supplied versus projected provenance
- A bounded reporting window and any unresolved source conflicts
- Which details may be exported and whether amounts or other fields are unknown
- Identity intent: newly authored snapshot entries, unchanged re-exports or updates to established entries, with revision evidence for retained identities

## Workflow

### Preserve date semantics

Use DTSTART with VALUE=DATE for a day without an agreed clock time. Do not convert midnight UTC into a local instant: that can display on the preceding day elsewhere. For a one-day event, use the following calendar date as exclusive DTEND, also VALUE=DATE. Test month, year and leap-day boundaries.

Retain each reviewed occurrence explicitly when recurrence semantics are uncertain or provider-specific. A list projected using an original-day clamp is not automatically equivalent to a monthly RRULE. Do not generate extra dates or reinterpret a trial milestone as a verified charge.

### Carry uncertainty into the artifact

Distinguish supplied dates, projections and actual completed actions. Use tentative status and transparent availability when the entries are planning references rather than appointments. Keep unknown amounts unknown; zero has a different meaning. Carry concise conflict and duplicate warnings where they affect interpretation.

Omit source URLs, private notes and account details that are unnecessary for the calendar. CLASS:PRIVATE is metadata, not access control: the calendar account or sharing destination still controls visibility. Do not add alarms, attendees or organizer fields without the corresponding intent.

### Choose an identity policy

For an actual update, preserve established UIDs and the consumer's revision semantics. For a standalone snapshot without an established import target, fresh export IDs are reasonable, but disclose that importing another snapshot may duplicate entries. A local row number is not a durable identity across different inventories.

Use a UTC `DTSTAMP` tied to the event revision, not automatically to export time. In this no-`METHOD` profile, [RFC 5545 §3.8.7.2](https://www.rfc-editor.org/rfc/rfc5545.html#section-3.8.7.2) makes it the component's last-revision timestamp. Newly authored entries use their actual creation/revision time; unchanged retained identities keep their established stamp. An authorized revision uses its actual revision time. Keep file-generation time in the handoff; if included, `LAST-MODIFIED` must agree with `DTSTAMP`.

Missing historical revision evidence is not permission to substitute today's time. Hold the affected update-ready entries and identify the missing fact rather than silently regenerating their UIDs. Never treat a file download request as confirmation that a calendar accepted the entries.

### Serialize safely

Escape TEXT backslashes, commas, semicolons and line breaks. Reject unsupported control characters and malformed Unicode rather than silently changing a label. Construct property names and parameters from fixed code, not source text. Use CRLF between content lines.

Fold lines at no more than 75 UTF-8 octets, including the leading whitespace of continuation lines. Iterate Unicode code points so a multibyte character is never split. Bound record count and text lengths before creating the file.

### Require a complete date-only file

Emit one `VCALENDAR` containing exactly one `VERSION:2.0` and one `PRODID`, with one `VEVENT` per reviewed occurrence. Each event needs one `UID`, one UTC `DTSTAMP`, one `DTSTART;VALUE=DATE` and, for this workflow's explicit one-day span, one `DTEND;VALUE=DATE`. Do not also emit `DURATION`. Omit `METHOD` for this file-only snapshot; producing a scheduling message is outside its scope. These container and property constraints come from RFC 5545's [calendar](https://www.rfc-editor.org/rfc/rfc5545.html#section-3.6) and [event](https://www.rfc-editor.org/rfc/rfc5545.html#section-3.6.1) definitions; requiring an explicit end for every milestone is this workflow's narrower output choice.

Check the saved structure and property multiplicity, not only values returned by a convenient parser getter. Date endpoints use basic `YYYYMMDD` values without a `TZID` parameter or UTC `Z` suffix; a date must not acquire a zone simply because the revision timestamp has one. See the [DATE](https://www.rfc-editor.org/rfc/rfc5545.html#section-3.3.4) and [TZID](https://www.rfc-editor.org/rfc/rfc5545.html#section-3.2.19) rules.

**Fictional, unexecuted illustration:** a draft repeats the same `DTSTART;VALUE=DATE:20280229` twice. Recovering February 29 from one getter does not clear the duplicate-property failure. Regenerate from the reviewed occurrence and inspect the saved structure. No file generation, parser execution or calendar import occurred for this illustration.

### Validate and hand over

Parse the exported bytes with an independent calendar library when available. Compare recovered dates, exclusive ends, exact text, event count, status, transparency and UID uniqueness to the reviewed source. Include delimiter/newline injection fixtures and long non-ASCII labels. For an unchanged re-export with retained UIDs, compare revision metadata with the previous record; a later file-generation date alone must not advance it. If a parser is unavailable, state the narrower validation performed.

Disable export when inputs change or a replacement review fails. Keep file generation separate from account import, which needs its own authorization and verification.

## Worked example

A fictional review contains a supplied renewal on February 29, 2028 with an unknown price. Export an all-day tentative entry beginning 20280229 and ending 20280301. Its description says the amount is unknown and identifies the supplied-date basis. It does not invent a midnight billing time or a payment result.

A later March 31 date projected from an evidenced original-day rule is a separate event labeled projected. Replacing that list with an unqualified monthly recurrence could skip or shift dates. The recipient reviews the snapshot before import; repeated fresh snapshots can produce duplicates.

An unchanged re-export of an established milestone last revised October 18 at 10:00 UTC retains `DTSTAMP:20261018T100000Z` even if the file is generated October 21. This fictional timestamp illustration does not represent a generated file, parser check or calendar import.

## Stop conditions and limits

Stop when the file is validated and delivered, or when an unresolved date or export-permission conflict prevents trustworthy output. File syntax validation is not proof of destination privacy, calendar import or billing accuracy.

## Reference

[RFC 5545](https://www.rfc-editor.org/rfc/rfc5545.html), especially content-line folding, TEXT escaping and VEVENT date boundaries.

