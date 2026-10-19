---
name: repair-windows-application
description: "Repair one malfunctioning Windows application through its supported maintenance interface, preserving required app data and checking the original failed function. Separate packaged-app Repair, vendor installer maintenance, and a separately approved destructive Reset; exclude OS repair and bulk app resets."
---

# Repair an installed Windows application

Deliver a supported repair of the identified installation and evidence about the original failed function, or a precise preservation, authorization or maintenance blocker. A repair completion indicator establishes an operation result; it does not establish recovered user data or a working application.

Use for an ordinary installed Windows app that repeatedly fails to open or perform a function after immediate session recovery is no longer the issue. The distinct task is maintaining the existing installation while accounting for its application state. [Frozen-app recovery](../recover-unresponsive-desktop-app/SKILL.md) handles a blocked live session; [new application installation](../install-desktop-application/SKILL.md) and [application removal](../uninstall-desktop-application/SKILL.md) cover different lifecycle outcomes.

Exclude Windows components, device drivers, security/VPN software, management agents, fleet repair and macOS preference deletion. Do not extend an app repair into Reset this PC, system restore, registry cleaning, all-package re-registration or operating-system component repair. An unsupported app has no generic safe reset recipe.

## Establish the failure and maintenance target

Resolve from the request and available native evidence:

- Computer, Windows release and user account; distinguish local and remote sessions
- Exact product, publisher, version, installation channel and any side-by-side copies
- Original failed function, its minimal safe reproduction, visible error and whether it is observed or reported
- Whether failure affects every input or only one document, account, remote resource or plugin
- App-managed data, unsaved work, unsynced changes and required preferences to retain
- Available supported maintenance choices, expected scope and any suite/shared-component effects
- Authority for repair, app closure and a harmless verification activity; any permitted restart window

Do not turn a clear request into a mandatory questionnaire. Ask only about a consequential unknown. If access is unavailable, prepare a source-verified plan for the actual device and label it unexecuted; repair on a different machine is not a substitute.

Inspect enough to avoid repairing the wrong layer. A single damaged document, expired subscription, denied resource permission or service outage does not by itself establish an installation problem. Use an already available harmless local input where appropriate to separate application launch from remote-resource access. Do not create accounts, change permissions or run active document content merely to establish a baseline.

If a simple supported reopening already restores the requested function, report that bounded result. Do not perform a repair solely because the user suggested it as a possible remedy. Conversely, if the user explicitly wants an applicable repair, establish the maintenance effects rather than demanding proof of a precise corruption mechanism.

## 1. Identify the installed entry and repair surface

Match the native installed entry to publisher, edition, version and user/machine scope where exposed. A shortcut name is insufficient when store and standalone editions coexist. A web-installed app or portable executable may have no native maintenance action. Do not select a suite manager merely because it shares the product's logo.

Microsoft's [Windows repair guidance](https://support.microsoft.com/en-us/windows/apps/repair-apps-and-programs-in-windows) gives these starting points:

- Windows 11: Settings > Apps > Installed apps, the selected entry's menu, then Advanced options when offered
- Windows 10: Settings > Apps > Apps & features, selected entry, then Advanced options when offered
- Traditional programs: Control Panel > Programs > Programs and Features, the exact entry's Repair or Change action

Not every program provides these controls. Change or Modify opens product-specific maintenance; it is not a guarantee that the next operation is repair. Read the actual choices before commitment. Missing Advanced options is a routing observation, not a reason to run a command-line reset.

Use current official product documentation for the selected installation type. Do not apply packaged-app guarantees to a traditional installer. A vendor's repair may replace files, retrieve packages, change shared components or affect an entire suite. Record the scope that the actual dialog and official guidance support; leave unknown effects explicit.

For example, Microsoft's [Office repair guidance](https://support.microsoft.com/en-us/office/lifecycle/repair-an-office-application) says that repairing a suite installation affects the whole suite even when only one member fails. It distinguishes Click-to-Run Quick/Online repair choices from MSI maintenance. A standalone product is a different target. Confirm the installation type and suite impact before selecting a mode; do not infer that “repair Word” permits interrupting every Office application's work.

These official sources were checked on 2026-10-19. Recheck when the interface or supported release differs. Source instructions explain mechanics and do not authorize adjacent troubleshooting actions.

## 2. Preserve the state the chosen operation can affect

Separate program files from user state before closing the app:

- Documents stored outside the application's managed area
- App-local libraries, databases, saved projects, drafts and downloaded content
- Preferences, presets, plugins and sign-in state
- Cloud-visible work versus changes that exist only on this computer

Use existing supported save/export/backup mechanisms for required work and an approved destination. Inspect a representative retained item or the relevant native backup evidence. Do not call a copied live database consistent without the product's supported procedure. A cloud icon does not prove the last local edits were uploaded, and a sync subscription does not establish an independent backup.

If the app cannot open, inspect existing preservation evidence without deleting or renaming its data folders. An inability to export is a reason to hold a destructive action, not evidence that the data is worthless. Avoid collecting full diagnostic bundles, credential stores or unrelated profile directories.

Save reachable work and close the exact affected app normally. A suite operation may require closing several named applications; inspect and preserve their work first. If closure would terminate the only remote access or assistive interface, establish a supported recovery route before proceeding. Do not force-terminate applications merely to clear an installer warning.

Write a small private baseline: selected installation, symptom, required retained data and preservation evidence, maintenance route/mode, and intended acceptance check. No full computer inventory is needed.

## 3. Keep Repair and Reset as separate decisions

Microsoft's [MSIX repair/reset documentation](https://learn.microsoft.com/en-us/windows/msix/desktop/managing-your-msix-reset-and-repair) distinguishes Settings Repair, which retains packaged-app data, from Reset, which removes app data and reinstalls the app fresh, including loss of preferences or sign-in details. This describes the documented packaged-app operation; it is not a universal promise for every vendor button labeled Repair.

Prefer the supported non-destructive repair when it fits the request. A request to repair the named ordinary app can authorize that scoped operation. A request to diagnose does not authorize mutation. Do not require duplicate approval for an already authorized unchanged repair, but resolve newly discovered suite effects, external downloads, data changes or other material scope first.

Reset is optional and never an automatic second click after Repair fails. Before any proposed Reset:

1. Identify the exact app, account/device scope and data the visible warning covers.
2. Establish what required work is independently preserved, what can be recovered through a supported route and what remains uncertain.
3. Explain expected local-state deletion and likely reconfiguration/sign-in work without promising that cloud data will reconstruct everything.
4. Obtain exact action-time confirmation immediately before permanently deleting non-recoverable app data, even if the user previously said to try everything or approved a future reset in general.
5. Recheck target and preservation after approval and before the final destructive control. If the warning reveals broader scope, hold and resolve it.

If required data cannot be preserved or the user declines the loss, finish with Repair unsuccessful/Reset held and the next supported investigation. Do not rename the data directory to simulate a reset, delete caches on speculation or substitute uninstall/reinstall for the held operation. Reinstalling is not a rollback for erased local state.

Other gates remain distinct: user entry of protected credentials through the secure route; specific approval for a new access grant; authorization for a restart or interruption; disclosure and approval of new explicit agreements; and authorization before transmitting diagnostic data. A repair request does not authorize security bypasses, remote support enrollment or account/license changes.

## 4. Perform one supported maintenance operation

Immediately before commitment, verify the exact installed entry, chosen mode, affected suite scope and preservation state. Use the native or already established official maintenance interface. Do not download a third-party repair utility, switch installation channels or run a similarly named installer to work around a missing control.

For packaged apps with the supported Settings control, choose Repair and observe its completion state. Do not press nearby Terminate, Reset or Uninstall controls incidentally. For traditional programs, inspect the maintenance wizard and select only the documented repair option. If it offers feature changes or removal instead, stop before applying them.

If maintenance requests source media, identify the exact required product, release and source. Do not browse to an unrelated package or accept a different edition to make the prompt disappear. Obtaining and executing an additional package requires its appropriate authority and official provenance. If the existing repair cannot proceed without it, report that prerequisite.

Observe the existing operation through completion, failure or a concrete blocker. A tool timeout does not establish that repair stopped. Inspect native state before retrying; never start concurrent maintenance on the same installation. Avoid terminating installer processes or powering off a busy machine. A pending restart leaves verification pending until an authorized restart and readback.

If a separately confirmed Reset is performed, record that operation distinctly and preserve its exact outcome. Do not report it as a data-preserving repair. Handle subsequent onboarding without granting new permissions, accepting a trial or enabling cloud synchronization automatically.

## 5. Verify function and retained state separately

Launch the same intended installation, not a stale shortcut pointing to another copy. Record the actual product/version; if repair changed it, disclose the observed change. Verify the original safe function with the same input/context when possible. A welcome window establishes launch only.

For a local editor, a meaningful check could be opening an approved copy, making a harmless synthetic edit, saving to an absent approved path and reopening that output. Do not overwrite the original to test saving. For a viewer, inspect the expected rendering. For a service client, distinguish reaching its local interface from successful authorized service access. Do not send a message, purchase, upload a private file, run a macro or start an external job merely to test repair.

Check required preserved content and settings against the baseline. Report the inspected subset rather than claiming all user data is intact. Following Reset, distinguish newly created default state, independently restored content and still-missing local state. Do not restore a whole former profile blindly into a fresh app and call that a repair; it can overwrite new work or reintroduce the suspected failure.

If the symptom persists, retain the useful error and stop speculative repair/reset loops. An unchanged symptom can reflect an account, input, add-in or service dependency; it does not justify more destructive maintenance. If data is unexpectedly missing, stop further changes and preserve remaining recovery candidates before proposing any restore.

## Outcome and handoff

Return a concise result with product/version and inspected scope, actual maintenance operation/mode, operation outcome, original-function check, retained-data evidence and any pending restart, sign-in or restoration step.

Use precise states:

- **Prepared only:** supported route and preservation/approval needs established; no repair performed
- **Repair completed, function verified:** operation and relevant safe activity observed; no claim of permanent reliability
- **Repair completed, symptom persists:** distinguish installer success from unresolved user outcome
- **Reset completed:** explicit destructive action and observed post-reset state, with restoration/sign-in limits
- **Pending or blocked:** current operation or missing source, approval, preservation, access or restart prevents completion

Keep logs private and minimized. A support upload, external message, software replacement or system repair is a separate next action. No cleanup of retained exports or recovery material is automatic.

## Fictional illustration — unexecuted

A fictional Windows user asks to repair a note application that opens to an error. Its native entry offers Repair and Reset. The cloud website shows older notes, but the user remembers editing a local-only notebook yesterday.

The planned route binds the installed entry, records the error, and checks available supported preservation without assuming the website contains yesterday's changes. A permitted Repair can proceed through the data-retaining packaged-app route after safe closure. If the same error returns, the operation is reported completed with the function still failing.

The next visible Reset warning says app data will be deleted. The plan holds Reset while the local-only notebook's preservation is unresolved; neither the older cloud copy nor the prior repair request supplies permission to lose it. A later supported recovery/export and exact action-time decision could allow Reset, after which the original function and independently retained notebook would require separate checks.

All names, states and outcomes here are invented. This is an authored decision illustration, not an executed repair, reset, recovery or application test.
