---
name: map-codeowners-review-routing
description: Produce a branch-specific GitHub CODEOWNERS map for selected files or a pull request, separating textual ownership matches, owner eligibility and actual review requirements. Use for a reviewer-routing handoff or ownership-rule review, not code review or permission changes.
---

# Map GitHub Code-Owner Review Routing

Tell a contributor which ownership rules apply to the selected paths, why those rules win, and what still needs verification before anyone claims that reviewers were requested or approval is required. Deliver a compact routing worksheet and specific rule gaps. Do not infer responsibility from who last edited a file.

Use [code-review-handoff](../code-review-handoff/SKILL.md) to explain the behavior of a patch, and [repository-onboarding-map](../repository-onboarding-map/SKILL.md) to explain implementation structure. This skill concerns GitHub's CODEOWNERS routing contract. GitLab and other hosts have different semantics; use the actual host's documentation instead of applying this guide unchanged.

## Establish the subject and permitted actions

Identify:

- Repository and GitHub host, plus the pull request or selected paths
- The target/base branch and its inspected commit; for a pull request, its head commit and current stage
- Existing CODEOWNERS candidates, the authoritative changed-path list or bounded path inventory, and any requested future rule changes
- The intended audience and whether the user wants a private worksheet, an authorized documentation edit or a proposed configuration patch

Use existing read-only access. A source export can support a static map when the provider is inaccessible. Ask for the base branch when it is genuinely ambiguous; a repository's default branch is not automatically the intended target. Do not fetch unrelated source contents when paths and ownership rules suffice.

Reading a routing file does not authorize inviting reviewers, mentioning teams, posting a comment, changing ownership rules, granting access, editing branch protection or marking a draft ready. A requested rule proposal can be prepared without activating it. Treat ownership changes as consequential configuration changes because they affect review routing; keep publication within the user's exact authority.

Private team names, repository paths and reviewer email addresses can disclose organizational information. Keep them within the approved audience, omit unnecessary membership lists, and never copy credentials or access tokens into the worksheet. Do not send private paths or team names to an external matching service.

## 1. Freeze the active rule source

Record the repository, inspected base commit, observation time, selected path source and completeness. Preserve path spelling and case. If a live pull request changes while preparing the report, recheck the base/head identities before presenting a current map.

GitHub uses the base branch's CODEOWNERS for pull-request routing and selects the first file found in `.github/`, repository root, then `docs/`. Record the chosen file and the other candidates without combining their contents. Check the file's size against the current host limit. See [GitHub's code-owner documentation](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners).

If no active file is present, report that fact; do not invent a fallback owner. A CODEOWNERS change found only on the proposed head belongs in a separate future-state comparison, not the current routing map. When given only one exported file, label active-file selection unverified unless the export establishes the other candidate locations.

Use stable source links or line locators for the exact inspected file. Do not call a mutable branch link an immutable snapshot. If a branch name cannot be resolved to a commit through available access, retain its observation date and that limitation.

## 2. Resolve each path to its winning rule

Retain rule order and source line numbers. GitHub uses the last matching pattern, case-sensitive paths, and owners listed together on the winning line; a later ownerless match can leave a path unowned. It does not support `!` negation, bracket ranges or escaping an initial `#` as a pattern. Invalid lines are skipped. These are [GitHub-specific rules](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners#codeowners-syntax), so a generic shell glob or gitignore matcher is not sufficient evidence of GitHub behavior.

For ordinary path-pattern details, consult [Git's pattern documentation](https://git-scm.com/docs/gitignore#_pattern_format), while retaining GitHub's exceptions. In particular, distinguish repository-root anchoring, a directory subtree and a single path component: `*` does not cross a slash, whereas relevant `**` forms can span directories. Patterns without a leading or internal slash can match names at any depth, so bare `*` is a repository-wide default. In GitHub's examples, `docs/*` covers immediate children while `/docs/` covers the whole root-level subtree. Do not assume two visually similar patterns have the same scope.

For each selected path, record:

- Exact path and its identity in the supplied inventory
- Winning line/pattern and its listed owners, or no match, explicitly ownerless, or unresolved
- Any earlier match that matters for explaining an override
- Syntax/provider findings that change interpretation
- Static conclusion and the source supporting it

Use direct inspection for a small set. For a large set, use only an available permitted matcher whose GitHub-specific behavior is established, and state its limits. Do not install an unapproved tool or execute repository hooks/scripts to generate a routing map. If a construct cannot be interpreted confidently, mark affected paths unresolved rather than silently skipping it.

Treat renames, deletions, additions and truncated changed-file lists explicitly. Preserve both old and new names for a rename, but distinguish the provider's actual changed-path evidence from extra planning checks. If how GitHub routed a special change is not established, report the static matches separately and verify provider evidence before claiming who was requested. Do not drop deleted paths merely because they cannot be opened in the head tree.

## 3. Separate three different conclusions

Keep these layers independent:

1. **Textual routing:** what the inspected rule file says for this path
2. **Owner eligibility:** whether the listed identities are usable code owners in this repository
3. **Review requirement and observed state:** what applicable repository rules require and what actually happened on the pull request

GitHub requires eligible owners to have write access; teams must also be visible and have explicit repository write access. Missing access evidence means eligibility unknown, not invalid. If an owner is demonstrably invalid, preserve the source finding and do not manufacture a substitute. See [GitHub's eligibility guidance](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners).

When supported by current authorized access, inspect provider-reported CODEOWNERS errors at the exact relevant ref. GitHub documents a read-only [list CODEOWNERS errors endpoint](https://docs.github.com/en/rest/repos/repos#list-codeowners-errors). Record the requested ref, returned evidence and any omitted checks. An empty error result is not proof that every intended path is covered, the correct team was chosen or a review was requested.

Read applicable review rules only when accessible. A CODEOWNERS match alone does not establish required approval, all-owner approval, merge readiness or lack of a bypass. [GitHub's protected-branch documentation](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#require-pull-request-reviews-before-merging) distinguishes required review policies, code-owner requirements and bypass behavior. Record the actual applicable policy rather than inferring it from a file comment.

For a real pull request, report observed requested reviewers and review events separately from predicted routing. Draft pull requests do not automatically request code-owner review; marking a draft ready for review triggers automatic notification under [GitHub's documented behavior](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners#about-code-owners). Still require actual event evidence before claiming that a particular notification occurred. Preserve dates and the relevant revision context. If the connection cannot read permissions, team visibility or review settings, state that precise limit and finish the static map. Do not request broader credentials or change security settings to make the worksheet complete.

## 4. Turn gaps into a useful owner handoff

Summarize the affected paths by effective owner set when it helps, while retaining the per-path evidence. Explain each material gap with its concrete scope: an unowned selected path, a later rule overriding an intended team, an invalid identity, or an unresolved rule construct. Do not label an unusual assignment a defect without an authoritative expectation.

If a proposal was requested, show the minimal suggested line change beside the current rule and the affected path set. Establish proposed owners from the user's request or authoritative ownership source, not commit counts, file names or personal availability. Label missing ownership decisions instead of appointing a team.

For each proposed pattern, check intended matches and nearby counterexamples: a sibling directory, a nested path, a case variant when relevant, and a later overriding rule. Consider whether the proposal changes who can review the CODEOWNERS file itself. Keep the future-state map separate until an authorized change is published and its base-branch state is verified.

## Acceptance and recovery

Deliver the worksheet with repository/base identity, active-file evidence, selected-path coverage, winning-rule explanations, eligibility/policy unknowns and any requested proposed changes. Check that:

- Every path from the bounded input has one explicit mapping state; omissions and incomplete pagination remain visible
- Earlier matches are not incorrectly unioned into a later rule's owner set
- No match, deliberate ownerless matching, invalid syntax and unavailable evidence stay distinguishable
- Current routing is not derived from a proposed head-only file
- A rule match is not presented as a sent request, human acceptance, required approval or merge authorization
- The artifact contains only the authorized audience's necessary organizational details

If refs or rules change during review, keep the older worksheet labeled with its identity and regenerate the affected map from the new source. If a provider read fails, retain the static findings and mark the provider layer unverified; do not reinterpret an error as “no owners.” If an authorized save has an uncertain result, inspect the destination before retrying to avoid duplicate posts. Denied access is a boundary, not permission to seek the same protected information through another route.

## Illustration: fictional and unexecuted

Assume an exported base-branch file has these three rules in order: `* @example/general`, `/manual/ @example/docs`, and `/manual/private/` with no owner. The chosen paths are `manual/start.md`, `manual/private/draft.md` and `src/main.py`.

The paper map assigns the first path to the docs rule, marks the second explicitly ownerless, and assigns the third to the general rule. It does not retain the general owner on the first two paths. Team eligibility, review policy and actual notifications remain unknown without additional evidence.

This is a fictional syntax illustration, not an executed matcher, GitHub API observation, reviewer request or live permission check. Report each real check and its actual scope when using the skill.
