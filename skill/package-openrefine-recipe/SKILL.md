---
name: package-openrefine-recipe
description: "Package an existing OpenRefine cleanup as reusable operation-history JSON with import prerequisites, row/record and facet scope, non-replayable steps and checked fresh-project replay. Use for a transferable transformation recipe, not a one-off cleaned spreadsheet, reconciliation service setup or unattended scheduling."
---

# Package an OpenRefine transformation recipe

Turn an established cleanup into a recipe another person can apply to the next compatible input. Carry the recipe's starting state and selection semantics with its native operations. A history export is not automatically a complete or portable reproduction of everything someone did in a project.

Prefer extracting supported operations from the existing authorized project rather than inventing opaque operation objects. If only a proposed process is supplied, create a reviewable specification or candidate and label it untested; do not fabricate an extracted-history claim.

## Inputs and delivery boundary

Establish:

- The source project's identity, current history position, OpenRefine version and relevant installed extensions
- The input format, import settings and accepted column/type/record structure at the recipe's starting point
- The selected history interval, desired transformation rules and a small representative or fictional input
- The expected output schema, preserved fields, row/record accounting and export format
- The delivery destination and audience; whether only a recipe, a sample result or a full project archive is requested

Inspect the current project and supplied evidence without disturbing its history. Use a separately created or restored rehearsal project for authorized replay. When only a history JSON and sanitized data are available, analyze those and state what the missing original project prevents verifying.

Deliver native operation-history JSON plus a concise usage contract: compatible input/import settings, ordered operation meanings, unsupported/manual steps, exact replay start point, export scope, recovery procedure and observed verification limits. Include a small approved sample and expected result only when useful. A project archive is an optional restoration artifact, not a default public attachment.

## Preserve the baseline and minimize disclosure

Retain the original input bytes and a usable pre-recipe project state before applying transformations. For a real project, a supported archive can preserve data and history; a CSV export does not preserve the entire project. OpenRefine's [history guidance](https://openrefine.org/docs/manual/running#history-undoredo) explains history restoration and the loss of later redo steps when a new operation is made after going backward. Do not use the user's active project as a disposable reset mechanism.

Project history and archives can contain values that have disappeared from the current grid. The operation recipe can also contain literal corrections, URLs, expressions, column names or service details. Inspect the actual package for private material; do not assume a data-free JSON filename means it is safe to share. Keep full archives local to the authorized destination unless the user approved their contents and recipient. Sanitizing values can change behavior, so verify a sanitized recipe as a separate candidate rather than silently editing the original evidence.

Keep this workflow local. Statically inspect every expression's language and possible file, process, network and cross-project effects before preview or replay. OpenRefine includes Jython and Clojure as well as GREL; an expression preview evaluates code rather than merely displaying it. See the [expression-language guidance](https://openrefine.org/docs/manual/expressions). Do not assume an expression is inert because it needs no extension or runs against fictional data. Hold unknown or unapproved effects, including reconciliation, URL fetching and export/upload actions, until their data, target and authority are established. Never preview code to discover whether it has side effects. Do not expose the local server on another interface, change security settings or install an extension as part of packaging.

## Reconstruct the recipe's actual starting state

Capture the import recipe separately from the transformation history: encoding, separator, header rows, ignored leading/trailing rows, quoting, blank handling and number/date inference that materially changes values. Preserve identifiers as text when their lexical form matters. A correct operation applied after a different import can produce a different dataset.

Record exact column names, required types and whether blanks, nulls and error cells have distinct meanings. Include the expectations that affect applicability, not an unnecessary full schema framework. New rows within that contract can be normal; renamed columns, changed units or a newly ambiguous date convention are a compatibility hold.

Establish rows versus records at the starting point and at operations that change structure. In OpenRefine, a record may span multiple rows, and its first-column/blank-cell structure matters; rearranging that key column can change grouping. See [rows and records](https://openrefine.org/docs/manual/exploring#rows-vs-records). Keep a stable source identifier or private lineage map for reconciliation without accidentally inserting a new first column that changes record boundaries.

Distinguish display state from data state. Temporary sorting, current page, facet selections and permanent row reorder are not interchangeable. Record the full population and the selected population used by each consequential operation. A row index in one imported project is not a stable business ID for another batch.

## Extract and inspect a coherent operation sequence

Use the supported history extraction interface for the chosen interval, save its exact JSON and record the history state it describes. OpenRefine permits selecting operations for extraction, but some changes, such as individual cell edits, are not reusable this way. See [reusing operations](https://openrefine.org/docs/manual/running#reusing-operations). Compare the extracted sequence with the intended cleanup and retained history; list omitted or non-extractable steps rather than claiming complete reproduction.

For each operation, capture the fields that determine meaning:

```text
sequence | native operation type | source/target columns | expression or rule
         | row/record mode | selection/filter scope | expected structural effect
         | prerequisite | portability or manual-step hold
```

Do not rearrange operations simply because they mention different columns. A prior rename, split, sort, fill, deletion or type conversion may establish the later operation's input. If selecting only part of the history omits such a prerequisite, either include the needed authorized steps or define the intermediate starting state explicitly. Do not silently assume the next user has it.

Inspect stored selection configuration, such as `engineConfig` when present, including mode, facets, selected values and expressions. A filter accidentally limited to last month's category is part of the behavior, even when the transformation expression is correct. Do not strip selection fields to “make it reusable”: choose an evidenced all-row or bounded-selection rule and prepare a revised candidate if that is the intended meaning.

Classify operations as reusable under the input contract, batch-specific, non-extractable or dependent on unavailable capabilities. Individual corrections tied only to a row number need a supported identity rule before they can become reusable. A manual decision is an explicit stop with instructions and evidence, not a guessed replacement. Preserve unknown native fields until their meaning is established; do not rewrite a newer operation type into a familiar older one.

Specify error behavior and preservation for expressions: whether invalid inputs remain unchanged, produce a separate error column or block completion. Preview representative null, empty, unexpected-type and unknown-category values where permitted. Do not convert errors to empty strings merely to make the export look clean. The recipe should apply already-approved meaning rules; it does not invent a locale or duplicate-survivor policy.

## Replay against a fresh compatible project

When application use is authorized and available, import an approved sample into a separate project with the recorded settings. Verify the precondition counts, types and record boundaries, then apply the saved operations through the supported interface. Use a complete coherent sequence, with explicit pauses for retained manual steps.

Check actual saved values and source-to-output coverage, not only the success banner or history count. Trace a changed value, an unchanged value, an excluded value and a meaningful exception. Reconcile row/record counts across splits, joins or removals; preserve separate accounting for rows and records. For a supposedly non-structural cleanup, the source population and order should remain intact unless another rule says otherwise.

Use a second compatible sample containing a new valid value or different row order when that can expose batch-specific assumptions. This is a transfer check, not proof over every future input. Test a known incompatible header or unsupported category as a held case without applying destructive operations. Do not require the recipe to be idempotent unless that is part of its contract: adding a column or splitting rows can be correct once and wrong when repeated on the already-transformed project.

Export according to the declared complete-versus-filtered scope and verify the saved artifact. Many OpenRefine export formats use current facets/filters, while a project archive includes broader data and history; see [export options and scope](https://openrefine.org/docs/manual/exporting). Clear or set view filters deliberately for the requested export, recording that step separately if it is not encoded in the operation recipe. Reopen the exported file and check identifiers, types, missing values and intended population.

When execution is unavailable or forbidden, finish the native JSON inspection, prerequisite map and concrete acceptance cases. Report replay, consumer export and recovery as not run. Static JSON validity does not establish engine acceptance or correct cleanup.

## Acceptance, interruption and handoff

The packet is ready for its stated level only when:

- Its exact operation sequence and required start state agree; omitted manual/non-extractable steps are visible
- Column, import, row/record and selection assumptions are explicit and meaningful
- Private values and network-dependent operations have the appropriate scope and holds
- Observed replay and saved export checks, if performed, support the claimed output; unperformed stages are named
- The next batch begins from a fresh compatible input, with a clear hold on incompatible schema or meaning

After interruption or an ambiguous apply response, inspect current history and data before retrying. Do not paste the whole JSON again because the interface stopped responding. If the completed prefix cannot be established reliably, preserve the partial project for diagnosis and restart in a separate fresh project from the retained input, within the same authorization. Keep a partially exported result clearly separate from the accepted output.

For a requested rollback, use the preserved baseline or supported history in the rehearsal project after checking for later work. Do not rewind the user's active project or erase its redo branch as automatic compensation. Report the operation boundary reached, affected project identity and smallest missing fact.

## Fictional, unexecuted example

A supplied row-mode catalogue has columns `item_id`, `status` and `note`. Its approved rule trims outer spaces from `status` for every row and changes exact status `in stock` to `available`; it leaves all other values, IDs and notes untouched. The sample rows contain `001 / in stock`, `002 / reserved` and `003 / preorder`.

The expected output statuses are `available`, `reserved` and `preorder`, with all three IDs and their order preserved. A source history exported while a stored facet selects only `reserved` would not implement that all-row rule. The packet must expose and correct that scope in a candidate rather than call extraction complete. A single-cell correction to a note is excluded and documented as non-replayable; it cannot be silently represented by its row position on next month's file.

Expected replay starts with a fresh import. Reapplying the recipe to an already-transformed project is not the transfer test. These are authored expectations only: no OpenRefine project, expression, history extraction, replay or export was executed for this example.
