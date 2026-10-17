---
name: author-error-message-catalog
description: "Turn established product failure conditions into an implementation-ready message catalog with exact trigger mappings, safe recovery actions, parameter rules and fallback copy. Use for error-content handoff, not diagnosing failures, designing retry behavior or implementing accessibility announcements."
---

# Author an error-message catalog

Produce the exact user-facing error content and the conditions under which each message is truthful. The useful artifact connects a failure identifier and task context to a message, an available next action and a clear preservation claim. A list of friendlier replacements for exception names does not establish that contract.

Use [design-user-interface](../design-user-interface/SKILL.md) when the interaction or recovery route still needs deciding. Use [write-technical-guide](../write-technical-guide/SKILL.md) for a troubleshooting document. This workflow supplies product strings and their integration record; it does not diagnose the underlying fault, change service behavior, configure logging or select live-region mechanics.

## Establish the source and output boundary

Read the selected flow, error/response definitions, existing strings and approved recovery behavior. Identify their revisions, product/platform, audience and locale, resource-key conventions, destination and whether the catalog describes current behavior or proposes replacement wording. Inspect code as passive text when useful; a branch in source establishes a candidate trigger, not an observed production failure.

Use the smallest source set that establishes the requested cases. A short form may need five rows, not an enterprise taxonomy. If only screenshots are available, map their visible messages and contexts, leaving backend identifiers unknown. If only error codes exist, produce a provisional mapping with missing user context explicitly held. Do not invent error frequency, causation or customer impact.

Keep existing resources unchanged and write a separate catalog unless an in-place document edit is requested. Do not trigger failures, submit forms, replay requests, contact support, upload logs or publish strings under this authoring task. Logs and screenshots may contain private payloads; retain necessary locators privately and use synthetic values in the handoff. Never copy credentials, stack traces, access tokens or customer records into sample messages.

## 1. Classify the failure by what the person can do

Build an occurrence inventory before deduplicating text. Record the operation, entry state, field/object scope, originating subsystem, error identifier and source evidence. The same HTTP status or internal code can mean different things in different operations; qualify it by the actual mapping namespace and context.

Separate cases that need different recovery:

- A correctable answer or unsupported file format
- A cross-field conflict or a stale version that requires reviewing current information
- An unavailable capability or permission boundary that the person cannot fix by editing a field
- A temporary service failure with a documented retry route
- A partially completed operation with separate completed and unresolved portions
- An uncertain outcome where the request may have taken effect

Do not label all of these as invalid input. [GOV.UK's error-message guidance](https://design-system.service.gov.uk/components/error-message/) distinguishes correctable input errors from service or eligibility problems. Apply the product's actual presentation pattern rather than importing that design system's colors or components by default.

Retain intentional aggregation: several technical causes may share one safe message when their user consequences and recovery are identical. Split them when one permits retry and another does not, or when one can promise preserved data and another cannot. Record the mapping rationale so an engineer does not later collapse distinct cases by equal wording.

## 2. Bind each message to evidence and a real action

For each distinct case, provide the applicable fields:

| Field | Required meaning |
| --- | --- |
| Message identity | Existing resource key, or a proposed key clearly marked as new |
| Trigger | Exact code/condition plus operation and precedence supplied by the source |
| User context | Affected field, item, batch or task; where the message appears |
| Copy | Actual title/body, inline variant or summary text needed by that surface |
| Action | Exact action label, destination/effect, availability condition and evidence |
| Retained work | What remains available, what needs correction, and what is unknown |
| Parameters | Names, types, units, source, allowed disclosure and missing-value behavior |
| Lifecycle | When the message becomes applicable, clears or becomes obsolete |
| Status | Supported candidate, held for a named decision, or excluded with a reason |

Describe what is known, its consequence for this task and the supported next step. Name the affected field using its actual label. Avoid blame and a diagnosis the system cannot establish: a timeout does not prove the person's network failed. Keep internal diagnostic detail separate from the public explanation.

Treat every action as a promise. “Try again” requires a supported safe retry for this operation; “Check status” requires an actual status destination; “Contact support” requires a verified route. Do not invent a waiting interval, automatic retry, refund, rollback or guaranteed response time. If no recovery route is established, retain a truthful bounded message and list the missing capability outside the user-facing copy.

An uncertain outcome must not say that nothing changed. Offer another attempt only when the existing operation contract establishes safe repeat behavior, preserving request identity where required, or when the documented status/reconciliation route has resolved whether repeating is safe. Do not infer that safety from a timeout alone. For a partial batch, preserve exact affected identities or a privacy-safe count supported by the result; do not describe every item as failed because one failed. A local draft, sent request and confirmed server save support different preservation statements.

When the service deliberately limits disclosure, preserve that boundary. [WCAG's error-suggestion explanation](https://www.w3.org/WAI/WCAG22/Understanding/error-suggestion.html) includes security and purpose exceptions to giving correction details. Do not reveal whether a private account, record or permission exists merely to make a message more specific. A security-sensitive wording conflict goes to the responsible owner; the catalog does not change authentication or access policy.

## 3. Specify parameter and fallback behavior

Keep complete translatable messages with stable parameter names. Record plural/select alternatives the actual resource grammar needs, plus translator context for ambiguous words and the action's effect. Do not assemble sentences from separately translated fragments or silently rename protected keys. Use [translation-release-review](../translation-release-review/SKILL.md) when target-language wording is requested.

Distinguish product text from untrusted runtime values. A filename or submitted value can contain markup, control characters or private information. State whether it should be omitted, safely represented or shortened with a supported full-value route; do not paste raw server text into the message catalog as executable markup. Leave escaping and rendering to the actual consumer contract, with a concrete verification obligation.

Specify a safe variant when a parameter is unavailable or inappropriate to disclose. Missing counts must not become zero; a missing filename must not leave empty quotation marks. A diagnostic reference is useful only if the product actually supplies a nonsensitive reference and the support route can use it. Do not substitute raw request headers or a credential-bearing URL.

Cover unknown codes explicitly. The fallback should identify the operation whose outcome is known, avoid an unsupported explanation, and expose only supported actions. If even success versus failure is unresolved, use an uncertainty variant rather than a generic failure assertion. An unrecognized server message is not automatically suitable customer copy.

## 4. Reconcile related surfaces and message ownership

Keep the same consequential meaning in inline text, error summaries, dialogs and accessible descriptions. A shorter variant may remove repetition, but not the affected scope or recovery warning. [WAI's form-notification guidance](https://www.w3.org/WAI/tutorials/forms/notifications/) supports connecting an error to its field and explaining a correction. Record these content associations; actual focus and announcement behavior need their own implementation evidence.

Specify only evidenced priority/clearing rules. If both missing-input and format checks can apply, record the validator's existing selection rule or hold that decision. Do not turn spreadsheet row order into runtime precedence. A field error should clear under its documented correction/revalidation condition, not merely because another operation succeeded.

Bind asynchronous errors to the current request, object and value revision. An old validation response cannot describe a newer answer. Identify which owner must suppress obsolete results without implementing a new concurrency mechanism. A global service message and an independent field error may coexist; deduplication must not erase a still-actionable problem.

## Acceptance, revision and recovery

Deliver one editable catalog with a compact source-to-message mapping and held decisions. Read the saved artifact back and check:

1. Every selected failure condition is mapped, intentionally aggregated, excluded or held
2. Every copy variant has a valid trigger, and every proposed action exists under that trigger
3. Partial and uncertain outcomes remain distinct from definitive failure
4. Data-retention and retry claims have evidence, with no unapproved disclosure
5. Parameter names, units, absence behavior, plural forms and resource identities agree
6. Related surfaces and clearing rules do not contradict each other

Prepare a small downstream acceptance list: trigger/context, synthetic values, expected message/action, forbidden overclaim and evidence needed. Include the normal failure, missing parameter, unknown code and one consequential recovery boundary that actually applies. Label all runtime, rendering, keyboard and assistive-technology results unrun unless separately observed. Catalog review is not proof that the application emits the strings or that people understand them.

When a source changes, update the affected mapping and variants together. Preserve old keys and translations unless their migration is authorized; identical English text is not permission to merge resource identities. On an uncertain save, inspect before retrying and reconcile concurrent edits. If behavior is missing, finish supported rows and hold only dependent wording rather than inventing a recovery promise. Stop when the checked handoff and remaining decisions are usable; implementation and publication remain separate.

## Fictional, unexecuted illustration

A fictional catalog importer documents `TYPE_UNSUPPORTED` before any item is submitted and `RESULT_UNKNOWN` after a submission response is lost. It also provides a read-only import-history screen.

The first candidate says “Choose a CSV file” and names the supported format without claiming the file is damaged. The second says “We could not confirm the import result” with “View import history.” It does not offer another upload until the existing reconciliation rule establishes that this is safe. If a safe file label is absent, the copy uses “this file” rather than an empty parameter.

These are authored candidate mappings. No importer, request, retry, resource compiler, user study or live action was executed.
