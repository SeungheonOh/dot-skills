---
name: select-record-review-sample
description: "Select a reproducible subset of real records for manual review from a defined eligible frame. Preserve selection units, strata, probabilities and unavailable-item outcomes without presenting targeted examples as a representative sample."
---

# Select records for review

Deliver the actual selected records or stable record references, together with enough selection information to reproduce and interpret the draw. A proposed sampling method alone is not a completed selection. Keep a small request small: a selected-ID list and a concise method note may suffice.

Use [validate-dataset](../validate-dataset/SKILL.md) to check records against rules, [analyze-data-question](../analyze-data-question/SKILL.md) to interpret observed outcomes, and [design-quantitative-experiment](../design-quantitative-experiment/SKILL.md) to assign experimental conditions. Sampling existing records is different from random treatment allocation, creating synthetic records or certifying an audit.

## Define what the selection is for

Read the review request, source definitions and available records. Establish the intended population, period, selection unit, review purpose and practical limit. Selecting support tickets, customers or individual messages produces different review opportunities even if they come from one export.

Distinguish a probability sample intended to support population analysis from a targeted set chosen to expose difficult cases. Both can be useful. Do not call the highest-value, most recent, suspicious or easiest-to-open records random. If both are requested, maintain separately labeled selections; a diagnostic supplement must not silently enter the probability-sample denominator.

Use the requested count when the task is simply to select that many records. If a precision or assurance claim drives the count, establish a suitable design and sizing basis first rather than inventing a universal percentage or minimum. A capacity-limited review can still proceed with its limitation stated. More records do not repair an unknown or biased frame.

## Freeze the eligible frame

Identify the actual snapshot or version, eligibility rule and record identity. Reconcile source occurrences, distinct selection units, exclusions and the resulting eligible count. Preserve the original data and the reason for each material exclusion.

Inspect duplicate keys before drawing. If the unit is a ticket, several messages belonging to that ticket must not give it several chances of selection. Conversely, equal displayed names need not identify the same unit. Retain a source locator separate from the business key when necessary.

Read beyond previews and retrieval caps before describing the frame as complete. A query, export or paginated read must have a defined boundary; mixing pages from changing populations can invalidate the frame. Use an authorized stable snapshot where available. If completeness cannot be established, identify the bounded supplied set and restrict claims to it.

The [Statistics Canada selection overview](https://www150.statcan.gc.ca/n1/edu/power-pouvoir/ch13/sample-echantillon/5214900-eng.htm) distinguishes the target population, accessible frame and selection/analysis units. State material omissions explicitly: random selection from an accessible subset does not establish coverage of records that never entered it.

Retain only the fields needed for selection and review. A selected-ID handoff may avoid copying sensitive record content. Preparing the sample does not authorize sending records to new recipients or granting access.

## Fix the design before seeing review outcomes

Choose a method that fits the stated question and available frame:

- For a simple random sample without replacement, select the specified number of distinct units from the frozen eligible set
- When each defined subgroup needs coverage, use mutually exclusive, exhaustive strata based on information available before selection, with a stated allocation and an independent draw within each stratum
- If a systematic design is explicitly useful, retain its random start, ordering and interval method; periodic ordering can make it unsuitable
- If selection is purposive, record the selection criterion and keep its non-probability status visible

[Statistics Canada's probability-sampling guidance](https://www150.statcan.gc.ca/n1/edu/power-pouvoir/ch13/prob/5214899-eng.htm) explains these method distinctions. Do not relabel a convenience choice as random because the final rows were shuffled.

Reconcile requested and feasible counts before drawing. For sampling without replacement, no stratum can supply more distinct units than it contains. Handle an empty or undersized stratum explicitly: select all its eligible units and revise the remaining allocation according to a stated rule, reduce the total, or ask about the consequential tradeoff. Do not invent records or silently redistribute a required subgroup quota. An empty frame yields an empty selection with its reason, not a fabricated draw or a division by zero.

For simple random sampling without replacement, retain the inclusion probability `n / N`, where N is the eligible frame size and n the selected count. For that same design within stratum h, retain `n_h / N_h`; the inverse of a positive probability is a base design weight, not a complete nonresponse adjustment. Unequal sampling fractions require a design-aware analysis rather than automatically pooling review outcomes. Do not apply these formulas to a different design merely because its output has the same size.

Set the response to inaccessible, later-discovered ineligible or invalid records before reviewing outcomes. A preselected reserve list can support an operational replacement policy, but it does not by itself preserve the original inference. Keep the policy and any effect on probabilities or interpretation explicit.

## Draw once and preserve the selection

Use a supported sampling tool or a small appropriate calculation, not invented IDs. Record the method, tool/version, seed when applicable, frame version, stable input ordering and allocation. A seed alone does not reproduce a draw from a changed or differently ordered frame.

Save the selected identities and their source locators immediately. Retain stratum, selection stage and probability where relevant. Keep a reusable procedure only when requested or useful; a one-off selection does not need a new framework.

Do not reroll until the sample looks balanced, interesting or easy to review. If a required balance constraint was omitted, explain the design error and create an explicitly superseding selection under a corrected rule before examining outcomes, preserving the original attempt. If outcomes were already inspected, disclose that fact rather than presenting the change as preplanned.

A repeated run for reproducibility should reproduce the saved draw, not replace it with a fresh favorable one. If selection was interrupted or saving is uncertain, inspect the saved artifact and known state before starting again.

## Keep selection separate from review completion

Track selected, available, reviewed, unavailable and excluded-after-selection records separately. An inaccessible item is not a passing item and must not disappear from the selected count. Preserve the original selection and reason when a replacement is used; identify reserve records separately from the initial draw.

Do not substitute the next row, a nearby record or an easily opened item without the declared policy. If a newly discovered frame error changes eligibility or identity, assess its effect on the frame and selection before continuing the dependent claim. Correcting the source and silently keeping the old sample is not automatically valid.

This workflow ends with selection unless review is also requested. Do not invent findings, contact record subjects or begin a live operational audit to make the handoff look complete.

## Check and deliver

Reopen the saved selection and verify:

- Every selected identity exists in the declared frame and meets the stated eligibility rule
- Distinct-unit and stratum counts match the design; replacement rules have not created hidden duplicates
- Selected IDs still map to the intended source records after export, sorting or joining
- Recorded probabilities and any base weights match the actual design
- Random and targeted selections, initial and reserve records, and review outcomes remain distinguishable

Inspect the selection procedure or tool settings as well as the output. Correct counts and a plausible mix do not establish that a random draw occurred. State which checks were performed and which were unavailable.

Deliver the selected list or records, concise frame/design metadata and the material coverage limits. Do not claim guaranteed representativeness, population conformance or a confidence level merely because the draw completed. Where later estimation is requested, carry the actual design and incomplete-review information into that separate analysis.

## Fictional, unexecuted illustration

A fictional frame contains 900 ordinary tickets and 100 escalated tickets. The requested design draws 20 distinct tickets at random from each group for a 40-ticket review. The inclusion probabilities are `20/900` and `20/100`, with base weights 45 and 5 respectively. Equal sample counts do not mean the groups have equal population sizes.

One selected escalated ticket cannot be opened. The handoff still contains 40 selected tickets, with one marked unavailable; it does not replace that ticket with the next accessible row or claim 40 completed reviews. A separate request to inspect five unusually long tickets produces a labeled targeted supplement, not five additional probability-sample observations.

These are authored design and arithmetic examples, not an executed draw, observed review results or measured skill effectiveness.
