---
name: build-stock-count-workbook
description: "Prepare physical inventory count sheets and a review workbook that reconciles returned counts to a dated stock snapshot, with units, movement cutoffs, recounts and unresolved variances. Use for a count packet, not perpetual inventory, packing lists or posting stock adjustments."
---

# Build a Physical Stock Count Packet

Deliver a usable counting artifact and, when observations are supplied, a traceable reconciliation workbook. Separate the system's expected stock from what someone actually reports counting. A prepared sheet is not a completed physical count, and a calculated variance is not an authorized stock adjustment.

Use [box-inventory-handoff](../box-inventory-handoff/SKILL.md) for household packing and item-to-container tracking. Use [spreadsheet-cleanup-reconciliation](../spreadsheet-cleanup-reconciliation/SKILL.md) to repair an export. This workflow covers the distinct count cycle: define a population, issue nonoverlapping count sheets, preserve observations, align their time basis, and review differences.

## Establish the count scope

Inspect the supplied item/location export, current count instructions and any returned sheets. Identify:

- Selected site, storage locations and item population, including exclusions and expected-zero items when in scope
- Snapshot identity and effective timestamp, with timezone; export time alone may differ from the stock's as-of time
- Item/variant, location/bin, lot/serial and stock-status dimensions required to distinguish stock pools
- Quantity units, pack conversions and whether fractional counts are legitimate for each item
- Count window, blind-versus-visible expected quantities, known movement-freeze procedure or movement records, and any supplied recount threshold
- Requested workbook/file format, permitted audiences and destination; whether this pass prepares blank sheets or reconciles actual returns

Ask only for missing decisions that change identity, quantity or comparability. Do not invent pack sizes, cutoff times, responsibility, loss causes or recount approval. A filtered export proves only that selected population; it does not prove every physical location or unexpected item was covered.

Use authorized read-only exports or supplied files. Do not freeze stock, change warehouse settings, contact counters, assign people to live work, post inventory transactions or modify accounting records merely because the workbook is ready. Saving or sending to others requires the requested destination and audience. Keep prices, supplier details, staff personal data and other unnecessary information out of count sheets.

## 1. Preserve a precise expected-stock baseline

Keep the selected source unchanged and record its revision/digest, filters, as-of time and relevant extraction limitations. Define the count key from the actual stock dimensions. An item in two bins or two lots is not one interchangeable row merely because its description matches.

Check repeated full keys before aggregation. Multiple source rows may be legitimate components, duplicate export occurrences or conflicting snapshots. Combine only under an evidenced grain rule and retain each source contribution. Hold ambiguous pools instead of letting a dictionary overwrite them.

Preserve text identifiers, including leading zeros. Keep source quantities, units and documented conversion factors separate. Convert packs to base units only when the factor and direction are established; `2 boxes` is not `2 units`. Do not sum unlike units or assume an undocumented serial item permits fractional quantities. Keep unknown quantities unknown.

Treat reserved, damaged, quarantine, consigned or in-transit stock according to supplied scope and status definitions. A reserved quantity is not automatically absent from a physical count. Do not subtract it twice or reclassify ownership from an item description. Record an unresolved stock-status distinction where it affects the comparison.

## 2. Issue count sheets that can be returned unambiguously

Assign a count-run ID, sheet/batch ID and stable line ID. Each planned stock pool should be allocated to one initial count scope, unless separate observations are explicitly intended as independent recounts. Record sheet revision and scope so reissued or overlapping sheets cannot be added together accidentally. A second copy of the same sheet is not a second quantity.

The contributor sheet needs only practical fields:

- Line ID and supplied item/location/variant/lot identifiers
- Item label and expected counting unit, with evidenced pack instructions if needed
- Blank counted quantity, count state, observation time and counter/reference field as required
- A short note field for inaccessible stock, uncertain identity, unusual units or movement during counting
- A separate unexpected-item section with temporary line IDs, exact location, supplied identifiers, observed unit/quantity and time

Keep quantity blank initially. A reported zero must be an explicit counted observation; an empty cell means no usable quantity has been supplied. Provide distinguishable states such as not counted, counted and unable to count, with a reason for the last. Do not require unnecessary personal identifiers when a team or sheet reference is enough.

For a blind count, create a separate minimal contributor file that excludes expected quantities, variances, prior counts and costs. Do not merely hide the comparison sheet or columns; inspect formulas, names, notes, caches and links for unintended disclosure. [Excel worksheet protection](https://support.microsoft.com/en-us/excel/protection-and-security-in-excel) is not a confidentiality boundary. Keep the expected-stock and reconciliation workbook for its authorized reviewers.

For digital sheets, use typed quantities, text-safe identifiers, clear input fields and supported entry checks. For requested printable sheets, repeat the run/sheet ID and column headers on each page, leave usable writing space, and inspect page breaks and full identifiers. Delivering a PDF does not prove it was printed or a person performed the count.

This separation is an artifact design choice, not a promise of an ERP feature. [Microsoft's Business Central documentation](https://learn.microsoft.com/en-us/dynamics365/business-central/inventory-how-count-inventory-with-documents) illustrates separate recording documents with blank quantity fields and explicit recorded states; use the actual user's system and rules rather than copying its product-specific workflow.

## 3. Preserve returned observations before choosing a count

Import only the authorized returns and retain their file/revision and line locators. Preserve the raw observation: run, sheet revision, line/stock key, quantity/unit, state, observation time and attribution when evidenced. Keep data literal, including notes that resemble formulas. An assistant reading a count report has not independently verified the physical stock.

Check for duplicate returns, stale sheet revisions, overlapping assigned scopes, missing line IDs, unknown items, changed units and contradictory count states. A stated `counted` row with no quantity is incomplete. A numeric quantity with `unable to count` is conflicting. Keep the original value and state rather than forcing the row into a complete tally.

Preserve first counts and recounts as separate observations, not additive quantities. Use the supplied acceptance rule or explicit reviewer decision to select the observation used for reconciliation. A later filename, larger count or closer agreement with the system is not a selection rule. Recounts taken at different times also need their own movement alignment.

Match unexpected stock to the baseline only with supported dimension identity. Until matched, show it separately with its actual unit and location. Do not assign expected quantity zero merely because the selected export lacks that row; the export may omit its location or stock status. Zero is valid only when the baseline scope and source semantics establish it.

## 4. Compare stock at the same effective time

A count assembled over a period is not necessarily an instantaneous observation. If stock moved during counting, establish which movements were physically included, or use evidenced subcounts and their times. Do not assign the sheet's finish time to every quantity and assume the cutoff arithmetic repairs double-counted or missed moving stock. Hold a pool whose observation time basis cannot be established.

Use one declared comparison time per stock pool. When the source baseline is at time T and the accepted observation is at later time C, an available complete movement record can roll the expected quantity forward:

```text
expected at C = baseline quantity at T
              + physical receipts/transfers in during (T, C]
              - physical issues/transfers out during (T, C]

quantity variance at C = accepted counted quantity at C - expected at C
```

State the time-boundary convention and include each applicable movement once. Align effective physical movement times with the baseline's inclusion rule, not just transaction-entry dates. A transaction already represented in the snapshot must not be added again. Hold comparisons where cutoff inclusion is ambiguous. If the count precedes the snapshot, derive and document the inverse interval or request a suitable baseline; do not reuse the forward formula unchanged.

For a bin transfer, apply departure and arrival to the correct pools and account for in-transit scope. It may net to zero at an encompassing warehouse level while changing each bin. Preserve both legs; do not add a transfer to a warehouse total as a new receipt. Avoid using a location-level total to conceal offsetting bin or lot discrepancies.

A stated freeze can justify no movements only to the extent its timing and coverage are evidenced. The assistant must not infer that no stock moved because the movement file is empty. If relevant movement coverage is incomplete, mark the variance not comparable or provisional with the specific gap. Do not display an unavailable comparison as zero variance.

Compute signed and absolute quantity differences in the applicable unit. Apply a supplied recount threshold with its exact inclusive/exclusive boundary. If percentage variance is requested, define the denominator and handle expected zero explicitly; no percentage may be meaningful there. Do not introduce currency valuations, financial materiality or loss classifications unless separately requested with suitable inputs and authority.

## 5. Make the review workbook actionable

Use the simplest linked tables that preserve the workflow: expected baseline, observations, applicable movements, reconciliation and decisions. These can be sections rather than five mandatory sheets. Keep the private master separate from a blind contributor artifact.

The main review view should expose stock key, source expected quantity/time, accepted observation/time, movement adjustment, comparable expected quantity, variance, required recount/review state and unresolved reason. Provide editable reviewer fields for the specific decision or accepted-observation ID, separate from raw evidence and calculated statuses.

Count coverage as well as differences. Show expected pools with no usable count, inaccessible pools, ambiguous identities, overlapping observations, pending recounts and unexpected stock. Define mutually exclusive primary coverage states for the pool totals, while retaining other issue flags separately. A zero grand-total variance does not settle missing observations or offsetting item differences.

Keep these stages separate: sheets prepared, count reported, quantity comparable, recount resolved, reviewer accepted, and any later adjustment action. Do not mark a row finished while a required recount or cutoff question remains open. [Microsoft's inventory-journal guidance](https://learn.microsoft.com/en-us/dynamics365/supply-chain/inventory/inventory-journals) describes posting as a distinct action that changes stock and can create financial effects. This workbook should stop at the authorized review artifact, not perform that action.

## 6. Verify the saved packet and hand it over

Reopen saved files and check source IDs, text identifier types, units, formulas and actual record coverage. Reconcile planned sheet lines to the selected baseline and account for every returned observation as accepted, superseded, duplicate evidence, unresolved or outside scope. Confirm that two returned copies or an initial count plus recount cannot inflate stock.

Use a disposable verification copy to exercise an explicit zero, a blank count, an inaccessible pool, a duplicate return, an unexpected item, a unit mismatch, a movement on a cutoff boundary and a recount at a later time. Trace a representative variance independently from the baseline and selected movements. Check transfer effects at both bin and aggregate levels where applicable.

Recalculate affected formulas in the supported engine, inspect the saved review and print layouts, and verify the contributor file contains none of the withheld expected-stock information. Restore the intended blank or actual-return state after checks. State the application used and distinguish source inspection, formula calculation, print-preview review and physical observations. Do not claim native behavior or actual stock was checked when it was not.

Return the count sheet artifact, the private reconciliation workbook when requested, the run/snapshot identity and a short list of unresolved counts or decisions. For a preparation-only request, completion means blank usable sheets and a ready reconciliation structure; no reported count is implied. For a reconciliation request, completion means all supplied observations are accounted for and any remaining variances or coverage gaps are visible, not that inventory balances were changed.

If a source revision, unit conversion or cutoff cannot be resolved, hold only the affected comparison. Preserve the prepared packet and exact missing evidence. If a shared workbook changes during preparation, reread and reconcile rather than overwriting it. After an uncertain save, inspect the destination before retrying. Do not publish the private master or substitute guessed quantities to make a blocked result look complete.

## Illustration: fictional and unexecuted

A workshop's snapshot at 09:00 lists 20 units of item `0008` in bin A. A sourced physical receipt adds 5 units to that bin at 09:20, with the snapshot confirmed to exclude it. The accepted report at 09:30 states 24 units. Under the declared `(09:00, 09:30]` movement interval, expected stock would be 25 and the quantity variance would be -1. A later recount would be a new observation, not another 24 units to add.

A second issued row has no reported quantity. It would remain not counted rather than contribute zero stock. An unexpected item absent from a partial export would remain unmatched until its scope and identity were resolved. Neither the -1 difference nor an accepted recount would authorize posting an adjustment or alleging a loss cause.

This authored illustration was not executed. No workbook was generated, physical stock counted, movement feed checked, ERP action taken or adjustment posted by the example.
