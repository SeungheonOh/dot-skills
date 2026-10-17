---
name: automate-repeatable-task
description: Turn a repeated task into a dependable reusable workflow, script, or supported automation with verified inputs, effects, outputs, and recovery. Use when the user wants a process made repeatable or scheduled, rather than a single reminder or diagnosis of an existing integration.
---

# Automate a Repeatable Task

Make the repeated operation work, then establish how it will run again. Deliver the usable mechanism and a verified representative result. Keep a prepared workflow, a manually runnable script, and an enabled background automation clearly distinguishable.

## Understand one run before repeating it

Identify the repeated unit of work, source scope, transformation or decisions, output, and destination. Inspect an actual example and the user's current process where available. Separate stable rules from judgment the user still needs to exercise.

Establish what the user wants to automate. “Make this report rerunnable” can mean a manual command; it does not necessarily request a schedule. “Send this each Friday” requires an actual supported trigger and delivery configuration. Ask when that distinction or a missing rule changes the implementation, not for every routine detail.

Define the authorized effects. Reading a source, preparing a file, updating a record, and sending a message are different operations. For recurring delivery, establish the recipient or audience and the bounded information to share. A successful first run does not grant broader future access, new recipients, or unrelated actions.

Use only the source and destination access actually available. Check required connections and capabilities before choosing a persistent mechanism. A tool name in a plan does not establish that it exists or supports the needed trigger. Use an available supported scheduler when scheduling is requested; do not imply that a saved script runs in the background by itself.

## Choose the simplest dependable mechanism

Prefer a form the user can operate and maintain: a documented repeatable procedure, a local command, an existing application workflow, or a supported scheduled automation. Match the mechanism to the requested outcome, available environment, and frequency of change. Do not build a service or introduce a framework when a small reusable operation is enough.

Keep variable inputs explicit, such as the source file, reporting period, selected project, or output folder. Validate the values that affect correctness before producing results. Do not infer a period from the current date if the user needs a reproducible historical report.

Separate the repeatable work from the trigger. First establish that one run produces the right result. Then configure manual invocation, a schedule, or a supported event as requested. Use the user's timezone for clock-based timing and preserve calendar semantics; a monthly task is not automatically a fixed number of days. Distinguish a real event subscription from periodic polling and check the platform's supported limits.

For scheduled work, separate the intended occurrence, the data period it covers, and its actual start time. Preserve explicit period boundaries and timezone when a delayed run starts; recomputing “yesterday” from the recovery time can select a different population. Use a logical run identity appropriate to the agreed scope and period so duplicate triggers can be recognized. Record configuration revisions as provenance without assuming a changed revision permits repeating an already completed effect. Check the actual scheduler's treatment of missed starts and repeated or nonexistent local clock times. [Kubernetes CronJob documentation](https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/#job-creation), for example, warns that scheduling can create two Jobs or none for an occurrence; do not generalize that provider's behavior to another scheduler.

Choose an explicit missed-run rule when it matters: skip expired work, combine only when one result genuinely covers the missed work, or catch up selected periods in a defined order and bounded batch. Keep catch-up within the authorized dates, effects and audience. Preserve failed or uncertain periods as unresolved; advancing a contiguous completion marker past them must not lose their work. A latest-state refresh can replace older refreshes, but it cannot stand in for separately required historical reports or per-event effects. Verify what the chosen mechanism can actually enforce; if it cannot retain period identity or honor the recovery rule, expose that limitation before enabling it.

Keep secrets out of source code, logs, and generated reports. Use established approved connections. Creating credentials or expanding persistent access requires the applicable authorization; the desire to automate does not remove that boundary.

## Define repetition and recovery

Choose behavior for inputs already seen. A report rebuilt from a complete snapshot may safely replace a designated output under the user's instructions. An operation that appends rows, creates items, or sends messages needs a way to avoid applying the same effect twice. Use stable source identities, versions, or a supported idempotency mechanism where relevant; a changed filename alone may not establish a new record.

Keep enough state to resume accurately, without inventing a stateful system for a simple read-only transformation. Distinguish received input, completed transformation, saved output, and confirmed delivery when those stages can fail separately. Record only the progress and provenance the workflow needs.

Define the failure path before enabling repetition:

- A missing or invalid input should produce a specific issue, not an apparently complete result
- A partial source fetch should not silently shrink the report's population
- A failed write should leave the prior useful output intact where the destination supports it
- An uncertain external result should be inspected before retrying, so a timeout does not create a duplicate effect
- An unexpected change in source scope or contract, schema, permission, or consequential rule should stop the affected operation for review rather than silently broaden behavior. Normal input updates within the agreed contract should remain runnable

Use bounded retries for failures that are actually safe to retry. Make permanent failures and decisions needing the user visible through an authorized channel. Avoid retry loops that repeatedly perform side effects or produce a flood of notifications. If overlapping runs are possible, use the destination's supported safeguards or prevent overlap where needed.

## Prove a representative run

Execute the repeatable operation on an appropriate original or approved sample within the authorized environment. Inspect the real output or changed state against the expected rules. A log saying “success” or a command exiting normally does not establish the report's contents or its delivery.

Check the repetition behavior that matters: the same input again, an updated input, or recovery from a meaningful interrupted step. Use a small relevant case; do not build an elaborate fault harness for a simple file transformation. Preserve originals and test data boundaries.

When the workflow includes a judgment step, keep that decision visible and make the surrounding work reusable. Do not invent an approval or select a consequential option merely to demonstrate a fully automatic run.

## Activate only the requested repetition

For a manual workflow, deliver the actual command or procedure, its inputs, output, and recovery instructions. Verify that another run can use the documented interface. Do not call it scheduled.

For a requested schedule or event, verify the saved configuration: source scope, trigger, timezone when applicable, action, destination, and stop or pause behavior. Use the provider's actual setup/readback. Respect missing permissions and access denials; finish the prepared work and identify the specific blocker instead of claiming activation or using an unsupported alternate route.

Distinguish configuration from future execution. A saved schedule establishes setup; an observed run and its output establish execution. Report the actual state, how the user can change or stop it, and any remaining limitation. Do not promise uninterrupted future operation or automatic recovery beyond what was implemented and verified.

## Additional static illustration: a late report run

This original fictional illustration is unexecuted. A workflow is specified to save one local report each day at 08:00 UTC for the preceding UTC calendar day. The October 16 occurrence is delayed until October 17 at 09:00. Its report still covers October 15 from 00:00 inclusive to October 16 at 00:00 exclusive; the October 17 occurrence covers October 16. The agreed recovery rule processes these two periods oldest first, using separate period identities and preserving any unresolved outcome. A duplicate trigger for the first occurrence checks that period's recorded outcome instead of changing its period to “yesterday.” No report was generated, schedule enabled or recovery executed for this illustration.
