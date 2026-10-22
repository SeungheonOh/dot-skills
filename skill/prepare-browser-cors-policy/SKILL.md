---
name: prepare-browser-cors-policy
description: "Prepare a route-scoped browser CORS policy and implementation handoff from approved client origins, credential modes and request requirements. Use for a reviewable cross-origin response-sharing contract, not authentication design, browser-security bypass or live activation."
---

# Prepare a browser CORS policy

Deliver a client/route permission map, concrete candidate response headers or a targeted configuration patch, and a bounded verification worksheet. The result should explain which browser clients may read which responses, not merely make a console error disappear.

Use [API contract design](../design-api-contract/SKILL.md) when the operations themselves need designing, [connection diagnosis](../trace-web-connection-failure/SKILL.md) when the failing boundary is unknown, and [HTTP cache policy](../prepare-http-cache-policy/SKILL.md) for response storage and reuse. This workflow reconciles the browser-facing sharing policy across an existing application's client, server and gateway configuration.

## Establish the actual consumer

Read the selected client call sites, route definitions and supplied server/gateway configuration at an identified revision. Obtain only the relevant sanitized request evidence when source is unavailable. Record the page origin separately from the API destination, method, request header names/content type, credentials mode, response headers read by application code, and relevant error/redirect paths. Do not include tokens, cookies, private bodies or full account captures.

Confirm the intended audience from requirements, not from observed traffic. A request from an unfamiliar origin is evidence of a caller, not permission to admit it. Keep production, preview, staging and local-development clients separate. Ask only for unresolved audience or data-sharing choices that change the policy; continue preparing settled routes.

Preparation does not authorize endpoint calls, credential use, publishing, gateway edits, access expansion or deployment. Keep a proposed grant visibly separate from an approved requirement. Preserve authentication, authorization, CSRF protection and cookie settings. The [Express CORS middleware documentation](https://expressjs.com/en/resources/middleware/cors/) explains that its headers govern browser reading, not request admission; command-line and server clients do not enforce them. A CORS error therefore does not prove a write never happened. Do not retry an uncertain write to investigate sharing.

## 1. Make the audience exact

Build one row per materially different client/route combination. Include the requirement source, origin, path/method scope, credential mode, required request headers, required exposed response headers, owner and decision status. Group rows only when all relevant requirements agree. Unknown credentials mode is not the same as omitted credentials.

For ordinary HTTP(S) clients, compare parsed and serialized origins rather than URL prefixes. The [HTML origin model](https://html.spec.whatwg.org/multipage/browsers.html#origin) distinguishes scheme, host and port; paths are not part of an origin. A page under one path cannot receive its own origin grant while another page at the same origin is excluded by CORS alone. Opaque origins serialize as `null`, which does not identify one trusted local file or sandboxed page.

Prefer the supplied explicit origin list. Do not turn a list into an unbounded suffix match, include every preview deployment, or reflect arbitrary request values. If a dynamic origin policy is actually required, document who may create admitted subdomains and require a boundary-aware matcher. Include a deceptive suffix, a different port and an absent origin in its review worksheet. Keep `null` ungranted unless the owner explicitly addresses the broader opaque-origin audience; do not add it as a development workaround.

## 2. Translate the agreed rows into a header contract

Consult the current [Fetch CORS protocol](https://fetch.spec.whatwg.org/#http-cors-protocol), including its credentials rules. Apply these constraints:

- Emit one allowed origin, not a comma-separated origin list. Credentials mode `include` needs an explicit matching origin and `Access-Control-Allow-Credentials: true`, even when no cookie happens to exist.
- Successful preflight uses OPTIONS and a 2xx response. It does not carry cross-origin credentials; preserve authentication on the actual operation instead of requiring a session cookie to answer preflight.
- Distinguish `Access-Control-Allow-Headers` for request headers from `Access-Control-Expose-Headers` for script-visible response headers. List needed names explicitly, including Authorization when used; do not rely on wildcard semantics.
- Write both preflight and actual-response candidates. Include intended readable error responses; preflight success alone is insufficient.
- `Access-Control-Max-Age` concerns preflight permissions, not response freshness. Select a deliberate duration, not an assumed instant-revocation guarantee.

Determine preflight requirements from the complete request and the standard's safelist rules, not method alone. Do not rewrite a JSON request, remove an auth header or switch to `no-cors` to evade the intended contract. Hold unsupported requirements rather than broadening permissions until a request works.

Choose whether a route is genuinely public to arbitrary browser origins or restricted to the approved clients. Do not equate lack of a cookie with public data: intranet/network access and other contextual privileges need owner review. Keep route-specific policies separate instead of giving an administrative endpoint the policy of a public asset.

### Separate missing exposure from forbidden access

Classify each response header the client wants to read: already safelisted, exposable through an explicit grant, or forbidden. Under [Fetch's forbidden response-header names](https://fetch.spec.whatwg.org/#forbidden-response-header-name), Set-Cookie and Set-Cookie2 cannot become script-readable through Access-Control-Expose-Headers. The [filtered-response rules](https://fetch.spec.whatwg.org/#concept-filtered-response-basic) also exclude them from a basic response; moving a call to the same origin is not a remedy for this read requirement.

Record the blocked call site and intended application outcome, not cookie values. Distinguish browser cookie handling from application code reading a response header. A missing script-visible value alone establishes neither that the server omitted the header nor that a cookie was rejected.

Do not add a forbidden name to the candidate and mark the dependency solved. Refer an impossible client requirement to the application/authentication owner while continuing valid exposure work. Do not copy session credentials into a custom exposed header or body, remove HttpOnly, or introduce a token-storage scheme as an incidental CORS fix. A replacement application signal needs its own agreed contract.

## 3. Name the layer that owns each header

Identify whether the application, framework middleware, reverse proxy or gateway emits each value. Record ordering, matching boundaries, replacement behavior and the exact version documentation. Avoid double emission by two owners. Inspect the selected OPTIONS path, ordinary responses and relevant errors rather than only a successful controller response.

Return a complete candidate in the actual target syntax when that target is known. Otherwise return a header-level contract and identify the missing platform translation. Do not label generic pseudocode a deployable server configuration. For Express targets, consult the [middleware's configuration and preflight guidance](https://expressjs.com/en/resources/middleware/cors/) for route/application scope and explicit options; do not copy an application-wide permissive example into a restricted route.

Under the [Fetch cache guidance](https://fetch.spec.whatwg.org/#cors-protocol-and-http-caches), origin-dependent responses need `Vary: Origin`, including the no-Origin branch. An always-emitted static origin or wildcard does not itself require that variation. Preserve unrelated Vary fields.

Review the actual cache layer with the cache-policy owner. Record any override that could defeat the chosen variation; do not assume a candidate header repairs existing stored responses. Keep preflight permission caching, HTTP response caching and application state as separate dependencies. Do not clear browser profiles or purge shared caches as an unannounced check.

## 4. Review from the client and operator sides

Read back the saved artifact against the approved audience map. For each consequential branch, write an expected result before inspecting the candidate: approved client, unapproved client, credential-mode mismatch, needed request header, script-read response header, and relevant error path. Include only branches that affect this integration, not a mandatory large test suite.

Check that the operator can answer:

- Which exact requirements justify each permission, and which proposed grants remain unapproved?
- Which component answers preflight, and which supplies headers on actual responses?
- What happens for an unrecognized or missing origin without silently changing ordinary non-browser behavior?
- Which auth, cookie, redirect or cache dependency could still prevent the client task?

A static worksheet establishes intended decisions, not observed browser behavior. If later browser verification is separately authorized, use the intended page origin and a synthetic non-destructive operation. Record browser/context, request type, served headers and what script actually read. A raw HTTP response is not proof of browser accessibility. Do not weaken browser protections, install bypass extensions, use public CORS proxies or replay sensitive captures.

If a negative case unexpectedly gains access, stop rollout and preserve bounded evidence for the owning operator. Do not widen another origin or header list to compensate. Recover by correcting the candidate or reverting the specifically authorized change, not by deleting unrelated gateway policy.

## Deliver and stop at the requested boundary

Return the audience map, header/configuration candidate, source revision and owning layer, unresolved decisions, and verification worksheet. Name the preserved original or rollback artifact if a configuration replacement is proposed. Refresh the candidate when a source revision or client requirement changes.

Separate source review, candidate preparation, parser checks, served-header observation and browser-read verification. Claim each only when it actually occurred. A prepared CORS package is not evidence of deployment, successful login, safe authorization, successful writes or complete security review.

## Fictional illustration, not executed

A fictional catalogue has an established GET endpoint `/exports/latest`. Its approved client is `https://desk.example.invalid`, uses credentials mode `include`, and reads an application-defined `X-Export-Revision` response header. Its second approved client is `https://review.example.invalid`; other origins are not approved. The supplied request has no author-set non-safelisted headers, so this ordinary GET does not require preflight merely because credentials are included.

The candidate selects the matched approved origin for Access-Control-Allow-Origin, uses Access-Control-Allow-Credentials with value true, exposes X-Export-Revision and preserves Origin variation. It does not emit both origins in one header or grant arbitrary subdomains. The worksheet keeps a missing session as an authentication case, not a reason to broaden the origin policy. It separately checks whether an intended error response remains readable by the approved client.

If the client later adds an Authorization request header, that is a changed requirement: refresh the preflight branch and its owner review rather than assuming the original package covers it. These are authored expectations for invented inputs. No HTTP request, browser session, configuration parser, application, test or deployment was run for this illustration.

### Fictional forbidden-header illustration, not executed

An invented export client needs Content-Disposition for its save name and also tries to read Set-Cookie to decide whether to display “signed in.” Its draft exposure list contains both names. Review retains Content-Disposition as an ordinary explicit exposure requirement but rejects the cookie-read requirement. The login indicator remains blocked on an agreed application signal; the worksheet does not equate a hidden cookie header with failed sign-in.

Expected handoff: one usable naming requirement and one precisely identified client-contract blocker, without changing session handling or copying secrets elsewhere. These are authored expectations. No request, login, browser check, cookie inspection, configuration change or test was performed.
