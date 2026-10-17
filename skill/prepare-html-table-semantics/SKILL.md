---
name: prepare-html-table-semantics
description: "Prepare an implementation handoff for an existing HTML-bound data table, mapping values to exact row, column and group headers while preserving units, notes and responsive representations. Use for a table-content and semantic-association package, not data analysis, document repair or interactive grid implementation."
---

# Hand off a data table's actual relationships

Turn an approved data-table design or source table into a semantic handoff: the content map, header association map, caption/notes and representation rules needed to implement the same comparison in HTML. The central question is what each value means when it is read outside its visual position. Bold cells and a header-row flag cannot answer that alone.

Use [document-dataset-fields](../document-dataset-fields/SKILL.md) to resolve field meaning, [repair-document-accessibility](../repair-document-accessibility/SKILL.md) to repair a Word/PDF or other existing document, and [design-user-interface](../design-user-interface/SKILL.md) when the comparison itself needs designing. This workflow produces a table-specific specification, not a whole-page accessibility audit, a data-cleaning task or a working grid component.

## Establish the source and destination contract

Identify the exact source table/design revision, intended reader task, HTML destination or component constraints, included rows/columns, approved labels and any requested narrow-screen representation. Obtain the field dictionary, legend and footnotes needed to interpret values. Prefer a structured source over retyping a screenshot; when only a picture exists, preserve transcription uncertainty and ask for the underlying values where ambiguity changes meaning.

Determine whether the content is genuinely tabular, with meaningful row/column relationships, or merely uses a visual grid for layout. Distinguish a data table containing a few links/buttons from an application grid requiring cell navigation or editing. The [APG table pattern](https://www.w3.org/WAI/ARIA/apg/patterns/table/) describes the table/grid boundary and prefers native HTML table elements where possible. Do not propose a grid role just to make a static comparison seem more accessible.

Deliver editable content and association maps plus implementation/review notes in the requested document format. Preserve the original source and accepted numeric/text values. Do not change calculations, query production data, add runtime behavior, upload private records to a converter, or publish the handoff without authority. Samples must be fictional or specifically approved for the recipient; hiding private columns visually does not remove them from delivered markup or a downloadable file.

## 1. Map cells before choosing markup

Give the table a stable ID and record what one data row represents. Identify dimensions, measures, comparison groups, subtotal/grand-total rows and notes. Keep a source locator for each value or repeated row template. Use stable cell/header identities in addition to visual coordinates because inserting a row can change positions without changing meaning.

For each kind of data cell, record:

- Source row/field or exact source cell and unchanged display value
- Row header(s), column header(s) and applicable group header(s)
- Unit, scale, period and population needed to interpret the value
- Note/qualification references and their intended scope
- Whether a blank, zero, dash or unavailable marker has a documented meaning

Expand merged areas into an explicit occupancy map for reasoning, without duplicating their source values. A spanning header covers several positions; it is not several independent headers with different identities. Detect overlaps, unexplained gaps and spans crossing an intended group boundary before describing associations.

Separate table content from annotation. Proposed labels belong in an annotation field until accepted; do not silently replace an ambiguous source header. Empty corner cells can be structural, while an empty data cell can carry missingness. Do not give either a fabricated meaning just to remove a blank.

## 2. Derive associations from meaning

For each representative data cell, answer in plain language: which entity/group, which measure, which period, which unit, and which qualifications apply? Compare those answers with the visual design and source dictionary. This becomes the semantic association map against which implementation can be checked.

For ordinary rectangular tables, describe the row and column headers and their scope. For grouped headers, specify the exact group boundaries as well as the spanning header. [WAI's irregular-header guidance](https://www.w3.org/WAI/tutorials/tables/irregular/) explains the relationship between row/column groups and scoped group headers. A colspan or rowspan expresses occupied geometry; it does not by itself settle the complete intended header relationship.

For changing or multi-level relationships that are not adequately represented by simple scope, hand off unique header identities and the explicit header set for each data-cell class. [WAI's multi-level guidance](https://www.w3.org/WAI/tutorials/tables/multi-level/) describes ID-based associations and simplification into smaller tables. Check that every referenced header actually belongs to the intended table and that IDs are unique in the complete containing document, not only within this fragment. Do not assume listing IDs guarantees a particular spoken order in all consumers.

Do not attach every preceding header to every value. A repeated “Actual” label under Q1 and Q2 needs distinct identity and the appropriate period context. A subtotal may have a different row meaning from the items above it. A note applying only to estimated values must not become a disclaimer for the entire table.

If the relationship is too difficult to explain without a visual gesture, consider a simpler representation only within the allowed editing scope. Splitting a table must preserve comparisons, shared units, group identity and the intended reading task. Preserve a source-to-output map and all values/notes; do not collapse multiple measures into prose, drop exceptions or change totals to make the layout easier.

## 3. Write the reader-facing context

Prepare a concise caption that identifies the table and its relevant subject/period. Include a short structural explanation when unusual grouping or an interpretation rule needs it. [WAI's caption and summary guidance](https://www.w3.org/WAI/tutorials/tables/caption-summary/) distinguishes identifying a table from explaining its organization; the explanation should not simply repeat the caption or substitute for header associations.

Retain units and scale at the level where they apply. If all amounts are in thousands, say so; if units differ by column, preserve those differences. Keep date-only periods, timezone-qualified timestamps, percentages and percentage-point differences distinct. Do not turn rounded displayed figures into a claim of exact equality with totals.

Convert a color-only or icon-only status to an equivalent text meaning based on the approved legend. Keep uncertainty explicit: a warning icon is not necessarily failure, a blank is not automatically zero, and an estimate is not an observed outcome. If the legend is missing, flag that content instead of inventing a label.

Provide relevant note text and a clear mapping from each marker to the cells or groups it qualifies. A header name, a note explanation and an action's accessible name serve different purposes. For row actions, specify enough row context to distinguish repeated labels such as “View” without dumping the entire row into every control name. Do not include hidden private identifiers just to make names unique.

## 4. Preserve the meaning across representations

For a narrow layout, document which representation is intended: the same table in a scrollable area, a simpler table arrangement, or a deliberately designed record view. Do not assume a CSS rearrangement preserves table relationships in the accessibility tree. A card view needs each value's actual labels and notes; it may also need a route back to a cross-row comparison if that is the reader's task.

If multiple layouts coexist, identify the authoritative content source and how duplicated visual structures avoid duplicated reading content and conflicting IDs. Hidden duplicate tables can retain private data or create contradictory names. Treat these as implementation obligations to verify, not as properties established by a static design.

When sorting, filtering, paging or virtualization already belongs to the design, preserve stable row identity, current filter/sort meaning, and partial-data boundaries in the handoff. A visible page is not the whole dataset. Specify how a moved row retains the correct headers and row-action context. Do not infer that a filter changes totals unless the supplied metric rule says so.

Hold interactive-grid mechanics, virtualized accessibility indices and runtime focus behavior for the actual component contract when not supplied. Naming those dependencies is better than proposing arbitrary roles or a fictional complete row count. The table handoff may finish for the supported static representation while that integration remains unresolved.

## 5. Accept the semantic package

Read back the saved content and association maps. Check:

1. Every in-scope source value and note has an output disposition, with no accidental duplication, omission or numeric rewrite
2. Header IDs, occupied positions and group boundaries are internally consistent; referenced headers belong to the intended table
3. A cell at each header/group boundary can be interpreted from its recorded relationships without relying on color, spacing or “same as above”
4. Similar header labels, subtotal rows and missing-value markers preserve their distinct meanings
5. Captions, units, labels and note scopes agree across every proposed representation
6. Reader-facing material contains only the data authorized for that audience

Select paper checks from the actual risk: the first cell under a new period, an irregular row group, an estimate footnote, a blank amount, a subtotal or a row moved by sorting. Write the expected interpretation and compare it to source evidence. These checks assess the specification; they do not establish browser accessibility-tree output, screen-reader reading or responsive rendering.

Include a short downstream acceptance sheet naming those separate checks on the eventual exact implementation: source associations, exposed table/header relationships, practical cell navigation, visible labels/notes at narrow width, and any existing controls. Leave them unexecuted until they actually occur. Do not certify WCAG conformance from this handoff or an untested markup candidate.

If headers or source values change, refresh the affected association classes and adjacent group boundaries before reusing the old mapping. If meaning remains ambiguous, deliver clear portions with the exact unresolved cell/header question. If the destination cannot preserve the required relationships, identify that loss and propose a supported alternative without silently replacing the requested format. Check uncertain saves before retrying and preserve concurrent work.

Return the content map, header-association specification, caption/notes and representation requirements with the source revision and review limits. Stop at the agreed handoff; editing an application, repairing a separate export or publishing the table needs its own scope.

## Fictional, unexecuted illustration

A fictional workshop table has rows for two rooms and two column groups, Spring and Autumn. Each group contains Capacity and Booked. The value 8 in the North Room's Autumn Booked cell belongs to North Room, Autumn and Booked; “Booked” alone loses the season. A note marks Autumn bookings as provisional. The room-capacity cells do not inherit that note.

The proposed handoff gives the repeated Booked headers distinct IDs, maps 8 to the correct row/group/measure, and keeps a documented dash in one cell as “not reported,” not zero. If the table becomes two seasonal tables, each receives the season identity and necessary room/unit context, with both original measures preserved.

This is a fictional authored illustration. No dataset, HTML renderer, accessibility tree, screen reader or live table was executed or inspected by the example.
