---
name: isolate-browser-profile-failures
description: Diagnose a website that works in one browser profile but fails in another by separating extension, site-setting, storage, and account differences through controlled, reversible comparisons. Use before suggesting a browser reset or clearing data.
---

# Isolate Browser Profile Failures

Find the smallest supported explanation for a profile-specific website failure while preserving the user's sessions, drafts, and security controls. A working private window is a clue, not proof that cookies or extensions are responsible.

## Trigger and scope

Use when the same site or feature appears to work in another profile, private window, or browser, and the user wants to understand the difference. Typical symptoms include a blank app pane, missing controls, blocked sign-in redirect, or a read-only page that never finishes loading.

This is a diagnostic workflow, not permission to reset a profile, migrate accounts, repair authentication, or weaken security. If the failure occurs everywhere, pivot to a site/network investigation and explain why the profile hypothesis is unsupported. Use only the browser and computer access authorized for the task; identify whose browser is being used.

## Required inputs

Obtain from the current UI or ask only for what is missing:

- Target origin, safe reproduction steps, expected result, observed error, and when the problem started
- Affected profile and available comparison contexts, using neutral labels such as A and B
- Browser family, full version/channel, OS/device, and whether the profile/browser is managed
- Website account and workspace/tenant in each context, separately from the browser's own sign-in/sync account
- Network/VPN/proxy state, relevant extensions, site permission overrides, and any known recent change
- Unsaved work, uploads/downloads, active calls, and the safe window for reloads or restarts
- Existing authorization for specific temporary changes and any sign-in needed for a comparison

Never request passwords, session cookies, storage dumps, or full account exports. Verify account equivalence in the UI; record only a masked identifier or a label when sufficient.

## Permission and preservation boundaries

- Reading the relevant UI and settings does not authorize changing them. Obtain permission before disabling an extension, changing a site setting, creating a profile, restarting the browser, or signing in/out in any context.
- State the exact profile, extension/setting, site, old value, proposed temporary value, impact, and restoration plan. A diagnostic request alone does not authorize all these changes.
- Do not disable enterprise-managed, security, identity, password-manager, VPN, or device-management extensions. Do not use a mode that disables them indirectly. Escalate those hypotheses to the responsible administrator.
- Do not relax certificate checks, Safe Browsing, tracking/security protections, or organization policy; bypass browser warnings; or modify experimental flags, proxy, DNS, VPN, or OS settings under this workflow.
- Do not copy cookies/tokens between profiles, export credentials, enable sync, import a profile, install extensions, or sign in as another person. New-context sign-in requires separate authorization and the supported secure login flow.
- Do not clear all browser data, reset/refresh a browser, delete a profile, or remove site storage as an isolation step. Even site-specific deletion can destroy local drafts or sessions and cannot be assumed reversible.
- Preserve drafts through the application's existing safe save mechanism, with authorization if saving would submit/share content. If preservation is uncertain, stop before reloading, navigating away, or restarting. Never submit a real purchase, message, or destructive action merely to test it.
- Use the smallest screenshot region needed. Before sharing, redact account names, unrelated tabs, document content, private URLs/query strings, and other identifiers. Do not attach raw storage, cookies, or unsanitized diagnostic exports.

## Execution workflow

### 1. Establish a safe, repeatable baseline

1. Define a harmless success check, such as “the existing project list appears,” not “a payment completes.” If the failing action has side effects, use an equivalent read-only step or stop before its commit point.
2. Capture A's current state and exact symptom. Check B's claimed working result using the same page and action only when authorized and safe. A public landing page succeeding does not establish that an authenticated feature works.
3. Record a compact comparison matrix before changing anything:

   | Input | A: failing | B: comparison | Matched? |
   | --- | --- | --- | --- |
   | Browser/build/channel, device/OS | | | |
   | Exact page and safe action | | | |
   | Website account, tenant, role | | | |
   | Network/VPN/proxy | | | |
   | Normal/private mode; browser sign-in/sync | | | |
   | Relevant extensions and site access | | | |
   | Site permissions, cookie policy, storage context | | | |
   | Time, result, exact error | | | |

4. Keep browser version, account, URL/action, network, and timing as constant as practical. A different browser or device is a broad comparison, not a profile-only control. Do not update the browser mid-comparison; if it updates, establish a new baseline.
5. Prefer closely paired checks. If A no longer fails or B also fails, record the inconsistency and investigate intermittency or a service change before altering settings.

### 2. Separate account differences before profile changes

- Check the site's active account and selected organization explicitly. A familiar avatar or browser profile name is insufficient.
- Compare the same resource and entitlement when available. Different roles, plans, tenants, feature rollouts, or expired sessions can mimic profile trouble.
- If matched, already-authenticated contexts exist, use them first. Do not create a new login simply to complete the matrix.
- If an account-controlled comparison requires sign-in or switching, explain the needed account/context and ask for authorization. Without it, report the account confound rather than declaring a profile defect.
- If the symptom follows the account across otherwise comparable contexts, report an account-side hypothesis. Do not change roles, subscription, SSO, or account-security configuration.

### 3. Use broad controls honestly

- A private/guest window or new unsynced profile changes several inputs: site state, authentication, extensions, and possibly permissions or policies. Treat success there as “context-dependent,” not “corrupt cookies” or “extension confirmed.”
- In Chrome, Incognito has temporary site data and blocks third-party cookies by default; extensions may be explicitly enabled for Incognito. Inspect effective state instead of assuming no extensions. An additional Incognito window continues the existing Incognito session. Do not close the user's other private windows to force a fresh session. See [Chrome Incognito](https://support.google.com/chrome/answer/95464?hl=en&co=GENIE.Platform%3DDesktop) and [extension controls](https://support.google.com/chrome/answer/2664769?hl=en).
- An approved new local profile can provide a fresh-state comparison without touching A. Do not sign it into browser sync, import settings, or assume it escapes managed policies. [Chrome profiles](https://support.google.com/chrome/answer/2364824?hl=en) keep browser information separate; removing one erases its local profile data, so deletion is not automatic cleanup.
- Firefox Troubleshoot Mode changes extensions, themes, acceleration, and other features. It is not an extension-only test, and its Refresh option is a persistent reset. Do not use it if doing so would disable protected extensions or security controls. See [Mozilla's mode description](https://support.mozilla.org/en-US/kb/diagnose-firefox-issues-using-troubleshoot-mode).
- Consult current official documentation for the actual browser/version before applying product-specific UI steps. Do not project Chrome behavior onto other browsers.

### 4. Choose one evidence-backed branch

Start with the smallest reversible difference that explains the failed feature. Inspect before changing. Use one baseline → changed state → restored baseline cycle per candidate, within any user-supplied observation budget. These are states within the affected profile, not switches between profiles A and B. If no budget was specified, use roughly three candidates or 15 minutes as a progress checkpoint: report the findings and reassess the next useful check. The checkpoint does not end an explicitly requested end-to-end diagnosis. Continue useful authorized checks until the requested result, an agreed limit, or a concrete blocker; do not repeat inconclusive toggles without a new hypothesis.

**Extension branch**

1. Identify a relevant, non-security extension with access to the affected site, such as a cosmetic page reformatter. Record its name/version, enabled state, and site access; exclude protected extensions.
2. Request a temporary toggle of that named extension in A, including the restoration step. Avoid “disable everything” and avoid increasing extension permissions.
3. Preserve work, disable only that approved extension, reload if safe, and repeat the exact check. Restore its original state and retest once if safe.
4. Failure → success → failure with the account/network held steady is evidence of an interaction with that extension in this context. It does not establish the extension as the sole cause or prove a permanent fix.
5. If results are unchanged, restore and move to the next justified candidate within the bound. Do not leave multiple changes active or claim an unchanged result excludes all extension interactions.

**Site-setting branch**

1. Compare only relevant per-site overrides, such as a popup blocked during an expected redirect. Distinguish the explicit override from the inherited default and any managed value.
2. Request an exact, narrow setting change only when appropriate; permission grants or security-sensitive changes retain their separate approval requirements. Do not globally relax settings or use “Reset permissions.”
3. Record the original effective value and whether it was inherited. Apply one approved change, perform the safe check, then restore the precise original state, including removing an exception if none existed.
4. Chrome's [site settings documentation](https://support.google.com/chrome/answer/114662?hl=en) describes per-site controls and automatic saving. A UI that says “temporary” may persist longer than the test; verify actual restoration rather than assuming closure undoes it.

**Site-state/storage branch**

1. Prefer the approved fresh-context comparison and non-secret metadata over deleting data. Compare whether site data exists and whether account/site-setting confounds remain; do not open or copy token values.
2. A fresh context working while A fails can support a profile-state hypothesis only after acknowledging unmatched settings/extensions/account state. It does not identify a corrupt cookie, cache, local database, or service worker by itself.
3. If further isolation requires storage deletion or a repair action, stop this workflow and propose the exact origin, data type, expected logout/draft-loss risk, and separate approval needed. [Chrome cookie guidance](https://support.google.com/chrome/answer/95647?hl=en&co=GENIE.Platform%3DDesktop) warns that deletion can sign users out and remove preferences.
4. Do not promise rollback of deleted storage. The user must decide whether a targeted repair is worth losing local state; a blanket reset is not the next default step.

### 5. Restore and verify

- Restore every authorized temporary extension/setting change immediately after its comparison, even when the hypothesis appears correct. Leaving a workaround active requires explicit authorization.
- Read back the restored control and compare it with the recorded original. If safe, recheck the baseline symptom once. Do not repeatedly recreate an error that risks losing work or locking an account.
- Close only disposable test tabs/windows you created when doing so will not discard work. Do not delete a test profile without separate approval; report that it remains.
- Stop when a useful differential is isolated, the agreed bound is reached, results become inconsistent, or progress requires new authority. “Unresolved with a narrowed hypothesis” is a valid outcome.

## Verification and deliverable

Report observed results separately from inference and proposed repair:

- Symptom, affected context, and matched/unmatched control inputs
- Each authorized test: change, baseline result, changed-state result, restored-state result, and time
- Best-supported explanation and confidence; explicitly list unresolved account, policy, or timing confounds
- Exact restoration status and any test profile or other authorized residual state
- Smallest next action or escalation, with the permission needed and a sanitized screenshot only if useful

Call a fix verified only when an authorized lasting change was made and the original success check passed afterward. A temporary improvement followed by restoration is a diagnosis, not a completed fix. If only instructions were provided, say no tests were executed.

## Failure handling

- **Managed or locked control:** Record its visible policy state; do not work around it. Prepare a short administrator handoff with the reproducible symptom and relevant differential.
- **Login, MFA, CAPTCHA, or warning appears:** Pause at that boundary and follow the applicable authorization/handoff rules. Do not retry authentication repeatedly or bypass the prompt.
- **Restoration fails:** Stop further tests. Report the exact changed control, original/intended value, observed current state, and what prevented restoration. Do not hide an active workaround.
- **Intermittent or multi-variable result:** Mark inconclusive, preserve observations, and propose a better matched comparison rather than escalating to blanket disablement or deletion.
- **Unsaved work or comparison unavailable:** Preserve the current session and deliver the read-only findings plus the one missing input/approval needed to continue.

## Fictional worked example — unexecuted

This invented scenario illustrates the reasoning only. No browser actions or tests were performed for this example.

Request: “The project list at boardroom.example is blank in my Work profile, but it works in Personal. Please find out why without resetting anything.”

1. The proposed baseline checks the same browser build, device, network, project URL, and already-signed-in website account/tenant. Browser sync identities are recorded separately. Drafts would be saved safely before any reload.
2. Inspection would compare relevant settings and find the fictional cosmetic extension “Roomy Layout” active in Work but absent in Personal. Managed security extensions would remain untouched.
3. The assistant would ask: “May I temporarily turn off Roomy Layout in Work, reload this project list, then turn it back on and check once more? This may change page formatting during the test.”
4. If approved, a hypothetical sequence of blank → list visible → blank, with other inputs matched, would support a Roomy Layout/site interaction. These are illustrative outcomes, not observations.
5. The report would say the extension was restored only if read-back verified it. It would propose a narrowly scoped workaround for separate approval, without deleting site data or claiming the issue permanently fixed.
