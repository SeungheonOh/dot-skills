---
name: recover-missing-git-work
description: "Locate missing committed or stashed work in an authorized local Git repository and preserve identified candidates under fresh recovery references or separate files. Use after a reset, deleted branch, detached-HEAD session or dropped stash; not disk forensics, rewriting shared history or merging recovered work into current edits."
---

# Recover Git work without resetting the present

Deliver the identified historical work in a durable, inspectable form while preserving the current branch, index and working files. A commit mentioned in a log is a candidate, not a completed recovery. Confirm its content and preserve the necessary objects before saying the work is recoverable.

Use [recover-unsaved-editor-work](../recover-unsaved-editor-work/SKILL.md) for content that remained only in an editor, [backup-restore-spot-check](../backup-restore-spot-check/SKILL.md) for a known backup, and [parallel-change-integration](../parallel-change-integration/SKILL.md) when already identified changes must be combined. This workflow finds and preserves Git-backed candidates; it does not decide which historical change should replace current work.

## Establish the missing work and preserve the present

Identify the authorized local repository/worktree, installed Git version, event sequence, approximate time, former branch or stash name, likely paths and recognizable content anchors. Ask whether the work was committed, staged, stashed or merely edited, while allowing uncertainty. Obtain the private output location and requested result: read-only candidate report, new recovery reference, selected files, or an isolated recovered checkout.

A recovery request can cover new local recovery refs and separate copies when that is the requested result. A read-only investigation cannot silently create them. Do not reset, switch, clean, stash, pop, drop, expire, prune or run garbage collection in the source. Leave existing merge/rebase/cherry-pick operations intact. Do not push, fetch or rewrite shared branches as an implied recovery step.

Read repository instructions and establish the real Git directory, common directory and worktree relationship. A linked worktree's .git file may point elsewhere. Check for shallow/partial history, alternate object stores, submodules and Git LFS or other clean/smudge filters. A committed pointer is not necessarily the missing large-file payload.

Use nonmutating inspection options, disable unneeded pagers and external diff/text-conversion helpers, and prevent implicit network retrieval. Current Git documents --no-optional-locks, --no-replace-objects and --no-lazy-fetch in [its main reference](https://git-scm.com/docs/git); check installed support. Treat replacement refs as an explicit alternative view rather than confusing replaced content with original object bytes. If a safe read path is unavailable, stop that operation rather than weakening trust or access settings.

Before status or index inspection, check configured filesystem-monitor behavior. [core.fsmonitor](https://git-scm.com/docs/git-config#Documentation/git-config.txt-corefsmonitor) can name an executable hook; --no-optional-locks does not disable it. Use an installed-version-appropriate, nonpersistent command override that disables fsmonitor, or another understood read route, without editing repository/global configuration. Do not assume older Git versions interpret Boolean settings like newer versions.

Capture enough source state to support the preservation claim: HEAD/branch, relevant refs, staged and unstaged identities separately, index entries or bytes, untracked/relevant ignored files and in-progress operation metadata. Avoid dumping secrets from configuration or file contents into a report.

Do not copy the whole repository into a public or synced location. A preservation snapshot must account for its actual object stores and concurrent writes. A fresh clone is not automatically a complete recovery snapshot: source reflogs and unreferenced candidates are not a promised clone contract, and shared/alternate objects can remain dependent on the source. The [clone reference](https://git-scm.com/docs/git-clone) also warns of local-copy races. Prefer identifying and preserving the bounded candidates over making unsupported completeness claims.

## Search from strongest clues to wider candidates

Start with available current refs and local history. The work may still be on another branch or already reachable under a different commit. Compare content and ancestry; identical subjects or nearby timestamps do not identify the same work.

Inspect the relevant HEAD/branch reflogs, then the stash list and stash reflog when appropriate. [Reflogs](https://git-scm.com/docs/git-reflog) record local reference movements and can locate a previous branch tip. They are local evidence with retention limits, not a remote backup or a complete history of file edits. Do not promise a fixed recovery window from default expiration settings.

Resolve a useful reflog selector to its full object ID immediately; positions such as HEAD@{2} and stash@{1} can move. Record where it was found, the observed log time, object type and relevant content evidence. Distinguish author/committer times from the time a local reference moved.

For each likely candidate:

- Verify that the object exists locally and has the expected type
- Inspect the actual tree or selected blob, parents and scoped differences without checking out or executing it
- Compare the user's known anchors and affected files; preserve competing candidates when evidence is insufficient
- Note absent children, missing payloads or unsupported types instead of treating a readable commit header as a complete tree
- Prefer the smallest useful range or selected paths; broaden only when the recorded clues fail

If ref/reflog inspection is insufficient, use a bounded, read-only unreachable-object search in the authorized object stores. [git fsck](https://git-scm.com/docs/git-fsck) distinguishes unreachable objects from dangling tips. A search excluding reflogs from the roots can expose more historical candidates; it does not resurrect deleted objects. Avoid --lost-found for a read-only search because it writes files.

Set a practical search scope and output limit before enumerating a large store. Inspect candidate metadata before dumping blob contents. A dangling blob can contain useful bytes without a recoverable path, timestamp, surrounding project or proof that it is the desired revision. Label those limits. If the store is changing, corrupt, inaccessible or the relevant objects were pruned, preserve the evidence and report the exact remaining gap; repeated scans do not manufacture missing bytes.

## Handle a stash as several states

Do not treat a stash as an ordinary single-parent feature commit. Git's [stash documentation](https://git-scm.com/docs/git-stash) describes its base, saved working-tree tree and saved index tree. Record these separately so staged versus unstaged work is not collapsed.

Check whether untracked or ignored content was actually included and available; never infer it from the presence of a stash or a filename remembered by the user. Inspect additional saved content through the installed version's supported stash/object interfaces. A partial stash may intentionally cover only selected paths or hunks.

A WIP subject or multiple parents is a search clue, not proof of stash identity. Validate the object's topology and contents. Do not apply an arbitrary merge commit as a stash. A dropped entry may still have objects, but recovery is not guaranteed.

Preserve the selected stash object before any later restoration. Do not use stash pop or stash branch as a harmless preview: they change the working state and can remove the stash entry. For this recovery task, retain the original saved index/worktree distinction and deliver the preserved candidate or separate inspected files. Applying it to a working branch is a subsequent integration action unless expressly included.

## Preserve a verified candidate without overwriting anything

Choose the least disruptive result that meets the request:

**Historical commit or stash:** Create a new, clearly named recovery reference pointing to the exact verified object through a supported Git operation. Check that the name is unused and make creation fail if another process creates it first; [update-ref's create operation](https://git-scm.com/docs/git-update-ref) supports a nonexistence precondition. Do not force-update a preexisting name. Inspect applicable hooks before any ref write, including the [reference-transaction hook](https://git-scm.com/docs/githooks#_reference_transaction); do not run repository-supplied hooks merely to recover content. Read back the new ref and reachable object availability. A new ref preserves reachability in that repository; it is not an independent backup.

**Selected files:** Read the selected blob bytes into fresh files in the private destination using a byte-preserving route. [git cat-file](https://git-scm.com/docs/git-cat-file) exposes stored object content; its textconv/filters options intentionally transform content and are inappropriate for a raw-byte recovery claim. Record original tree path, blob ID, type/mode, destination and any conversion. Safely map paths and collisions; do not materialize symlinks or special entries blindly. Keep a symlink target as labeled data when a safe link restoration was not requested.

**Isolated checkout:** Only materialize when requested and when its effects are understood. Prefer an independent destination; a linked worktree shares refs/object storage. Control hooks, filters, submodules and automatic editor tasks before checkout. Verify the exact selected revision and disclose any missing large-file payloads, submodules or filtered representation. Do not run recovered programs or install dependencies to establish content recovery.

For a standalone blob with unknown filename, use an object-ID-based neutral name and preserve its original type. Do not invent a path or reconstruct surrounding history from similar text. For a history bundle or other portable result, establish and verify its required object closure separately; the presence of a local reference alone does not prove portability.

If preservation times out or returns an uncertain result, inspect the exact reference and destination before retrying. A known absent target permits a bounded retry; an existing different target is a conflict, not permission to overwrite. Read-only restrictions or unavailable write access leave a candidate report with preservation explicitly pending.

## Verify and hand over

Check the saved reference/files from their final location. Verify exact object or byte identity, relevant content anchors and required tree/file availability. Report separate states: candidate found, content matched, preserved locally, materialized, and completeness unresolved. A valid Git object proves its own recorded bytes, not that all work the user remembers was ever stored.

Compare the original HEAD, index, working files, relevant refs and operation state with the initial observations. The new recovery ref is an intended change; unrelated changes must be investigated and disclosed. Do not overwrite concurrent user edits to make a preservation comparison match.

Deliver:

- Recovery reference or files, exact object IDs and private provenance
- Which remembered changes are present, missing or uncertain
- Saved index/worktree distinctions for a stash and known payload exclusions
- Preservation checks and any unavailable comparison
- The next decision if several candidates remain, or the exact additional source needed

Stop when the requested recoverable work has been preserved and checked, the bounded sources are exhausted with explicit limits, or access/authority prevents the next meaningful step. Do not clean up old recovery refs, discard candidates or restore over present work automatically.

## Fictional example, not executed

A fictional developer deleted a branch after an interactive rebase and later noticed that a paragraph in a Markdown guide was missing. The current checkout has unrelated staged and unstaged changes.

The proposed search would inspect local reference history, pin the candidate's full ID, and compare the missing paragraph and adjacent content. If the original paragraph is present, the planned result is a fresh recovery reference plus a separate copy of that historical guide, with the current index and files left untouched. Two candidates containing different revisions would both be retained pending the user's selection. Finding only the commit header while its tree is missing would remain incomplete recovery.

This illustrates decisions and acceptance criteria only. No repository was searched, Git command run, object recovered, branch created, file written or code executed for the example.

