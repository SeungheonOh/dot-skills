---
name: create-linked-git-worktree
description: "Create a second local Git working tree at an explicit revision or branch, verify its registration and materialized source, and preserve the original checkout. Use for concurrent review or development, not independent backups, integrating contributions, or repairing repository corruption."
---

# Open a second Git working tree safely

Deliver a usable additional checkout at the requested revision, with a clear path-to-branch map and evidence that existing work survived. A second folder is not enough: its Git identity, materialized contents and shared-state boundaries must be understood.

Use this when someone needs to inspect a release or start another task without switching their current checkout. Use [parallel-change-integration](../parallel-change-integration/SKILL.md) to combine finished contributions, [recover-missing-git-work](../recover-missing-git-work/SKILL.md) to find lost history, or [repository-onboarding-map](../repository-onboarding-map/SKILL.md) to understand and run an unfamiliar project. This guide ends at checkout readiness; it does not install dependencies, run project code, publish a branch or remove old worktrees.

## Inputs and action boundary

Establish these from the request and available repository instructions:

- The authorized repository and existing checkout to preserve
- The intended source revision, existing branch or new branch name, and whether the second task will make commits
- A permitted new local directory, filesystem constraints and available space
- Whether only a proposal or actual creation is requested; any allowed object acquisition and source endpoint
- Any required source exclusions, such as intentionally absent large-file payloads, and whether an independent repository is actually required

For a requested second checkout, ordinary local creation and a fresh requested branch can be within scope. An explanation-only request does not authorize either. Do not add redundant approval for an already authorized creation, but resolve an ambiguous repository, occupied destination or missing target decision before writing.

Do not fetch from an unapproved source, run repository programs, change trust/security settings, install tools, create credentials, push or delete anything as a hidden prerequisite. Do not copy credentials or local environment files from the original. Keep the new directory outside synced/shared locations unless that exposure is authorized. Identify an existing permitted environment rather than assuming a particular assistant has computer access.

## 1. Decide whether a linked checkout fits

Git's [worktree reference](https://git-scm.com/docs/git-worktree) describes separate HEAD/index state with shared repository objects and most refs. This is working-file separation, not an independent backup or security sandbox. Branch and ordinary repository configuration changes can affect siblings. Its current submodule caveat is also a reason to avoid treating a superproject as a routine case.

Proceed with the ordinary path here for a repository whose required source can be materialized without submodule initialization or shared-configuration migration. If the task needs a fully independent repository, incompatible repository settings, or populated submodules, explain the mismatch and propose a separately authorized independent checkout. If it needs untrusted-code execution isolation, a separate clone is insufficient too; stop at source preparation and obtain an appropriate isolated execution plan. Do not silently substitute an incomplete worktree or a different environment.

Choose the intended mode before creation:

- Review one immutable revision: use detached HEAD and plan no commits
- Develop a new task: use a fresh explicit branch at a pinned starting commit
- Continue an existing local branch: use that exact branch only after checking that no other worktree occupies it

If the existing branch is occupied, offer its current worktree when appropriate, a detached view of its observed commit, or a separately named task branch. These produce different editing and commit behavior; do not choose a new branch when the user specifically needs to advance the original one. Never override branch occupancy to make two checkouts write the same branch.

## 2. Inspect the real repository and preserve the present

Read local instructions. Establish the installed Git version and resolve the checkout root, Git directory and common directory through [git rev-parse](https://git-scm.com/docs/git-rev-parse). Do not assume `.git` is a directory or infer the repository from a terminal's previous working directory. Check explicit Git-related environment overrides without printing secret values; stop if they redirect commands to a different repository or index.

Inventory current registrations, branch occupancy, missing paths and lock reasons. Use the installed version's machine-readable worktree listing and preserve exact paths, including whitespace. Do not regard a missing directory as disposable: it may be an unmounted volume or a moved checkout. Keep this inventory bounded to the selected repository.

Before status or checkout, inspect effective configuration and attributes for executable behavior in both the original checkout and the new target. Include applicable repository info attributes and global/system attribute files, not just the target revision's tracked attributes. [Git hooks](https://git-scm.com/docs/githooks) include post-checkout and reference-transaction hooks; [attributes](https://git-scm.com/docs/gitattributes) can select conversion/filter programs. [Filesystem-monitor configuration](https://git-scm.com/docs/git-config#Documentation/git-config.txt-corefsmonitor) may name a command, with version-dependent interpretation. Also inspect conditional configuration whose applicability can change at the new path or branch. Do not display credential-bearing configuration wholesale.

Use only understood, authorized helpers. Where policy permits suppression of incidental helpers, use reviewed command-local controls compatible with the installed version; do not persistently rewrite shared/global settings. Do not bypass intentional organizational controls. If the safe execution boundary cannot be established, stop before materialization and return the proposed setup.

Record the original HEAD/branch, staged and unstaged state separately, untracked files, relevant ignored assets and any operation in progress. [Git status](https://git-scm.com/docs/git-status) explains optional index refresh writes; use a supported nonrefreshing inspection route when index-byte preservation matters. A clean tracked diff is not evidence that ignored assets are absent. Hash or otherwise identify the particular local work being preserved without copying sensitive contents into the report.

Leave the original branch and any merge, rebase or cherry-pick alone. Do not stash, reset, clean, commit or switch there. Capture only the preservation detail needed for the task; a whole repository export is unnecessary and may expose unrelated data.

## 3. Pin the target and reserve a safe location

Resolve the requested source to a full commit ID and record which name supplied it. For an existing branch, record both its full ref and observed tip. Resolve tags to commits rather than assuming a tag names a commit directly. Keep replacement-object views distinct from the actual pinned objects: use the installed Git's supported nonpersistent no-replacement control consistently during target inspection, materialization and verification. If a replaced view is specifically required, resolve that separate contract before proceeding; do not claim original-object identity for replaced content. Do not use the original checkout's dirty files as the implicit source of a second committed checkout.

Check availability of required tree/blob objects and any external payloads. For offline scope, prevent implicit object acquisition using installed-version-supported controls from [Git's global options](https://git-scm.com/docs/git), as well as avoiding explicit fetch. A partial clone may have a readable commit but lack source bytes. If approved acquisition is necessary, record the endpoint and resulting pinned target; never silently substitute a newer available revision.

Inspect the target tree for submodules, symlinks, path collisions, conversion needs and unsupported filesystem names. Account for sparse-checkout settings rather than equating a successful command with full source availability. Hold a required source representation that cannot be materialized safely on this filesystem. Do not normalize filenames or weaken filesystem protections to force success.

Use a fresh, absent destination outside every existing worktree and outside application watch/output folders. Verify its parent, real path, permissions and free space. Reject symlink redirection, case-equivalent collisions and an existing registration at that location. Choose a short recognizable name without embedding confidential task details. Do not reuse a populated directory even if its contents look temporary.

For a new branch, validate the proposed name using the installed Git interface and require nonexistence. For an existing branch, recheck its identity and occupancy immediately before creation. If another process changes either, reassess rather than overwriting its work.

## 4. Create exactly the selected checkout

Derive the invocation from installed help and the reviewed configuration. The following are command shapes, not commands executed by this guide; all uppercase values must be replaced with verified, safely quoted arguments, and required command-local controls must be included:

```text
git -C REPO worktree add --detach DEST COMMIT
git -C REPO worktree add -b NEW_BRANCH DEST COMMIT
git -C REPO worktree add DEST EXISTING_LOCAL_BRANCH
```

Use an explicit source and mode instead of basename-derived or remote-guessing defaults. Do not use force or branch-reset variants. A detached checkout is appropriate only when its no-branch status matches the request. If the operator later needs to commit there, first obtain the intended fresh branch name and preserve the current commit under that branch; do not promise that an unnamed commit is durably handed over.

Execute only after the helper, source and destination checks pass. A no-checkout staging route may be useful when supported, but registration without files is a partial state, not completion; do not invent a generic reset command to finish it. If deliberate sparse materialization or worktree-specific configuration is needed, scope that separately and inspect its effect on siblings before proceeding.

Keep the new folder closed in editors that auto-run project tasks until their behavior is understood and authorized. Do not start a dev server to prove creation. Worktrees do not isolate ports, external databases, absolute output paths, shared caches or inherited credentials; any later execution needs its own environment and effects review.

## 5. Verify from the new location

Read back the final state independently of the creation message:

1. The exact destination is registered once under the intended common repository
2. The new checkout root and private Git/index locations resolve as expected
3. HEAD equals the pinned commit and branch/detached mode matches the decision; an existing branch tip has not changed unexpectedly
4. Required tracked files are present in the intended representation, with sparse paths, submodules and external payloads explicitly accounted for
5. New staged/unstaged state is understood; hook/filter output or partial checkout is not mislabeled as clean readiness
6. The original HEAD, staging, working files, relevant refs and ongoing operation agree with the preservation evidence, apart from the intended new branch/registration

Use representative content checks plus the required-path inventory; checking one README does not establish that the requested source is present. Git object identity and working-file byte identity may differ legitimately through approved conversions. State which was checked.

Reinspect shared settings and source refs affected by the operation. Do not claim the common Git directory is byte-identical after adding a registration. If concurrent edits explain a difference, report the newer state without restoring the old snapshot over it. If preservation cannot be established, keep that uncertainty visible and stop further mutations.

## Interruption and recovery

On failure, inspect the actual branch, registration, directory and materialized files before retrying. A nonzero result can follow partial writes or a failing hook. Do not rerun with force or recursively delete the destination to obtain a clean retry.

- No registration, no destination and no new branch: after identifying a transient cause, a bounded retry of the same approved operation may be appropriate
- Any state exists: record which pieces were created and whether local work has appeared; resume only through a reviewed supported route that preserves them
- Branch or destination belongs to another task: stop that path and ask for an alternate identity or owner decision
- Registration points to a missing/moved location: locate the real checkout or unavailable volume first; do not prune to hide the discrepancy
- Source bytes or helper permission unavailable: leave the setup partial and identify the exact missing requirement

Git documents lock and repair operations for worktree registrations in its worktree manual. Use them only for a diagnosed, authorized need; a lock is not a concurrency mutex or access-control mechanism. Never edit administrative links by hand as routine recovery. Creation does not authorize retirement: removal of a directory or branch is a separate requested action with fresh preservation checks and any required deletion confirmation. Keep detached commits, ignored assets and untracked work in that future check.

## Handoff and stopping condition

Return the exact new path, safe repository label, branch or detached status, full commit ID, source completeness, preservation result and any intentional shared-state change. Include the minimal command or editor path needed to enter the new directory, without automatically running the application. List excluded execution and the next concrete blocker only when relevant.

Stop when the requested checkout is registered, materialized and checked, or when further progress needs a specific unavailable object, destination, authority or user decision. Distinguish "proposal prepared," "registered only," "source ready" and "application verified." Only the first three belong to this workflow by default.

## Fictional, unexecuted illustration

A fictional Cedar repository has staged documentation edits and an untracked sketch in its main checkout. Its `release` branch is already open in another worktree. The user wants to inspect the observed release commit in a new local folder while leaving both existing checkouts alone.

The proposed choice is a detached checkout at the pinned release commit, because advancing `release` is not requested. Before creation, a configured checkout filter is discovered. If its effects are not authorized, the plan stops before checkout and identifies that exact blocker; it does not retry by forcing branch occupancy or claim that an empty directory contains usable source.

After an approved safe materialization route, acceptance would require the new registration and exact commit, the requested source files, unchanged original staging/sketch, and unchanged release-branch occupancy. If the user instead needs to develop a fix, a fresh explicitly named branch is a different agreed outcome. These are authored decisions and expected checks only: no Git operation, project program, checkout, test or external action was performed for this illustration.
