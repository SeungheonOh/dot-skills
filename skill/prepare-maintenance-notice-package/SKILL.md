---
name: prepare-maintenance-notice-package
description: "Prepare a version-consistent set of maintenance notices from a supplied change window, affected workflows and communication rules, including reschedule and completion conditions. Use for an operator-ready notice package, not release notes, scheduling maintenance in a service or executing the change."
---

# Prepare maintenance notices that agree

Turn an established maintenance plan into concise audience-specific drafts and an operator handoff that preserves timing, impact and message revision. The useful result is a coherent notice package, including what may be said when the plan changes. It is not a change approval, an outage prediction or evidence that a notice was sent.

Use [change-log-release-notes](../change-log-release-notes/SKILL.md) to describe shipped behavior and [release-readiness-gate](../release-readiness-gate/SKILL.md) to evaluate a release candidate. Use ordinary correspondence drafting when only one message is needed and there is no maintenance-window or lifecycle coordination to resolve.

## Inputs and permitted output

Read the current authorized change record and any already-issued notice. Establish:

- Change/window ID and plan revision; service, environment, components and affected audience/cohorts
- Exact start/end and source timezone, plus any expected interruption duration within that window
- Supported impact, unaffected functions when evidenced, user preparation, deadlines and workarounds
- Plan status and who can authorize timing, impact statements and completion
- Required channels, length limits, audiences, notification rules and existing public/private labels
- Supplied checkpoints or evidence conditions for start, delay, verification, completion, cancellation and rescheduling
- Requested artifact destination and whether this task is preparation only

Derive what is known before asking. Missing timing, audience or material impact blocks the affected send-ready notice, not the whole packet. Keep an explicit editorial hold outside draft copy. Do not invent downtime, an all-clear, data-safety promises, compensation, a support commitment or a next-update deadline.

Create one editable package with the canonical window record, required drafts, channel/trigger matrix and unresolved decisions. Use separate files only when they help the requested handoff. Drafting in a third-party platform, publishing, notifying subscribers, scheduling messages or changing status-page components requires authority for those effects; preparing this package implies none of them.

## 1. Create one canonical window record

Retain the original dates and timezone, derive explicit UTC instants when supported and record the planned duration. Keep the maintenance window separate from the expected service interruption: a two-hour work window does not establish two hours of downtime or a guaranteed maximum outage.

For recipient-local versions, convert both endpoints using the named zone's rules on those dates. Include the date at each endpoint when the interval crosses midnight. Ambiguous repeated clock times require an offset or other source resolution; nonexistent local times require a corrected plan. Do not infer which daylight-saving occurrence an owner meant or use a fixed present-day offset for a future date.

Check elapsed duration in absolute time. Human wall-clock differences can be misleading across offset changes. Keep an explicit timezone beside every published window; avoid abbreviations such as CST when they do not identify a unique zone. [RFC 3339](https://www.rfc-editor.org/rfc/rfc3339) supplies an offset-bearing timestamp representation; it does not identify the regional rules needed for a future local-time conversion.

Separate planned start/end, actual start/end, announcement time and next-update time. A schedule becoming past does not prove that maintenance started or finished. If the owner replaces a window, keep the prior revision and mark it superseded in the operator record, while making the replacement unambiguous in current drafts.

## 2. Map impact to the reader's workflow

Build a small impact-to-audience map from the plan: component, affected behavior, cohort/region, expected symptom, action needed, action deadline, allowed workaround and evidence source. A backend component name alone is rarely useful to a customer. Translate it to an evidenced workflow without broadening the affected population.

Distinguish unavailable, read-only, delayed, intermittently failing and degraded performance. Do not replace uncertainty with the most reassuring wording. An unaffected login service does not establish that users can complete downstream work; similarly, one affected export queue does not establish a whole-product outage.

User actions must be supported by the plan. A vague suggestion to retry can duplicate consequential submissions; include retry guidance only when the documented workflow supports it. Keep internal hostnames, topology, customer-specific identifiers, change tickets and operational commands out of external variants unless their disclosure is authorized. Use a verified audience-appropriate support/status reference; never manufacture a public link from a private ticket ID.

## 3. Prepare only the lifecycle drafts the handoff needs

Use the team's terminology and channel conventions. A practical package can include:

| Draft | Required evidence before use | Important wording boundary |
| --- | --- | --- |
| Advance notice | Current plan, established window and supported affected scope | Planned timing and expected impact stay prospective |
| Start notice | Reported or observed start for this change | Reaching the scheduled time alone is insufficient |
| Delay/extension update | Current status, changed impact and approved new estimate or update checkpoint | Unknown completion time stays unknown |
| Verification update | Work completion evidence plus remaining checks | Verification is not an all-clear |
| Completion notice | Required service checks and completion decision for the affected scope | Do not promise zero data loss or universal availability without evidence |
| Cancellation/reschedule notice | Owner's changed decision and any replacement window | Explicitly withdraw the old window; a replacement is not an additional outage |

Avoid six empty templates when only two states matter. For each prepared draft, put its audience, channel, plan revision and usage condition in the operator wrapper, separate from the actual copy. Future-state drafts remain clearly conditional and must not be placed where an automated publisher could treat them as current messages.

Maintain the same service/cohort labels, window, impact qualifiers and required action across short and long variants. A short channel may point to the approved detailed notice, but still needs the consequential warning and enough time context to stand alone. Do not remove the timezone or affected-cohort restriction to meet a character limit.

For a reschedule, state the old window and its cancellation before the new window when confusion is likely. Carry the change ID and revision in the private handoff; preserve the actual old notice ID/link if supplied. A text edit in one channel does not update copies, email or subscriber notifications elsewhere.

## 4. Hand over exact publication conditions

Provide a channel/trigger matrix with the intended audience, draft/revision, evidence required, responsible publisher, proposed or supplied send time, existing notice identity and authorization state. Keep `prepared`, `approved for this use`, `scheduled`, `published` and `delivery confirmed` separate. Only evidence can establish the latter stages.

Inspect the named platform's official behavior when it changes the handoff. For example, [Statuspage's maintenance documentation](https://support.atlassian.com/statuspage/docs/schedule-maintenance/) describes separate scheduled, in-progress, verifying and completed states, plus notification and automatic state-change options. A platform entry may therefore notify people or change components; it is not necessarily a private draft. Record relevant effects without activating them.

A supplied next-update time is a communication commitment. If none exists, leave a specific owner decision rather than inserting “we will update in 30 minutes.” Do not create reminders, recurring monitoring, subscriber lists or automatic all-clear messages as a side effect of document preparation.

When publication is separately requested, recheck the exact current plan, audience, final copy and platform effects before proceeding through the appropriate authorized workflow. This package alone does not grant permission to schedule the underlying maintenance, send future updates or broaden the audience.

## Verify, preserve and recover the package

Read back the saved package and check:

1. Every variant derives from the same current plan revision and identifies the intended audience
2. Both endpoints, date changes, offsets and elapsed duration agree; interruption duration is not substituted for window duration
3. Supported impact and user actions survived shortening, with no invented promises
4. Conditional start/verification/completion copy cannot be mistaken for an observed state
5. Replaced windows are unambiguously superseded and the correction identifies the notice being corrected
6. Public copy contains no private operational details, recipient list, secrets or restricted evidence links
7. Every publish/send claim has actual evidence; preparation remains preparation

On conflicting plan revisions, preserve both and hold the conflicting timing or impact claim until the owner resolves it. On later changes, update affected variants from the canonical record and keep a concise revision note; do not silently patch only the longest draft. If an old notice was already issued, prepare a correction explicitly; do not claim editing a file retracted it.

Preserve the original plan, issued messages and unrelated edits. Check an uncertain artifact save before retrying. Stop when the package is usable with its remaining decisions clearly assigned. Readiness of notice copy is separate from readiness of the maintenance itself.

## Fictional, unexecuted example

A fictional change M24 moves the export queue. Plan revision 2 replaces a previously announced 01:30-02:00 UTC window on 18 October 2026 with 02:30-03:00 UTC. Only scheduled exports for the stated pilot cohort are expected to be delayed; browsing is supported as unaffected. The owner supplied no exact recovery estimate beyond the planned window and no post-change check result.

The draft correction says the earlier window is canceled and gives the replacement date, UTC window, affected cohort and export-delay warning. The operator matrix references the old fictional notice N7 and revision 2. Its conditional completion draft is held pending the required export check. The package does not claim that N7 was edited, subscribers were notified or exports recovered at 03:00.

This is an authored illustration. No status page, calendar, message scheduler, subscriber notification or maintenance operation was accessed or executed.
