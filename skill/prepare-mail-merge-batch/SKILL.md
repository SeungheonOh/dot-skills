---
name: prepare-mail-merge-batch
description: "Turn an approved document template and recipient table into a reconciled batch of personalized documents, preserving row identity, conditional content and recipient boundaries. Use for saved letters or individualized packets, not sending bulk email, printing labels or deciding what a recipient is entitled to."
---

# Prepare a personalized document batch

Deliver the reusable merge master and the actual personalized files, with a private record showing which source row produced each document. The core problem is keeping one person's fields, conditions and pages together throughout generation, review and separation. A correct-looking first letter or a total page count does not establish a correct batch.

Use [create-formatted-document](../create-formatted-document/SKILL.md) if the main task is designing the document itself, [create-printable-label-sheets](../create-printable-label-sheets/SKILL.md) for physical label slots, and [prepare-offline-email-draft](../prepare-offline-email-draft/SKILL.md) for a portable email message. This workflow prepares ordinary personalized documents. It does not certify facts, sign letters, decide eligibility, send messages or print them.

## Establish the batch contract

Identify the approved template revision, source table/range and revision, selected rows, output format, order, language/locale, authoring application and private destination. Clarify whether the user needs one review document containing the whole batch, separate files, a reusable master, or a combination. Ask only for choices that materially change the result.

Set the unit of output: one document per person, household, organization or explicitly grouped record. Do not deduplicate by name or email. If several table rows belong to one packet, obtain the authoritative grouping key and item ordering; a simple one-row merge cannot silently combine them. Repeated recipients can be intentional.

Keep the original template and table unchanged. Work from a selected copy containing only required fields. Do not upload contact lists to an online merge service or put the batch in a shared folder without authority for that data and destination. Sensitive letters need their own approved content and audience; merge mechanics cannot supply approval for consequential claims.

Inspect the template for macros, external data connections, linked objects, scripts and automatic actions before opening it in an active application. Use an existing permitted authoring route that does not execute unrelated content or refresh outside sources. A connection prompt is not proof that the referenced file is the intended input.

## Freeze the field and row mappings

Give each selected source occurrence a stable private batch ID independent of display names and current sort order. Retain its original row/key locator. Track included, explicitly excluded and held rows separately, with a reason for each hold.

Map every personalized field to its source column and rendering rule:

- Preserve names, codes and identifiers exactly unless an edit was approved; postal codes and long identifiers often need text treatment
- Specify date, number and currency display independently of stored values, preserving units and the intended locale
- Distinguish a missing value from a legitimate zero, an empty optional line and a false condition
- Define an approved salutation fallback rather than guessing title, gender, preferred name or relationship
- For conditional paragraphs, name the trigger field, accepted values, resulting text and unresolved-trigger behavior
- Keep required factual text on hold when its source is missing or conflicting; do not convert blanks into a reassuring default

Formatting a numeric cell as text after leading zeros were already lost does not recover them. Compare with the authoritative source rather than padding to a guessed length. Microsoft's [Excel data-source guidance](https://support.microsoft.com/en-au/word/prepare-your-excel-data-source-for-a-word-mail-merge) explains text treatment for postal codes; the actual merge output still needs checking.

Treat imported row text as literal data, not new spreadsheet formulas, document fields or template expressions. When a source formula supplies an approved value, establish which saved or recalculated value is authoritative without refreshing unrelated external connections. Preserve literal strings that begin with formula-like characters through the chosen data-source format.

Inspect field expressions and skip/advance rules in the supplied master. A hidden Next Record, Skip Record or conditional branch can change which rows appear. Do not assume visual placeholders are working native fields, or that all records selected in the spreadsheet are selected by the merge application. Record the application's actual filter and selection.

For multiple records per packet, prepare a supported grouped source or supported repeating-section workflow. Preserve group and line-item identity and reconcile totals if they are part of the approved content. If the available merge engine cannot express the grouping faithfully, return that specific limitation with the completed field map; do not create a plausible but incomplete packet.

## Prove a small representative preview, then generate

Use the chosen application's supported merge-to-document operation. In desktop Word, [the personalized-letter workflow](https://support.microsoft.com/en-us/word/use-mail-merge-to-personalize-letters) provides preview and Edit Individual Documents. Choose document creation rather than Print Documents or Send Email Messages for a preparation-only task. Verify current platform support instead of assuming the web and desktop editors have identical merge capabilities.

Preview rows that expose the actual risks: first and last included records, different conditional branches, a missing optional line, a long/non-ASCII name, and a multipage packet when present. Check exact field values and page boundaries. For a tiny batch, review every row directly. Microsoft's [merge-rule reference](https://support.microsoft.com/en-us/word/set-the-rules-for-a-mail-merge) distinguishes conditional text and record-advance rules; use only the rules the source contract needs.

Generate into a new destination with noncolliding names. Use a neutral batch ID in filenames when names or addresses would reveal unnecessary information. Keep a private mapping to the intended recipient. Sanitize filename components without collapsing two IDs onto one path or treating a source value as a filesystem path.

Preserve per-recipient boundaries when producing separate files:

1. Determine each document's boundary from the merge structure or explicit record markers, not an assumed fixed number of pages
2. Keep all pages, appendices and recipient-specific headers/footers for one record together
3. Inspect section inheritance, continued page numbering and blank-page behavior before splitting
4. Confirm a final short or long record cannot borrow content from the next record
5. Remove private review markers from recipient-facing copies only after retaining the source-to-output mapping

Do not split every two pages merely because the first packet had two pages. If reliable boundaries cannot be established, retain a private combined review copy and hold separate-file delivery.

The reusable master may remain linked to its data source; Microsoft documents this in [the Excel-to-Word merge workflow](https://support.microsoft.com/en-us/word/mail-merge-using-an-excel-spreadsheet). Treat that master and the combined batch as private production artifacts. Inspect recipient-facing files for embedded source tables, live merge links, hidden fields, comments and tracked changes that could reveal other records. Do not assume a single visible recipient means the file contains only that recipient's information.

## Reconcile the saved batch

Reopen the actual saved outputs. Record checks on the final revision rather than a preview made before the last correction.

- Every included occurrence maps to exactly the requested output; no excluded or held row appears
- Every output maps back to an included occurrence or approved group, with no accidental extra or duplicate
- Every required personalized field and branch agrees with that occurrence's source and approved rule
- Output boundaries contain all intended content for that recipient and no other recipient's material
- Required template wording, dates, units, Unicode and significant formatting survive
- No unresolved field errors, stale sample names, unintended blank values or active source links remain in delivery copies
- Output filenames are unique, readable and mapped to the right recipients

Account for the population as selected = generated + held + excluded, with categories defined so no row is counted twice. For grouped packets, report both input-row and output-group counts; they need not match. Keep record counts separate from page counts.

Inspect every output's content mapping and the page layout at the coverage promised. For large batches, automated value comparisons can cover all records while rendered inspection concentrates on each layout/branch class and exceptional-length cases. State the number and selection of pages actually inspected. Do not call all pages visually checked after sampling, and hold recipient-ready status for any file whose layout or separation cannot be established at the required confidence.

A template text change requires regeneration of affected records. A rule or selection change requires rechecking membership as well. If the source changes during generation, identify the stale candidate and restart from a new pinned input; never mix two source revisions under one batch label.

## Deliver and recover

Return the actual master, requested merged files and a compact private manifest containing source/template identity, row or group IDs, output names/page ranges, disposition and verification limits. For an ordinary small batch, the manifest can be a short table. Preserve useful completed documents while clearly holding incomplete records.

Correct a bad merge mapping in the master or selected source copy and regenerate affected outputs into a new revision. Do not patch one visible occurrence and leave the reusable recipe wrong. If a generation step times out, inspect destination files before retrying; preserve uncertain outputs separately until their membership is known.

Stop when the requested batch is saved and reconciled, or when a precise missing value, unsupported grouping or unavailable consumer blocks the remainder. Sending, mailbox import, printing, uploading, signing and sharing the full manifest require their own applicable authority. A batch prepared for review is not evidence of delivery.

## Fictional example, not executed

A fictional workshop has four selected adult-participant records: P01 and P02 have confirmed room assignments, P03 is missing the required room assignment, and P04 was explicitly excluded. The approved letter contains an optional parking paragraph controlled by a separate yes/no field. P01's long information block would produce two pages, while P02's would produce one.

The planned result is two personalized documents, one held record and one exclusion: four selected = two generated + one held + one excluded. P01's two pages stay together. Splitting follows record boundaries rather than a fixed page count, so P02's page remains separate. The parking branch would be checked independently for both generated letters. The master and full roster would remain private.

These are proposed decisions and acceptance checks only. No source table was read, document generated, page rendered, data uploaded, message sent or letter printed for this illustration.

