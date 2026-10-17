---
name: install-desktop-font-family
description: "Install or activate a selected desktop font family for a named user and application, preserving existing font versions and verifying the requested styles in a saved native sample. Use for local font availability, not font design, character-coverage auditing, document restyling, webfont deployment or font redistribution."
---

# Make the intended font usable in a desktop app

Deliver the selected font faces in the intended local account, a checked sample in the target application, and a small record of what changed. A successful installation dialog is not evidence that the app uses the right family, style or version.

This workflow covers native font installation and activation on macOS or Windows. It does not select a brand typeface, purchase a license, install a font-management service, change system UI fonts or replace fonts throughout existing documents. [audit-font-character-coverage](../audit-font-character-coverage/SKILL.md) examines character mappings; [prepare-print-production-package](../prepare-print-production-package/SKILL.md) handles embedding and production delivery. Neither substitutes for checking the local app's actual font selection.

## Establish the small installation contract

Resolve from the request and available state:

- The computer, OS/version and account in which the font must work; distinguish a local desktop from a remote application's host
- The selected family, supplier/version if specified, requested weights and styles, and supplied font files or official source
- The target desktop application and version, including whether the reported problem instead occurs in a browser-based editor
- Whether the goal is a new installation, activation of an existing copy, or a specifically requested version replacement
- Current-user versus explicitly requested all-user scope, existing font managers, and any managed-device restriction
- A harmless sample of the needed text and an approved local save location; use invented text when content is private

Ask only for a missing choice that changes the action. If the font is already correctly installed, do not reinstall it merely to follow the steps. If only a family name is supplied and several unrelated foundries use it, resolve the intended source before downloading anything. A web editor may have its own supported font catalog or upload service; local installation alone is not a promise of browser-app support.

For plan-only work, return the exact selected files, installation scope and pending checks. Do not label them installed or activate a subscription to make the plan executable.

## 1. Identify the faces, not just the filenames

Preserve the original download and any supplied permission information. For an archive, inspect and extract only the expected font files through a supported safe route; do not run bundled installers, scripts or unrelated utilities. Check the actual container against the platform's current supported types. A renamed extension does not convert a webfont, and converting it is outside this task.

Create one short row for each requested face: source file, family/style names shown by the native viewer, available version or supplier, intended use and current installation state. Collect internal names or file identity only when they help distinguish conflicting copies. Do not require a binary-parser project for an ordinary installation.

OpenType has separate family, subfamily, full-name and version records, with additional typographic grouping names. Consequently, the installed menu name need not be the filename, and an extended family's weights may appear under more than one family entry. Use the actual metadata and consumer menu rather than guessing a missing installation from a label mismatch. [Microsoft's naming-table specification](https://learn.microsoft.com/en-us/typography/opentype/spec/name) explains those distinctions.

Check the requested set explicitly. A file labeled Regular does not supply a separately requested Italic face. A [font collection](https://learn.microsoft.com/en-us/typography/opentype/spec/otff#font-collections) may contain multiple faces; a variable font may expose named instances or controls differently in different consumers. Select the intended static or variable distribution from the authorized package, rather than installing every alternative together. Do not rename internal font records to force coexistence or assume every available weight is required.

## 2. Preserve the existing font environment

Search for the family and relevant styles in the native font manager before changing anything. Record whether each matching copy is installed, active/deactivated where exposed, locally or externally managed, and available to the intended account. Capture its version/location when available. On macOS, [Font Book's preview and information controls](https://support.apple.com/guide/font-book/view-fonts-fntbk1001/mac) show styles and font details, including file location.

Decide the smallest operation:

| Observed state | Next action |
| --- | --- |
| Intended copy already active | Skip installation and check the target app |
| Intended copy present but inactive | Activate only that identified copy when authorized |
| No matching installed copy | Install only the requested files at the approved scope |
| Different version or ambiguous duplicate | Preserve both source identities and hold replacement until the intended winner and recovery path are clear |
| Font managed by another utility or organization | Use its supported owner-managed route; do not fight it with a second installation |

Replacing an existing font may affect other documents that use its names. Before a requested replacement, retain a permitted recovery source for the previous version and preserve any open documents. A screenshot of its name is not a reinstallable copy. If the previous version cannot be recovered and replacement was not explicitly approved with that limitation, stop before removing it.

An explicit request to install a selected font covers that ordinary scoped installation; it does not authorize buying it, accepting a new license, granting a utility persistent access, or removing unrelated fonts. Use trusted official or otherwise approved sources. Obtain any required action-time approval for an unrecognized source. Hand off password entry and submission; never ask for an administrator password in chat. Stop at management restrictions or security warnings instead of disabling protection.

Default to current-user scope when the request is for this person's own app and no broader scope is needed. If the requested action needs elevation or affects other accounts unexpectedly, explain the actual scope before proceeding. Do not change global installation defaults merely for convenience, or treat the ability to read a shared font file as permission to install or redistribute it.

## 3. Install or activate through the native route

Match the controls to the actual OS version. The official pages below are procedural starting points; inspect the current interface and keep the user's existing scope.

### macOS

Use Font Book to add the selected files. Apple's [installation and validation guide](https://support.apple.com/guide/font-book/install-and-validate-fonts-fntbk1000/mac) documents File > Add Fonts to Current User, automatic checks during installation, and a separate file-validation action. Review each warning rather than treating the dialog as a blanket success.

Font Book's duplicate workflow can skip, retain or replace copies; automatic resolution can deactivate or discard copies according to settings. Do not resolve the whole library. Inspect the affected pair and the exact proposed effect, and obtain missing replacement/removal authority before continuing. A failed validation is a stop for that file; preserve the message and seek a supported replacement from the approved source rather than forcing installation. A warning needs its specific cause resolved, not an automatic override. A validation pass does not certify security, licensing or application compatibility.

Check [Font Book's installation settings](https://support.apple.com/en-au/guide/font-book/fntbk1004/mac) for the actual destination. Its user and all-user scopes differ, and a custom library can keep files at their existing location. If that route is already in use, record its dependency instead of later moving the source folder as cleanup. Avoid changing an existing default unless the user requested it.

For an already installed but inactive copy, use the supported [activation control](https://support.apple.com/guide/font-book/remove-deactivate-or-activate-fonts-fntb2bcb512d/mac). Deactivation retains a font for later activation; removal is a different operation. Protected system fonts are outside this workflow.

### Windows

For selected supported desktop files, use the native file installation action. [Microsoft's font-management guide](https://support.microsoft.com/en-us/windows/experience/personalization/manage-fonts-in-windows) documents .ttf/.otf installation, a separate all-users option, and Settings > Personalization > Fonts for discovery and preview. Choose the intended scope deliberately rather than selecting the broader option to overcome an unexplained failure.

If a duplicate/replacement or elevation prompt appears, inspect it against the recorded plan before confirming. Do not manually delete files or registry entries to force a replacement. After the action, locate the family in the native settings and inspect the faces. Microsoft notes that custom-font support varies by app; a successful comparison in another existing app narrows the problem but does not complete the requested target-app task.

### After either route

Read back the resulting family, faces, available version and installation scope. Reconcile each requested face as unchanged-and-already-present, newly installed, activated, held or failed. If an action times out or its result is unclear, inspect this state before retrying; a second install is not a neutral diagnostic.

Do not fetch a random substitute if one face fails. Keep a partial installation explicitly partial and leave the unaffected requested faces usable unless the user prefers reversal.

## 4. Prove use in the named application

Save existing work before a necessary app restart; do not force-quit it or reboot the machine as a first response. Use the app's documented font refresh/reopen behavior when available. Start with a fresh harmless native document so that an old document's retained font name is not mistaken for local availability.

1. Find the family under its actual consumer name, clear a relevant font-list filter if necessary, and select each requested style or supported variable setting.
2. Enter the approved sample, including the characters and punctuation relevant to the task. Inspect the visible result at a useful size and check for missing glyphs, obvious substitution or a style that failed to change.
3. Record the selected face, weight/style controls and any missing-font or substitution warning. A Bold or Italic button being selected does not by itself prove that the intended separately supplied face was used. Use the app's font-information or substitution diagnostics when available; otherwise state the exact-face limit.
4. Save the sample as a new native file, close it safely, reopen that exact file and check the same text/style selections. Preserve the sample and its location in the handoff.
5. If fixing a named existing document is part of the request, inspect a separate copy for changed line breaks, page count, clipping or substituted runs. Do not save a reflowed original without the requested document-editing authority.

Keep three results separate: native installation, target-app selection/rendering, and saved-file reopen. A settings preview establishes only the first local rendering path. A visually plausible sample and matching menu name cannot prove an exact version when competing copies remain unresolved. Likewise, a local sample does not establish recipient availability, embedding rights, PDF fidelity or support in every language. Those require their own requested checks.

If the target app is unavailable, deliver installation evidence and its pending check rather than inventing a successful sample. Do not upload the font or private text to a web editor, font-identification site or converter as a workaround without authorization for that data and destination.

## Recovery and stopping point

Use the narrowest observation that changes the next action:

- **Absent from the native font manager:** Recheck the exact file, account, scope and operation outcome; do not keep repeating the same installation
- **Present natively but absent in the target app:** Check the actual family name, app font-source support and refresh requirements; a comparison app can isolate the boundary
- **Only one face missing:** Check package membership and consumer grouping before reinstalling the whole family
- **Visible but wrong-looking:** Preserve the sample and examine duplicate identity, style selection and substitution evidence; do not delete every similarly named font
- **New instability or unwanted document reflow:** Preserve unsaved work, stop further changes and propose reversal of the exact newly added or replaced copy

Agree to removal or deactivation when it is not already part of the authorized recovery. Before reverting, reidentify the affected copy and confirm that the scope does not include pre-existing fonts or other users. Prefer reversible deactivation where supported and appropriate; if removal is needed, retain the authorized source first. Restore an earlier version only from the preserved matching source, then repeat the native and target-app checks. Report rollback as unverified if either check cannot be performed.

Do not reset the system font library, clear all font caches, delete font registries, install a font manager or remove system fonts as generic cleanup. Stop when the requested faces are usable at the intended scope and the saved consumer sample supports that result, or when a precise missing source, permission, recovery route or application capability prevents completion. Report the latter as blocked or partial, not complete.

Return a compact handoff: installed/activated faces and source version; account/scope; previous-copy treatment; target-app and reopen results; sample location; unresolved warnings; and the exact reversal if relevant. Do not distribute font binaries with the sample unless separately requested and permitted.

## Fictional, unexecuted illustration

A fictional user requests the invented family Harbor Serif version 2, Regular and Italic, for their own desktop publishing app. The supplied authorized package contains both faces. Native font information shows version 1 Regular already active; no Italic is installed. The user asked to add the family but did not approve replacing version 1, which an older open layout still uses.

The proposed plan holds the Regular replacement, records the existing copy and its recovery source, and explains that adding version 2 Italic alone would leave an unapproved mixed-version result. It does not resolve all duplicates or overwrite the open layout. After specific replacement approval and preservation of version 1, the intended check would select both faces in a fresh sample, save and reopen it, then inspect a copy of the old layout if that additional check is requested.

This illustration shows a decision boundary, not a completed installation. No font, font manager, application, account setting, sample document or recovery action was operated for it.
