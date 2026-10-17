---
name: reconcile-release-inclusion
description: "Reconstruct which requested changes are present in an exact Git release candidate by reconciling ancestry, replayed changes, reverts and final source content. Use for a release inclusion ledger, not release notes, readiness approval, branch integration or proof of deployment."
---

# Reconcile what actually made it into a release

Answer which changes a particular candidate contains, which expected work is missing or only partly retained, and which unexpected changes need attention. Keep three separate facts: a commit is in history, its intended change survives in the candidate, and a distributed product contains that candidate. These are different evidence questions.

Use [change-log-release-notes](../change-log-release-notes/SKILL.md) after membership is established, [release-readiness-gate](../release-readiness-gate/SKILL.md) for acceptance decisions, and [parallel-change-integration](../parallel-change-integration/SKILL.md) to combine accepted branches. This workflow reads and reconciles existing records; it does not merge, cherry-pick, revert, build or publish anything.

## Establish the exact comparison

Collect from the request and authorized sources:

- Repository identity and host, candidate ref or commit, and the prior release or other expressly chosen baseline
- Product/component and branch scope, including relevant submodules, generated sources or independently versioned components
- Expected changes identified by issue, pull request, commit or source-backed behavior; retain the source of each inclusion expectation
- Accessible commit graph, parent relationships, exact trees/diffs, pull-request merge records and any release manifest tying an artifact to a source revision
- Evidence cutoff, intended reader, requested file or document destination and applicable access limits

Resolve moving refs to full commit IDs and record the observed ref-to-commit bindings. A tag name, issue milestone or release date is not an immutable source identity. Preserve both tag object and peeled commit identity when available; do not claim signature verification from seeing a signature field.

If the candidate is unknown, inventory expectations but hold candidate-membership conclusions. If the baseline is unknown, an absolute check of a few requested changes may still be possible; do not invent a previous release. A supplied source archive can support content findings but cannot establish unavailable ancestry.

Use already-authorized read interfaces or passive object inspection. Do not run repository scripts, checkout filters, hooks or test commands to prepare this ledger. Do not fetch additional objects into a user checkout, modify refs or request broader credentials as an incidental step. Missing objects, pagination caps and denied reads are coverage limits, not evidence of absence. Keep private issue titles, paths and customer details within the authorized audience; omit secrets and unnecessary author/contact data.

## 1. Establish history coverage and endpoint differences

Read the parent graph needed for the selected comparison and state whether the baseline is an ancestor of the candidate. For an ancestral baseline, the history set is commits reachable from the candidate but not the baseline. Git's [revision-range documentation](https://git-scm.com/docs/gitrevisions#_specifying_ranges) distinguishes this two-endpoint set from a symmetric difference. Do not substitute a three-dot comparison or a timestamp filter without explaining the different question.

Maintain two views:

1. **History:** commits and integrations newly reachable relative to the baseline, including merge parents and relevant intermediate changes
2. **Net source difference:** the actual baseline and candidate trees, including additions, modifications, deletions, modes and relevant component pointers

A first-parent view can explain integration order but may hide constituent changes. Conversely, merely listing constituent commits can miss a merge's own resolution edits. Inspect the integration result against relevant parents when those edits affect inclusion. Preserve commits that have no net endpoint difference; an addition and its revert still explain why expected work is absent.

If histories diverge, retain the chosen endpoints and show the relationship. Separate candidate-side and baseline-side history and inspect the direct tree difference. Do not silently move the baseline to the merge base or describe everything on the candidate side as newly delivered. If an API returns an incomplete commit or changed-file list, do not treat its displayed subset as the full release.

## 2. Map work to changes without trusting titles

Build a small many-to-many crosswalk. Each requested item has its stable ID, exact expected behavior or component, linked changes, evidence location and unresolved mapping. Each discovered commit or meaningful change has an item mapping or an explicit unassigned disposition.

Use merge records and inspected content to establish relationships. A PR linked to an issue may address only part of it; one commit may contain several items. A milestone assignment or a message saying “fixes” is a useful lead, not proof that all acceptance criteria are present. Retain preparatory refactors separately from the behavior they enable.

For merges, squashes, rebases and cherry-picks, preserve both the original identity and the candidate-side identity. An original commit that is not an ancestor may have been replayed under another ID. Similar titles are insufficient to identify that replay. Compare the changed contract, affected paths and surrounding candidate content; record partial or modified replay explicitly.

If existing patch-equivalence evidence is available, treat it as a matching aid. Git's [patch-ID documentation](https://git-scm.com/docs/git-patch-id) describes normalization choices; patch equivalence does not prove identical ancestry, runtime behavior or survival after later edits. Do not calculate or infer a semantic equivalence claim from a hash alone.

## 3. Determine what survives at the candidate

For every consequential mapped item, inspect the final relevant source and its intervening history. Record separately:

| Dimension | Useful states |
| --- | --- |
| Historical relationship | Original reachable; mapped replay reachable; not found in covered history; incomplete or disputed mapping |
| Net content | Retained as specified; retained with an identified modification; partly retained; removed/reverted; already present at baseline; unresolved |
| Distribution link | Exact source/artifact linkage evidenced; partial linkage; not supplied |

Use these states only to the depth the evidence supports. “Retained as specified” concerns the inspected source change, not a passed functional test. Name the source-level condition that was checked and any runtime behavior still unverified.

Trace reverts by actual inverse effect and final content, not message prefixes or simple commit parity. A revert may be partial or modified; a later change may reintroduce only one component. Reverting a merge also has ancestry consequences distinct from reverting ordinary content, as explained in [Git's revert documentation](https://git-scm.com/docs/git-revert). Preserve the original, reversal and reintroduction chain without automatically canceling pairs of records.

For partial inclusion, split the item into its evidenced components. For example, a serializer may be present while its caller or migration is absent. Do not mark the whole issue shipped because one path changed. Conversely, a missing original commit ID is not grounds to mark the behavior absent when a mapped replacement implements it.

Review unassigned changes for meaningful scope additions, removals or integration fixes. Report them without inventing intent or assigning them to the nearest issue. Preserve deleted features and baseline-only fixes in a diverged comparison; a release inclusion ledger must not account only for additions.

Treat submodule pointers, dependency locks and generated outputs as their actual artifact types. A changed pointer establishes a referenced revision, not the contents of an unread submodule. Source presence does not establish packaging, deployment, feature-flag enablement or user eligibility. Keep those questions outside this result unless the supplied records directly establish the narrower fact.

## Deliver, check and revise

Return a concise answer, the pinned comparison, an expected-item inclusion ledger, an unexpected/unassigned-change list and the precise coverage gaps. For each row retain original and candidate-side identities, relevant reversal/supersession links, net-content conclusion and evidence. Keep the artifact proportional: a small backport check may need only a few rows.

Before delivery:

- Reconcile all requested items and all meaningful changes in the covered comparison, including unknown mappings
- Trace affirmative inclusion to final candidate content rather than only ancestry or a merged label
- Recheck every missing claim for squash/replay alternatives and for incomplete graph or file coverage
- Confirm that removals, partial reverts, baseline-only changes and merge-resolution edits were not lost
- Verify that one issue, several commits and several source components were not counted as the same unit
- Confirm that no inclusion conclusion became an approval, test pass or availability claim

Save only the requested artifact, preserving prior release records and unrelated edits. Read the actual saved result back, including endpoint IDs and exceptions. If a save is uncertain, inspect before retrying. If the candidate ref moved, retain this report as an assessment of its pinned ID and reconcile the newly observed candidate before calling it current. Do not rewrite the old report as if it always covered the later source.

Stop when the requested membership questions have supported results or localized evidence gaps. Return missing inputs precisely; do not fill the gap by modifying a branch, rerunning builds, contacting authors or updating issue milestones.

## Fictional illustration, not executed

The invented release branch for Birch Notes starts at baseline B. Expected issue N-21 is a two-part export change whose original PR contains a serializer and caller update. The candidate history contains a mapped cherry-pick C with only the serializer, then commit D reverting that serializer, then E restoring a revised serializer. The original PR commit is not an ancestor. A separate repair U is present but has no expected-item mapping.

The ledger retains the original-to-C relationship and the C/D/E chain. N-21 is partially retained: the revised serializer is present at the candidate, while the required caller update is absent in the complete inspected source scope. U is an unexpected included repair, not silently assigned to N-21. Neither the ancestry check nor the net diff proves that a package was built or deployed.

These identities, records and expected conclusions are fictional. No repository was queried, history transformed, source behavior executed or release verified by this illustration.
