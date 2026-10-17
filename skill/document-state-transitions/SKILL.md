---
name: document-state-transitions
description: "Derive a version-bound lifecycle reference from existing state-machine definitions or workflow rules, preserving state identity, guards, effects, hierarchy and unknown event handling across a transition table and diagram. Use for documenting established behavior, not designing a state machine, executing transitions or proving reachability."
---

# Document a lifecycle without inventing its rules

Turn an existing stateful workflow into a usable transition reference: what state means, which event can change it, what must hold, what effects occur and what remains unspecified. The deliverable is a source-linked state/transition register with a faithful diagram and text alternative, not an attractive chain of status names.

Use [design-data-model](../design-data-model/SKILL.md) when state and history requirements still need deciding, [find-finite-workflow-counterexamples](../find-finite-workflow-counterexamples/SKILL.md) for bounded exploration of a supplied model, and [build-stepwise-trace-explorer](../build-stepwise-trace-explorer/SKILL.md) for an interactive teaching artifact. This workflow documents existing rules and does not certify runtime correctness, authorization safety or eventual completion.

## Inputs and authority

Identify the lifecycle owner/object, exact source revision and runtime or notation when relevant, states/events in scope, intended reader, requested format and private destination. Sources may be a state-machine definition, versioned workflow specification, operation rules or passive inspection of the controlling code. Use existing traces only as observations; a few recorded paths do not enumerate the allowed machine.

Establish whether the document describes a normative contract, configured implementation or observed subset. Keep those claims separate. A status enumeration alone supports a state-name inventory, not legal transitions. If only status names exist, deliver that inventory and ask for the transition rules rather than inventing forward/back arrows.

Return a state register, transition table, editable diagram source and readable export when supported, with source locators and unresolved rules. Preserve prior source and documentation versions. Do not run imported machines, evaluate guard expressions, invoke callbacks, submit state-changing requests, reset workflows or generate a controller under a documentation request. Do not send internal workflow detail to an unapproved renderer or recipient. Use fictional examples and omit unnecessary payloads, personal case details and secrets.

## 1. Establish what one state describes

Define the object/session being tracked and the scope of its identity. Separate persisted business status from UI display state, transport connection status and a worker's execution phase unless the sources intentionally combine them. Two objects with the same status are not one state-machine instance.

Give each state a stable qualified ID, original name, meaning, source locator and applicable parent/region. Keep identical labels in different regions distinct. Record which states are initial, final, transient, composite or simply ordinary only when the model supports that classification.

An initial state must be tied to the relevant creation or entry condition; a default field value does not necessarily describe every restored or migrated instance. An apparent final status with no visible outgoing edge may just be the end of the inspected scope. Preserve documented reopening, compensation and external deletion separately rather than declaring such states impossible to leave.

For hierarchical or parallel models, record the active-state configuration the source uses. Do not flatten simultaneously active regions into mutually exclusive values of one status field. If a simplified overview hides substates, name that simplification and retain the detailed register.

## 2. Extract transitions as complete rules

For each transition record, as applicable:

- Stable transition ID and source locator
- Source state/configuration and target state/configuration, including unchanged-state behavior
- Triggering event or eventless condition, and its parameters needed for interpretation
- Guard and the point at which it is evaluated
- State/data updates and separately described side effects
- Entry/exit actions, ordering/priority and event-consumption rules established by the source
- Timing, failure and retry conditions that alter the transition

Keep trigger, guard and action distinct. “Submit” might be an event; “all required fields present” a guard; “send notification” an effect. Do not make an effect's successful completion implicit in arrival at a named state unless the source defines that boundary. A request to cancel is different from a transition confirming cancellation.

Retain exact predicates and constants in the table with a readable explanation beside them. Never execute expressions copied from an input. A missing guard may mean unconditional only under the source language's rules; missing documentation means unknown. Do not change a strict comparison, time unit or null case while simplifying a label.

Preserve multiple transitions with the same source/event when their guards, priorities or targets differ. State the actual selection rule if established. Do not sort the table alphabetically and imply that display order determines precedence. If conditions overlap and priority is unknown, retain the ambiguity; do not choose a preferred path.

Distinguish rejected, ignored, deferred and unhandled events when the source distinguishes them. A state/event pair with no extracted transition is unspecified in this document unless the contract or engine semantics establish the consequence. Label those evidence states in a coverage table rather than silently treating all blank cells as forbidden.

## 3. Preserve lifecycle semantics beyond arrows

Apply the actual source engine's documented semantics. [SCXML's transition rules](https://www.w3.org/TR/scxml/#transition) provide one concrete example: a targetless transition can perform actions without changing the active configuration, while a self-targeting transition can exit and re-enter its state. A simple loop arrow does not preserve that difference. Do not apply SCXML behavior to another runtime merely because its drawing looks similar.

When hierarchy matters, document applicable inherited transitions, entry targets, history behavior and parent/child completion only as established. Parallel regions need their coordination rules; completion of one region does not by itself establish completion of the whole lifecycle. Keep the source's distinction between an intermediate completion event and final termination visible. The [SCXML recommendation](https://www.w3.org/TR/scxml/) defines these concepts for SCXML models; use corresponding primary documentation for other engines.

For timers, retain when the timer starts, what cancels/resets it, the clock or duration basis and what happens if its event arrives after another transition, when specified. Do not infer an exact timer from a prose phrase such as “eventually expires.” For an external side effect, retain whether the state update happens before, after or independently of its acknowledgment. Unknown atomicity stays unknown.

Keep attempts and lifecycle instances separate where retries create a new attempt. A path returning to a previous label may preserve counters or prior effects; it is not automatically an undo. Reopening and compensation should be described by their actual updates rather than drawn as reversing history.

When implementation and specification disagree, attach each claim to its source and version. Do not add a missing transition, adjust a guard or reinterpret a final state to resolve a documentation conflict. Complete unaffected regions and give the owner the smallest question that changes the reference.

## 4. Build a readable projection and text alternative

Select the requested notation and supported renderer/version. [Mermaid state diagrams](https://mermaid.js.org/syntax/stateDiagram.html) can express transitions, composite states, choices and concurrent regions; their visible symbols are not an executable guarantee of another engine's behavior. Check the actual target's syntax and limitations before choosing a representation.

Use stable state IDs with readable labels and transition IDs. A concise label can show event, guard and effect in a declared convention, with long rules retained in the transition table. Do not use a choice node to imply mutually exclusive branches or a join to imply synchronization unless the source supports it. Provide a legend for any simplified notation.

Keep internal/targetless transitions, entry/exit actions and unsupported hierarchy details in explicit notes or companion tables if the drawing cannot faithfully encode them. Link overview nodes to detailed regions; do not remove timeout, rejection or recovery paths merely to fit a page. A state with no displayed outgoing edge must have its scope or terminal meaning explained.

Provide a plain-language path description and state/event lookup so the image is not the only usable reference. Use safe escaped labels, and disable or avoid remote includes and active content when processing untrusted source text. Render only through an authorized route; when unavailable, deliver source and tables as an unrendered candidate with a named visual check outstanding.

## 5. Accept the reference and handle revisions

Reconcile the saved register to the source before reviewing appearance:

1. Every selected state/transition is present or explicitly excluded; qualified identities and initial conditions agree
2. Every diagram edge has a table row, and every omitted table transition has a visible detail/scope reference
3. Guards, priorities, event parameters and effects retain their meaning; unchanged-state effects do not become false re-entry
4. Known rejected/ignored/deferred events remain distinct from unspecified state/event pairs
5. Hierarchy, parallel regions, completion and timer semantics are preserved or explicitly marked as unrepresented
6. Declared rules, implementation observations and unresolved conflicts remain visibly different

Walk a representative accepted path and a relevant guard-false, repeated-event, timeout or unchanged-state case on paper when those cases exist. Carry the necessary state/data values through each step and check the documented consequence against its source. Do not call a paper walkthrough a test, exhaustive reachability analysis, deadlock check or proof that an implementation enforces the rules.

Inspect any rendered final output for clipped guards, overlapping loops, ambiguous source/target endpoints and lost region boundaries. Read back the text alternative and verify source links. A syntax-valid diagram can still express the wrong machine; a reviewed transition table does not prove a separate export rendered correctly.

For new revisions, retain stable IDs where meaning is unchanged and classify changed guards/effects separately from renamed labels. Preserve the earlier reference until the replacement is ready. If extraction is incomplete or a rule depends on unavailable dynamic configuration, label that area partial and name the evidence needed. On a failed or uncertain save, check the destination before retrying and preserve concurrent edits rather than overwriting them.

Return the covered lifecycle/version, artifact locations, unresolved behavior and actual checks. Stop at a usable documented contract with honest limits; redesign, model checking, live transitions and publication require their own scope and authority.

## Fictional, unexecuted illustration

A fictional job specification defines queued, running, cancelling, succeeded, cancelled and failed. Start moves queued to running. Cancel while running only moves to cancelling; a later cancellation-confirmed event moves cancelling to cancelled. A documented completion race permits a finished event to move either running or cancelling to succeeded. A progress event updates progress while remaining in running, with no exit/entry actions.

The expected table keeps cancel-request and cancellation-confirmed separate, preserves the cancelling-to-succeeded race, and records progress as an unchanged-state effect. The diagram does not imply that requesting cancellation guarantees cancelled, or that a progress update restarts the job. The source names failed but supplies no incoming failure rule, so the reference retains failed with its entry behavior unresolved. Retry behavior after failed also remains unspecified rather than forbidden or automatically allowed.

This is an authored illustration. No state machine, guard, workflow action, model checker, renderer or application was executed.
