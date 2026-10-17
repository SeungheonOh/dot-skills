---
name: build-controlled-input-workbook
description: "Create a reusable spreadsheet template that contributors can fill and return, with explicit editable fields, stable record IDs, input rules and visible completion checks. Use for structured data collection, rather than forecasting, cleaning completed data or building an online form."
---

# Build a Workbook People Can Fill Correctly

Deliver the requested editable workbook with a clear entry surface and a dependable way to identify incomplete or invalid returns. The useful result is a contributor-ready template, not just a field list or a sheet that looks protected. Use the available spreadsheet authoring guidance for the actual file or native-sheet work.

Use [build-spreadsheet-model](../build-spreadsheet-model/SKILL.md) when the main job is calculating planning outputs. Use [validate-dataset](../validate-dataset/SKILL.md) to assess an already completed dataset. This workflow designs the collection artifact, including what a blank template, a partially completed row and a usable return mean.

## Establish the collection boundary

Read the supplied template, field definitions and example returns first. Resolve only missing decisions that change what contributors must enter:

- What does one row represent, and are contributors completing a preissued roster or adding new records?
- Which fields are entered, prefilled reference data, or calculated? Which are required, conditional or optional?
- What values, units, date interpretation, code lists and missing-value meanings are actually established?
- Which application/file format will contributors use, how many rows are expected, and must they add rows, sort, filter or paste blocks?
- Who can see the output, where should the template be saved, and is the task preparing a file or changing a named existing workbook?

Reuse existing conventions. Do not invent mandatory fields, numerical limits, collection purposes or recipients. When a consequential rule is missing, expose it as a proposed rule for the owner instead of treating the current sample as the complete set of allowed values. Complete the supported portions.

Keep the file private within the authorized destination. Preparing a template does not authorize distributing it, inviting contributors, changing their access, scheduling reminders or collecting additional personal information. Do not embed real completed returns as examples. A template copied from a previous collection can retain private values in hidden sheets, notes, names or caches; prefer a fresh minimal artifact when preservation is not required.

## 1. Turn field definitions into an entry contract

Create a compact field map inside the workbook or its existing instructions. For each applicable field, record its exact header, meaning, stored type, unit, required condition, allowed inputs and error message. Keep the map readable; a small form does not need a separate specification file.

Separate these cases before implementing rules:

- A text identifier such as `00042` is not a number. Long IDs must retain all digits
- Zero is an entered value. Blank can mean not yet provided; not applicable or unknown needs the agreed explicit representation
- A date-only field is different from an instant. An ambiguous date string needs the supplied locale, not a guess
- A field can be required only when another field has a particular value. An invalid or absent controlling value must leave that dependent check unresolved, not silently satisfied
- A dropdown displays an allowed vocabulary. It does not establish that the selected statement is true

Decide how a row enters the expected population. For a preissued roster, every supplied record remains expected even when its entry fields are blank. For an appendable table, unused template space is not an incomplete record; define the small set of fields that activates a row, and make any partly entered row visible. Do not rely on a formula-filled status column to decide whether a record exists.

Assign stable text record IDs where the collection needs later returns or corrections. Preserve existing IDs. Do not use current row numbers as identity, or an ID formula that changes after sorting. For concurrent entry, use a supported unique-ID mechanism or preallocated IDs; do not promise that copied formulas prevent collisions.

## 2. Build the smallest practical entry surface

Keep one clear header row for the record table, with no merged cells or decorative subtotal rows inside its editable data region. Identify input fields with labels and consistent formatting rather than color alone. Put units in headers or nearby instructions. Freeze useful headers, fit meaningful values and make the required input sequence easy to follow.

Separate reference values and formulas from contributor inputs. In an existing workbook, inventory relevant tables, formulas, names, validation, protection, notes, hidden content and external connections before editing. Preserve unrelated features and user entries. Do not rebuild a macro-enabled or connected workbook through a writer that silently removes required features. Do not execute macros or refresh connections to prepare the template.

Use native validation for the established entry rules when the selected tool and application support it. Include a short input hint and a specific error, such as “Enter a whole number of units, including 0,” rather than “Invalid value.” Choose reject-versus-warning behavior deliberately; a warning that can be accepted is not a hard restriction. Keep code lists maintained in one clearly identified place, and specify how a new legitimate code is requested.

Apply supported edit guards to reference and formula areas within the requested scope while leaving all required input cells editable. Do not add passwords or change collaborator rights as a side effect. Explain any feature that the available writer cannot actually implement; cell color or a “locked” label is not enforcement.

Worksheet protection is an edit guard, not confidentiality. [Microsoft's Excel guidance](https://support.microsoft.com/en-us/excel/protection-and-security-in-excel) distinguishes those purposes. [Google's protection guidance](https://support.google.com/docs/answer/1218656) likewise warns that protected spreadsheets can still be copied or exported. Do not place confidential reference data in a contributor file and rely on hidden or protected cells to withhold it.

## 3. Make usable-return checks independent of dropdowns

Add concise row-level checks for missing required input, invalid types/codes, duplicate IDs and relevant conditional rules. Include a count or list of affected record IDs so the user can find the problem. Keep known zero separate from blank and use text statuses alongside any conditional formatting.

Validation alone is insufficient: [Microsoft documents](https://support.microsoft.com/en-gb/excel/more-on-data-validation?nochrome=true) that copy/fill operations can avoid entry alerts, and adding validation does not automatically flag existing invalid data. Check the actual stored values again. Include the expected type, not just a numeric-looking display, where coercion would change meaning. Formula-looking contributor text must remain literal data; do not construct formulas from it.

Define completion narrowly. “No input issues found” means the documented checks passed on the expected rows. It does not mean a person submitted, reviewed or approved the return. Keep any requested contributor declaration or reviewer decision as its own blank editable field with an evidenced actor/date when actually supplied.

For an appendable collection, make row extension part of the design: either a supported table expansion or an explicitly bounded entry range. New rows must inherit required checks and formatting without overwriting calculated columns. Do not imply unlimited capacity when rules cover only a fixed range. Keep summaries tied to the actual intended record set, including filtered-out records when they still belong to the return.

## 4. Exercise the contributor actions in a disposable copy

Before delivery, verify the saved artifact through the supported authoring and consumer tools. Use a separate check copy, then deliver the requested blank or legitimately prefilled state. Choose probes that could expose a real failure:

1. Enter one valid row, then leave a required field blank. The row must move from usable to incomplete without converting the blank into zero
2. Enter an explicit zero and a text ID with leading zeros. Read back their underlying types and exact values
3. Try a bad dropdown value by typing and by pasting. Record actual rejection behavior and confirm the independent check still exposes an invalid stored value
4. Change the controlling field for a conditional requirement. Check both applicability and missing-controller behavior
5. Exercise the requested next-row, sort/filter and paste operations. IDs, notes and validations must stay with the correct records; formulas must remain intact
6. Attempt an edit in a guarded formula/reference area through the intended application, while confirming input cells remain editable

Check first, middle and last covered rows, not just the first example row. Recalculate and inspect applicable formulas, review the layout at normal size, save, and reopen. State which engine was used and what could not be exercised. Static formula/validation inspection does not establish native edit-blocking behavior.

Remove only the temporary test inputs, restore the intended delivery state and read it back. A blank collection should show “No records entered” or the expected incomplete roster, not a fabricated complete return. Confirm no fictional demonstration records contribute to production totals or remain in the contributor data table.

## Deliver and recover

Return the actual editable template or verified authorized sheet link, its entry instructions, version/collection identifier and meaningful checks performed. Identify any unimplemented guard, untested consumer behavior or unresolved field rule. Keep a usable template distinct from a completed collection.

If protection or validation cannot be preserved, keep the original unchanged and report the affected behavior; do not silently return an unguarded replacement as equivalent. If an existing native destination changed during preparation, reread and preserve the newer edits before applying a narrow authorized update. After an uncertain write, inspect the destination before retrying. Do not distribute the file to a new audience to work around a save failure.

## Illustration: fictional and unexecuted

A studio requests an XLSX for departments to report equipment needs. Each issued row has a text `request_id`; contributors enter a whole-number quantity, a supplied priority code and a reason only for priority `urgent`. Quantity zero means no equipment is requested, while blank means the department has not answered.

The template would retain issued ID `00042`, leave quantity blank, and expose the missing answer. Entering 0 with `normal` would satisfy those field rules. Pasting `soon` into the priority field would remain an input issue even if the application's entry alert were bypassed. Changing the priority to `urgent` without a reason would make the row incomplete. None of these states would mean the department or procurement team approved a purchase.

This authored illustration was not executed. No workbook, validation control, protection setting, application behavior or collection was tested by the example.
