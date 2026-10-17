---
name: change-recurring-calendar-series
description: "Plan and perform a scoped change to an existing recurring calendar series, preserving occurrence identity, exceptions and authorized notification behavior. Use for one occurrence, the full series or a defined future segment; not finding a new meeting time or repairing an offline ICS file."
---

# Change a recurring calendar series without losing its exceptions

Deliver the exact requested calendar change, or a ready-to-apply change map with a precise blocker. The result must explain which occurrences change and which remain intact. A saved master event or a correctly displayed next meeting is not enough to establish that later exceptions, cancellations and attendee settings survived.

Use [meeting-window coordination](../meeting-window-coordination/SKILL.md) when selecting a time is the main task, and [calendar-file reconciliation](../calendar-file-reconciliation/SKILL.md) for an offline `.ics` repair. This workflow operates on an existing series in its owning calendar; changing a personal calendar entry does not reschedule an outside provider's appointment or booking.

## Resolve the series and the intended change

Identify the account, owning calendar, organizer, stable series ID and a known occurrence. A title alone is insufficient when copies, earlier series splits or separate calendars use the same name. Determine whether the user controls the organizer event, has delegated editing rights, or can edit only their attendee copy. Read-only access or a personal copy does not authorize changing everyone's meeting.

Establish the requested before/after fields and one of these scopes:

- **One occurrence:** name its original scheduled slot as well as its current displayed time when moved
- **Entire series:** establish whether past occurrences and existing exceptions are meant to change; do not interpret a casual “from now on” as a historical rewrite
- **This and following:** identify an inclusive boundary occurrence and the intended treatment of later moved, canceled and otherwise customized occurrences
- **A finite selected set:** enumerate exact occurrence identities; do not silently substitute a whole-series update

Resolve a material ambiguity before mutation. For example, “move next week's review” can identify a moved occurrence by its original week or by its actual displayed date. Preserve both facts and ask when they point to different events.

For timing changes, establish the authoritative time zone, desired local clock or fixed-instant behavior, duration, recurrence frequency and end rule. Preserve the existing attendees, reminders, visibility, conferencing, resources and content unless the request changes them. If a field conflict cannot be safely interpreted, complete the source and change map while holding that portion.

## 1. Capture the complete affected recurrence structure

Read the master, relevant linked series segments and exception/cancellation records through a supported interface. Record revision/etag, capture time, recurrence rule, original occurrence keys, effective start/end, exception fields and known notification behavior. Preserve enough authorized before-state evidence for a narrowly scoped recovery without copying unrelated private calendars or descriptions into the report.

Distinguish ordinary generated occurrences from stored exceptions. Absence from a limited list is not evidence of cancellation. A moved exception belongs to its original recurrence slot even if its displayed date lies outside the requested preview window. Retrieve and paginate the metadata needed to account for every existing exception affected by the proposed scope, not only exceptions whose current displayed start falls inside the window.

Do not expand an unbounded recurrence forever. Use a finite preview horizon for ordinary occurrence checks, but separately establish completeness of stored exceptions across the mutation scope. A six-week preview cannot justify dropping an exception six months away. If the provider cannot enumerate or reliably preserve all affected exceptions, hold the broad operation and provide the smallest supported alternative for the user's decision.

Consult the current provider and tool documentation. [Google Calendar documents separate recurring-event and instance identities, with an original start that persists when an instance moves](https://developers.google.com/workspace/calendar/api/guides/recurringevents). It also warns against representing a whole-series change as numerous individual exception edits. UI, connector and API capabilities can differ; an option present in a calendar app is not proof that a particular connector supports it.

## 2. Make an occurrence-aware change map

Prepare a compact map of the proposed effect, retaining exact identity references privately. Include:

- The series and source revision, changed fields and untouched fields
- The scope and inclusive boundary, using original occurrence identity
- A before/after view of ordinary occurrences around the boundary, first and last affected dates when finite, and relevant zone transitions
- Every affected exception or cancellation, its original key, current behavior and intended after-state
- Attendee/resource and notification consequences, unsupported cases, and operation order when several writes are required

Define exception policy field by field. An exception that moved only the time may still need a new location; an exception with a specially chosen location may need that location preserved. “Keep exceptions” is ambiguous when the requested change targets the same field. Do not choose a global exception policy merely because it is easier to implement. Retain known cancellations unless the user expressly asks to restore them.

Keep future segments aligned to the intended recurrence. An original day-of-month rule is different from “last weekday”; changing a start date must not silently shift a weekly interval's phase. A finite count belongs to the actual recurrence definition, not the number of records in an API response. For a split, calculate the retained and replacement portions using the provider's documented count/end semantics; do not copy the original count to both segments and extend the schedule.

For a canceled boundary or an exception moved across the boundary date, select membership by the provider's recurrence identity and the user's intent, not a sort of visible start times. If the provider's supported operation cannot express the intended boundary, show that mismatch before proceeding.

## 3. Check times and practical conflicts

Use date-specific regional time-zone rules. Retain all-day events as dates with the provider's end-date semantics. For local recurring times, verify the local date, clock time, offset and elapsed duration on both sides of a relevant daylight-saving transition. Adding seven fixed UTC days is not a substitute for preserving a weekly local-time meeting.

For an ambiguous or nonexistent local clock time, establish the provider's supported behavior and ask for a choice when human intent remains unclear. Do not normalize to another clock time silently. A fixed-UTC request may intentionally change attendees' local display time; make that consequence visible.

For time changes, check the attending organizer/user, required attendees and resources over the agreed bounded horizon, using free/busy rather than private event titles. Identify the target occurrences' own existing occupancy: a proposed move may overlap the busy block that will move with it. Exclude only an identity-attributed contribution of the exact occurrence being changed, through a supported exclusion or minimal authorized event-level evidence. Do not subtract its whole interval from merged free/busy, which could also contain another overlapping booking. If the source cannot distinguish self-occupancy from other events, mark that interval's conflict status unresolved instead of declaring either a conflict-free slot or a definite unrelated conflict. Never delete, cancel or temporarily mark an event free merely to probe availability.

Also check overlaps within the proposed occurrence set, including preserved moved exceptions: current free/busy does not describe collisions introduced between two future candidate events. Report which dates and calendars were checked and which remain unknown. A finite free/busy check does not guarantee availability for an indefinite series. Do not move conflicting events, add recipients, reserve substitute rooms or shorten meetings unless authorized.

If the user gave an exact time despite known limits, follow that instruction within policy without claiming all attendees are free. If the task required conflict-free dates and evidence shows a conflict or missing required availability, return that decision rather than inventing an acceptable exception.

## 4. Use a supported mutation with explicit side effects

An explicit ordinary rescheduling request can authorize its intended calendar update and normal attendee notifications. Do not ask again merely because planning is complete. Ask when the audience, scope, affected exceptions, room/conference consequences or notification pattern materially differs from the request. A preview-only request stops before saving. Sharing private content, changing access, or sending separate correspondence requires its own applicable authority.

Immediately before the first write, re-read the affected master and exceptions and compare their revisions with the plan. Recheck time-sensitive availability when it is a condition of the request. Do not replace concurrent attendee changes or a newly canceled occurrence with a stale snapshot. Refresh the plan and resolve material new conflicts.

Prefer the provider's native operation for the exact scope. Determine whether a connector updates a master, an instance or a displayed copy before calling it. Do not repeatedly edit individual instances to imitate an unsupported future-series operation. Do not delete and recreate the entire series as an incidental workaround; that can change identity, invitations, responses and conference details.

If the documented route requires splitting a series or several non-atomic writes, establish before execution:

1. The precise old and new series identities or creation correlation, expected boundary and field mapping
2. How existing overrides and cancellations are carried forward without reviving removed meetings
3. Which steps notify whom, alter RSVP state or request resource acceptance
4. The safe order, each step's readback condition and the permitted response if only part completes

A proposed split is a material change when it causes new invitations or drops exceptions the user expected to retain. Explain that consequence and obtain the missing decision. Do not recreate old acceptance responses as if attendees had accepted a new event. Do not copy a conference object into a new series unless the provider supports that reuse.

Keep an operation ledger with preconditions, intended effect, returned IDs and observed state. Use supported conditional writes or idempotency features where available. For full-field replacement APIs, retain all unchanged writable fields required by the actual operation; do not fabricate read-only state or erase attendees from a partial read.

## 5. Verify the saved series, not only the next occurrence

Read the live result back. Verify the exact owner/calendar and series/segment IDs, changed fields and untouched settings. Expand the same bounded preview and inspect all stored exceptions affected by the operation.

Check especially:

- The last unchanged and first changed occurrences, with no duplicated or missing boundary slot
- A moved exception's original slot remains suppressed and its intended effective event remains present
- Canceled occurrences remain canceled; inherited fields and explicit exception fields follow the approved policy
- Recurrence frequency, phase, finite end/count and time-zone behavior match the plan
- Attendees, organizer, resource requests, reminders, visibility and supported conference details have the intended values
- Notification evidence supports the claimed state; saved, notification requested, notification sent, delivered and accepted are different outcomes

For an infinite series, qualify ordinary projection coverage while checking the actual saved rule and complete known exception set. Do not report all future availability or all future application behavior verified from samples.

## Recovery and stopping conditions

- **Timeout or uncertain save:** inspect the exact series, target occurrence, any newly created segment and notification evidence before retrying. Do not create another segment because the first response was missing
- **Partial split:** stop dependent writes, show which segment exists and which boundary is active, and determine whether completion or a narrow restoration is both supported and authorized. Reversing a write can itself send notifications; inspect those consequences before doing it
- **Concurrent change:** retain the new source state and revise only compatible planned fields. Hold conflicting fields instead of overwriting the whole series
- **Exceptions or fields cannot be preserved:** provide the change map and unsupported field/occurrence list. Do not substitute flattening into individual events, wiping overrides or importing an edited ICS file
- **Unexpected notifications or lost resource acceptance:** report the verified state promptly. Do not send an unrequested explanatory message or fabricate attendee acceptance

Stop when the requested update and readback are established, or when a specific unsupported operation, missing decision or uncertain side effect blocks safe continuation. Continue unaffected reporting and provide an exact next action; do not leave a partial update described as a completed reschedule.

## Output contract

Return a verified event/series link where available, the exact change and scope, original and new local times with zone, exception handling, bounded conflict-check coverage and notification status. Include the reusable occurrence/change map for a complex edit and identify any still-pending resource or attendee responses. Keep the report private unless its audience is authorized.

## Fictional illustration, not executed

A fictional weekly review has original slots D1, D2, D3, D4 and D5. D3 was moved to the following day, D4 was canceled, and D5 has a special location. The user requests “Change the location to Room B from D3 onward, preserving D4's cancellation and D5's special location.” Times and attendees stay the same.

The intended map leaves D1–D2 unchanged, changes D3's location while keeping its moved time and original occurrence key, keeps D4 canceled, and retains D5's location override. Ordinary later occurrences inherit Room B. An adapter that discards future overrides during a split does not meet this request without an explicit supported preservation plan.

This illustration supplies symbolic slots rather than asserting real dates or provider behavior. No calendar read, write, invitation, recurrence expansion, availability check or recovery was executed for this example.
