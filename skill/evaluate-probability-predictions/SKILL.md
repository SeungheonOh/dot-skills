---
name: evaluate-probability-predictions
description: Evaluate supplied binary probability predictions against known outcomes with explicit comparison cohorts, proper losses, ranking metrics and reliability bins. Use for an existing prediction export; not for training a model or approving consequential decisions.
---

# Evaluate probability predictions

## When to use

Use when someone has predicted probabilities and realized binary outcomes and wants to understand their quality. Produce a reproducible scorecard and reliability view with coverage and limitations. Do not turn a descriptive evaluation into a deployment recommendation without the separate evidence and authority that requires.

## Inputs

- Stable case ID, model/version ID, probability of the specified positive class, and outcome
- Target meaning, prediction horizon and whether outcomes are mature
- Evaluation split or time/group boundary, if supplied
- Comparison population, threshold convention and requested metrics

If split independence, leakage or label quality cannot be checked, say so. Unknown outcomes are not negatives. Synthetic fixtures can test the evaluator but cannot establish real model performance.

## Workflow

### 1. Validate the prediction unit

Preserve case identity and model identity. Reject duplicate case/model pairs or reconcile them under an explicit version rule. Check that models agree on the recorded outcome for a shared case; do not let inconsistent labels silently change the comparison.

Require finite probabilities between zero and one and explicit binary outcomes. Do not coerce a blank probability to zero, “unknown” to a negative label, or a percent value into a fraction without a known unit contract. Report invalid input rather than quietly removing difficult examples to improve scores.

Check whether repeated records represent independent cases, multiple horizons or repeated observations of one entity. The same textual ID is not enough when the prediction unit differs. Keep supplied weights, grouping and timing semantics explicit; do not introduce them merely to make a metric favorable.

### 2. Set the comparison cohort before scoring

For paired model comparisons, identify the intersection of eligible case IDs and show each model's available, used and excluded counts. The intersection may change the population, so retain the coverage effect beside the scores.

Separate-cohort scores can be useful descriptively, but differences may reflect population difficulty or prevalence rather than model quality. Do not rank models as though they saw identical cases. If the common cohort is empty, return no comparable score rather than fabricating zero.

### 3. Compute metrics with their actual meaning

For binary outcomes y and positive-class probabilities p:

- Binary Brier loss is the mean of `(p-y)^2`, on the zero-to-one scale
- Binary log loss is the mean of `-log(p)` for positives and `-log(1-p)` for negatives
- ROC AUC measures ranking, giving half credit to tied positive/negative scores; it requires both classes
- Threshold classification uses a declared boundary such as `p >= threshold`, with TP, FP, TN and FN retained

Use numerically stable expressions such as `log1p(-p)` where appropriate. Decide and disclose the boundary-probability policy. Un-clipped log loss is infinite when a model assigns zero probability to the observed outcome. If a library clips probabilities, record its epsilon and do not compare that result to an un-clipped implementation as if their definitions were identical.

Keep undefined ratios explicit: precision is undefined without predicted positives; recall is undefined without actual positives; AUC is undefined with only one class. Do not replace undefined values with zero for a cleaner table. Serialize infinities deliberately because ordinary JSON numbers cannot represent them.

A lower Brier or log loss does not alone prove better calibration; these scores also reflect discrimination and the outcome distribution. AUC says nothing about whether the probabilities are numerically well calibrated. A constant observed-prevalence Brier baseline is a descriptive reference, not a deployable baseline trained independently of the evaluation labels.

### Apply supplied case weights consistently

When supplied weights are part of the question, establish what they represent: repeated frequency, sampling adjustment or a task-specific importance measure. They do not automatically describe the same population. Match weights by case ID, and use the same case weights for paired model comparisons; identical case intersections with different weights are not the same weighted comparison. Reject negative or non-finite weights. Keep zero-weight cases in coverage reporting, but exclude their contributions before evaluating the weighted loss so `0 * Infinity` does not contaminate it. This does not waive the input-validation rules. A zero total weight has no weighted mean.

For total positive weight `W`, use `sum(w * (p-y)^2) / W` for binary Brier loss and `sum(w * individual_log_loss) / W` for mean log loss, preserving the declared clipping convention. A certainty error with positive weight still makes un-clipped log loss infinite. Weighted TP, FP, TN and FN are sums of case weights; retain ordinary case counts separately. In each reliability bin, use `sum(w*p) / sum(w)` and `sum(w*y) / sum(w)`, and show both case count and weight total. A bin containing only zero-weight cases has no weighted reliability point. Do not pair weighted losses with an unlabeled unweighted calibration plot.

For weighted binary AUC, sum `w_positive * w_negative` across positive-negative pairs, awarding full credit when the positive score is higher and half for a tie; divide by the product of total positive-class and negative-class weights. Either class having zero total weight makes weighted AUC undefined even if both labels occur in the file. The documented `sample_weight` arguments for [Brier loss](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.brier_score_loss.html), [log loss](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.log_loss.html) and [ROC AUC](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html) are distinct from class-averaging options; `average='weighted'` does not supply case weights and is ignored for binary AUC. Verify the chosen implementation against the declared weighted definitions.

Check that positive rescaling of every weight leaves normalized scores and reliability coordinates unchanged, while weight totals scale. Reconcile weighted confusion and bin totals to `W`. Weight totals are not automatically counts of independent observations, so do not use them as a sample size for uncertainty intervals without a matching sampling interpretation.

**Fictional illustration, not executed:** Two cases have `(p, y, w)` values `(0.2, 0, 9)` and `(0.6, 1, 1)`. Expected weighted Brier loss is `(9*0.04 + 1*0.16)/10 = 0.052`, versus unweighted `0.10`. In a single bin covering `[0,1]`, weighted mean prediction is `0.24` and observed positive fraction is `0.10`; unweighted coordinates would be `0.40` and `0.50`. Report two cases and weight total ten. No evaluator was run and these invented values establish no model quality.

### 4. Inspect reliability with denominators

For a stated bin rule, compute each nonempty bin's mean prediction, observed positive fraction and count. Keep empty bins empty. State interval boundaries, including where p=1 belongs. Plot mean prediction on x and observed frequency on y with a diagonal reference; do not plot bin midpoints as if they were actual mean predictions.

Show counts alongside points. A one-case bin does not supply strong calibration evidence. Binned absolute calibration error depends on the bins and sample; label it descriptive and avoid presenting it as a universal model property. If uncertainty intervals are requested, choose an approach consistent with independent or grouped sampling and document its assumptions rather than adding generic error bars.

### 5. Separate threshold tuning from probability quality

Changing the decision threshold changes confusion counts and threshold metrics, but must not change Brier loss, log loss or AUC for the same predictions. Verify this invariant.

Do not choose a final threshold on the evaluation set and then describe that same result as untouched validation. If costs or constraints are supplied, retain them explicitly and distinguish exploratory threshold review from a prospective operating policy.

### Preserve pairing in requested uncertainty estimates

If uncertainty for a model comparison is requested, estimate the declared score difference on the common cohort, with its sign and units explicit. Do not substitute overlap of separate model intervals for an interval or test of that difference. Keep each case's outcome, both predictions and applicable weight together. Under an appropriate independent-case bootstrap, resample the same case indices for both models and recompute their score difference in every draw; independently resampling the two models destroys their within-case dependence. Grouped, temporal or survey data require a design-compatible method, not automatic row resampling. [SciPy's bootstrap reference](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.bootstrap.html) documents shared-index resampling with `paired=True`; the default is unpaired.

Keep the uncertainty target narrow: resampling supplied predictions describes evaluation-sample variability under the stated assumptions, not variability from retraining or choosing the model. A shared resampling scheme does not repair leakage or biased coverage. Retain the method, resampling unit, settings and any undefined replicates. Do not silently discard one-class AUC draws, turn non-finite losses into finite differences, or suppress a degenerate-interval warning to return a plausible interval. Use a justified alternative or report that the requested interval was not established.

**Fictional, unexecuted diagnostic:** Two models have identical predictions on every case, but their Brier losses differ across cases. Every shared-index resample must give a Brier-loss difference of zero. Independent draws can create artificial variation in that difference. A degenerate bootstrap distribution may leave a chosen interval method undefined; it does not establish population equivalence or error-free predictions. No model evaluation or resampling was executed for this illustration.

### 6. Verify independently and deliver

Use hand-computable cases for perfect, tied and reversed rankings; one-class data; exact zero/one probabilities; empty shared cohorts; missing and conflicting rows. For a small dataset, compare the efficient AUC computation against direct positive-negative pair enumeration. Check total confusion counts and bin counts against the used denominator.

Test that changing bins or thresholds leaves the underlying proper losses unchanged. Preserve precision in calculation and round only presentation. Label every export with the cohort, threshold, bin rule and metric conventions.

Export only the data needed for the recipient. Removing original case IDs reduces exposure but does not automatically anonymize small-group aggregates or model names. Do not publish or send sensitive evaluation data beyond the approved destination.

## Worked example

Two independent fixture cases have predictions 0.1 for outcome 0 and 0.9 for outcome 1. Binary Brier loss is `(0.01 + 0.01)/2 = 0.01`; un-clipped mean log loss is `-log(0.9)`, approximately 0.1053605; AUC is 1. At threshold 0.5, both cases are classified correctly. At threshold 0.95, both are classified negative, so accuracy becomes 0.5 while Brier, log loss and AUC remain unchanged.

A separate one-case fixture with probability 0 and outcome 1 has infinite un-clipped log loss and undefined AUC. Writing null or zero for that loss would conceal the certainty error. An exported string such as `"Infinity"` with the stated convention is an explicit representation.

In a local JavaScript evaluator exercised with Node 24.19, 200 seeded small prediction sets with tied scores were compared to an independent all-positive/all-negative-pairs AUC oracle. Confusion and bin totals reconciled, and threshold/bin changes left the proper losses and AUC unchanged. A simulated UI check verified cohort controls, invalid-input export guards and absence of case IDs from the aggregate export. A rendered reliability SVG was inspected separately. These checks validate the evaluator on those fixtures; they do not establish that any real model is calibrated, leakage-free or useful in production.

## References

- [scikit-learn probability calibration](https://scikit-learn.org/stable/modules/calibration.html): reliability diagrams and the distinction between proper losses and calibration alone
- [scikit-learn model evaluation](https://scikit-learn.org/stable/modules/model_evaluation.html): metric definitions and interpretation boundaries
