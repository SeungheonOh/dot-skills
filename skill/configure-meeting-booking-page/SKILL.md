---
name: configure-meeting-booking-page
description: "Prepare or configure a single-host meeting-booking page with scoped availability, calendar conflict rules and bounded booking effects, preserving shared settings and existing appointments. Use for native self-service scheduling setup, not booking one meeting, team routing, payments or building a scheduler."
---

# Configure a meeting-booking page

Deliver the requested booking-page setup, or a complete provider-specific proposal when saving or exposing it is not authorized or supported. The useful result is a page whose offer, availability rules and future booking effects match the user's intent. An empty calendar, a copied URL or a saved availability schedule alone does not establish that result.

Use [meeting-window-coordination](../meeting-window-coordination/SKILL.md) for choosing or inviting people to one meeting, [change-recurring-calendar-series](../change-recurring-calendar-series/SKILL.md) for existing recurring events, and [map-team-coverage-windows](../map-team-coverage-windows/SKILL.md) for a read-only coverage map. This workflow covers ordinary single-host, one-booking-per-slot meetings. Multi-host allocation, group capacity, room reservation, paid services and regulated appointment intake need their own requirements and authority.

## Establish the booking offer and action boundary

Resolve the following from the request, current page and authorized context. Preserve established values for an edit rather than reopening every choice.

- Account, host identity, provider and exact existing page/event-type ID, or the requested new page
- Meeting purpose, duration, location/conferencing method and intended booker audience
- Preparation, private configuration, enabling booking or sharing the link; distinguish these effects
- Weekly hours and their regional timezone, dated overrides, breaks and the intended active dates
- Minimum notice, maximum advance window, start-time spacing, buffers and booking limits when specified
- Already connected calendars to check for conflicts and the calendar receiving new bookings
- Approved page content, intake questions, guest permissions and ordinary booking/cancellation notifications
- Fields that must remain unchanged, linked schedules or account-wide settings, and existing appointments to preserve

Ask only for missing decisions that change availability, exposure or commitments. Do not infer willingness to accept meetings from free time, invent working hours or assume that an existing profile makes every personal detail suitable for the page.

An active booking page offers future meetings and may send confirmations automatically. Authorization must cover that offer, audience and ordinary information sent to future bookers. A draft request does not authorize activation. If saving immediately exposes the page to anyone with its link, establish that visibility before saving; an unadvertised link is not a private draft. Do not require another approval when the request already covers these effects.

Use the connected tool if it supports the exact native operation. Read-only calendar access may not include booking-page settings. Do not add OAuth grants, reconnect accounts, expand calendar sharing, install an integration or change security settings as an incidental workaround. If new access is required, identify the provider, calendars and access requested and use the applicable approval flow. Continue preparing the settings without claiming they were applied.

## Inspect the settings that actually control this page

Capture a minimal private before-state: page identity and visibility, current fields, availability-source ID, assigned consumers, calendar bindings, limits, dated exceptions and capture time. Retain only the information needed to make and recover the scoped change. Free/busy intervals usually suffice; private event titles and absence reasons do not belong in the setup record or page.

Separate these objects instead of treating them as one calendar:

1. The booking page or event type describing the meeting
2. The reusable availability schedule, which may feed several pages
3. The conflict-check calendar selection and connection state
4. The destination calendar for confirmed bookings
5. Existing bookings and any rules retained with them

Check current official documentation and the actual account's controls before translating the request. Features, roles and plans differ. [Calendly's schedule guidance](https://calendly.com/help/how-to-set-your-availability) distinguishes shared schedules from event-specific custom hours and notes that schedule edits can save automatically. Identify every linked page before editing a shared schedule. For a one-page request, use a supported page-specific setting or separate schedule without changing other consumers. Creating a separate schedule is useful only if the correct page is actually assigned to it.

Calendar bindings can be broader still. [Calendly's connection documentation](https://calendly.com/help/connect-your-calendar-to-calendly) describes account-wide calendar connections and one destination calendar. Do not promise a per-page destination when the account cannot represent one, or silently change all other pages' destinations to satisfy one request. Report the exact mismatch and a supported choice.

Inspect which changes autosave, whether a new page begins active, and whether a control affects existing appointments. Preserve stable page links where possible. Do not delete and recreate a page merely because its present configuration is inconvenient.

## Translate availability without changing its meaning

Build a compact settings map: requested rule, native control, effective scope, proposed value and any mismatch. For a small edit, record only the changed fields and their dependencies.

Keep the schedule's timezone separate from the booker's display zone. Weekly 09:00 local should follow that region's date-specific rules, unless the user instead requests a fixed UTC instant. Check relevant clock changes, overnight windows and travel-date exceptions. Resolve ambiguous or nonexistent local times; do not substitute the computer's zone or today's offset. A location-locked display may be appropriate for an in-person meeting only when it matches the requested location and behavior.

Distinguish weekly hours, date-specific replacement/addition rules and explicit closed dates. Confirm the provider's precedence rather than assuming an override is intersected with weekly hours. Preserve unrelated overrides. An end date, a rolling advance window and minimum notice are separate restrictions: the rolling window moves as time passes and is not a fixed expiry. [Google's availability guidance](https://support.google.com/calendar/answer/11423292?hl=en) describes these separate controls and allows adjusted availability outside a recurring schedule's start/end range. Inspect dated exceptions at both boundaries before claiming a finite offer has ended.

Duration and start-time spacing are different. Thirty-minute appointments offered every fifteen minutes do not imply fifteen-minute appointments or permission for overlapping bookings. Check the last usable start and the end of the meeting, not only the first displayed slot.

For buffers, establish before/after duration, which existing events they consider, whether they must fit inside declared hours, and whether they are retained on existing bookings. [Calendly documents](https://calendly.com/help/how-to-use-buffers) that buffers can extend beyond availability hours and that changing event-type buffers does not automatically update previously booked meetings. If the user's full work interval must remain inside a boundary, a buffer setting alone may not meet it. Prepare a supported narrower meeting window or ask about the discrepancy; do not reduce the required buffer or alter existing bookings silently.

For limits, establish their counting scope and period: this page, all event types, host, or another documented unit; date-of-meeting versus date-of-booking; and the relevant day/week boundary. [Calendly's meeting-limit documentation](https://calendly.com/help/how-to-set-meeting-limits) separates event-type and host-wide limits. Keep an existing broader cap intact, and do not report a page-specific daily cap as limiting all meetings on the calendar. Leave unsupported counting details unresolved instead of reverse-engineering a confident promise from a label.

## Reconcile conflict checks and visible content

Confirm every requested conflict calendar is selected and readable by the booking provider, not merely visible to the assistant. Keep the destination calendar and conflict-check list explicit even when they happen to match. A missing or stale connection is unknown availability. Do not turn conflict checking off to make slots appear or mark an existing event free without authority.

Determine how the provider treats all-day, busy/free, tentative and unaccepted events, existing bookings, holds and any priority rules. Do not carry one calendar client's semantics into another booking engine. If official guidance or the observed controls disagree on a status that matters, retain that uncertainty and withhold the affected readiness claim until supported evidence resolves it. Do not manufacture bookings or change event status just to probe the behavior.

Inspect the booker-facing title, host identity, description, location, timezone behavior, form questions and confirmation content. Keep private calendar names, reasons for blocked time, personal phone numbers, home addresses and internal links out unless their disclosure is authorized. Use only necessary ordinary intake fields. Do not add sensitive questions, recording, payment collection, marketing opt-ins, extra reminder sequences or third-party workflow actions merely because a template includes them.

Review existing integrations and notifications that will fire for this page. A new page copied from an old one may inherit more than its hours. Preserve unrelated automation; hold activation if an unintended inherited effect cannot be isolated within the request. Native mandatory confirmations may fit the authorized booking offer, while unrelated follow-up campaigns do not.

Treat visibility controls literally. [Calendly's hidden-event setting](https://calendly.com/help/how-to-fine-tune-your-availability-settings) removes a page from its public listing but still permits direct-link booking. [Google's schedule-editing guidance](https://support.google.com/calendar/answer/10730791?hl=en) likewise distinguishes hiding a schedule on the owner's calendar from stopping bookings. Do not call either action access restriction or deactivation. Changing the account name/photo, publishing a website embed or sending the link elsewhere is separate from configuring the selected page.

## Apply and verify the authorized setup

For proposal-only work, deliver the settings map, page copy, unresolved decisions and expected checks without creating provider state. For an authorized configuration, re-read the target and shared dependencies just before editing. Reconcile concurrent changes instead of replacing the whole object with an old snapshot.

Make only the mapped changes. Order them so incomplete content or overly broad hours do not become bookable accidentally. Use an actual inactive/draft mode if available and authorized; do not substitute a hidden listing. If the interface cannot keep an intermediate state from becoming live, describe the smallest safe save sequence and resolve any material exposure before starting.

After saving, reopen the exact page settings and read back the effective values. Verify the correct availability source is assigned, the intended calendars remain selected, dated exceptions survived, and shared consumers or account-wide settings outside scope are unchanged. Read a changed live value rather than treating a success banner as proof.

Inspect the actual booker-facing page or supported preview without submitting a booking. Use a bounded observation record with date, viewer timezone, check time, expected result, observed result and limits. Select cases relevant to the changed rules:

- A supported opening and a known closed or busy interval
- An override date and the first/last permitted dates
- A minimum-notice or advance-window boundary relative to the check time
- A last slot whose meeting or buffer approaches the working boundary
- A relevant timezone transition or second display zone
- An existing limit or conflicting page that could suppress an apparently open time

Do not create busy events, fill a booking quota or cancel a real appointment to construct these cases. Use existing authorized evidence and native explanations; otherwise report that case unobserved. A slot list is a point-in-time offer, not a reservation or proof of conflict-free future operation. Opening a slot may itself hold it in some services: use a non-mutating preview, or stop before the first reservation action when its effects are unclear.

Separate configuration readback, rendered slot checks and actual booking/notification evidence. The first two can complete a setup request without an unsolicited end-to-end test. If a real booking test is requested, establish its exact host, test invitee, content, time, notifications and cleanup authority first. Treat the resulting event as a real commitment until its authorized cancellation is verified; never repeatedly submit after an uncertain response.

## Recover and hand off

After an uncertain save, inspect the exact page and any newly created schedule before retrying. Do not create a second page because the first response was lost. If only some settings changed, report the actual active state and finish or restore only within the existing authority. A restoration can reopen booking times, so check its effects and later user edits before applying it.

Keep existing bookings separate from future availability. Reducing hours does not establish that accepted meetings were moved or canceled. [Google's cancellation guidance](https://support.google.com/calendar/answer/10737245?hl=en) distinguishes deleting an appointment schedule from canceling its bookings: deleting the schedule breaks its page link while booked appointments remain. Do not use deletion as a general pause, migration or rollback shortcut.

If an incorrect live offer is discovered, stop further activation, sharing and test actions; promptly report the affected rule and what is actually exposed. Use an already-authorized narrow correction or pause, or request the specific missing authority. Do not contact bookers, cancel appointments or broaden access to repair the setup silently. Preserve any bookings made during the change as real records needing a separate decision.

Return the verified page link when available, host/account, concise effective settings, visibility and active state, preserved shared dependencies, check coverage and remaining gaps. Label the result prepared, saved/read back, slot-preview checked or blocked according to evidence. Include the supported way to edit or stop future bookings without implying that existing appointments disappear. Stop when the requested setup and bounded checks are complete; recurring monitoring or distributing the link requires its own scope.

## Fictional, unexecuted illustration

A fictional host wants one 30-minute review page available from 09:00 to 12:00 in their specified regional timezone, on two named dates only. They require fifteen minutes after each meeting to remain within those hours. An existing reusable schedule also serves a separate mentoring page, and a previously booked review at 11:30 already exists.

The proposed configuration uses date-specific hours assigned only to the review page, with no unintended weekly openings. Because the hypothetical provider allows buffers outside availability, the meeting window ends at 11:45; a 30-minute start grid therefore offers no start later than 11:00. The packet retains the mentoring schedule and flags the existing 11:30 booking for a separate decision rather than claiming the new rule changed it. The host's private calendar blocks are checked only through the approved provider binding.

The expected handoff distinguishes prepared rules from actual saved settings and observed slots. A page hidden from a public listing remains direct-link bookable if that is the provider's documented behavior, so it cannot satisfy a request for a private draft. No page, schedule, calendar, booking, notification or preview was created, changed or exercised for this illustration.
