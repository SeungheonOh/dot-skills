---
name: configure-personal-screen-time
description: "Configure an adult user's own native Screen Time app-use limits and optional downtime, with explicit device scope, preserved essential access, checked exceptions and a reversible settings handoff. Use for usage budgets, not notification silencing, parental controls or productivity surveillance."
---

# Make a personal app-use limit match the intended boundary

Deliver a narrowly configured personal Screen Time setup, or a complete proposal when settings access or a consequential choice is missing. Make clear what is limited, when, on which devices, and how the user can recover access. A saved duration is not evidence that an app was blocked, that a website was covered in every browser, or that the user spent less time online.

Use [review-notification-delivery](../review-notification-delivery/SKILL.md) for banners, sounds and Focus exceptions, and [plan-personal-workweek](../plan-personal-workweek/SKILL.md) for allocating work. This workflow changes native app-use budgets and access windows for the requesting adult's own account. It excludes child or family-member controls, employer monitoring, content filtering, purchase restrictions, account-role changes, passcode recovery and bypassing someone else's restrictions.

The concrete reference route below is macOS Tahoe 26 Screen Time. Select the installed version in current official help and compare the actual interface before acting. Other releases can rename or reorganize these controls; do not paste an old click sequence into an unfamiliar panel. A different platform needs its own verified native capabilities, not assumed feature parity.

## Establish the limit without judging the user

Resolve the few choices that change the result:

- Selected Mac and local user, OS version, and whether the Screen Time subject is the user themself
- Named apps or website scope, daily allowance, and any weekday/weekend difference
- Whether the user wants a reminder that they can dismiss or the available blocking behavior
- Optional time-of-day downtime, its relevant days, and any overnight boundary
- Essential apps that must remain usable, including tools needed to finish this setup or regain access
- Device-local scope versus an explicitly requested cross-device setup
- Proposal only, a requested configuration change, or an additional agreed behavior observation

Do not interpret “help me focus” as permission to block arbitrary apps, inspect a month of browsing history, lock settings, or impose a schedule. Ask for the smallest missing choice, such as which app and how much daily time. Do not infer addiction, health status or work performance from usage totals. Existing settings and the user's declared goal are enough for an ordinary setup; historical usage analysis is optional and separately scoped.

For “thirty minutes across these apps,” retain the combined-budget intent. For “thirty minutes each,” retain separate allowances. Do not silently translate one into the other because a picker accepts multiple checkboxes. Establish the installed version's grouping semantics from official guidance, visible explanatory text or an authorized observation. If those semantics remain unclear, provide the unresolved group proposal rather than promising a pooled budget.

## Inspect the subject, existing rules and escape path

Open System Settings > Screen Time on the selected Mac. If a family-member selector is present, verify that it points to the requesting user before reading or changing rules. Do not select a child to obtain a missing control. If settings are managed or belong to another person, stop the affected change and describe that boundary.

Read only the relevant state: App & Website Activity, the global App Limits switch, each relevant entry's enabled state and selected members, daily values, block options, Downtime, Always Allowed, Share across devices, and whether settings are locked. A saved entry can exist while its own switch or the global switch is off. Capture safe before-values, including these activation states, in a short change note. Do not record a passcode, Apple Account credential or private website history. Use app names and necessary domain labels rather than screenshots containing unrelated activity.

[Apple's self-setup instructions for macOS 26](https://support.apple.com/guide/mac-help/set-up-screen-time-for-yourself-mchle4e2edfe/26/mac/26) identify App & Website Activity as the setup control and distinguish reporting, cross-device sharing and locking settings. Turning on activity collection should be part of the user's understood setup scope, not an incidental diagnostic step. Leave optional lock and sharing controls unchanged unless explicitly requested.

Before tightening access, establish the visible route back to the affected rule and whether the user can use it. A request for an app budget does not authorize converting an administrator to a standard account. If an account-role prompt appears, cancel that branch and explain the additional consequence. If passcode entry or creation is needed, hand off before entry; the user enters and submits it privately. Do not choose, retain or solicit the code in chat.

Check for overlap rather than treating the new rule in isolation. A named app may already be included in a category, an all-app rule or an exception. An existing active downtime can explain immediate restriction even when a daily allowance remains. Preserve these rules unless the requested outcome actually requires changing them and that scope is authorized.

## Translate the request into the smallest supported configuration

Prepare a short before/after record for each affected entry: subject, selected apps/sites, days and duration, enabled state, block mode, device scope, exception changes, and recovery value. Include the global App Limits activation state separately. Reuse the correct existing entry when revising it; a similar label alone is insufficient to identify its selected members.

### Daily allowances

In the macOS 26 route, use Screen Time > App Limits. Add or edit the intended limit, inspect its actual app/category/site selection, choose Every Day or Custom daily values, and inspect Block at end of limit before saving. A category is broader than its currently familiar app; use named apps when that is the user's scope. [Apple's app-limit instructions](https://support.apple.com/guide/mac-help/mchl630bc02f/26/mac/26) document these controls and the distinct operations for disabling and removing limits.

If App Limits is globally off, inspect which saved entries would become active before enabling it. Activating the global switch can reactivate unrelated saved limits; a request for one new allowance does not automatically authorize that broader effect. Resolve the scope before switching it on, including any separately authorized changes needed to keep unrelated limits inactive. Do not silently disable those entries either. Preserve their prior states and the prior global inactive state for recovery. If the necessary choice is missing, the target may be prepared as an inactive entry or proposal when authorized, but must not be reported as an active limit.

Do not select the whole browser when the request concerns one website. Conversely, an app selection does not establish coverage of the same service's website or another installed client. A URL accepted by the picker does not prove path-level, subdomain or every-browser coverage. Record the exact selected target and leave unsupported granularity explicit. Do not install a blocker extension or change DNS to fill that gap without a separate request.

Daily duration is a use allowance, not a clock-time window. A two-hour limit does not mean “allowed only from 19:00 to 21:00.” Keep uncertain day-reset, travel and overlapping-rule behavior visible when material. Never change the system clock to force a reset or test a schedule.

### Optional downtime

Only configure downtime when requested. It changes access by time of day and can affect more than the selected app budget. For macOS 26, inspect Screen Time > Downtime, choose its schedule, and check the separate blocking option. [Apple's downtime guidance](https://support.apple.com/guide/mac-help/manage-downtime-in-screen-time-mchl69510069/26/mac/26) distinguishes the saved schedule from immediate activation and states that Block at Downtime requires a Screen Time passcode.

For an overnight request, write the intended interval in ordinary language with the start day and following-day end before using the controls. Check the saved day assignments; do not assume a weekday switch means the same overnight boundary the user intended. If the current time lies inside the proposed window, warn about the immediate effect and preserve the recovery route before saving. Do not turn downtime on immediately merely to test a future schedule.

### Exceptions and device scope

Use the existing Always Allowed list to identify conflicts with the requested behavior. Add or remove only specifically authorized app exceptions; preserve communications and contacts controls. [Apple's Always Allowed guidance](https://support.apple.com/en-euro/guide/mac-help/mchl4949e9f4/26/mac/26) describes access during downtime. Do not extrapolate that page into an unverified precedence rule for every app limit. If the target also appears as allowed, resolve the actual interaction before calling the limit effective.

Cross-device reporting and synchronization make a desktop-only request consequential beyond one screen. [Apple's cross-device Screen Time explanation](https://support.apple.com/en-ke/guide/iphone/iphbfa595995/ios) describes shared settings and usage across devices on the same Apple Account. Inspect the actual scope before changing a limit. If sharing is already enabled but the user requested only this Mac, explain the mismatch and obtain the necessary scope decision; do not quietly disable sharing or modify their other devices. An inaccessible second device remains unverified.

## Apply and read back without accidental expansion

A clear request for specified ordinary personal settings can authorize those changes. A review-only request stops at the proposal. New activity collection, device sharing, locking, account-role changes or materially broader app coverage require the corresponding explicit authority; do not bundle them into a routine save.

Immediately before saving, recheck the subject, selected members and existing values. Apply one coherent rule change, then reopen it and inspect every relevant field. For multiple entries, verify each before proceeding so a partial save cannot lead to duplicate budgets. If a save times out or a panel disappears, inspect the current list and entry contents before retrying.

Do not disable all Screen Time to simplify one app's setup. Turning an individual limit off, turning off App Limits globally, and removing an entry have different scope. [Apple's App Limits settings reference](https://support.apple.com/guide/mac-help/change-app-limits-settings-screen-time-mac-mchld1c137dd/26/mac/26) explains the preserved-but-inactive global state. For a temporary change, preserve the entry and its previous values rather than deleting it. Permanent deletion requires the applicable confirmation; do not assume reconstruction of settings is equivalent to normal recovery.

## Verify configuration separately from behavior

For a configuration-only request, acceptance requires readback of the correct subject, exact target set, each relevant daily value, blocking choice, schedule if requested, intended exceptions and device scope. Explicitly read back both the global App Limits switch and the target entry's enabled state; an active configured allowance requires both to be on. Verify that unrelated entries retain their agreed activation states. An intentionally inactive saved entry is configured but inactive, not an active restriction. Report any unavailable or conflicting control precisely. Do not call a reminder-only setup an enforced block.

If a behavior check is requested, agree on a harmless target, time window and restoration before changing a real allowance for a trial. Avoid apps needed for meetings, accessibility, authentication, urgent communication or ongoing work. Do not open private content, spend money, send messages or deliberately consume someone's real entertainment budget merely to create evidence.

Record what was actually seen: app/site and client, date/time and device, relevant reported usage, rule and exception state, and the warning or restriction shown. Inspect whether today's already-recorded use could explain an immediate limit; do not assume a new rule starts a fresh stopwatch. A report total is supporting evidence, not a precise independent measurement of foreground time.

Check the preserved-access case as well as the restricted case when both belong to the request. Successfully opening an essential app does not prove its notifications, calls or every feature work. A successful restriction in one browser does not prove coverage in another. If the natural limit or schedule boundary has not occurred, say that behavior remains unobserved; do not invent a successful timed test from a settings screenshot.

## Recover and deliver

If an unintended restriction appears, first identify whether it comes from the changed entry, downtime, a broader pre-existing rule or a different device's state. Restore only the recorded changes attributable to this work under the agreed recovery authority, including the prior global inactive state and affected entry activation states when these were changed. Recheck for intervening user edits before restoring. Do not erase history, sign out of the Apple Account, reset credentials or remove management controls as troubleshooting shortcuts.

Deliver the actual configured or proposed rule in plain language, its scope, essential exceptions, saved-state evidence, observed behavior and remaining gaps. Include the specific setting to revisit or disable and whether a user-controlled passcode is needed. Do not include credentials or unrelated usage data. Stop at the requested setup and observation; do not add ongoing surveillance, reports to another person or automatic tightening of limits.

## Fictional illustration, not executed

A fictional adult asks for a 25-minute daily limit on one named game on their Mac, with no changes to their phone and no new passcode. Supplied screenshots show that App & Website Activity is already on, Share across devices is off, and there are no existing entries containing that game. The desired setup can use one named-app entry with 25 minutes for each day. The available blocking control still needs inspection; no passcode is created to manufacture an unavailable option.

A second screenshot reveals that the game is in Always Allowed. The proposal now carries that conflict rather than claiming success. The next action is to establish its effect in the installed version and, if removing the exception is necessary, resolve that specific change with the user. The game is not launched to exhaust today's budget, and the phone is not altered.

The deliverable would distinguish a saved rule from an observed restriction and preserve the prior exception state for recovery. These are original invented inputs and proposed decisions. No Mac settings were changed, no app was run and no limit boundary was observed for this illustration.
