---
name: configure-versioned-file-backup
description: "Configure a bounded file-backup job in an existing supported tool, establish its actual capture scope and retained versions, and verify the first capture and requested repetition. Use for working backup setup, not coverage planning, two-way synchronization, disk imaging, restore execution or backup-store cleanup."
---

# Configure a versioned file backup

Deliver a usable backup job for the selected files, with saved source and destination settings, capture evidence, visible omissions and the exact state of any requested schedule. Preserve existing protection while establishing the new job. A current mirror, a local snapshot and a version retained on a separate destination are different results.

Use [backup coverage planning](../plan-file-backup-coverage/SKILL.md) when the sources, recovery needs or storage choice are still undecided. Use [backup restore spot checking](../backup-restore-spot-check/SKILL.md) for separately authorized retrieval into an isolated location. [Folder synchronization](../build-folder-synchronizer/SKILL.md) reconciles independently editable copies; this workflow captures source history without applying destination edits back to the source.

Use an existing supported backup application and an already prepared destination. This guide does not build a backup engine, migrate or repair an archive, image a device, capture a live production database, administer organizational retention or certify recovery after an incident.

## Establish the job and its consequential choices

Identify the actual source computer/account, backup tool and version, selected roots or native collections, destination identity, existing jobs and private handoff location. Establish whether the user wants a one-time capture, a manually reusable job or enabled recurring capture. A request to prepare settings does not authorize starting the job.

Resolve the few choices that change its effects:

- Which file classes and nested locations belong in this job, including future files created within selected roots?
- Which versions and source-deletion history must remain available, and under what accepted retention behavior?
- Which existing destination, account and audience may receive the data, once or repeatedly?
- Which run window, resource limits and disconnected-device behavior are acceptable?
- What first-capture, later-version and optional recovery evidence is required before setup is accepted?

Use an existing coverage plan where available instead of asking again. If the requirement exceeds the chosen tool's actual selection or retention capabilities, explain the mismatch before enabling anything. Do not quietly broaden a single-project backup to the whole user profile, or replace a requested historical backup with folder sync.

Read-only settings and catalog inspection can proceed within authorized access. Copying or uploading needs the selected data and destination approved; recurring sharing needs that same bounded scope and audience. Shared work, sensitive material and a destination already accessible to other people need particular attention. Keep credential stores, private keys, authentication tokens and password-vault contents outside this ordinary-file workflow. If the tool cannot exclude them, hold capture and use an appropriate user-controlled handoff rather than silently transmitting them.

New software, paid storage, network transfers beyond the agreed budget, elevated permissions, security-setting changes and newly created or expanded persistent access are separate gates. Do not embed credentials in commands, configuration exports or the handoff. Use an established authorized access route; hand credential entry and submission to the user when required. On a busy shared or production host, establish an owner-approved resource window before scanning or copying; a read-only source operation can still impose substantial I/O and network load.

## 1. Bind the source and destination before selection

Record enough identity to distinguish the intended drive, mounted share, account and backup set from a same-named replacement. Check the actual destination root and existing backup-set identity, access boundary, available capacity or quota and expected connection. A matching drive letter or mount path alone does not prove the selected device is present. An absent external source must not become an apparently valid empty directory.

Keep the backup destination outside its source population, including aliases, nested mounts and synchronized folders that could copy the backup back into itself. Do not infer failure independence from two folder names or partitions. State whether the destination shares the source's physical device, account or location when that matters to the recovery need.

Inspect existing destination contents without initializing, adopting, repairing or erasing them. Do not point a new job at an unfamiliar archive merely because the application accepts the path. Preserve existing backup jobs, versions and settings; adding coverage does not authorize retiring them.

Determine what selected source entries actually contain:

- Ordinary resident files can be captured through the tool's supported file route
- Cloud placeholders and native online documents need evidenced local payload or an explicitly approved supported export/capture route
- App libraries, packages, linked projects and open data stores need the application's documented consistency requirements; a directory copy does not establish a coherent application state
- Symlinks, shortcuts and mount points need a known follow/exclude policy so selected roots cannot pull in unapproved trees

Keep required source collections independent of the backup's own listing. Record intentional exclusions and unresolved sources separately. An ignored directory, an unreadable directory and a genuinely empty directory must not share one “nothing to back up” conclusion. Preserve required sidecars and linked resources, or report that the capture cannot yet support the intended use.

If saving, closing or pausing an application is needed for consistency, use only the authorized supported procedure and preserve unsaved work. Otherwise hold that source or report the limited file-level capture. Do not stop services or run export hooks merely because a backup template includes them.

## 2. Review selection, retention and activation as one change

Inspect current official guidance for the selected product/version and verify its actual settings. Determine whether setup saves a disabled job, starts a capture immediately, or enables future captures as a side effect. For example, [Apple's Time Machine setup guidance](https://support.apple.com/en-us/104984) says setup starts backups immediately and can present disk-erasure or existing-backup adoption choices. Do not click through those choices as routine setup.

Translate the selected source scope into the tool's real include/exclude rules. Check default libraries, inherited exclusions, recursive filters, hidden files, file-size limits and filesystem boundaries where applicable. Review representative required entries and an already existing excluded entry when useful; counts alone cannot establish the right population. If no safe preview exists, the first write must still be bounded by a sufficiently understood configuration. Hold any unresolved broad inclusion rather than using a real capture to discover what private data it copies.

[Microsoft's File History documentation](https://support.microsoft.com/en-au/windows/experience/backup-recovery/backup-and-restore-with-file-history) describes library-based selection and external-drive or network destinations. Inspect which libraries are actually selected on the target system; do not assume that adding one folder narrows the job to that folder. Product names containing “backup” do not establish identical source or history semantics.

Resolve retention before any operation that can expire history:

1. Identify the exact backup set and all other sets sharing its storage or policy
2. Determine whether retention counts versions, capture-bearing calendar periods, elapsed age, space pressure or a combination
3. Separate removal of a historical catalog/snapshot entry from later reclamation of its stored data
4. Identify whether a new run, destination selection or policy change can immediately remove existing versions
5. Retain the prior settings and use a supported nonmutating preview when available

Never interpret “keep seven daily backups” as a guaranteed seven-day recovery window without checking the product's semantics. [Restic's snapshot-removal documentation](https://restic.readthedocs.io/en/stable/060_forget.html) distinguishes capture-bearing periods, snapshot grouping and removal from pruning, and documents a dry-run preview. Use the actual backup-set filters; changing paths, host labels or tags can change which histories a policy groups together.

Do not prune snapshots, shorten retention, format storage or enable destructive housekeeping under a generic backup-setup request. Obtain the applicable specific approval before any such action. Permanent deletion still requires per-action confirmation; a standing schedule is not a substitute. If the platform cannot separate capture from future irreversible deletion under the available approval rules, leave activation to the user and report the blocked boundary. Apple's same setup guidance documents capacity-driven deletion of older backups; available space alone does not remove that policy consideration.

Save only the approved configuration, preferably inactive until its effects are checked when the tool supports that state. Reopen the saved settings and compare source roots, exclusions, destination identity, retention, run identity, hooks and activation state with the accepted change. Do not export secrets to obtain this record. If unrelated settings changed, hold the job and resolve the exact discrepancy rather than resetting the whole application.

## 3. Establish the first capture from observed results

Recheck selected source availability, destination identity and capacity immediately before starting. Use the supported job entry point under the intended account. Record the configuration version or observation, start/end time, resulting capture identity and any excluded, failed or skipped items. Keep logical source size, transferred bytes and stored size separate; compression, deduplication and reused data can make them differ without proving an omission.

Read the actual outcome, including warnings and item-level failures. A snapshot identifier can coexist with missing files. For example, [Restic's backup documentation](https://restic.readthedocs.io/en/stable/040_backup.html) describes exit status 3 as an incomplete snapshot after source-read failures. Interpret the selected tool's result contract instead of converting any created snapshot into success.

Inspect the exact destination capture through the tool's supported catalog. Reconcile each required source collection with its recorded selection and available membership evidence. Check representative known files and required exceptions, with content or version evidence where the catalog supports it. Preserve unresolved listing or read coverage; a global green badge is not proof that every selected source was included.

Use a stable pre-capture version or coherent snapshot when making a historical byte claim. A file that changed during or after the run is not a valid same-version comparison merely because its name matches. A collection of individually readable files also need not be a single application-consistent state. Keep capture completeness, byte inspection and application usability as separate conclusions.

If the task includes a restore check, use the separately approved alternate destination and the linked restore workflow. Otherwise give the capture/catalog evidence and leave retrieval and usability explicitly unverified. Browsing the history does not prove that every payload can be restored.

## 4. Verify version retention and requested repetition

For a continuing versioned job or requested history check, establish a later captured version without editing the user's real work to manufacture a test. Prefer an ordinary user-authorized change with independently known before/after contents. When an isolated check is appropriate and authorized, use a clearly identified disposable file within the selected source, preserve two distinct known revisions, and record which captures should contain each. Do not delete a real source file to demonstrate retention. For a one-time capture, report that later-version retention was not exercised rather than adding another run.

After the second capture, inspect the earlier and later versions by exact capture identity. Establish that the earlier version remains listed and, where an authorized supported content read is available, contains its earlier contents; establish the later version separately. If only catalog metadata was checked, report version entries observed, not historical bytes verified. Current-source contents and two success timestamps cannot prove that two distinct historical versions were retained.

For a reusable manual job, verify that the same saved job selects the intended source and destination again. Do not call it scheduled. For requested automatic capture, configure the actual supported trigger and read back its account, cadence or timezone, wake/connectivity conditions, overlap behavior and pause control. [Restic's backup documentation](https://restic.readthedocs.io/en/stable/040_backup.html) notes that restic itself has no built-in scheduler; a successful manual invocation does not establish automation.

Observe a trigger-driven run if that is part of the acceptance requirement. A manual “run now” can validate the capture path while leaving the scheduled trigger unobserved. Do not change the system clock, force sleep, unplug active storage or wait indefinitely merely to create evidence. Report configured versus observed execution separately and continue within an agreed observation window when future execution is required.

Check the missed-run behavior through current settings and documentation. If a laptop sleeps or its destination is disconnected, a nominal cadence is not a maximum data-loss guarantee. Do not silently redirect a failed backup into a local directory or a different cloud account. Use an authorized notification route if required; setup does not authorize sending filenames or logs to new recipients.

## 5. Recover without sacrificing existing history

After interruption or an uncertain tool response, inspect active jobs, the exact destination and newly recorded captures before retrying. A timed-out response does not prove that no snapshot was saved. Do not start overlapping copies, remove locks, kill another process or repeatedly rerun a full scan to clear uncertainty.

Handle the actual boundary:

- **Missing source or mount:** Hold the affected capture and preserve history; do not treat missing content as a deliberate empty replacement
- **Unreadable or unstable files:** Retain partial evidence, correct only an authorized cause, and capture again under a new observed result; do not relabel the earlier partial capture complete
- **Wrong destination or unexpected audience:** Stop further transmission through the supported scoped control, report what may already have copied, and seek the specific containment decision; do not erase evidence or improvise permission changes
- **Full storage or quota:** Stop or leave the tool's supported failure state and identify the capacity decision; do not buy storage, delete snapshots or run archive repair as an incidental retry
- **Changed job, source scope or competing run:** Reconcile current settings and ownership before another capture; do not replay stale settings over someone else's changes

When abandoning a newly configured job, use its supported pause/disable control only within the requested authority and verify the resulting state. Preserve its data and any pre-existing jobs. Reversing configuration does not undo copied data, cloud exposure or retention losses. Keep old protection until the user separately authorizes retirement based on the evidence they require.

## Deliver and accept the setup

Return a concise private handoff with:

- Job/tool and source/destination identities, selection and exclusions
- Saved activation, cadence, retention and resource settings, plus any user-controlled setup step
- Exact observed capture identities, requested versus performed history checks, outcome warnings and source coverage limits
- Separate results for catalog membership, historical content, trigger-driven execution and any actual restore
- How to invoke, inspect or pause this job, what requires a coverage review, and unresolved decisions

Read back the handoff and ensure its conclusion matches its evidence. A successful setup requires the intended saved configuration and the requested capture evidence; acceptance of automatic operation also requires the requested trigger evidence. A job prepared but awaiting access or a destructive-policy decision is prepared, not active. A complete first capture with an unobserved future trigger is not a proven recurring backup. No small setup check certifies every file, indefinite retention or disaster recovery.

## Fictional, unexecuted illustration

A fictional illustrator requests nightly versioned capture of one local project folder to an already prepared private backup store. A linked texture library is on an external source drive, while online reference documents are merely placeholders. The proposed job has no deletion or pruning step.

The workflow would verify both source identities, hold the reference documents until a supported capture route is approved, and check that the backup tool's default source selection does not include unrelated libraries. An authorized sample file could provide two distinct revisions for separate captures; its first version would need independent history evidence after the second capture. If the external source drive were absent, the library would remain a coverage failure rather than a valid empty capture. If only manual runs were observed, the handoff would say that the nightly trigger was configured but unobserved.

This is an invented, unexecuted illustration. No application, source file, device, account, backup store, capture, schedule or retention setting was accessed or changed.
