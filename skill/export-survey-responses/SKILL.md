---
name: export-survey-responses
description: Prepare a portable handoff of collected questionnaire responses while preserving instrument versions, coded choices, branch-related missingness and repeated answers. Use when moving survey results between tools, not designing questions, analyzing findings or certifying anonymity.
---

# Export survey responses without changing their meaning

Deliver response data that another analyst can interpret with its actual questionnaire and export settings. Preserve what a respondent answered separately from what a platform exported or inferred. A rectangular table alone cannot establish that every blank means the same thing.

Use [design-questionnaire](../design-questionnaire/SKILL.md) for deciding what to ask, [document-dataset-fields](../document-dataset-fields/SKILL.md) for a dictionary-only request, and [analyze-data-question](../analyze-data-question/SKILL.md) for findings or statistical comparisons. This workflow produces a bounded response-transfer package, including the instrument-specific mapping needed to retain meaning.

## Establish the handoff contract

Inspect the actual supplied export and available instrument definitions. Identify:

- Survey/form identity, collection versions, export time, selected response population and applied filters
- Source files, export settings, question and choice identifiers, labels, code mappings, branching and repeated-group definitions
- The receiving tool or team, requested table/file format, required fields and permitted exclusions
- Whether the request ends with a private file or includes an authorized download, upload or destination import

Prefer the source platform's native export when it already satisfies the request. Convert only the parts that prevent the intended use. A common portable result is UTF-8 response tables plus a compact versioned question/choice map and a transfer note. Add repeat tables or answer-state columns only where the instrument needs them. Do not force a short, flat questionnaire into a sprawling normalized database.

If the instrument or export settings are missing, preserve the uninterpreted values and list the specific unresolved meanings. Do not invent option labels or infer why a response is blank. A supplied file establishes its own coverage; it does not establish that all account responses, unfinished sessions or historical fields are included.

Keep the source snapshot unchanged. Do not edit live questions, recode values, alter survey logic, close sessions or delete test responses to improve an export. Use only approved fields and audience. Names, email addresses, IP addresses, location, free text and attachment metadata can expose respondents. Pseudonymous IDs do not establish anonymity, and removing direct names does not authorize publishing the remaining data.

## 1. Freeze instrument and export versions together

Record the exact source files, their version/date and the selected population. Preserve any multi-row headers, field IDs and import metadata as source evidence before constructing a simpler analysis table. Separate actual response rows from platform header rows, totals or notes; count them using the documented export layout rather than guessing from nonempty lines.

The [Qualtrics dataset guide](https://www.qualtrics.com/support/survey-platform/data-and-analysis-module/data/download-data/understanding-your-dataset/) documents three header rows in its CSV/TSV exports, response rows that need not represent different people, response-type metadata and distinctions between completion fields. These are provider-specific facts, not assumptions for every survey file. Inspect the producer and export version actually supplied.

Bind answer codes to the question and instrument version that give them meaning. Preserve a source question ID, subquestion ID and choice ID when available; keep editable question numbers and human labels separately. A repeated label is not a durable identity. If a platform reused an ID or changed a label's meaning, keep the affected versions separate until an explicit crosswalk is justified.

Do not treat today's instrument as proof of what every respondent saw. Identify whether labels and coding came from the collection-time version, the export-time configuration or an unknown revision. If historical wording is unavailable, mark that uncertainty in the handoff instead of reconstructing plausible questions.

Keep response identity distinct from person identity. Several submissions may belong to one person, while anonymous submissions may have no reliable respondent link. Do not deduplicate by name, contact address, timestamp or identical answers. Preserve source response/revision identifiers and apply a latest-response or repeat-attempt rule only when the request defines it.

## 2. Preserve survey-specific answer states

For each affected question, define the distinction the source actually supports. Possible states include answered, shown but unanswered, not shown by routing, not reached, explicit not applicable and unknown absence. These are meanings to substantiate, not a mandatory list of codes to invent.

Use an explicit source marker or exposure evidence before assigning a branch-related state. A blank answer and the final value of an earlier question may not reveal the full route: the respondent may have changed an answer, exited early or been shown randomized options. If the evidence cannot distinguish these cases, retain the blank with an unknown state. Keep any inactive retained answer separate from a current answer only when source evidence establishes that distinction.

Record export recoding and value/label settings. [Qualtrics export options](https://www.qualtrics.com/support/survey-platform/data-and-analysis-module/data/download-data/export-options/) include values versus labels, splitting multi-value choices into columns, and configurable markers for shown-but-unanswered questions. Recode values can change before a later export. Preserve the actual settings and mappings instead of treating a familiar number such as `0` or `-99` as universal missingness.

Do not turn an explicit zero into missing, an empty text answer into a chosen “none,” or an export marker into a numeric response. Retain the raw source value alongside its interpreted state when the mapping is consequential. State fields must have their own documented meanings and must not collide with legitimate answer codes.

Keep completion, response type and eligibility separate. Apply an agreed inclusion rule to preview/test/imported/partial responses without deleting them from the source. A platform's finished flag does not by itself establish a fully answered instrument, a qualified participant or a representative sample. Report the excluded population by reason and count without copying unnecessary private records into the transfer note.

## 3. Carry repeated and structured answers correctly

Map each actual question type deliberately:

- **Single choice:** retain the selected code and its versioned label mapping. Preserve unfamiliar codes as unresolved rather than assigning the closest label
- **Multiple selection:** preserve the chosen option identities and the overall question state. Use a documented repeated-answer table, an unambiguous encoded list, or explicitly mapped option columns. Never split choice text on commas when commas may occur inside a label
- **Option columns:** distinguish a known unselected option from an unanswered or unexposed question when the source supports that distinction. An all-zero row must not silently claim a completed selection when exposure or response state is unknown
- **Ranking:** carry the supplied item identity and rank separately. Do not infer preference from source column order, displayed random order or list order. Preserve ties and incomplete rankings if allowed; do not renumber them to make a neat sequence
- **Matrix questions:** retain the matrix row/subquestion as well as the selected scale value. A label shared across rows does not make them the same measure
- **Repeated groups:** retain parent response, repeat occurrence and nesting. Keep repeated identical answers as separate occurrences; avoid multiplying two independent repeat groups through a Cartesian join
- **Other text and attachments:** keep text tied to its actual question/choice. Include files only when required and authorized; preserve approved attachment references without activating download links or treating filenames as identities

The [ODK Central submission documentation](https://docs.getodk.org/central-submissions/#downloading-submissions-as-csvs) describes root and repeat join tables, attachment folders, filtering and an option to include previously deleted fields. When using such an export, preserve its actual parent joins and version coverage. Do not flatten it into one row per person merely because that is a convenient spreadsheet layout.

Preserve exact identifiers and literal free text. For timestamps, retain documented timezone and distinguish collection, submission, last-interaction and export times. A date-only answer is not an instant. Do not recalculate durations, scores, weights or reverse-coded scales during a transfer unless requested under a defined analysis contract.

## 4. Write the portable package and inspect saved values

Choose a serialization the receiver supports. For CSV, document encoding, delimiter, quoting, header layout and how missing states are represented; use a real serializer rather than concatenating values. [RFC 4180](https://www.rfc-editor.org/rfc/rfc4180.html#section-2) documents common quoting and record conventions, not the survey's value meanings. Do not assume CSV stores types or has a universal null marker.

If a spreadsheet review copy is requested, preserve IDs and formula-looking text as literal values through the writer's text API. CSV quoting alone does not prevent spreadsheet formula interpretation; [OWASP's CSV injection guidance](https://community.owasp.org/attacks/CSV_Injection) describes that risk and the limitations of escape-based remedies. Provide a checked literal-text workbook or explicit text-import guidance when spreadsheet viewing is intended. Keep any protective display encoding separate from the untouched machine values and describe it; do not silently prefix or alter canonical responses.

The compact transfer note should identify the source snapshot, selected population, instrument/export versions, file roles, keys and versioned code maps. Record intentional exclusions, unresolved meanings and any loss accepted by the user. Do not reproduce full respondent free text merely to illustrate the schema; use a fictional example.

Reopen the saved output with the chosen reader and compare the transfer against the frozen source:

1. Every in-scope response occurrence is present once or explicitly held/excluded under the agreed rule
2. Every selected question, subquestion and repeat maps to its correct instrument version, response and parent
3. Codes, labels, multiple selections, ranks and answer states retain their established meaning
4. Unicode, literal text, long or leading-zero IDs, commas/newlines and null/empty/zero distinctions survive the serialization
5. Counts reconcile separately for responses, question answers and repeat rows; no join has multiplied responses
6. The delivered files and notes contain only the approved fields, with attachment and contact-data exclusions checked

Choose a few consequential cases from the real instrument: changed question wording, a skipped branch, an unanswered multi-select, an explicit zero, a repeated group or an incomplete ranking. A paper walkthrough is a mapping check; successful parsing is a serialization check. Neither establishes that a destination platform imported the package correctly. Do not import into a live survey or activate a connected refresh merely to obtain that claim.

## Recovery and completion

- **Instrument/code mapping is missing:** retain raw values, qualify the affected interpretation and ask for the exact version or export settings
- **Versions conflict:** separate the affected records or columns; do not merge them under one apparently stable label
- **Source export omitted fields or rows:** identify its filters/options and request or perform only the already-authorized bounded re-export; do not automatically download every field and attachment
- **Receiver coerces or drops data:** preserve the failed candidate, use a truthful supported representation or disclose the incompatibility, and repeat saved-file comparison
- **An authorized import has an uncertain result:** inspect destination counts and source IDs before retrying; a second append may duplicate responses

Return the actual transfer files, concise interpretation note, included/held/excluded counts and checks performed. Stop when the agreed response-transfer contract is met or a named unresolved meaning prevents it. Do not describe the result as statistically valid, anonymous, population-complete or destination-verified without the separate evidence those claims require.

## Fictional illustration, not executed

A four-response workshop survey asks which sessions were attended. Its documented export uses separate option columns and a distinct marker for shown-but-unanswered questions. Two responses contain selected session codes, one has the unanswered marker, and one has no answer with no exposure evidence. The last response also contains two repeated feedback items.

The proposed package preserves four response occurrences, distinguishes the documented unanswered state from unknown absence, and carries the two feedback items with their parent response and occurrence order. It does not replace both missing states with “attended none,” count the feedback rows as additional people, or claim the supplied labels match an earlier instrument version without evidence.

This illustration was authored, not executed. No response export was downloaded, private data processed, file generated or survey modified by the example.
