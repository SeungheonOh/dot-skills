---
name: document-dataset-fields
description: Build a source-linked data dictionary for an existing table, export or dataset so another person can interpret its fields, units, codes, missing values and relationships. Use for documenting current meaning, not designing a new schema, cleaning records or certifying data quality.
---

# Document a Dataset for Its Next Reader

Create an editable data dictionary that lets someone use an existing dataset without guessing what its columns mean. Preserve exact field identity, separate declared rules from observations, and make unresolved meanings visible. A polished table of guessed definitions is worse than a short dictionary with clear questions for the data owner.

Use [design-data-model](../design-data-model/SKILL.md) for a proposed new representation, [profile-a-local-csv](../profile-a-local-csv/SKILL.md) for measured file characteristics, and [validate-dataset](../validate-dataset/SKILL.md) for checking records against established rules. This workflow documents the current dataset; it does not silently redesign, normalize or validate it.

## Inputs and deliverable

Identify the dataset/table/sheet and its version or dated export; the intended reader and intended use; the selected fields; and any schema, producer documentation, code list or data-owner explanations. Obtain only the sample rows needed to resolve interpretation. A schema and codebook may be sufficient without any raw records.

The deliverable is one editable dictionary plus a short dataset overview and a focused unresolved-meaning list. It may be Markdown, a requested spreadsheet or another agreed format. Preserve an existing format when it works. Ask only for a missing input that changes the meaning or authorized audience, not for a complete intake form.

Use already-authorized read-only sources. Keep output private unless saving or sharing to a specific destination is requested. Do not query production, refresh connected data, run embedded macros, upload files to an external profiler, or broaden access merely to fill missing definitions. Do not copy real personal or sensitive values into examples unless that exact disclosure is authorized and necessary. Use clearly labeled fictional examples instead; a changed name alone does not establish anonymization.

## 1. Establish the dataset's unit of meaning

Before defining individual fields, write what one row represents. Distinguish, for example, one order from one order line, one person from one attendance, and one observation from one daily aggregate. State the population, coverage period, known exclusions and refresh schedule only when the sources establish them.

Record the source identity and inspected version/date. For a workbook, distinguish sheet names, named tables and selected ranges; for an export, identify the exact file and export settings when known. A filename containing a date does not prove the observation period. A complete header list does not prove that a sample includes every kind of record.

For multiple tables, give each its own row meaning and qualified field names. Do not merge equally named columns across tables without evidence that their semantics agree. Keep join keys and relationships explicit, including a relationship's documented cardinality and any unresolved uniqueness assumption.

If row meaning is unknown, still inventory fields and evidence, but flag the affected use cases. Do not endorse counts, totals or joins until the distinction is resolved.

## 2. Inventory exact fields before writing definitions

Read the actual header/schema, preserving field order, spelling, case and relevant nesting. Assign each field a source locator. When duplicate or blank headers exist, distinguish them by source position, such as column D, rather than silently renaming them. Record any approved friendly label separately from the original name.

Reconcile the field inventory with the supplied documentation. Classify documentation-only fields, data-only fields and incompatible versions instead of combining them into a fictional unified schema. A deliberate exclusion should remain visible by count and neutral reason when exposing its name would be inappropriate.

For each in-scope field, capture only applicable properties:

- Exact name/location and a short human-readable meaning
- Stored representation and intended logical type, with the source for each
- Unit, currency, scale or timezone/calendar interpretation
- Documented missing-value markers and their meanings
- Code values and labels, including unknown or deprecated codes where relevant
- Identifier scope, relationships or derivation rule
- Declared constraints and where they are enforced, if known
- Definition source, evidence status and a safe synthetic example when helpful

Use a compact main table; put long code lists or formulas in named sections. Avoid forcing every field through dozens of empty columns.

## 3. Resolve the interpretation traps

Separate the literal value from its meaning. The [Frictionless Table Schema specification](https://specs.frictionlessdata.io/table-schema/) distinguishes physical text from logical types and applies missing-value markers before conversion. Use that distinction even when the deliverable is ordinary prose; do not label a numeric-looking identifier as a quantity just because a parser could convert it.

Work through the distinctions that matter for this dataset:

- **Identifiers:** preserve leading zeros and formatting that carries identity; state the namespace and whether reuse is documented. A sample with no duplicates does not establish a primary key
- **Amounts and measures:** identify units and scale, whether a percentage is a fraction or a whole percent, whether an amount includes tax, and what a sign means. Do not infer currency from the reader's location
- **Time:** distinguish event time, processing time and reporting period; date-only values from instants; timezone from display formatting. Leave an unspecified timezone unknown
- **Missingness:** distinguish blank, absent, null, zero and a sentinel only as supported. A blank may mean unknown, not applicable or not collected; do not choose silently
- **Codes:** copy the authoritative mapping and its version. Observed values are examples, not necessarily the complete allowed set. An unfamiliar code stays unresolved
- **Derived fields:** describe the actual numerator/denominator, filters, rounding and refresh boundary where established. A suggestive field name does not prove a formula
- **Relationships:** identify the referenced table and qualified key. Equal labels are not a join contract, and repeated detail rows can multiply a total

The [W3C tabular metadata vocabulary](https://www.w3.org/TR/tabular-metadata/) provides separate concepts for column names, titles, descriptions, datatypes, null markers and keys. If the user requests CSVW or another machine-readable format, use its actual specification and version; a Markdown dictionary alone is not a conforming schema or a validation result.

## 4. Keep evidence and unresolved meanings apart

Use clear local labels such as documented, observed in the inspected sample, inferred, conflicting or unknown. Tie consequential definitions to the exact source section or owner statement. An authoritative schema may establish a storage type while a data-owner explanation establishes the business meaning; retain both when they answer different questions.

If sources conflict, first check whether they describe the same export/version. For a current conflict, show both meanings and their locators; do not select the newer document automatically. Ask a narrow question such as “Does amount include tax in export version 4?” while completing unaffected fields.

Do not turn a documented requirement into an observed guarantee. “Required by producer schema; records not checked” is different from “present on all rows.” A successful sample parse does not prove all values fit, all keys are unique, or a business rule is enforced. Link existing profiling/validation evidence with its scope instead of manufacturing it.

## 5. Check the handoff from the reader's side

Read back the saved dictionary against the source field inventory. Verify:

1. Each selected field appears exactly once under the right table, or has an explicit exclusion; duplicate labels remain distinguishable
2. Definitions retain the actual units, time meanings, missing markers and code mappings that change interpretation
3. Declared constraints, observations and unresolved assumptions are visibly different
4. A representative intended question can be interpreted from the dictionary, including its population and join boundary, without inventing a rule
5. Synthetic example values fit the documented meaning and do not accidentally expose real records
6. Source locators, version notes and cross-references point to the intended material; formatting has not truncated long codes or definitions

This is a semantic/document check. Report any actual parsing, sample inspection or full-data validation separately; do not describe a paper walkthrough as an executed query.

If a header or source version changes during preparation, identify added, removed or renamed fields and refresh affected definitions. Do not copy old meanings onto a renamed field without evidence. If a workbook viewer coerces values, return to an authorized representation that preserves the source or mark the affected values unreadable; do not save the coerced copy over the original. If a definition cannot be resolved, deliver the usable dictionary with its specific open question rather than guessing.

Return the artifact, covered table/field scope, important limitations and the smallest remaining owner questions. If a requested save fails, keep the prepared file and identify the blocked destination. Do not add a new recipient or broader sharing setting as a workaround.

## Illustration: fictional and unexecuted

An export has one row per order line with fields order_id, line_id, amount_minor and sold_on. Its producer note defines amount_minor as the line amount in USD cents and sold_on as the shop's local calendar date. A sample has repeated order_id values and one blank sold_on; no missing-date rule is supplied.

The dictionary would describe order_id as repeating across lines, keep the amount's currency and scale explicit, and describe sold_on as date-only with blank meaning unresolved. It would not declare order_id unique, convert the date to UTC, or treat a blank as “no sale.” A sample value of 1299 could be shown as a fictional 12.99 USD line amount without claiming totals were computed or data validated.

This is an authored illustration. No dataset was parsed, query executed, spreadsheet edited or sharing action performed by the example.
