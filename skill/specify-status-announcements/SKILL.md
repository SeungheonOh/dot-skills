---
name: specify-status-announcements
description: "Prepare an event-to-message contract for dynamic web status updates, specifying truthful wording, focus versus announcement behavior, live-region ownership and stale or repeated-message handling. Use for an accessibility content/integration handoff, not general UI copy, async implementation repair or a live screen-reader audit."
---

# Specify which changes need to be announced

Produce a version-bound status-announcement handoff for an established web flow. It should tell the content author and implementer which event permits a message, what meaningful information it carries, where it remains available, and how competing updates are handled without taking focus unnecessarily. A list of toast strings or a blanket instruction to add a live region is not enough.

Use [design-user-interface](../design-user-interface/SKILL.md) when the flow and visible states still need deciding, [reconcile-obsolete-ui-requests](../reconcile-obsolete-ui-requests/SKILL.md) to implement stale-result ownership, and [keyboard-form-completion-check](../keyboard-form-completion-check/SKILL.md) for an actual form journey. This guide prepares the event/content/accessibility contract. It does not implement an announcer, run the product, produce timed-media captions or certify accessibility.

## Inputs and authority

Identify the flow/components and revision, accepted state/event descriptions, current visible messages, completion evidence and cancellation/retry semantics. Include the target browser/assistive-technology support policy when supplied, existing design-system announcement mechanisms, and requested artifact destination. Record whether the deliverable documents existing behavior or proposes the intended contract.

Prefer approved event definitions and minimal synthetic scenarios over production logs containing personal records. Source code may be read as passive text; an event handler's existence is not proof of its observed announcement. Do not execute requests, activate notifications, change accessibility settings, create a live test account or send messages under this preparation task.

Keep the packet and its source excerpts within the approved audience. Announcements can expose information beyond a visually abbreviated label, so include only the necessary approved context. Do not insert secrets, full addresses, health details or another person's data into sample strings. Preserve current copy and integration notes; publication and changes to the application remain separate actions.

## 1. Classify the changes before writing strings

Build a small event inventory from the actual flow. For each event state its cause, current object/request identity, visible change, whether focus changes, and what the user needs to know. Separate:

- A non-focus-taking status update about waiting, progress, results or errors
- A control-state change already represented by the control's semantics
- A navigation or dialog transition with its own focus/context contract
- Ordinary newly available content that the reader can navigate
- A genuinely important time-sensitive alert

Use the [WCAG status-message explanation](https://www.w3.org/WAI/WCAG22/Understanding/status-messages.html) to distinguish status messages from all dynamic content. A result count and a result list are different; expanding a disclosure does not make all revealed text a status message. Do not classify every DOM mutation as something to announce or add messages solely to populate a catalog.

For each candidate, record the reason for notifying, using ordinary semantics or deliberately remaining quiet. Quiet handling must not hide an important visible status from users who do not see it. Conversely, duplicating a control's state or a focused dialog's full text through a separate channel can produce confusing repetition. Keep these decisions tied to the actual experience, not to message severity names in a backend log.

## 2. Bind wording to an evidenced event

Create catalog rows with a stable message ID and only the applicable fields:

- Trigger and required evidence, including the owning request/object/version
- Visible wording and the meaningful information the announcement must convey
- Placeholder definitions, units, plural/zero forms and localization constraints
- Presentation location and whether it persists, replaces earlier text or joins a history
- Intended announcement mechanism/priority and whether focus stays or moves elsewhere
- Suppression, replacement and recovery rules, with source or proposal status

Make pending, confirmed completion, partial completion and unknown outcome distinct. “Saved” requires the product's defined save acknowledgment; a click, queued request or local edit does not establish it. If the service only confirms receipt, say that rather than promising completed processing. If Cancel only stops waiting, the wording must not claim a remote effect was reversed.

Write a self-contained meaningful unit: object/task plus outcome and next step when needed. A changed number alone may lose the context provided visually by surrounding text. Keep visible and nonvisual versions equivalent in consequential meaning, even if a short contextual phrase is added for clarity. Do not hide a materially stronger promise in a screen-reader-only string.

Define zero, singular, plural, unknown and partial values when the flow uses them. Keep placeholder identities separate from their wording, and use the product's existing localization mechanism rather than concatenating sentence fragments. Never turn unknown counts into zero or use a fake percentage when progress is indeterminate.

## 3. Specify the announcement surface

Select the smallest established mechanism that fits the message. [ARIA22](https://www.w3.org/WAI/WCAG22/Techniques/aria/ARIA22) describes role=status with polite and atomic defaults, while noting that some environments need explicit atomic handling. Use a concise status region for routine outcomes; describe which contextual text belongs in its update unit and require the intended whole-phrase behavior to be checked. Avoid making the entire application or results table atomic and live merely to announce a short outcome.

Use an alert only when its importance and timing justify it. The [APG alert pattern](https://www.w3.org/WAI/ARIA/apg/patterns/alert/) keeps alerts from moving keyboard focus and warns about frequent interruptions or disappearing information. If the interaction requires acknowledgment or a decision, use the separately specified dialog/focus behavior; an alert role is not a substitute for an operable dialog.

For a genuinely sequential history, [ARIA23](https://www.w3.org/WAI/WCAG22/Techniques/aria/ARIA23) describes the log role. Decide whether this flow needs retained entries or only its current state; do not create a history containing sensitive data just because a log is available. For progress, [ARIA25](https://www.w3.org/WAI/WCAG22/Techniques/aria/ARIA25) separates progressbar state from a live status update. Define useful milestones or a product-appropriate update policy rather than narrating every increment.

Document the chosen region's lifetime, owner, initial state and relevant update types. Establish a status region before the update it is expected to expose; record mounting/reuse as an integration obligation rather than promising that newly inserted populated content always announces. Specify the intended atomic context and whether meaningful removals need equivalent text. Ordinary cleanup should not read as a new user event.

If aria-busy is used to group related updates, state which region is busy, when it clears, and what coherent result becomes available. The [WAI-ARIA specification](https://www.w3.org/TR/wai-aria-1.2/#aria-busy) defines busy and live-region properties; they do not verify server completion or guarantee a spoken queue. Avoid conflicting nested announcers and redundant mechanisms that expose one event more than once. Keep exact markup choices with the actual component integration when it is not yet known.

## 4. Reconcile competing and repeated updates

Give each announcement an ownership boundary. If search B supersedes search A, a late A result must not announce as the current result, even if the visible UI correctly ignores it. Include stale errors and cleanup messages as well as stale successes. A component closing or navigation changing context may invalidate its pending routine announcements; identify which important outcome still needs an approved persistent destination.

Define duplicate suppression by meaningful event identity, not only by equal text. A retry that genuinely succeeds after failure is a new outcome even if its success wording matches a prior operation. Re-rendering the same confirmed event is not a new success. Repeated identical strings may not automatically produce repeated announcements in every environment; record this as a target integration/verification requirement rather than prescribing arbitrary clearing delays.

Separate “replace stale pending text” from “discard important outcomes.” Coalesce rapid progress updates while retaining the current state and final result. Do not let a routine progress update overwrite an unresolved actionable error. If several independent tasks run at once, identify the task in each message and set a policy for summarization or ordering; avoid one global last-message field that makes unrelated tasks erase each other.

Specify durable access to important results and recovery actions. A temporary announcement should not be the only place the user can discover a failed operation or reach Retry. For the end of a waiting state, give the actual next state a meaningful representation rather than relying solely on a spinner disappearing. Clearing an old message must not imply that its problem was resolved.

Do not promise exact delivery time, verbatim speech, interruption order or successful receipt by a person. Assistive technologies and user preferences can affect presentation. The contract should define the intended information and nonduplication behavior, then name the environment checks needed to establish what actually happens.

## 5. Review the catalog and hand it over

Reconcile the saved catalog to the event/state inventory. Every relevant visible status needs an assigned semantic route or a specific unresolved gap. Every message must have a valid trigger and current owner; placeholders must be supplied by that event. Check that proposed focus behavior agrees with the keyboard/UI contract and that no routine message creates an unexplained focus jump.

Walk representative event sequences on paper: ordinary success, failure and retry, partial/unknown outcome, superseded completion, repeated render, and one concurrent update when applicable. Track visible state, persistent text, pending announcement, focus and permitted recovery separately. Record the intended output or suppression at each step. A paper sequence is specification review, not a screen-reader recording or an executed race test.

Prepare downstream acceptance cases for the exact target implementation: trigger/reset, semantic information expected, unacceptable stale/duplicate content, focus expectation, persistent recovery location, and the browser/assistive-technology combinations to be exercised. Verify actual announcement timing and repeated-identical-message behavior later rather than claiming them from role names. Keep all observed results explicitly unrun until obtained.

If the backend event cannot establish the promised result, narrow the wording or mark the missing evidence; do not invent a success signal. If the existing announcement mechanism cannot express the contract, return that integration gap without adding a second announcer secretly. When copy or event versions change, refresh their bindings together. Inspect a failed/uncertain save before retrying and preserve concurrent editorial changes.

Return the message catalog, event/region ownership map, retention/recovery rules and unexecuted acceptance cases, with exact source revision and open decisions. This completes the requested handoff; implementation, live testing, measured usability and conformance require separate evidence.

## Fictional, unexecuted illustration

A fictional catalog search leaves focus in its search field. Search A starts, then the person changes the filter and starts B. B returns seven matching items. The proposed routine status conveys “7 items match the current filters,” with the count and context in one update unit. A later failure from A produces no current-result announcement. The result list remains ordinary navigable content.

In a separate fictional draft-saving flow, an uncertain response does not permit “Saved.” The visible status and announcement instead explain that saving could not be confirmed, while a persistent review action remains available. Re-rendering that same uncertain event does not create a new alert; a separately confirmed retry has its own event identity and truthful result.

This is an authored illustration. No request, application, announcer, screen reader, timing experiment or live action was executed.
