---
name: prepare-content-security-policy
description: "Prepare a document-scoped Content Security Policy and integration handoff for an existing website, reconciling resource dependencies, script trust, delivery layers and reporting. Use for a reviewable candidate and rollout worksheet, not live activation, automatic allowlisting or a security certification."
---

# Prepare a Content Security Policy

Deliver a concrete CSP candidate, its document/template integration map, unresolved compatibility decisions and a bounded verification worksheet. The useful result is an explainable restriction on what selected pages may load or execute, with a viable implementation path, not a header copied from another site.

[Browser CORS policy](../prepare-browser-cors-policy/SKILL.md) controls cross-origin response sharing. [HTTP cache policy](../prepare-http-cache-policy/SKILL.md) controls storage and reuse. [Passive HTML review](../review-html-without-execution/SKILL.md) inspects supplied markup without activating it. This workflow owns the page's CSP contract across source templates and delivery layers; it does not replace application authorization, injection fixes or a broader security review.

## Establish the selected pages and owners

Read the supplied application/template source, existing policy configuration and sanitized evidence at an identified revision. Identify the document origins and routes, delivery layers, browser targets, and the actual user journeys that must keep working. Keep development tooling and production behavior separate. Ask only for missing decisions that affect the candidate, such as whether a page must be embedded by a partner or whether a third-party widget is still required.

Collect the policies emitted by the application, framework, gateway and any HTML meta elements separately. Record whether each is enforcing or report-only and which owner can change it. Do not assume a header in one configuration file is the complete served policy.

Preparation does not authorize deployment, live requests, browser execution, collection of visitor telemetry, new reporting accounts or uploading private source to an online evaluator. Existing policies and source files remain intact unless an edit is explicitly within scope. Copy only the necessary sanitized excerpts into the handoff, not tokens, session captures or private page contents.

## 1. Turn page behavior into a dependency map

Make a short row per materially different dependency: page/template, resource or behavior, reason it is required, owning source, proposed directive and unresolved constraint. Inspect more than script tags: stylesheet imports, fonts, images, network connections, frames, workers, manifests, forms, base URLs and dynamically inserted resources can matter. Include the selected error/login paths when they use different templates.

Separate an approved functional requirement from an observed URL. A third-party address in a console report is not authorization to trust that host. Trace it to application code, an intended integration, an extension or an unknown source before deciding. Do not turn one captured browsing session into a comprehensive inventory claim.

For script execution, distinguish external parser-inserted scripts, inline blocks, dynamic loaders, inline event handlers and string evaluation. Record whether generated markup changes at request time or only at build time. This determines whether a proposed trust mechanism can actually be maintained. If only rendered HTML is available, name the missing generator rather than inventing a framework change.

## 2. Write explicit restrictions and fallbacks

Start from the agreed behavior, not a promise that every site needs the same directive list. For each selected directive, explain what it permits and why. Keep schemes, hosts and ports intentional; broad wildcards and blanket data/blob allowances need a concrete requirement, not a disappearing warning.

The [default-src reference](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/default-src) describes fallback for fetch directives, not an additive inheritance rule. An explicit `img-src` replaces that fallback for images; it does not automatically retain a default `'self'`. Work out the applicable fallback chain for any omitted specialized directive instead of assuming every resource consults default-src directly.

Do not infer restrictions on document base URLs, form destinations or embedders from default-src. Name these decisions explicitly where relevant. The [frame-ancestors reference](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/frame-ancestors) distinguishes pages allowed to embed this document from `frame-src`, which governs frames this document loads. Ancestor checks include every ancestor in a nested embedding chain. A missing frame-ancestors is not a denial merely because default-src is `'none'`.

Use [Chrome's CSP guidance](https://developer.chrome.com/docs/lighthouse/best-practices/csp-xss) to distinguish a resource host list from an injection-mitigation design. A trusted host may expose script-capable content that defeats a host-only script policy. Consider nonce/hash-based script trust, object restrictions and base-URL restrictions together. Do not claim that an allowlist, a score or the presence of a header proves protection from all XSS.

## 3. Make script trust implementable

Choose a mechanism compatible with the page's actual generation path. [Google's strict-CSP guide](https://web.dev/articles/strict-csp) describes a nonce as a cryptographically unpredictable value regenerated for each response, with at least 128 bits recommended and base64 encoding. The response policy and approved script elements need the same value. Identify the generator and template binding; never supply a hard-coded example nonce as deployable security configuration.

Do not stamp every script in already-rendered, possibly untrusted HTML with a nonce. Mark intended trusted elements at their owning templates. Review caching and edge transformations with the delivery owner: the header and HTML must remain paired, and a cached fixed nonce is not a fresh per-response generator. Hold activation if that contract is unresolved rather than silently disabling caching or redesigning delivery.

For stable inline scripts, the [script-src reference](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/script-src) describes hash sources. Hash the exact inline content, excluding the surrounding tags; whitespace changes matter. Record the final-byte source and regeneration point. Do not invent a plausible-looking digest. External script hash authorization has additional integrity-metadata requirements; do not apply an inline recipe to external scripts without reviewing those requirements. Inline handlers need separate treatment, not a nonce added to their containing button.

If choosing `'strict-dynamic'`, document the resulting trust delegation. The [CSP specification's authoring guidance](https://www.w3.org/TR/CSP3/#strict-dynamic-usage) explains that supporting browsers propagate trust to qualifying non-parser-inserted script loads and ignore host/scheme sources and `'self'` for those script-source checks. A host list alongside strict-dynamic is not a second fence around trusted loaders. Review who controls loader URLs and hold an unexplained loader rather than assuming it is safe.

Return required application changes as explicit prerequisites. Do not insert `'unsafe-inline'`, `'unsafe-eval'` or broad compatibility fallbacks simply to make the candidate look complete. If a legacy dependency cannot meet the intended restriction, expose the choice between refactoring, a deliberately reviewed exception and deferring that page. Do not silently label the exception strict.

### Resolve specialized script directives before claiming strictness

Map each script behavior to the directive actually governing it in each retained policy. In supporting browsers, `script-src-elem` takes precedence over `script-src` for script elements; `script-src-attr` does so for inline event handlers. If absent, each falls back to `script-src`, then `default-src`. These are fallback choices within one policy, not the intersection rule for separate enforcing policies. See the [CSP Level 3 working draft's directive-selection rules](https://www.w3.org/TR/CSP3/#directive-fallback-list).

Do not leave a legacy `script-src-elem 'self'` beside a new nonce-based `script-src` and assume both restrict the same script element. The [script-element reference](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/script-src-elem) explains its separate scope. A nonce/hash or strict-dynamic decision must reach the effective element directive, or the specialized directive must be deliberately removed so the intended fallback applies. Review the change at its owning layer; do not delete specialized rules without checking the behavior they were preserving.

Likewise, a permissive `script-src-attr` can preserve inline handlers despite a restrictive `script-src`; consult the [script-attribute reference](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/script-src-attr). Keep handler permission separate from element permission. Check browser-target support rather than assuming an older browser honors the specialized restriction.

Do not move all script policy into `script-src-elem`: string-evaluation checks still use `script-src` or its fallback. Worker requests have their own chain: `worker-src`, `child-src`, `script-src`, then `default-src`, not `script-src-elem`. Record those dependencies when present; a page-script nonce decision alone is not a worker policy. See the [CSP script-element scope](https://www.w3.org/TR/CSP3/#directive-script-src-elem).

**Fictional, unexecuted illustration:** one candidate policy for an invented gallery introduces correctly paired per-response nonces in `script-src`, but retains `script-src-elem 'self'`. For a supporting browser, an ordinary same-origin parser-inserted script without a nonce is still permitted by that element directive, assuming no other enforcing policy blocks it. The intended nonce requirement therefore remains unmet. Hold the strictness claim and reconcile the effective directive. The later worksheet must distinguish approved nonce-bearing scripts, unapproved nonce-free elements and inline handlers. This is source reasoning for invented inputs, not a browser result; no page, parser, test or deployment was run.

## 4. Reconcile delivery and reporting

Prefer an HTTP response-header candidate when the target can emit one. [CSP multiple-policy rules](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy#multiple_content_security_policies) mean an additional enforcing policy cannot loosen an existing enforcing policy: an operation must satisfy them all. Propose an explicit replacement at the intended owner when necessary, not a second permissive header as an override. Meta delivery applies only after its position and does not support all header capabilities; in particular, it cannot supply report-only policy or frame-ancestors.

Provide the exact target configuration patch when its syntax and insertion point are known. Otherwise deliver a complete header-level contract and hold only platform translation. Consult current target documentation before representing a generic snippet as valid server configuration. Keep unrelated headers, authentication and routing unchanged.

The [report-only header reference](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy-Report-Only) distinguishes observation from enforcement. A report-only candidate does not relax a concurrently enforced policy. For network reporting with `report-to`, map the endpoint name to its Reporting-Endpoints declaration. Check target support; a deliberately retained legacy report-uri path is a separate compatibility decision, not a reason to promise uniform reporting.

Before proposing a reporting destination, identify its operator, approved data scope, retention and access. [The report-uri reference](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/report-uri) describes fields such as document URI and optional script samples, and cautions that received reports are untrusted. Treat reports as potentially sensitive input. Do not enable samples or send visitor URLs to a third party without the necessary approval. If reporting is out of scope, omit a fabricated endpoint and specify the later local observation plan instead.

## 5. Review the candidate before activation

Reopen the saved policy and integration notes. Walk each required behavior through its actual directive/fallback, script trust mechanism and every retained enforcing policy. Check one meaningful disallowed behavior too. This is source reasoning, not an executed browser result.

Write a later verification worksheet proportional to the selected pages:

- Exact document/route, source revision, intended browser/context and user journey
- Expected headers and mode, including other policies that must remain active
- Required behavior and a synthetic disallowed case with an expected observation; for scripts, name the effective element/handler directive rather than checking only `script-src`
- Header/markup pairing for nonce pages, or final-byte/hash pairing for hash pages
- Evidence to capture, reporting privacy constraints, owner and stop condition

Browser work requires its own authorization. When permitted later, use approved synthetic data and a bounded context, inspect served headers and exercise actual journeys, then distinguish report-only violations from enforced blocking. A successful page load misses unused branches; no received reports can reflect missing coverage or delivery failure. Do not call either complete compatibility evidence. Never switch off browser security or replay a consequential operation to gather a cleaner report.

Name the original configuration and dependent template changes needed for rollback. If authorized activation later breaks a required journey or grants unexpected execution, stop expanding rollout, preserve bounded evidence and correct or revert only the approved change. Do not erase every policy or automatically allow every reported host.

## Deliver at the requested boundary

Return the candidate, dependency/integration map, source revision, unresolved prerequisites and verification worksheet. Keep `prepared`, `source reviewed`, `served headers observed`, `report-only behavior observed` and `enforcement observed` separate. Claim only stages actually completed. A preparation-only task ends with a reviewable package, not a deployment or a security guarantee.

## Fictional illustration, not executed

A fictional public reading-room page has no scripts, forms, frames, workers or base element. Its approved resources are same-origin external CSS and images. The owner says no other page should embed it. A header-level enforcing candidate is:

```http
Content-Security-Policy: default-src 'none'; style-src 'self'; img-src 'self'; base-uri 'none'; form-action 'none'; frame-ancestors 'none'
```

The invented source inventory contains no inline style attributes. The expected worksheet permits the two resource classes and rejects scripts and embedding. This is a candidate for the supplied requirements, not a default for interactive sites.

A previously retained gateway policy says `img-src 'none'`. Adding the candidate above would still leave images blocked; the package therefore holds activation until the gateway owner reviews the intended replacement. Adding an image host to a third header would not repair that conflict. A report-only copy of the candidate would not enforce its new restrictions or remove the gateway block.

No browser, parser, application, network request, report collection, test or deployment was run for this illustration. Its outcomes are authored expectations for fictional inputs.
