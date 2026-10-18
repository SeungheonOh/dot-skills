---
name: configure-desktop-wifi-hotspot
description: "Share an existing approved internet connection from a personal desktop through its native Wi-Fi hotspot, bind the upstream and downstream paths, and verify an intended client and ending. Use for macOS Internet Sharing or Windows Mobile hotspot, not phone tethering, router administration, guest-network isolation, VPN sharing or network repair."
---

# Share a desktop connection with the intended Wi-Fi client

Deliver a usable native desktop hotspot for the agreed devices, with a small connection/stop handoff and evidence that a client actually used it. Keep the host's upstream connection, advertised wireless network, client association, fresh internet use and final sharing state distinct. A broadcast name or connected-device count does not establish internet access through the host.

Use an already configured personal Mac or Windows PC, an existing authorized upstream connection and the operating system's supported Wi-Fi sharing interface. This workflow does not install adapters or software, configure a router, bridge networks, alter firewall/DNS policy, expose a wired LAN, create a NAT64 test network, share a VPN, or evade provider or workplace restrictions. Bluetooth/USB sharing, a phone serving as the hotspot and organization-managed access points have different setup contracts.

[Web-connection diagnosis](../trace-web-connection-failure/SKILL.md) locates an existing request failure. [Desktop folder sharing](../configure-desktop-folder-sharing/SKILL.md) publishes files rather than internet access. [Existing VPN sessions](../connect-existing-vpn-session/SKILL.md) establish an already provisioned tunnel. None makes a desktop hotspot's clients inherit a particular tunnel, proxy or isolation policy.

## Establish the connection contract

Resolve the few inputs that determine whether sharing is appropriate:

- Actual host, OS/version, native sharing capability and available authorized local control
- Existing upstream connection, its owner and permission to share it; any provider restrictions, metering or data budget
- Intended client devices and their owners, supported Wi-Fi/security capabilities and one available authorized observer
- Desired network name, credential responsibility and duration; use an ordinary non-personal name that can be distinguished from nearby networks
- Existing sharing state, connected users and host/client work that a connection change could interrupt
- One harmless public read for acceptance, whether actual path evidence is required, and the requested ending: prepared, active for use or stopped after the check

Ask only for an unresolved consequential choice. Do not needlessly inventory nearby networks or collect device serial numbers. A missing client can permit configuration preparation but prevents claiming a demonstrated client path.

The network owner may differ from the computer owner. Permission to use a workplace, hotel or other third-party connection does not establish permission to redistribute it. Resolve a known restriction with its owner; do not use sharing to bypass device limits, payment, access controls or captive-portal requirements. Provider terms or paid tethering activation are separate boundaries. On a metered upstream, connected clients can generate background traffic as well as the intended read; a small test is not a data cap.

Treat this as access to a network, not a promise of an isolated guest network. If the requirement is that clients cannot reach the host, one another, a private LAN or other sensitive resources, hold this workflow until an appropriate separately established network design meets that requirement. Do not claim isolation from a password, a different subnet or the absence of a visible shared folder. Do not probe private services to test an unapproved exposure.

## 1. Inspect the two sides and preserve a local return path

Read the current native hotspot controls without changing them. Record only the non-secret state needed to preserve existing work: active/off, selected upstream, downstream Wi-Fi interface, network name, exposed security/band options and existing automatic activation/shutdown behavior. Identify an already active share before planning a new one. Replacing its source or credentials can disconnect its current users.

Match the source label to the actual active connection. A dock's Ethernet service, Wi-Fi service, cellular connection and VPN can have similar friendly names. Confirm the intended upstream with its current native status and an agreed harmless host-side read where useful. A host page already in cache does not show current upstream availability. Do not switch adapters, renew leases or change a network profile merely to improve the baseline.

Establish that the installed OS and hardware support the requested source-to-Wi-Fi combination. Use the current official procedure for that version, not an old command-line hosted-network recipe. A radio capable of joining Wi-Fi is not sufficient evidence that every simultaneous sharing topology is available. Preserve a missing or disabled option as a capability/policy gap.

On Mac, keep the upstream and shared-to connection unambiguous. Apple's [Internet Sharing guidance](https://support.apple.com/guide/mac-help/share-internet-connection-mac-network-users-mchlp1540/mac) warns that sharing through the same network port can disrupt the network and other users. Do not work around an unavailable source/output combination by selecting a shared wired segment. Use only the verified supported topology; the ordinary documented example is Ethernet upstream to Wi-Fi clients.

Check dependencies on both devices before a transition: uploads, calls, remote files, remote desktop, assistive access and the assistant's own control route. Have the local user save work and retain a documented way to stop sharing and return to the prior client connection. If the assistant would lose its only observation/control path, let the local user perform the transition and provide the result. Do not install remote access, schedule an unattended rollback or send blind keystrokes after connectivity disappears.

A VPN or proxy active on the host is not evidence that client traffic will inherit it. If protected routing is required or the interaction is unknown, hold activation and resolve that distinct requirement; do not disconnect the VPN or copy its settings to clients as a workaround. Preserve security software, network profiles and management controls.

## 2. Settle access and credentials before broadcasting

State the exact proposed source, host, network name, allowed audience, expected duration, metered-data consequence and possible interruption. Obtain required action-time confirmation immediately before applying a network-security change or creating/materially expanding persistent network access, even when the overall task requested hotspot help. A preparation-only request stops before activation.

Keep password creation, entry, confirmation and submission with the user through the supported secure handoff. Do not generate a password in chat, reveal a saved one, copy it to client fields, or place it in commands, notes or screenshots. A native network-join QR code can carry the credential; do not capture, decode or redistribute it. Have the user make any approved private device-to-device credential handoff. Credential storage and automatic joining need their own applicable authority; do not turn them on simply to speed the check.

Review the security mode that the actual platform exposes and the clients support. Keep the approved protected mode; do not select an open network, remove the password or downgrade security to troubleshoot. If a required security mode is unavailable or cannot be established, report the compatibility gap. A password-holder can potentially share it further; listing intended devices is not a per-person access-control guarantee.

Where the interface supports it, prepare the source/output and private credential settings before turning on the broadcast. If entering configuration itself requires an activation step, first establish what stored configuration will become active and obtain the required confirmation for that real effect. Do not briefly broadcast unknown/open settings and tighten them later. If the initial exposure cannot be bounded, leave the transition to a clearly explained user-controlled local setup or hold it.

Do not accept unexpected firewall, certificate, location, device-enrollment, account or administrator prompts by habit. Obtain the applicable decision or protected user action. A documented feature being locked by policy is a stop point; another control surface is not a route around it.

## 3. Apply the matching native route and read it back

These primary procedures were inspected on 2026-10-18. Match the displayed controls to the installed version; do not guess where a missing option moved. Follow only the host's branch.

### macOS Internet Sharing

Use System Settings → General → Sharing and the Internet Sharing configuration. Bind the existing source connection to Wi-Fi as the downstream port; leave other output ports unselected. Use the version's Wi-Fi options for the agreed network name and protected security choice. Apple documents WPA3 Personal and a WPA2/WPA3 Personal compatibility choice where available. Let the user complete protected credential steps privately.

Apply only the confirmed sharing transition. Do not enable Content Caching, additional sharing services, NAT64 mode or another output interface as convenience additions. The same official page covers a separate NAT64 workflow; it is outside this ordinary connection-sharing task. Leave channel selection at the existing/default supported choice unless the request and actual evidence call for a specific change.

### Windows Mobile hotspot

Use Settings → Network & internet → Mobile hotspot. Microsoft's [native hotspot guide](https://support.microsoft.com/en-us/windows/experience/connectivity-networking/use-your-windows-device-as-a-mobile-hotspot) distinguishes the source connection from “Share over”; select the approved source and Wi-Fi output. Its Properties/Edit controls expose network name, password and band on supported versions. Keep credential entry private and choose only a supported client-compatible band.

Activate the exact configured hotspot after confirmation. Avoid the quick toggle for initial setup: Microsoft states that it starts with default or last-used properties. Do not assume a previously used source and audience remain correct. Do not add Bluetooth pairing or remote-activation behavior, manipulate the legacy adapter Sharing tab, restart networking services or change registry settings under this workflow.

### After either route

Reopen the same controls and read back the selected source, Wi-Fi output, non-secret network identity, visible security/band choices and active state. Check that no additional output or sharing service was enabled. Keep a saved configuration distinct from an active broadcast.

After a timeout or lost tool response, inspect the current state before repeating activation. A delayed response can leave sharing already on. If the native settings revert or become managed, stop and retain that evidence instead of repeatedly toggling. If another person changed them, reconcile the intended delta rather than restoring an old complete network configuration over new work.

## 4. Verify from one intended client

Use the named client through its authorized session, or explicitly attribute a local user's observations. A host-side browser, another cloud computer or an anonymous connected-device count cannot establish that client's result.

1. Match the advertised network to the configured host using its actual name and local setup context. If several networks have the same name, resolve the identity rather than trial-connecting to strangers
2. After the required network-transition decision, have the user join it through the client's native Wi-Fi controls and protected credential step. Preserve the previous connection and saved profiles; do not forget all networks or add a new account
3. Inspect that client's current association and relevant local network details. Where available, compare its selected interface/address/gateway with the hotspot's actual state. Do not hardcode a common private subnet or infer host identity from an address alone
4. Perform the agreed fresh harmless public read in the intended client application. Do not use a cached document, queued message, login challenge or successful host-side read as the internet check. Do not run a speed test, stream media or download a large file on a metered connection
5. Establish the path to the level required. A client may use cellular fallback, another adapter, a VPN or a different effective route while showing Wi-Fi connected. Prefer existing scoped native route/status evidence for the selected destination. Record unresolved alternatives instead of declaring they were excluded

Do not disable cellular, another adapter or a VPN without its applicable confirmation and an interruption-safe plan. If the desired proof requires a controlled single-path comparison that the user cannot safely perform, finish with the actual evidence limitation. An on/off comparison is not mandatory, and a page ceasing to load after an interruption does not explain every earlier request.

Keep the acceptance layers explicit:

| Observation | Supported result |
| --- | --- |
| Reopened host settings match the approved source and output | Configuration is saved with the observed sharing state |
| Intended client is associated with the identified hotspot | Wireless association is observed |
| Client has relevant address/gateway details | Local network configuration is observed; internet access remains separate |
| Fresh approved resource read succeeds on that client | The client used that resource at that time |
| Scoped path evidence accounts for other possible connections | The inspected request/path is attributable to the intended hotspot within that evidence's limits |
| Required check unavailable or only host-side use succeeds | The missing client/path requirement remains unverified |

If the application fails after association, preserve the first evidenced boundary: authentication, address configuration, upstream availability, name resolution, connection or application access. The linked web-connection workflow can help with a bounded failed read. Do not change DNS, disable a firewall, configure a bridge, publish a file share or open router ports to make it work.

One check does not establish all clients, future reliability, throughput, client isolation or protected VPN routing. Leave those stronger claims out. Keep screenshots and notes free of passwords, QR codes, unrelated client identities and private traffic details.

## 5. Leave the requested state and recover narrowly

For continuing use, leave the observed share active only as requested and provide its normal stop control. Explain that the host and upstream must remain available; inspect any visible automatic behavior without promising uptime. Do not change sleep or power policy, enable remote startup or create monitoring as an incidental part of setup.

For a temporary check, save dependent client work, obtain required action-time confirmation for stopping this network-sharing transition, then use only this hotspot's off control. Read back the host state and the client's resulting association as observable. Restore the client's prior connection only within its authorized transition and credential boundaries. A client still reaching a public page through cellular or another network does not prove the hotspot stayed on.

Stopping the broadcast is different from removing saved settings, retiring its password or deleting a client's remembered profile. State what remains. Do not erase credentials or profiles, remove other shares or rotate the password as automatic cleanup. A requested later reactivation needs its actual transition and observation; it cannot be credited from retained settings.

- **Source or sharing entitlement unclear:** hold activation and identify the exact owner/provider prerequisite; do not evade a restriction
- **Wi-Fi output missing or incompatible:** preserve the setup and report the supported-capability gap; do not install drivers, add hardware or try old hosted-network commands
- **Wrong network or unexpected client:** pause new activity and report the observed exposure; use only the authorized exact-host stop/containment transition rather than guessing who a device belongs to
- **Client joins but has no usable internet:** distinguish its local connection from the host upstream and application path; do not grant broader access or repeatedly reset everything
- **Client success uses another path:** hold the hotspot-use claim and resolve evidence or the specifically approved comparison
- **Activation/save/stop uncertain:** inspect the existing state or request local readback before retrying; never infer off from a closed Settings window
- **Recovery would interrupt unrelated users:** preserve their work and obtain the scoped decision instead of restoring a stale before-state

Stop when the requested configuration, client-use/path evidence and ending are established, or when a specific capability, local observation, protected action or new permission blocks progress. Do not repeatedly retry an unchanged failure, contact a provider, upload diagnostics or make the hotspot permanent without the corresponding request.

## Deliver the usable result

Return a compact private handoff: host/OS, actual upstream and Wi-Fi network identity, authorized audience/duration, non-secret settings changed, checked client and resource, evidence source and path limits, final sharing/client state, and the supported start/stop route. Mention metering or availability dependencies that materially affect use. Save a separate record only when useful or requested, and inspect it for accidental credentials before delivery.

Use precise outcomes such as **prepared; activation held**, **configured; client check pending**, **client internet use observed; hotspot path unverified**, **usable within the checked scope**, or **stopped; client return pending**. Acceptance is the requested result with its actual evidence, not a green network icon.

## Fictional, unexecuted illustration

A fictional user wants a personal Windows laptop's existing permitted Ethernet connection shared to one personal tablet over Wi-Fi for a short session, then stopped. The computer has an older stored hotspot configuration and the tablet also has cellular connectivity. No isolation or VPN requirement is present.

The proposed workflow would identify the actual Ethernet source, preserve the old settings, review the intended audience and metered-data implications, and obtain action-time approval before activating the exact configuration. The user would perform any password setup and tablet entry privately. The older quick-toggle defaults would not substitute for inspecting the source and network identity.

In an invented intermediate observation, the tablet displays the hotspot name and opens a public page, but the available evidence does not establish whether cellular carried the read. The handoff would retain that path gap. It would neither disable cellular silently nor announce verified hotspot internet access. A separately authorized safe comparison or adequate existing path evidence could settle that requirement. At the requested end, stopping the hotspot and observing the tablet's return would remain separate checks; retained credentials would not be described as removed.

This original illustration is fictional and unexecuted. No computer, tablet, network, credential, hotspot, browser, traffic, setting or connection was accessed, changed or tested for it. The operational checks describe later authorized work, not live validation results.
