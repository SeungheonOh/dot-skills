---
name: configure-desktop-web-proxy
description: "Configure an existing approved web proxy or PAC URL in a desktop's native network settings, preserve application and network-service boundaries, and verify the requested browsing path and ending. Use for client-side proxy setup, not choosing proxy providers, bypassing restrictions, authoring PAC scripts, VPN setup or administering a proxy service."
---

# Configure a desktop web proxy for its actual consumers

Deliver a usable, bounded web-proxy configuration on the identified computer, or a precise prepared handoff when activation or path verification is blocked. Separate the saved setting, the application's effective selection, a fresh resource read and the actual intermediary used. One successful page load does not establish all four.

Use an already available native macOS or Windows interface with an existing trusted proxy service. This workflow covers supplied manual web-proxy settings or an explicit, approved proxy auto-configuration (PAC) URL. It does not discover an arbitrary proxy, enable automatic discovery, write or repair PAC code, install interception certificates, change DNS/firewalls/routes, set up a VPN, or modify managed policy. SOCKS tunnels, application-specific proxy deployment and service-account configuration need their own supported procedure.

[Web-connection diagnosis](../trace-web-connection-failure/SKILL.md) identifies a failure boundary without reconfiguring the network. [An existing VPN session](../connect-existing-vpn-session/SKILL.md) establishes a separately provisioned tunnel. [Integration configuration handoff](../prepare-integration-config-handoff/SKILL.md) prepares loader-specific artifacts rather than activating native desktop settings. Do not append these workflows unless the requested result needs their distinct work.

## Establish the target and routing contract

Resolve the consequential inputs from the request, current settings and trusted administrator/provider instructions:

- Computer, OS/version, ordinary user context and named browser/application profiles
- Intended native scope: the selected macOS network service or Windows settings context, with VPN-specific settings distinguished
- Configuration owner and verified manual server/port/protocol assignments, or exact approved PAC URL and its owner
- Required exceptions and simple-hostname behavior, preserving their platform-specific meaning
- Which approved destinations should use which intermediary, which may connect directly, and whether direct fallback is acceptable
- Existing discovery, manual, PAC, application override and managed settings that could compete with the proposed change
- One or a few harmless resource checks, the required level of route evidence, and whether the setting should remain enabled or be restored afterward
- Active uploads, calls, remote files and the assistant's own observation/control connection that could be disrupted

Do not require a network-wide inventory. A verified configuration, intended consumer, expected route and safe local recovery path can suffice. Ask for the exact missing endpoint, scope or fallback decision rather than inventing a port, exception or organization hostname. Do not copy a setup snippet from an unverified message into network settings.

A request for one browser does not necessarily authorize a native change that affects other applications using those settings. Explain the actual wider scope before activation; if the requirement is strictly application-only, hold the native change. Do not silently substitute a browser extension or command-line flag. Likewise, an endpoint supplied for one network service or VPN is not authority to copy it into every network context.

## 1. Preserve the current configuration and a way back

Read the exact controls and relevant effective application settings without saving. Record a compact non-secret before-state: selected service/context, enabled modes, ordinary server/port fields, exceptions, and whether each value is editable, inherited or managed. Keep inactive configured values when they could become a fallback; an off toggle does not make its stored endpoint irrelevant.

Do not reveal passwords, tokens or credential-bearing URLs. If a PAC address contains authentication material, stop before copying it into chat, logs, screenshots or a report; use the required protected user-controlled entry route. Do not export a complete network profile, browser environment or credential store to preserve a few fields.

Identify the actual consumer. A browser's own proxy setting, extension or policy may take precedence over the native configuration. Read the relevant evidence; do not disable it to force agreement. A command-line client is not automatically a substitute for the requested browser. The [platform and consumer notes](references/native-settings.md) give the native paths and the documented distinctions to check for the installed versions.

Preserve unsaved work through the application before a change that could interrupt it. Do not retry a purchase, upload, message submission or other uncertain write as a connectivity check. A safer existing read-only page can establish part of the path without reproducing the consequential action.

If changing proxy state could sever remote control, arrange local observation and a user-readable return path first. Do not enable another remote-access service or schedule an unattended rollback to compensate. Without a reliable recovery route, prepare the exact steps and have the user perform the transition locally. Losing the tool connection is neither evidence of successful activation nor permission for blind retries.

## 2. Review mode, exceptions and fallback before activation

Create a small change record containing the old state, proposed state, expected affected consumers and requested ending. For a simple manual configuration this can be a few lines; do not manufacture a separate workbook.

For **manual settings**, bind each target-protocol field to the supplied server and port. Distinguish the destination URL scheme from the transport to the proxy; an HTTPS website or a native control label is not enough to promise encryption of every network leg. Do not enter a full URL into a host-only field or assume that an HTTP field also configures HTTPS. Preserve separate values when the supplied contract requires them.

For **PAC**, confirm the exact configuration source and owner, not just a filename ending in .pac. Enabling the URL delegates request-routing choices to a remotely supplied program that can change without editing the local URL. Establish the approved routing scope and fallback expectation from its owner and applicable consumer documentation. Do not execute downloaded PAC in a shell, general-purpose interpreter or online checker, or rewrite it to make a failing destination go direct. Static inspection, if permitted and useful, is evidence about supplied text rather than proof of the native consumer's selection.

For **exceptions**, retain the documented platform syntax and the intended host classes. Distinguish a short hostname, a fully qualified name and a broad wildcard. A private-looking name is not itself a reason to bypass the proxy. Do not enlarge the exception list or toggle simple-hostname bypass to make a test pass. The manual exception list is not automatically a policy for a PAC-selected route.

For **competing modes**, determine the actual precedence and fallback from current platform/application documentation. Do not turn every mode on as insurance or turn automatic discovery off merely for tidiness. An existing manual value can matter if PAC acquisition fails. If the approved requirement forbids direct access, do not claim that native proxy configuration alone enforces that requirement; hold activity requiring that guarantee until the owner establishes an adequate supported control.

This is a network-security setting change. Obtain required action-time confirmation immediately before applying the exact change, even when the overall task already requested proxy setup. Describe the computer, scope, proxy/PAC operator, affected traffic, expected exceptions/fallback, persistence and interruption risk. Explain that the intermediary can receive destination information and potentially unencrypted HTTP content; do not promise anonymity or assume inspection rights. Resolve any separate approval needed for the information and recipient before sending the check traffic.

Credential entry and submission remain with the user through a supported secure flow. Do not copy credentials into fields, URLs, commands or artifacts, save them as a convenience, or create persistent access under the setup request. Unexpected authentication, certificate trust, permission or enrollment prompts are separate boundaries. Do not bypass browser security warnings, add trust anchors, disable validation or accept an unknown proxy identity.

## 3. Apply the smallest native change and read it back

Use the matching branch in [native settings](references/native-settings.md). Select the identified service/context and modify only the approved controls. Preserve unrelated protocols, exceptions, existing values and other network services. Do not use registry edits, environment variables or a global network reset to imitate the native change.

Complete only the authorized save/apply transition. Reopen the same native panel and compare its saved state with the approved record. Retain the difference between typed, saved and effective values. A setting that reverts, becomes locked or is replaced by policy is a blocked result, not a reason to fight management with another interface.

If a save times out or observation disappears, inspect the current native state before repeating it. Do not assume the old state remains. If someone changed the settings concurrently, reconcile ownership and the new values rather than overwriting them with the stale before-state.

Application restart or reload may be necessary for the actual consumer; establish its documented behavior and safe boundary first. Do not close other profiles, clear caches or discard sessions just to force a new connection. If safe adoption cannot be observed, report the native setting as saved and the consumer state as pending.

## 4. Verify the intended consumer, resource and intermediary

Use the named application/profile on the same computer and network context. Start with the agreed harmless read and the original hostname. Do not substitute an IP-address URL, an unrelated public IP-check service or a different browser and call it equivalent. Do not send private destinations to a public diagnostic service.

Retain four separate results:

| Layer | Useful evidence | Limit |
| --- | --- | --- |
| Saved native configuration | Reopened settings match the accepted scope and values | Does not show that the application adopted them |
| Effective consumer selection | Supported app settings or scoped diagnostics identify the configuration source and selected route for this request | A candidate proxy list does not establish the endpoint actually used |
| Resource use | A fresh harmless network read completes in the intended app/account | Cache, service-worker content or a login page can leave the requested access unproved |
| Actual path | Existing permitted request-level diagnostics or owner-supplied evidence bind the request to the intended proxy or approved direct route | One request does not establish every destination, protocol, app or future request |

Require the path layer when acceptance depends on using the proxy. Otherwise state clearly what was saved and observed without claiming verified routing. An OS route lookup concerns an IP path and cannot by itself settle a browser's proxy-selection decision. An unchanged or changed public IP is also insufficient.

For a required bypass, check only an approved harmless destination in that class, and keep an observed direct route separate from mere reachability. Never add DIRECT fallback or an exception to create the expected result. PAC acquisition, PAC evaluation, proxy connection, proxy authentication, destination TLS and destination authorization are different failure boundaries; retain the earliest evidenced failure without inventing its cause.

Prefer already available minimized diagnostics. Do not capture all traffic, dump authorization headers, export a full browser NetLog or upload logs merely to make the evidence stronger. If the available interface cannot bind the request to its actual route without new data collection or access, report that exact verification gap. Do not manufacture certainty from a green settings indicator.

Keep observations tied to time, application/profile, network service, destination and configuration state. If Wi-Fi, Ethernet, VPN, app profile or PAC contents change, prior evidence may no longer describe the new context. Recheck only the requested relevant path; do not roam across networks to claim universal support.

## 5. End deliberately and recover at the failed boundary

Leave the approved configuration enabled when the user requested continuing use. Provide its normal inspection and return path, and note that ongoing PAC content and other application overrides remain relevant. Do not disable it simply because the check finished.

If restoration is requested, preserve active dependent work and obtain the required action-time confirmation immediately before restoring the exact approved prior state. Restoration is another network-security transition. Reopen the controls and check the intended consumer again when safe. Removing the newly entered URL alone may leave a manual mode or automatic discovery active; restore the actual agreed state, not an imagined universal “direct” default. Do not delete saved credentials, profiles or unrelated configuration as cleanup.

- **Untrusted or ambiguous endpoint/PAC owner:** do not activate; request the authoritative configuration through an established channel
- **Managed or locked settings:** preserve them and return the exact owner-controlled prerequisite; do not change policy or use another setting source to evade it
- **PAC not acquired or applied:** separate native URL storage from consumer acquisition/evaluation; do not substitute another URL, add fallback or disable discovery without a new approved change
- **Proxy unavailable or authentication fails:** stop unchanged attempts, preserve the non-secret error and avoid account lockout; a direct connection is not an equivalent repair
- **Page works through an unexpected route:** hold the proxy-success claim and affected activity whose routing requirement is unmet; resolve selection/fallback evidence before changing anything
- **Certificate or destination-access failure:** preserve the boundary; do not trust a new certificate, bypass a warning or try another account
- **Uncertain save or lost observation:** obtain local state before retrying; report any unknown current routing state
- **Rollback cannot be verified:** stop further changes, report the exact residual state and give the user the documented local recovery path

Stop when the requested saved configuration, consumer/resource/path evidence and ending are established, or a concrete input, permission or capability blocks the next step. An active save or check remains pending until its outcome is observed; repeated unchanged failure does not justify a broader reset. Do not turn this setup into ongoing monitoring, provider administration or unsolicited support outreach.

## Deliver the usable result

Return a concise private handoff identifying the computer and native scope, configuration owner and non-secret mode/endpoint identity, changed controls, exceptions/fallback, checked application/profile and destinations, evidence for each required layer, and final state. Include the short normal-use/restoration route and any remaining decision. Save a separate artifact only if useful or requested, and read it back for accidental secrets or private request content.

Use an accurate completion label: **prepared; activation not performed**, **saved; consumer adoption unverified**, **resource read observed; actual proxy path unverified**, **usable within the checked scope**, or **restored; final consumer check pending**. A native setting alone is not a privacy guarantee, all-application routing enforcement or proof that a remote PAC will make the same decision tomorrow.

## Fictional, unexecuted illustration

A fictional Windows user wants a trusted organization's explicit PAC URL applied for an existing browser profile and retained for work. The supplied setup record permits that organization's named proxy, requires one reference page to use it, and forbids direct fallback for that page. The before-state contains an older manual proxy value as well as the proposed script setting.

The proposed workflow would resolve the old manual value's role and actual fallback behavior before activation, establish the affected native scope, preserve work, and request the action-time network-change confirmation. It would not erase the old value or add an exception by assumption.

In an invented continuation, the native URL saves and the reference page appears, but the page came from cache. The resource and route requirements would remain unmet. If later supplied diagnostics showed a failed PAC fetch followed by a different manual proxy, page availability would still not establish the requested configuration. The result would identify that selection boundary and hold the success claim rather than announcing that PAC works or turning the proxy off. Any restoration would require its own confirmed transition and readback.

This is original, fictional and unexecuted. No computer, browser, network, proxy, PAC program, credential, setting, request or diagnostic capture was operated for this illustration. The operational checks describe future authorized work, not evidence of live validation.
