---
name: profile-a-local-csv
description: "Inspect a supplied CSV for structural errors, missing values, candidate types and distributions while preserving source values and local processing."
---

# Profile an authorized CSV locally

## When to use

A dataset needs an initial quality review before analysis, charting or import into another system.

## Required inputs

- The authorized file or text and its encoding/header/separator expectations
- Size bounds and the missing-value convention
- Requested profile scope and any fields that must be excluded from the output

## Workflow

1. Preserve the source and parse quoted records with a CSV parser that handles escaped quotes and embedded newlines. A physical line is not always a logical record. Reject malformed quotes or inconsistent widths with a useful locator.
2. Confirm or disclose separator detection. Preserve duplicate/blank headers as distinct columns using an explicit naming map; never drop them silently.
3. Count missing cells under the agreed convention. Keep numeric zero, literal NA labels, percentages and currency strings distinct. Numeric-looking identifiers may be categorical.
4. Infer numeric columns only under a strict finite-number rule and report that rule. Calculate summaries excluding missing values with stated denominators. Guard overflow in sums/ranges and constant or underflowing histogram widths.
5. Produce a bounded preview and distributions. Category values may be private even when presented only as counts; minimize exported content to the authorized scope. Do not upload a table merely because a parser service is convenient.

### Produce a profile with a denominator

Keep physical byte identity separate from logical records after parsing. Report header handling, data-row count, excluded records and normalization explicitly. Decide whether a repeated row is meaningful data or a duplicate candidate; do not deduplicate during profiling.

For each summary, include included-value count and missing-value count. Distinct-value counts use an explicit exact-text or normalized-text rule. A column’s inferred numeric shape does not override a supplied semantic role such as postal code or client ID. Keep the output bounded so a top-category list does not disclose a large private roster unnecessarily.

### Keep an interrupted profile separate from a complete scan

Record the source digest, decoder, full CSV dialect, header decision and parser/version before calculating summaries. Treat automatic header detection as a proposal: Python's [CSV documentation](https://docs.python.org/3/library/csv.html#csv.Sniffer) calls it a heuristic that can produce false positives and negatives. With Python, preserve newline handling with `newline=''`, select strict parsing where appropriate, and check widths separately; parser acceptance alone does not settle the intended table. Set file, field and record limits before expensive processing.

A preview cap must not silently become a scan cap. If only a prefix or sample is inspected, label every derived count, distribution and missingness rate with that population and the sampling rule. Do not claim global uniqueness, absence or total row count from it. On interruption, preserve the last complete logical-record boundary and stop reason; restart from the unchanged source or a verified parser-safe checkpoint. Seeking to the next physical line can start inside a quoted field. A changed source digest requires a new profile rather than appending summaries from different versions.

Reopen the saved report and reconcile its column naming map, denominators and displayed values against the inspected records. Keep formula-looking category labels literal in the chosen review format, and distinguish a shortened display from the complete category value used for counting. If a safe faithful spreadsheet representation is unavailable, use an authorized text/JSON report rather than modifying source values. Recheck the original digest and state whether the scan ended normally or remains partial.

**Fictional, unexecuted example:** A limit stops a read after 250 complete records, immediately before a quoted multiline record. The report may describe those 250 records and their observed duplicates, but cannot say the file has 250 rows or no later duplicates. A 20-row preview of a fully completed scan is different: its summaries may use the full verified population while the preview remains visibly capped.

## Output

A profile containing source identity, parse decisions, row/column counts, missingness, candidate types, anomalies and scoped summaries, with the original unchanged.

## Verification and limits

Reconcile histogram totals to included records. Spot-check quoted multiline cells, duplicate headers, zeros and empty values. Mark columns whose semantics remain unknown rather than guessing.

## Missing-input handling

If separator or encoding is ambiguous, present the bounded alternatives that change the parse. If a malformed record prevents reliable column alignment, report its logical record location and stop statistics for that parse rather than silently dropping it.

## Worked example

The fictional file has headers id,amount,note and three rows: (001, 0,"a,b"), (002,empty,"line one\nline two"), and (003, 4,NA). The second note is one quoted multiline field, not two records. The user identifies id as an identifier and defines only blank/whitespace cells as missing.

The profile has 3 data rows and 3 columns. amount has 2 numeric values, 1 missing value, mean 2, median 2 and range 0–4. Zero contributes to every numeric measure. The note value NA remains text, and the embedded comma/newline remain inside their original fields. IDs keep their leading zeros and categorical meaning.

The handoff includes the parser decisions and this reconciliation. It does not upload the rows, replace the empty amount with zero, or claim the table has only three physical lines.

## Evidence status

The worked example illustrates the stated inputs and reasoning. Unless an execution result is explicitly identified, it is not a claim that external services, real devices or user data were tested. Report actual checks and unrun stages on each use.
