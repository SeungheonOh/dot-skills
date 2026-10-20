---
name: map-requirement-verification
description: "Reconcile versioned requirements with implementation references, verification procedures and result evidence into a bidirectional traceability map. Use to find uncovered obligations, unsupported links and change-affected evidence, not to write requirements, run tests or approve a release."
---

# Map requirements to verification evidence

Produce a traceability map that answers two different questions: “What checks this obligation?” and “What does this result actually establish?” Keep planned verification, an existing implementation and a passing result separate. A requirement linked to a test name is not necessarily covered by that test's assertions.

Use [define-project-brief](../define-project-brief/SKILL.md) when the requested behavior still needs definition, [write-behavior-tests](../write-behavior-tests/SKILL.md) when tests must be implemented, and [release-readiness-gate](../release-readiness-gate/SKILL.md) when the question is whether one candidate meets a release policy. This workflow reconciles the relationships between existing records, including revisions that make an older relationship uncertain.

## Set the baseline and the question

Identify the bounded requirement set, its accepted version, the product or artifact being assessed, and whether the user needs an initial map, a gap review or a comparison after specified changes. Read the relevant specification, accepted change records, design or implementation references, verification procedures and available results. Use existing authorized sources; a missing export is not a reason to require one if the native records can be inspected.

Record stable identities and versions, not just filenames. A spreadsheet row number, changing issue title or branch name alone is a weak identifier. If sources lack IDs, assign local mapping IDs without altering the originals; retain a precise section or record locator so the assignment is reproducible.

Establish which source is authoritative for each obligation. Preserve proposals, rejected changes and superseded requirements separately from the active baseline. A newer timestamp does not prove acceptance. If acceptance or scope is unclear, map the available material but label the disputed baseline; do not issue an apparently definitive coverage total.

NASA's [requirements-management guidance](https://www.nasa.gov/reference/6-2-requirements-management/) treats traceability and changes to requirement baselines as connected activities. Its [verification-matrix appendix](https://www.nasa.gov/reference/appendix-d-requirements-verification-matrix/) emphasizes unique requirement identifiers and identifiable source documents. These are useful background principles, not a requirement to adopt NASA governance, terminology or certification claims for an ordinary project.

## Preserve the obligation before linking it

Keep each requirement's exact controlling text or an appropriately bounded source reference alongside a short explanation. Preserve its conditions, units, quantifiers, exceptions and version. “Every exported record” must not become “one sample record,” and “within two seconds after acknowledgment” must not lose its starting event.

If a sentence combines independently checkable obligations, create traceable clause labels beneath the original ID. Do not silently rewrite the accepted requirement or inflate the requirement count by counting those clauses as new requirements. An unclear word such as “fast” remains a clarification gap; a convenient threshold invented by the mapper is not acceptance criteria.

Keep hierarchy distinct from evidence. A parent requirement may be allocated to several children, but links to those children do not prove that they jointly fulfill it. Inspect the allocation rationale and retain any unallocated part. A derived requirement without a supplied parent can have a legitimate rationale; flag the missing rationale or decision rather than deleting the requirement as unnecessary.

## Build explicit relationships, not checkmarks

For a small task, one readable table and a short gap list may suffice. For a larger set, keep requirements, checks and results as separate records joined by stable IDs. Avoid one giant row whose comma-separated cells hide which assertion covers which clause.

For each proposed relationship, record:

- Source and target IDs with their applicable revisions
- Relationship type, such as allocated to, implemented by, checked by or evidenced by
- The exact clause or behavior addressed
- A source locator and a short explanation of why the link is valid
- Review state: supported, partial, proposed, conflicting or needs reassessment

Represent many-to-many relationships explicitly. One check can address several requirements, and one requirement can need several checks. Do not duplicate a result to make it look like independent evidence. Conversely, a shared setup step or a nearby test-file name is not evidence of an assertion about every linked requirement.

Read the check's setup, stimulus, assertions, expected result and relevant environment. Match its actual scope to the requirement, including negative behavior, boundary conditions and relevant configurations. A successful save test does not establish that invalid input is rejected. A procedure may use inspection, analysis, demonstration or testing; retain the method actually specified instead of relabeling every check as an executed test.

Read backwards too: for each in-scope check or result, identify what obligation it supports. Unlinked checks may protect implementation-specific behavior or explore a risk. Report the missing relationship or rationale; do not remove them or invent a requirement to justify them.

## Keep three coverage questions separate

Report separately:

1. **Trace coverage:** Is there a supported relationship from each obligation to an identified verification method or check?
2. **Verification adequacy:** Do those checks jointly address the obligation's material conditions, rather than only mention its topic?
3. **Result evidence:** Is there an applicable observed result for those checks, on the relevant version and configuration?

A planned check can satisfy a planning question while leaving execution unknown. A recorded pass applies only to the assertions and conditions actually exercised. A missing log is an evidence gap, not automatically a product defect; a visible failed assertion remains a failure even if other evidence is missing.

For results, retain the producing check revision, assessed product/artifact revision, environment or configuration, observation date, outcome and evidence locator where available. Distinguish passed, failed, skipped, blocked, not run and unknown. Preserve conflicting applicable results rather than selecting the most reassuring one. Apply supplied rerun or supersession rules when they exist; otherwise leave the conflict for review.

Use counts only when the denominator is defined. State whether it counts active requirements, individual clauses or a selected subset. Keep partial, excluded, superseded and unknown records visible. “Has a linked check” and “has applicable passing evidence” need different counts; neither is a defect-rate or reliability measure. A tiny set is often clearer as named gaps than as a percentage.

## Reassess links when something changes

Compare the old and new requirement text, check procedure and assessed artifact identities. Identify added, removed, split, merged and materially changed records. Preserve stable IDs when the source does; retain an explicit old-to-new mapping when it does not. Similar wording alone does not establish identity.

Mark relationships needing reassessment when their meaning or supporting evidence could have changed. This is a review flag, not a declaration that the product failed. Trace the affected requirement's linked checks and evidence, then inspect shared checks for other obligations whose assessment could also change.

Reassess at the smallest justified scope. A changed threshold may invalidate one assertion's applicability without invalidating unrelated assertions from the same run. Equally, an unchanged requirement does not make an old result applicable to a changed implementation. Record the reason for retaining, replacing or withholding each affected link; do not automatically carry green statuses forward.

An approved requirement withdrawal changes the current scope but does not erase its historical results. A proposed withdrawal does not remove it from the active denominator. Keep the map's baseline and comparison boundary explicit so a later reader can reconstruct what changed.

## Deliver the map and the next useful decisions

Return the actual matrix or relationship register, source/baseline identities, and a short prioritized gap list. Lead with uncovered obligations, unsupported “pass” claims, conflicting baselines and links needing reassessment. For each material gap, name the smallest next step: clarify one clause, inspect an unavailable assertion, obtain a version-bound result, or decide whether an established reuse rule applies. Assign an owner only when the source supports that assignment.

Check the final artifact in both directions:

- Every in-scope requirement has supported links or an explicit gap
- Every claimed evidence relationship points to the actual check and result, not a similarly named item
- Split clauses, shared checks and superseded records have not inflated counts
- A changed requirement cannot retain an unexplained old pass
- No diagram or summary silently converts a proposed link into a verified relationship

Open source locators where access permits and report inaccessible evidence as such. A structural link check cannot establish semantic coverage. For a saved artifact, reopen it and check that IDs, links, revisions, caveats and row relationships survived the export.

This is a read-and-reconcile workflow. It does not run checks, edit the authoritative requirements, close defects, change tracker states, request approvals or release a product unless those additional actions are independently part of the user's authorized task. Preserve source records and concurrent edits when updating an existing map. After an uncertain save, inspect the saved version before retrying; deliver the completed local map with the precise remaining blocker if placement is unavailable.

## Fictional, unexecuted illustration

A fictional team's specification revision 4 contains:

- R1: Export every selected record and preserve selection order
- R2: Reject an export request containing an unknown record ID

Procedure C1 revision 2 exports three valid records and checks only their count. Its recorded pass on build B7 supports the count check, but not R1's order clause or R2's rejection behavior. A title such as “Complete export validation” does not expand its assertions. The map records R1 as partially addressed and R2 as lacking a supported verification link.

Now a proposed revision 5 would change R1 to sorted order. Before acceptance, revision 4 remains the baseline and the proposal is a separate comparison. After evidenced acceptance, the R1-to-C1 relationship needs reassessment; the old count result cannot establish the new ordering obligation. A new ordering check can be planned without claiming it ran. If C1 later adds an ordering assertion, its earlier execution cannot retroactively cover the new procedure.

These are authored reasoning examples, not executed product checks, measured skill effectiveness or a claim that a real requirement set was verified.
