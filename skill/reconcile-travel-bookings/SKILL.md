---
name: reconcile-travel-bookings
description: "Reconcile selected booking confirmations, changes and cancellations into a current trip itinerary with preserved segment identity, local dates and unresolved connection or lodging gaps. Use for a reliable trip record, not choosing a new trip, buying travel, disruption rerouting or exporting calendar files."
---

# Reconcile bookings into a usable trip itinerary

Create one dependable view of the travel already arranged: where the traveler must be, on which local date, what is actually confirmed and what still needs attention. Keep a compact source/change record behind that view so a forwarded old confirmation cannot quietly restore a superseded plan. The itinerary is a reconciled evidence snapshot, not a guarantee that services will operate.

Use [travel-contingency-options](../travel-contingency-options/SKILL.md) when a known disruption needs replacement choices, [itinerary-packing-checklist](../itinerary-packing-checklist/SKILL.md) for packing and [calendar-file-reconciliation](../calendar-file-reconciliation/SKILL.md) for repairing existing calendar files. This workflow does not book, cancel, check in, select seats, contact providers or change a calendar.

## Establish the bounded trip

Read the supplied records or the relevant authorized booking threads. Identify the trip window, included travelers or traveler groups, origin and final destination, requested output and any already-stated arrival requirements. Distinguish a personal itinerary from a copy meant for a companion or work team. Do not search the user's entire travel history when one journey is specified.

Useful inputs include transport confirmations and tickets, lodging dates, ground transfers, reserved activities, provider change/cancellation notices and user-approved plans for unbooked gaps. Read attachments and the current message text separately from quoted older messages. A calendar entry, receipt or travel-agent summary may supply useful evidence but is not automatically the authoritative current booking state.

Keep booking-management links, reservation codes combined with identifying details, ticket barcodes, passport/identity numbers, payment details and door/access codes out of generated itineraries, source tables and shared copies. Use neutral booking labels and safe source locators instead; do not reproduce an access-bearing link even in a private derivative. Minimize addresses, traveler details and support contacts to the audience's actual need. Existing access to a booking does not authorize sharing it or uploading it to a new itinerary service.

## 1. Identify bookings, services and source versions

Give each relevant source occurrence a stable locator and record its issue/update time where known, retrieval time and affected booking/service. Keep the originals unchanged. A forwarded copy is another occurrence of a source, not necessarily a new booking or revision.

Represent the useful levels separately:

- Booking/order and its provider or agent
- Individual service segment or lodging stay within it
- Covered traveler group when people have different arrangements
- Source version and which fields or segments it actually changes

Resolve identity through the selected records' evidenced relationships. The same service number on another date is a different occurrence. Two travelers on the same train can have different tickets. Different reference numbers may belong to an agent and operating provider for the same service; the same reference can cover multiple legs. Do not deduplicate by title, route or confirmation-code appearance alone.

For each service retain its mode, operator, exact origin/destination location, local dates/times, booked status wording, relevant ticket relationship and source. Keep order submitted, payment recorded, reservation confirmed, ticket issued, cancellation requested and cancellation confirmed separate where the evidence distinguishes them. Do not infer ticketing, a refund or completed travel from a payment receipt.

Classify every selected source as supporting current details, an identical representation, superseded within a proven lineage, relevant historical evidence or unresolved. Preserve a conflict rather than choosing whichever message was received last. A later notice may update only one segment, terminal or traveler, leaving the other fields governed by their earlier evidence.

## 2. Apply changes without inventing a coherent booking

Use explicit provider revisions, linked change confirmations or a clearly scoped user correction to determine the current view. Record before/after values and the evidence for each consequential change. Do not combine convenient fields from competing whole-booking versions without a supported relationship.

A change request or proposed alternative remains pending until supported acceptance/confirmation exists. A cancellation request does not remove the service from the confirmed view as though cancellation succeeded. Conversely, a confirmed cancellation prevents an older active confirmation from being revived as a fallback. Preserve the canceled leg's location in the trip chronology as a gap when onward arrangements still depend on it.

Keep provider records and user intentions distinguishable. If the user says they intend to skip an activity, show that intention without asserting that the reservation was canceled. If only one traveler is affected by a change, preserve the others' arrangements. If the scope cannot be established, hold the affected segment/group while completing the rest.

Check current official provider information when the request or departure proximity requires a current operating update. Record the retrieval time and service/date match. Public operating status and private booking state are different evidence: a flight operating does not prove this traveler holds a usable ticket, and a confirmation does not establish today's gate. Retain stale or inaccessible checks as explicit limits.

## 3. Normalize the travel chronology

Show the local date, clock time and location for each timed event; include a clear zone or offset where crossing zones could confuse the reader. Preserve source wording and map events to instants for elapsed-time comparisons. The [IANA time-zone database](https://www.iana.org/time-zones) tracks changes in civil-time offsets and daylight-saving rules; use date-specific zone information, not the offset currently shown on the author's computer.

Keep departure and arrival dates explicit, including overnight travel and date-line crossings. A printed next-day marker is evidence to interpret with the source convention; do not supply an omitted date solely because a plausible duration results. Resolve ambiguous or nonexistent local times before asserting an elapsed duration. If a source's stated duration conflicts with its times, preserve the discrepancy and identify what must be checked.

Treat lodging check-in and checkout dates as local calendar dates. Count booked nights from those dates, then retain separately stated check-in availability and checkout deadlines. A room booked from Tuesday is not necessarily available immediately after a Tuesday dawn arrival. An overnight flight is not automatically a missing hotel night, and a gap in hotel records does not prove the traveler needs a hotel. Ask only where the intended overnight arrangement affects the usable plan.

Keep transfer pickup, boarding/check-in cutoff, service departure, scheduled arrival and destination arrival as distinct events. Do not turn a provider's arrival time into the time the traveler can leave the terminal. Preserve exact station, airport, terminal or pickup-point identity when known; two locations sharing a city name are not interchangeable.

## 4. Check continuity against supported requirements

Walk through each traveler group's itinerary in chronological order. Identify overlapping bookings, incompatible locations, unfilled ground transfers, arrival before lodging access, checkout before a late departure and a canceled service that strands a still-confirmed booking. Separate a proven conflict from missing information and from an optional comfort preference.

For a connection, compare the available elapsed interval with the specific requirements supported for that journey: arrival processing, baggage collection/recheck, terminal travel, border steps, pickup windows and boarding cutoffs. Retain whether services share a ticket or are separately booked; do not infer protection from their presence in one email. Use applicable official rules and authorized route evidence when needed. No universal buffer establishes connection feasibility.

Track the coverage of each time estimate. A transfer estimate including terminal walking must not have that same allowance added again. Unknown processing or travel time is not zero. A mathematically adequate interval with unknown access or service availability remains conditional; if a known lower bound already misses a hard cutoff, the conflict can be established without inventing the remaining durations.

Do not transmit private pickup addresses, sensitive visit details or the complete itinerary to a new mapping service without authority covering that disclosure. Continue the source-based chronology while an external check is blocked. If a real conflict needs alternative travel, deliver it with the implicated booking labels and route to the disruption workflow only within the requested scope.

## 5. Produce the traveler-facing view

Lead with the next usable sequence and any material unresolved issue. A compact day-by-day itinerary should include the local date/time, service and route, departure/arrival or check-in/check-out locations, current evidence status and a safe source reference where useful. Keep confirmations and tentative personal plans visually distinguishable. Avoid burying a critical mismatch in an appendix.

Include a small action list only for evidenced gaps: what must be confirmed, why it matters and the relevant cutoff if supported. A planned follow-up is not a provider contact already made. Do not schedule reminders, monitor live services or send messages under an itinerary-preparation request.

Keep the source/version map and superseded/canceled dispositions available behind the main view. Do not copy every receipt or private booking field into the readable itinerary. If the user asks for a shared copy, establish its recipients and approved content, minimize it separately and verify access before delivery. A private file is the default output when sharing was not requested.

## Acceptance and recovery

Reopen the saved itinerary and reconcile it to every selected service and material change. Verify that each traveler group's segments appear once in the appropriate current, tentative, canceled or unresolved state; source occurrences must not inflate the service count. Recheck all changed dates, cross-zone intervals, lodging-night ranges, endpoint identities and continuity findings against their evidence. Confirm the output's privacy exclusions and source links.

If updating an existing itinerary, preserve user-added notes and manually arranged segments. Show the affected delta rather than replacing the whole trip with an older import. If saving is uncertain, inspect the destination before retrying. A late provider revision requires rechecking its dependent transfers and stays, not merely replacing one displayed time.

Deliver the actual itinerary, its evidence-as-of time, the consequential changes, open questions and verification limits. Complete the supported parts even if one booking is unavailable. Stop when the requested trip snapshot is saved and checked or an exact identity/time/authority question blocks a dependent portion. Do not claim all travel confirmed, all connections safe or booking changes completed unless the evidence supports those specific conclusions.

## Fictional, unexecuted illustration

A fictional packet contains five source documents: a flight confirmation, a forwarded identical copy, a confirmed revision for the same flight, a rail confirmation and a hotel confirmation. The flight's original local arrival is 07:10; the revision changes it to 08:30 on the same local date. Rail departs at 10:00 with a documented 09:40 boarding cutoff. Supplied planning evidence gives 30 minutes of arrival processing and a separate 85-minute terminal-to-station transfer. The hotel is booked that date with room access from 15:00.

The current view contains three booked services, not five. The earlier flight arrival is retained as superseded evidence. With the revised arrival, station arrival under the supplied estimates is 10:25, which misses the rail cutoff by 45 minutes. The hotel remains booked, but neither early room access nor a replacement train is invented. The itinerary flags the transfer conflict and preserves 15:00 as the known room-access time. No hotel arrival time or need for earlier access is supplied, so that need remains unresolved rather than becoming an asserted lodging gap.

This is an original authored example with fictional records and planning inputs. No booking, provider status, route, account, calendar or transaction was accessed or changed for it.
