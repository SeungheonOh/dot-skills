---
name: configure-desktop-startup-apps
description: "Choose whether selected existing desktop apps open at sign-in, distinguish login registration from session restoration and background helpers, and verify the intended next-login behavior while retaining manual use. Use for ordinary current-user startup choices, not service administration, security software, startup performance repair or scheduled automation."
---

# Make selected apps open only when intended

Deliver a bounded startup configuration for named installed apps on one macOS or Windows account, together with the observed next-sign-in result or an explicit pending check. Keep the apps installed and usable on demand. An off toggle proves a registration changed; it does not prove that the app will never run, that its background tasks stopped, or that sign-in became faster.

This is a login-behavior workflow. [Installation](../install-desktop-application/SKILL.md) establishes a usable installed copy; [uninstallation](../uninstall-desktop-application/SKILL.md) removes one; [sleep diagnosis](../diagnose-desktop-sleep-prevention/SKILL.md) explains a power-state problem. None replaces identifying which launch mechanism opens an otherwise wanted application at sign-in.

Exclude OS services, drivers, endpoint protection, VPN/security clients, remote-control agents, password managers, essential assistive software and organization-mandated startup components. Do not create scheduled tasks, launch agents, daemons, registry startup entries or elevated launch wrappers. If the desired behavior requires those mechanisms, report the separate administration task instead of forcing it into an ordinary preference change.

## Establish the small contract

Resolve the facts that affect the next action:

- Exact computer, operating system/version and user account, including whether this is a local session or a remote session
- Named app, publisher and installed location when needed to distinguish copies
- Intended behavior: open after this user signs in, or remain closed until explicitly opened
- Whether the user means a visible window, a menu-bar/tray presence, a helper process or unwanted reopening of old documents
- Required functions to preserve, such as manual launch, existing documents and an already configured sync or update function
- Whether the request authorizes configuration, diagnosis only, and a sign-out/sign-in or restart trial
- Work that must remain uninterrupted and a safe way for the owner to return to the same account

Use available settings and evidence before asking. “Stop this app opening every morning” can authorize its ordinary startup preference change once the target is clear. “My computer starts slowly” does not identify which apps may be disabled. Return candidates with consequences rather than deciding that every high-impact item is unnecessary.

Keep the scope to selected ordinary apps and the intended current user. A shared-machine change, another user's profile or an all-user startup entry needs its own authority. Do not switch scope because the current-user control is missing or locked.

If desktop access is unavailable, prepare the version-specific steps and intended checks. Do not report a local change based on a setting viewed on another machine or an instruction sent to the user. Distinguish an owner-reported result from a directly observed one.

## 1. Identify what actually opens the app

Inspect the native login/startup view and, where relevant, the app's own documented launch preference. Record the selected entry's current state and identity before changing it. Use an information/details control or the existing shortcut target when needed; do not execute an unfamiliar item to learn what it is.

Classify the evidence instead of treating all automatic activity alike:

| Observation | Possible mechanism | Discriminating next step |
| --- | --- | --- |
| Named app is enabled in the native startup list | Registered sign-in launch | Match the entry to the intended installed copy and record its state |
| App returns with the same windows after logout/restart | Session restoration may be involved | Check whether it was left running and inspect the applicable reopen setting |
| App appears only after opening a document/link | File/protocol handling or explicit launch | Reproduce the actual trigger; do not change startup settings to fix it |
| A helper appears without the main window | Background component | Establish its owner and purpose; do not infer it is an unwanted foreground launch |
| App is absent from the list but still opens | App preference, shortcut, another launcher or managed registration | Trace the documented owner before changing anything |
| Same-named entries point to different paths | Multiple registrations or installations | Resolve the actual target and preserve unrelated copies |

A process existing after sign-in does not show which mechanism launched it. Conversely, a hidden window does not establish that the app stayed closed. Check the user's requested observable behavior and the relevant native process/app state when available, without sweeping every process into the task.

Do not classify an unfamiliar publisher as malicious or safe from its name. If identity cannot be resolved, leave that entry alone and return the uncertainty. Security investigation is separate from choosing ordinary launch preferences.

## 2. Preserve the session and choose a reversible change

Record a compact before-state: app identity, account scope, controlling setting or shortcut, prior value, intended value and restoration method. Keep unrelated startup entries out of the receipt. Paths and screenshots can reveal account names or private documents; retain only necessary evidence privately and do not upload diagnostic inventories or contact support without approval.

For disabling startup, prefer the existing native toggle or the app's supported preference. Removing a login-list registration should not become deleting the application. For enabling, prefer an existing supported registration for the verified installed app. Do not add a second route merely because the first setting has not yet been exercised.

If two controls represent the same registration, do not treat them as independent changes. If they control different mechanisms, explain which one governs the requested behavior. Change one evidenced mechanism at a time so a later result remains interpretable.

Keep foreground startup separate from background work. A user who does not want a window at login may still rely on synchronization, updates, notifications or a device helper. Do not disable background activity or notification delivery merely to make the desktop look quieter. If an app offers no separate foreground control, identify the trade-off and obtain the user's choice rather than guessing.

Before any logout/restart, preserve unsaved documents, terminal jobs, transfers, recordings, calls and other users' work. Do not rely on automatic reopening as a backup. Establish a permitted reconnection route and someone able to handle sign-in; never sign out of the sole remotely reachable session without an agreed recovery path. Keep password, PIN and authentication entry/submission owner-controlled through the supported secure flow. Do not enable automatic login or weaken lock settings for a convenient test.

## 3. Use the supported current-user route

Read current official guidance for the installed OS version and relevant app. Interface labels can change; use the observed control rather than blindly replaying old coordinates. The source links below support the platform entry points, not every possible troubleshooting action linked from them.

### Windows

[Microsoft's startup guide](https://support.microsoft.com/en-us/windows/experience/startup-boot/configure-startup-applications-in-windows) describes Settings > Apps > Startup and Task Manager > Startup apps for registered applications. Set the selected app's enabled state through one of these views, then read it back. The two views expose the same registered list; changing both is unnecessary.

For an app without a listed registration, the guide also documents a shortcut in the current user's Startup folder, opened with `shell:startup`. Use this only for the named trusted installed app when enabling automatic launch was requested. Inspect its target and any arguments first. Use a shortcut, not a copied executable or installer. Do not use `shell:common startup`, which affects all users, for a current-user task.

Before creating a shortcut, check for an existing equivalent entry and preserve any collision. Do not overwrite another shortcut or carry an unknown command line into an automatic launch. If disabling a shortcut-based launch, remove only the verified startup shortcut through the approved recoverable route, retaining its identity and restoration information. Leave the actual executable and ordinary Start menu/desktop shortcut intact. Do not purge the Recycle Bin.

A broken-path entry is not permission to reinstall the app or edit the registry. Determine whether the installed copy moved, an external location is unavailable or the old app no longer exists; return the exact boundary when no supported ordinary preference fixes it. Startup impact labels do not quantify the time this particular change will save.

### macOS

[Apple's login-items guide](https://support.apple.com/guide/mac-help/open-items-automatically-when-you-log-in-mh15189/mac) describes System Settings > General > Login Items & Extensions. For the intended ordinary app, add or remove its login-list entry using the native control. Check the installed target before adding it; do not select a downloaded installer, a temporary mounted copy or a private document instead of the app.

The same settings area can include background activity controls. Those are distinct from the list of items that open at login. A background component may check for updates or synchronize data. Leave it unchanged unless that separate effect is requested and authorized; an unfamiliar helper is not a reason to disable every item from its publisher.

[Apple's reopening guidance](https://support.apple.com/en-gb/102318) distinguishes login items from reopening windows after logout or restart. Inspect the applicable “Reopen windows when logging back in” choice if the symptom depends on apps left running. A global reopening change can affect other apps, so do not silently use it to satisfy a request about one app. Quitting the selected app normally before an agreed comparison may isolate session restoration without imposing a permanent global preference.

### App-owned preference

Some ordinary apps expose a documented launch-at-login preference. Use it when it is the supported owner of the target behavior, record its exact meaning, and compare the native registration when available. Do not assume “run in background,” “keep running after closing,” “restore last session” and “launch at login” are interchangeable.

An app-specific control may open OS settings or request a helper approval. Inspect that request independently. Do not install a helper, approve new access or accept terms simply because the setting is convenient. If the app re-registers startup after a launch or update, identify that behavior and its documented control instead of repeatedly removing unidentified files.

## 4. Apply the permission boundary without broadening the task

Carry the user's scoped ordinary-setting approval forward; avoid redundant confirmation for navigation and readback. Pause where the effects change:

- Obtain the missing decision for an unapproved all-user change, shared dependency, interruption or global session-restoration preference
- Obtain required action-time approval for new persistent sensitive-data/security-critical access or security settings; ordinary startup enrollment is not authority to grant such access
- Hand credentials and elevation authentication to the owner; do not collect or enter them
- Respect managed/disabled controls. Do not remove policy profiles, alter permissions, edit startup registries or disable security components to bypass a restriction
- Keep installing software, uninstalling apps, changing accounts, deleting application data and changing notification subscriptions separate from startup configuration
- Obtain required confirmation for an unexpected warning or permanent deletion; never empty a recovery location or delete the app's data to clear an entry

Immediately before a change, recheck the account, target and current value. If the user or another process changed it since the baseline, reconcile the new state rather than restoring an outdated assumption. Apply only the selected control and read back its resulting state.

## 5. Verify registration, next login and manual use separately

First reopen or refresh the controlling view. Confirm the intended value for the same app and account, or the exact presence/absence of the selected startup shortcut. This establishes **configured**, not **next-login verified**.

If a transition trial is authorized and safe:

1. Recheck saved work and the recovery path. Preserve the desired final session and avoid interrupting another account's activity.
2. Normally quit the selected app if the comparison must isolate login registration from restoration. Record that condition and any remaining restoration ambiguity. Do not force-quit to improve the evidence.
3. Use the agreed normal sign-out/sign-in or restart route. A lock/unlock or reconnect to an existing session does not exercise a fresh sign-in launch.
4. After the owner signs in to the same account, observe the intended app through a window appropriate to its documented normal startup behavior. Record when the session was ready and whether a delay or login prompt limits the result; do not use a universal few-second timeout to claim absence.
5. Before manually opening it, inspect whether the selected main app started and whether the requested visible behavior occurred. Keep foreground and helper observations separate. Do not count a manual launch by the observer as automatic startup.
6. Check normal manual use when included in acceptance: open the known installed copy, inspect its expected ordinary starting state or an approved harmless document, then quit normally if that is the desired final state. Do not create accounts, upload content or allow a library migration just to prove usability.
7. Read back the controlling setting after manual launch. If it changed again, record the re-registration and keep the intended persistent result unresolved.

For enabling startup, an entry present but no usable app after login is not success. Check whether it points to the wrong copy, depends on an unavailable volume or stops at an unapproved sign-in/permission requirement. Do not weaken protections or add a second startup mechanism to hide that failure.

For disabling startup, absence of a window is insufficient when the request was that the app not run. Conversely, an unrelated background helper is not failure when only opening the main window was in scope. Report exactly the property exercised. If another mechanism still launches the app, retain the successful registration change but mark the overall behavior unresolved.

If a transition cannot be performed now, leave the configuration in the approved state and state the pending next-login check. Do not manufacture a restart deadline or recurring monitor. If the user requested end-to-end verification and an observation is still pending, keep it pending until the agreed opportunity or required owner action resolves it.

## Recovery and stopping

- **Wrong entry or unintended effect:** stop further changes, preserve the observed result and restore only the recorded reversible setting if authorized and still appropriate. Do not overwrite a later user change
- **Needed sync/update/helper stops:** distinguish coincidence from the actual changed control. Restore that control when covered, then verify the needed function through its native status; do not claim restoration from a toggle alone
- **App returns despite disabled registration:** identify whether session restoration, another registration, managed policy or the app itself caused it. Do not bulk-disable services or remove launch files
- **App fails to open automatically:** inspect the exact target and pending first-run requirements; retain a working manual route. Repair installation or move the app only as a separately authorized task
- **Multiple duplicate entries:** resolve each target and owner. Keep an uncertain entry unchanged rather than removing every same-named item
- **Control reverts or is managed:** record the mismatch and responsible owner when known. Stop attempts to override it
- **Logout/restart cannot safely complete:** preserve the configured state and report verification pending. Do not force termination, power off or alter sign-in security

Stop at verified intended behavior for the checked condition, a precise managed/access boundary, or a missing user decision. Do not turn a successful launch preference change into a general boot optimization, malware scan or deletion campaign. One sign-in does not prove future performance or behavior after every software update.

## Return a short configuration receipt

Include the selected app and account scope, prior/final registration state, controlling route, any session-restoration distinction, the observed transition and manual-launch check, and the reversal method. State whether background activity was inspected or left unchanged and identify any unresolved dependency. Minimize device/account details and omit unrelated app inventories.

Use explicit result labels: **prepared**, **configured; next login unverified**, **verified for the checked sign-in**, or **blocked/unresolved**. Never substitute a settings screenshot for a launch observation or promise faster startup without a separately authorized meaningful measurement.

## Fictional, unexecuted illustration

A fictional user wants the invented “Pebble Notes” app to stop opening on a personal Mac but remain available manually. The user permits its login preference change and a later sign-out test, while asking that an existing file-sync app remain untouched.

Invented initial evidence shows Pebble Notes in the login list and still running with an unsaved note. The proposed workflow first preserves that note through the app's normal save route. It records the login entry, removes only that registration, leaves background controls alone and reads back the list. At that point the honest result would be configured with next-login behavior unverified.

For the later authorized trial, the user would quit Pebble Notes normally before sign-out to avoid confusing restoration with registration. After signing into the same account, the observer would check whether the app appeared before manually opening it. A normal manual launch would then confirm continued availability, followed by another login-setting readback.

If the app returned only when left running at logout, the remaining issue would be session restoration. The workflow would explain the global reopening trade-off instead of silently changing every app's behavior. If the user deferred sign-out, the result would remain pending rather than claiming that the issue was fixed.

All names, settings and observations in this illustration are fictional. No computer was accessed, app launched, setting changed, session ended or startup behavior measured for it. The operational acceptance steps describe later authorized work, not completed validation.
