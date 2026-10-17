---
name: document-software-compatibility
description: "Create a release-specific supported-environment statement and evidence matrix from existing policy, package declarations and observed checks. Use for documenting compatibility claims, not choosing a new support policy, approving a release or running a platform certification."
---

# Document software compatibility without overstating coverage

Deliver a statement a user can use to determine whether a particular product release covers their environment, plus the evidence behind its qualifications. Keep a support commitment, an installation constraint and an observed successful check separate. None substitutes for the others.

Use [api-contract-change-audit](../api-contract-change-audit/SKILL.md) for directional old/new API analysis, [dependency-upgrade-plan](../dependency-upgrade-plan/SKILL.md) for an upgrade proposal, and [release-artifact-verification](../release-artifact-verification/SKILL.md) to exercise an exact distribution. This workflow authors and reconciles the compatibility statement; it does not perform those tasks merely to populate a table.

## Input and output contract

Establish from the request and available records:

- Product/component, release or immutable candidate, edition/channel, distribution format and the public behavior being covered
- Relevant environment dimensions: operating system, architecture, runtime, browser, installation method, server/client versions, required extensions or hardware, as applicable
- Existing support policy, exclusions, support-period dates and the authority behind them
- Version-specific package declarations, official dependency requirements, documented exceptions and identified check records
- Evidence cutoff and desired readers, document destination and whether the request covers drafting, a scoped documentation edit or publication

Do not require every possible dimension. Include a dimension when it changes the answer for this product. Ask for a missing release identity or policy owner only when it blocks a consequential statement; prepare the evidence inventory meanwhile. If there is no support policy, produce an observed-coverage statement and explicitly leave support commitments undecided.

Return a concise reader-facing compatibility statement, a row-level evidence matrix, and a short conflict or missing-evidence list. Include the release identity and as-of date. These can be sections of one document; a small request does not need a separate reporting system.

## 1. Freeze the claim boundary

Pin the product and artifact to the most specific known identity. Keep source revision, package version, build variant and artifact digest distinct; record a digest only if supplied by a trusted record or actually calculated within the task. One package name can cover platform-specific artifacts with different restrictions.

Separate three questions before extracting facts:

1. **Policy:** which combinations does the maintainer commit to support, and with what exceptions or duration?
2. **Declared constraints:** which combinations do metadata, installers and dependencies accept or require?
3. **Observed coverage:** what was actually checked, against which artifact and workflow, and with what result?

A configured CI job is planned coverage, not a passing observation. A build badge for the main branch is not evidence for an older release. A package's minimum runtime is not a promise about every later runtime. A version label alone does not prove behavior; [Semantic Versioning 2.0.0](https://semver.org/) describes versioning relative to a declared public API, not a platform test result.

Preserve source locators, revisions, dates and authority for each question. When a source is mutable, record the retrieved revision or quoted scope sufficient to explain the conclusion later. Do not represent a copied statement as independently verified.

## 2. Build environment rows that retain the conditions

Begin with the combinations the reader needs and those the supplied policy names. Use explicit rows or compact range rules with exclusions; do not infer the Cartesian product of separately listed platforms, runtimes and architectures. “Linux and Windows; runtime 8 and 9” does not establish all four combinations unless the source says so.

For each row, retain:

| Field | Meaning |
| --- | --- |
| Environment ID | Stable reference independent of table position |
| Conditions | Exact platform/architecture/runtime and relevant installation or feature limits |
| Policy state | Explicitly supported, explicitly unsupported, conditional, or not stated |
| Declaration result | Constraints permit, constraints exclude, conflicting declarations, or unresolved |
| Observation | Passed, failed, skipped, cancelled, incomplete, or not observed |
| Evidence scope | Candidate, check date, method, tested behavior and source location |
| Reader consequence | Supported route, known limitation, conflict needing resolution, or unanswered coverage |

Keep range endpoints, exclusions and preview/stable channels exact. Do not turn “versions 8.2 and 8.4 tested” into “8.2–8.4 tested,” or “8 or later” into an indefinite future support promise. Resolve version comparisons using the ecosystem's actual version rules if needed; lexical ordering and assumptions about SemVer are insufficient for every product.

Separate host from target when relevant. A cross-compiled artifact is not evidence that the target executed it. An emulator result is scoped to that route. Installation, startup, selected behavior and upgrade interoperability are different observations. Do not compress them to a single green “works” cell.

## 3. Reconcile policy, declarations and observations

Bind a check to its exact artifact, environment and tested behavior. Keep the producing party visible: a supplied log reports someone else's check; it is not a test performed during this task. If evidence is missing, truncated, for another build or stale under the supplied freshness rule, explain that limitation rather than selecting a convenient pass.

Apply these distinctions:

- **Supported with no observation:** retain the policy claim and say the provided evidence does not establish a check for that row
- **Observed pass outside support:** report the bounded pass without expanding the support promise
- **Supported but declaration excludes:** hold an unqualified compatibility claim; preserve both the policy and the blocking package constraint
- **Supported but a check failed:** identify the failing behavior and environment, retaining the existing commitment as policy rather than implying success
- **Explicitly unsupported with a successful experiment:** preserve the unsupported status and label the experiment accurately
- **Missing row:** use “not stated” or “not assessed,” not “unsupported”

Resolve differences through release applicability, artifact variants, superseding decisions and the authority of the source for that fact. A newer timestamp alone does not repeal a policy. If no source settles the conflict, assign the precise open question to the supplied owner, or state that the owner is unknown. Do not invent an exception, support tier, end-of-support date or corrective release.

## 4. Write the usable statement

Lead with release identity, the supported route and consequential exceptions. State what “supported,” “tested” and “not assessed” mean in this document. Put conditions next to the claim they limit, especially feature subsets, optional dependencies, preview status, installation methods and unavailable architectures.

Describe a failure specifically. “The supplied Windows startup check failed for build X” is different from “Windows is unsupported.” If unresolved evidence makes a safe general statement impossible, publishable copy should state the bounded known facts and the unresolved limitation; do not hide it only in the internal matrix.

Keep lifecycle commitments separate from present compatibility. Copy existing support dates with their time zone or date semantics and source. Do not start a retirement clock or promise future testing. Existing support contact details may be included when supplied and appropriate for the audience; do not contact maintainers as an unrequested fallback.

Keep private device labels, customer names, local usernames, internal CI links and unredacted logs out of public copy. Maintain useful private evidence in the authorized review material. Use public source links only when verified for that audience; do not widen source permissions to make a citation work.

## Acceptance, preservation and recovery

Before delivery:

- Trace each affirmative support claim to applicable policy and each observed result to its exact check scope
- Reconcile all requested environments, including excluded, unknown and conflicting rows
- Confirm that a skipped job, configured matrix or successful build did not become an executed consumer check
- Confirm ranges and grouping have not created unobserved combinations
- Check that supported-but-failing and passed-but-unsupported cases remain distinguishable
- Verify that private evidence and unsupported guarantees did not enter the reader-facing statement

Edit only the requested release section or document. Preserve historical matrices, existing exclusions, source links and unrelated changes. If the destination changed after inspection, reconcile the new version before writing. Read the saved statement back and verify its scope and qualifications.

When evidence later changes, update the affected rows and statement with a dated correction, retaining the old conclusion's scope. Do not retroactively present a later successful check as evidence available at the earlier cutoff. If a documentation write has an uncertain outcome, inspect the destination before retrying. If writing is blocked, return the finished draft and exact blocked destination.

Stop when the statement faithfully represents the available policy and evidence, even if some rows remain unresolved. A documentation request does not authorize testing software, installing dependencies, altering metadata, changing support policy, approving a release or publishing to a new audience. Perform already-requested ordinary documentation edits within scope; ask only for the additional action or decision that is actually missing.

## Fictional, unexecuted example

The following input and expected document are invented. No package was installed, no CI job was run and no compatibility was established by this example.

**Input:** Alder Formatter 4.2.0 has policy P7 covering Linux x64 and Windows x64 on Python 3.10–3.12. Its supplied wheel declaration says Python >=3.11. A supplied Linux x64/Python 3.11 formatting record reports a pass for this artifact. The Windows x64/Python 3.12 job was skipped. A separate Linux arm64/Python 3.11 experiment reports a pass, while P7 explicitly excludes arm64. No support-policy change is authorized.

**Expected rows:** Python 3.10 has a policy/declaration conflict and cannot receive an unqualified compatibility claim. Linux x64/Python 3.11 is policy-supported with a scoped reported pass. Windows x64/Python 3.12 remains policy-supported but unobserved in the supplied records. Linux arm64 remains explicitly unsupported despite the reported experiment. Python 3.13 is not assessed merely because the wheel's lower-bound declaration would permit it.

**Expected reader-facing extract:** “For Alder Formatter 4.2.0, policy P7 covers Linux x64 and Windows x64 on Python 3.10–3.12. The supplied wheel excludes Python 3.10, so that policy/artifact conflict remains unresolved. The supplied check records show the selected formatting workflow passing on Linux x64/Python 3.11; the Windows 3.12 check was skipped. Arm64 is outside P7.” The decision queue asks the owner to resolve the 3.10 mismatch without silently rewriting the policy or package.
