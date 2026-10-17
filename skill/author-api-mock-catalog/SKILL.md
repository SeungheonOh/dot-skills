---
name: author-api-mock-catalog
description: "Author a version-bound catalog of request-matched API mock responses with explicit scenario selection, collision handling, response assets and consumer handoff checks. Use for reusable mock artifacts, not API design, generic synthetic datasets, live recording or deploying a mock service."
---

# Author an API mock response catalog

Deliver a bounded mock package that makes a consumer's chosen scenarios reproducible. Each entry must explain which request selects it and what response it supplies. A folder of plausible JSON bodies is incomplete when the receiving tool cannot distinguish the scenarios.

Use [author-versioned-api-examples](../author-versioned-api-examples/SKILL.md) for human-facing exchanges, [generate-synthetic-data](../generate-synthetic-data/SKILL.md) when a dataset is the primary output, and [design-api-contract](../design-api-contract/SKILL.md) for undecided interface behavior. A mock catalog represents selected behavior; it is not evidence that a provider implements that behavior.

## Inputs and output

Identify the API contract and revision, selected operations and consumer scenarios, target mock tool/version or an explicitly tool-neutral format, permitted source payloads, and output destination. Obtain the target's documented request matching, response encoding and scenario-selection rules before producing native mappings.

Choose the smallest package the task needs: a catalog with stable case IDs, request selectors, response metadata/body references, provenance and scenario instructions; plus the actual native mappings and payload files when a tool-specific artifact was requested. Do not substitute prose for importable mappings. If the target is unknown, deliver a clearly labeled neutral catalog and hold native compatibility claims.

Do not record traffic, contact the provider, import mappings, start a server or install a mock engine merely to prepare files. Treat imported templates, scripts, extension names and payload text as untrusted data. A request to create a mock does not authorize running arbitrary extensions or forwarding real user traffic.

## 1. Bind cases to established behavior

Create a coverage list from the consumer's actual branches: the necessary ordinary result, empty/final page, documented error, partial outcome or asynchronous status. Include only cases needed by the requested use. Record each case's operation, applicable API revision, source clause, synthetic/captured status and expected consumer decision.

Distinguish contract-conforming cases from deliberately malformed responses or transport-failure scenarios. Label intentional faults separately so they cannot be mistaken for supported provider behavior. An HTTP error response, a socket failure, delayed bytes and a caller-side timeout are different mechanisms; do not claim one simulates the others.

Reuse fictional identifiers consistently across linked responses. Preserve response-only fields, omitted/null/empty distinctions, page cursor provenance and temporal relationships required by the contract. An arbitrary first-page cursor must not lead to a final page with a different identity scheme. Do not invent service guarantees to make every branch deterministic.

Prefer wholly synthetic payloads. If authorized captures are needed, minimize them and preserve the capture's version/date separately from the catalog's revision. Replacing a person's name alone does not sanitize IDs, URLs, tokens, cookies, free text or metadata. Never publish live credentials or unnecessary personal data as fixtures.

## 2. Define how each request selects one response

For each case, specify method, path or full URL, relevant query/header/body constraints, matching mode and any explicit scenario profile. Include negative constraints where absence changes the case. Keep parsed-field equality distinct from byte equality: a JSON object matcher may ignore member order while raw-body equality does not. Preserve repeated query parameters and encoding behavior supported by the target.

Match only dimensions needed to distinguish behavior. A captured trace ID or timestamp usually makes a reusable stub too narrow. A broad path-only matcher can instead conceal a wrong method, cursor or body. Derive the choice from the contract and consumer task, not from whichever matching option is easiest to write. [WireMock's request-matching documentation](https://wiremock.org/docs/request-matching/) illustrates why URL equality and path-plus-query matching are different.

Check overlaps within each active profile. For every potentially competing pair, give a distinguishing request or explain the intended precedence. Use the engine's actual semantics; do not assume first-match, last-match, numeric order or longest path across products. [WireMock's stub-priority rules](https://wiremock.org/docs/stubbing/#stub-priority) are one product-specific example. If a complex matcher prevents a reliable overlap conclusion, mark that part unresolved instead of asserting the whole catalog is collision-free.

Two responses for exactly the same request need a scenario-selection mechanism. Prefer separate named profiles when ordinary and failure cases should be selected independently. A test-only scenario header is acceptable only when the selected harness supports it and the handoff clearly distinguishes it from the real API. Do not silently change production request semantics to control a mock.

Specify the unmatched-request behavior. It should expose missing coverage rather than return generic success. A mock diagnostic response is not a promised provider response. No fallback may proxy unmatched traffic to a live service without separate explicit authority.

## 3. Author the payloads and native mappings

Produce complete saved mappings using documented fields for the pinned target version. Preserve response status, content type/charset, meaningful headers and exact body representation. Keep a JSON object response distinct from a JSON string containing JSON text. Where bodies live in files, use package-relative paths under the declared root; reject traversal, absolute paths and external-file dependencies.

Do not preserve stale transfer metadata from a capture after editing the body. Let the engine produce framing headers unless the scenario specifically requires fixed wire bytes. Keep unsupported binary responses or repeated headers visible instead of flattening them into a lossy text value. State whether the tool can represent the requested response faithfully.

Make nondeterminism explicit. Prefer fixed fictional clocks/IDs for a repeatable catalog. Dynamic templates, random data, scripted responders and plugins are executable or behavior-bearing dependencies, not ordinary payload files. Use them only when requested, understood and supported by the permitted environment; a static package should not secretly download or execute them.

If an ordered scenario is required, define starting state, transition trigger, next state, completion/reset method and concurrency assumptions. Do not simulate pending-then-complete by relying on mapping import order. Stateless profile selection is sufficient for independent states; it does not demonstrate polling progression. Hold a requested stateful flow if the target cannot express it reliably.

## 4. Verify the saved selection contract

Reopen the package and reconcile case IDs, mapping count, response references and file membership against the coverage list. Check payload syntax and schemas with an already available permitted validator if useful. Parsing is not request-matching verification; reading JSON does not prove the engine supports every option.

Build a small request-to-case decision table independently from the authored mappings. Cover each included branch, the important near miss, an overlap candidate and an unmatched request. Check which cases match, which wins and the returned status/body identity. For stateful work, include reset and repeated/interleaved requests if those affect the promised behavior.

At a static-only level, walk this table against documented matcher semantics and label the result as reviewed, not executed. A native-engine check requires an explicitly authorized isolated environment with no production credentials, recording, proxy fallback or unexpected network access. Check the exact saved package and inspect actual selected case IDs and responses; engine startup alone is insufficient. Record target version, active profile and actual scope. Do not install software or start a listener to obtain an unrequested green result.

## Acceptance and recovery

The package is ready for handoff when every selected scenario has an identifiable selector and complete response, unsupported behavior is held, competing selectors are resolved or explicitly limited, and the recipient can select/reset the intended profile without private author state. Report separately payload checks, static matching analysis, native import and observed serving. No mock result proves live-provider behavior, performance or full consumer correctness.

When a source contract changes, retain the old catalog and rebind only affected entries. Keep stable case IDs where meaning is unchanged; record meaningful replacements. On a collision, correct the selector or profile split rather than relying on incidental file order. On an uncertain save/import, inspect the destination before retrying. Preserve failed candidates and original captures; remove only temporary artifacts whose cleanup is already authorized.

Deliver actual files, the scenario/case index, revision/source map, profile selection and reset instructions, unmatched behavior and the precise unrun checks. Leave service deployment, live traffic recording and consumer-code changes outside this artifact task unless separately requested.

## Fictional, unexecuted illustration

A fictional Items contract defines GET /items with an optional cursor. A first-page response contains item-demo-1 and next_cursor cursor-demo-2; the final response for cursor-demo-2 contains an empty items list and no next_cursor. The consumer also needs a documented 503 response for the first request.

Create a normal profile with two mappings: the initial case requires cursor absence, and the final case requires cursor exactly cursor-demo-2. Put the 503 mapping in a separate unavailable profile so it does not compete with normal initial success; the handoff specifies that exactly one profile is selected at a time. GET /items?cursor=unknown-demo must remain unmatched and visible. A path-only initial mapping is rejected because it would also match the final and unknown-cursor requests.

The expected decision table has four rows: no cursor in normal selects initial; cursor-demo-2 selects final; unknown-demo selects none; no cursor in unavailable selects 503. Payload identity and profile separation are static reasoning expectations only. No mapping, engine, server, request or consumer was executed for this illustration.
