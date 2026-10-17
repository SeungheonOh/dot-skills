---
name: diagnose-pr-merge-blockers
description: "Explain why a GitHub pull request cannot merge by joining applicable rules, exact-revision checks, review state and merge-queue evidence. Use for a read-only blocker diagnosis and precise next action, not code review, CI repair, approval, bypass or merging."
---

# Explain what is blocking a pull request

Tell the user which observed requirements still prevent the requested pull request from merging, what evidence would clear each one, and what cannot be determined with available access. A green workflow badge, a clean diff or several approval comments is not a complete mergeability assessment.

Use [map-codeowners-review-routing](../map-codeowners-review-routing/SKILL.md) when path ownership needs resolving, [review-code-change](../review-code-change/SKILL.md) for code correctness, and [failing-build-repair](../failing-build-repair/SKILL.md) for a failed job's implementation cause. This workflow reconciles GitHub's merge conditions; it does not perform those downstream tasks automatically.

## Identify the pull request and observation boundary

Establish repository and host, PR number/verified URL, target branch, current head and base commit IDs, draft/open/closed/merged state, observation time and the merge route the user is asking about. Use actual provider IDs and links, not a title match alone. For GitHub Enterprise Server, consult documentation for the installed version where behavior differs.

Read existing authorized PR metadata, provider merge messages, applicable rule records, check runs and commit statuses, review events, conversation state and queue/deployment evidence as needed. A supplied export can support a dated diagnosis. Record pagination, missing sources and capture times, especially when several reads may span a new push.

Keep the work read-only. Do not mark ready, update a branch, approve or dismiss a review, resolve a thread, request reviewers, rerun/cancel jobs, enqueue, enable auto-merge, merge, change settings or bypass protection. A request to explain the blocker is not authority for those effects. Do not generate credentials or seek alternative access after a denial. Return the supported diagnosis even if policy or permission records cannot be read.

Limit copied evidence to relevant IDs, safe check names, conclusions and short diagnostics. Private source, logs, reviewer identities and organizational rules stay within the authorized audience. Do not include secret-bearing job output or upload a repository to an external diagnostic service.

## 1. Separate the questions hidden by “mergeable”

Keep independent columns for:

1. **Content integration:** whether the provider currently reports a conflict-free integration of this head into this base
2. **Policy requirements:** which enforced conditions apply to that branch and route, and whether the current evidence satisfies them
3. **Queue/operational state:** whether the PR is waiting, being checked, removed, closed or already merged
4. **Actor capability:** whether the intended actor is permitted to take the proposed next action, when that fact is actually observable

A positive content-merge result does not establish permission or satisfied policies. A null or pending provider calculation is unknown, not a conflict. GitHub's [pull-request API reference](https://docs.github.com/en/rest/pulls/pulls#get-a-pull-request) distinguishes the PR's head from a test-merge commit and documents asynchronous mergeability calculation. Record the actual field meaning before interpreting it; do not infer a final verdict from an undocumented summary enum.

If calculation is pending, a later read may settle it when requested or necessary for this diagnosis. Avoid repeated unchanged polling; preserve a clear as-of pending result when no new evidence is available. This one-time diagnosis does not itself create a watcher or promise continuous monitoring.

## 2. Establish the requirements that really apply

Read the active branch protection and accessible repository/organization rulesets for the exact target. Retain rule IDs, source, enforcement state, include/exclude targeting and observation time. A configured rule for a similarly named branch is not automatically relevant.

[GitHub rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets#about-rule-layering) can layer with each other and branch protection; do not select the first convenient rule and discard other active requirements. Keep disabled or non-enforcing records separate. When effective policy cannot be established, use the provider's explicit blocker message as evidence of that observed blocker, while leaving unobserved requirements unknown.

Build a concise requirement ledger. Include only applicable conditions: review count and eligibility, latest-push or stale-review rules, code-owner approval, conversation resolution, exact required check identities/producers, required workflows, branch freshness, queue use, deployment conditions, signatures, history/merge-method restrictions or other provider-reported rules. Preserve source wording where a condition is ambiguous instead of guessing its semantics.

Do not infer bypass rights from a job title, repository ownership or historical successful merges. An observed bypass option is not a recommendation or authorization to use it. Access limitations must not be reframed as “there are no restrictions.”

## 3. Bind each check to its actual target and producer

For each applicable check requirement, retain the required context/name, expected app or workflow identity when restricted, source rule, relevant commit/ref, run ID, attempt, event, status, conclusion, timestamps and direct result link. Keep check runs and legacy commit statuses distinguishable when both exist.

Compare the requirement to actual evidence on the head, test-merge or queue candidate that GitHub is evaluating. Do not use a pass on an older head, a similarly named job from another producer or a main-branch run as a substitute. Names alone can be ambiguous. A successful workflow containing several jobs is not proof that the required job reported on the evaluated revision.

[GitHub's status-check troubleshooting](https://docs.github.com/en/pull-requests/how-tos/merge-and-close-pull-requests/troubleshooting-required-status-checks) explains important distinctions between head and test-merge results, absent workflow reports and skipped jobs. Apply the provider's current accepted conclusion semantics; preserve raw outcomes. A provider-accepted skipped or neutral result can satisfy a merge rule without establishing that behavioral checks executed.

Under GitHub's documented rules, when a required name is emitted as both a check and a legacy commit status, both need applicable passing results. For Actions jobs, also verify event eligibility: a passing same-SHA job from an ineligible trigger can fail to satisfy the rule. Consult the host/version documentation and provider evaluation rather than assuming every run attached to that SHA counts.

Classify each required result as satisfied by applicable evidence, failed, running/queued, absent/pending report, stale/wrong subject, producer mismatch, or unresolved. Separate an actually failing job from a required context that was never emitted. For a missing report, inspect only relevant existing workflow/event/filter evidence to identify a supported explanation; do not assume path filtering, a rename or an unsupported trigger without inspecting it.

With retries, retain attempts and provider-selected current state. A pass elsewhere does not erase an applicable failure; a canceled older attempt is not automatically the present blocker. If the provider's effective selection cannot be established, show the competing records rather than selecting the most favorable one.

## 4. Reconcile review and queue evidence

Count effective eligible approvals under the actual rules, not every historical review or comment containing “approved.” Retain reviewer identity only as needed, review state, submitted time, reviewed revision, dismissal and current provider decision. A review request is not an approval. An old approval may remain valid under one policy and be dismissed under another; do not invent a universal expiration rule.

Distinguish required code-owner approval, total approvals, approval of the latest reviewable push and unresolved required conversations. A thread becoming outdated does not by itself prove resolution. A resolved thread does not prove the corresponding code defect was fixed. If owner eligibility or current policy is unavailable, preserve that uncertainty.

[Protected-branch settings](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches) govern review freshness, expected check producers, branch freshness and other restrictions. Use the repository's actual setting and provider evaluation, rather than treating a possible GitHub setting as enabled here.

For a required merge queue, distinguish eligibility to enter, current queue membership, the current merge group's checks and final merge. Record the temporary candidate SHA, group identity and latest removal/rebuild reason when accessible. A head-only pass cannot establish a current group's result, and a result for a replaced group is stale. GitHub's [merge-queue documentation](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-a-merge-queue) describes these temporary combined candidates and separate CI trigger requirements.

If the PR is already merged or closed, report that terminal state and its evidence. Do not continue diagnosing a formerly missing approval as a current merge blocker. A queue's waiting state is not automatically a failure; use its observed reason and coverage.

## Return the smallest useful unblock path

For each established blocker provide:

- Exact requirement and source rule or provider message
- Current contradictory/missing evidence, with commit/group identity and direct link
- The actor or role able to address it when known, without assigning responsibility by guess
- The smallest next action or evidence request and what observable result would remove this blocker
- Whether that action is merely proposed, already authorized in a separate request, or outside available access

Order proposed actions by dependency. A new push may invalidate checks or review state, so place a needed source update before dependent check/review requests in the proposed sequence. Do not suggest weakening rules, renaming a failing job to evade a required context, empty successful checks, review dismissal or queue jumping as routine fixes. If a rule appears misconfigured, identify the evidence and owner decision without changing it.

Lead with a short answer, followed by the blocker ledger and consequential unknowns. If every visible requirement is satisfied, say “no blocker found in the inspected evidence” and include the provider's observed state and policy coverage; do not guarantee that a merge will succeed or certify code quality. Keep rule satisfaction separate from permission to merge.

## Acceptance and recovery

Before calling the result current, reread the PR's head/base and provider state. If either moved, refresh affected evidence or deliver the report explicitly pinned to the earlier pair. Recheck queue identity when a group result is decisive. Account for every visible mandatory requirement with satisfied, blocker or unknown; preserve failures even when another condition would independently block the PR.

Verify that each cited result belongs to the stated run/revision, and that a missing read was not interpreted as a missing requirement. Check the minimal next action against the actual blocker, rather than proposing a rerun for a missing workflow trigger or requesting a reviewer when the only blocker is a queue result.

Write only the requested private report or explicitly authorized artifact destination, preserving existing content and access. Read back any save and inspect an uncertain result before retrying. On denied policy access, finish the visible-state diagnosis and name the missing policy evidence; do not claim that switching accounts or bypassing restrictions is necessary.

Stop after the requested diagnosis, unless the user separately requested continued tracking or a specific repair. Report observations, proposed actions and actions actually performed distinctly.

## Fictional illustration, not executed

An invented PR has current head H2 and target B4. Its visible summary shows a passing lint job and one approval. The applicable rule requires check `verify` from app A. The only `verify` pass is on H1; a same-name H2 pass comes from app B. The effective review record also shows that the approval was dismissed under the active stale-review rule. No queue candidate exists yet.

The diagnosis identifies two current blockers: no accepted `verify` result from app A for the evaluated H2 subject, and no effective required approval. It does not call lint a substitute, count the dismissed review or prescribe queue checks for a nonexistent group. If a later permitted read observes a new head H3, the H2 report stays dated and requires refreshed evidence before it can describe H3.

All IDs, rules and outcomes are fictional. No PR was inspected or altered, check rerun, reviewer contacted, approval granted or merge attempted by this illustration.
