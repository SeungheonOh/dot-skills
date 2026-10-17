---
name: repair-document-cross-references
description: "Repair internal cross-references in an existing editable document by reconciling intended targets, native anchors, generated labels and displayed results. Use for broken or stale figure, table, heading and page references, preserving live update behavior; not bibliography maintenance, prose editing or PDF bookmarks."
---

# Repair the relationship behind a document reference

Deliver the corrected editable document and the requested reading copy, with live internal references that identify the right content. Typing the current figure number over an error message can hide the defect until the next edit. The repair must preserve the connection from an occurrence to its intended target and the format's supported update mechanism.

Use [maintain-source-linked-citations](../maintain-source-linked-citations/SKILL.md) for references to published works, [document-revision-reconciliation](../document-revision-reconciliation/SKILL.md) for deciding between competing wording, and [add-pdf-navigation](../add-pdf-navigation/SKILL.md) for navigation in an already fixed PDF. This workflow owns native internal reference repair in an established document, not a redesign of its structure or numbering policy.

## Inspect the maintained source and requested scope

Identify the exact source/revision, intended editor and version where material, affected references or whole-document scope, required output formats, and protected features. Determine whether the document contains native reference fields, internal hyperlinks, generated-source labels, manually typed mentions, or a mixture. A visible “Table 4” and an editable DOCX file do not establish that the number is linked.

Prefer the document's established supported editor/processor. If a source-generated document is maintained through labels and a build, repair those maintained inputs and use its existing build route; do not silently patch the generated reading copy. For application-managed fields, use the actual application when native update or navigation is part of acceptance. An XML or text inspection cannot prove that the editor refreshed a field successfully.

Preserve the original or use a recoverable, revision-aware authorized update. Keep comments, tracked changes, section breaks, styles, lists, formulas, notes, links, embedded objects and protection intact unless specifically in scope. Do not accept tracked changes, remove restrictions, change sharing or strip a signature to make the repair easier. For signed or protected material, establish an appropriate editable derivative or return the reference map and precise blocker.

Inspect without running macros, following external links or refreshing unrelated data. A blanket field update can affect dates, linked content, calculations or external resources as well as references. Identify the relevant fields and supported scoped update route first. If opening the source itself would refresh external content and this cannot be safely avoided through a supported route, use passive inspection and hold the native step. Do not upload a private document to a new conversion service.

## Resolve targets independently of their displayed numbers

Build a small target-and-occurrence map where the repair needs it. For each target retain its native anchor or source label, kind, structural location, short identifying caption/heading, current numbering context and evidence for intended identity. For each occurrence retain its location, actual reference mechanism, stored target, display mode, current result and intended target evidence.

Treat these as separate facts:

- The object the author meant: for example, the table comparing storage options
- The target identity the document stores: bookmark, reference mark or source label
- The value requested by this occurrence: label and number, full caption, heading text, page or relative position
- The result currently displayed or cached, and the destination reached when activated

One target can have several references with different display modes. Two targets can share a title or restart numbering in different chapters. A number that looks correct can still link to the wrong object. Use content, source lineage or explicit user direction to resolve intent; do not infer identity solely from a nearby number or the nearest similar caption.

Inspect all in-scope containers the format supports, including tables, notes, headers/footers and text boxes when present. Main-body selection does not by itself establish whole-document coverage. Keep inaccessible regions in the coverage record. Search for manually typed mentions as candidates, but do not automatically convert every numeral or phrase into a reference.

Classify the defect before editing:

| Finding | Supported response |
| --- | --- |
| Correct target and field, stale displayed result | Refresh the relevant supported field/dependencies and verify the result |
| Field codes shown instead of results | Check display state; do not rewrite valid code as prose |
| Missing anchor, intended object still exists | Recreate/rebind through the supported reference mechanism using evidenced object identity |
| Anchor resolves to the wrong or expanded range | Repair the target range or reinsert affected references without disturbing other consumers |
| Target deleted, split or replaced with uncertain intent | Hold the substantive choice; do not point to the next numbered item |
| Native link replaced by plain text | Restore live linkage only where the requested scope and intended target support it |
| Numbering or caption source is wrong | Repair the authorized source of numbering before dependent references; preserve intentional restarts |

Word, for example, uses hidden bookmarks for some cross-references; inserting at a referenced item's boundary can expand what that bookmark covers. Its [cross-reference guidance](https://support.microsoft.com/en-us/word/create-a-cross-reference) describes these field and bookmark relationships. Use the actual target range rather than treating a bookmark name as proof of meaning. LibreOffice's [reference guidance](https://help.libreoffice.org/latest/en-US/text/swriter/guide/references.html) describes its supported targets and reference insertion; do not assume Word identifiers are portable into another editor.

## Repair the smallest connected set

Work on the preserved candidate. For a valid stale field, update it rather than replacing it. For a wrong or missing binding, reinsert or repair through the editor's native operation where supported, preserving the occurrence's display mode, surrounding wording and requested hyperlink behavior. A full-caption reference must not silently become a number-only reference.

Before changing or removing a target anchor, identify every in-scope reference that depends on it. Preserve unaffected external consumers or explicitly mark them unverified if they are outside the accessible document. Reusing a missing anchor name for a different object can make all errors disappear while changing the document's meaning. Do not repurpose identities to silence errors.

If the caption or heading's own numbering is defective, inspect its list/style/sequence and chapter context. Correct the approved source, then recompute dependent labels. Do not force a section to continue numbering when an intentional restart exists, rename every label to match a house style the user did not request, or renumber unrelated equations. An unresolved decision about which target should remain must stay unresolved in the repair record.

Preserve review state. A deleted target under tracked changes may still appear in one review view and disappear in another; establish which document state the requested deliverable represents without accepting or rejecting changes by inference. If the target's existence depends on an undecided edit, hold its affected references or provide a clearly labeled candidate under the user's chosen treatment.

Keep the operation proportional. One known broken figure link needs a focused repair and checks of its dependents, not a whole-document refactor. For a broad repair, account for each in-scope occurrence as preserved, repaired, excluded with reason or unresolved. Do not replace unrecognized field structures with flattened text.

## Recompute dependencies and inspect the saved candidate

Update in dependency order using the actual consumer: target labels/numbering first, dependent text references next, and page references after layout/pagination is current. A contents or figure list can be a related derived consumer when in scope; select the update mode that changes its intended membership as well as page values when necessary. Do not assume a single keyboard shortcut refreshes every document region.

[Microsoft's field-update guidance](https://support.microsoft.com/en-us/word/update-fields) distinguishes an individual update from broader updates and notes additional selection needs for some table fields. Treat those as application-specific operations, not permission to refresh unrelated dynamic content or change a global print setting. If dependent refreshes alter pagination again, repeat the relevant update/check until the requested displayed values agree with the saved layout; investigate oscillation instead of repeating indefinitely.

Save a distinct candidate unless an in-place update was requested. For a shared source, recheck its current revision before writing and use a conditional write where supported. If concurrent changes affect targets or occurrences, reconcile against them rather than overwrite a newer document. A pre-save read alone is not an atomic concurrency guarantee.

Reopen the exact saved file and verify three different properties:

1. **Binding:** Each repaired occurrence points to the intended object/range, with the required live field or source relationship still present
2. **Display:** The actual label, caption, relative position or page value matches the current target and saved layout, including chapter restarts and repeated headings
3. **Use and preservation:** Activating supported internal links reaches the intended content, and protected text, native features and review markup remain intact

Inspect every affected occurrence and target at useful reading size, including surrounding grammar when a label's value changed. Search for localized error messages as one check, but a document with no error strings can still have wrong-target references. Compare unaffected content and the changed structure against the preserved source. Record the actual coverage rather than claiming every field was tested from a sample.

When continued update behavior is required, use an already-requested structural change or a disposable test copy to verify propagation. For example, a permitted insertion before a referenced figure should update its displayed number while retaining the same figure identity. Do not leave a test caption in the delivered file or modify the final prose solely to produce a demonstration. If the native consumer is unavailable, distinguish structurally repaired from update/navigation verified and hold that acceptance claim.

Check each requested export independently. In a PDF reading copy, verify the current visible references and internal navigation the exporter supports; it need not retain editable Word fields. A good native result does not prove that the exported page links or page numbers survived. Do not edit the PDF alone while leaving the maintained source broken.

## Deliver and handle incomplete repairs

Return the corrected maintained source and requested reading copies, a concise list of material repairs, the next supported update action, and exact unresolved locations. Keep a detailed occurrence map only when it helps future maintenance or a pending decision. Describe which references remain live and which application checks actually ran.

Acceptance requires a source-backed intended target for every repaired occurrence, preserved reference semantics, correct saved display, and no unexplained native-feature loss. Where an intended target is ambiguous, the correct result is an explicit hold rather than a plausible relink. A repair with outstanding holds is a partial candidate, not a fully reconciled final document.

If a save or update outcome is uncertain, inspect that candidate before repeating insertions. If a tool flattens fields, changes numbering outside scope or loses review markup, stop using that route and recover from the preserved source into a separate copy. Reconcile newer edits before any replacement. Do not hide a failed native update by manually editing cached display text.

## Fictional, unexecuted example

A fictional equipment handbook has two figures called “Connection layout,” one in chapter 2 and one in appendix B. An occurrence in chapter 3 is intended to refer to the chapter-2 figure, but its field currently points to appendix B. A second occurrence points to the correct chapter-2 target and displays an old page number. A third refers to a deleted figure whose replacement is undecided.

The candidate would rebind the first occurrence using the chapter-2 object's identity, refresh the second after pagination, and hold the third for an author decision. Acceptance would reject a clean-looking number that still opens appendix B, a page value checked only before layout, or a guessed replacement for the deleted figure. Unrelated bibliography citations and tracked changes would remain intact.

No document, field update, navigation action, export or propagation check was executed for this fictional illustration.
