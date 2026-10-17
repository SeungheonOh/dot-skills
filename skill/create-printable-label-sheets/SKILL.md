---
name: create-printable-label-sheets
description: "Turn approved text or table rows into stock-matched printable label sheets, preserving record counts, repeated copies and exact placement. Use for address, name, folder or equipment labels; not inventory reconciliation, postage purchase, regulated product labeling or commercial-print preflight."
---

# Make labels that fit the sheet

Deliver an editable label master, a fixed-page print PDF and a short sheet map so the user can print the intended labels on the stock they actually have. The task is the content-to-slot layout: which record appears in each physical label, at what size and in what order. A list of label text, a generic table or an attractive page preview alone does not establish that fit.

Use [box-inventory-handoff](../box-inventory-handoff/SKILL.md) when box assignments or contents first need reconciling. Use [prepare-print-production-package](../prepare-print-production-package/SKILL.md) for a commercial provider's production contract. Neither task is required just to lay out an already approved list.

## Establish the content and physical contract

Reuse the supplied facts and ask only for missing details that change the sheet:

- Exact source list or selected table range, intended fields, record order and copies per record
- Label manufacturer/product/template code, sheet size and orientation; alternatively, measured label dimensions, row/column count, pitch and page-edge offsets
- Intended label use and audience, minimum legibility needs, approved wording and any permitted abbreviations
- Available editor and requested editable format, plus the user's printer model or documented margins when available
- Whether every sheet is fresh or a particular slot pattern must remain unused; whether the task ends at file preparation or includes separately authorized printing

Sheet size and label size are separate. A template with the right number of labels can still have the wrong pitch or page size. Prefer the exact manufacturer's template or dimensional specification, verifying the product code against the package information. Do not infer geometry from a screenshot's displayed pixels or a similar product name.

If the stock is unknown, prepare the exact label text and a labeled layout proposal while requesting the code or measurements. Do not call that proposal stock-matched. If only a PDF can be created, state that the editable master is unavailable rather than renaming the PDF or substituting an unrelated format silently.

## 1. Freeze what each label says

Keep the original unchanged. Make a compact occurrence list with a stable source-row locator, approved display lines, requested copy count and any hold. Keep postal codes, identifiers and room numbers as text when needed; preserve leading zeros and intentional line breaks. Do not convert a date-like identifier or infer a missing address element.

Distinguish intentional copies from duplicated input. Two selected records with identical wording remain two records unless the user asked to merge them. A quantity of three means three label occurrences, not a printed numeral appended to the text. Require nonnegative whole-number copy counts; flag blanks or ambiguous quantities rather than silently treating them as one.

Map fields explicitly. Suppress an absent optional line without leaving awkward blank space, but hold a record when a field essential to the requested use is missing. Keep edits separate from source values. Layout work does not authorize shortening a person's name, changing an address, translating a label or inventing a warning symbol. Address formatting is not postal-address validation, and an address label is not paid postage.

Use only fields needed on the label. A source spreadsheet may contain private notes, contact details or unrelated columns that should not enter the master, PDF, hidden merge data or recipient-facing sheet map. Do not upload the list to an online label designer or print service merely because its template is convenient. Verify the authorized destination before placing source-linked files in shared or synced storage.

## 2. Build the slot map before the layout

Define the origin and reading order in a view of the sheet's printed face: for example, top-left, then across each row. Give each physical slot a page, row and column. Do not confuse the printer's feed edge with the logical first label.

For a regular rectangular grid, record label width/height, horizontal/vertical pitch and top/left offsets in one unit. Pitch is the distance between corresponding points on neighboring labels, not the gap alone. Check the final label edge against the sheet dimensions and documented printable area. Use the actual dieline for staggered, round or irregular stock rather than forcing it into a rectangular assumption.

Expand each approved source record into its requested number of occurrences, preserving the agreed ordering. Assign each occurrence to an available slot once. Mark remaining slots blank. Reconcile requested copies, placed copies, held copies and deliberate blanks; do not quietly drop the last few rows or repeat the first page to fill a sheet.

For a partially used sheet, require an exact unused-slot map from the user and evidence that the stock/printer permits that sheet to be fed again. Otherwise prepare for fresh sheets. A blank area in a photograph does not prove that a label is present or safe to feed. Never suggest feeding peeled, damaged or unsupported sheets as a way to save material.

## 3. Lay out and merge without changing the grid

Use a supported label/template workflow or fixed page geometry. Keep the label grid stable while fitting text inside its safe area. Do not rely on automatically growing table rows, browser margins, invisible paragraph spacing or application defaults to preserve physical placement.

For a desktop Word workflow, [Microsoft's label instructions](https://support.microsoft.com/en-us/word/create-a-sheet-of-nametags-or-address-labels-in-word) describe choosing the label type/size and creating a page of different labels. Use the current supported workflow for the installed editor; do not promise equivalent label authoring in an unsupported web editor.

In a mail merge, separate the record advance from the text fields. Preview the first two different records, the last slot of a page and the first slot of the next page. A repeated first record, skipped record or page-boundary reset is a merge problem even when each label looks well formatted. Resolve merged output into a saved print candidate and compare it with the slot map.

Fit the longest, multiline and non-ASCII records, not only the first row. Prefer a sensible line wrap or an agreed layout change over tiny text. Do not silently truncate, shrink every label to unreadability or remove a meaningful line. Keep orientation and padding consistent; use a hold when a particular record cannot fit the chosen stock legibly.

Avoid adding cut outlines, page headers, crop marks or grid lines to the print PDF unless requested. A separate proof can show slot boundaries and IDs. If a requested label contains a QR code, use [create-scannable-qr-asset](../create-scannable-qr-asset/SKILL.md) for that asset and preserve its clear area; a correct sheet layout is not a scan test.

## 4. Check the saved sheets and distinguish physical proof

Reopen the editable master and exact PDF. Confirm page size, orientation, page count, fixed slot dimensions and each occurrence's text. Render every page for visual inspection when tools permit. Compare the PDF against the slot map, including blank/held positions, repeated copies, first/last records and page transitions. Inspect glyphs, wrapping, clipping and content crossing a label boundary.

For a plain-paper alignment proof, [Avery's home-printing guidance](https://www.avery.com/blog/how-to-print-labels/) recommends matching sheet size, using actual-size scaling and checking a paper proof against the label sheet. Keep that recommendation distinct from an executed print. Use the printer and stock manufacturer's own feed and media-setting instructions; do not change a shared printer's defaults to prepare a file.

The print note should identify the exact PDF, stock/template, page size, single-sided orientation, actual-size/100% setting and expected feed orientation if established. Warn against fit-to-page scaling for this calibrated layout. Physical alignment remains unverified until an actual proof is inspected. A screen ruler or correct PDF dimensions cannot establish the printer's feed accuracy.

If an authorized proof is available, compare positions near all four corners and across later rows. A constant offset suggests a placement/feed offset; increasing drift suggests a scale or pitch mismatch. Check those causes before altering individual labels. Save a new candidate for an accepted correction and repeat the affected checks. Do not disguise the wrong template by nudging every record separately.

## Delivery, recovery and stopping point

Return the editable master, fixed-page PDF and a concise note containing the source revision, stock geometry, record/copy/page counts, held rows, print settings and checks actually performed. Keep a private source-to-slot map when it is useful for reprints; avoid duplicating personal data unnecessarily in a public proof.

- If a field changes after layout, regenerate affected occurrences from the new source revision and recheck all pages whose pagination moved
- If an exporter changes page size or row height, correct the export/layout setting in a new candidate; do not rescale the approved text blindly
- If physical alignment is unknown, deliver the preparation with the proof step pending, rather than claiming the labels were printed successfully
- If a print submission has an uncertain result, inspect the relevant job status before resubmitting; do not create duplicate batches or cancel unrelated jobs

Stop when the requested files meet the content and geometry contract, or the exact stock/fit decision is identified. Printing, mailing, applying labels, buying stock and sending the list to another service need their own applicable authority.

## Fictional example, not executed

A supplied fictional template has two columns and three rows. Labels are 80 by 40 mm; pitches are 90 and 45 mm; top and left offsets are 15 mm on an A4 portrait sheet. Three approved equipment names need respectively two, one and three copies, in source order.

The proposed sheet map places the first name in row 1's two slots, the second at row 2 column 1, and the third in the remaining three slots. Six requested copies occupy six slots. The last right edge is 185 mm and last bottom edge 145 mm, so the grid fits the stated sheet dimensions; the printer's printable area still needs its own check. A long third name must be reviewed in all three positions rather than truncated.

The intended deliverables are one editable master and one single-page PDF, with an actual-size proof instruction. This is an authored illustration only. No document was rendered, source list merged, printer queried, proof printed or physical alignment checked for this example.
