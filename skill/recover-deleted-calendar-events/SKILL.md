---
name: recover-deleted-calendar-events
description: "Locate and restore selected retained calendar events without confusing a personal entry with an organizer meeting, reviving an excluded recurrence segment, or treating event recovery as recovered RSVPs and room reservations. Use for bounded native event undelete, not calendar-wide rollback, rescheduling or importing old invitations."
---

# Recover the intended calendar event, not a new meeting

Return selected deleted events through the owning service's supported recovery route, or provide an exact recovery finding and blocker. Separate event contents, recurrence membership, attendee responses, resource acceptance and device visibility. A meeting appearing on the user's grid does not establish that the meeting is reinstated for everyone.

Use [calendar-file reconciliation](../calendar-file-reconciliation/SKILL.md) for offline ICS repair and [recurring-series changes](../change-recurring-calendar-series/SKILL.md) for a new scheduling decision. Use [calendar-time diagnosis](../diagnose-calendar-time-displays/SKILL.md) when the record exists but its displayed date or time differs. This workflow is not a mailbox-wide restore, service-booking reinstatement, calendar migration or account-wide historical rollback.

## Establish the recovery target

Resolve from the request and available evidence:

- Service, signed-in account, owning calendar and whether the user is organizer, attendee or authorized calendar editor
- Selected event or series, known original date/time and zone, approximate deletion interval, and useful identity evidence such as a verified event link
- One occurrence, a specific set, or the complete deleted series; include intentionally canceled occurrences that must remain absent
- Locate-only, recover contents for reference, restore a personal entry, or reinstate an organizer meeting
- Whether invitations, attendee-visible reinstatement and resource requests are within the intended action
- Known replacements, recent schedule changes and unsynced work that must remain untouched

For one unmistakable personal appointment, do not demand a complex recovery plan. Ask only when the difference changes scope or consequences. “Find the notes from the deleted meeting” does not authorize restoring a meeting for its guests. “Put this back on my calendar” may refer to an attendee copy rather than an organizer's cancellation.

A clear request to restore an identified ordinary event can authorize its narrow native restore with understood effects. Do not repeat approval merely because the item was found. Resolve additional recipients, consequential content, a larger recurring selection, renewed invitations or broader rollback when those effects are not covered. Locate-only work stops before mutation.

## 1. Distinguish missing from deleted

Use a connected tool only for capabilities it actually exposes. Ordinary event search is not a deleted-event listing or restoration API. If necessary, use the service's supported interface through an authorized browser; do not provision credentials or acquire administrative access to fill a gap.

Inspect the selected calendar's current state and the relevant native recovery location. Compare account/calendar identity, organizer, event identity and original occurrence slot where available. Use the title only as a clue. A forwarded invitation, exported copy, cancellation email and retained calendar object are different records.

Classify the finding before choosing an action:

| Finding | Next step |
| --- | --- |
| Event active in the owning calendar but absent from one view | Diagnose selected calendar, filter or synchronization evidence; do not create a replacement |
| Calendar removed from a personal list or access revoked | Resolve that view/access issue separately; event undelete is not an access grant |
| Exact event present in native deleted state | Identify its restore unit and effects |
| Invitation or attendee copy removed while organizer event remains | Determine the supported personal recovery/response route; do not restore or recreate the organizer's meeting |
| Organizer canceled the meeting | Do not silently revive attendance from an old invitation; establish the requested reinstatement authority |
| Only an old export or invitation remains | Treat it as historical evidence, not a current retained object or proof of an active meeting |
| No retained candidate visible | Record accounts, calendars, time range and listing coverage inspected; absence from a limited view does not prove permanent loss |

Inspect only the information needed to identify the event and assess the requested recovery. Keep private descriptions, attendee addresses and conference links out of broadly shared reports. Do not follow embedded links or open attachments merely because they occur in a recovered entry.

## 2. Check the service-specific recovery unit

The following official references were checked on 2026-10-20. Match the actual product/account and recheck when its controls differ. Do not translate one provider's retention or recurrence behavior into another's.

### Google Calendar

[Google's deletion and restoration guidance](https://support.google.com/calendar/answer/37113?hl=en) documents a separate Trash for each calendar, a 30-day period, and restoration by users with sufficient event-editing permission. On a computer, use Settings → Trash, select the correct calendar and restore the identified row or deliberate selection.

A grouped recurring-deletion row can restore all occurrences represented by that row; it is not necessarily one occurrence. Deleting “This and following” does not put those instances in Trash. When the creator restores an event, guests must RSVP again; a room that is no longer available is crossed out. These limits make restored contents, attendance and room availability separate outcomes.

Inspect the row's actual scope before choosing it. If it includes occurrences the user excluded, hold that row rather than restore everything and delete the unwanted meetings afterward. Do not fabricate an undelete request for absent future instances or present recurrence reconstruction as recovery.

### Outlook

Use the matching New Outlook, Classic Outlook or Web section of [Microsoft's deleted-item recovery guidance](https://support.microsoft.com/en-us/outlook/mail/recover-and-restore-deleted-items-in-outlook). Look first in Deleted Items; where supported, inspect Recoverable Items next. Confirm the candidate is the calendar item, not merely a message about it.

In classic Outlook, Recover Deleted Items From Server restores selected recoverable items into Deleted Items; then move the identified appointment to its intended Calendar folder. The recovery list uses envelope icons for different item types, so icons alone cannot identify an appointment. Account support and retention vary; inspect the available route and policy instead of promising a universal recovery window. New Outlook and Web have different controls and return behavior: verify the actual destination rather than applying the classic two-step sequence universally.

Recover only the intended item, not a mixed selection of messages and appointments. Preserve any returned identity mapping. Stop if the available destination or item type cannot be established without an unsupported conversion.

### iCloud: do not substitute a broad archive restore

[Apple's calendar restoration guide](https://support.apple.com/en-gb/guide/icloud/mm7478c562f3/icloud) describes restoring an archived version of calendars/events together with reminders and lists, not a selected-event Trash operation. It removes sharing information and affects devices using iCloud Calendars; changes made during restoration are not saved.

Do not invoke that route for a request to retrieve one event. Report its broader scope and prepare a separate rollback decision if wanted. Do not temporarily rewind calendars to extract one entry and then rewind again. Re-sharing calendars, requesting invitations and recovering newer work are additional actions, not automatic cleanup. An Apple Calendar client may also display events owned by another provider; use that provider's lifecycle rather than assuming the data belongs to iCloud.

## 3. Establish recurrence and meeting consequences

For a retained recurring item, identify whether the recoverable unit is an instance, master or deletion bundle. Map each requested occurrence by its original slot and current/effective time if moved. Account for preserved active instances, known exclusions and any replacement series. A visible date range alone cannot distinguish an intentional exception from a lost occurrence.

Use a bounded preview for ordinary repeated dates, and inspect the stored exceptions affected by the restore. Do not claim all future dates verified from the next two meetings. If the interface cannot establish the bundle's membership or exception preservation sufficiently for the user's constraint, deliver the identified candidate and hold the restore.

For a meeting with people or resources, establish before acting:

1. Which calendar record will become active, under whose organizer identity
2. Whether the operation sends updates, requests new responses or changes attendee-visible state
3. Whether known cancellations, replaced meetings, conference details or room responses conflict with reinstatement
4. Whether the user wants an active meeting or only its historical contents

Do not copy old acceptance responses as fresh consent, manufacture conference objects, or claim a room reserved from its name in the location field. A provider success message is not evidence of current attendance. If the native operation's communication behavior is unclear and a no-notification condition matters, hold it and explain the specific uncertainty. Do not experiment on a real event to discover those effects.

Avoid downloading and importing old ICS files as a substitute for native recovery. That can create a separate event rather than return the retained one. Do not open an old invitation and accept it merely to make a grid entry reappear. Reissuing an invitation or creating a replacement is a separately scoped scheduling action, with its own identity and communication consequences.

## 4. Restore once and verify independently

Immediately before mutation, refresh the active calendar and selected retained record. Check that another person has not already restored, replaced or rescheduled the event. A same-title replacement must remain separate. Preserve the minimal before-state and operation identity needed to explain what changed, without exporting unrelated calendar data.

Perform the smallest supported authorized restore. Do not choose Select all because search appears to show one result, and do not empty Trash or change retention. Preserve the returned identifiers and any intermediate recovery location. A two-step recovery is unfinished until the calendar item reaches the intended calendar.

Afterward, reopen the event through a fresh calendar view or lookup rather than relying on the recovery dialog. Check:

- Correct account, calendar, organizer and event identity or evidenced returned-ID mapping
- Wanted title/contents, start and end, all-day versus timed meaning, and timezone
- Requested recurrence membership, moved occurrences and exclusions, with the inspection horizon stated
- Preservation of known live replacements and unrelated calendar entries
- Guest, RSVP, resource and conference state as separately observed facts
- Notification evidence, distinguishing an update requested or sent from delivered, read or accepted

If a particular device matters, inspect its normal synchronized view separately when accessible. Server readback cannot certify an offline phone. Do not sign out, clear caches, remove accounts or discard local work just to force the device to match.

## Recovery and completion

After a timeout or ambiguous result, inspect the exact active/retained identity and any intermediate folder before retrying. An item missing from Trash may already be restored; it may also be inaccessible or purged. Do not infer either outcome from disappearance alone, repeat a series operation blindly, or create a replacement while restoration remains uncertain.

If unexpected occurrences or attendee-visible changes appear, stop further writes and report the verified discrepancy. Deleting the recovered item is not harmless Undo: it may cancel the meeting again or remove later edits. Recheck the current state and communication consequences before an authorized correction. Never change response statuses or send explanations merely to make the recovery look complete.

Deliver a concise per-target result: already active, retained and located, restored/read back, contents only, partially recovered, held, unavailable through inspected routes, or outcome unknown. Include a verified non-secret event link where available, calendar and occurrence scope, retained-object mapping, verified content, remaining attendance/resource issues and the exact blocked next action.

Acceptance for event recovery means the intended retained record is active in the intended calendar, the required contents and recurrence scope are checked, and unexpected effects are absent or explicitly reported. If the requested outcome was a fully reinstated meeting, outstanding room/attendee requirements remain outstanding; do not call that broader outcome complete merely because the entry returned. A locate-only result needs no restore. Stop when the requested outcome is evidenced or the bounded supported routes reach a specific permission, capability or scope blocker. Do not promise recovery of unavailable records or start recurring monitoring without a separate need and scope.

## Fictional illustration, unexecuted

A fictional coordinator asks to recover one deleted workshop occurrence for reference, without contacting guests or reviving the rest of the series. Suppose inspection would find a native Trash row representing three deleted occurrences, including one deliberately canceled workshop. The intended result would identify the bundle, retain the requested occurrence's available content evidence privately, and hold restoration: restoring that row would exceed the requested scope. An old invitation would not justify recreating the event under a new identity.

In a different invented case, a user authorizes restoration of a single personal appointment. Suppose the restore response would time out, but a fresh read would identify the original appointment in the intended calendar with matching contents and time. That readback would support recovery without a second restore. If readback were unavailable, the outcome would remain unknown rather than become a new appointment.

These are authored decision illustrations, not observed results. No calendar, mailbox, Trash, recurrence engine, browser workflow, invitation, restore operation or device synchronization was exercised for this guide.
