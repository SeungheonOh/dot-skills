---
name: reserve-workplace-resource
description: "Reserve, change or release existing workplace rooms or equipment for one agreed time window, verifying each resource's actual acceptance and preserving the underlying meeting. Use for native internal resource booking, not finding meeting times, provisioning resources, paid venue reservations or recording physical custody."
---

# Reserve a workplace resource and verify its acceptance

Deliver a usable reservation for the requested room or equipment, or the exact unresolved booking state and next decision. Keep an organizer's saved event, a resource request, the resource's accepted reservation and physical access separate. A room name in a Location field does not establish a booking.

Use [meeting-window-coordination](../meeting-window-coordination/SKILL.md) when people still need a meeting time, [configure-shared-calendar](../configure-shared-calendar/SKILL.md) for calendar setup, and [borrowed-item-return-ledger](../borrowed-item-return-ledger/SKILL.md) for evidence of physical handover and return. This workflow uses already provisioned internal resources through their supported reservation interface. Exclude paid venues, resource-policy administration, recurring-series changes, pooled seat allocation and regulated or hazardous equipment. Ordinary office equipment, such as a projector, is in scope when its native booking unit is established.

## Establish the reservation contract

Recover from the request and authorized context:

- Organization/account, acting booker and exact owning calendar or booking service
- Existing meeting/event identity, or authority to create a resource-only reservation
- Resource identity or permitted selection criteria: building, floor, capacity, needed features and acceptable alternatives
- Full date, start/end, regional timezone, and any separate setup, pickup, teardown or return interval
- Whether the request is to find options, reserve, replace, move or release; what existing event fields and reservations must remain unchanged
- Approved resource recipients, ordinary booking content, human-attendee update behavior and any explicitly authorized fallback
- Known approval, check-in, access, collection or release rules and the actual completion condition

Ask only about a gap that changes the action. A request to find a room authorizes inspection, not a hold. A request to reserve a named room for an exact meeting ordinarily authorizes the necessary native request to that resource; do not ask again for unchanged, already approved effects. It does not authorize new human invitees, a changed meeting time, multiple speculative room holds or cancellation of the meeting.

Default to existing no-fee workplace resources with existing access. If a booking exposes a charge, deposit, new contract, access grant or eligibility requirement, stop before that commitment and obtain the separately required approval or handoff. Do not change resource permissions, delegates, conflict policies, security settings or account ownership to make a booking succeed. Do not treat a resource's empty calendar as permission to use it.

## Resolve the resource and the event separately

Use the connected resource directory, official booking catalog or native room picker. Match the stable resource ID/address with its actual building, room label, equipment asset or service-defined unit. Keep same-named rooms in different locations and individual copies of the same equipment distinct. A room list, building, floor or human contact is not itself necessarily a reservable resource.

Read only the metadata needed for suitability. Capacity and listed features are evidence from the catalog, not proof of physical condition, accessible entry or functioning equipment. Do not infer a room's capacity from its name, a projector from a video link, or a physical key from calendar permission. If a stated hard requirement lacks evidence, hold that candidate or report the precise limitation before selection.

For an existing event, verify its organizer, calendar, stable ID, current revision, exact instants, attendees, resource participants, location, recurrence state and relevant content. Determine whether the acting account can make the requested organizer-side change. A guest's editable local copy is not automatically the authoritative invitation. Do not duplicate the event or book from another account to bypass a missing right.

If the selected event belongs to a recurring series, establish its exact occurrence or series scope through [change-recurring-calendar-series](../change-recurring-calendar-series/SKILL.md) before changing a resource. A date-specific display is not proof that the event is an independent one-off reservation.

Some interfaces offer a separate reservation when the existing event cannot be edited. [Google documents a duplicate-event shortcut that creates a single event without guests](https://support.google.com/calendar/answer/143753?hl=en). Such a copy is a separate lifecycle: it may not follow later changes or cancellation of the original. Use it only when that separate reservation, owner, linkage and maintenance responsibility fit the user's authorization; otherwise report the exact organizer-side dependency.

Before adding a resource to an existing invitation, inspect the information it will receive. A room mailbox or its delegates may receive event content; treat them as recipients. Keep ordinary title/time/location sharing within the booking request, but obtain any missing permission before transmitting sensitive agenda text, private participant information, attachment access or unrelated material. Do not strip content from the human invitation or change document permissions silently. A separately authorized minimal resource-only booking can be a supported alternative, not an automatic workaround.

## Check suitability, policy and the complete occupied interval

Create a small candidate record with exact resource, suitability evidence, required interval, availability coverage, observed state and check time. Use free/busy or the booking interface where possible; do not collect other bookings' descriptions or identify the people blocking a room.

Distinguish these questions:

1. Does the resource fit the stated need?
2. Does the visible schedule cover the entire requested occupied interval?
3. Is this booker and request eligible under the applicable policy?
4. Has the resource actually accepted this exact request?

A positive answer to the first three is still a candidate, not a reservation. An unavailable, missing, errored or incompletely returned resource remains unknown or unsuitable according to the evidence; it is not an empty schedule. A busy block need not reveal its cause. Do not describe an unseen policy denial as another person's booking.

For a change, distinguish the selected reservation's own occupancy from other bookings. Exclude only the exact booking's identified contribution through a supported availability view or minimal authorized event evidence. Do not subtract its whole interval from merged free/busy, which may also contain another booking. If the source cannot separate them, retain conflict uncertainty; never release the old reservation temporarily to probe availability.

Consult current official documentation and visible account-specific controls. [Exchange resource policy](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-resource-mailboxes) can restrict eligible bookers, working hours, advance window and maximum duration, and can require a delegate rather than automatic acceptance. [Google also supports resource-manager approval](https://knowledge.workspace.google.com/admin/calendar/approve-or-deny-calendar-room-and-resource-bookings). Treat defaults in documentation as examples, not the selected resource's actual policy. Do not inspect admin settings outside existing authorized read access merely to remove uncertainty.

[Google's room guide](https://support.google.com/calendar/answer/143753?hl=en) limits conflict checks to 12 months ahead. Qualify evidence beyond that horizon; do not infer either conflict freedom or a universal prohibition on booking.

Use explicit start and end instants with the resource location's relevant timezone. Resolve ambiguous or nonexistent local times rather than using the computer's current offset. A date-only or All day control is not a safe substitute for an exact occupied window. If the user requests a whole working day, establish that day's actual hours and the service's supported representation. Show both local dates when the interval crosses midnight.

Keep human meeting time and resource occupation separate. A 10:00–11:00 meeting with fifteen minutes of room setup needs evidenced coverage from 09:45, not merely a note saying “setup.” If the service binds all resource attendees to the event interval, do not extend the human meeting silently. Use a supported resource-specific interval or an explicitly authorized linked reservation; if neither is available, ask for the smallest necessary choice. Never claim an unreserved buffer is secured.

Treat each required resource as its own booking unit. A room with an installed projector may cover both needs when the catalog establishes that relationship; a separate projector resource needs its own acceptance. Do not reserve an extra copy just because the word “projector” appears in the request. If the task needs several resources, establish whether the user permits partial reservations and what to do if the complete set cannot be secured. Native saves across resources need not be atomic.

Select only within the approved rule. If no candidate satisfies all hard constraints, return the constraint or missing evidence and any clearly labeled alternatives. Do not shorten the booking, choose another site, exceed capacity, change the meeting time or alter a policy to create apparent availability. Refresh the chosen interval immediately before submission; the check reduces races but does not lock the resource.

## Submit one supported resource request

For options-only work, stop with current candidates and their limitations. For authorized booking, retain the before-state and use the actual native resource mechanism:

- **Google Calendar:** open the intended event, use Add rooms or Add room booking, select the directory-matched resource and save. For removal, remove the resource from the Rooms list and save the event. The [official room guide](https://support.google.com/calendar/answer/143753?hl=en) describes these controls. Follow the actual client and account, not a guessed label.
- **Outlook:** select the intended event and use the matching client's Room Finder or resource picker. [Microsoft's Room Finder guidance](https://support.microsoft.com/en-gb/outlook/use-the-scheduling-assistant-and-room-finder-for-meetings-in-outlook) supports filtering by location and room characteristics, then sending the meeting request. Choosing a typed location label without the resource binding is insufficient.
- **A supported connector/API:** inspect its schema and documentation before using it. [Microsoft Graph distinguishes location metadata from a resource attendee with the resource's email address](https://learn.microsoft.com/en-us/graph/api/user-post-events?view=graph-rest-1.0). [Google distinguishes the resource flag from that attendee's response status](https://developers.google.com/workspace/calendar/api/v3/reference/events). Use those semantics only when the available tool supports them; never invent a missing parameter or set the resource's response to accepted yourself.

Preserve the event identity, human attendees, meeting time, conferencing details, visibility, attachment permissions and unrelated resources unless the user requested a specific change. Read the complete relevant attendee/resource set before using a replacement-style update. An omitted or truncated list is not authority to remove unseen participants.

Check the effect of Save, Send or Send update in the current client. Creating an attendee-bearing event can send real invitations; [Graph's create-event documentation](https://learn.microsoft.com/en-us/graph/api/user-post-events?view=graph-rest-1.0) states that it sends to all attendees. Use an authorized native update scope where supported, and make unavoidable human notifications explicit when they conflict with the request. Do not suppress a necessary resource request or cancellation merely to avoid email. If the tool cannot satisfy a no-notification constraint, resolve that conflict before submission.

Retain the returned event/reservation identity and observation time. Use a supported stable operation identity for uncertain retries, but do not manufacture a second booking as a test. A resource request remains a real pending request even when a response is slow.

## Verify resource acceptance against the saved request

Reopen the exact organizer event or booking through its supported interface. Check the final resource IDs, full reservation interval, owning account, current event revision and unchanged human-event fields. Then read each resource's response or provider reservation result. Use a matching official response or authorized resource-calendar record as corroboration when available; never require broader calendar access merely for additional proof.

Keep these result states separate:

| State | Evidence and claim |
| --- | --- |
| Candidate only | Suitability/availability observed; no request submitted |
| Requested, pending | Submission is established, but resource acceptance is absent, tentative or awaiting a delegate |
| Confirmed | The correct resource accepted the exact current interval/request, with current readback |
| Declined | An evidenced rejection, with only the supported reason and allowed next option |
| Partially confirmed | Some resources accepted; list each remaining pending, declined or unverified unit |
| Outcome unverified | A write may have occurred but its durable state or acceptance cannot be established |
| Released | The exact reservation's removal/cancellation is supported, with any remaining uncertainty stated |

A top-level event status, organizer success message, participant RSVP or green availability tile is not resource acceptance. A read response that omits the resource cannot establish its response. In Google, the event's status and each attendee's response are separate fields in the linked Events reference. Do not initialize or overwrite an attendee's response to create the evidence you need.

Match acceptance to the actual current request, not a similarly titled event or an older interval. If the event changed after the accepting response, obtain current evidence of the resource result. [Google explains that changing an event's time releases the booked room and attempts a new booking](https://support.google.com/calendar/answer/16107253); it can fail. The same guidance notes that rooms can be declined later and that secondary-calendar bookings may have no email notification. Therefore neither an old acceptance email nor absence of rejection mail is sufficient readback.

Check for automatic resource substitution when the service exposes it. A different accepted room does not meet a request for one exact room unless substitution was allowed and its requirements still pass. Do not silently certify the substituted resource from the original room's features. Report any physical-access or check-in condition separately from reservation acceptance. Never mark a room occupied, collect equipment, or check someone in merely to test the booking.

If the user asked for a completed reservation, keep a pending acceptance open for reasonable supported read-only checks, using the provider's processing or approval state and the meeting's useful decision window. Do not turn pending into confirmed after an arbitrary delay. Stop dependent work when a required human decision, unavailable read path, explicit user cutoff or no-longer-useful time window blocks completion, and report that exact blocker. Do not send a reminder to a resource manager or create recurring monitoring without the required scope.

## Change or release without losing the underlying meeting

For an explicitly requested move or replacement, re-read the source event and old reservation, check the new candidate, and identify whether the provider releases the old reservation before it can accept the new one. Do not promise an atomic swap. If a user requires “keep the old room until the new one is confirmed” and the interface cannot guarantee that without a second real hold, ask about the supported tradeoff before mutating. Do not stockpile alternatives.

Apply only the requested resource/time change through the authoritative event or reservation. Verify both outcomes: acceptance of the new resource/interval and release of the old one. Restoring the old event values is another reservation attempt and may fail if someone else has taken the slot; it is not guaranteed rollback. Preserve concurrent organizer edits rather than overwriting the whole event from a stale snapshot.

For “release the room, keep the meeting,” remove/cancel only the resource booking through the supported route. Retain the human invitation and online meeting. For a separate resource-only reservation, cancel that exact object and keep its linked human event. [Microsoft's cancellation guidance](https://support.microsoft.com/en-us/outlook/cancel-a-meeting) distinguishes an organizer cancellation from deleting an invitee's own calendar copy. Deleting a local copy or clearing the location text does not by itself establish resource release.

Use current per-reservation cancellation/removal evidence. A free/busy interval still appearing busy may belong to a new booking; an empty interval alone does not prove that this request was canceled. If release was submitted but cannot be verified, label it release pending/unverified rather than repeatedly removing or canceling events. Do not cancel other people's reservations, delete the resource calendar, change event retention or abandon a partially accepted set without reporting its actual state.

## Recover uncertain results and deliver a usable receipt

After a timeout, first inspect the exact event/reservation, resource set, interval and response. If the intended state already exists, continue verification instead of retrying. Retry only after the current state establishes that the same authorized operation is still needed and the supported route is safe. If several possible copies exist, stop creating and reconcile identities. Ask before deleting an unintended duplicate when cleanup authority is absent.

For a partial resource set, continue only the missing authorized request or approved fallback. Keep confirmed resources visible while resolving the blocked part. Do not say the meeting is equipped or the whole set reserved until every required unit is confirmed. If a decline has no clear reason, report the rejection without inventing a capacity, permission or conflict diagnosis.

Return a concise private receipt with:

- Confirmed, pending, partial, declined, released or unverified state for each requested resource
- Exact building/room or equipment label and the verified event/booking link when safe
- Full local date and occupied interval with timezone, including any different setup/pickup interval
- Owning event/reservation and any separate linkage the user must maintain
- Acceptance/release evidence and check time, plus meaningful suitability or access limits
- Any stated check-in, collection, return or no-show requirement and the precise remaining action

Avoid public directories of internal resource addresses, unrelated booking details or credential-bearing access links. Complete options work with honest candidates; complete booking with current exact-resource acceptance; complete a change with both the new reservation and old release established. A confirmed booking is a point-in-time resource commitment, not proof of attendance, physical possession, working equipment or permanent future availability. Do not continue into building access, purchasing, equipment operation or unrelated scheduling.

## Fictional, unexecuted illustration

An invented coordinator asks to reserve “Workshop Room 4” and “Projector P-2” for an existing one-off event on 22 October, 10:00–11:00 Europe/London. The named room is in the South building; a same-named North-building room is out of scope. The request includes the ordinary resource notifications, preserves the human invitation, and permits no alternate room or time.

The hypothetical room responds accepted, while the projector requires a delegate and remains pending. The expected receipt says the room is confirmed and the required projector is pending; it does not say the whole setup is ready. A success banner on the organizer event cannot fill that gap. If submission timed out, the next step would be to read this event and both resource responses, not create a second reservation.

In a separate invented variation, fifteen minutes of setup are required, but the native event binds resources to the human meeting interval. The agent must resolve how to reserve 09:45–11:00 without moving the human meeting before claiming setup coverage. In a later release request, removing only the room must leave the meeting and projector untouched. An older room acceptance for 10:00–11:00 would not prove acceptance if the event were moved to 11:00–12:00.

No resource directory, calendar, booking, notification, physical check-in or downstream application was queried, changed or exercised for this illustration. The expected decisions above are fictional reasoning examples, not execution or test evidence. Provider references were consulted on 2026-10-17; recheck the relevant client and organization rules when applying them.
