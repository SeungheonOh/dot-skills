---
name: repair-spreadsheet-formulas
description: "Diagnose and repair incorrect or broken formulas in an existing workbook, tracing calculation dependencies and preserving intended meaning, native features and unresolved inputs. Use for a checked formula-repair candidate, not designing a new model, cleaning source data or replacing formulas with values."
---

# Repair the calculation, not just the error display

Deliver a workbook whose selected calculations express the established rule, with a traceable repair record and evidence from the saved candidate. Removing visible error codes is not sufficient: a plausible number can still use the wrong range, stale cache, incorrect lookup mode or unintended blank-as-zero treatment.

Use [build-spreadsheet-model](../build-spreadsheet-model/SKILL.md) when the relationships themselves need designing, [spreadsheet-cleanup-reconciliation](../spreadsheet-cleanup-reconciliation/SKILL.md) for input normalization, and [reconcile-spreadsheet-review-copies](../reconcile-spreadsheet-review-copies/SKILL.md) for competing reviewer edits. This workflow restores an existing calculation contract; it does not invent a business rule to fit an expected total.

## Establish the repair boundary

Identify the exact workbook or native sheet revision, application/version, affected output cells, observed symptom, and intended rule or independently established result. Resolve whether the request is diagnosis, a separately saved repair candidate, or an authorized edit to a named live sheet. A screenshot can establish a symptom but usually cannot establish the formula, underlying cell types or dependency graph.

Inspect supplied evidence before asking questions. Useful anchors include a previously working revision, approved metric definition, a small known calculation, or a source-linked business rule. A neighboring formula or remembered total is a clue, not unquestionable authority. If the intended rule is ambiguous, deliver the dependency finding and proposed alternatives while holding that semantic choice.

Keep the original and any current unsaved work. Use a noncolliding copy in the authorized private destination, or a verified recoverable revision before an explicitly authorized in-place edit. Do not upload the workbook to an online repair service, expose private cell values in a public search, unlock protected ranges, or enable macros, external links, add-ins or data connections as incidental troubleshooting.

## 1. Separate formula, input, cache and display

Capture each affected cell's actual formula or literal value, storage type, available cached/displayed result, number format, relevant names/table identity, and current calculation state. Record the observed application and source revision. A values-only reader cannot establish which formula is present; saving its view over the workbook destroys the calculation.

Inventory relevant workbook features before choosing an editing tool: named ranges and their scope, tables, dynamic or legacy arrays, protected cells, hidden sheets/rows, external references, custom functions, macros and linked charts. Retain unsupported features rather than recreating the file through a lossy writer. A data-only extract can support diagnosis but is not a repaired workbook.

Classify the symptom with evidence:

- Formula stored as text, text-only view, or display formatting mistaken for a calculation error
- A valid expression with stale results because calculation did not run
- Parse or unsupported-function failure in the actual consumer/version
- Broken or shifted references, wrong name scope, missing external source, or an unintended circular dependency
- Input/type/lookup mismatch, including significant identifier spaces, missing keys, text numbers or ambiguous dates
- Correctly calculated but semantically wrong logic, range, aggregation or error handling
- Array output blocked by occupied/merged cells or an unsupported location

Do not fix a column-width display problem by editing arithmetic. Do not convert identifiers into numbers, fill missing inputs with zero, enable iteration, or change the workbook date system merely to make a symptom disappear.

### Check whether display precision changes the data

Inspect the workbook's precision setting before changing number formats or diagnosing a rounded value as display-only. Excel's [precision-as-displayed option](https://learn.microsoft.com/en-us/troubleshoot/microsoft-365-apps/excel/floating-point-arithmetic-inaccurate-result#method-2-precision-as-displayed) can reduce stored numeric precision across all worksheets; disabling it does not restore discarded digits. Record the setting and preserve the file before any authorized change. Do not enable it as a shortcut for matching a total, or assume a formatting edit is cosmetic while it is active.

If constants have already lost precision, a formula-only repair cannot reconstruct them. Recover a supported value from preserved source evidence or a suitable earlier revision, retaining that input correction separately; otherwise leave the missing precision unresolved. Distinguish an explicitly required rounding step from workbook-wide precision loss. Any proposed setting change needs its own scope and dependent-output checks, not silent inclusion in a local formula patch.

**Fictional, unexecuted illustration:** A source rate is 0.1234, but a workbook saved with precision as displayed and a two-decimal number format now stores 0.12. Multiplying by 1,000 correctly gives 120 for that stored input, rather than 123.4 for the original rate. Increasing the displayed decimals or replacing the multiplication formula cannot recover the missing digits. No workbook was edited or recalculated for this illustration.

## 2. Trace the first meaningful divergence

Start at the reported result and follow actual precedents until the first unsupported value or relationship appears. Retain a compact path of cell/name identities, formula meaning and observed values. Trace shared dependencies before repairing dozens of downstream errors independently.

Use the actual consumer's formula inspection where available. Microsoft's [Evaluate Formula guidance](https://support.microsoft.com/en-us/excel/evaluate-a-nested-formula-one-step-at-a-time) describes intermediate inspection and its limits: some branches are not evaluated, blank references may display as zero, and volatile functions can change during inspection. A diagnostic display is evidence about that evaluation, not a substitute for the source's missing-value meaning.

Compare analogous rows using reference-aware relationships. Relative, absolute and mixed references, structured table references, scoped names and array anchors can legitimately differ. Do not copy the nearest formula merely because it looks similar. Determine whether a row is a detail, subtotal, exception or deliberately overridden input before changing it.

For a lookup, inspect the actual match rule, key types, duplicate-key behavior, search/range assumptions and the meaning of no match. For a total, inspect range endpoints, inserted rows, filters, hidden rows, subtotal inclusion and units. For division, distinguish a valid zero denominator case from missing or incorrectly typed input. A blanket error wrapper that returns zero can conceal all of these.

If a reference was deleted, use preserved history, a known mapping or an approved rule to establish its intended target. A broken-reference token does not retain enough evidence to reconstruct a missing sheet or range by itself. Keep unresolved repairs explicit and complete independent supported portions.

For spill problems, inspect the intended output region and its owners before any change. Microsoft's [spill-error reference](https://support.microsoft.com/en-us/excel/how-to-correct-a-spill-error) distinguishes occupied space, merged cells, table placement and other causes. An obstructing note or formula remains user work. Prefer an authorized layout-preserving correction; deleting blockers, unmerging cells or converting a table needs appropriate scope and cannot be assumed harmless.

## 3. Make the smallest meaning-preserving repair

Record each proposed change as source revision, exact cell/name or formula group, before expression, after expression, rule evidence and dependent outputs. Group repeated repairs only when their reference relationship is actually the same. Keep exceptional rows separate.

Preserve the intended expression and editable behavior. Do not paste a computed answer over a formula, replace a supported function with a hard-coded value, suppress errors globally, or widen a lookup until one result appears. An input correction is a separate evidenced change; do not silently repair source facts while describing the work as formula-only.

Apply changes through a consumer or library that preserves the required workbook features. Use its supported formula representation, locale and separator rules; raw search-and-replace across formula strings can alter quoted text, names and unrelated references. Edit an array's owning expression through the supported route rather than overwriting individual spill cells. Inspect automatic table-formula propagation and stop it from changing out-of-scope exceptions.

For a shared sheet, reread the exact target cells and revision immediately before writing. Reconcile intervening edits instead of overwriting a whole range from an old export. Use narrow or conditional writes where available. Do not change sharing, protections or external-data permissions to gain a convenient editing route.

## 4. Recalculate within a known execution boundary

Before calculation, identify formulas that could run custom code, contact external services, read changing linked workbooks or alter state. Use only already-authorized sources and execution. A repair request is not permission to enable active content or refresh every connection. If the required calculation cannot be safely isolated, provide the candidate with that check blocked.

Inspect calculation mode without changing unrelated open workbooks. Microsoft documents that [open Excel workbooks share the current calculation mode](https://learn.microsoft.com/en-us/troubleshoot/microsoft-365-apps/excel/current-mode-of-calculation). A global switch or broad recalculation can affect more than the selected file. Prefer a supported isolated copy/session or suitably scoped calculation; retain the user's established mode unless its change is authorized.

Use a compatible calculation engine for the requested formulas. Writing expressions, setting a recalculate-on-open flag or reading cached numbers is not an executed recalculation. Another engine's successful result does not establish full fidelity in the user's chosen application, especially for custom functions, arrays and external references.

Check an independently derived result and a distinguishing boundary in a disposable verification copy. Choose cases that address the repair: first/last included row, exact missing key, zero versus missing input, a copied-row reference, or an unobstructed array region. Verify affected dependent totals/charts as well as the corrected cell. Preserve legitimate errors and unknowns instead of demanding an error-free sheet at any cost.

Restore the intended delivery inputs, calculate as authorized, save, and reopen the exact candidate. If volatile results change by design, record the relevant calculation time or input state and compare the meaningful relationship rather than inventing exact repeatability.

## Acceptance, recovery and delivery

The repair is ready when:

- Each changed expression has supported intent, and unrelated formulas, input facts and native features remain intact
- The originally failing relationship and its affected dependents have the expected behavior under the actual checked inputs
- Missing values, unresolved references and unsupported functions remain visible
- Saved formula text, results and intended inputs were read back from the delivered revision
- Recalculation, application compatibility and visual inspection are separately reported according to what actually occurred

If a save or live write is uncertain, inspect the destination before retrying. If a writer drops a required feature, retain the original and failed candidate, use a preserving route when available, and otherwise deliver the repair map with the exact limitation. Undo only this task's identified changes; a whole-workbook rollback can erase concurrent work. Do not use a broad reset, external-link break or deletion as automatic recovery.

Return the candidate or verified sheet link, the corrected calculation and cause, a compact before/after repair register, actual checks, and remaining holds. Stop when the bounded repair and meaningful available checks are complete or the next step requires an unresolved rule, source, capability or permission.

## Fictional, unexecuted illustration

A fictional packing workbook calculates work minutes from units multiplied by minutes per unit. Rows 7 and 8 contain 12 and 9 units, and the approved rate is 4 minutes per unit in a fixed input cell. Row 7 displays 48 minutes. Row 8 displays zero because its copied formula moved the rate reference to the blank cell below.

The proposed repair fixes that rate reference under the evidenced rule, yielding an expected 36 minutes for row 8. Acceptance would also check that a missing rate remains unresolved under the workbook's existing rule, and that the downstream total includes both rows once. The correct-looking 48 above is useful comparison evidence but is not the authority for treating every blank as zero.

All values and cells are invented. No workbook was edited, formula evaluated, application opened, connection refreshed or result recalculated for this illustration.
