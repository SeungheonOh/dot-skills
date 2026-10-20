---
name: assess-labeling-agreement
description: "Compare two existing categorical annotation sets on matched ordinary-material items. Deliver coverage, a disagreement cross-tab and appropriately qualified agreement statistics while preserving original judgments and separating consensus from independent agreement."
---

# Assess agreement between labelers

Return a checked comparison of supplied judgments, including where they differ and what the comparison can establish. A single agreement percentage is not enough when unmatched items, changing category meanings or concentrated disagreements affect its interpretation. For a small set, a cross-tab, item-level disagreement list and short explanation may suffice.

Use [design-classification-scheme](../design-classification-scheme/SKILL.md) to create or revise the categories, [evaluate-probability-predictions](../evaluate-probability-predictions/SKILL.md) to score probabilities against known outcomes, and [analyze-data-question](../analyze-data-question/SKILL.md) for broader analysis. This workflow compares two categorical annotation sets; it does not assume either is truth, rank employees or authorize consequential judgments about people.

## Define the comparison

Read the source annotations, item definitions and applicable codebook. Establish the annotation unit, relevant source version, labelers or systems, labeling round and question. One judgment about a document is not interchangeable with one judgment about each sentence.

Check whether the judgments were made separately or after discussion, assistance or exposure to the other set. Preserve that distinction even when the numbers can still be computed. Agreement after adjudication measures a different process from agreement between original judgments.

Identify whether each item receives one nominal category, an ordered category, several simultaneous labels or a continuous value. Do not apply a single-label nominal calculation to other structures by silently choosing one label, concatenating arbitrary sets or binning numbers. Use a method appropriate to the requested structure or return the supported comparison and the unresolved method choice. More than two raters requires an explicitly suitable design; a collection of pairwise kappas is not automatically one overall reliability estimate.

## Pair records without changing their meaning

Match by stable item identity, source revision and annotation round, not row position or similar text alone. Preserve the original records. Reconcile duplicate item/labeler keys using a supported version rule; repeated judgments must not inflate the number of independently annotated items.

Keep the eligible set, items present in each annotation set and the jointly usable set distinguishable. Report unmatched, missing, invalid and excluded records with reasons. Unknown or unfinished annotations are not agreements, disagreements or a substantive category unless the codebook explicitly defines that category. Do not manufacture a pair by filling a missing label with the other labeler's choice.

Check category identities and codebook versions before joining label values. Apply documented aliases consistently, but do not merge categories merely to raise agreement. A semantic change requires an explicit mapping or separate comparison; the same displayed word can refer to different rules.

Define the analysis cohort before calculating its summary. A complete-pair comparison describes that cohort, not automatically all eligible items. If difficult items are disproportionately unpaired, retain that coverage limitation beside the result.

## Make the disagreements visible

For single-label nominal annotations, build a count cross-tab with labeler A's categories as rows and labeler B's as columns, using one explicit common category order. Include categories observed on either side. A library's label-subset option must not silently remove disagreements.

Show row totals, column totals and the number of paired items. Link off-diagonal cells to the corresponding item references when the requested handoff permits it. Keep counts even if a normalized view is useful; row, column and overall percentages have different denominators.

The [scikit-learn confusion-matrix reference](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html) documents axis ordering, label selection and normalization options. If using that function for two annotation sets, label the axes with the actual labelers rather than claiming that its parameter names establish ground truth.

Inspect material disagreement patterns against the source items and codebook when that review is requested. Distinguish inconsistent use of a category boundary, unavailable evidence and genuinely ambiguous material. Do not declare one labeler wrong solely because the other disagrees, or silently replace original labels with the reviewer's preference.

## Calculate a suitable summary

For an unweighted paired cohort of N items, raw agreement is the diagonal count divided by N. If N is zero, there is no agreement rate.

When Cohen's unweighted kappa is appropriate, calculate `kappa = (p_o - p_e) / (1 - p_e)`. Here `p_o` is raw agreement and `p_e` is the sum, across categories, of the product of the two labelers' marginal proportions. Retain those marginals. The [scikit-learn kappa reference](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.cohen_kappa_score.html) defines this two-annotator statistic and distinguishes category-distance weighting from sample weights.

When `p_e = 1`, kappa is undefined; preserve the reason rather than replacing it with zero or one. Raw agreement may still be defined. Record the library version and any undefined-value convention, and prevent a display or export default from concealing this case.

Use ordered-category weighting only with a justified category order and stated disagreement-cost rule. Numeric label codes do not themselves establish meaningful distances. Supplied item weights require a consistent weighted cross-tab, marginals and agreement calculation; keep ordinary item counts separate and explain what the weights represent. Do not confuse weighted kappa's disagreement penalties with weighting the sampled items.

Report raw agreement and category distributions alongside kappa. Its marginal adjustment is a defined reference model, not evidence that the labelers actually guessed randomly. Different category mixes can change the statistic, so do not interpret a score difference across cohorts as a demonstrated improvement in the labeling process. Avoid universal quality labels or acceptance thresholds unsupported by the task.

Agreement does not establish correctness: two labelers can share the same mistake. Accuracy requires an independently justified reference and a separate comparison. If intervals are requested, use a method appropriate to the sampling and dependence structure; keep each item's paired judgments together and account for clustered items. Do not treat every sentence from one document as an independent replicate merely because it occupies its own row.

## Preserve original and resolved judgments

If adjudication is also requested, save the original pair, resolved label, rationale and relevant codebook version separately. Recompute an after-resolution summary only as a distinctly labeled result. It cannot replace the initial agreement evidence.

A proposed rule clarification does not retroactively prove that the initial labels followed that rule. Preserve which items and rounds used each version. Fresh independently obtained judgments can answer a later reliability question; an editor's corrections to the existing pairs cannot impersonate them.

Stop at the authorized comparison and any explicitly requested adjudication. Do not contact labelers, change live annotations, train a model or publish source material merely because the analysis identifies useful next steps.

## Verify and deliver

Check that the cross-tab total equals the paired denominator, marginals equal the corresponding source-label counts, and diagonal plus off-diagonal counts reconcile. Trace a few disagreements back to exact source records rather than trusting a plausible aggregate.

Check the implementation against transparent cases when execution is part of the task: identical nonconstant labels, a known disagreement table, an empty intersection and both sets assigning only the same category. Swapping the two labelers should transpose the cross-tab while leaving unweighted raw agreement and kappa unchanged. Renaming categories consistently on both sides must not change those statistics.

Deliver the actual comparison, coverage reconciliation, disagreement references and meaningful interpretation limits. Retain enough method and source-version information to recompute it. Reopen saved outputs and check category names, axis orientation, denominator and undefined values. Distinguish source inspection, calculations and any human review; report only work actually performed.

## Fictional, unexecuted illustration

Two labelers classify 100 fictional documents as Routine or Exception. The paired counts are 90 Routine/Routine, 5 Routine/Exception, 5 Exception/Routine and 0 Exception/Exception.

Raw agreement is `90/100 = 0.90`. Each labeler uses Routine 95 times, so `p_e = 0.95² + 0.05² = 0.905`, giving kappa `-0.005/0.095`, approximately `-0.0526`. Reporting only “90% agreement” conceals that none of their Exception judgments coincide. The negative kappa does not establish that either labeler is inaccurate.

If both labelers instead assign Routine to every paired document, raw agreement is 100% but kappa is undefined because `p_e = 1`. An additional item missing one judgment belongs in coverage reporting, not the paired table. These are authored arithmetic examples, not executed annotation studies or measured skill effectiveness.
