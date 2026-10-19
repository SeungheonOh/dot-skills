---
name: configure-desktop-app-firewall-access
description: "Create or revise a bounded native desktop inbound firewall exception for a known installed application, reconcile saved and effective policy, and verify the intended peer activity without widening unrelated access. Use for host-side app access, not general connectivity diagnosis, router forwarding, outbound isolation or managed-policy bypass."
---

# Allow the intended incoming app connection

Deliver the smallest supported native firewall exception for an existing desktop application, together with evidence of its actual scope, the requested peer activity and the retained or restored state. A rule in a list is not proof that it applies; a successful connection is not proof that only the intended audience can connect.

Use this workflow on an identified Windows or macOS desktop with an existing installed app and a trusted network already in place. It does not install or launch unknown software, start a new server, change a listener's bind address, configure routers/NAT, open public internet access, alter organization policy, disable security products or create an outbound data-loss control. Container, VM, WSL and third-party firewall layers need their own supported procedures; do not assume a host rule controls them all.

[Web-connection diagnosis](../trace-web-connection-failure/SKILL.md) finds where a request fails. [Local port diagnosis](../diagnose-local-port-conflicts/SKILL.md) identifies the listener and its process. [Native folder sharing](../configure-desktop-folder-sharing/SKILL.md) publishes a folder and grants file access. This workflow owns the separate host firewall change after the app, audience and required traffic are established. It does not infer that a timeout proves a firewall problem.

## Establish the access contract

Resolve only the material facts from the request, current state and trusted app documentation:

- Host computer, OS/version, firewall implementation and whether policy is locally owned or managed
- Exact installed app, actual receiving executable or helper, and existing listener/service identity
- Purpose of incoming access, intended peer devices/network and required application authentication
- Required protocol and local port(s) when the app contract specifies them; relevant address families and interface/profile restrictions
- Existing relevant exceptions, explicit blocks, default policy and protections that must remain unchanged
- A harmless activity from an authorized peer, what content may be sent, and the required evidence level
- Whether the result is a prepared proposal, continuing access or a temporary exception with an explicit removal owner

Do not require port numbers from a user who only knows the app. Read the installed app's relevant settings and current official documentation first. Ask for unresolved audience, app identity or exposure decisions. A marketing app name is not enough to authorize a similarly named executable or every helper installed beside it.

Keep inbound and outbound needs separate. An app that cannot browse a website does not automatically need an inbound exception. Conversely, a local preview opening on the host does not demonstrate incoming peer access. Do not add both directions or both TCP and UDP as a troubleshooting default.

Use the narrowest requested audience the native control can actually express. An IP address restriction identifies an address, not a person or authenticated device. Private-profile selection is not a rule for one named Wi-Fi network. If the desired audience is only one device but the selected interface can allow only the whole app broadly, report the capability mismatch before activation. Do not silently reinterpret “my other laptop only” as “any reachable peer.”

## 1. Inspect the baseline and distinguish the controls

Read relevant settings without changing them. Record the firewall's enabled state, active network context, applicable profiles, relevant app/rule identities, directions, actions and scopes. Retain enough prior values to reverse the specific change without exporting the entire machine's policy or unrelated network details.

Establish that the intended app is already available through its approved lifecycle and that its receiving endpoint belongs to it. A loopback-only listener, absent service or wrong address is a prerequisite problem. Do not broaden the bind address or start another process to make the firewall test possible. Keep the peer's destination, the host's receiving address and any intermediate route distinct.

On Windows, inspect the effective policy as well as any local candidate. Microsoft's [rule reference](https://learn.microsoft.com/en-us/powershell/module/netsecurity/get-netfirewallrule) distinguishes the active policy store from the persistent local store and explains that address, port and application conditions are separate filter objects. If using an already available authorized read-only interface, retain the exact rule identity and associated filters; a display name or a basic rule listing alone is incomplete. Do not pipe an inspection into a modifying command or copy a documentation example that changes policy.

For an ordinary inbound Windows exception, [Microsoft's rule guidance](https://learn.microsoft.com/en-us/windows/security/operating-system-security/network-security/windows-firewall/rules) says explicit conflicting blocks beat allows, full executable paths are required for path-based app rules, and management can prevent local rule merging. An additional narrow allow does not repair an overlapping block. Establish the block's owner and purpose; do not delete it, reorder rules or use a local policy editor to evade management. A managed restriction yields an owner handoff.

Check whether the profile blocks incoming connections even for allowed apps. Microsoft's [Windows Security guide](https://support.microsoft.com/en-us/windows/security/windows-security/firewall-and-network-protection-in-the-windows-security-app) documents that setting and the advanced-settings entry point. Changing a profile-wide protection to enable one app is a broader decision than adding one rule. If it is active, hold the app change and explain the exact conflict rather than clearing it incidentally.

On macOS, inspect Firewall Options, the selected app/service row and relevant automatic allowances. Apple's [settings reference](https://support.apple.com/guide/mac-help/change-firewall-settings-on-mac-mh11783/mac) describes block-all, automatic signed-app allowances and stealth mode. Preserve those global choices. An absent row does not establish a denied app, and a removed row is not automatically an explicit block. Do not toggle stealth mode to make ping work.

If the native firewall is off or another product owns filtering, a saved exception cannot establish protected effective access. Return that prerequisite; enabling the firewall, switching providers or disabling another product is a separate security change with wider consequences. Do not manufacture a clean baseline by resetting defaults.

## 2. Prepare the exact exception before requesting activation

Make a compact before/proposed record. For Windows include the executable/service target, inbound direction, allow action, protocol, local/remote ports, local/remote addresses, applicable profiles and any required interface restriction. For macOS include the exact app/service identity, current and proposed incoming disposition and the app-level scope limitation. Record the specific existing rule being revised or a noncolliding new-rule name; do not identify a removal target only by a friendly duplicate label.

Prefer an app-constrained exception over an all-programs port opening. Microsoft's [risk explanation](https://support.microsoft.com/en-us/windows/security/firewall/risks-of-allowing-apps-through-windows-firewall) distinguishes those choices and recommends removing unneeded exceptions. Where supported and appropriate, combine app and port restrictions rather than making two independent rules that each admit more traffic.

Avoid common scope mistakes:

- The receiving service's port normally belongs in the inbound local-port condition. Do not copy it into the peer's source-port condition without an actual requirement
- The host-side destination address and peer source address are different fields. Do not put the host's address in both
- A trusted subnet is wider than one peer. Do not substitute it for a missing stable peer address
- Dynamic address assignment can change which device occupies an address. Preserve that limitation instead of claiming permanent device identity
- A general interpreter or shared service-host executable can represent several applications. Do not allow it broadly just because it owns this listener
- A rule for one executable path may stop matching after an app update moves the binary. Do not replace it with All programs or a broader runtime exception

If the application uses a shared host, dynamic ports or multiple helpers, obtain the vendor's supported minimum rule definition. Stop at an unsupported service-specific constraint rather than altering service security identifiers, granting every helper or guessing a port range. Preserve authentication and encryption at the application layer; a firewall exception grants reachability, not permission to read private content.

Before applying, obtain the required action-time confirmation for the exact security-sensitive change. State the host, app, incoming traffic, permitted sources/profiles, persistence, what becomes reachable and any interruption risk. A general request to help the app connect does not waive this boundary. If access exposes content, separately resolve the data, recipient and application grant before testing; an allowed address is not permission to disclose all app data.

Keep administrator passwords and protected submissions with the user through the supported secure route. If the change could affect the assistant's remote-control path, arrange a local observation and recovery route first. Without one, deliver the prepared change for local execution rather than risking blind follow-up actions.

## 3. Apply only the supported native scope

Match the installed version to current official documentation. The cited references were inspected on 2026-10-19. Do not translate a Windows rule into a macOS checkbox or use undocumented low-level packet-filter edits to overcome a missing UI feature.

### Windows

Use Windows Security → Firewall & network protection → Advanced settings for the local Windows Firewall with Advanced Security console. Select the exact existing inbound rule when revising one; otherwise use New Rule → Custom. Microsoft's [configuration guide](https://learn.microsoft.com/en-us/windows/security/operating-system-security/network-security/windows-firewall/configure) also covers domain administration, which is outside this local task.

Choose the specific program and, when supported and necessary, its service. Enter the required transport/local port, address scope, allow action and approved profiles in the wizard. Custom exposes the fields needed to combine conditions in a single rule. Give it a clear purpose/name. Finish only after the configured conditions match the approved record; never save a broad rule first with the intent to tighten it afterward. Effective-policy readback remains a separate step after saving.

For a simple app-wide allowance, the ordinary Allowed apps interface may suffice when that is genuinely the approved scope. It is not a substitute for source-address or port restrictions. Do not accept a generic launch-time allow prompt if it cannot express the contract. Resolve the exact generated rule state before any further changes.

### macOS

Use System Settings → Network → Firewall → Options. Apple's [app-access instructions](https://support.apple.com/guide/mac-help/block-connections-to-your-mac-with-a-firewall-mh34041/mac) describe adding the selected app/service and choosing its incoming allowance. Select the actual installed target rather than a download, installer or similarly named copy.

This documented app-level interface does not supply the Windows wizard's source-address/port/profile contract. Proceed only if that app-level allowance is the user's approved scope. If the requirement is a single peer or protocol-specific port restriction, return a prepared limitation handoff; do not promise those restrictions from this row or install another firewall. Leave block-all and automatic allowances unchanged. If they conflict with the requested result, hold for a separate decision.

An app-wide allowance is not a LAN-only control. Account for existing reachable interfaces and address families before promising that outside traffic cannot reach the app; a familiar Wi-Fi name or a private IPv4 address alone cannot establish that boundary. If the required trusted-network-only exposure cannot be established without additional controls, hold this branch. Public internet exposure remains outside this workflow.

### Read back before sending test traffic

Reopen the same native controls. Compare the exact saved target, state and supported conditions against the approved record. On Windows, reconcile the relevant effective policy and overlapping rules; on Mac, retain the global/app-level distinction. Check that no extra rule, broad app entry or profile change was introduced by a prompt or installer.

After an uncertain save or timeout, inspect the actual state before retrying. If the rule already exists, reconcile it rather than creating a duplicate. A reverted or locked rule is a blocker; do not fight policy through a second interface.

## 4. Verify the intended peer activity and preserve the limits

Use the identified authorized peer on the intended network, the known host destination and the agreed harmless activity. State which computer each observation uses. The host's localhost request, a cloud browser and an unrelated internet availability check cannot substitute for the peer.

Keep four results separate:

| Layer | Evidence and limit |
| --- | --- |
| Saved exception | Exact native setting readback; does not establish current applicability |
| Effective boundary | Relevant policy/profile/app scope is consistent with the contract; incomplete overlap visibility leaves exclusivity unproved |
| Transport reachability | A fresh bounded connection to the actual endpoint; does not establish the correct app or authorization |
| Useful activity | Intended peer completes the approved harmless app operation; does not prove every protocol, future network or excluded peer |

Do not send credentials to an unidentified listener. Do not bypass a certificate warning or authentication error to show progress. A cached page, discovery icon or successful ping is insufficient. Prefer existing minimally scoped app/OS evidence to whole-device packet capture or diagnostic uploads.

If the user requires a negative check, agree on one controlled excluded peer/context and a harmless operation beforehand. Treat possible success as real access and use no private content. Failure supports only that observation; it does not prove the firewall caused it or that all excluded peers are blocked. Do not scan other addresses, switch to an untrusted network or disable the firewall for an A/B test.

A narrow new allow can coexist with an older broader allow. If the contract requires exclusive access, inspect the relevant existing routes and grants or mark that requirement unresolved. Do not claim that the newest rule narrows previous rules. Correcting unrelated broad access requires its own scoped decision.

When the check fails, classify what actually failed: host destination, listener, effective firewall policy, transport, TLS, app identity or app authorization. Return to the evidenced boundary. Do not expand sources, enable every profile, add UDP, turn off a firewall or alter router forwarding until something works.

## 5. Retain, remove or restore deliberately

Leave the exception active when continuing access was requested and report its persistence. A date in its description is not automatic expiry. Do not create scheduled cleanup or background monitoring without a separate request.

For temporary access, preserve dependent work, obtain the required action-time confirmation and reverse only the identified change. Disable the newly created Windows rule or restore the recorded prior settings as appropriate; do not disable a pre-existing rule merely because its name resembles this task. On Mac, distinguish restoring the previous disposition from removing a row, and inspect automatic allowances before making any denial claim.

Reopen settings and reconcile the result. Do not restore an old whole-policy snapshot over concurrent changes. Removing the new exception does not prove all existing connections ended, other allow paths disappeared or previously received data was revoked. If immediate session termination or a fresh post-removal check is required, resolve its separate impact and authorization rather than killing the app or disconnecting every peer.

Stop on managed policy, unknown rule ownership, unsupported granularity, missing safe peer access or unavailable protected approval. For unexpected broader exposure, stop further test traffic, report the exact known state and request the scoped containment transition. Do not silently leave a broad fallback active or claim rollback when observation was lost.

## Deliver and accept

Return a short private handoff: host/app identity; changed rule or app row; actual audience/profile/protocol limits; saved and effective state; peer/activity evidence with time; remaining gaps; and precise inspection/removal steps. Keep internal addresses and executable paths out of a broader report unless needed and authorized.

Use accurate outcomes such as **prepared; activation held**, **saved; effective policy unverified**, **peer activity observed; exclusive audience unresolved**, **usable within the checked scope**, or **restored; connection ending unverified**. Completion requires the authorized exposure, preserved unrelated protection, requested activity evidence and intended ending. This is bounded configuration, not a security certification.

## Fictional, unexecuted illustration

A fictional user wants an already running workshop app on a Windows desktop reachable from one established laptop address on the existing Private network. The app's trusted instructions specify one TCP receiving port. The user wants a proposal first; no firewall changes or connection tests are authorized yet.

The paper proposal would bind one inbound allow to the actual receiver executable, the documented local port, the approved peer address and Private profile. It would leave outbound rules and the host's listener unchanged. An invented baseline includes an explicit block for the same receiver. The plan would identify its owner and purpose and hold activation; adding another allow would not resolve the conflict.

In a separate hypothetical continuation, the block's owner authorizes its precise revision through the required action-time decision. A saved rule would still need effective-policy readback and a harmless fresh peer operation. If an older all-sources allow remained, a successful peer connection would not establish the requested one-peer boundary. That exclusivity requirement would remain open rather than being hidden by the successful test.

For the same one-peer request on the documented Mac app-level interface, the proposal would instead identify unsupported granularity and stop before an app-wide allowance. It would not claim feature equivalence or suggest turning the firewall off.

This original illustration is fictional and unexecuted. No computer, application, firewall, rule, network, peer, credential or service was operated for it. The checks describe future authorized work, not observed results.
