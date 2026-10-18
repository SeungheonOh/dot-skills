---
name: configure-git-lfs-tracking
description: "Introduce Git LFS for selected current asset paths, preserve their full payloads and existing staging, and verify the relationship between tracking rules, index pointers and local objects. Use for bounded forward adoption, not history rewriting, remote publication, locking administration or repository cleanup."
---

# Track large assets without losing their payloads

Deliver a scoped Git LFS configuration and, when requested, selected assets staged as pointers with their complete local payloads accounted for. A matching tracking rule is not proof that a file was converted; a pointer is not a backup of its object; and a local object is not evidence that another checkout can download it.

This workflow adopts LFS for new files or the current versions of selected tracked files. It does not rewrite earlier commits or reduce existing repository history. [Git line-ending configuration](../configure-git-line-endings/SKILL.md) owns text normalization; [pinned submodule restoration](../restore-pinned-submodules/SKILL.md) owns dependency repositories; [source archive contents](../define-git-archive-contents/SKILL.md) owns what an exported snapshot includes. LFS needs a separate payload-availability contract across Git's pointer storage and the LFS object store.

## Establish the selection and intended stopping point

Read repository instructions and existing attributes before asking for information already available. Establish:

- Repository/worktree identity, selected revision, installed Git and Git LFS versions, and actual execution environment
- Exact asset paths or justified future matching families, exclusions, expected sizes and available local space
- Whether each selected path is untracked, an ordinary indexed blob, already an LFS pointer, or conflicted
- Current staged and unstaged changes, existing LFS configuration, effective hook location and shared worktree/storage relationships
- Requested scope: proposal only, apply local configuration, stage selected current assets, and any separately authorized checkout verification
- Intended future consumers and LFS host, if known; leave unknown remote availability explicit

Choose LFS because these versioned assets need pointer-backed storage, rather than because a filename sounds large. Generated artifacts that do not belong in version control need a different selection decision. Do not convert every binary, add a lock policy or alter ignored-file rules as a side effect.

A configuration request does not inherently authorize staging, committing, uploading assets, altering shared hooks, installing software or accepting storage charges. Reuse explicit permission already given for the specific steps. If runtime access or installation authority is absent, finish the candidate and its path-level verification plan with application unrun.

## 1. Preserve the three existing representations

For each selected ordinary file, capture its current working-tree size and SHA-256, index entry/object identity if present, and committed identity if present. Preserve recoverable copies of valuable bytes before conversion in an approved private location. Keep staged content distinct from later working-tree edits. A path with partial staging needs reconciliation or a separate candidate; staging its full working copy would change the user's intended commit.

Do not treat a small text file as a payload merely because it has an asset extension. Check whether it is already a pointer. For ordinary v1 LFS pointers without extensions, the object ID is the payload's SHA-256 and size is its byte length; Git's blob ID identifies the pointer bytes instead. Empty files are a documented special case that pass through unchanged. See the [LFS pointer specification](https://github.com/git-lfs/git-lfs/blob/main/docs/spec.md). Hold malformed pointers, unknown extensions and missing payloads rather than wrapping pointer text into a new asset.

Keep a compact record:

```text
path | initial index/worktree relationship | payload size/SHA-256
intended attribute source | proposed index representation
local object availability | preserved copy | remaining decision
```

Include a nearby excluded asset so overly broad matching can be detected. Do not inventory unrelated private files or dump entire Git configurations, environment variables or credential-bearing URLs into the report.

## 2. Inspect the execution and storage boundary

Find the actual repository Git directory and common directory, not just a presumed `.git` folder. Inspect relevant filter settings, local/global attribute sources, filesystem-monitor configuration, hook paths and existing hooks before commands that may invoke them. Git's [hook documentation](https://git-scm.com/docs/githooks) includes index-change and push hooks; a staging operation is not necessarily just an inert file copy. Run only understood authorized helpers, or keep the result at proposal level. Do not bypass a denied control.

Inspect `lfs.storage`, any LFS stream extensions, custom transfer agents, `.lfsconfig` and relevant endpoint overrides. LFS can use storage outside the default directory, and its extensions can execute transformations during clean/smudge. This workflow assumes ordinary untransformed LFS payloads; hold an extension-based setup for its specific preservation contract. Inspect endpoint identities without contacting them. The [LFS configuration reference](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-config.adoc) defines these settings and the possibility of separate upload/download destinations.

Budget the original payload, retained preservation copy and local LFS object together. Replacing full Git blobs with pointers does not imply smaller local disk usage. Do not prune objects, remove backups or clear caches to fit the operation. If space is insufficient, return the size requirement and a choice of safe destination or smaller scope.

## 3. Configure the client without replacing existing owners

Distinguish having the `git-lfs` executable from having its filters configured for this repository. Use the installed version's documentation and inspect the effective values before writing. Do not install a different Git or LFS release merely to make the guide's preferred option available.

`git lfs install` normally changes global filter configuration and installs a repository pre-push hook; `--local` limits filter configuration to the repository, but the hook location still follows `core.hooksPath`. The documented `--manual` route helps integrate with an existing hook, while `--skip-repo` omits hook installation. See [LFS installation options](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-install.adoc).

Choose only the scope the user approved. In a linked-worktree setup, repository-local configuration or a shared hook directory may affect other worktrees or repositories. An existing hook is not disposable. Preserve its full behavior and obtain authority for its real scope before integration. Never use force installation or overwrite a hook to silence a conflict. If filter configuration is prepared but push-hook integration remains blocked, say so; do not call that a complete collaborator-ready setup.

Explain the future effect of an installed LFS push hook: a later Git push may upload associated LFS objects. That behavior is documented by [LFS pre-push](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-pre-push.adoc). Do not perform a push as a configuration test. No new token, credential storage, account, remote endpoint or access grant belongs implicitly to this task.

## 4. Define and inspect the actual tracking rules

Use the smallest repository-visible `.gitattributes` change that covers the selected assets and future family, if a family was requested. Preserve comments and unrelated EOL, archive, diff and merge policy. An ordinary rule produced by LFS uses `filter=lfs diff=lfs merge=lfs -text`; inspect the generated rule rather than assuming an extension glob is sufficiently narrow.

Quote a pattern when passing it through a shell so the shell does not expand it first. For a literal name containing glob characters, the supported `git lfs track --filename` mode escapes them for attributes. `git lfs track` edits attributes and can touch matched files; its dry-run option previews those effects. See [LFS tracking options](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-track.adoc). A direct scoped candidate edit is also useful when no configuration activation is requested.

Resolve effective attributes per selected path, including nested `.gitattributes`, local overrides and relevant global rules. Matching lines override individual attributes, and directory patterns do not recursively cover descendants by themselves. See [Git attributes](https://git-scm.com/docs/gitattributes). Check the working-tree policy and the staged policy separately when their files differ. Preserve a conflicting rule for review instead of silently overriding another owner's conversion policy.

Use the installed Git's bounded `check-attr` queries for `filter`, `diff`, `merge`, `text`, `eol`, `ident` and `working-tree-encoding`, with literal/NUL-aware path handling where necessary. `-text` alone does not disable every possible conversion. Confirm selected payloads have no unexplained transform, excluded siblings stay excluded, and the policy can travel in the repository rather than working only through local overrides.

## 5. Convert only the authorized current paths

Recheck payload digests, index state, effective rules and available space immediately before staging. Hold changed or conflicted paths. Keep the approved path list independent of a glob so a mistaken pattern cannot quietly expand the conversion scope.

When staging is authorized, stage the required attribute changes and exact selected new files through the reviewed LFS filters. For already tracked ordinary blobs, a bounded `git add --renormalize` reapplies the clean process and updates the index; it is an actual conversion step, not a preview. It does not add new untracked files. See [Git add](https://git-scm.com/docs/git-add). Do not use repository-wide add/renormalize, remove files from the index first, or clear unrelated staging.

Keep attribute staging as narrow as asset staging. If `.gitattributes` contains unrelated unstaged edits, do not stage the whole file accidentally; prepare a precise change or stop for reconciliation. Existing partial staging of an asset is likewise not permission to substitute all working-tree content.

Inspect the result even after a failure. Filter execution may have written local objects or some index entries before another path failed. Do not repeat the whole batch blindly. Track successful, failed and untouched paths separately, and retain full payloads in the working tree and preservation location.

Do not use `git lfs migrate import` for this bounded adoption. History migration has different commit-identity and collaboration consequences; its modes and exceptions are described in the [migration manual](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-migrate.adoc). Old ordinary blobs remain in old commits after current-version adoption. Do not promise repository-history shrinkage or repair of an earlier rejected push.

## 6. Verify pointers, objects and preservation independently

Read back the final attributes and every selected staged blob without invoking external diff/textconv helpers. Check these distinct properties:

1. **Selection:** Only approved paths and scoped attributes changed in the index; original unrelated staging remains intact
2. **Representation:** Each converted nonempty asset's staged bytes form the intended canonical LFS pointer rather than the full payload or an accidental pointer-to-pointer
3. **Identity:** Pointer SHA-256 and byte length match the independently recorded original payload for this ordinary no-extension workflow
4. **Local availability:** The referenced object exists in the effective local LFS store and its actual bytes match that identity; a filename resembling a hash is insufficient
5. **Preservation:** Selected working-tree payloads and retained copies still match their baselines; pre-existing work and configuration outside scope remain unchanged
6. **Distribution limit:** Remote upload, another checkout's acquisition and hosted archive behavior remain unverified unless separately exercised within authority

A native pointer check can validate staged pointer bytes saved to a fresh inspection file: `git lfs pointer --check --strict --file=<pointer-copy>`. Use the installed version's [pointer command](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-pointer.adoc) and interpret its status; canonical syntax alone does not prove object presence. Keep binary payloads out of terminal output.

Do not assume a command named check is read-only. `git lfs fsck` can move corrupt objects, and its revision/index coverage and exclusion settings affect what it checks. Use a supported non-mutating mode only after verifying its scope, or perform bounded read-only object/hash inspection instead. See [LFS consistency checking](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-fsck.adoc). Do not change exclusions or delete corruption merely to obtain a clean result.

If a real checkout demonstration is requested, use a separately authorized isolated destination with a clearly identified candidate revision and local object source. Do not commit simply to make that demonstration possible. `git lfs checkout` materializes available local objects without downloading them; missing payloads remain a separate acquisition problem. See [LFS checkout](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-checkout.adoc). Never delete the original payload to create a demonstration. A local materialization check does not prove remote retrievability.

## Deliver, recover and stop

Return the actual attributes patch or saved file, local filter/hook changes and their scope, selected path record, pointer/object/preservation evidence, and exact unfinished steps. State whether configuration was proposed or applied, assets were staged or only planned, and any checkout was actually observed. Do not deliver a readiness claim based only on `git lfs track` listing a pattern.

For failed conversion, retain the payload baseline and inspect the index and object store before retrying. Correct only the understood cause within scope. For rollback, compare current files and configuration with the task's writes, restore only those changes and the selected prior index entries, and preserve newer edits. Removing an attribute rule does not turn a staged pointer back into a full Git blob. Likewise, deleting a local LFS object can strand a pointer; retain objects rather than pruning as routine cleanup.

If a payload is missing, report its exact object identity and allowed source; do not fabricate bytes, alter the pointer, disable required filters or accept incomplete uploads to conceal the gap. Stop when the requested local adoption has evidenced outcomes or a specific missing tool, payload, preservation decision or authority blocks it. Remote publication, migration of history and cleanup require their own scope.

## Fictional, unexecuted illustration

A fictional sculpture project wants LFS for two new nonempty files, `assets/source/model-a.mesh` and `assets/source/model-b.mesh`. Its existing `assets/reference/sample.mesh` must remain ordinary Git content. A broad `*.mesh` rule would include the reference file, so the proposed policy is limited to `assets/source/*.mesh`. An unrelated Markdown edit is already staged, and the existing pre-push hook performs a team check.

The proposed plan preserves both full source files and records their byte lengths and SHA-256 values without inventing digest strings here. It prepares the narrow attributes rule, holds hook replacement, and proposes integration that retains the team check. If the user authorizes that hook integration and selected staging, acceptance would require two canonical pointers matching the original payloads, corresponding local objects with matching actual bytes, unchanged full working files, no change to the reference asset, and the original Markdown staging preserved.

If one pointer exists but its local object does not, that asset remains incomplete even if the other passes. No push would be attempted to discover the problem remotely. This is an authored decision walkthrough only: no repository was configured, asset staged, hook executed, object transferred, checkout tested or application run for this illustration.
