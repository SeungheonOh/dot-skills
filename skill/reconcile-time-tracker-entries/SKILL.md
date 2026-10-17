---
name: reconcile-time-tracker-entries
description: "Reconcile a person's bounded time-tracker records into a reviewable work log, separating recorded duration, unique covered time, overlap attribution, open timers and rounding. Use for resolving timer/export discrepancies, not employee evaluation, payroll approval, invoicing or inventing activity from calendar presence."
---

# Reconcile what the time tracker actually records

Deliver a usable work-log copy and a precise correction list from existing time entries and the user's supported corrections. Explain why totals differ without rewriting history to make a target total fit. Timer records describe recorded intervals; they do not prove attention, completed work, entitlement to pay or billable service.

Use [plan-personal-workweek](../plan-personal-workweek/SKILL.md) for future allocation and [spreadsheet-cleanup-reconciliation](../spreadsheet-cleanup-reconciliation/SKILL.md) for ordinary table normalization. The distinctive work here is interval accounting and attribution: simultaneous logs, incomplete timers, date boundaries and different rounding scopes. This workflow prepares a separate reconciled artifact; it does not edit the live tracker, submit a timesheet, approve hours or calculate compensation.

## Establish the reporting contract

Identify the person, workspace/account, date range, reporting timezone, source export or authorized read interface, and desired grouping such as project or task. Keep the review limited to the named person's records. Use an explicit as-of time for still-running timers and partially current reports.

Inspect available data before asking questions. Determine whether the source contains start/end timestamps, durations only, manual entries, running state, stable entry IDs, revisions, project/task IDs, tags, billable flags and report settings. A duration-only row can support a duration total but cannot establish its placement or overlap.

Clarify the few rules that change the result:

- Is the requested total logged activity duration, non-overlapping elapsed coverage or an allocation of that coverage to projects?
- Are intentional simultaneous activities permitted, or does the user's reporting purpose require exclusive allocation?
- How are breaks represented, and are they already excluded from recorded intervals?
- Does the source display raw or rounded durations, and does rounding apply per entry, per day, per project or only to the final total?
- Which corrections are established by the user or contemporaneous evidence, and which remain guesses?

If those rules are unknown, preserve raw data and show supported measures separately. Do not invent a multitasking rule, default working day, rounding increment or billable status. Calendar events, application activity and online presence may offer clues only when relevant and authorized; they cannot silently replace the user's record of work.

Keep project names and descriptions private. Minimize personal explanations for breaks or corrections. Do not transmit raw time logs to an online converter or share a report with a manager/client merely because the eventual use might be a timesheet.

## Preserve entries and resolve their time basis

Keep the original source unchanged and record its scope, capture time, filters and completeness. Retain source entry IDs and source-row locators. Repeated export rows for one evidenced entry are representations, whereas two independently created entries with equal values may be genuine duplicates or intentional separate records. Do not collapse them from matching text alone. Preserve conflicting versions until the source's revision rules or direct evidence resolves them.

Represent each usable interval by exact start and end instants with its original timestamp text and timezone/offset. Use a start-inclusive, end-exclusive interval so adjacent entries do not overlap. Preserve the source precision; calculate in integer seconds or a finer evidenced unit rather than repeatedly rounding decimal hours.

Resolve local-clock ambiguity before computing duration. A repeated daylight-saving hour needs an offset or other evidence; a nonexistent local time needs correction evidence. Do not infer an overnight entry solely because the end clock is earlier. An explicit next date can establish an overnight interval; a date-free pair remains ambiguous. Use current timezone rules for the actual dates, not the present offset.

Compare endpoint-derived duration with any stored duration. Keep a discrepancy visible: the source may have paused time, explicit break subtraction, rounding or manual duration semantics. Do not subtract a break twice or overwrite the stored value just because endpoint arithmetic differs. Verify the product's actual representation. Only treat a full endpoint span as continuous recorded activity when the source semantics establish that interpretation; equal totals alone do not establish it.

Keep three distinct populations: stored-duration records, gross endpoint spans, and effective activity intervals. Where pause/break boundaries are evidenced, subtract their union from the gross span to derive effective intervals, retaining the parent entry and excluded segments. If an entry spans 60 minutes but records 30 minutes after an unlocated pause, preserve both quantities; neither specifies which 30 minutes were active. Keep that entry's activity placement, overlap and exclusive allocation unresolved. Do not distribute its duration uniformly or assign the pause to a convenient gap.

An open timer is not a completed entry. If its running state and start are evidenced, a separate provisional interval may end at the declared snapshot cutoff for coverage analysis. Label that endpoint as analytical, keep the source end missing, and exclude it from finalized totals unless the requested report explicitly includes provisional time. A missing end without a running-state signal stays incomplete.

## Compute overlap without deciding who gets the time

For each explicitly labeled interval population in the selected window, first clip only the report view to the window and retain the full source interval. Gross-span coverage can describe timer envelopes, while effective-interval coverage describes where activity was recorded under the source's model. Never mix them into one union or imply the gross metric measures active time. Split at reporting-day boundaries when daily totals are required; compute elapsed duration between instants, since a civil day need not be 24 hours. Every split segment must retain its parent entry ID, and its durations must reconcile to the included portion. Do not allocate a stored duration across days when its placement is unknown.

Sort all relevant start and end boundaries and examine each resulting segment's active entry set. This catches nested intervals and triple overlaps that checking only neighboring rows can miss. Group by person before doing interval arithmetic; simultaneous work by different people is not one person's overlap.

Calculate separate quantities with explicit populations and units:

- Stored-duration totals, including their source semantics and unresolved placement; keep these distinct from interval-derived sums
- Sum of interval durations within the chosen gross-span or effective-activity population, counting simultaneous intervals separately
- Unique covered duration within that same population, counting each instant once
- Overlap excess: that interval-duration sum minus its unique coverage, counting a triply covered minute as two excess minutes
- Duration of time affected by any overlap, which counts that triply covered minute once
- Duration-only, unlocated-pause and incomplete/ambiguous records, which cannot be placed on an effective-activity timeline

Do not call unique coverage verified working time. Do not add duration-only or unlocated-pause entries to it as though their placement were known. Keep project-level logged sums distinct from an exclusive project allocation; their sum may legitimately exceed unique coverage when entries overlap. Report gross-span conflicts separately from established effective-activity overlaps when pauses change the result.

For each overlap component, show the exact competing intervals, affected duration and decision needed. A long forgotten timer can contain several valid shorter entries; flagging only its immediate neighbor misses the remaining conflict. [Clockify's overlap guidance](https://clockify.me/help/troubleshooting/permissions/overlapping-entries) confirms that overlap is possible in an actual tracker. Its existence alone does not identify which record is wrong or authorize a workspace-wide prevention setting.

## Build the supported correction and allocation copy

Apply only corrections supported by explicit user statements, source revision evidence or an established rule. Preserve original and proposed values, the affected entry/segment IDs, the reason and the evidence. A remembered estimate must remain labeled an estimate, even when the user wants it included.

For exclusive activity allocation, use the effective-activity intervals, resolving each overlapping segment using the approved rule or user decision: assign it to one task, split it by stated proportions, or leave it unallocated. An unplaced duration needs placement evidence or an explicit user correction before joining this allocation. Do not choose the more valuable project, silently prorate, or delete the shorter entry. Preserve an intentional concurrent-record view when that is the requested contract instead of forcing every timeline to be exclusive.

Keep corrected timestamps, attribution changes and presentation rounding as separate transformations. If rounding is requested, apply the actual rule at its stated aggregation level and show the difference from raw totals. Rounding each entry and rounding the day's sum can produce different answers. Do not alter source endpoints to disguise that difference, and do not round the same duration twice.

Retain billable and approval flags as source metadata unless the user supplied an explicit correction within the artifact's scope. Do not interpret a missing flag as nonbillable, infer overtime, or convert the work log into a financial claim. Locked or approved source records remain untouched; the correction list identifies them for the appropriate owner.

## Reconcile and deliver

Provide the reconciled work-log copy, compact totals with their definitions, and a correction/exception list. A short review can use one table with source values, proposed values and status; a larger one may need a separate interval-segment sheet. Preserve text IDs and prevent exported description text from executing as spreadsheet formulas.

Verify from the saved output that:

- Every input record has a disposition and any split or merged representation retains lineage
- Parent durations reconcile to their in-window segments; report-boundary exclusions are explicit
- Each gross-span or effective-interval duration sum equals its own unique coverage plus overlap excess; stored-duration totals are reconciled separately
- Exclusive assigned duration plus unresolved effective-interval coverage equals that effective population's unique coverage, without inventing time in gaps or claiming unplaced records are covered
- Project/day totals use the same inclusion and rounding rules; provisional, duration-only and ambiguous records are visibly separate
- Corrections have evidence, unknown endpoints remain unknown, and the live source was not changed

Use an independent endpoint/segment recomputation for consequential totals rather than checking only that summary cells add up. Reopen the actual delivery file and verify the period, timezone, IDs, formulas if present and representative boundary cases. Say whether calculations were performed, a spreadsheet was recalculated or only a proposal was prepared.

On an uncertain save, inspect the destination before retrying. On a source revision change, refresh affected entries and recompute their overlap components before presenting a correction as current. Preserve the prior source and candidate rather than overwriting with a guessed merge.

Stop when the requested artifact and supported totals are complete, leaving unresolved intervals and decisions visible. Live tracker correction, stopping a timer, changing rounding settings, submitting the report or contacting another person requires a separately scoped action.

## Fictional, unexecuted illustration

A fictional closed-entry export shows A from 09:00–10:30 and B from 10:00–11:00 on one ordinary local morning. Their recorded sum is 150 minutes; unique coverage is 120 minutes; the overlapping segment and overlap excess are both 30 minutes. These are record-derived quantities, not proof of 120 minutes of focused work.

The source defines A and B as continuous activity intervals. The user explicitly says A should have ended at 10:00. A proposed corrected copy therefore contains 60 minutes for A and 60 for B, with the original 90-minute A preserved in the change record. A separate 12-minute duration-only entry remains outside the interval-union calculation. Another entry spanning 13:00–14:00 with 30 stored minutes and an unlocated pause contributes a 60-minute gross span and a separate 30-minute stored duration; its effective activity coverage stays unresolved. If an unrelated timer has a missing end and no running-state evidence, it stays incomplete rather than being closed at the report cutoff.

No tracker, timesheet, spreadsheet or account was changed, and no real work was observed. The inputs and arithmetic illustrate how one supported correction differs from an invented allocation.
