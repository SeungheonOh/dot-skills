---
name: trace-desktop-link-routing
description: "Trace why a link clicked in a desktop app opens the wrong browser, profile, or native app, isolate the routing layer, and verify an authorized narrow correction without resetting defaults or sessions."
---

# Trace Where a Desktop Link Goes

Produce an evidence-backed route from the original click to the observed destination, plus a verified correction or the smallest unresolved handoff. A browser being configured as the system default does not establish which browser a particular source app actually launches.

Use for links that open in the wrong application/profile, unexpectedly stay inside an app, show an external-app prompt, or stop between applications. This workflow ends at application/resource routing. For the correct page failing inside one browser profile, use [isolate-browser-profile-failures](../isolate-browser-profile-failures/SKILL.md); for the intended person lacking document permission, use [shared-link-access-verification](../shared-link-access-verification/SKILL.md). Neither a routing repair nor a different profile grants access to a resource.

## Establish the affected route

Read available UI and settings before asking for missing details:

- Authorized computer, OS/version, source app and desktop/web variant, and the specific action used to open the link
- Actual link target, including its initial scheme, versus the visible label; inspect privately and retain only a redacted route in reports
- Expected browser/app, browser profile, website account/workspace, and final resource, keeping these identities separate
- Observed app/window/profile, final resource or exact prompt/error, and whether the failure occurs for all links or a particular source/scheme/domain
- Relevant system defaults, source-app link preferences, installed intended handler, managed-policy indicators, and any recent change
- Unsaved drafts or active sessions at risk, and whether the user requested diagnosis or an actual preference correction

Do not require a full machine inventory. Missing handler or redirect evidence can remain unknown while the already-visible portion is traced. A screenshot from another computer is reported evidence, not a live check on the authorized device.

## Protect the session and the link

A link can contain a sign-in code, private sharing token, prefilled message, or action that takes effect on opening. Do not publish full private URLs, replay one-time authentication links, click unsubscribe/approval/payment links as tests, or invoke an undocumented custom scheme. Inspect the target and documented purpose first. If reproducing would have consequences outside the request, stop at inspection and obtain the specific permission needed.

Use a harmless existing link with the relevant route when possible. A public HTTPS control can test browser selection but cannot validate a private redirect or native-app handoff. Do not replace a query string or remove a signed parameter and then treat the changed link as equivalent. Avoid clipboard replacement merely to inspect a target; if copying is necessary, preserve irreplaceable clipboard work through an approved local route first.

Keep authentication, security warnings, managed policies, extension permissions, remembered external-app permissions, and account access unchanged. Do not reset all defaults, rewrite registry/handler databases, reinstall applications, disable protections, or sign into a different account to make the symptom disappear. Changing a browser default is not permission to enable sync or move cookies between profiles.

## 1. Record the chain before making changes

Capture the observable hops, not an assumed universal sequence:

```text
source app + action
  → actual initial target/scheme
  → source-app override or embedded browser, if observed
  → operating-system handler, if that path is used
  → launched browser/application + profile
  → observed redirect or external-app handoff
  → website account/workspace + final resource
```

For each hop, record the setting, UI observation, or supported diagnostic that establishes it. Mark unobservable transitions unknown. A final address alone does not prove the intermediate redirects; a familiar avatar does not identify the active website account. Keep browser profile identity separate from the account selected inside the site.

Distinguish these initial cases:

| Observation | Next useful inspection |
| --- | --- |
| One source app opens a different browser | Its own link-open preference, embedded view, or managed setting |
| Ordinary web links from several apps select the wrong browser | Relevant system web-link defaults and any installed routing utility already in use |
| Browser is correct but profile/account is wrong | Actual profile-selection behavior, then website account/workspace; do not reset the OS default |
| HTTPS page opens correctly, then requests a native app | The observed page-to-app handoff and its registered/allowed handler |
| `mailto:` or another scheme fails while HTTPS works | That scheme's handler; HTTPS success does not validate it |
| Correct destination opens with a permission or missing-resource error | Resource/account investigation rather than routing changes |

An installed routing utility is another layer to inspect, not a reason to install one. Record only the relevant rule and its scope; do not export the user's complete routing configuration.

## 2. Compare the smallest safe paths

Use controls that distinguish a particular layer:

1. Reproduce the safe original click once with its source app and intended link. Record the launched process/window and visible profile, then the final result. If the action is unsafe, preserve the original report and label live reproduction unperformed.
2. Open the same harmless URL directly in the intended browser's already-available profile. This checks that destination context, but bypasses source-app and OS dispatch. Success is not proof that default routing works.
3. When useful, activate that URL from another already-available desktop app using its normal link action. Do not send yourself an email/chat merely to construct a test. Record whether this comparison actually uses system dispatch or has its own override.
4. If only one domain or a native handoff differs, compare the observed web stage with the external-app prompt. Do not confirm the prompt, select an “always allow” option, or launch an action-bearing URI without applicable authorization.

Keep the URL, account, network, and device matched where relevant. A different link, browser, or signed-in account changes the conclusion. If repeated safe observations disagree, report intermittency and collect the next distinguishing observation instead of cycling through defaults.

## 3. Inspect the applicable control

Use current official guidance for the actual platform and visible application build. The following are starting points checked on 2026-10-17, not promises that every deployment exposes the same menu:

- **Windows:** Settings → Apps → Default apps supports inspecting associations by file type or link/protocol type. Inspect the types actually in the route; do not infer every association from an application-level badge. See [Microsoft's default-app guidance](https://support.microsoft.com/en-us/windows/apps/change-default-apps-in-windows).
- **macOS:** In Ventura 13 or later, the default web-browser control is under System Settings → Desktop & Dock. Default email handling is separate. Do not add a mail account just to investigate a web-link problem. See [Apple's default browser and email guidance](https://support.apple.com/en-us/102362). Apple also notes that [some apps open pages outside the default browser](https://support.apple.com/en-gb/guide/safari/ibrwa008/mac).
- **Outlook/Teams on Windows:** Microsoft's documented web-link preference is independent of the Windows default and can affect both apps. New Outlook exposes it under Settings → General → Files and links; classic Outlook uses File → Options → Advanced → File and browser preferences. Inspect the actual setting and managed state before acting. Disclose the coupled Outlook/Teams scope before a change; permission limited to one app may be insufficient. This documented behavior is not a macOS rule. See [Microsoft's link-opening explanation](https://support.microsoft.com/en-us/outlook/web-links-from-outlook-emails-and-teams-chats-open-in-microsoft-edge).

For another platform, source app, or custom protocol, consult that vendor's current documentation rather than improvising a handler-registration command. If the relevant control is unavailable or policy-managed, capture that fact and prepare an administrator handoff.

## 4. Correct only the supported layer, then verify

If a correction is within the user's request, record the exact control, old value, new value, and affected scope. If the request was diagnosis only, or the change would affect additional apps/accounts, ask for that specific change. Apply one supported ordinary preference change at a time. Authentication, security permissions, software installation, and managed-policy changes retain their own boundaries.

Repeat the original safe source-app click. Check all parts of the requested outcome: launched app, profile when relevant, website account/workspace, and resource. A setting readback is necessary but not a functional retest. Check an unchanged control route when it is useful to detect a broader effect; do not claim untested protocols or apps were verified.

Restore failed temporary changes before trying another hypothesis, using the recorded original value. For an authorized lasting fix, leave the requested value and report it. If restoration fails, stop further modifications and state the current value and blocker. Close only disposable test windows you created when no work would be lost.

Finish when the requested route is verified, a useful routing differential is established for a diagnosis-only request, or the next discriminating step needs unavailable access or permission. Do not repeatedly launch the same failing handler or substitute a global reset for missing evidence.

## Deliverable

Return a concise route report with:

- Original symptom and intended destination
- Observed chain, evidence for each hop, and unknown transitions
- Paired checks and what each establishes or leaves unresolved
- Supported explanation, distinct from a suspected cause
- Exact changed/restored values and final state
- Verified outcome, or the smallest next action with its required permission/access

Say “routing corrected” only after the original path passes. If only settings were inspected, say so. A manual open in the intended browser can be reported as a workaround, not as repair of the original click path.

## Fictional worked example — unexecuted

This invented scenario illustrates the workflow. No desktop, browser, settings, or links were operated for this example.

Request: “Links from my Windows Outlook app open in Edge, although I use Firefox. Find the cause before changing anything.”

An illustrative evidence packet says a harmless public link opens in Edge from Outlook, opens in Firefox from a second app confirmed to use system dispatch, and opens normally when entered directly in Firefox. The Windows web associations name Firefox; the visible Outlook link preference names Edge.

The hypothetical conclusion is a source-app preference differential, not a broken Windows default or a website-permission failure. The report would identify that preference as the supported routing explanation and note Microsoft's documented Outlook/Teams coupling. It would request approval for that scoped coupled change if the user wants a fix. No change or successful retest would be claimed from this fictional evidence.
