---
name: trace-web-connection-failure
description: "Locate the evidenced failure boundary for a website that will not connect or load, separating destination, name resolution, connection, TLS, HTTP and page-resource failures. Use for a bounded connection diagnosis and actionable handoff, not security bypass, network reconfiguration or application-code repair."
---

# Find where a web connection stops

Return a useful explanation of the failing request and the smallest next action supported by evidence. A browser's generic error page, a successful ping or a working public landing page does not establish what happened to the user's requested page. Keep observations tied to the actual client, destination and time.

Use [isolate-browser-profile-failures](../isolate-browser-profile-failures/SKILL.md) when a matched comparison already points to one browser profile, [audit-har-request-timings](../audit-har-request-timings/SKILL.md) for detailed performance calculations, and [integration-delivery-reconciliation](../integration-delivery-reconciliation/SKILL.md) for whether an application write eventually took effect. This workflow locates a connection/load boundary; it does not reset the network or establish a website's security.

## Establish the request and safe observation

Identify the intended site from the user's link or other trusted source, affected page or operation, expected result, exact visible error, approximate onset and whether the failure is current. Record the client/browser, device and network context that actually experienced it. State whose browser or computer any new observation uses; a cloud browser result is a comparison, not a measurement of the user's laptop.

Ask only for missing information that changes the next check. A screenshot with its error code and a known destination can be enough to start. For technical evidence, retain scheme, hostname, port and relevant path separately. Keep query values, private path segments, fragments, account names and internal addresses out of the shareable report unless needed and authorized. Do not follow an apparent replacement login or support link from an error page without verifying its destination independently.

Determine whether a retry is harmless. A page load can issue writes, send a one-time link, resubmit a form or repeat a download. Preserve unsaved work and inspect uncertain operation outcomes before retrying. Do not replay captured requests, copy a request as a credential-bearing command, or submit a real transaction to reproduce a connectivity symptom. If no safe reproduction exists, work from the supplied evidence and state that limit.

Keep the scope to named destinations and necessary documented dependencies. This is not permission to scan ports, enumerate hosts, test unrelated systems, use a public diagnostic service with a private hostname, or capture all device traffic. Prefer existing error details and request metadata over a full HAR or packet capture. Headers, bodies, cookies and browser logs can contain credentials and personal data; do not export them just because a support form asks.

## Build a small request-path record

Preserve the original error and observations before changing conditions. For each relevant attempt record:

- Time with timezone, client/version if material, device/network label and account context where relevant
- Intended destination, actual request/redirect destination and observation source
- Method or safe user action, whether the response came from the network, cache or a service worker when known
- Exact error/status, last evidenced successful boundary and first evidenced failure
- What is unknown, the next discriminating check and any unmatched comparison conditions

Keep attempts and resource identities separate. A page may load its HTML successfully and then fail to obtain a script or data response. One failed analytics request may have no bearing on the broken feature. Connect a failed dependency to the symptom using initiator, page behavior or established architecture rather than choosing the first red row.

Inspect effective developer-tool conditions if already available: offline emulation, throttling, request blocking and overrides can affect a test. Record them without assuming they are defaults or silently clearing the user's debugging setup. Consult the actual browser's current documentation. [Chrome's Network reference](https://developer.chrome.com/docs/devtools/network/reference) distinguishes HTTP statuses, blocked requests, CORS errors and failed requests; its log only covers requests observed while recording. A missing row from an incomplete capture is not proof that no request occurred.

## Locate the earliest supported failure

Use the available evidence to choose a branch; do not require every layer to be actively probed. Later success can establish an earlier prerequisite for that particular attempt, but it cannot fill a missing history for another attempt.

| Boundary | Useful evidence | Important limit |
| --- | --- | --- |
| Destination and client handling | Exact typed/opened destination, malformed-URL or unsupported-scheme error, redirect chain | A search result or similar hostname is not an authorized replacement; an app-routing problem may precede networking |
| Name resolution | Browser's resolution error; an authorized resolver result for the exact hostname and context | A command-line resolver can differ from the browser's resolver, proxy or cached state; no answer is not automatically a global DNS outage |
| Connection to an endpoint | Connection refusal, timeout or reset tied to the resolved destination or proxy | These observations do not uniquely identify firewall, routing, server load or server ownership; ping uses a different path/protocol |
| TLS and certificate validation | Browser security/error details, hostname match and validity information when exposed | A TLS failure is not a successful secure HTTP exchange; do not bypass it to obtain a page |
| HTTP response or redirect | Actual status and response source, redirect destination and relevant safe metadata | A response may come from a proxy, gateway, cache or service worker; an HTTP error is different from failure to connect |
| Page and dependency use | Main-document result, necessary subrequests, browser blocking or script errors | Receiving bytes does not establish that the application rendered or completed the requested task |

For name-resolution differences, keep hostname, resolver context, answer family and time. Multiple addresses can be normal, and a split-horizon corporate name may intentionally resolve differently. Do not change DNS providers or query private names through a new public service to get a preferred answer. Do not treat an IP-address URL as an equivalent HTTPS test: it changes hostname-dependent routing and certificate validation.

For transport evidence, distinguish the destination from an explicitly configured proxy. A browser using a proxy need not resolve or connect in the same way as a direct command-line client. A successful connection to one address/family does not establish all addresses work. If existing read-only tools can make an appropriate narrow comparison, keep its host, request count, timeout and result bounded; do not turn it into a scan or broad traffic capture.

For TLS, record the specific error and the relevant visible certificate facts without exporting unrelated certificate stores. A local clock discrepancy is a hypothesis to verify, not permission to change system time. [Chrome's security-panel documentation](https://developer.chrome.com/docs/devtools/security) describes inspection of HTTPS and certificates. Certificate exceptions, insecure flags, trusting a new certificate, disabling interception/security software and bypassing a browser warning are outside this workflow; stop at the applicable handoff or approval boundary.

For HTTP, distinguish response receipt from useful content. A login redirect can establish reachability while leaving authorization unresolved. A 404, 403 or 5xx supports only the actual response observed, not a universal root cause or permission to try another identity. Preserve individual redirect hops; a success before a redirect does not establish reachability of the new origin. A HEAD response can differ from the user's GET path. Do not strip meaningful URL parameters to create a supposedly equivalent request.

For page failures, separate the top-level document from its dependencies and the browser's decision to expose a response to script. CORS or mixed-content blocking is not evidence that changing the user's network will repair the application. Do not disable browser protections or add a permissive extension. A command-line client receiving data does not demonstrate that a browser is allowed to use it.

When a command-line comparison is appropriate and already permitted, consult that installed client's documented errors and preserve its context. [libcurl's error reference](https://curl.se/libcurl/c/libcurl-errors.html) separates proxy resolution, host resolution, connection and TLS failures. Do not equate a curl exit status, an HTTP response status and a browser-specific error code.

## Use comparisons to narrow the explanation

Choose the smallest comparison likely to distinguish the remaining hypotheses. Prefer an already available known-good page, current official service-status evidence or a closely timed existing observation before changing anything. A status page saying operational does not exclude a regional, account-specific or dependency failure.

Keep destination, method, account, network, client settings and time as comparable as practical. Changing browser, device and network together can show context dependence but cannot isolate which change mattered. Label this explicitly. Success from the assistant's cloud computer establishes only that cloud context; failure there can also be a tool/network restriction.

Do not switch Wi-Fi, disconnect VPN, alter proxy/DNS/firewall settings, flush caches, clear browser data, restart shared equipment or install a diagnostic tool under a diagnosis request. If an already-authorized narrow non-security correction is within scope, record its previous and new state and repeat the same safe check. Otherwise return the exact proposed action and consequence for the appropriate decision. Do not keep retrying unchanged requests after a rate-limit response, authentication challenge or evidence of a deliberate access restriction.

If the failure disappears, record an intermittent or no-longer-reproducing result with time and conditions. Do not credit a setting that was never changed, or claim the original cause was established by eventual success. If a matched profile difference emerges, hand that concrete differential to the profile-isolation workflow rather than accumulating network speculation.

## Deliver and recover

Provide the conclusion first, followed by a compact request-path record and one useful next check. For a support handoff, include minimized identifiers, times, affected scope, exact error, comparison limits and the question the receiving team can answer. Do not send it or upload logs without authority for that destination.

Acceptance requires that:

- The conclusion refers to the correct destination, request and client context
- Observed successes/failures, causal hypotheses and untested boundaries are separated
- The evidence accounts for relevant redirects and necessary resource failures without claiming complete capture when it was partial
- No success claim relies solely on ping, a different public page, a stale cached response or another machine
- Any authorized correction has actual before/after evidence and a clear final state; otherwise the result is a diagnosis or proposed remedy

For saved reports, reopen the actual file and check that private URLs, credentials and unrelated logs were not copied in. Inspect an uncertain save before retrying. Preserve the user's sessions and settings; disclose any authorized temporary state still active. Stop when the requested boundary is established or the exact missing access, permission or observation is identified. Do not create ongoing probes unless separately requested.

## Fictional, unexecuted example

A fictional library website's main page loads, but opening its catalogue shows a connection error. Supplied browser records show the main document came from the network with HTTP 200; the required catalogue request to a second hostname failed during name resolution. A successful request to the main page from a cloud browser is also available.

The report would localize the observed failure to resolving the catalogue hostname in the affected browser context. It would not call the entire website down, blame the user's router, or treat the cloud result as proof that the catalogue works. The next useful check would be the exact hostname's resolution in the same authorized context, with browser/proxy differences retained. No DNS settings, profiles or security controls would be changed.

This is an invented reasoning example. No website, resolver, browser, network probe or repair was executed.
