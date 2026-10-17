---
name: reconcile-event-registration
description: "Reconcile an event's registrations, party replies and attendance evidence into a current coordinator roster with session-specific counts, linked cancellations/transfers and explicit waitlist or identity gaps. Use for attendee-list continuity, not scheduling the event, selecting invitees, issuing tickets or running admission."
---

# Reconcile an event's attendee roster

Deliver a usable answer to “Who has a place, how many places are accounted for, and what still needs the organizer's attention?” Keep a booking, a person's stated intention and an observed check-in separate. A plausible headcount is not enough if its underlying guests, ticket units or session registrations cannot be explained.

Use [event-run-sheet-handoff](../event-run-sheet-handoff/SKILL.md) for operational timing and staff handoffs, [meeting-window-coordination](../meeting-window-coordination/SKILL.md) for finding and inviting people to one meeting, and [export-survey-responses](../export-survey-responses/SKILL.md) when preserving questionnaire answers is the primary deliverable. This workflow produces a private registration/attendance record from existing evidence; it does not decide eligibility, allocate scarce places, process payments or change a registration service.

## Establish the roster boundary

Read the supplied roster, registration export, reply records and relevant organizer rules before asking questions. Establish:

- Exact event and occurrence, session or ticket scopes, event date/zone and the report's as-of cutoff
- The practical use: organizer review, a minimal check-in sheet, session totals or reconciliation after the event
- Source snapshots and their coverage: export filters, included statuses, guest inclusion, pagination, timestamps and any known omitted channels
- What each source row represents: an order, party, attendee slot, ticket, session registration, response or scan
- Existing stable IDs, supported change/transfer links and the authoritative source for registration status versus replies
- Supplied rules for party size, guests, approved places, pending holds, waitlist offers and relevant capacity totals
- Requested format, private destination, approved fields and intended audience if a separately authorized sharing step is involved

Keep the scope proportionate. A six-person dinner can use a compact party/guest list and a few unresolved notes. A multi-session conference needs separate event and session identities, not a larger flat sheet with every row treated as another person. If the organizer's approval or capacity rule is missing, preserve source statuses and withhold the dependent conclusion; do not invent an admissions policy.

Preserve originals and prior roster versions. Read only relevant records, and do not search private attendee identifiers on the public web. Ticket barcodes, claim links and confirmation tokens can grant access; omit them from the working summary and ordinary check-in sheet. Do not collect credentials or replicate ticket credentials as a convenience.

Names and contact details belong only in the requested private working artifact. Dietary, disability, health and minor-related information needs particular care: retain only necessary, explicitly supplied operational facts in an approved restricted view, without inferring a diagnosis or copying free-text disclosures into the general roster. Removing names does not necessarily anonymize a small event. Preparing a roster does not authorize sharing it with a caterer, venue, volunteer or mailing service, inviting anyone, releasing tickets, marking check-ins, changing capacities or contacting nonresponders.

## 1. Recover the right identities and counting units

Namespace every record by its source and event occurrence. Keep the source IDs and locators; assign a stable local row ID only where needed for the artifact. A local ID tracks a record, not a verified human identity.

Separate the layers that actually exist:

- **Order or party:** the purchaser or responder may represent several places and may not attend
- **Attendee slot or ticket unit:** a named or unnamed place belonging to that party, with its own changes when supported
- **Event/session registration:** one person's place in a particular occurrence or session; repeated participation is legitimate
- **Evidence occurrence:** a reply, export row, cancellation record or scan that may describe an already represented registration

Do not collapse records by shared name, email, payment amount or repeated buyer details. One email can coordinate a household or team; the same person can hold distinct session registrations. A repeated source ID in two snapshots may be another observation of one record, while two different IDs may represent separate purchases. Retain competing matches rather than silently choosing the newest or most complete row.

For a party of three with one supplied name, retain the named slot and two unnamed slots if the source's party rule establishes that three includes the respondent. Do not invent guest names, count the buyer as a fourth attendee or interpret “plus two” as “two total.” When the inclusion meaning is unclear, hold the affected quantity. If only party quantities are available, use party-level quantities rather than manufacturing person-level records that imply identification.

Bind quantity to the source's unit. A table booking, family pass or multi-day ticket is not automatically one person or a fixed number of seats. Use an evidenced conversion and keep ticket units distinct from people and session places. Do not claim a unique-human total when reliable person correspondence is unavailable.

Record filters before relying on an export. For example, [Eventbrite's attendee-report guidance](https://www.eventbrite.com/help/en-us/articles/496608/download-an-attendees-report/) exposes event selection and an option to include guests. An export without guests cannot establish a whole-party headcount. Apply the actual provider's definitions rather than assuming every attendee report has the same coverage.

## 2. Reconstruct current state without erasing its history

Apply changes to the exact affected scope and quantity. Keep the original record, change evidence, effective time where supplied, retrieval time and resulting state. A partial party cancellation affects the specified slots, not every ticket in the order. A missing row in a filtered export is not a cancellation.

Use the organizer's established source precedence and version rules. A later-arriving forwarded reply is not necessarily a later decision. If an authoritative registration and a participant reply disagree, preserve both and identify the next question; do not use a generic “latest timestamp wins” rule across unrelated sources.

Keep independent dimensions when they matter:

| Dimension | What its evidence can establish |
| --- | --- |
| Place/registration | Confirmed, pending, held, canceled, transferred or another provider-defined state for the exact event/session |
| Stated intention | Yes, no, maybe or no evidenced reply, attributed to the responder and applicable party members |
| Waitlist/offer | Waiting, offered, expired, declined or converted, with an actual offer/registration link where available |
| Attendance | Recorded check-in/out or a supplied attendance report, with scope, time and coverage limits |

These are explanatory categories, not a universal status dictionary to impose on a service. An RSVP “yes” can be enough for a small invitation-only gathering under the organizer's rule; it need not mean an approval-gated registration was accepted. An attendee's “can't come” message may inform expected turnout while the platform still reserves the place. A payment/refund badge does not independently establish registration or presence; keep money processing outside this workflow.

Link transfers through evidenced old and new registrations, including the event/session and quantity. Keep the old scope's transferred-out record and the destination's current record so the same place is not counted twice. Do not treat a name edit as an additional attendee. When transfer evidence is incomplete, flag the old/new relationship rather than deleting either candidate. [Eventbrite's transfer-report guidance](https://www.eventbrite.com/help/en-hk/articles/549323/view-your-transfers-report/) specifically distinguishes original and new order information after a ticket change; use the actual service's change record when available.

Waitlist membership, a claim offer and a resulting registration require their own evidence. Read the relevant configuration: some workflows create a registration automatically, while others require a response. [Microsoft's waitlist documentation](https://learn.microsoft.com/en-us/dynamics365/customer-insights/journeys/set-up-and-manage-waitlist) describes both modes and separate event/session states. Do not turn an offer into a confirmed place without the applicable state evidence, or demote an evidenced automatic registration merely because no manual reply exists. Preserve a recorded claim deadline with its timezone. Passing that time does not prove the system released a hold when release behavior or a refreshed state is unknown.

## 3. Reconcile totals at the level that matters

Define each summary's population and unit before totaling it. Useful views can include active registered places, separately reserved pending places, waitlisted requests, expected attendance under an explicit reply rule, session registrations and recorded check-ins. Label them so the reader cannot mistake one for another.

For each event or session scope:

1. Account for every selected source record as supporting a canonical record, retained history, duplicate evidence under a justified rule, out-of-scope material or an unresolved match
2. Partition current registration units under the chosen state mapping. Historical change events are not extra places. Show unknown quantities separately from known totals
3. Preserve linked party quantities and slot counts; require agreement where both are known. An unnamed guest can be a known place even though the person's identity is unknown
4. Reconcile event and session views without summing overlapping session participation into unique attendees. Apply prerequisites such as required event registration only when the organizer/service establishes them
5. Compare supplied capacity with the documented capacity-consuming states. Show confirmed places, additional distinct holds and unresolved capacity exposure separately; avoid counting an offer and its resulting registration as two reservations

Where the count and rule are complete, nominal unallocated places equal the supplied capacity minus distinct capacity-consuming units. A negative value is an evidenced oversubscription in that model, not permission to cancel someone. Missing holds, uncertain party units or partial exports make availability unresolved. Do not present a lower-bound known count as a complete headcount, manufacture balancing guests or use an estimated no-show rate to free places.

Capacity arithmetic is only an organizer planning comparison. It does not certify occupancy, safety, accessibility provision or admission rights. A request to reconcile a roster does not authorize selecting who should attend, reordering a waitlist or automatically promoting anyone.

## 4. Keep recorded attendance distinct from registration

If attendance evidence is in scope, match it to exact ticket/registration identities and event/session occurrences. Preserve repeated scans, corrections and check-outs as events; derive a distinct checked-in count only under the source's semantics. A re-entry scan is not another person, and an order-level check-in is not evidence that every party member arrived unless that is what the system records.

Distinguish “no check-in recorded in these sources” from “did not attend.” Offline devices, manual admissions or missing session logs can make the attendance record incomplete. A checked-in flag does not establish time spent, session participation or current presence after a check-out. Historical attendance can coexist with a later canceled registration; show that sequence rather than erasing the scan.

For a pre-event check-in sheet, provide the minimal identifiers, permitted display names, party/session information and blank recording fields the user requested. Mark unresolved identities and registration questions for the organizer. The sheet is a dated working reference, not a replacement ticket credential or a live admission decision. Do not mark anyone present while preparing it.

## Deliver, verify and refresh

Return the actual requested artifact with:

- Event/occurrence, scope, cutoff, source coverage and the few counts that answer the user's question
- A current roster with stable identities, parties/quantities, applicable registration and reply states, and traceable supporting evidence
- Session or check-in views only when needed, with their own units and denominators
- A concise exception list: exact affected record, consequence, missing fact and organizer decision needed
- A change note for updates, including transferred/canceled records and any unresolved newer evidence

Keep the private source/change ledger separate from a minimized operational view when audiences differ. Do not include private replies, sensitive notes, full contact lists or ticket tokens merely to demonstrate provenance. Sharing or uploading requires the actual authorized destination and audience; an inaccessible save location is not permission to use a public alternative.

Reopen the saved version. Recalculate its known quantities and state totals, trace a partial cancellation and any transfer, check that buyer details did not duplicate attendees, and compare event/session totals without double counting. Verify exact IDs and literal text, including leading zeros and formula-looking names in a spreadsheet. Check the saved operational view for unintended fields, hidden sensitive content and stale totals. Confirm originals are unchanged. Static file inspection does not prove a live service was updated or that a check-in system accepted the roster.

For a refresh, preserve the prior cutoff and stable identities, re-read the relevant source revisions and apply each supported change once. Keep user annotations distinct from imported source fields. If the roster changed during preparation, reconcile those edits before a narrow authorized update. If a save times out, inspect the destination before retrying; do not replace a newer roster with an older snapshot.

If a source is inaccessible, an ID match is unresolved or a count rule is missing, finish unaffected portions and label the exact coverage gap. Keep ambiguous rows out of definitive totals while showing their possible effect; do not discard them from the report. Stop at the requested snapshot. Ongoing monitoring, reminders and registration changes need their own scope and authority.

## Fictional illustration, unexecuted

A studio supplies an adult workshop roster for one afternoon, with eight places of capacity. Its rule reserves confirmed places and active unclaimed offers; waitlist-only requests do not reserve a place. Party P1 originally has three confirmed ticket slots T1, T2 and T3; T3 is later explicitly canceled. Party P2 has confirmed slots T4 and T5, one named and one unnamed. A transfer record replaces T8 with T9 in the same workshop; T8 is retained as transferred-out history and T9 is confirmed. The buyer for P2 is not an attendee.

At the stated cutoff, W1 has an active one-place claim offer and W2 remains waitlisted. The current planning view therefore has five confirmed places: P1's two, P2's two and T9's one. W1 adds one distinct reserved place, making six capacity-consuming places and two nominally unallocated places under the supplied rule. Neither T3 nor T8 adds a current place, and W2 adds no reserved place. The unnamed guest remains a real confirmed slot without an invented name.

A later attendance extract has scans for T1, T4 and T9, with a second scan for T9. Under its documented repeated-scan rule, that is three distinct ticket units with recorded check-in, not four attendees and not proof that the two other confirmed places were no-shows. The packet includes the active roster, the transfer/cancellation lineage and the separate offer and attendance views. It neither releases W1's place nor promotes W2.

All identifiers, rules and quantities are invented. This illustration was authored, not executed. No registrations were read or changed, no roster was generated in an application, and no messages, tickets, payments or check-ins were created.
