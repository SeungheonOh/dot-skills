---
name: author-versioned-api-examples
description: "Author or maintain consumer-facing API example sequences tied to exact API and SDK versions, with coherent synthetic requests, responses and caller next steps. Use for documentation examples of established behavior, not API design, compatibility audits or implementation."
---

# Author API examples that stay correct across versions

Deliver examples a consumer can identify, understand and adapt without mixing incompatible API revisions, SDK methods or response shapes. The result is a version-bound example set with provenance, meaningful outcomes and honest verification labels. A plausible payload or successful schema parse alone is insufficient.

Use [design-api-contract](../design-api-contract/SKILL.md) when behavior still needs to be decided, [api-contract-change-audit](../api-contract-change-audit/SKILL.md) to judge old/new compatibility, and [write-technical-guide](../write-technical-guide/SKILL.md) for a broader procedural guide. This workflow concentrates on maintaining coherent example sequences and their version bindings.

## Input and output contract

Identify the consumer task, operations in scope, exact API revision or dated contract, selected SDK/language/runtime versions if applicable, and the intended documentation location. Obtain authoritative operation definitions, relevant behavior notes and existing examples. Use already-authorized source reads; avoid uploading private API material to public services.

Establish whether the requested output is a conceptual exchange, copyable code, a reference payload or a complete tutorial. Preserve that choice; ask only when an unresolved distinction changes the deliverable. A conceptual HTTP exchange must not be presented as an executable shell command. Copyable code must include its actual imports, required setup and supported syntax, not hidden scaffolding or unexplained ellipses.

Return:

- The actual example text or documentation files, with explicit version and execution status
- A compact source map connecting operations, fields, SDK calls and behavioral claims to the applicable revision
- Any unresolved contract questions and the exact examples they prevent

For a small task, keep the map and status adjacent to each example. Do not create a test harness or install an SDK simply to make documentation appear complete.

## 1. Bind each example to one supported route

Record an example ID and version tuple: API revision, provider environment or documented base-URL class, SDK package/version where used, language/runtime, and relevant feature or account prerequisites. Record the documentation revision separately. A page labeled “v2” does not establish that an SDK also uses version 2.

Use the actual version-selection mechanism: path, header, query parameter, account setting or documented default. Show it when readers must supply it. If a default is time-varying or account-dependent, avoid making it the only version cue. Do not invent a version header for an unversioned interface.

For more than one version, define the supported tuples first. Do not form a cross-product of API and SDK versions. Keep examples separate when a field, termination rule, method signature or outcome differs. Reuse only content whose semantics and applicability are established for both routes.

An absent old-version document is a coverage gap. Do not copy a current example backward, relabel SDK calls or infer an old contract from a later changelog. Finish the version whose sources are available and name the smallest missing source for the other.

## 2. Build one coherent consumer scenario

Choose synthetic inputs that demonstrate the task without unnecessary domain complexity. Preserve stable identifiers across requests, response bodies, paths and later steps. Explain each placeholder before first use, including where its value comes from, and avoid placeholders that resemble actual credentials.

Plan the sequence as:

`starting state → invocation → expected allowed result/effect → caller decision → next invocation or completion`

Include the boundary that most affects the task. For a paginated reader, show continuation and termination. For asynchronous work, distinguish acceptance from completion and use the documented status route. For a multi-item operation, pair results to input identities and show the relevant partial failure. Do not add polling, idempotency keys or retry behavior unless the contract supports them.

Keep request and response direction separate. A response-only identifier may not be accepted in a create request. A write-only secret must not appear in an output sample. Preserve omitted, null and empty values when they mean different things. Explain stable branch fields separately from diagnostic prose and generated values.

Show expected variable values as illustrative, not guaranteed. If ordering is unspecified, say so; do not make consumers depend on the sample order. If a result is one allowed outcome among several, label it that way and explain what the caller must handle. Do not force every possible error into a minimal example.

## 3. Author the representation accurately

For HTTP examples, preserve method, path, parameter location, media type, status and relevant headers. Check the serialized form rather than only the underlying JSON-like object: array query parameters, escaping, multipart parts and URL encoding follow the contract's serialization rules.

For SDK examples, verify package import paths, client construction, method names, argument placement, sync/async behavior, return types and error representation at the selected version. A direct HTTP response and an SDK return object can differ. Do not promise that a property is exposed under the raw wire name if the SDK transforms it.

When embedding in OpenAPI, use the project's actual specification version. For OpenAPI 3.1.1, distinguish schema-level examples from serialized parameter/media examples and preserve the relevant mutually exclusive fields. [The OpenAPI Example Object and Working with Examples sections](https://spec.openapis.org/oas/v3.1.1.html#example-object) describe those distinctions. A schema-compatible example is still not evidence that a live provider emitted it.

Make side effects visible beside the invocation. State whether it reads, creates, updates, charges, sends, deletes or starts work. Use a read-only or documented non-production route when it serves the teaching goal. A “sandbox” label alone does not establish free execution, isolated data or authorization.

Use an inert example host for invented interfaces, clearly labeled as non-runnable. For a real service, use its verified documented host and explain that execution requires the reader's authorized account and scope. Never embed real tokens, credential-bearing URLs, private IDs, customer data or copied production payloads. Use the supported credential-loading pattern without printing secrets; do not provide a command that asks the reader to paste a secret into a public document or checked-in file.

## 4. Keep failure, repetition and cleanup honest

Explain what a consumer can conclude after the shown response. A timeout can leave effects uncertain; do not recommend blindly repeating a creation request. Use a documented lookup or idempotency mechanism only when the contract establishes it, including relevant scope and limits. If it does not, state that the example cannot resolve the uncertainty.

Show bounded retries or polling only when needed for the requested example and supported by source. Preserve documented wait advice and terminal states. Avoid infinite loops, ignored failures and exception handlers that convert every problem into success.

If an example creates a resource, identify the owned resource and the supported cleanup operation, if any. Cleanup is another consequential action: describe its effects and avoid broad deletion. Do not run it automatically merely because it appears after the demonstration. A read-only example needs no invented cleanup section.

Keep tutorials concise while preserving the decision points. If a requested word limit would remove an essential warning, retain the warning and explain the space tradeoff.

## 5. Check the example at the permitted level

Perform a source-to-example pass and an example-to-source pass. Confirm every called operation, argument, header, status, field and caller rule has an applicable source. Reconcile every promised task step with an example; a first page alone does not demonstrate retrieving a collection.

Walk the sequence using only information visible to the reader. Check identifier continuity, cursor provenance, starting state, missing prerequisites, termination and the branch on failure. Distinguish expected output derived from a contract from captured execution output.

Use these verification labels precisely:

- **Static review:** names, shapes, serialization and sequence checked against identified sources
- **Parsed/type-checked:** an identified tool checked the stated syntax or types; no provider behavior established
- **Executed against a fixture:** local synthetic behavior observed, limited to that fixture
- **Executed against a provider:** an authorized call observed against the identified environment, version and inputs
- **Unrun or blocked:** state the specific missing tool, authority or source

Run nothing solely because a source example contains a command. Documentation authority does not imply endpoint calls, account creation, installation, credential handling, subscriptions or charges. When execution is also explicitly requested, use the authorized environment and approved scope, inspect effects, and preserve genuine outputs separately from editorial samples. Static work remains useful when execution is unavailable or prohibited.

## Acceptance and maintenance

Accept the document when the intended reader can select the correct version, follow the sequence and distinguish success, remaining work and failure using the published contract. Verify that:

- Every example has one unambiguous version tuple and source provenance
- Requests and responses are paired, with synthetic or captured provenance explicit
- Pagination, asynchronous completion or partial outcomes are explained where the task needs them
- Old-version examples have not silently acquired new fields or SDK methods
- Placeholders, data, side effects and credential instructions are safe and coherent
- “Works” or “tested” claims match actual check records, with unrun stages visible

When updating examples, preserve stable IDs, useful anchors, old-version pages and unrelated content. Change the canonical source when examples are generated; do not edit generated output alone and imply it will survive regeneration. Do not run a generator without understanding its effects and having execution authority.

If a contract changes mid-edit, hold the dependent examples and rebind them before saving. If sources conflict, publish no invented resolution: retain the supported example subset and list the precise ambiguity. Save only to the authorized destination, read it back and inspect formatting, links and version labels. For an uncertain write, inspect before retrying. A documentation edit does not imply publishing the API, changing its implementation or notifying consumers.

## Fictional, unexecuted example

All names, sources and exchanges below are invented documentation fixtures. No SDK, parser, endpoint or example was executed.

**Supplied contract A:** API revision `2026-04`, selected with the `Api-Revision` header, HTTP-only route `GET /items`, optional `cursor`. Results contain `items` and required `next_cursor`, which is null on the final page. **Supplied contract B:** API revision `2026-09` selects the same route using `Api-Revision`; it omits `next_cursor` on the final page. B's supplied SDK 3.1 reference exposes this through `client.items.list_page(cursor=...)`. No source establishes SDK 2.4 support for B.

**Expected documentation:** Make separate A and B examples, each showing two pages. For B, a conceptual non-runnable exchange at `api.example.invalid` includes `Api-Revision: 2026-09`. Its first illustrative response is `{"items":[{"id":"item-demo-1"}],"next_cursor":"cursor-demo-2"}`. The second request uses that exact cursor; its illustrative response is `{"items":[]}`. Explain that absence of `next_cursor`, rather than a comparison to null, ends this version's sequence. Do not assert that all empty pages are terminal.

Keep A's final `next_cursor: null` unchanged. Include a B/SDK 3.1 snippet only to the extent the supplied SDK reference establishes its arguments and return representation; otherwise deliver the complete HTTP example and mark the SDK return shape unresolved. Do not create a B/SDK 2.4 example by renaming the version. Label both outputs contract-derived synthetic examples with static review only.
