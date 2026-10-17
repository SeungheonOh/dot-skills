---
name: configure-work-tracker-view
description: "Create or revise a saved native list or board view over existing work items, with faithful filters, useful grouping and verified save scope. Use for a reusable tracker view, not prioritizing work, changing item records, redesigning workflows or building a reporting app."
---

# Configure a useful work-tracker view

Deliver the saved view the user can return to, or a complete platform-specific configuration when saving is unavailable or outside the request. Establish which records belong before arranging their cards. A screenshot, temporary search or attractive empty board does not establish a working saved view.

Use [issue-backlog-prioritization](../issue-backlog-prioritization/SKILL.md) to decide importance or execution order, [analyze-work-item-flow](../analyze-work-item-flow/SKILL.md) for historical delivery measures, and [plan-project-delivery](../plan-project-delivery/SKILL.md) to plan the work itself. This guide configures retrieval and presentation of existing work; it does not create missing tasks, assign people or change the team's workflow.

## Establish the view and its audience

Read the request, current tracker and relevant existing view before asking questions. Identify:

- Exact service, workspace, project/team and existing view or board IDs; whether this is a new view or an edit
- The recurring question the view should answer, record types and hierarchy level, and important included and excluded cases
- Source fields and their identities, accepted status/label meanings, ownership conditions, and any date window with timezone and boundary rules
- Requested layout, useful visible fields, grouping, ordering and handling of empty values
- Who should see and maintain the view, whether settings are personal or shared, and the authorized destination
- Available capabilities for reading records, inspecting settings, saving the view and reopening it

Use existing definitions rather than inventing priorities, categories or commitments. Ask only about ambiguity that changes membership or external effects. “My open work” may require resolving whether it means assigned items, authored items or watched items; a color preference need not block a sensible draft. If the user wants a fixed list, preserve those exact identities instead of silently replacing it with a changing query.

Inspect the actual account and product edition. A connector that can list issues may not support creating views. Use a supported native route within the authorized environment, or deliver the exact filters and settings with the missing action identified. Do not substitute a new service, custom dashboard or scheduled export without agreement.

## Preserve the source and shared configuration

Record the existing view's identity, query, backing-filter identity, layout and save scope before changing it. Include owners, audience and known dependent boards, reports or subscriptions when a reused filter is involved. A personal variation should not overwrite a shared filter. Creating a separate view can preserve the original, but first check its creation defaults: a new view is not necessarily private or unsaved.

An existing subscription may send different records after a filter change even when its notification settings stay untouched. Check those dependent effects before editing a subscribed view. Hold an expansion beyond the authorized information or audience; propose a separate view when suitable. Do not silently disable existing subscriptions to avoid the question.

Keep item content, statuses, assignments, dates, links, estimates and manual ranks unchanged. Do not drag a card to check appearance, edit a cell to improve grouping, add a sample issue or change a field's options. These can mutate source records. [GitHub's board documentation](https://docs.github.com/en/issues/planning-and-tracking-with-projects/customizing-views-in-your-project/customizing-the-board-layout) explicitly describes field changes when cards move between columns or groups.

View access and record access are separate. Restrict the destination to the audience authorized by the user; do not broaden project permissions to make the view work. Hidden columns and filters are presentation choices, not a security boundary. Keep sensitive issue titles, query text and screenshots out of wider destinations. A view request does not authorize notifications, channel subscriptions, ownership transfer or granting new credentials. Missing access is an unresolved coverage limit, not an empty workload.

## Translate the question into exact membership

Write a compact membership rule in ordinary language before entering the platform expression. Bind it to actual field and option identities, including same-named statuses in different teams. Distinguish a tracker item's open/closed state from a project's custom status; they need not agree. Keep draft items, issues, pull requests, parents and children distinguishable when the service mixes them.

Resolve the conditions that commonly change the answer:

- **Boolean logic:** retain parentheses and the difference between any and all. Do not approximate an unsupported cross-field OR with an AND or broaden it to unrelated work
- **Empty values:** explicitly decide whether unassigned, undated or unlabeled items belong. Negation may exclude blanks; [Jira's operator reference](https://support.atlassian.com/jira-software-cloud/docs/jql-operators/) documents this for its not-equal and NOT IN operators
- **Dates:** distinguish due, created, updated, completed and iteration dates. Preserve fixed versus rolling windows, local-day boundaries and inclusive/exclusive limits. An updated timestamp does not prove substantive progress
- **Relative identity:** “current user” may resolve differently for each viewer; a named assignee is fixed. Choose the meaning the user requested, not the identity used during setup
- **Hierarchy and lifecycle:** decide whether children, archived items, completed work or triage items are in scope. A missing parent must not silently exclude a matching child unless the requested rule says so

Use current supported query syntax or the native filter builder. [GitHub Projects filtering](https://docs.github.com/en/enterprise-cloud%40latest/issues/planning-and-tracking-with-projects/customizing-views-in-your-project/filtering-projects) distinguishes combining fields from supplying alternatives within one field; syntax from the separate issue-search interface is not interchangeable. If the requested expression cannot be represented, show the precise limitation and a faithful alternative for the user to choose. Do not change item labels to make the query possible.

Before saving, compare candidate membership with existing known examples: a clear include, a clear exclude, and a meaningful boundary such as an empty owner or mixed status. Use actual authorized records without editing them. Where an independent complete record set is available, reconcile exact IDs. For large or partially accessible scopes, state the checked cases and coverage rather than claiming exhaustive membership.

## Make the visible result match the membership

Inspect layers beyond the main query: project scope, backing filter, board sub-filter, quick filters, search text, selected swimlane, hidden columns, collapsed groups, archive rules and hierarchy display. Diagnose a missing known item by its stable ID before changing the query. It may match the filter yet be hidden by the board. [Jira's column guidance](https://support.atlassian.com/jira-software-cloud/docs/configure-columns/) notes that unmapped statuses can remove matching items from board and backlog displays.

Change only layers included in the request. A shared status-to-column mapping can affect other users and operational behavior; do not remap it merely to make a personal view look complete. Use an authorized alternative layout or identify the additional decision needed. Keep a legitimate exclusion visible in the handoff instead of claiming the view covers all work.

Choose a layout that supports the question: a list/table for scanning dates and fields, or a board when grouping helps work review. Show enough identity and context to distinguish similar titles. Preserve empty/unassigned groups when they matter. Set ordering without manufacturing dates or priorities. Do not claim a stable tie order that the provider cannot save. Keep manually ranked order unchanged unless its alteration is explicitly requested.

Check group counts against what they measure: unique items, displayed occurrences, estimates or other sums. Parent and child rows are not automatically equal delivery units, and one item can appear in more than one grouping. Visual limits are not necessarily enforced capacity controls. A view is not a performance assessment of its assignees.

## Save the intended layer and verify it

Distinguish temporary filters, personal display preferences, a persistent view definition and shared defaults. For example, [Linear's display options](https://linear.app/docs/display-options) distinguish personal changes from workspace defaults and note that manual ordering can affect everyone. [GitHub's view management](https://docs.github.com/en/issues/planning-and-tracking-with-projects/customizing-views-in-your-project/managing-your-views) distinguishes unsaved configuration changes from automatically saved creation, renaming and tab order. Check the current service rather than assuming every control waits for Save.

1. Prepare the smallest before/after configuration needed, preserving unrelated settings and shared dependencies
2. Confirm the actual save audience and effects match the request. If a private setup would necessarily create a team-visible object, ask before that action; otherwise proceed within existing authority without a redundant approval round
3. Save through the supported interface. Retain the returned view/filter identity and actual URL, not a guessed address
4. Reopen the canonical saved view through its native navigation. Inspect persisted filters, layout and audience, distinguishing saved settings from any personal overlay
5. Recheck decisive included/excluded IDs and meaningful empty-value cases. If records changed during setup, refresh those records and explain the difference; do not force a moving live set to equal an earlier count

Do not rely solely on the browser URL for verification. [Linear's custom-view guidance](https://linear.app/docs/custom-views) explains that URLs can carry temporary filters and that a copied link does not grant view access. Verify recipient access through available permission evidence; do not impersonate another user or broaden access. If another viewer's result was not observed, say so, especially for relative-user queries.

Use readback and inspection for setup checks. Do not manufacture a real issue, alter an assignment, trigger an automation or send a notification just to demonstrate that the view updates.

## Acceptance and recovery

The deliverable should identify the saved view or complete proposed settings, the membership rule, meaningful exclusions, save/audience scope and actual checks. Include only the unresolved limitations that affect use. A small view does not need a separate audit workbook.

Call it configured only when its identity and intended settings are saved and read back. Call its membership checked only to the coverage actually inspected. Record access, loading or pagination gaps separately from zero matching items. A useful saved view can be delivered with a specific unverified audience or boundary case clearly disclosed; do not claim that case passed.

If saving times out, inspect the destination for the exact created or changed view before retrying. Reconcile partial changes one setting at a time. If shared settings changed concurrently, retain the newly observed state and resolve the conflict instead of restoring an old snapshot over someone else's work. Revert only your authorized changes after checking they are still yours; deletion of a duplicate or recovery object is not an automatic cleanup step.

If the final view hides required work, keep the affected acceptance claim open, isolate the filtering or display layer, and correct only the authorized setting. When blocked by access or unsupported semantics, deliver the prepared configuration, exact missing capability and any verified partial result. Stop at the requested saved-view outcome; do not add recurring monitoring or notifications.

## Fictional illustration, not executed

A fictional Flint team requests a view of its Review or Blocked items assigned to Riley or nobody, grouped by status. Four supplied fictional records are FLT-17 (Review, Riley), FLT-18 (Blocked, unassigned), FLT-19 (Review, Morgan) and FLT-20 (Done, Riley).

The intended rule is Flint AND (Review OR Blocked) AND (Riley OR empty assignee). Its expected membership is FLT-17 and FLT-18. A leftover personal quick filter for Riley would hide FLT-18 even if the saved rule were correct. The preparation therefore calls for checking that overlay, preserving FLT-18's empty assignment, and reopening the saved view without the extra filter. If the platform cannot express the empty-or-named condition, the configuration remains a proposal pending a faithful supported choice.

These records and expectations are original fictional material. No tracker, query, view, save, permission or notification was exercised for this illustration.
