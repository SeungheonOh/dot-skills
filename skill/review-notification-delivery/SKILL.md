---
name: review-notification-delivery
description: "Review missing, duplicated or disruptive desktop notifications across app, browser, OS focus and device-routing settings; prepare or apply a narrowly authorized delivery plan with separate configuration and observed-alert evidence."
---

# Make the intended alerts reach the intended place

Deliver a small notification map for the user's actual work context: which event should interrupt, where it should appear, and what remains available for later review. Then make only the requested changes and distinguish saved settings from observed delivery. A badge, a message in an app, an OS notification and a sound are different outcomes.

Use for cases such as “meeting reminders disappear while I present,” “the desktop and browser both alert for each message,” or “quiet routine chat without hiding direct requests.” [Email filing rules](../configure-email-filing-rules/SKILL.md) change where mail goes; this workflow concerns alert presentation. It does not create forwarding, auto-replies, on-call escalation, a monitoring service or a guarantee that urgent events will arrive.

## Define the smallest delivery contract

Resolve from the request and current evidence:

- Exact device, OS/version, app or website, account/workspace and relevant desktop/browser/mobile variants
- One or two representative event classes: direct messages, mentions, calendar reminders or a named app's routine updates
- Desired destination and presentation: banner, sound, badge, notification history, or no interruption
- Contexts that matter: ordinary work, focus mode, presentation/fullscreen, locked screen or outside working hours
- Any must-retain alerts, accessibility needs, content-preview privacy and existing device-routing expectations
- Diagnosis or proposal only, versus the exact settings changes already authorized

Use a compact row per event/context. “Keep calendar reminders during presentation; silence routine channel banners; keep history” is actionable. “Reduce distractions” leaves important choices open. Ask only for the missing consequential choice, rather than listing every installed application.

Do not infer who is important from private message contents or silently disable a class of safety, security, health or work-critical alerts. A request for less noise does not authorize changing emergency/contact exceptions. Capture only the relevant setting values and event metadata, with redacted previews; avoid exporting notification history or unrelated conversations.

If device access is unavailable, work from supplied screenshots and observations. Label settings not currently visible as unknown. A screenshot taken later cannot establish the active mode when a previous alert was missed.

## 1. Trace one event through its actual route

For a missing or duplicate alert, identify the event and its approximate time, with timezone, without collecting its full private text. Follow the observable stages:

1. **Source event:** Did the exact account receive the message, reminder or update? Distinguish an unsent event from one present inside the app.
2. **App eligibility:** Did that event satisfy the app's notification criteria? Inspect the relevant conversation mute, mention-only rule, reminder setting, quiet-hours schedule or active-device suppression where supported.
3. **Delivery surface:** Is the publisher the desktop app, a browser profile/site, an installed web app, or another device's mirrored alert? A similar icon/title does not prove the same source.
4. **OS presentation:** Inspect permission, banner/history/sound settings and the active focus or do-not-disturb mode, including its relevant exceptions and automatic triggers.
5. **Context and routing:** Was the screen locked, mirrored, shared or fullscreen? Does the app document mobile handoff or suppression while active elsewhere? Record only verified behavior for the actual client/version.

Keep “source event absent,” “app did not request an alert,” “OS presentation suppressed,” and “not observed” distinct. A notification already in history supports different reasoning from an event only visible inside the app. Missing sound alone does not establish missing delivery; inspect the selected output path without changing meeting audio or system volume unnecessarily.

For duplication, match event identity/time and publisher labels. Two alerts can represent two events, a reminder repeat, or the same event from desktop and browser publishers. Do not uninstall an app or sign out an account to test that distinction.

## 2. Compare interacting settings, not just individual toggles

Read current official guidance for the installed product/version. Menu wording changes, and one platform's “priority” may mean display order rather than bypass permission.

- [Microsoft's notification guidance](https://support.microsoft.com/en-us/windows/experience/notifications-and-do-not-disturb-in-windows) distinguishes per-app presentation from do-not-disturb exceptions and automatic triggers, including display duplication and fullscreen use. Review the active condition and exception together; a high position in notification history is not proof of interruption during do-not-disturb.
- [Apple's notification settings](https://support.apple.com/guide/mac-help/notifications-settings-mh40583/mac) separate previews, sound, presentation contexts and app options. Enabling previews is not needed merely to make a banner visible.
- [Apple's Focus guidance](https://support.apple.com/en-nz/guide/mac-help/mchl613dc43f/mac) describes app/person exceptions and synchronization across devices. Check whether a proposed change also affects other devices, automatic activation or shared Focus status. Do not change those as an incidental desktop correction.

For browser alerts, inspect the correct existing profile, site permission and OS publisher. Do not grant notifications to all sites, change unrelated browser permissions, or install an extension to obtain a test facility. For managed settings, retain the policy boundary rather than bypassing it.

Produce only the relevant before/desired map. For each proposed change, include its scope, current value, intended value, expected event classes affected and recovery value. If silencing a publisher would also remove the user's requested alerts, the configuration does not meet the contract. Offer the narrower supported choice or mark the limitation; do not silently widen the mute.

## 3. Apply a minimal authorized change

A request to set a particular notification behavior can authorize that ordinary setting change. A review-only request does not. New website permissions, notification subscriptions, changes to privacy previews or cross-device sharing need the corresponding authority. Ask about the exact missing effect, not a generic “may I proceed?”

Before changing a setting, recheck its account, publisher and current value. Change one meaningful layer at a time and read it back. Preserve unrelated schedules, quiet hours, existing exceptions and notification history. Do not clear history, mark all messages read, unsubscribe, remove calendar reminders or alter mail filing as a shortcut to quieter alerts.

For a temporary focus-mode comparison, agree on the short context, any critical alerts that could be suppressed, and restoration. Avoid testing while the user is in an active call or presentation. Starting a real screen share is a separate action with an audience, not a harmless way to reproduce presentation mode.

If an effect is unclear or the save times out, inspect the actual settings before retrying. Do not create duplicate rules or repeatedly toggle a cross-device control. A failed temporary trial should return to its recorded prior state within the trial's authority; do not overwrite a later user change.

## 4. Verify the contract without manufacturing messages

Keep three levels of evidence separate:

- **Reviewed:** The relevant settings and documented interactions support a proposal
- **Configured:** The intended values were saved and independently read back in the correct account/device
- **Observed:** A specific event produced the expected presentation in the recorded context

Use a built-in local preview when available and safe, but identify which stage it bypasses. An app's test banner may verify OS presentation without testing the real message source, mention rule or push path. Do not contact a colleague, place a call, send a message to the user, create a calendar invitation or generate a security event just to test alerts unless that action is authorized.

When permitted, observe an ordinary relevant event or a specifically approved harmless test event. Record event identity/time, active mode, source app/account, device and observed banner/history/sound result. Use synthetic preview text and a private screen when possible. Verify one must-arrive case and one must-stay-quiet case when both are in the contract. A quiet case is inconclusive if no eligible source event occurred.

For duplicate-route changes, verify the retained route as well as the removed duplicate. Absence of the second banner does not prove the first route still works. Do not claim lock-screen, presentation or mobile behavior from a normal unlocked-desktop observation.

If future observation is requested, use the user's stopping condition and permitted observation window. A configuration-only task finishes with delivery unobserved; it does not automatically become indefinite monitoring. If no suitable event occurs, retain that limitation instead of reporting a successful delivery test.

## Deliver and recover

Return the concise before/final notification map, changes actually applied, verified configuration, event observations and remaining gaps. Identify any unavoidable trade-off, such as an app-wide exception being broader than the requested event type. Keep private message bodies out of the report.

Acceptance means the requested configuration is read back and, where actual delivery was requested, the relevant events are observed in their required contexts. An unknown source event, unavailable second device, managed restriction or unsupported event-level rule remains a concrete gap. Provide the specific next check or decision rather than declaring notifications broken globally.

If the change suppresses an intended alert or exposes previews, restore only the affected recorded values under the applicable authority, read them back and report the result. Changing settings cannot recreate missed alerts or guarantee their later replay; review existing history only within scope. Leave any unauthorized corrective action pending and preserve the evidence.

## Fictional illustration — unexecuted

A fictional user wants Calendar reminders on a Windows laptop while presenting, but routine chat should remain quiet. Supplied observations show a reminder inside Calendar and a notification in history while do-not-disturb is active. The current priority-app list does not include Calendar.

The proposed review would check the exact Calendar publisher, the presentation trigger and documented exception behavior. If authorized, it would add only the required app exception and read it back, leaving chat and preview privacy unchanged. A built-in preview would be labeled presentation-path evidence only; a real reminder in the intended context would still be needed to observe the complete route. No such event or settings change has occurred in this illustration.
