---
name: document-protocol-sequences
description: "Turn an existing message or API protocol into version-bound sequence documentation with participant roles, correlation rules, branch conditions and completion boundaries. Use for a consumer handoff derived from established contracts, not designing a protocol, reconstructing a recorded incident or generating runnable requests."
---

# Document the exchanges a protocol actually defines

Produce a sequence-diagram set and a source-linked exchange register that let an implementer distinguish what is sent, who receives it, what each response establishes and which next steps are allowed. The difficult work is reconciling protocol semantics across sources; a plausible happy-path drawing is insufficient.

The result is a contract-level multi-party reference across the selected scenarios. It reconciles sender and receiver obligations, intermediaries and control fragments; it does not merely illustrate a consumer's populated request/response examples in a different format.

Use [design-api-contract](../design-api-contract/SKILL.md) when the protocol still needs design, [author-versioned-api-examples](../author-versioned-api-examples/SKILL.md) for concrete consumer request/response examples, and [reconstruct-partial-event-order](../reconstruct-partial-event-order/SKILL.md) for ordering observed records. A documented permitted scenario is not evidence that it occurred, and an observed trace does not establish every permitted scenario.

## Bound the documentation task

Identify the operation or message family, exact protocol/API version, intended consumer role, relevant source revisions, scenario scope, target notation and private destination. Sources may include published specifications, supplied interface definitions, maintained workflow docs, passive source inspection and existing test descriptions. Record which source establishes intended obligations and which merely illustrates or implements one path.

Deliver editable sequence source, readable diagrams when supported, an exchange register and a concise list of unsupported or conflicting behavior. The register should cover message identity/type, sender and receiver roles, precondition, correlation, response/completion meaning, branch/loop membership and exact source locator. Use scenario IDs so a simplified overview can link to its detail.

Use only authorized read-only material. Do not send messages, replay captures, call endpoints, subscribe to channels, run handlers, start a recorder or change a broker to prove the diagram. Do not embed credentials, real payloads, private callback URLs or sensitive business identifiers in the handoff. Preserve original source files and prepare a separate documentation candidate unless a scoped update is requested. A remote diagram editor is a data recipient, not automatically a harmless preview tool.

If a specification only lists endpoints or message schemas, say which ordering and completion rules remain unspecified. Continue documenting supported exchanges; do not invent an orchestration layer to connect them.

## 1. Establish participants and contract perspective

Assign stable IDs to roles before drawing lifelines. Distinguish caller, gateway, application, broker/channel, worker and external participant only where the sources establish them. A component can play different roles in different exchanges; a role can have multiple instances. Do not merge participants because they share a hostname or split one role merely because two display names differ.

For each source, establish whose viewpoint words such as send, receive, request and reply use. The [AsyncAPI 3.0 specification](https://www.asyncapi.com/docs/reference/specification/v3.0.0) models operations, channels, messages, replies and correlation information separately. Read the actual operation and bindings; a channel name or message schema alone does not identify a particular producer-to-consumer delivery or its order.

Keep intermediaries that change meaning. A producer-to-broker acknowledgment may concern acceptance by the broker, while a consumer response concerns processing. Do not draw a direct producer-to-worker exchange unless the protocol supports that abstraction and the omitted intermediary is disclosed. For fan-out, state whether the recipient set is fixed, selected or unknown; one representative consumer must not imply that only one exists.

Reconcile the two ends of each exchange where both are documented: sender operation, transmitted message variant, channel/address binding and receiver operation. A common schema name is insufficient to pair them. Keep sender-only or receiver-only evidence as a boundary obligation, and expose disagreement over direction, variant or correlation instead of inventing a counterpart.

## 2. Build the exchange register before ordering arrows

For each exchange, separate:

- The logical operation from an individual request/message attempt
- Send, transport receipt, acknowledgment, application acceptance and completed effect
- Response content from a later callback, published event or polling observation
- A correlation identifier from a trace identifier, idempotency key or entity identifier
- Required, optional, forbidden and unspecified behavior under a stated condition

Preserve identifier scope, lifetime and matching location when known. A shared entity ID may relate many operations; it is not necessarily enough to match a reply to an attempt. A retry can reuse a logical operation ID while requiring a new attempt ID, but include that rule only when established. Never imply exactly-once effects from a correlation field or a deduplication claim lacking scope.

Read status meanings rather than guessing from success-looking arrows. For HTTP, [RFC 9110's 202 semantics](https://www.rfc-editor.org/rfc/rfc9110.html#name-202-accepted) distinguish acceptance for processing from completed processing. Show the protocol's actual completion evidence, if any; a later status read or callback should not appear merely because the initial response is asynchronous.

For errors and timeouts, record what the participant knows. A caller timing out does not establish that the receiver stopped or that no effect occurred. Preserve specified cancellation acknowledgment and completion races separately. Leave delivery, retry or rollback behavior unknown when the source does not define it.

## 3. Turn obligations into scenario paths

Choose a compact set of source-supported scenarios that covers the requested contract distinctions: ordinary completion, a material alternative, and applicable rejection, pending, cancellation or retry paths. Do not force every protocol through every category.

Give each scenario its starting condition, participating roles, triggering event, required exchanges and end condition. End conditions can be completed, rejected, accepted/pending, unknown outcome or waiting on an external actor. Avoid an unlabeled end that a reader will interpret as success.

Order arrows only where the protocol establishes precedence. List independent exchanges as unordered or use a clearly explained parallel fragment. A lack of ordering evidence is not proof of simultaneous execution, and a diagram's vertical spacing is not a latency measurement. A synchronous-looking return arrow does not prove a caller thread was blocked.

For alternatives, label the exact branch condition and where it is evaluated. Do not describe alternatives as mutually exclusive unless the source supports that. Keep overlapping conditions or priority rules visible. For loops, state the repeat trigger, stopping condition and attempt/time bound when defined; write unspecified rather than inventing a safe retry budget. Show whether a retry repeats one exchange or starts a new logical operation.

Retain relevant subscription/setup prerequisites without adding an unrequested account-setup guide. Do not depict a late subscriber receiving earlier events unless retention/replay semantics establish that behavior. Likewise, a documented callback possibility is not proof the consumer has registered or authorized a callback destination.

If source and implementation disagree, keep separate contract and inspected-implementation views or a focused discrepancy row. Static call order may support an implementation path, but dynamic dispatch, configuration and asynchronous work can leave other paths unresolved. Do not quietly choose an implementation detail as the public guarantee or repair the product while documenting it.

## 4. Encode the view without silently changing meaning

Use the requested supported notation and version. [Mermaid sequence syntax](https://mermaid.js.org/syntax/sequenceDiagram.html) provides participants, message styles and fragments for alternatives, optional paths, loops and parallel paths. Define a small legend matching the actual artifact; an arrow style cannot substitute for an explicit delivery or completion statement.

Label messages with exchange IDs and concise contract meaning. Put long payload definitions in referenced source material rather than copying whole schemas into labels. Use activation bars only with an explained meaning supported by the source. Do not imply object destruction, transaction atomicity or locking simply to make the drawing look complete.

Keep every fragment tied to register rows. Split an overloaded diagram into linked scenarios rather than removing the error or pending path that changes consumer behavior. Provide a text path description for readers who cannot use the visual. Escape untrusted labels and avoid embedded HTML, remote includes or clickable internal endpoints in a broader handoff.

Render and inspect with an available authorized tool when that is part of the task. If the target cannot express a needed condition, retain it in a visible note and register; do not substitute a stronger standard symbol. If rendering is unavailable, deliver editable source plus the register as an unrendered candidate and identify the missing check.

## 5. Accept, revise and recover

Read back the saved artifact set and check both directions: every drawn arrow must have a source-linked register entry, and every in-scope required exchange must appear in a view or have an explicit omission. Check role perspective, message direction, correlation scope and reply pairing, including repeated attempts when present.

Walk each documented path on paper from its precondition to its labeled end. Confirm branch conditions, loop scope and completion evidence against the sources. Include a negative reading: can a recipient mistake a timeout, acknowledgment or pending response for failure or completed effect? Correct that ambiguity. This is a documentation walkthrough, not an executed request or a protocol conformance test.

Inspect actual rendered output, when available, for clipped guards, missing arrows, misleading lifeline merges and split-page loss of context. Check the final delivered format as well as the authoring preview. Report semantic/source review, syntax checks, rendering and execution as separate evidence categories; do not imply any category ran merely because the source file exists.

When protocol versions conflict, isolate the affected scenario and return a precise owner question. When an exchange is unspecified, label the boundary rather than fabricate a reply. For a revision, preserve scenario/exchange IDs where meaning is unchanged and document changed obligations, removed paths and superseded sources. On an uncertain save, inspect the destination before retrying; do not overwrite concurrent documentation edits.

Finish with the covered operations/version, artifact links, unresolved behavior and actual checks. Publishing the protocol or sending its diagrams to a new audience needs that specific authority.

## Fictional, unexecuted illustration

A fictional export API v2 defines client, export API, jobs channel and worker roles. Its workflow note says the API accepts an export request, returns 202 with job_id, and then publishes a job message containing that same job_id to the jobs channel. The worker consumes that message type from the channel. The client may poll the documented job-status endpoint using job_id. Only status ready with an artifact reference establishes export completion. The note does not define callback delivery or automatic client retries.

The expected diagram ends the initial request at accepted/pending, preserves the separate publish and consume exchanges, and puts status reads in an optional polling scenario with its defined responses. The exchange register keeps job_id's operation-matching role separate from any unspecified delivery-attempt identity. It includes a worker-failure branch only if that branch is documented. A timed-out poll is an unknown observation, not proof of export failure. No callback or retry policy is invented to make a complete-looking path.

This is an authored illustration. No request, queue operation, polling loop, worker execution, render or publication was performed.
