# Native settings and consumer boundaries

Use this reference for the actual macOS or Windows branch and the requested application's adoption check. Consult the linked current official documentation for the installed version; controls and policy can differ. These notes do not authorize an apply action, credential entry, a diagnostic capture or a network request.

## macOS: bind the change to the network service

Apple's [proxy-settings reference](https://support.apple.com/guide/mac-help/change-proxy-settings-on-mac-mchlp2591/mac) locates the controls at System Settings > Network > the selected network service > Details > Proxies. It distinguishes automatic discovery, an explicit PAC URL, HTTP and HTTPS web-proxy fields, SOCKS, simple-hostname exclusion and a host/domain bypass list. Its bypass-list entries use commas.

Select the actual service in the approved scope. A saved Wi-Fi setting does not establish the Ethernet service's state. For manual web-proxy setup, enter only the supplied per-field host/port assignments; for PAC, use the approved explicit URL control. Follow the actual panel's save/confirmation behavior and reopen the same service. Preserve unrelated modes and services. SOCKS configuration and discovery setup are outside this guide.

Apple exposes a password-required choice for applicable manual proxy fields. If authentication is needed, hand entry and submission to the user through the protected flow; do not reveal an existing value. Do not infer a new credential-saving permission from the presence of that control.

## Windows: keep general and VPN-specific contexts separate

Microsoft's [native proxy instructions](https://support.microsoft.com/en-us/windows/experience/connectivity-networking/use-a-proxy-server-in-windows) distinguish automatic detection, a setup-script URL and manual configuration in Settings > Network & internet > Proxy. An explicit script uses the setup-script control and its Save action. Manual configuration has server/port fields, semicolon-separated exceptions and a separate local/intranet-address choice. The same article documents proxy settings within an individual VPN connection separately.

Use only the approved script or manual branch. Match the requested context before saving; do not apply a VPN-specific instruction to the general panel or alter a VPN to validate this setup. The provider's exact port and exception contract controls the change. Do not adopt a generic support-page recommendation to bypass intranet addresses when the user's accepted route requires those addresses to use the proxy.

Reopen the same saved controls and check the application separately. Do not “synchronize” every Windows network stack. Microsoft's [WinHTTP configuration explanation](https://learn.microsoft.com/en-us/windows/win32/winhttp/setting-wininet-proxy-configurations-in-winhttp) describes application/session/request-level handling of user proxy settings. It does not establish that every program inherits the desktop browser configuration. Changing WinHTTP, service identities or machine-wide settings to fix an unrelated client is outside this workflow.

## Application selection is its own evidence

Mozilla's [Firefox connection settings](https://support.mozilla.org/en-US/kb/connection-settings-firefox) distinguish use of system proxy settings from no proxy, manual settings and an automatic-configuration URL. The same page notes when an extension controls the connection. Inspect the chosen profile's actual mode before attributing its behavior to a native OS change; do not replace its configuration or disable the extension as an incidental test.

For Chrome, the primary [Chromium proxy documentation](https://chromium.googlesource.com/chromium/src/+/HEAD/net/docs/proxy.md) describes several important limits:

- Policies, command-line options, extensions and system settings can supply proxy configuration
- A PAC result can contain multiple candidate proxies; connection failures and retained state can affect which candidate is used
- Failed PAC acquisition can fall back to another configuration or direct access, depending on the actual settings and consumer
- An HTTP proxy can carry an HTTPS destination through CONNECT; the destination's HTTPS scheme alone does not identify the transport security to the proxy
- System-configured bypass rules use the platform's format, rather than assuming the same syntax as browser-specific rules

These are reasons to inspect the actual consumer and request, not instructions to change flags, introduce fallback or collect broad logs. Do not generalize Chrome's acquisition, caching or failure behavior to every browser. A browser-loaded view of the PAC address is not proof that its network stack acquired and used the same configuration. If the necessary effective-route evidence is unavailable, preserve that limitation in the handoff.

## Keep sources and execution separate

The linked documentation supports native control meanings and consumer differences. It is not a report of a configured computer. A later real task must establish its own versions, authority, prior state and observed result. No native setting, application or PAC script was executed while preparing this reference.
