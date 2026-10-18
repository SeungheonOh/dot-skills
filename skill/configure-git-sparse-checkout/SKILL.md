---
name: configure-git-sparse-checkout
description: "Configure or revise a directory-based sparse checkout in an existing Git working tree, preserving local work and verifying the intended source subset. Use when only selected monorepo directories should be materialized, not to create another checkout, restrict access, erase history or hide local edits."
---

# Keep the needed source directories in a Git checkout

Deliver a working tree with an explicit, verified directory selection and a safe route to expand or restore it. Keep the repository's revision and staged content intact. A smaller folder view is insufficient if required shared source disappeared or local ignored files were lost.

Use [create-linked-git-worktree](../create-linked-git-worktree/SKILL.md) for a second checkout, [repository-onboarding-map](../repository-onboarding-map/SKILL.md) to discover a project's entry points, and [restore-pinned-submodules](../restore-pinned-submodules/SKILL.md) for missing submodule contents. Use [portable-project-handoff](../portable-project-handoff/SKILL.md) to prepare a bounded transfer package. This workflow configures an existing checkout; it does not clone, change branches, install dependencies, execute project code or publish anything.

## Inputs and scope

Resolve these from the request, repository instructions and available evidence:

- The authorized existing checkout and intended activity or selected directories
- Required shared source, root-level manifests and configuration needed by that activity
- Whether the request is a proposal, initial selection, expansion, replacement or return to a full working tree
- Installed Git and editor/Git-client versions, filesystem constraints and available space
- Local changes, staged work, untracked and ignored assets to preserve
- Allowed object acquisition and source endpoints, including any offline constraint

Ask only for a missing choice that changes the operation. An explicit setup request can authorize the scoped configuration and tracked-file materialization changes. It does not authorize discarding ignored assets, moving secret files, changing global settings, bypassing security controls or running project tasks. Keep reports private and omit credential-bearing remotes, secret values and unrelated filenames. Use only an environment that is actually available and authorized.

## 1. Decide whether a sparse working tree fits

Separate three goals before touching configuration:

1. Fewer checked-out source files: this workflow
2. Less downloaded object data: a separately scoped acquisition decision; [partial clone](https://git-scm.com/docs/partial-clone) manages object availability, which is different from working-tree selection
3. Prevent another person or process reading excluded source: stop and choose an actual access-control design; sparsity does not provide one

Do not promise that repository history or existing objects shrink. Do not use sparsity as a backup, redaction method or way to conceal tracked local edits. Git's [index guidance](https://git-scm.com/docs/git-update-index#_skip_worktree_bit) distinguishes skip-worktree from assume-unchanged; neither is a general promise to protect edited files from future operations. Use the supported high-level interface rather than hand-setting index bits.

Choose directory-based cone mode for new setups. Its inclusion is wider than the named leaf: files directly inside ancestor directories, including the root, also appear. Explain this before accepting a strict file allowlist. If the request requires arbitrary file exclusions or an existing non-cone setup must retain its semantics, return a reviewed plan or route that case separately; do not silently translate patterns into directory names. See Git's [sparse-checkout model](https://git-scm.com/docs/sparse-checkout).

Before any object-content inspection, establish whether the checkout can fetch missing objects implicitly. Enforce an offline boundary from the first read using installed-version-supported controls, or leave unavailable content unknown. Apply the same acquisition boundary during later materialization.

Do not infer the required source solely from directories that happen to exist now. Read relevant manifests, workspace declarations and relative references at the recorded revision/index. Agree the smallest useful directory selection, including shared packages, schemas or configuration needed for the activity. A static dependency map is a candidate, not proof that a build works. Hold an explicit exclusion that conflicts with a required dependency instead of expanding it silently.

## 2. Preserve the current state before shrinking anything

Establish the real checkout root, Git directory, common directory and any Git environment overrides. Read instructions before invoking repository-specific helpers. Record HEAD, branch, ongoing operations, current sparse mode/rules, index mode and effective setting origins. Resolve paths through Git's installed interfaces; `.git` may be a file, and linked checkouts can share configuration.

Inspect effective executable behavior before status or materialization: filesystem monitors, hooks, attributes and conversion/filter programs. [Git attributes](https://git-scm.com/docs/gitattributes) can select external filters when files enter or leave the working representation. Include applicable info, global and system attributes, not only the visible tracked file. Use understood, authorized helpers or a supported nonpersistent suppression route that does not bypass organizational controls; otherwise hold the operation. Do not dump all configuration or environments to diagnose this.

Keep staged and unstaged changes separate. Inventory tracked index entries and actual local files, including ignored files in every directory that may disappear. Use [git ls-files](https://git-scm.com/docs/git-ls-files) with supported staged, untracked and ignored-file modes as appropriate; preserve path boundaries with NUL-delimited output rather than whitespace splitting. Account for sparse-directory entries instead of treating them as ordinary files. Inspect affected filesystem paths without following symlinks outside the checkout.

Record content identity for valuable affected files without exposing their contents. A diff does not preserve an untracked file; a digest is not a recoverable copy. Arrange an authorized verified copy outside the shrinking tree when needed, or retain its containing directory. Do not move credentials into an ordinary backup folder. If sensitive material cannot safely be preserved, hold the narrowing operation and ask for the owner's handling decision.

Important: cone-mode changes can delete ignored files in excluded directories. Git's [command reference](https://git-scm.com/docs/git-sparse-checkout) documents this behavior. A clean status is not sufficient permission or preservation evidence. Do not depend on a neighboring untracked file accidentally keeping an ignored asset alive. Treat an unknown cache, local database, generated output or environment file as valuable until its disposition is established. Obtain any required deletion approval before allowing incidental removal.

Pause affected transitions during unresolved merges, rebases or concurrent index writers. Do not stash, commit, clean, reset or resolve conflicts as a hidden prerequisite. Unrelated dirty work need not block a proposal, but every file threatened by materialization or removal must have an explicit preservation path.

## 3. Review the exact transition and configuration reach

Build a compact before/after plan: selected directories, newly included tracked paths, paths leaving the working tree, retained local-only files and exceptions. Derive it from the recorded index and candidate selection, not a recursive directory listing alone. Use the installed version's rule-inspection interface when available; otherwise describe the cone expansion explicitly and leave uncertain matches unresolved. Do not call an operation a dry run unless it genuinely avoids writes and helper execution.

Choose replacement versus expansion deliberately. A replacement must contain the complete desired selection, including retained directories. Reject nonexistent or wrongly cased selections unless the request deliberately targets future source and the installed behavior is understood. Use literal directory names with verified quoting/input encoding; do not let the shell expand wildcard characters. Unusual names require the installed interface's documented representation, not an ad hoc line-splitting script.

Inspect shared configuration before activation. Git may enable worktree-specific configuration during sparse setup. The [worktree configuration reference](https://git-scm.com/docs/git-worktree#_configuration_file) explains the extension and migration considerations, including core.worktree and core.bare. Record affected siblings and older clients. If this transition would change their behavior or compatibility outside the request, stop for that specific decision rather than assuming a checkout-local command has only checkout-local effects.

Keep an ordinary full index for a new setup unless sparse-index compatibility is deliberately requested and established for every client that touches it. Preserve an existing supported index mode unless changing it is needed and authorized. The [configuration reference](https://git-scm.com/docs/git-config) defines setting scopes; a worktree-targeted write is not isolated merely because its option is named worktree when the extension is absent. Do not migrate unrelated settings or rewrite the entire config.

Before expansion or restoration, check required object/payload availability, capacity and destination obstructions. Partial clones can acquire missing objects on demand. Enforce the requested network boundary with installed-version-supported controls or stop before a command that could fetch. An approved Git remote does not automatically approve a filter's different payload service. Treat submodule initialization and LFS payload retrieval as separate requirements; absence from disk does not by itself diagnose a sparsity error.

## 4. Apply one reviewed selection

Recheck HEAD, index content, rules and affected local files immediately before the write. Reconcile concurrent changes rather than overwriting them with the earlier plan. Keep editors or watchers that auto-run on file changes out of the transition unless their effects are understood and authorized.

These are command shapes only, not executed instructions. Substitute verified, safely represented arguments and required command-local controls, using the installed Git help:

```text
git -C CHECKOUT sparse-checkout set --cone --no-sparse-index --stdin
git -C CHECKOUT sparse-checkout add --stdin
git -C CHECKOUT sparse-checkout disable
```

For initial setup or replacement, supply the reviewed complete selection to set. For an established compatible cone-mode checkout, add expands it. Disable requests full materialization. Avoid an unnecessary init-then-set sequence. The [command reference](https://git-scm.com/docs/git-sparse-checkout) documents these operations and their version-dependent options. Preserve an established index mode when the displayed new-setup shape does not fit it.

Apply once and retain the actual outcome, including warnings. A successful process exit is not proof that every excluded path disappeared. A failure is not proof that nothing changed. Do not force success with cleanup, skip-check flags, low-level index surgery or automatic retries. Keep this task at source configuration; starting a server or running a package script needs its own requested scope.

## 5. Verify selection, source and preservation independently

Read back the saved selection, effective modes and setting origins. Compare intended membership with actual materialized source and account for every exception. Required paths must exist with the correct type and expected representation; an LFS pointer or empty submodule directory is not its payload. Distinguish object bytes from approved line-ending/filter conversions.

Verify these separately:

- HEAD and branch are unchanged
- Staged path/mode/object identities and staged-versus-unstaged intent are preserved, even though index representation or sparse flags may change
- Required directories and ancestor-level files are available; omitted source is omitted for the intended reason
- Valuable modified, untracked and ignored bytes survived at the agreed locations
- Existing sibling worktrees retain their source selection and effective behavior, with intentional shared configuration changes recorded
- Retained out-of-selection files are explained, not silently erased to make the view match

Git operations may materialize paths for conflicts or other work. The [sparse-checkout design guide](https://git-scm.com/docs/sparse-checkout) distinguishes saved patterns from actual working/index state. Leave dirty or conflicted extras alone. Reapplication is a later reviewed transition after the owner has handled that work, not permission to discard it.

When an authorized editor inspection is useful, check the selected source opens without automatic project execution. Do not confuse editor visibility with dependency completeness. Mark a build or application check unrun unless separately authorized and actually performed against this final selection.

## Recovery and handoff

After interruption, inspect the actual rules, config, index and filesystem before choosing a remedy. For an incomplete expansion, identify the exact missing object, denied endpoint, obstructing file, filter failure or capacity problem. Preserve successful materialization and existing work; do not delete the checkout or broaden acquisition to obtain a clean retry.

Returning to the earlier selection requires renewed preservation checks because later edits may exist. Restoring all tracked source requires capacity and object availability. Neither restores deleted ignored files. Recover those only from the verified preserved copy through an authorized, no-overwrite route. If no copy exists, stop further writes and report the specific loss/uncertainty; do not claim Git can recreate untracked bytes.

Do not blindly replace configuration with an old snapshot or remove the shared worktree extension. Reconcile each task-owned change with current values and sibling use; configuration rollback is different from restoring source and local data. Retain recovery copies until their disposal is authorized.

Return the checkout, unchanged revision, final directory selection, active modes, necessary ancestor-level inclusions, verified preservation, intentional configuration changes and any source/verification gaps. Give the minimal installed-version-appropriate expansion and full-restoration route with its prerequisites. Stop when the requested selection and preservation checks are satisfied, or identify the exact decision/access/capacity blocker. Label proposal, applied configuration, materialized source and application execution as different outcomes.

## Fictional, unexecuted illustration

A fictional Birch checkout contains apps/viewer, apps/admin and packages/theme. The user requests a viewer-focused checkout without running code. Static references show viewer needs theme. An ignored apps/admin/local-preview.db also exists, and the owner has not decided whether it can be removed.

The candidate selection is apps/viewer plus packages/theme, with root and ancestor-level files included by cone semantics. The database blocks narrowing until it has an authorized verified preservation route or its containing directory remains selected. A later request to add docs would expand the saved selection rather than replace viewer and theme with docs alone.

Expected acceptance is unchanged revision and staging, required source present, the database preserved, and every leftover path explained. If a filter needs an unavailable external payload, configuration may be applied while source readiness remains blocked. This is an authored decision illustration only: no Git command, checkout change, file copy, project test or external action was executed.
