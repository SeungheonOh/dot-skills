---
name: configure-recurring-tasks
description: "Configure or revise native recurring human tasks with explicit calendar-versus-completion timing, preserved unfinished work and checklist behavior, and verified saved settings. Use for task recurrence setup, not automated job schedules, calendar meetings, duty assignment or marking work done."
---

# Configure recurring tasks without losing unfinished work

Deliver a usable native repeating-task setup, or an exact configuration handoff when the chosen service cannot represent it. Establish what one completion means before choosing a repeat rule. A task that reappears on a date does not prove that the earlier work happened or that every missed period remains accounted for.

Use [automate-repeatable-task](../automate-repeatable-task/SKILL.md) when the repeated operation itself should run automatically, [change-recurring-calendar-series](../change-recurring-calendar-series/SKILL.md) for meeting/event changes, and [plan-personal-workweek](../plan-personal-workweek/SKILL.md) for allocating work time. This workflow configures human work records in an existing task service; it does not perform the underlying work or invent its schedule.

## Establish the task and its recurrence meaning

Read the request and selected current tasks. Resolve only missing facts that change the setup:

- Exact service/account, list or project, existing task IDs or authorized new task destination, and the requested change scope
- Work represented by one task completion, current unfinished work, first intended date and any fixed external deadline
- Calendar-anchored recurrence, such as a named weekday or month date, versus an interval after actual completion
- Date-only or clock-time meaning, relevant timezone, finite end/count or explicitly ongoing repetition
- Whether missed periods remain separate required work, can be skipped by agreement, or represent one still-open current task
- Checklist or subtask requirements, intended owner/audience, reminders and any existing rules that create follow-on effects

Do not turn “every month” into thirty elapsed days or “after finishing” into a fixed calendar cadence. An app's “workday” option may mean Monday–Friday rather than the user's holiday calendar; verify its meaning before using it. Establish an initial date separately from the rule for later occurrences. Some services supply today's date when none is specified; accepting that default can make a new task immediately overdue or send an unwanted alert.

Keep a planning date, due-date field, hard deadline, reminder time and recurrence end distinct. A separate deadline property need not stop repetition. A date-only task does not acquire midnight or a notification merely because a tool uses a timestamp-shaped value. If a legally significant or other consequential obligation has unsettled timing, retain the supplied requirement and leave that interpretation for the appropriate reviewer.

For an edit, identify whether the user means the next occurrence, the repeating pattern, a future boundary, or ending repetition. Do not apply an ambiguous “move it” to the whole pattern or rewrite historical completions. Preserve unrelated tasks and past records.

## Check the selected service's real capabilities

Use current official documentation and the actual account interface or connector. Determine how the service represents repetition: advancing an existing task, creating a new task after completion, or maintaining a series with individually addressable occurrences. These models have different identities, history and change scopes. A future calendar preview is not necessarily a collection of stored tasks.

Check the supported route for the requested rule, occurrence edit, end condition, checklist reset and saved-state readback. The UI and API may expose different fields. For example, the [Google Tasks API task resource](https://developers.google.com/workspace/tasks/reference/rest/v1/tasks) describes its scheduled-date field as date-only and says scheduled clock time cannot be read or written through that API. Do not claim a timed setup from an API date or encode unsupported recurrence as text in a title.

Look for these consequential platform differences without treating one product's rules as universal:

- [Todoist's recurrence guidance](https://www.todoist.com/help/todoist/features/introduction-to-recurring-dates-YUYVJJAV) distinguishes scheduled-date and completion-relative patterns and documents overdue cases that advance to a future occurrence. Verify the exact parsed rule and its special cases rather than assuming a similar-looking phrase preserves every period
- [Planner's recurrence guidance](https://support.microsoft.com/en-gb/planner/recurring-tasks-in-planner) describes a successor appearing after completion and warns that moving a due date can suppress intervening planned tasks. Check the applicable product experience
- [Google's repeating-task guidance](https://support.google.com/tasks/answer/12132599?hl=en) distinguishes next-task and series edits, restricts some task types and list moves, and warns that stopping repetition may require a new series to start again

If the tool cannot inspect or preserve the relevant setting, deliver the exact proposed configuration and missing capability. Do not silently substitute a custom scheduler, duplicate a calendar event, change services or create many dated tasks. Those can be useful alternatives only after the user chooses their different behavior and effects.

## Preserve identity, outstanding work and reusable content

Before changing anything, capture the relevant current task identity and revision, pattern, active date/status, applicable end condition, checklist/subtask state, owner, project/list, reminders and any affected links. Read the selected history or exception records needed to understand the requested change. Follow pagination and visibility settings where applicable; missing history is unknown, not proof that work was never completed.

Check for an existing matching setup using work purpose, destination, recurrence and task/series lineage. Similar titles alone do not establish duplicates. Conversely, different dates may be genuine period-specific obligations. Do not merge or delete them just to produce a tidy list.

Keep three things separate:

1. The recurring work definition
2. A particular outstanding or completed occurrence, including its intended period when relevant
3. The displayed next date or projected future occurrence

When the provider advances one record, retain whatever history evidence the task actually needs; do not invent per-occurrence IDs. When it creates successors, preserve the predecessor/successor relation only if the service or other evidence establishes it. A changed task ID is not automatically an unrelated task, and an unchanged ID is not proof that the same occurrence remains open.

If every missed period must be completed separately, a single rolling task that skips to the next future date may be unsuitable. Preserve existing outstanding records and show the mismatch before enabling or altering repetition. Ask for the missing choice between a supported per-period mechanism and an explicitly accepted skip policy. Do not mark old periods complete, delete them, or call them superseded without evidence and authority.

Inspect reusable content at the right level. Decide which checklist steps repeat, which one-time setup steps stay completed, and whether independent child recurrence already exists. [Asana's scheduling documentation](https://help.asana.com/s/article/scheduling-tasks-using-start-dates-due-dates-and-times) describes copying task fields and subtasks but excluding comments, and warns against independently recurring children under a recurring parent. Do not assume notes, attachments, ordering or completion history copy faithfully in another service.

Check whether reset behavior is task-specific, chosen at completion, or an account-wide default. [Todoist's subtask-reset guidance](https://www.todoist.com/help/todoist/features/reset-a-sub-task-in-todoist-V6SRBGPw0) distinguishes its general setting from a completion action and documents limits for nested subtasks and ordering. Do not change a global default to fix one task, or promise an ordered multi-level checklist when the native recurrence does not retain it.

## Prepare a small, concrete change map

Record the before/after values and expected scope. For a straightforward new private task, a short configuration record is enough. For an existing complex series, include the affected current occurrence, preserved historical/open items and any fields that the next cycle will copy or reset.

Check a few dates or transitions that distinguish the intended behavior:

- The first occurrence and next ordinary occurrence
- A late completion, with its effect on cadence and intervening unfinished periods
- A one-time reschedule versus a pattern edit, when that operation is requested
- The relevant finite end/count, month-end, holiday or clock-change boundary, if the rule encounters one

Derive these expectations from the selected service's documented semantics and the user's intent. Keep date-only arithmetic as calendar arithmetic. For timed recurrence, retain the named zone and check date-specific offsets when they matter. If an ambiguous/nonexistent local time or unsupported month-day rule changes the result, resolve it instead of silently normalizing.

Do not infer lifecycle behavior from the next visible date alone. In particular, [Todoist's completion guidance](https://www.todoist.com/help/todoist/features/complete-a-task-with-a-recurring-date-dmI6SVqdP) documents special consequences of completing manually rescheduled tasks and a limited immediate undo path. Inspect the exact operation, including whether it would skip periods or create another successor.

State what has been checked from documentation, what has been read from the actual saved task, and what remains unobserved. An authorized private disposable pilot can establish additional behavior when genuinely needed, but setup does not authorize creating test tasks, triggering notifications or completing real work as an experiment. Never advance an unfinished real task merely to see what the next date becomes.

## Save only the authorized configuration

A clear request to set up an ordinary private recurring task can authorize its configuration; do not insert a redundant approval round once the necessary meaning is settled. A proposal-only request stops before saving. Resolve any newly discovered material difference first, such as a shared destination, new assignee, broadened audience, unsupported skip behavior or changed reminder delivery.

Keep task titles, notes and references appropriate for the destination. Do not copy sensitive source material into a shared list, notification preview or new service. Task setup does not authorize credential creation, permission changes, separate messages, reassignment of other people or new integrations. Preserve existing sharing and unrelated notifications. If a provider forces a material side effect outside the request, explain it before proceeding.

Immediately before saving, reread the affected task and compare its relevant fields with the change map. A concurrent completion may already have advanced the cycle. Refresh the plan rather than writing the old date back or editing the wrong successor. Use the smallest supported mutation and preserve unrelated fields; do not replace a full task from a partial read.

Retain returned identities and inspect the saved state. If changing several tasks, finish and verify each separately so a partial batch does not lead to recreating all of them. Do not complete, delete or regenerate tasks as an incidental way to apply a setting. Ending repetition needs the correct supported operation: stop repeating, remove a pattern, complete forever and delete a series can have different effects on current work and history.

## Acceptance, recovery and delivery

Reopen the exact saved task or supported native details and verify:

- The intended account, destination and identity, without an unintended duplicate series
- The parsed recurrence, anchor, first/current date, time meaning and end condition
- Scope of the edit, with existing outstanding work and historical completions preserved
- Checklist/reset behavior and inherited content to the extent the service exposes it
- Unchanged owners, access and unrelated fields; intended reminder settings and known notification effects

Separate configuration evidence from occurrence execution. A saved pattern does not establish that a future task was created, a reminder was delivered, or the user completed the work. Do not require a real completion to call a checked setup configured. State any essential lifecycle behavior that could not be verified through available settings or documentation.

Handle failures without falsifying task history:

- **Uncertain create or update:** inspect the precise destination, task identity, current pattern and changed fields before retrying. Do not infer failure from a timeout or create another copy blindly
- **Unexpected successor or changed date:** inspect the current task and available completion/history evidence before another mutation. Do not repeatedly complete or reopen tasks to force the expected date
- **Concurrent edit/completion:** preserve the newer state and reconcile only compatible requested changes. Hold conflicting fields or an unclear occurrence boundary
- **Partial setup:** report which tasks and fields are saved, unchanged or uncertain. Continue independent checks; restore only authorized changes that are still attributable to this work
- **Unsupported preservation or stopping:** leave the affected operation pending and provide the exact capability/decision needed. Do not treat delete-and-recreate as an equivalent reversible correction

Deliver the verified task link when available, a concise description of its cadence and late-completion treatment, preserved open work, checklist behavior, actual saved changes and verification limits. For blocked setup, return the complete platform-specific proposal rather than saying it is active. Include how the requested cycle can be changed or stopped, with any loss of restartability or history clearly explained. Stop at the requested setup or revision; do not add monitoring or record future completions without separate scope.

## Fictional illustration, not executed

A fictional user wants a private camera-kit inventory on the first day of each month. The first planned check is 1 November 2026. One completion covers that month's inventory; the user's approved routine does not require separate catch-up checks for skipped months. A late completion on 4 November should leave the next planned check on 1 December. A different request, thirty calendar days after completion, would instead point to 4 December. These are two intended policies, not interchangeable date strings.

The reusable checklist contains inspect cases and reconcile equipment labels. A one-time step, prepare the initial inventory sheet, must not reappear. The setup therefore needs supported recurring steps while preserving the one-time completion. If the chosen app resets every child with no suitable per-task distinction, the proposed structure needs a user-approved adjustment before activation. An existing October task cannot be discarded merely because the new rule starts in November; its outstanding status is reported separately.

No task was created, completed, moved or deleted; no notification or provider pilot ran. The dates and records are original fictional inputs for a static illustration, not observed product behavior.
