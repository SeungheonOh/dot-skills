---
name: analyze-work-item-flow
description: "Reconstruct team work-item flow from bounded status histories and calculate throughput, work in progress, age and elapsed cycle time with explicit reopening, cancellation and incomplete-history rules. Use for delivery-flow analysis, not employee rankings, effort tracking, backlog prioritization or delivery forecasts."
---

# Analyze how work moves through a team

Answer where delivery time accumulates and what the recorded flow actually shows. Reconstruct item lifecycles before calculating averages. A current board snapshot, a collection of closed tickets or a count of comments cannot establish the same history.

Use [issue-backlog-prioritization](../issue-backlog-prioritization/SKILL.md) to choose work, [reconcile-time-tracker-entries](../reconcile-time-tracker-entries/SKILL.md) to reconcile recorded effort, and [workflow-effectiveness-review](../workflow-effectiveness-review/SKILL.md) to compare matched assisted and baseline tasks. This workflow describes a team's delivery system from existing records. It does not rank people, prescribe staffing, change a tracker or promise completion dates.

## Define the item and the flow boundary

Inspect the authorized board/export and its history coverage. Establish:

- Project/team boundary, item types, hierarchy level and stable tracker-scoped item identity
- Reporting interval, exact cutoff and timezone; whether the question concerns completions in a period, a start cohort or work open at the cutoff
- The workflow definition and revisions: actual start and finish boundaries, intermediate states, cancellation and reopening rules
- Status-transition/event records, initial state or earlier history, issue creation and closure semantics, and relevant board/filter changes
- Existing exclusions, class-of-service or item-type distinctions, and the intended private report/destination

Choose the smallest meaningful population. Do not count a parent epic and all its child issues as equivalent completed units in one throughput measure. Retain hierarchy and split/merge links; ticket duplication or splitting can change item counts without increasing delivered scope.

The [Kanban Guide's flow definitions](https://kanbanguides.org/the-kanban-guide/2025.5/#flow-metrics) depend on the team's explicit start and finish points. Use its distinctions between started-but-unfinished work, finished items per period, age of unfinished work and elapsed time of finished work. Do not silently replace those boundaries with issue creation, first assignment, PR merge or deployment.

Ask only for a missing rule that changes the result. If no agreed workflow exists, prepare a clearly labeled candidate mapping and source accounting, then show conditional results where useful. Do not present an analyst's choice as an adopted team policy. Store definitions beside the report so a later comparison can use the same basis.

Minimize personal data. Team-level flow usually needs item IDs, types, states and times, not assignee names, private comments or reasons for an individual's absence. Do not join HR, health, presence or personal time records into this analysis. Avoid external converters and retain sensitive issue content only in its authorized source.

## 1. Preserve source identity and observation coverage

Record the extraction time, query/filter, pagination completeness, event coverage and source revision. Preserve raw records and calculate in a separate representation. Identify the item population independently of a closed-only export; otherwise label the analysis as restricted to observed completions and do not infer total WIP or a completion rate.

Deduplicate repeated representations of the same event by stable event ID and revision. Equal status/time values on different events are not automatically duplicates. Retain moved issues, board transfers and workflow renames without treating them as new work or new completion. Where two trackers share issue numbers, preserve their separate namespaces.

Normalize timestamps to exact instants while retaining source text and timezone. Reject unresolved daylight-saving or date-only ambiguities for precise interval arithmetic. Use provider sequence information for tied timestamps; row order is not a substitute when the transition order affects the result.

A history beginning with an item already active does not establish its start time. An earlier active observation supports a minimum age only when continuity of that same lifecycle or episode through the cutoff is evidenced; it does not establish an exact duration. A missing transition interval remains unknown; do not stretch the preceding state across an unobserved gap without source support. Record the affected metrics rather than discarding the entire item.

## 2. Reconstruct states and delivery episodes

For each item, build an ordered transition record with before/after state, event time, source locator and workflow version. Confirm that consecutive states agree. A mismatch may indicate a missing event, import correction or changed workflow; preserve it until resolved.

Map states into not started, within the delivery boundary, finished, canceled, or unresolved according to the agreed rules. Blocked and waiting states ordinarily remain inside the started-to-finished boundary unless the team's explicit definition says otherwise. They do not become human effort or disappear from elapsed cycle time.

Handle lifecycle changes explicitly:

- **Reopening:** establish whether it resumes the original item lifecycle or creates a separately measured delivery episode. Preserve every finish and reopen event either way
- **Cancellation:** keep it separate from successful completion; it can remove WIP without producing delivered throughput
- **Split or merge:** retain the original and successor relationships. Apply a stated counting policy; do not silently manufacture a completed item from administrative closure
- **Transfer into/out of scope:** record it separately from starting or finishing delivery. A board move may change observed WIP without any change in lifecycle state
- **Workflow revision:** map the version applicable at the event, or show a documented common analysis mapping. Do not infer old-state meaning from a current label

Do not choose first or last closure after seeing which makes a metric better. Define whether the requested completion count is distinct items, completed episodes or finish events. Report episode/event throughput under that name when the same item can finish more than once; do not label it a count of unique delivered items.

For reopened work, distinguish completed earlier episodes, current unfinished age and eventual item completion that is still unknown. A later reopen does not erase the earlier event, but it can invalidate a claim that the item was finally complete at the earlier cutoff. Keep historical as-of reporting separate from a later corrected view.

## 3. Calculate the supported measures

Use one endpoint convention throughout. For example, a reporting interval includes events at its start and excludes those at its end; state snapshots must use the corresponding before/after convention. Retain elapsed calendar units unless a separate business-calendar measure is explicitly requested and fully defined.

| Measure | Required calculation and qualification |
| --- | --- |
| Throughput | Count eligible completed units in the interval under the declared distinct-item or episode rule; show cancellations and unknown classifications separately |
| WIP | Count in-scope units that have crossed the start boundary and not the applicable finish/cancel boundary at an exact observation instant |
| Age | Cutoff minus the evidenced start of a currently unfinished item or episode, with the chosen reopening rule stated |
| Cycle time | Applicable finish minus evidenced start for completed units; retain the duration of waiting and blocked intervals within that boundary |
| State residence | Sum evidenced intervals in each state, preserving repeats and gaps; this describes workflow elapsed time, not active labor |

Keep open and completed populations side by side. An open item's age is time spent so far, not its eventual cycle time and not a zero-duration completion. Completed-only averages omit still-open work and may look faster when slow items have not finished. Show the completion cohort's count and distribution together with WIP count, observed ages, missing starts and unresolved histories.

If reporting median or percentiles, name the eligible population, number of exact observations and calculation convention. Do not fabricate a percentile from a tiny or incomplete sample or use an unspecified interpolation rule. Use ordinary descriptive summaries for the requested question; survival modeling, simulation and probabilistic delivery forecasting are separate work.

A fully covered interval with no eligible completions has zero throughput, but no completed-cycle median or percentile. Missing completion coverage is unknown, not a zero count.

Preserve item-type and scope differences when comparing periods. A larger share of small maintenance tickets can change pooled cycle time. Show comparable strata when the records support them, and disclose changed definitions, filters and follow-up lengths. A before/after improvement does not establish that a process change caused it.

Never convert status residence into utilization, productivity per person, billable time or individual performance. A long review column can contain waiting, genuine review work, batching or delayed status entry. Name the observed interval and the missing evidence needed to distinguish explanations.

## 4. Reconcile the flow, then answer the question

For a complete event-defined population, reconcile the boundary inventory:

opening WIP + starts + reentries/reopens + active transfers in - finishes - cancellations - active transfers out = closing WIP

Count each boundary crossing once using the defined unit. A transition between two in-progress states contributes to neither side. If the unit or reopening policy requires a different identity, derive that identity explicitly instead of forcing these terms to fit. Unknown initial states or incomplete events prevent an exact equality claim; show the unmatched residual and affected items.

For each fully observed completed interval, check that its nonoverlapping state durations sum to its elapsed cycle time. Keep unknown gaps visible rather than allocating them to a convenient state. A blocked marker that overlaps another state is a separate dimension: use interval intersections/unions, not a sum that double counts time.

Lead the report with the supported finding, such as “completed items were faster in this window, while the oldest open work grew older.” Give the decisive counts, duration distributions and coverage. Provide a compact item/episode ledger and definitions sufficient to reconstruct the result, plus the most useful missing-evidence question. Do not prescribe new deadlines, WIP limits or team commitments from the analysis alone.

## Acceptance, preservation and recovery

Before delivery, independently retrace the items driving the headline, the oldest open work and any reopened/canceled boundary. Check source accounting, unit counts, time arithmetic, endpoint conventions and the WIP inventory. Verify that no parent/child double count, closed-only selection or missing start is hidden by a summary chart.

Save to the requested authorized destination and read the delivered artifact back. Preserve source statuses, assignments, labels and prior reports. If a source correction arrives, rebuild affected lifecycles and dependent aggregates, retaining the old cutoff and recording the changed basis. If an export or write is incomplete, preserve the usable work and identify the precise gap; inspect an uncertain save before retrying.

Stop with the bounded descriptive answer and its limitations. Do not start monitoring, contact teammates, edit tickets, rerun work or invent a future service-level promise to make the report actionable.

## Fictional illustration, not executed

A fictional team measures distinct items, elapsed hours, and final completion as of a Friday cutoff. All times are UTC within one week. Item A starts Monday 09:00, finishes Tuesday 09:00, reopens Wednesday 09:00 and remains open Friday 09:00. Its agreed reopening rule resumes the original lifecycle. Item B starts Tuesday 09:00 and finishes Thursday 09:00. Item C starts Wednesday 09:00 and is canceled Thursday 09:00.

At the cutoff, B contributes one final completed item with 48 hours of cycle time. A has 96 hours of current lifecycle age; its earlier finish/reopen events remain in the history. C is a cancellation, not delivered throughput. A separate event-count view has two finish events, and must be labeled differently. With no opening WIP or transfers, three starts plus one reopen minus two finishes minus one cancellation leaves one open item.

These dates, rules and expected calculations are invented. No tracker was read, analysis program run, team performance measured or operational rule changed by this illustration.
