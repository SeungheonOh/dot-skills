---
name: build-duty-rotation
description: "Build or revise a finite team-duty roster from an approved participant pool, coverage rules and prior load, delivering dated assignments, uncovered slots and a traceable load ledger. Use for recurring operational duties, not hiring, performance ranking or activating an on-call service."
---

# Build a duty rotation

Create an editable roster that explains who is proposed for each duty, where coverage is missing and how the burden is distributed. Typical uses include rotating meeting facilitation, a shared support inbox or an equipment-check rota. A named row is a proposed assignment unless existing evidence establishes acceptance.

Use [project delivery planning](../plan-project-delivery/SKILL.md) for project responsibilities and dependencies. Use [small resource schedules](../verify-small-resource-schedules/SKILL.md) for a fixed-duration job model and optimality proof. This workflow handles the practical roster, carry-over history, exceptions and revisions needed by a team.

## Establish the roster contract

Recover these from the request and authorized records; ask only about a gap that changes the assignments:

- Exact duty, finite start/end dates, slot boundaries, role requirements and minimum people per slot
- Approved participant IDs and names, explicit role eligibility, participation limits and any accepted fixed assignments
- Declared availability or exclusions, effective dates, time zones where clock times matter, and whether availability is complete for each person
- Hard rules such as no overlapping duties, maximum consecutive slots, minimum rest or distinct primary/backup people; softer preferences separately
- Agreed rotation order or burden rule, tie handling, and relevant historical assignments with a cutoff
- Existing roster/version, change scope, output format and audience

Do not infer eligibility, capacity or willingness from job titles, commit counts or prior responsiveness. This is not a tool for selecting employees, judging performance or certifying a regulated staffing plan. If the duty requires a qualification, use the authorized eligibility list; do not independently decide qualification from personal records.

Collect unavailable intervals, not medical, family or other private reasons. Keep those reasons out of the roster even if a source includes them. Use internal IDs in calculations and only the contact details needed by the approved audience. Reading a roster does not authorize sharing it, contacting participants, creating calendar events or changing a live paging configuration.

## 1. Preserve the baseline and expand the slots

Keep the existing roster and source records unchanged. Give the candidate a revision and record the source cutoff. Preserve stable participant and slot IDs; a display-name change is not a new person. Flag duplicate IDs or conflicting source versions before assigning through them.

Expand the requested recurrence into explicit slots over the finite horizon. Keep date-only duties date-only. For timed duties, record each start/end date, IANA zone and resolved UTC instant; an overnight slot needs its actual next-day end. Use date-specific zone rules, resolve ambiguous or nonexistent local times, and calculate elapsed hours in UTC. Do not call every civil day 24 hours or use today's offset for every future slot.

Apply exclusions and fixed assignments without silently repairing them. A fixed assignment that violates a new hard rule is a conflict for review, not permission to reassign it. Keep out-of-scope assignments intact, while checking neighboring assignments when they affect rest or consecutive-duty limits at the horizon boundary. Missing boundary history makes those particular checks unknown.

## 2. Build eligible choices before balancing load

For every slot and role, list the people whose supplied eligibility and complete availability support the assignment. Distinguish `eligible`, `ineligible` and `unknown`; unknown availability is not an empty calendar. If the source contains only exclusions without asserting completeness, say what assumption would be needed to assign the remaining time.

Check joint constraints, not only individual rows. A person cannot satisfy two simultaneous exclusive roles, count twice toward a two-person requirement, or serve as their own distinct backup. A backup is not additional primary coverage unless the supplied policy explicitly says so. Include preparation or handoff time only when it is a declared requirement, and identify whether it consumes capacity.

Keep required coverage separate from preferences. Mark a slot with no supported candidate as uncovered or unresolved. Do not reduce coverage, use someone outside the approved pool, ignore an absence or relax a rest limit to make every row look filled.

## 3. Construct a candidate using the agreed burden rule

Follow the team's actual rotation rule. A round-robin needs a starting position and a rule for skipped people: retain their place, move them to the end, or another agreed treatment. Do not quietly reset the cycle at a month boundary.

If fairness is requested but undefined, show the factual workload and a clearly labeled proposed rule before treating its result as agreed. Distinguish slot count, elapsed duty hours and any explicitly weighted burden; a weekend weight or primary/backup weighting is a policy choice, not a fact to invent. Keep unlike roles separate unless the user provides a meaningful conversion.

Calculate historical load and proposed new load separately, then combine them only for the stated horizon and rule. Do not erase carry-over because someone was unavailable or treat time off as negative contribution. If normalization by participation share is requested, use supplied shares and identify their denominator; zero or unknown eligibility does not support a numeric fairness comparison.

A simple constrained rotation is often enough. When an early choice blocks later coverage, backtrack or revise unfixed choices within the authorized change scope. If a heuristic cannot fill every slot, report an incomplete construction; that does not prove no feasible roster exists. Claim impossibility or optimality only with an adequate bounded search or other proof, stating its scope. Do not install a solver or expand the task solely to make such a claim.

For each changed assignment, preserve the before/after value and reason. A requested swap needs both resulting assignments checked against eligibility, overlaps, rest, consecutive slots and coverage. Do not assume both people accepted it because one proposed it.

## 4. Deliver the roster and its exceptions

Save the actual editable artifact in the requested format, with these views scaled to the roster:

- **Roster:** slot ID, exact date/time or date range, role, proposed/accepted assignee, assignment status and any required handoff reference
- **Load ledger:** participant ID, historical load, candidate load, combined metric and rule; show the whole approved pool, including people with zero assignments or no eligible slots
- **Exceptions and changes:** uncovered demand, unknown inputs, hard-rule conflicts, material preference tradeoffs and before/after changes
- **Basis:** source/version cutoff, horizon, rotation position or rule, and what establishes assignment acceptance

Keep personal absence reasons out of every view. Do not export a candidate with unknowns as an active roster. If a native document save is authorized, preserve unrelated tabs, formulas, assignments and access settings; preparing a local artifact alone does not authorize publishing it to the team.

## Acceptance and recovery

Read back the saved artifact and check every slot against the same frozen inputs:

1. Every required slot/role appears exactly once with its required headcount and explicit coverage state
2. Each proposed person is eligible for the entire slot, no identity is double-counted and all applicable joint constraints pass or remain visibly unresolved
3. Historical plus candidate loads reconcile to the assigned slots and declared weights; no skipped or unknown person silently disappears
4. Fixed and out-of-scope assignments are preserved, and the change register explains every permitted alteration
5. Acceptance, proposed assignment and actual notification remain separate states

Inspect boundary cases that occur in the real roster: the last historical duty, an overnight slot, leave crossing a slot boundary or a swap involving a backup. Static review establishes only the checked rules; a spreadsheet's appearance does not establish formula recalculation or participant acceptance.

If new availability or a concurrent roster revision appears, keep the previous candidate labeled and regenerate only the affected plan with its dependent constraint checks. If saving has an uncertain result, inspect the destination before retrying. If a rule makes coverage unresolved, deliver the usable portion and the smallest decision needed; do not solve a hard-rule conflict by hiding it in a balancing score.

Stop at the requested candidate or authorized roster-file update. Activating an on-call schedule, sending assignments and arranging recurring reminders are separate actions with their own authority and verification.

## Illustration: fictional and unexecuted

Assume four equal weekly facilitator slots, an approved pool A, B and C, and a supplied rule that chooses the lowest current combined count among feasible candidates, breaking ties by the approved order A, B, C and retaining fixed assignments. Prior counts are A=2, B=1, C=1. B is unavailable for week 1. Week 2 is already fixed to A. No person may facilitate consecutive weeks, and the preceding week was B.

A candidate is C, A, B, C. Candidate counts are A=1, B=1, C=2; combined counts are A=3, B=2, C=3. The ledger shows the remaining difference instead of calling the roster perfectly equal. If C later becomes unavailable in week 4, that candidate must be reconsidered rather than silently assigning B twice consecutively.

This is a paper illustration, not an executed optimization, verified real roster, participant agreement or sent assignment.
