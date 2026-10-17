---
name: restore-pinned-submodules
description: "Initialize or realign a selected Git submodule tree to its recorded commits, reconciling per-level gitlinks, URLs and local work without advancing dependency versions. Use for missing or mismatched dependency checkouts, not dependency upgrades or merging submodule development."
---

# Restore the dependency commits the project records

Deliver the selected dependency working trees at the intended recorded commits, with local work preserved and an explicit account of anything still unavailable. An empty dependency directory, a fetched repository and a matching commit are different states. None alone establishes that all requested nested source is present.

Use [dependency-upgrade-plan](../dependency-upgrade-plan/SKILL.md) when choosing a new dependency version, [recover-missing-git-work](../recover-missing-git-work/SKILL.md) when the task is finding lost local history, and [parallel-change-integration](../parallel-change-integration/SKILL.md) when local contributions must be merged. This workflow restores existing pins; it does not choose replacement commits or repair application behavior.

## Inputs, outcome and authority

Resolve from the request and repository instructions:

- Authorized superproject checkout, intended revision or accepted index state, and installed Git version
- Selected submodule paths, whether their nested dependencies are included, and intentionally excluded components
- Requested outcome: read-only diagnosis, a proposed repair, or actual local initialization/realignment
- Allowed source repositories, existing local mirrors/URL overrides, network constraints and permitted destination
- Local changes or unpublished work to preserve, relevant filesystem constraints, and any separately requested build or test

A request to restore named submodules can cover ordinary local initialization and checkout within that scope. A diagnostic request cannot silently become a mutation. Acquisition from an additional destination, running dependency programs, installing tools, changing security settings or creating ongoing account access needs the appropriate authority. Reuse clear existing approval; ask only for a missing decision or permission that changes the next step.

Keep the superproject branch, staged gitlinks and tracked configuration unchanged unless their alteration was specifically requested. Do not stage a newly checked-out dependency, rewrite `.gitmodules`, push a commit, or change a pin to make an unavailable dependency appear fixed. Return a private path-level record with intended commit, observed result, preservation evidence and remaining blocker.

## 1. Separate the three commit identities

Record the superproject's immutable HEAD and the selected paths' committed-tree entries, index entries and actual submodule HEADs. A gitlink is a commit reference in the containing repository, not a directory whose contents are stored in that repository. The child commit need not exist in the parent's object store. Git's [submodule model](https://git-scm.com/docs/gitsubmodules) explains this separation.

Use the [tree listing](https://git-scm.com/docs/git-ls-tree) for a named commit and the [index listing](https://git-scm.com/docs/git-ls-files) for staged mode, object ID and stage. Keep full object IDs and exact paths; use supported literal path handling and NUL-delimited output rather than splitting filenames on whitespace. Identify mode 160000 entries, missing mappings and file/directory conflicts. A directory merely containing a Git repository is not sufficient evidence that it is the expected submodule.

Choose one target authority before updating:

- If restoring the current committed project, the selected stage-zero gitlinks must agree with that commit
- If restoring an explicitly accepted staged dependency state, record that index snapshot as the target; do not describe it as the committed project
- If the user named another superproject revision, inspect its pins without silently switching the original checkout. Use a separately authorized checkout or resolve the revision-change decision first

An unexplained staged gitlink change or unmerged entry is a hold for that path, not permission to choose HEAD, ours or theirs. Do not resolve a merge merely to initialize a dependency. Record other staged/unstaged changes without treating unrelated dirty files as a universal blocker.

For every selected edge, keep the containing repository identity, logical submodule name, relative path, target gitlink, current child HEAD, initialization state and reason for any discrepancy. Names can differ from paths. Nested targets come from each immediate parent's intended tree/index, not from the root project or the child's newest branch tip.

## 2. Inspect the work that an update could disturb

Establish the real working tree, Git directory and common-directory relationships. A submodule's `.git` may be a file pointing into another directory; linked worktrees and older embedded Git directories need their actual paths recorded. Do not delete or relocate administrative directories to repair registration.

Before moving any populated parent, inspect existing descendants that might be affected, including ones absent from the target revision. Record per-repository HEAD/branch, staged and unstaged work separately, untracked files, valuable ignored files, ongoing operations and local commits that would lose their only useful name. A parent-level status summary does not preserve its children's work, and a root stash is not a recursive backup.

Read relevant configuration without dumping credentials. For status inspection, prevent optional index refresh writes when preservation requires it, and do not rely on submodule-ignore settings to expose dirty work. [Git status](https://git-scm.com/docs/git-status) documents both the optional refresh and the `--ignore-submodules=none` override. Inspect each affected child directly as well; a matching child HEAD does not prove its working tree is clean.

Treat Git operations as potentially executable. Inspect effective hook locations, filesystem-monitor settings, attributes and configured conversion drivers before status or checkout. [Hooks](https://git-scm.com/docs/githooks) can run after checkout, and [attributes](https://git-scm.com/docs/gitattributes) can invoke smudge/process filters, including payload acquisition. Use an understood, installed-version-appropriate, nonpersistent way to suppress unapproved helpers, or stop before that operation. Merely disabling optional locks does not disable helpers. Do not bypass an intentional control or alter global settings to force progress.

For an offline inspection, prevent automatic object acquisition as well as explicit fetches. [Git's global options](https://git-scm.com/docs/git) include controls for lazy fetch, replacement objects and optional locks; verify support in the installed version. Keep an alternate/replaced view distinct from the actual recorded objects. An unsupported safe-read route leaves the affected observation unknown.

If local work overlaps the required movement, pause that edge or use an approved separate destination. Preserve a detached local commit under an authorized fresh recovery reference before leaving it when otherwise only transient history protects it. Do not automatically stash, hard reset, clean, deinitialize or force checkout. A recorded commit ID is useful evidence, but is not a backup of uncommitted or untracked bytes.

## 3. Resolve the source at each level

For the target parent state, compare its committed/index `.gitmodules` with the working copy and relevant local configuration. Hold malformed, missing, conflicting or unexplained edited mappings. Do not combine a gitlink from one revision with a convenient URL/path map from another.

The [`.gitmodules` reference](https://git-scm.com/docs/gitmodules) defines the name-to-path/URL mapping and the optional update, branch and shallow settings. Check the actual path's type and containment before use; a pre-existing unrelated repository, symlink, populated nonrepository directory or case-colliding path needs reconciliation. Do not overwrite it or guess a rename.

Record the intended source and the effective source separately:

1. The target `.gitmodules` URL, including any relative form
2. The containing repository's default remote used to resolve that relative URL
3. Existing local `submodule.<name>.url`, activation/update choices and the populated child's fetch remote
4. Relevant URL rewrites and the final endpoint/protocol that an operation would contact

The [submodule command reference](https://git-scm.com/docs/git-submodule) defines default-remote selection and initialization. Initialization seeds missing local configuration but preserves existing values. Synchronization replaces local URL configuration from `.gitmodules`; it is not a harmless prerequisite. Preserve intentional mirrors, access-method overrides and inactive components unless the task requires an approved change.

Use scoped initialization when needed, then set only an already approved local override before acquisition. Synchronize only selected entries whose old/new destinations and override consequences are understood. Inspect relevant [configuration behavior](https://git-scm.com/docs/git-config), including command-valued filesystem monitors and `url.*.insteadOf`; record safe endpoint identities without credential-bearing URLs.

A root-level source approval does not automatically approve every newly discovered nested destination. Inspect each new child's intended metadata before contacting its dependencies. Never weaken TLS/SSH checks, protocol restrictions or repository trust settings to silence an acquisition error. Use the authorized sign-in route when needed; do not put credentials into `.gitmodules`, commands or the report.

## 4. Acquire the pinned objects without selecting new versions

Check object availability in the correct child repository. Distinguish an absent clone, a missing commit, missing tree/blob objects, a shallow-history boundary, a partial clone, and unavailable external payloads. A readable commit header is not enough to materialize its tree. An LFS pointer is not the referenced file payload.

When acquisition is authorized, use the reviewed source and a bounded operation sufficient for the target commit. Disable incidental recursive fetches so they cannot contact unreviewed descendants. [Git fetch](https://git-scm.com/docs/git-fetch) documents recursion controls, shallow-history options and partial-object filters. Fetching changes local object/ref state; it does not move the target gitlink or prove that checkout succeeded.

If acquisition would immediately materialize an unread target, separate those stages with a supported no-checkout route. Inspect the acquired target's checkout attributes and nested metadata before materialization; existing working-tree metadata cannot stand in for a different target revision. If the available route cannot enforce that boundary, hold checkout rather than executing unknown filters to discover what they do.

If a shallow clone lacks the pin, inspect the advertised source/ref relationship and obtain the necessary history within scope. Do not assume every server accepts a raw object-ID fetch or that deepening an unrelated branch will supply the commit. If the approved repository cannot supply the required object, report that exact pin/source pair and the evidence. The owner may need to publish the missing dependency commit or provide an authorized archive/bundle; do not substitute a nearby tag, latest commit or another host.

Keep retry reasons concrete. Authentication, forbidden transport, an unavailable object and interrupted transfer are different failures. Retry a transient interruption only after checking existing partial state. An unchanged access denial or confirmed unavailable pin calls for a decision, not a broader clone or repeated requests. Respect offline scope even when Git could fetch missing objects on demand.

## 5. Align one reviewed parent-to-child edge at a time

Recheck the target index entry, mapping, local work and effective source immediately before mutation. If another process changed them, reconcile the new state rather than restoring an old snapshot over it.

Use the installed Git's selected-path submodule update with an explicit checkout procedure. Under [the documented update semantics](https://git-scm.com/docs/git-submodule), this chooses the containing index's pin; `--remote` instead selects a remote-tracking commit. Do not use `--remote`, merge/rebase update modes, pull or force for pin restoration. Explicit checkout avoids an inherited custom update command. Matching an already-checked-out pin may require no movement; detached HEAD is normal when checkout occurs, not a defect to fix by creating a dependency branch.

Start without blanket recursion. Inspect and nonpersistently suppress inherited checkout recursion, including [submodule.recurse](https://git-scm.com/docs/git-config#Documentation/git-config.txt-submodulerecurse), while operating on one reviewed edge; omitting a recursive flag alone does not establish that boundary. Use supported command-local controls or hold the operation if the boundary cannot be enforced. After aligning a parent, read its intended nested mapping and inspect the actual nested working state again. Earlier metadata from a different parent revision may no longer apply. Expand only along the agreed dependency subtree, repeating source review, preservation and pin checks at every level. A recursive operation is appropriate only when the full affected closure, destinations and local state have already been reviewed; a familiar root path is not that review.

If only a deep child was requested, establish whether its ancestors already represent the intended revisions. Do not move an unapproved ancestor as a hidden prerequisite. Likewise, nested components that disappeared from the target can leave existing directories or administrative data behind; identify them as retained out-of-target state rather than deleting them.

Record each completed edge and the actual result before proceeding. A later failure does not undo earlier initialization, URL changes, fetches or checkouts. Do not interpret a nonzero exit as proof that no files moved; a post-checkout hook can fail after the checkout. Inspect current state before a retry or recovery.

## 6. Verify the requested closure and preserved work

Build the expected dependency list from the agreed target pins and mappings, independently of what a recursive status command happens to display. Uninitialized, inactive or inaccessible descendants must remain in that denominator when they are part of the requested scope. An omitted path is not a successful path.

For every requested edge verify:

- Actual child HEAD equals the full intended gitlink and the expected working tree exists at the correct path
- Required tracked source is materialized, with sparse checkout, missing objects, conversion/filter effects and external payload exclusions made explicit
- The child's own staged/unstaged/untracked state agrees with the preservation plan; no dirty state is hidden by parent ignore settings
- Nested edges are resolved against that exact parent's target state, and each is completed, intentionally excluded or blocked
- Local source configuration changes are limited to the approved entries; retained overrides and excluded siblings remain intact

Use submodule status only as a cross-check: its leading `-`, `+` and `U` flag uninitialized, index-mismatched and conflicted entries respectively. A normal prefix establishes neither clean child contents nor complete nested coverage. Compare the root HEAD, staged gitlinks, tracked `.gitmodules` and unrelated work with the initial evidence. The selected child's index/working tree may intentionally change during checkout; do not claim every index or all Git administrative bytes stayed identical.

Separate source restoration from execution readiness. A structural pin/working-tree check does not show that dependencies build, tests pass, generated files are fresh or licenses permit a new use. Run a build or application check only when separately within the requested execution scope. Report it independently and tie any result to the final restored state.

## Recovery, delivery and stopping

Return a concise restoration record: superproject target authority, selected closure, per-path expected/actual commits, preserved local work, applied local configuration changes, acquisition/materialization results and exact unresolved source or decision. Keep safe source links where useful and omit secrets. Clearly distinguish inspected, configured, acquired, aligned and verified states.

After interruption, resume from observed per-path state. Preserve fetched objects and local recovery references. Reverting a local URL change requires checking that the value still equals this task's write; do not restore an entire old config over concurrent edits. Moving a child back to its previous commit likewise requires renewed worktree and descendant checks. A checkout rollback does not undo filters' side effects, restore discarded data or remove acquired objects. Never delete `.git/modules`, force-deinitialize or garbage-collect as routine cleanup.

Stop when every requested dependency is aligned and the preservation checks are satisfied, or when the next edge requires a specific unavailable object, access, authority or user decision. A partially restored tree remains a useful partial result. Do not alter dependency versions or broaden acquisition merely to produce an all-green summary.

## Fictional, unexecuted illustration

A fictional Atlas project records `vendor/renderer` at commit R. The index instead stages commit S, and the current renderer checkout is at S with an untracked debugging note. Renderer R records `codecs/fast` at commit C. A local mirror override exists for the renderer, while the codec is uninitialized and its source is a relative URL.

A request to restore Atlas's committed dependencies would first hold the R-versus-S target conflict without unstaging S. If the owner chooses a separate checkout of the committed Atlas revision, the proposed work would retain the original note and staging, review the mirror for that destination, acquire R, and derive C plus its source from renderer R. It would resolve the codec URL against renderer's applicable default remote, not Atlas's root directory. An approved mirror lacking C would leave the codec explicitly blocked; a newer codec commit would not satisfy the pin.

Acceptance would require renderer R and codec C at their intended paths, complete requested source, and evidence that the original staged pin, note and local overrides survived. These are authored decisions and expectations only. No repository was cloned, command executed, dependency checked out, test run or external configuration changed for this illustration.
