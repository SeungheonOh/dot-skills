---
name: serialize-a-utc-calendar-event
description: "Prepare a valid calendar file from an agreed event interval while preserving time-zone interpretation, text escaping and import limits."
---

# Serialize a UTC calendar event

## When to use

The date and interval are already selected and the user needs a portable .ics event; this does not find availability or send invitations.

## Required inputs

- Exact start/end instants or local dates/times with IANA zones and resolved ambiguity
- Event title and only the authorized optional details
- Whether this is a new event, an unchanged re-export or an update with a known UID and revision evidence

## Workflow

1. Resolve the interval to UTC using current zone data. For repeated or nonexistent local clock times, obtain the intended offset/instant rather than guessing. Confirm end follows start and preserve date rollovers.
2. For a new event generate a UID; for an update preserve the known event identity and applicable revision semantics. Do not invent attendees or organizer addresses.
3. Serialize UTC DTSTART/DTEND with Z and a revision-supported UTC DTSTAMP. Escape text backslashes, commas, semicolons and line breaks so user text cannot inject calendar properties.
4. Fold content lines by UTF-8 byte count without splitting a code point. Use CRLF and the required VCALENDAR/VEVENT structure under RFC 5545.
5. Parse the result independently when available and compare the recovered instants and text with the approved input. Save a new file; do not import or send invitations without authorization.

### Preserve event identity and text safely

Use a structured event record before serialization: title, UTC interval, source local interval/zone, UID policy and permitted optional fields. For an update, identify the existing event instead of generating a new UID that would create a duplicate. Recurrence is a separate specification; do not add RRULE because the title sounds recurring.

Unfold the serialized content after writing and compare recovered Unicode text and instants. A calendar parser check confirms syntax and values it exposes, not that a recipient’s calendar accepted or displayed the file. Report actual import separately.

### Keep revision time separate from file generation time

Omit `METHOD` for this file-only profile. [RFC 5545 §3.8.7.2](https://www.rfc-editor.org/rfc/rfc5545.html#section-3.8.7.2) gives `DTSTAMP` different meanings depending on `METHOD`: without it, the stamp records the component's last revision, not each export. For a newly authored event, record its actual creation/revision instant; for an unchanged re-export, retain the established stamp. An authorized revision needs its actual revision time. Record file-generation time separately in the handoff. If emitted, `LAST-MODIFIED` must agree with the no-`METHOD` stamp.

Do not use today's clock or a file's modification time to fill missing historical revision evidence. Hold the update-ready claim until that evidence is resolved; do not quietly switch to a new UID. A valid stamp and preserved UID still do not prove the destination supports updates from imported files.

**Fictional, unexecuted illustration:** an event record was last revised on October 18 at 10:00 UTC. Exporting it unchanged on October 21 retains `DTSTAMP:20261018T100000Z`; October 21 belongs in the export report. Compare the same record across two export dates: UID and revision metadata should remain unchanged. No serializer, parser or calendar was exercised for this illustration.

### Check the narrow UTC output profile

For this single timed-event workflow, require one `VCALENDAR` with one `VERSION:2.0` and one `PRODID`, containing one `VEVENT` with exactly one each of `UID`, `DTSTAMP`, `DTSTART` and `DTEND`. Use basic UTC date-time values such as `20261112T090000Z`, without a `TZID` parameter or numeric-offset suffix. Do not also write an event `DURATION`. RFC 5545's [calendar component](https://www.rfc-editor.org/rfc/rfc5545.html#section-3.6), [event](https://www.rfc-editor.org/rfc/rfc5545.html#section-3.6.1) and [date-time](https://www.rfc-editor.org/rfc/rfc5545.html#section-3.3.5) rules supply the property and time-form constraints; restricting output to one timed event with both endpoints is this workflow's narrower profile.

An all-day `DATE` span is outside this timed profile: preserve its dates and exclusive end instead of converting it to midnight UTC. Fractional-second input also needs an explicit precision decision, since [iCalendar time values do not support fractional seconds](https://www.rfc-editor.org/rfc/rfc5545.html#section-3.3.12). Do not silently truncate the agreed interval. Inspect component counts, property multiplicity and parser warnings before relying on a convenience getter or dictionary that may hide duplicate fields. Recovered values alone are insufficient acceptance evidence.

**Fictional, unexecuted illustration:** a generated draft contains two identical `DTSTART` properties. A tolerant reader could expose the expected start, but the draft still fails the single-property check. Regenerate it from the approved structured record and recheck the saved copy; do not treat that getter's value as proof of a conforming file. No file was generated, parser run or calendar opened for this illustration.

## Output

The .ics file and a short human-readable UTC/local interval summary, with validation and real calendar-import checks clearly distinguished.

## Verification and limits

Test next-day endings, DST transitions, fractional offsets, Unicode line folding and titles containing newlines/delimiters. Generating a file does not establish calendar availability.

## References

[RFC5545](https://www.rfc-editor.org/rfc/rfc5545.html)

## Example request

“Make an .ics for this agreed interval and title. Preserve the stated timezone interpretation, validate the file locally, and do not send invitations or import it into my calendar.”

## Worked example

The fictional request is a new 90-minute event beginning October 2, 2026 at 23:30 UTC, titled “Design, review; A/B.” The interval ends October 3 at 01:00 UTC. In Bangkok it runs October 3, 06:30–08:00 under UTC+07:00.

The event uses DTSTART:20261002T233000Z and DTEND:20261003T010000Z. Its summary escapes the comma and semicolon, preserving the displayed title after parsing. A newly generated UID and the new event record's actual creation/revision DTSTAMP are included; the example does not invent a real recipient or organizer.

The handoff provides the .ics and both time representations, while saying no invitation was sent and no calendar availability was checked. A request to update an existing event would require its established identity.

## Evidence status

The worked example illustrates the stated inputs and reasoning. Unless an execution result is explicitly identified, it is not a claim that external services, real devices or user data were tested. Report actual checks and unrun stages on each use.

