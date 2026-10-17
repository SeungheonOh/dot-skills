---
name: reconcile-design-cut-list
description: "Reconcile an established benign design, assembly quantities and supplied stock records into a revision-bound part/material cut list with preserved variants, blank-versus-finished dimensions and unresolved yield. Use for a reviewable preparation ledger, not nesting optimization, purchasing, stock posting or machine operation."
---

# Reconcile what a design needs before material is committed

Produce a traceable list connecting the selected design's part occurrences to required pieces and supplied material availability. Keep finished geometry, preparation blanks, purchased components and raw stock distinct. A bill of materials total or matching sum of lengths does not establish that the necessary pieces can be obtained from the available stock.

Use [build-stock-count-workbook](../build-stock-count-workbook/SKILL.md) to collect and reconcile physical stock observations. Use [solve-constrained-optimization](../solve-constrained-optimization/SKILL.md) when the requested outcome is an optimized allocation or nesting plan. This workflow prepares the demand and reconciliation ledger; it does not operate tools, choose machine settings or produce fabrication instructions.

## Establish scope, units and authority

Identify the exact approved design revision/configuration, requested number of finished assemblies and selected subassemblies. Obtain only inputs that affect quantities or compatibility:

- Source part list, CAD/BOM export or dimensioned design records, with their export scope and quantity semantics
- Part identities, variants/handedness, material specifications and finished dimensions with units
- Supplied blank allowances, grain/pattern direction, permitted rotations, finish/edge treatments and required geometric distinctions
- Purchased or complete subassemblies, nonmodeled items and explicit spare/overage rules
- Dated stock records, usable dimensions or piece counts, condition/compatibility evidence and existing reservations
- Requested output format, permitted preparation destination and whether this is a new plan or revision reconciliation

Resolve whether quantities are per parent, per finished assembly, already expanded for the job, or reported as a length/area rather than a count. Ask for missing definitions before multiplying. A row labeled Qty is not enough evidence.

Limit this guide to benign non-structural projects such as organizers, decorative panels or mockups. Exclude dangerous devices, weapons, load-bearing design approval and safety-critical fabrication. Do not create toolpaths, G-code, machine settings or cutting sequences. Do not buy materials, reserve or consume stock, contact suppliers or update an ERP merely because a shortage is calculated.

Keep source files unchanged and create a separate ledger. Preserve private design identifiers and supplier details within the authorized audience. Treat formulas, macros and external links in exports as untrusted data; use literal text-safe import for identifiers and notes. Do not upload designs or stock records to external optimization services without specific authorization.

## 1. Freeze the design population and reconcile hierarchy

Record source identities, revision/configuration, selected assembly tree, export time and inclusion rules. Account for suppressed, excluded, reference-only and optional parts. Absence from an exported BOM does not prove absence from the model or omission from the physical requirement.

Trace quantities from the actual hierarchy. A subassembly used three times and containing two copies of a part creates six occurrences, unless the source already reports the expanded six. Preserve the parent path or another lineage key for each contribution. Do not add a complete purchased subassembly and all its internal parts to procurement demand unless the user actually requires both.

Structured, flattened and top-level-only BOMs answer different questions. Onshape's [BOM documentation](https://cad.onshape.com/help/Content/Assembly/bill_of_material.htm) describes configurable subassembly display, while its [table guidance](https://cad.onshape.com/help/Content/Assembly/working_with_the_bom_table.htm) distinguishes local suppression from global exclusion. Inspect the actual application's export behavior; a familiar column layout does not establish complete coverage.

Keep source row identity distinct from table item numbers, which may change on reordering. Distinguish repeated occurrences from duplicate exports of the same occurrence. Never deduplicate solely by matching description or dimensions. Record separately any required nonmodeled item supplied by the user; do not invent adhesive, hardware or consumable quantities from appearance.

## 2. Build part identities that preserve interchangeability

Group contributions only when they represent interchangeable required pieces under the supplied design rules. Relevant fields can include part ID/revision, configuration, material/specification, thickness/profile, finished dimensions, handedness, grain direction, edge treatment, finish and hole/cutout pattern. A shared rectangular footprint does not make left- and right-handed pieces equivalent.

Keep nominal stock descriptions separate from measured usable dimensions. Do not replace a nominal material thickness with an assumed actual value, convert a model envelope into a blank size, or merge grades because their names are similar. Preserve unknown specifications as holds for the affected group.

Normalize supported units while retaining original values and precision. Length, area, volume, count, mass and packs are different quantity types. Convert a pack only with an established pack size; do not use density or a coverage rate without applicable evidence. [check-dimensional-calculations](../check-dimensional-calculations/SKILL.md) can support a consequential conversion, but ordinary unit checks do not establish material suitability.

## 3. Separate finished pieces, blanks and raw stock

For each made part, retain the finished geometry and any explicitly supplied preparation-blank rule as separate fields. Show which allowance changes which edge or dimension and its source. For example, an approved allowance of 2 mm on each end adds 4 mm to that dimension, not 2 mm and not an unexplained percentage. Do not invent allowances for trimming, finishing, tool kerf or material movement.

Keep a blank's length, width, thickness/profile, orientation and other shape constraints together. A total-area comparison cannot establish that a long piece fits on a short sheet. Summed lengths cannot establish a feasible allocation among individual boards. Irregular pieces may require profile geometry rather than a bounding rectangle; a conservative envelope can reject a possible placement without proving the real shape cannot fit.

If the user supplies an existing stock-layout or yield plan, reconcile its material accounting rather than silently generating a new one. For each stock identity, include all assigned blanks, documented end trims, actual separation losses and declared reusable remainder. Kerf depends on the supplied layout and separation count; do not assume it is always piece count minus one. Do not add it twice when blank dimensions or the source plan already include it.

If layout or process-loss evidence is missing, return piece demand plus length/area totals as summaries or lower bounds with their conditions. Leave raw-stock yield and purchase quantity unresolved. Do not round a calculated area quotient into a supposedly sufficient number of sheets or claim an optimal cut list.

## 4. Reconcile demand with evidenced availability

Compute design demand from the reconciled occurrences, then add only explicit spares or overage. Keep those extra quantities separate with their rule; a percentage applied per part type and one applied to the whole job can produce different rounded counts. Preserve the user's rule and round at its defined level.

Deduct only evidenced compatible, usable and available supply. Keep ready-made parts, already prepared blanks and raw material in different stages. A ready-cut piece can cover one compatible requirement directly; a raw strip covers future pieces only through an accepted allocation/yield basis. Do not subtract the same raw stock again after deducting pieces that are already represented as cut from it.

For finished pieces or compatible blanks with established one-for-one allocation, show required quantity plus approved spares, allocated available quantity and remaining demand. Keep surplus separate rather than displaying negative need. For raw stock, show assigned demand, the accepted layout reference if any and unresolved capacity instead of pretending the conversion is one-for-one.

Respect reservations and competing uses. Assign each stock ID or quantity at most once across the job and preserve existing commitments. When the same limited stock could cover alternative part types, show the allocation conflict or apply the user's established priority; do not deduct the full pool independently from every line. Unknown availability is not zero, and it cannot support a firm shortage or sufficient-stock conclusion.

Do not invent substitution permission. A proposed different material, thickness, finish or orientation belongs in an option/hold column, not the accepted allocation. A supplier stock record is evidence of a reported state at a time, not a fresh physical count or guaranteed current availability.

## 5. Handle revisions without mixing old and new work

Compare old and new demand by stable part identity and compatibility, not row position. Separate added, removed, quantity-changed and geometry/material-changed requirements. A retained part number with changed dimensions may make an already cut piece unusable for the new design; keep that decision unresolved until supported.

Carry work-in-progress evidence explicitly: reported cut, uncut, reserved, consumed or unknown. Do not assume a removed requirement restores raw stock that has already been cut or consumed. Nor does an obsolete drawing prove physical material was committed. Keep actual reports distinct from planned allocations.

Record what can be retained, what requires remeasurement or design review, and what has merely become unneeded under the new demand. Do not discard pieces, release reservations or overwrite earlier evidence as part of this planning update. A CAD drawing table and its views may describe different configurations; Onshape's [cut-list table documentation](https://cad.onshape.com/help/Content/Drawing/cut_list_table.htm) explicitly notes that changing the table configuration does not change the views. Reconcile both configuration identities when using a drawing as input.

## 6. Verify and deliver the preparation ledger

Keep the output proportional: a small project may need one table and a short assumptions note. Include part/revision, source occurrence contributions, material, finished dimensions, approved blank dimensions, required count, explicit extra count, compatible allocation, remaining demand and holds. Add stock-layout references only when they exist.

Read back the saved file and reconcile every selected occurrence to an included group or explicit exclusion. Trace one nested quantity independently, check a repeated or mirrored part and confirm unlike materials/units remain separate. Recompute totals from saved rows and verify that allocations do not exceed the same stock pool. Preserve text IDs and literal notes in any spreadsheet output, and inspect formula/recalculation behavior only with an available authorized consumer.

Check the specific gaps that matter: missing material, an unknown allowance, unclear BOM expansion, duplicate exports, incompatible stock, uncertain reservation or absent layout. A clean grand total cannot cancel an unresolved line. For a revised plan, reconcile changed requirements and retained work against both source versions.

Deliver the actual ledger with its design/configuration, stock as-of evidence, unresolved yield or supply and the next necessary decisions. Label piece demand reconciled, stock allocation supported and raw-stock yield established as separate conclusions. Stop at the review artifact; no material was ordered, reserved, cut or physically verified by producing the list.

If source semantics or stock identity cannot be resolved, hold the affected group and continue independent groups. Preserve unsuccessful imports or candidates separately. If a save or concurrent edit leaves the destination uncertain, inspect it before retrying and reconcile rather than overwriting another person's changes.

## Fictional, unexecuted illustration

A selected organizer design uses two identical rails and one base per finished unit. The job is three units, and the user separately requests one spare rail. The BOM quantities are confirmed to be per finished unit, so demand is six rails plus one spare, and three bases.

The stock record reports two compatible ready-cut rails, one already reserved for another project. Only one can be allocated: six rails remain needed. A raw sheet has enough total area for three bases, but its usable width and the base orientation rule are absent. It cannot yet cover those bases or establish a purchase quantity.

A second export of the same assembly is duplicate evidence, not another three units. If a later design revision changes rail length, the old ready-cut rail needs a new compatibility check rather than an automatic deduction.

This authored illustration was not executed. No CAD export, workbook, stock count, nesting calculation, purchase or physical cutting occurred.
