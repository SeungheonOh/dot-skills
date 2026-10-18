---
name: configure-local-https-development
description: "Establish a trusted HTTPS origin for an existing local development application, connecting exact names, certificate identity, client trust, server configuration and application checks. Use for local HTTPS setup or repair, not public certificate issuance, production TLS, warning bypasses or general network diagnosis."
---

# Configure a local development HTTPS origin

Deliver a development URL that the intended local browser can validate normally and use for the requested application activity, plus the minimal reusable configuration and a secret-free operating note. A certificate file, a running process and a page without a visible warning are different checkpoints. Establish their connection to the same intended origin.

Keep this workflow to one developer's machine and an existing non-production application. Phones, remote teammates, public tunnels, public DNS, production certificates, mutual TLS and organization-wide certificate authorities need a separate scope. Do not distribute a development authority to make an unrelated client work.

[Connection diagnosis](../trace-web-connection-failure/SKILL.md) locates an existing failure without changing trust. [Integration configuration handoff](../prepare-integration-config-handoff/SKILL.md) authors secret-free settings without activation. [Development containers](../configure-development-container/SKILL.md) define the runtime lifecycle. This workflow owns the local HTTPS identity and trust setup across those boundaries; it does not replace their broader work.

## Establish the intended origin and evidence

Find these inputs in the user's request, project instructions and existing configuration before asking for missing decisions:

- Exact machine, OS, browser/profile and versions that must use the application
- Project/workspace and existing development-server version, startup route and current working state
- Why HTTPS is needed, the exact scheme/hostname/port, and one harmless activity that demonstrates the requirement
- Whether the process runs directly on the host, in a local container or through an existing local reverse proxy
- Existing development certificate authority and certificate arrangements, described by public metadata and ownership only
- Whether the user wants a prepared configuration or activated local setup; permitted installs, edits, service starts and final running/stopped state

Do not install a trust anchor merely because a feature is described as requiring a secure context. The [Secure Contexts specification](https://www.w3.org/TR/secure-contexts/#is-origin-trustworthy) treats certain loopback origins as potentially trustworthy. That property is not encrypted transport or evidence that all browser APIs, cookies and integrations behave identically. Establish whether an actual HTTPS URL is part of the requirement. If the existing localhost setup already satisfies the request, report that rather than creating unnecessary credentials.

Inspect only relevant settings and public certificate information. Do not dump the process environment, browser profile, keychain or private key files. Preserve existing edits and record the current startup/configuration route before modifying it. If the machine, safe key-provisioning route or required approval is unavailable, finish a precise secret-free candidate and name the held activation step.

## 1. Map names, addresses and process boundaries

Make a small origin map, not a general network inventory:

| Boundary | Record |
| --- | --- |
| Browser origin | Exact HTTPS hostname or IP literal and port the user will open |
| Resolution | Intended local address and how that name resolves on this machine |
| Listener | Owning process, actual bind address and port |
| TLS termination | The server or local proxy presenting the certificate |
| Application | Existing upstream, if any, and the harmless acceptance activity |
| Certificate | Required DNS names or IP addresses, issuer identity and public fingerprint when available |
| Trust consumer | Specific browser/profile and any separately required client |

Prefer the existing supported localhost route when it meets the task. A certificate for a name does not configure name resolution. Likewise, setting a development server's host option does not add that name to a certificate. Do not add wildcards, unrelated domain names or IP addresses merely for convenience. A port belongs to the URL and listener configuration, not the certificate's name list.

Keep loopback exposure explicit. A certificate does not make a development server safe to publish. Preserve a working loopback bind and do not change it to all interfaces, add firewall rules, enable a tunnel or publish a container port broadly to fix a failed load. A browser on the host and a process inside a container have different loopback contexts. Resolve that path without copying a whole credential directory into the container.

If a custom name or existing proxy is genuinely required, document only the exact proposed mapping and its scope. Changes to host resolution, proxy behavior or other security-sensitive network settings require the applicable specific approval. Do not replace the user's system proxy, DNS provider or unrelated hosts-file entries.

## 2. Separate certificate issuance from trust installation

Use the project's established supported development method when it is suitable. An already approved certificate and trust arrangement may need only correct server wiring. Do not create another authority to mask an expired leaf certificate or wrong file path.

For a new local authority, consult current official tool and platform documentation. [mkcert's documentation](https://github.com/FiloSottile/mkcert) describes local development issuance and supported trust stores; it does not configure the web server. Its installation into trust stores and its issuance of a server certificate are distinct operations. Do not run a setup command just to discover its effects.

Explain the important security consequence before requesting action-time approval: trusting a local authority permits certificates signed by it to be accepted by the selected consumers, and that trust is not restricted to this project's port. Name the authority, machine and intended trust stores. Avoid automatic installation into additional stores just because the tool discovers them. A managed-device restriction is a blocker to resolve with its owner, not a reason to use a hidden exception.

Credential creation and persistent key configuration also need their applicable action-time approval. Keep private-key generation, entry, copying, import and submission user-controlled through an appropriate secure local route; do not ask the user to paste keys or passwords into chat. Hand off before any highly sensitive material would be transmitted. Only continue with public metadata, an approved local binding reference and the observed provisioning result. If an existing server already owns its protected key binding, retain that route rather than exporting it.

The public root certificate, root private key, leaf/server certificate and leaf private key are different objects. Never put the root private key in the application or a container. Never include private keys in source control, bundles, cloud-synced output, logs, screenshots or support attachments. [Google's local HTTPS guidance](https://web.dev/articles/how-to-use-local-https) recommends separate developer-local authorities instead of sharing a team's authority and certificate material. This guide does not authorize distribution of either keys or trust anchors.

Use a private local destination outside the served root, build context and shared/synced directories. Check the actual destination; a folder name such as private is not proof of its access boundary. Before issuance, ensure new outputs cannot overwrite another project's credentials. If safe storage requires permission changes, obtain the specific authority rather than applying a recursive permissions fix. Do not treat ignore rules as protection from an HTTP server or a Docker build context.

## 3. Inspect the public certificate and prepare server wiring

After the user-controlled provisioning step, inspect only the public certificate using an available documented viewer. Record issuer, validity interval, intended DNS/IP coverage and a public-certificate fingerprint sufficient to match it to the served certificate later. Keep private infrastructure names out of a public handoff.

A certificate's subject label alone is insufficient name evidence. Use the documented identity-checking facilities for the intended DNS name or IP literal. [OpenSSL's x509 reference](https://docs.openssl.org/3.6/man1/openssl-x509/) distinguishes certificate printing, hostname checking and IP checking options; select read-only operations and verify support in the installed version. A matching name does not establish a trusted chain, a valid current time or the server's possession of the matching key. Leave each unobserved property open.

Author the smallest scoped configuration change for the installed server, keeping the established startup command, application settings and HTTP fallback intact where required. Refer to user-provisioned local certificate/key paths through the project's supported private binding mechanism. Do not embed key contents. Configuring a new persistent credential binding remains held for its required approval or user-side step even when only a path is written.

Use server-version documentation for the TLS options, bind address, fixed port and any hot-reload WebSocket endpoint. For example, [Vite's server options](https://vite.dev/config/server-options.html) distinguish HTTPS configuration, address binding and strict port behavior. Do not paste a setting from the latest docs into an older installed version without checking support. If a required fixed port is occupied, return that conflict; do not silently accept a different origin or terminate the other owner.

For an existing reverse proxy, establish which process terminates TLS and which certificate it presents. Preserve the upstream route and record whether its separate hop is HTTP or HTTPS; browser-to-proxy encryption is not evidence about that hop. Do not introduce a proxy solely to avoid understanding the current server's TLS support.

Inspect startup scripts and plugins for installation, code execution, additional listeners, automatic opening and network calls before launching. A configuration file can execute code. A request to draft configuration does not authorize starting the application, installing packages or running setup hooks. Keep shared configuration secret-free and machine-specific bindings private; deliver only changes within the approved edit scope.

## 4. Activate and verify the same origin

Read back the saved configuration and confirm its identity before any authorized launch. Start only the owned development process through the established route. Record its actual listener, TLS termination point, selected certificate and any unexpected alternate-port behavior. After a timeout or lost control session, inspect the existing process before retrying; do not create duplicate listeners.

Use the intended browser on the intended machine. State whose browser is being used; a cloud browser's localhost is a different destination. Open a harmless application route with no production transaction or secret-bearing request. Verify the exact final origin after any redirect.

Check the following independently:

1. **Identity and trust:** the browser performs normal certificate validation without an exception or disabled checks. Its displayed certificate corresponds to the intended leaf certificate and issuer, covers the URL identity and is within its validity interval
2. **Application identity:** the response is the expected local project and current process, not another service, a cached page or a stale service worker response
3. **Required behavior:** the agreed harmless activity works at this exact origin. If secure-context status matters, inspect that status in the page context; it is not a substitute for the TLS check
4. **Dependencies:** required subresources, local API requests and development WebSockets use the intended routes and actually function. Distinguish application failures from trust failures
5. **Exposure and retention:** the listener remains within the approved local boundary, unrelated configuration is preserved, and the agreed final service state is observed

Use the browser's supported certificate/security inspection. [Chrome's security-panel guide](https://developer.chrome.com/docs/devtools/security) describes inspecting certificate and origin details. Do not rely solely on an address-bar icon or the absence of an interstitial that the profile may previously have bypassed. If an existing exception, insecure launch flag or unknown validation state prevents trustworthy evidence, hold the normal-validation claim; removing it is a separate scoped decision.

A command-line HTTPS result supports only that client's trust configuration. It does not establish browser trust. Similarly, browser success does not establish that another runtime accepts the authority. Add a second consumer only when requested, and obtain approval before changing its trust settings.

If a page loads but required resources fail, inspect the precise dependency. [MDN's mixed-content guidance](https://developer.mozilla.org/en-US/docs/Web/Security/Defenses/Mixed_content) explains browser handling of insecure resources in secure pages. Do not disable mixed-content checks, CORS, certificate verification or other browser protections. Correct an in-scope local endpoint or return the required application change separately. Do not switch to production services to obtain a green check.

## Recovery and stopping

- **Wrong certificate served:** inspect the selected server instance, termination point and loaded public certificate before changing trust. A newly trusted authority cannot repair a server still serving another certificate
- **Unknown issuer:** compare the actual browser/profile and intended trust-store result. Do not repeatedly install the authority into every discovered store or click through a warning
- **Name mismatch or validity failure:** preserve the public evidence and return the exact reissuance or clock-verification prerequisite. Do not broaden name coverage or change system time without authority
- **Key access or pair mismatch:** stop repeated starts and let the user correct the protected binding. Do not print the key, loosen permissions broadly or replace the authority as a shortcut
- **Partial issuance or installation:** preserve the identities and observed state; inspect before retrying. Do not overwrite files, create another authority or assume an interrupted installer made no change
- **Unexpected network exposure:** stop further use and report the observed listener. Stop only an owned process when authorized; changing a firewall or unrelated service is not incidental recovery

Rollback has separate layers. Reconcile and restore only the edited server settings, preserving subsequent user edits. Stop only the identified owned process if that is the agreed ending. Removing an authority from a trust store is a security-sensitive change that needs its own applicable approval and dependency check; it may break other local projects. Deleting key files is a separate deletion decision and does not remove installed trust. Restoring a configuration does not undo trust installation, certificate copies or earlier exposure.

Stop when the selected origin and requested activity are established, or an exact permission, provisioning or client-access blocker remains. Do not renew certificates on a schedule, install background services, change team settings or publish the project as an implied follow-on.

## Deliver and accept

Return the minimal configuration or patch, exact local URL, startup/stop instructions, public certificate identity and expiry, intended trust-consumer scope, private binding location by reference only, and the observed final process state. Identify what remains machine-local and must not enter source control. Include a short renewal note: replacement issuance requires the same protected process, and the served replacement must be checked again; do not claim automatic renewal.

Separate prepared, provisioned, trust installed, server running, browser validated and activity verified statuses. Acceptance requires evidence connecting the intended certificate, normally validating browser, exact origin, correct application and useful behavior. If only files were prepared, deliver those files and the remaining steps without calling HTTPS operational. This is local development setup, not a security certification or proof of production readiness.

## Fictional, unexecuted illustration

An invented developer wants an existing local preview application to use https://localhost:8443 for its documented browser integration. The server currently binds to loopback. The user wants a configuration candidate first, and has not authorized trust changes, credential creation or execution.

The candidate would retain loopback and the fixed port, identify the installed server's HTTPS options, and describe a private user-controlled certificate/key binding outside both the project and served root. Its certificate requirement would cover localhost; it would not add a LAN address or wildcard. The prepared note would identify the particular browser as the required trust consumer and hold all provisioning and activation steps.

For a later explicitly authorized activation, suppose the browser showed a certificate for an old preview name while a newly provisioned public certificate covered localhost. The next step would inspect which server or proxy loaded the old certificate. Installing the new authority again would not be the remedy. Only after the intended certificate is actually served, normal browser validation succeeds and the harmless preview interaction works would the result qualify as operational.

These are fictional inputs and proposed reasoning, not observed results. No key was generated or read, certificate issued, trust store changed, server started, browser operated or application check executed for this illustration.
