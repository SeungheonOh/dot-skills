---
name: prepare-http-cache-policy
description: "Prepare a response-class HTTP cache policy and implementation handoff for an existing site or API, reconciling storage, freshness, variants and validation across browser and shared caches. Use for policy candidates, not cache-algorithm simulation, CDN activation, purging or performance certification."
---

# Prepare an HTTP cache policy

Deliver a bounded response-class policy, concrete candidate headers or an owning-layer configuration patch, and a rollout/check worksheet. The outcome is a reviewable answer to which responses may be reused, by whom, for how long and under which representation identity, not a blanket long TTL on every successful request.

[Website creation](../build-usable-website/SKILL.md) owns the application. [HTTP request collections](../package-http-request-collection/SKILL.md) package client requests. [Integration configuration handoff](../prepare-integration-config-handoff/SKILL.md) documents established loader bindings. This workflow decides and translates an HTTP response-reuse contract for an existing delivery path. It does not implement a cache engine, service worker, access-control system or production deployment.

## Establish the bounded delivery path

Identify the selected host/routes, methods and response classes; source revision; application/server/CDN owners; existing cache rules; and the user's freshness and privacy requirements. Obtain supplied source/configuration or authorized sanitized captures. Do not collect private account pages merely to obtain representative headers.

Draw a short origin-to-client layer list. Name which layer generates, replaces or forwards each proposed header and which layer owns any cache-key override. Include an application cache or service worker as a separate dependency if present rather than claiming HTTP headers configure it. Distinguish proposed policy, observed response headers and observed reuse.

Ask only about unresolved decisions that change the result: whether a response is identical for all recipients, acceptable update delay, whether stale content is allowed during failure, or whether a supposedly versioned URL is ever overwritten. If these are unknown, hold that response class and continue the rest. Do not infer business tolerance from an existing TTL.

Preparation does not authorize requests to live endpoints, credential use, CDN changes, warming, purging or deployment. Keep original configuration and captures intact. Strip credentials, cookies and private response contents from the deliverable; retain only the necessary header names and behavior descriptions.

## 1. Classify responses before writing rules

Use a small policy map with one row per materially different class. Record a representative route, match boundary, method/status, audience, change model, desired storage/reuse behavior, validator source, variant inputs, and owning layer. Group routes only when those facts really agree.

Consider the site's actual classes: mutable public documents, content-versioned assets, personalized responses, authentication-related redirects, and missing/error responses. Do not classify only by extension: a path ending in .css can still be handled by an application fallback. Check rule ordering and overlapping matchers against the existing server or provider's documented semantics. Keep exceptions narrow and explicit.

For each class, state the user-facing requirement first, such as “the public timetable may lag by at most the agreed interval” or “account details must not enter a shared cache.” Then choose a policy. A missing owner decision is not permission to copy a public-asset policy onto user-specific data.

## 2. Choose storage and freshness separately

The [Cache-Control reference](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Cache-Control) distinguishes these response directives:

- `no-store`: prohibit storage by HTTP caches; not the same as requiring validation.
- Unqualified `no-cache`: storage is possible, but reuse requires successful validation.
- Unqualified `private`: prohibit shared-cache storage while allowing private-cache storage subject to other rules.
- `max-age=N`: a freshness lifetime in seconds, not a promise of retention.
- `s-maxage=N`: shared-cache lifetime, overriding max-age/Expires there, not in private caches; it also requires successful origin validation before shared reuse once stale.
- `must-revalidate`: once stale, do not reuse without successful validation.

Choose the smallest coherent set that meets the requirement. Do not pile every restrictive directive into a single header. Record nonnegative integer durations and distinguish browser and shared-cache decisions. Avoid duplicate or contradictory values emitted by multiple owners. Review existing Expires values rather than leaving an unexplained competing policy.

[RFC 9111](https://www.rfc-editor.org/rfc/rfc9111.html#section-3.5) allows shared reuse of Authorization-bearing requests under particular directives, including public, s-maxage and must-revalidate. Do not treat authentication as an automatic cache bypass. Set-Cookie alone does not prohibit caching under that standard. Hold personalized shared caching unless the intended isolation is explicitly established; adding Vary is not an authorization design.

For content-versioned assets, [RFC 8246](https://www.rfc-editor.org/rfc/rfc8246.html#section-2) defines immutable as a commitment not to change the representation during its freshness lifetime, not forever and not a freshness lifetime by itself. Require an actual never-overwrite/versioning practice before proposing it. Keep mutable entry documents separate. Record how old asset versions remain available to older documents and how a corrected asset receives a different URL.

Treat failure behavior as part of the selected directive, not a separate undocumented CDN default. [RFC 9111 §5.2.2.10](https://www.rfc-editor.org/rfc/rfc9111.html#section-5.2.2.10) gives s-maxage the shared-cache revalidation constraint of proxy-revalidate; it is not merely max-age with a different audience. Under [the stale-response rules](https://www.rfc-editor.org/rfc/rfc9111.html#section-4.2.4), disconnection or a client's max-stale request does not override that prohibition. Record the expected outcome when the shared copy is stale and origin validation fails. Do not promise an offline fallback from the lifetime value alone, or remove the directive to obtain one without revisiting the approved freshness and privacy requirements.

Do not add stale-serving extensions merely for performance. If requested, document the allowed failure conditions, maximum extra age and target implementation support from its current official documentation. Keep that business decision distinct from the normal freshness interval.

## 3. Preserve representation identity and validation

For each class, list inputs that change the returned representation: path/query, language, content coding, relevant negotiation headers or user context. Compare that list with the actual cache key and response Vary handling. Do not strip query parameters or merge variants just because doing so increases hits.

[RFC 9111's Vary rules](https://www.rfc-editor.org/rfc/rfc9111.html#section-4.1) require matching nominated request fields for reuse without revalidation; `Vary: *` never matches. Review missing-header cases as well as two different values. Record unsupported provider key behavior as a blocker rather than assuming a conforming header alone fixes an overriding CDN rule.

Identify who generates ETag or Last-Modified and how it tracks the selected representation. Do not hard-code an invented validator in deployable configuration. A source inspection can establish the intended generator, not that production emits it correctly. If no validator exists, note that a policy requiring validation may need a full response rather than a conditional 304.

Record validator strength as well as its value. [RFC 9110 §§8.8.3.2–8.8.3.3](https://www.rfc-editor.org/rfc/rfc9110.html#section-8.8.3.2) distinguishes byte-sensitive strong comparison from weak comparison. Gzip and unencoded representations need distinct strong tags; `Vary: Accept-Encoding` does not repair a shared strong tag. Transfer framing alone does not create another representation. Inspect whether compression occurs after tag generation and which owner keeps the final validator consistent.

[If-None-Match](https://www.rfc-editor.org/rfc/rfc9110.html#section-13.1.2) uses weak comparison for cache validation, so a weak tag can still support conditional GET/HEAD. Do not strip `W/` to make it strong or treat a cache-validation match as proof of byte identity. Keep [conditional-write design](../design-api-contract/SKILL.md) and [range recovery](../interrupted-download-recovery/SKILL.md) separate: their stronger requirements are not established by a successful cache revalidation. If the generator or transformation behavior is unknown, hold the affected validator contract rather than inventing tags or silently changing compression.

[RFC 9110's 304 requirements](https://www.rfc-editor.org/rfc/rfc9110.html#section-15.4.5) tie Not Modified to conditional GET/HEAD and prohibit response content. A 304 must include the applicable Content-Location, Date, ETag, Vary, Cache-Control and Expires fields that would accompany its 200 response. Check the owning conditional-response path, not only ordinary 200 handling. Do not mistake an empty 304 for missing content or fabricate an unconditional 304 example.

## 4. Translate into the actual owning layer

Provide complete candidate header values for each class. When the requested target syntax is known, also provide a narrowly scoped patch or configuration fragment with its insertion point and replacement behavior. Do not invent generic CDN YAML or label a prose matrix deployable. If the platform is unknown, finish the header contract and hold only the platform translation.

Consult the actual provider/version documentation for cache eligibility, header precedence, bypass conditions and status-specific behavior. For example, [Cloudflare's Origin Cache Control documentation](https://developers.cloudflare.com/cache/concepts/cache-control/) distinguishes enabled/disabled behavior and interactions with Authorization and Set-Cookie. That is a provider dependency, not a rule to generalize to every CDN. Record the relevant effective setting without changing it.

Include error and redirect paths when they share the selected matcher. A successful asset policy must not accidentally make a personalized error or fallback inherit the same treatment. Preserve unrelated compression, authentication and routing settings. Do not remove Set-Cookie, weaken authentication or drop a meaningful variant merely to make a response cacheable.

## 5. Check the candidate and plan a bounded rollout

Read back the final artifact and reconcile it with the policy map. Walk an ordinary response, a boundary matcher, a personalized exception, two representation variants and an error/fallback when applicable. Derive expected outcomes from the requirements, not from the candidate itself. Static inspection must identify conflicting owners, unmatched exceptions and unresolved generator dependencies.

Write a small later verification worksheet: target/environment, request context without secrets, expected response class, relevant headers, expected reuse or validation, evidence to capture and a stop condition. [RFC 9111's age calculation](https://www.rfc-editor.org/rfc/rfc9111.html#section-4.2.3) accounts for upstream age and transit/residence time; do not restart freshness at every hop. A cache hit, a 304 and a fast response are different observations, not interchangeable proof of correctness.

Run checks only within the user's separately authorized scope. For a later live check, distinguish origin from edge and private-client behavior and use synthetic identities if isolation needs examination. Do not send credentials to an unapproved diagnostic service. A header capture alone cannot prove that one user's content was never reused for another.

Plan the transition before promising immediate effect. Identify already stored objects, old client copies, overlapping rules and any versioned URL changes. A new origin header is not proof that every old copy has disappeared. Name the operator, scoped invalidation or expiry dependency, and rollback artifact. Do not purge everything or erase a user's browser profile as a verification shortcut.

If deployment is outside scope, stop at the prepared package. If an authorized rollout later produces unexpected reuse, stop widening it, preserve the relevant evidence, and revert only the approved change through its owner. Do not repeatedly alternate TTLs or key rules without explaining which old objects remain relevant.

## Acceptance and handoff

Return the response-class map, concrete header/configuration candidate, owning-layer and source revision, unresolved decisions, and verification/rollout worksheet. The operator should be able to explain each class's audience, freshness, variants, validation and transition without guessing. Keep the package proportional to the selected routes.

Label evidence precisely: source reviewed, candidate prepared, syntax checked if actually performed, served headers observed if actually fetched, and reuse/validation observed only when actually exercised. Do not claim reduced latency, reduced origin load, privacy assurance or worldwide propagation from a documentation review.

## Fictional illustration, not executed

A fictional museum supplies three requirements: public exhibit HTML must be validated before reuse; versioned artwork bytes are never overwritten; visitor account details must not be stored in HTTP caches. Its draft policy maps `/exhibits/` to `Cache-Control: no-cache`, `/assets/v7/` to `Cache-Control: public, max-age=86400, immutable`, and `/account/` to `Cache-Control: no-store`. These are authored values for this scenario, not universal defaults.

The museum's asset matcher also catches missing artwork. The candidate therefore holds activation until the owning configuration distinguishes successful asset responses from the application's fallback. Its public HTML is language-negotiated, so the handoff records `Vary: Accept-Language` and requires checking the selected CDN's variant handling. It does not add a made-up ETag; the existing generator remains an explicit dependency.

Expected review outcomes are three distinct policies, a visible fallback hold, preserved language variants and a named validator owner. No HTTP requests, cache simulation, browser checks, deployment or purge were performed for this illustration. The policy remains a draft until its platform translation and checks are completed at the authorized level.

### Fictional shared-cache outage illustration, not executed

An invented public timetable has `Cache-Control: max-age=600, s-maxage=60` and no stale-serving extension. At an established current age of 90 seconds, an otherwise eligible browser copy is still within its 600-second lifetime, but the shared copy is stale. If origin validation cannot succeed, the shared cache must not serve that stale copy merely because the request accepts stale data. Replacing that two-lifetime policy with `max-age=60` would also shorten the browser lifetime; it is not an equivalent outage fix.

The handoff should distinguish those two cache decisions and hold any requested stale-fallback redesign for owner review. These are authored expectations, not measured cache behavior. No request, cache process, outage simulation, deployment or test was executed.

### Fictional compression-validator illustration, not executed

An invented document route negotiates gzip at its gateway. The supplied candidate preserves `Vary: Accept-Encoding` but forwards the same strong `ETag: "notice-8"` for both the compressed and unencoded bodies. The worksheet rejects that validator contract even though its variant key is present. The package names the gateway/tag-generator dependency and holds activation until its owner establishes representation-specific strong tags or a deliberately reviewed weak-validator design.

A separate conditional-GET worksheet compares stored `W/"notice-8"` with current `"notice-8"`. The opaque values match under weak comparison; the result is not a byte-equality certificate. These invented tag labels illustrate decisions, not deployable generators or observed responses. No compression, HTTP request, cache process, range request, write, test or deployment was performed.
