---
name: prepare-offline-work-session
description: "Prepare selected document tasks for a bounded period without reliable internet, with a task-to-file readiness map, authorized offline working copies and a reconnection plan. Use for a usable offline work kit, not whole-account backup, app migration, sync repair or scheduling the user's week."
---

# Make the planned work possible without the connection

Start from what the user wants to do while offline, then prepare the minimum files and supported application behavior needed to do it. Deliver a usable work kit when access and authorization allow, or a precise preparation plan when they do not. A folder full of shortcuts or a list of things to download is not verified offline readiness.

Use [portable-project-handoff](../portable-project-handoff/SKILL.md) for a transfer archive, [plan-tool-switch](../plan-tool-switch/SKILL.md) for changing tools, and [resolve-cloud-file-conflicts](../resolve-cloud-file-conflicts/SKILL.md) if actual conflicting revisions already exist. This workflow keeps the current tools and prepares a bounded reading, writing, annotation or presentation session for the same user.

## Establish the session and permitted preparation

Identify the chosen tasks and intended outputs, the device and installed applications the user will actually use, the expected disconnected period, source file identities/revisions, and allowed local destination. Find whether the request is for a plan only, preparing the selected content, or also checking a supported offline path. Preserve any source-only or no-device-access limit.

Ask only for information that changes usability, such as the target device or whether edits must return to the original shared document. Do not choose an unrelated device or new app because it is available to the assistant. If the target is unavailable, finish source/dependency preparation and state that target-device readiness is unverified.

Use only selected files and necessary authorized dependencies. Do not sweep a mailbox, account, cloud drive or browser cache to make the kit appear complete. Check that storing the selected material on this device is allowed, particularly for shared/work data, and that the output is not an unapproved shared or auto-uploaded folder. Do not copy credentials, session cookies or password stores into the kit.

Preparing selected work does not authorize installing extensions, adding account access, changing security/network settings, signing out, disabling sync or broadening permissions. Mark such prerequisites for the applicable approval or user action. A file's export/download restriction is a boundary, not a problem to bypass by printing, screenshotting or another account.

## Map each task to the capability it needs

Use one row per useful outcome rather than every file in a folder. Record the task, exact source, required action, local working identity or supported app entry point, required dependencies, chosen offline route and readiness evidence. A simple session may need only a handful of rows.

Distinguish the actual capability:

- Reading an existing document can be satisfied by a faithful readable copy when the user accepts that format
- Editing requires an offline-capable editor, retained native structure and a known saved-output location
- Annotating requires saved annotations to survive reopening, not only a visible highlight in a temporary viewer
- Presenting may require embedded media, fonts, notes and an appropriate viewer; a static export has different limits
- Live lookup, collaboration, online refresh, cloud processing, sending or submission can remain connected-only even when the surrounding file is local

Keep a current task's unsupported part visible. A readable workbook with stale external values may support reviewing a dated snapshot but not producing a current result. Do not relabel stale data as current or turn a screenshot into an editable document. Split a task into an honest offline portion and a later connected action only when that preserves the user's purpose.

Trace dependencies that the selected task really uses: attachments, linked files, referenced reading, embedded versus streamed media, font availability, external data and app/license/session requirements. Preserve source identities and versions. A file with the same name on another device is not evidence of the same revision, and a local link can still lead to a cloud-only object.

## Choose the least disruptive supported offline route

Prefer the existing app's scoped offline facility when it meets the required behavior and is authorized. Otherwise use an approved independent export/copy in an already available compatible application. Explain any lost comments, history, formatting, calculations or collaborative meaning before treating the alternative as equivalent. Keep the source unchanged.

Use current official documentation for the actual app, account type, platform and version. [Google's offline Drive guidance](https://support.google.com/drive/answer/2375012?hl=en) distinguishes offline preparation for Google-native documents from ordinary streamed files and documents application/account dependencies. Do not infer a desktop file's offline usability from its name or icon alone, or assume a capability configured on one device applies to another.

Distinguish an ordinary local file, a provider-managed offline copy, an incidental cache, an online-only placeholder and a shortcut. Record the supported access path and any continuing app requirement. Do not manipulate internal caches or sync databases. Avoid broad account mirroring merely to prepare a few selected documents.

Check available storage and the selected download/export size when observable. Unknown size stays unknown; it is not zero. Prepare files individually or in a bounded selected set, inspect completion and keep partial downloads separate. Do not free space by deleting unrelated material. For unavailable dependencies, provide a supported alternative or identify the task that remains blocked.

Choose the write-back contract before editing:

- **Managed offline editing:** changes may synchronize automatically to the original shared object when connectivity returns. Confirm that this effect and audience are within the user's requested authority before using this as a draft/rehearsal location
- **Independent working copy:** retain the original object/revision and local copy identity; later replacement or upload is a separate action unless expressly authorized
- **Read-only snapshot:** preserve its source cutoff and do not imply later updates will appear automatically

If the user wants private drafting for later review, do not put it in a location that will automatically publish edits to collaborators. A separate review copy may meet that intent if its transformation is acceptable; otherwise leave the preparation decision pending.

## Prepare and check the actual kit within scope

Create a new, noncolliding destination or use the specifically authorized offline entries. Preserve source revisions and existing user work. Keep each task's start point obvious: a local file, a supported app item or a clear pending prerequisite. Do not move originals out of a synced folder to make copies.

Reopen the actual prepared artifact through an appropriate safe viewer/editor. Check the content needed for the task, including relevant tables, notes, attachments or media. Do not enable macros, active content or external refresh simply to make a check pass. A structural readback establishes content presence; it does not establish the target application's offline behavior.

When actual offline behavior is in scope, use a supported offline preview or an explicitly authorized isolated check on the intended device. Do not toggle network, VPN or security settings without the necessary authority, and do not interrupt an ongoing call or transfer. Record whether the check truly prevented network dependency or merely displayed an offline preview. Neither a connected successful open nor a preview alone proves every later action will work without connectivity.

For requested editable working copies, make a harmless representative edit in a disposable copy when permitted, save, close/reopen safely and confirm it persisted. Do not test by changing the shared original or adding a comment that later syncs to others. Keep requested working content free of test edits. If the exact app/device cannot be checked, retain that limitation beside the task rather than applying one global “ready” label.

Use meaningful statuses: planned, downloaded/copied, opened on target, supported offline path checked, or blocked. Attach the date, device/app and relevant observation to consequential claims. A task is ready only for the operations actually supported by its inputs and checks; successful reading is not proof of editing, media playback or eventual synchronization.

## Make reconnection preserve the offline work

Include a short return sheet before departure: where offline outputs will be saved, which items are automatically synchronized versus independent, which source revisions they began from, and which online actions remain pending. Do not place an unsent message in an active outbox or queue a submission merely to label it offline preparation.

For independent copies, the planned return process is to preserve the edited copy, inspect the current source revision, and compare changes before any authorized replacement. If the source advanced, keep both and resolve substantive conflicts; do not use “newest timestamp wins.” A PDF export should not silently replace its editable source.

For managed offline edits, document the provider's supported reconciliation behavior and warn that reconnection may propagate changes automatically. Do not promise a manual approval gate the app does not offer. If automatic write-back conflicts with the user's requested review boundary, choose a permitted independent-copy route before work begins.

Record later completion only from actual evidence. A local save is not an upload, a sync indicator is not content readback, and an upload is not a recipient's acceptance. When reconciliation or delivery is later requested, verify the exact target and preserved edits. Do not delete offline copies or clear caches as automatic cleanup after the connection returns.

## Acceptance, failures and delivery

Return the actual prepared kit or its verified local entry points, a compact readiness map, the connected-only remainder and the reconnection sheet. Keep private paths and source content out of a report intended for anyone else. A plan-only request receives a plan without downloads or app changes.

For each selected task, check that its starting material is present at the intended version, its dependencies are either available or explicitly blocked, the required offline operation has the stated evidence, and its output has a known preservation/write-back route. Count selected tasks, not just files, when explaining coverage. A hundred downloaded files do not complete a single task whose required editor is unavailable.

If a download/save has an uncertain result, inspect its exact destination before retrying. If content or native features are lost, keep the source and failed candidate separate and repair only the affected copy within scope. If the source changes during preparation, refresh the affected dependency or disclose the deliberate snapshot cutoff. Never mark an unfinished download, inaccessible target or failed offline check complete because departure is near.

Stop when the requested kit or plan is delivered and the material readiness gaps are clear. Do not continue into new subscriptions, connectivity purchases, live synchronization repair, uploads or file cleanup without their own scope and authority. State prepared, locally checked and target-offline-verified separately.

## Fictional, unexecuted illustration

A fictional user wants to review a report, annotate a PDF and draft changes to a shared spreadsheet during a train journey. They ask for private drafts that will be reviewed before upload. The report and PDF have approved local copies; the spreadsheet's required comments do not survive the available export, and its normal offline mode would automatically sync edits on reconnection.

The readiness map leaves the spreadsheet editing task blocked on a suitable private-copy route rather than dropping the comments or promising a nonexistent approval gate. The report can be prepared for reading, while the PDF still needs a supported save/reopen check for annotations. The return sheet preserves each copy's source revision and leaves upload unapproved.

These invented facts illustrate partial readiness. No files were downloaded, applications used, connections changed, edits synchronized or offline behavior tested for this example.
