---
name: reconcile-support-response-deadlines
description: "Apply supplied support response or update policies to bounded case histories, replaying qualifying events and business-calendar clocks to produce due times, observed performance and localized unknowns. Use for policy-bound support timing, not reminders, queue prioritization, legal entitlement or resolution guarantees."
---

# Reconcile support response clocks

Answer when a support response was due, whether the available history establishes that the timing target was met, and which missing rule or event prevents a conclusion. Produce a case-and-cycle record that another reader can reconstruct. A ticket's age, latest message timestamp or displayed status is not a substitute for the policy's actual clock.

[Awaited-reply follow-up](../awaiting-reply-user-followup/SKILL.md) schedules future checks. [Deadline alerts](../deadline-leadtime-alert/SKILL.md) schedule a warning from an established deadline. [Service-quality review](../service-quality-window-review/SKILL.md) assesses request/error/latency telemetry. This workflow calculates support response obligations from existing evidence; it creates no watcher, sends no escalation and changes no ticket.

## Establish the applicable policy and case scope

Read the bounded authorized case histories and governing response/update policy, including its version and applicability to the case's service, channel, support plan, priority and creation date. Use account-specific terms or a supplied policy when those govern; a current general help page may not apply to an older case. If applicability is unsettled, show the candidate rule sets instead of choosing the most favorable deadline.

Record the analysis cutoff with timezone and the source coverage through that point, including relevant public replies, private notes, status changes and transfer/reopen events only where already authorized and available. Missing channels or pages can hide a qualifying response. Access to an internal status should not be assumed from a customer-visible transcript.

For each requested metric establish:

- Its unit and threshold: elapsed duration, accumulated support hours, a number of business dates, or an explicit promised timestamp
- The event that starts a cycle and which case identity or request it belongs to
- What qualifies as a response or update, including audience, actor and content conditions
- Which events pause, resume, stop, cancel or reset the clock, if any
- How reopenings, merged cases, transfers, customer replies and priority/policy changes affect an existing cycle
- The support calendar, named timezone, dated hours, holidays/exceptions and endpoint/rounding rules that matter

Do not invent a universal definition of a human reply, business day or pending status. An automated receipt might count under one policy and be excluded by another. “Usually within a day” is a descriptive expectation, not an exact enforceable timestamp. Ask for the missing rule only when it changes the requested result; continue metrics and cases that are supported.

This is a factual calculation under supplied rules, not a legal interpretation, compensation determination or authority to change service commitments. Keep personal identifiers and message contents to the minimum needed for case/event identity. Never copy credentials, access tokens or unrelated diagnostic payloads into the timing record.

## 1. Bind events to cases, metrics and cycles

Create an event ledger with stable provider-scoped case ID, source event/message ID, timestamp as recorded, timezone/offset, event type, audience, actor role when established, relevant policy facts and source locator. Distinguish submitted, received and created times when the policy does. A local draft time is not a provider receipt time.

Preserve duplicate-source lineage without double counting one event. Quoted earlier replies do not become fresh responses. Different cases with the same number in different providers remain distinct. If a case was merged or reopened, retain its original history and apply only the documented clock-continuity rule; neither restarting every clock nor inheriting the oldest clock is a safe default.

Classify each candidate response against the policy before measuring it. Record qualifies, does not qualify, or unresolved with the decisive evidence. A public acknowledgment may satisfy a receipt metric while leaving a substantive-response metric open. A private internal note may not satisfy a customer-facing response obligation. A partial answer can satisfy a defined first-response target without resolving the user's problem.

Give separate cycle IDs to independently measured obligations: first response, next reply after a customer message, periodic update or an explicit promised callback. A later response does not erase the outcome of a missed earlier cycle. Preserve completed, canceled and currently open cycles instead of reporting only the latest timer.

## 2. Replay the actual clock rules

Start each metric/cycle from its evidenced trigger. Walk relevant events in established order and record the transition, rule citation and clock consequence. Keep stopped, paused, running, not yet started and unknown separate. Do not infer that every provider status transition has a timing effect.

Distinguish pause from reset: a pause retains accumulated time; a reset begins the policy-defined new measurement and must not erase the prior cycle's result. A customer reply can start, resume or leave a clock unchanged depending on the metric. A priority change may alter the target prospectively, retroactively or only for a new cycle; keep the dependent deadline unresolved if the policy does not say.

Union overlapping valid pause intervals before subtracting them, and never deduct a pause before the relevant cycle began or after it ended. Retain an open-ended pause as such. If the clock is paused and its resume time is unknown, report accumulated time and remaining allowance; give a future due time only conditionally on a stated resume assumption, not as an exact current deadline.

With tied timestamps, use an evidenced provider sequence or an order-insensitive result. If event order changes whether the clock stopped, reset or exceeded its threshold and no order is known, keep that conclusion unresolved. Do not impose order from row position or message display order without a source basis.

## 3. Accumulate time under the correct calendar

Keep original local timestamps and normalize exact instants using the named timezone's rules for their dates. Do not apply today's offset across daylight-saving changes. Missing offsets, repeated local times or nonexistent local times need source clarification or an explicit bounded interpretation. A timestamp's display precision must not create false certainty at the threshold.

For an elapsed-duration target, measure the policy-defined active duration without excluding nights or weekends unless the rule does. For accumulated support hours:

1. Expand the applicable dated calendar into working intervals, including split shifts, overnight windows and supplied exceptions
2. Resolve those intervals to actual instants under the provider's documented counting semantics; preserve any ambiguity about repeated hours or wall-clock counting
3. Intersect each running cycle segment with the working intervals
4. Remove only supported pause intervals and combine overlaps so no time is counted or excluded twice
5. Sum the resulting durations in the policy's units and retain the segment arithmetic

The due instant is where the permitted active time would be exhausted under those rules. Carry unused allowance across closed periods. A case submitted outside working hours can have a recorded start time then while accumulating zero support time until the calendar opens. Do not move the source event itself to the opening time.

For “next business day,” “end of the second working day” or another date-count rule, use its explicit date and cutoff semantics. Do not replace a business date with eight hours or assume that today counts as day one. Apply a supplied holiday calendar for the relevant location and year; an unverified absence of holidays is not a complete calendar.

Keep deadlines reported by the provider alongside calculated ones. If they disagree, check policy version, calendar, start event, pause handling, priority and rounding before proposing a correction. Preserve unresolved discrepancies; do not rewrite the portal's value or present your calculation as the provider's confirmed promise.

## 4. Classify results without overstating coverage

For each metric/cycle return the target, start/stop evidence, relevant pauses, counted duration, supported due instant or bound, response classification and outcome:

- Met under the supplied rule, with the qualifying response and its counted duration
- Missed under the supplied rule, with the complete evidence or defensible bound establishing the threshold was exceeded
- Open and not yet due at the cutoff
- Open and past the calculated due time, only when observation coverage establishes no qualifying stop before that point
- Paused, canceled or not started, under an explicit policy rule
- Unresolved, naming the missing rule, applicability, timestamp, event or source coverage

Use the policy's inclusive/exclusive threshold and rounding convention. Show unrounded arithmetic when rounding could change the conclusion. Distinguish time beyond the target from total case age and from time to resolution.

When uncertainty can be bounded, carry the range through the calculation. A result is conclusive only if every allowed interpretation supports it. Otherwise show conditional deadlines or outcomes without inventing a midpoint. A source gap can prevent an overdue conclusion even when the nominal date is past. An earlier established miss remains established if later events are missing, but the current unanswered state may still be unknown.

Do not infer that a late response causes harm, breaches law, earns a credit or warrants a particular escalation. A precisely calculated target is still conditional on the correct policy and event record. Report the operational discrepancy and the smallest evidence or decision needed next.

## Deliverable and acceptance

Return one concise timing brief with:

1. The supported answer as of the cutoff and material coverage limits
2. Policy/applicability and calendar sources with exact revisions or capture dates
3. Case/metric/cycle results, including reported versus calculated deadlines
4. The event-transition and counted-interval records needed to reconstruct decisive results
5. Localized unknowns and the precise next evidence question

Keep the structure proportional. One simple case may need only a few linked intervals, not a multi-sheet workbook. Save to the requested private destination and read the actual saved contents back. Preserve source records, provider statuses and access permissions.

Before delivery, independently retrace each decisive start, qualifying stop and pause transition. Recalculate interval totals and the due boundary; inspect the off-hours or holiday crossing that matters. Check that separate metrics and cycles have not been blended, no pause was subtracted twice, and no incomplete read became an absent-response claim. Verify that completed-cycle results survived later resets and that a response-target pass did not become a resolution claim.

If new history arrives, update the affected cycles with their stable identities and preserve the previous as-of result. If the policy or calendar is corrected, label that as a changed calculation basis and identify which conclusions change. After an uncertain save, inspect the destination before retrying; do not overwrite a newer review. Finish with the bounded assessment and its specific unknowns. Continuing observation, reminders, customer contact and ticket changes require a separate authorized task.

## Fictional illustration, not executed

A fictional policy requires a qualifying public support response within two accumulated support hours. Automated receipts are excluded. The supplied calendar is Monday through Friday, 09:00–17:00 UTC, with Monday 19 October 2026 explicitly closed as a fictional holiday. A case is received Friday 16 October at 16:30 UTC, and an automated receipt follows at 16:31.

Thirty minutes accumulate on Friday. The remaining ninety minutes accumulate on Tuesday 20 October from 09:00 to 10:30, so the calculated due time is Tuesday at 10:30 UTC. A qualifying public reply at 10:45 produces 135 support minutes, fifteen beyond the two-hour target. The receipt did not stop that clock. A complete supplied event record supports the missed first-response target; it says nothing by itself about problem resolution.

A separate fictional four-support-hour update cycle begins Tuesday at 11:00. Its explicitly allowed awaiting-user pause lasts 12:00–14:00, and a qualifying update arrives at 16:00. That cycle counts one hour before the pause and two after it, totaling three hours, so its target is met. It does not erase the earlier first-response miss.

All policy rules and case events are invented. These are expected calculations only; no provider policy was adjudicated, portal changed, reminder scheduled or escalation sent.
