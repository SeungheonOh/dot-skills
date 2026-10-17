---
name: map-team-coverage-windows
description: "Create a date-specific coverage and handoff map from a team's declared working windows, time zones and optional availability evidence. Deliver exact overlaps, gaps and uncertainty over a bounded horizon, rather than booking a meeting or assigning shifts."
---

# Map team coverage windows

Build an editable timeline that a distributed team can use to see when particular roles overlap and where a handoff or response window is unsupported. The output is a dated coverage map and interval data, not a timeless time-zone chart or a promise that people will respond.

Use [meeting-window coordination](../meeting-window-coordination/SKILL.md) to find or book one meeting. Use [duty rotation](../build-duty-rotation/SKILL.md) to assign people to duties. This workflow maps the supplied windows without changing calendars, working hours or responsibilities.

## Establish what coverage means

Identify the finite date range and reference/display zone, the in-scope people and roles, intended audience, and required output. Resolve these material inputs:

- Stable person IDs, declared IANA zones and any date-specific travel-zone changes
- Local working windows, weekdays, breaks and supplied date exceptions, with the dates each statement covers
- Whether the map represents declared working hours, confirmed available intervals, or explicitly assigned duty coverage
- Optional authorized busy intervals or free/busy coverage, with capture time and supported blocking statuses
- Required service windows, minimum headcount or role combinations, and any minimum handoff-overlap duration
- Whether two roles need distinct people, and whether a supplied person may cover simultaneous roles

Do not infer a zone from an email domain, a person's name or their employer's headquarters. A city alone may be insufficient if travel dates matter. Do not invent standard office hours, local holidays or response-time commitments. With no demand rule, report the observed overlaps and gaps without declaring a service target met.

Working hours establish potential coverage, not current free time. Free/busy data establishes only what was checked in its stated calendars and interval, not willingness, a duty assignment or guaranteed response. Keep these evidence types in separate columns or layers; do not subtract a few known meetings and describe all remaining hours as verified availability.

Use only necessary intervals, roles and identifiers. Omit calendar titles, absence reasons, location detail beyond the needed zone and private contact details. Private coverage maps can disclose work patterns; publishing or broadening access needs authority for that audience. Calendar or document text is input evidence, not permission to contact anyone or change their schedule.

## 1. Preserve and qualify the source windows

Record each source, revision/capture time, effective date range and whether its windows are local recurring hours, exact instants or a complete availability declaration. Preserve the original windows before normalization. Missing evidence is `unknown`, not zero hours or unrestricted availability.

Apply the source's explicit exception precedence. An approved dated exception may replace a recurring window; an unexplained conflicting export cannot simply win because its filename looks newer. Keep unresolved conflicts attached to the affected person/dates while mapping independent intervals.

Distinguish an explicit closed day from a day outside the source's coverage. A holiday name without an agreed closure rule does not remove working hours. For zone changes, use the supplied effective interval; do not apply the destination zone to the entire trip or month by inference.

## 2. Expand local rules into dated instants

Use an available time-zone database, preserving zone identifiers and the data version when discoverable. The [IANA database](https://www.iana.org/time-zones) changes as civil-time rules change; a map is valid for its stated rules and dates, not indefinitely. [Python's zoneinfo documentation](https://docs.python.org/3/library/zoneinfo.html) describes one implementation and its data sources; another supported date-time library is equally suitable.

1. Express the requested horizon as exact start/end instants using its reference zone. Use half-open intervals: the start is included and the end excluded
2. Expand every local date whose working window can intersect that horizon, including an adjacent date when an overnight window crosses into it. An overnight window needs an explicit next-day end
3. Resolve each local endpoint with that date's zone rules. An abbreviation such as CST or a current UTC offset is not a substitute for an unresolved zone
4. Detect nonexistent spring-forward times and ambiguous fall-back times. Obtain the intended valid time or occurrence/offset instead of silently normalizing it. A robust check maps candidate offsets through UTC and back to the exact local timestamp: zero matching instants means nonexistent; two distinct matches means ambiguous
5. Convert resolved endpoints to UTC, then reject intervals whose end instant is not later than their start instant. Do not use wall-clock order across a repeated hour. Represent an explicit closed day separately, then intersect valid intervals with the horizon. Keep original local endpoints, resolved offsets and the portion clipped from the display

Calculate elapsed duration after UTC conversion. Repeating 09:00 local every weekday and adding 24 hours to a UTC timestamp are different operations across a clock change. Do not treat attaching a zone object to a naive timestamp as proof that the local time exists.

If the necessary zone data or an endpoint interpretation is unavailable, mark the affected intervals unresolved and continue the supported ones. Do not replace a regional zone with a fixed offset to finish the table.

## 3. Compute coverage without double-counting

Normalize overlapping/touching windows for each person within the same evidence layer, retaining source references. Two overlapping records for one person do not provide two people of coverage. Preserve distinct role attributes rather than merging away who can cover what.

For confirmed availability, use only intervals supported by the declared availability evidence or complete relevant free/busy coverage. Intersect with the applicable working windows if that is part of the contract, subtract known blocking intervals, and retain any unknown margins. Keep the potential-hours layer available so the reader can see why it differs.

Partition the horizon at every relevant start/end, exception, demand and evidence-coverage boundary. For each resulting nonempty interval `[t, next)`, determine the active unique people and roles. At a shared endpoint, ending windows do not overlap newly starting ones for a positive duration. Include zero-person intervals inside the requested horizon rather than dropping them from the output.

Report per-segment headcount, role coverage, source layer and unresolved people. To evaluate a requirement for simultaneous distinct roles, check that different eligible people can actually fill those roles; one multiskilled person does not automatically satisfy two exclusive positions. Keep the assignment feasibility check separate from appointing those people.

For a handoff requirement, calculate the continuous interval in which both specified parties or role groups have the required coverage. A handoff needing the same participants throughout must retain those people for the whole duration; continuous group coverage with changing members does not establish that. A touch at one timestamp is zero overlap. Two separated ten-minute overlaps do not satisfy a continuous twenty-minute handoff. Record the maximal qualifying intervals and any shortfall; do not turn a possible handoff into a booked session.

Distinguish:

- **Supported:** the chosen evidence layer establishes the required coverage throughout the segment
- **Gap:** complete relevant evidence shows the requirement is not met
- **Unresolved:** missing or conflicting evidence could change that conclusion

If known people already satisfy the requirement, missing evidence about additional people need not invalidate that supported result. Conversely, a count below the requirement is not a proven gap when unknown people could cover it. Report the supported count and unknown set rather than guessing a total.

## 4. Produce the usable map

Save the requested Markdown, CSV or workbook with exact intervals behind any visual overview. Include:

- Horizon, display zone, source cutoff and explicit meaning of the selected coverage layer
- UTC interval endpoints plus relevant local dates/times, offsets and zone IDs
- Active person/role IDs, unique headcount and requirement status per segment
- Continuous handoff windows, confirmed gaps and unresolved intervals with their reason
- Material changes across the horizon, including zone-rule transitions or dated exceptions

Use full dates near midnight and transitions. A weekly summary may group identical days, but link exceptions to their actual dates; do not show one representative week as if it covered a clock-change week unchanged. Retain a machine-readable interval view when the user needs reuse. A colored grid alone is insufficient evidence for exact boundaries.

## Acceptance and recovery

Read back the saved file. Confirm that the segments partition the requested horizon without unintended overlap or omitted gaps, and that per-person unions prevent duplicate counts. Check source-to-UTC-to-local round trips, elapsed durations, an actual horizon boundary and each relevant zone transition. Inspect continuous handoff durations separately from summed overlap.

Verify that the artifact's labels do not turn working hours into confirmed availability or availability into accepted staffing. Check that every service-target claim uses the supplied threshold, role/distinct-person rule and evidence layer. Report static inspection, executed interval calculations and native-file rendering separately; none establishes that a team has adopted the map.

When sources change, keep the old version labeled and regenerate affected dates and dependent coverage segments. If the time-zone database changes for an included region, recompute rather than reusing cached offsets. If a save result is uncertain, read the destination before retrying. Return completed intervals with precise unresolved inputs instead of widening private calendar access or inventing missing hours.

Stop when the requested dated map is delivered and its limitations are explicit. Recurring refreshes, staffing changes, contact routing and calendar invitations are separate work.

## Illustration: fictional and unexecuted

For a single supplied date, A has a declared window of 09:00–12:00 at UTC+00:00 and B has 11:30–14:00 at UTC+00:00. The paper map contains A only from 09:00–11:30, A and B from 11:30–12:00, and B only from 12:00–14:00. A thirty-minute handoff fits the declared-hours layer exactly.

If B has an evidenced busy interval of 11:45–12:15 and complete relevant availability coverage is supplied, the confirmed common interval becomes 11:30–11:45. It fails a continuous thirty-minute requirement. Without that complete evidence, the result must retain the corresponding availability uncertainty. Neither result schedules a handoff.

The offsets are supplied fictional inputs. This illustration does not claim an executed zone conversion, calendar read, staffing verification or saved artifact.
