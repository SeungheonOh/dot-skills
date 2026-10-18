---
name: prepare-git-bundle-handoff
description: "Prepare a bounded offline Git history bundle and verify its advertised refs, object closure and recipient prerequisites without checking out or executing source. Use for disconnected history transfer, not a source ZIP, whole-machine backup, lost-work discovery or merging received work."
---

# Prepare an offline Git history handoff

Deliver a Git bundle that another authorized repository can consume, with a precise statement of what history it supplies and what the recipient must already have. A bundle file's existence does not establish independent recoverability. The central decision is whether the handoff stands alone or deliberately depends on earlier history.

Use [portable project handoff](../portable-project-handoff/SKILL.md) for ordinary selected files, [Git archive contents](../define-git-archive-contents/SKILL.md) for a source snapshot, and [missing Git work recovery](../recover-missing-git-work/SKILL.md) to discover historical candidates. This workflow transfers known Git history; it does not find missing edits, apply received changes or promise a complete backup of local state.

## Define the history contract

Establish:

- Authorized source repository and exact branches or tags to transfer
- Recipient or destination class, intended use and whether delivery is included
- Fresh private output location, available space and transfer-size ceiling
- Sender and recipient Git versions and object formats when known
- Whether the recipient has no history or a specifically evidenced prerequisite history
- Whether local artifact creation and isolated import verification are authorized, or only a proposal is requested

Resolve selected names to full refs and object IDs. Preserve annotated-tag identity separately from the commit it names. Record the selected objects independently of the bundle command so an omitted ref remains detectable. Do not infer that similarly named recipient branches contain the same history.

Prefer a self-contained handoff when recipient prerequisites cannot be established. An incremental handoff is useful only when its dependency can be described and checked. Do not use a recent date or arbitrary commit count as a substitute for a known recipient baseline. If the size ceiling cannot accommodate a complete permitted handoff, return the tradeoff; do not silently shorten history.

## Review historical disclosure and source boundaries

History can expose removed files, previous credentials, author identities and commit messages that are absent from today's checkout. Confirm that the selected reachable history is appropriate for the intended recipient. Do not use path exclusions, `.gitignore`, sparse checkout or export rules as a secrecy filter for a history bundle. If secrets or prohibited information are discovered, hold delivery and report the safe finding without reproducing the values. Rewriting history or rotating credentials is separate authorized work.

Preparation does not authorize upload, email or publication. Verify the intended local destination is not already shared or synced beyond the approved audience. Sharing requires the package and audience to be authorized, including any sensitive content. Keep hashes and safe ref labels in reports rather than copied private commit bodies or raw remote configuration.

Record excluded local state: unstaged/staged edits, untracked or ignored files, reflog-only candidates, local configuration and hooks are not part of this selected-ref handoff. A stash is not an implicit inclusion: leave it outside the selection unless a separately reviewed transfer explicitly requires it. LFS payloads and submodule repositories require separate completeness decisions; pointer files and gitlinks do not supply those external objects. Do not fetch them or broaden the package automatically.

Inspect the real repository/common-directory relationship, shallow boundaries, partial-clone promises and alternate object stores. Source objects borrowed from an alternate store must be available during creation; the final independence claim must be tested without relying on that store. For this ordinary workflow, hold shallow or filtered/incomplete history until a separately authorized route can establish the requested closure. Never present a tip-only approximation as complete history.

## Make the operation bounded and nonexecuting

Read local instructions and relevant Git configuration without dumping secrets. Before invoking Git, inspect environment overrides and configured helpers that could change the target or execute code. Use installed-version-supported nonpersistent controls to avoid pagers, replacement-object views, optional index refresh and lazy object fetching where relevant. Git documents these controls in its [global options](https://git-scm.com/docs/git); a flag that suppresses one behavior is not a universal sandbox.

Do not run checkout filters, project programs, hooks or automatic maintenance as an incidental verification shortcut. Inspect the intended commands' helper and hook behavior. Keep the source worktree, index, refs and any in-progress operation untouched. Do not stash or commit dirty work merely to include it. If a safe understood command route is unavailable, finish a proposal and identify the blocked operation.

Before artifact creation, capture the preservation baseline through that reviewed read route: HEAD and selected/relevant ref identities, index entries or byte identity, staged-versus-unstaged state, affected working-file identities and any in-progress operation state. Include valuable untracked or ignored work that the operation could affect, without copying private contents into the report. Keep the baseline separate from the artifact selection. If a required before-state cannot be observed, mark that preservation claim unavailable rather than inferring it from a later clean status.

Creation uses selected named refs. The [bundle manual](https://git-scm.com/docs/git-bundle) distinguishes complete history from exclusions that require earlier objects, and requires a named advertised ref rather than an arbitrary bare object ID. Use exact full ref names and record their observed IDs. Avoid `--all`, which can include unintended refs. If a target is only an object ID, ask for the intended transfer ref or use a separately authorized fresh reference; do not modify an existing branch to make it bundleable.

Recheck selected refs just before creation and inspect their IDs in the resulting bundle afterward. A moving branch means the artifact must be held if it no longer matches the approved snapshot. Do not silently relabel a different tip as the original. A deliberately frozen ref needs its own safe nonexistence and hook checks; it is not mandatory when the source is stable and the resulting identity can be verified.

Use a fresh absent output under an owned directory and do not overwrite an existing bundle. Reserve space for both the artifact and its verification repository. The following are invocation shapes only, not executed commands; replace every uppercase value with a verified safely quoted argument and add applicable reviewed command-local controls:

```text
git -C SOURCE bundle create NEW_BUNDLE FULL_REF
git -C SOURCE bundle create NEW_BUNDLE FULL_REF ^BASE_COMMIT
git bundle list-heads NEW_BUNDLE
```

Use the second shape only for the agreed incremental contract. Record all actual prerequisite IDs emitted by the bundle; do not assume the header contains exactly one prerequisite merely because one exclusion was supplied. The [bundle format](https://git-scm.com/docs/gitformat-bundle) describes prerequisite records, advertised refs, object-format and filter capabilities. Hold an unexpected filter capability for this complete-object workflow. Select a supported format rather than forcing a legacy format incompatible with the repository's object algorithm.

## Verify the actual saved artifact independently

Keep ref identity, object integrity, closure and source readability separate. Record the exact output path, byte size and SHA-256. A matching file digest establishes byte agreement with the supplied baseline, not trusted authorship or safe code.

1. List every advertised ref and compare its object ID with the independent approved selection. Detect extras and omissions, including unintended tags or HEAD advertisements
2. Inspect format/capabilities and the actual prerequisite list. Match them to the declared self-contained or incremental contract
3. Create a fresh owned verification repository using the correct object format, inspected template/configuration and no source alternates. Avoid an ordinary source clone that could inherit or borrow extra objects. [Git init](https://git-scm.com/docs/git-init) documents template and object-format controls
4. For self-contained scope, start with an empty object store. For incremental scope, seed only the independently approved prerequisite history, then verify it; record how that baseline was obtained and do not substitute the sender's full store
5. Run the installed Git's bundle verification in that repository, then import the bundle's objects through the supported object-import route without checkout. The bundle manual distinguishes prerequisite verification from `unbundle`, which stores objects and reports refs without serving as a working-tree restoration
6. Check imported object integrity and traversal from each exact advertised root. Use [Git fsck](https://git-scm.com/docs/git-fsck) with explicit selected roots and inspect missing-object or connectivity failures. Do not rely on default ref discovery when no refs were created by the object import
7. Read representative required trees/blobs from this isolated store, preserving raw object identity. Verify requested history reachability with an understood bounded [revision traversal](https://git-scm.com/docs/git-rev-list). Keep shallow, replacement and promisor behavior from masking absence
8. Recheck the artifact digest and source preservation evidence. Report concurrent source changes rather than undoing them

Keep verification offline when that is the contract. An import that obtains missing data from a remote has not established standalone closure. Do not check out source or execute code to prove its object graph exists. Materialization, dependency installation and application behavior are later workflows.

For an incremental bundle, successful verification in the sender's repository proves little about the recipient. If the actual recipient baseline is unavailable, report the dependency IDs and label recipient applicability unverified. A failed check in an empty store may be the expected consequence of declared prerequisites, not bundle corruption. Conversely, an incremental artifact must never be delivered as an initial full clone.

## Recovery and delivery

After interruption, inspect the output and scratch store before retrying. Preserve diagnostic evidence and leave incomplete artifacts clearly marked and out of delivery. A revised attempt should use a fresh output identity; deletion of old files or verification repositories requires the appropriate cleanup authority. Do not run garbage collection, prune the source or remove alternates to simulate independence.

On missing prerequisites, request the correct baseline or offer a separately approved self-contained package. On an unexpected ref or moved tip, refresh the selection and regenerate only within the authorized scope. On incomplete source objects, identify the missing source boundary; do not silently fetch, rewrite refs or weaken the acceptance contract. If the artifact exceeds the size limit, present options without switching transfer providers.

Hand over the exact bundle, digest, selected full refs/object IDs, format, prerequisite manifest, intentional exclusions, source-preservation result and checks actually observed. Include an import plan that uses a fresh inspection repository first. Updating an existing recipient branch, merging, pushing or executing source is not implied by receiving the artifact. Do not recommend a blind pull as the default inspection step.

If delivery is authorized, verify the destination and access, transmit only the reviewed artifact and companion manifest, and check the available delivery evidence. Distinguish preparation, isolated import, recipient applicability and delivery. Stop at the requested state or a precise unresolved prerequisite; no ongoing synchronization is created.

## Fictional, unexecuted example

A fictional Cedar repository has a `refs/heads/offline-review` branch and unrelated staged notes. A colleague needs its history on a disconnected machine. The sender remembers that the colleague once had an earlier release, but has no exact baseline evidence.

The proposed outcome is a self-contained bundle of the one selected branch, leaving the notes and other refs untouched. A size concern is not sufficient reason to change it to `release..offline-review`. Acceptance would require the advertised branch to match its recorded full object ID and the saved bundle to import into a fresh empty compatible object store without alternates or network access. The staged notes remain explicitly excluded.

If the colleague later establishes an exact complete prerequisite history, an incremental artifact becomes a different documented choice. Its actual prerequisite records must still be inspected and tested against that baseline. These are authored decisions and expected results only. No bundle, repository, import, command execution, live check or delivery was performed for this example.
