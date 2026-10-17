---
name: diagnose-calendar-time-displays
description: "Explain why the same calendar event appears at different times across clients by reconciling event identity, stored time meaning, date-specific zone rules and display settings. Use for a comparison record and narrowly authorized display correction, not rescheduling events, recurrence edits or repairing an ICS export."
---

# Find why a calendar shows the wrong time

Deliver a source-linked explanation of the selected discrepancy and, when requested, a verified narrow display-setting correction. Establish whether the clients disagree about the event's actual instant, merely show it in different zones, or have different event revisions. Do not move a meeting to compensate for an unexplained display offset.

Use [meeting-window-coordination](../meeting-window-coordination/SKILL.md) to select a meeting time, [change-recurring-calendar-series](../change-recurring-calendar-series/SKILL.md) for a requested series change, and [calendar-file-reconciliation](../calendar-file-reconciliation/SKILL.md) for faulty offline calendar files. This workflow diagnoses actual client views without editing event times, sending updates or changing recurrence rules.

## Bound the comparison

Identify one or a few affected events, the relevant account/calendar and clients/devices, the exact displayed dates/times, and what the user expected. Record the event date, observation time and client/version. Establish whether the mismatch appears in the calendar grid, event details, notification, invitation email, widget or a third-party embedded view; these can use different sources and settings.

Resolve the user's desired viewing zone for this task. It may be their current location, home office or a fixed travel reference. Do not infer it from account language, an email domain, the assistant's clock or an approximate location. Retain a regional zone identifier where available; an abbreviation such as CST can be ambiguous and a fixed UTC offset does not describe every date in a region.

Inspect only the selected records and settings. Use event IDs, timing fields and revision information rather than copying private descriptions, attendee details or meeting links into the diagnosis. Calendar screenshots can expose unrelated events; crop or minimize them in any report. Keep the comparison private and do not send an event link or calendar export to an external time-conversion site.

Diagnosis does not authorize event edits, new invitations, account reconnection, calendar import, deletion, system-clock changes or location-permission changes. A specific request to fix a display setting permits only the established setting and scope; seek any additional authority needed for a materially broader effect.

## 1. Prove that the views refer to the same event

Match the provider account, calendar identity, event ID and, for a recurring occurrence, its original occurrence identity as well as effective date. Similar titles are insufficient: an imported copy, subscribed calendar, attendee copy and organizer record can look alike while having different sources or revisions.

Read the current authoritative record through an authorized connector or the owning service's official interface when available. Retain its revision/retrieval time and original timing representation. A web view is another observation, not automatically the authority over a native app; identify which service actually owns the event.

Check whether a later move, cancellation or series exception explains the difference. An invitation email can show an old time even when the current event is correct. Distinguish stale evidence from timezone conversion before changing a setting. If source revision cannot be established, keep that comparison unresolved.

For a missing or moved occurrence, inspect the exact instance rather than comparing the series master with a modified instance. This is a bounded diagnostic read, not permission to expand or rewrite the series. If the problem is actually incorrect event content, return that finding and route the requested correction to the event-owning workflow.

## 2. Identify what kind of time the event stores

Keep the source representation and the displayed interpretation separate:

- A timed event with an explicit instant/offset can be compared in UTC and projected into each viewing zone
- A local time with a named regional zone requires that event date's rules to establish its instant
- A floating local time has no universal instant until a relevant interpretation is established; do not silently assign the assistant's zone
- An all-day event is a calendar date/span, not midnight UTC; preserve the provider's end-date semantics

Record both start and end, the original zone/offset when present, any explicit event zone, and whether a client is showing source-zone details beside local grid time. A label containing an event's original zone need not match the grid's primary zone.

Use the actual event date and current supported regional-zone data, recording the database/runtime version when material. A conversion based on today's offset can be wrong for the event. Retain full local dates and endpoint offsets when the interval crosses midnight or an offset transition. A duration shown as wall-clock difference can differ from elapsed time across a clock change.

If the source gives a repeated or nonexistent local clock time without enough offset/zone evidence, do not manufacture the intended instant. Record the ambiguity and ask for the smallest authoritative clarification. Do not apply a one-hour adjustment merely because the symptom resembles daylight saving.

## 3. Compare source, configured zone and actual rendering

Build a compact comparison record for each selected event/client:

`event/occurrence identity; source revision and time form; viewing-zone setting; expected full local interval; observed interval and surface; observation time; supported explanation or missing evidence`

Read the layers that actually apply to that client:

- Event-specific zone and the owning calendar/service's settings
- Primary/secondary display zones, calendar timezone support or explicit override
- Device timezone and whether the app follows it or uses a fixed zone
- Browser/app profile, account and embedded-view settings where relevant
- Source synchronization or cached revision state

Do not assume locale, date format, operating-system zone, calendar zone and event zone are the same setting. A secondary clock is not necessarily the grid's active zone. An apparently different date can be the correct local projection of an instant near midnight.

Classify the finding:

| Evidence | Finding and next step |
| --- | --- |
| Same source instant; both displays match their configured zones | Expected different views; explain the local dates and the user's preferred display choice |
| Same source instant; one configured override differs from intended viewing zone | Candidate narrow display-setting correction |
| Different event revisions or identities | Resolve revision/source mismatch; do not apply an offset correction |
| Same source and selected zone; observed rendering disagrees with supported conversion | Client/rule-data or rendering issue remains; record version and exact failing event |
| Floating or ambiguous source timing | Source interpretation unresolved; a display change cannot establish intent |
| All-day span differs | Compare date semantics and revisions; do not convert dates through midnight UTC |

This map may expose more than one problem. A corrected zone does not resolve a stale exception, and a successful refresh does not prove the device's clock is right.

## 4. Use the product's actual display controls

Consult current official documentation for the identified client/version. These references illustrate distinct controls; do not apply one product's behavior to another:

- [Google Calendar's timezone guidance](https://support.google.com/calendar/answer/37064?hl=en) separates calendar display settings from an individual event's timezone and notes limitations around changed daylight-saving rules. A change to the event's zone is not the same operation as a display preference.
- [Apple's iPhone Calendar guidance](https://support.apple.com/en-ie/guide/iphone/iph69525c028/ios) describes Time Zone Override as a Calendar display choice. The same page also describes editing an event's zone, which has a different scope.
- [Apple's Mac Calendar guidance](https://support.apple.com/en-qa/guide/calendar/icl1030/mac) explains timezone support and that the selected calendar zone affects new event creation. Consider this side effect before treating a view selection as purely cosmetic.

Do not change the operating system's clock or timezone to compensate for a calendar-only setting. Avoid signing out, deleting an account, clearing the calendar cache, reimporting events or creating duplicate “test” meetings. Those actions can remove unsynced work or alter far more than the selected display.

For diagnosis-only requests, provide the supported correction and stop before applying it. For an authorized setting change, capture the exact prior value, target value, affected account/client and documented scope. If the control also changes creation defaults or other views, disclose the consequence and resolve a material mismatch with the requested scope before saving. Leave event fields and unrelated settings intact.

If source evidence is merely stale, use a supported refresh only within the existing task authority and after checking for unsaved edits or relevant side effects. Do not delete local state to force synchronization. A blocked read remains a blocker, not evidence that the remote event is absent.

## Acceptance and recovery

After a setting change, read the saved value back and reopen the selected event view through the supported interface. Compare the full displayed start/end dates and times with the established source instant and selected viewing zone. Where the reported problem depends on a zone transition, include an appropriate existing occurrence on the other side, with its revision/exception identity checked. Do not create an event just to obtain a convenient probe.

Verify the relevant event fields/revision did not change as a result of this task. If no event revision interface is available, qualify preservation evidence instead of claiming absolute proof. A correct configuration value alone is not a verified rendering fix; a refreshed grid alone does not establish notification behavior on another device.

If the save is uncertain, inspect the setting before retrying. If the display worsens, restore only the captured setting when that remains safe and authorized, without reverting newer user changes. Keep an unresolved client rendering problem tied to the exact client, event date, source representation and observed mismatch. Do not keep toggling unrelated preferences.

Deliver the concise answer, comparison record or private report, any verified setting change and its previous value, and the exact unresolved source/client boundary. State what was observed versus inferred. Stop when the discrepancy is explained and the requested correction is verified, or when a missing source, access, interpretation or product capability prevents further authorized work.

## Fictional, unexecuted illustration

A fictional review is stored as a timed event from 16:00 to 17:00 UTC. Two supplied client records refer to the same event revision. Client A is explicitly set to a fixed UTC+02:00 display and shows 18:00–19:00. Client B is explicitly set to UTC and shows 16:00–17:00. Both correctly represent the same interval; the differing clock numbers do not show that the meeting moved.

If the user wants Client B to use that fixed UTC+02:00 view and specifically authorizes its display setting, the planned correction changes that preference and then checks the same event while preserving its stored 16:00–17:00 UTC interval. The fixed offsets are invented inputs for this illustration, not claims about any region's daylight-saving rules.

No calendar was read, setting changed, event edited, client opened, notification triggered or timezone conversion tool executed for this illustration.
