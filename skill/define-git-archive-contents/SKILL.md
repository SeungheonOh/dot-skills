---
name: define-git-archive-contents
description: Define and verify a Git source-archive membership contract using scoped export-ignore rules, required-file coverage and an exact source revision. Use for source snapshot inclusion policy, not built-package runtime checks or release publication.
---

# Define What Belongs in a Git Source Archive

Deliver a reviewed source-archive policy: the minimal `.gitattributes` patch, the required/excluded path manifest, and actual archive membership evidence when generation is authorized and available. A repository file listing is not the archive's membership list. A local preview using new working-tree rules is not proof that a committed or hosted download uses those rules.

Use [release-artifact-verification](../release-artifact-verification/SKILL.md) for installing or exercising a built package. Use [portable-project-handoff](../portable-project-handoff/SKILL.md) for selecting, renaming and packaging arbitrary project files for another platform. This skill concerns a Git source snapshot and its exclusion contract; it does not approve a release or establish that the program builds.

## Establish the archive's purpose and source

Resolve:

- Repository and exact commit, or the proposed revision and its uncommitted policy patch
- Delivery route: local `git archive`, a named host's generated source download, or an existing supplied archive
- Expected format and safe top-level prefix, intended audience/use, and approved local output path
- Required source, license/notice, build-definition, schema, template, documentation and fixture files for that use
- Explicit exclusions with reasons, plus any submodule, Git LFS, generated-but-untracked or externally supplied dependencies
- Whether the user wants a policy proposal, configuration edits, local archive creation, or additional publication/sharing

Do not guess exclusions from directory names. Tests, examples, development metadata and CI files can be necessary for a source consumer; keep or exclude them according to the stated purpose. An archive intended to reproduce a build has a different contract from a documentation snapshot.

Read-only inventory and a proposal can proceed without activating changes. A request to prepare a local archive does not authorize a release, tag, registry upload, external sharing, repository-settings change or deletion of source files. Do not use `export-ignore` as a secrecy control: excluded files still remain in Git and may be reachable through other repository views/history.

## 1. Create a source inventory independent of the archive

Resolve mutable refs to the exact inspected commit when possible. Record source identity, observation time, selected tree scope and completeness. Preserve unrelated staged/unstaged changes and do not substitute the current working tree for an older release tree.

With an available permitted Git installation, a useful tree inventory is:

```text
git ls-tree -r -z --full-tree <resolved-commit>
```

Retain entry type/mode, object identity and exact path. Treat a gitlink/submodule as a separate dependency boundary, not proof that its files will be embedded. Use NUL-aware handling for unusual names. See [Git's tree-listing documentation](https://github.com/git/git/blob/master/Documentation/git-ls-tree.adoc).

Reconcile the inventory to the desired contract before adding exclusion rules. For each required or excluded path/family, record its purpose, source evidence, current export state, proposed state and unresolved dependency. Keep mandatory files individually visible; counts alone cannot prove their presence. Trace only the references needed for this archive's use, including build/readme references to files proposed for exclusion.

Git archives start from a named tree, not arbitrary untracked working files. `.gitignore` describes untracked-file handling and does not remove already tracked files from this archive contract. See [Git's ignore documentation](https://github.com/git/git/blob/master/Documentation/gitignore.adoc). Do not silently add untracked generated files or run a generator to fill the gap. Return the missing required input or an explicitly authorized packaging alternative.

## 2. Resolve the effective export rules

Read root/nested `.gitattributes` for the source tree plus relevant local/global attribute sources. Preserve all non-archive attributes. Under [Git's archive documentation](https://github.com/git/git/blob/master/Documentation/git-archive.adoc), normal archive generation takes `.gitattributes` from the tree being archived; `--worktree-attributes` uses working-tree attributes for a preview, and `info/attributes` can apply local overrides.

Map each candidate path to effective `export-ignore` and `export-subst`, including source lines and any overriding rule. Use the installed Git's supported source-aware `check-attr` interface when available, or provide a bounded static map with its limits. Do not equate a plain working-tree query with the committed tree's rules. See [attribute-query options](https://github.com/git/git/blob/master/Documentation/git-check-attr.adoc).

Apply [attribute syntax](https://github.com/git/git/blob/master/Documentation/gitattributes.adoc) precisely:

- `export-ignore` sets the exclusion attribute; `-export-ignore` unsets it. A string assignment such as `export-ignore=false` is not the boolean-unset syntax
- Later lines override earlier values per attribute; closer attribute files and local overrides can change the result
- Negative path patterns are not supported. Do not copy `.gitignore` negation syntax into `.gitattributes`
- Ordinary attribute matching of a directory is not recursive assignment to every descendant

Archive traversal adds a separate consequence: when an excluded directory is pruned, a later child exception cannot make Git traverse back into it. Inspect ancestor-directory decisions as well as leaf attributes. The [Git archive implementation](https://github.com/git/git/blob/master/archive.c) shows this traversal boundary. For selective inclusion beneath a directory, avoid excluding the ancestor itself; design narrow exclusions and verify actual members. A leaf-only `check-attr` map is insufficient.

`export-subst` changes designated placeholder content when Git has the required commit information; a tree-only archive can behave differently. Preserve existing substitution rules and include their expected output in the content contract. Do not introduce commit-author/email or other metadata substitutions without a purpose and appropriate sharing scope.

## 3. Prepare the policy patch and preview safely

Edit only the intended export attributes when configuration edits are requested. Retain encoding, comments, line-ending/filter rules and unrelated local changes. Keep the manifest independent of the patch, so a mistaken exclusion cannot remove itself from the expected-file denominator.

For an uncommitted candidate, use an authorized isolated copy or a clearly labeled `--worktree-attributes` preview. Record which rules actually fed that preview. Do not commit merely to obtain a convenient test tree. If no preview can represent the intended hierarchy safely, deliver the patch with generation unperformed.

Before invoking `git archive`, inspect content-conversion attributes and configured drivers for selected files. Git's [archive implementation](https://github.com/git/git/blob/master/archive.c) can apply working-tree conversion, including configured filters; even a source archive can therefore execute a program or contact a service. Review `filter`, `working-tree-encoding`, `text`, `eol`, `ident` and `export-subst` effects relevant to the selection. Do not run unknown/networked filters, custom archive commands or dependency fetches under assumed inert-inspection permission.

When authorized, use an understood built-in archive format and a fresh output name in an approved nonsynced location. Run from the repository root or record intentional subdirectory/path selection, since the invocation directory can bound the archive. Specify a simple relative prefix with no leading slash or `..` components. Do not overwrite an existing archive, use `--remote`, or add unrelated files for convenience.

Record the exact invocation, Git version, source commit, attribute mode, relevant overrides, format, prefix, and output identity. Use the actual command's status and saved output; an archive named after a version is not proof that it contains that version. Treat configured custom compressors as executable code, not harmless filename choices.

## 4. Reconcile the saved archive to the contract

Inspect the actual saved archive with a format-aware reader. List members before any extraction. Normalize only the declared top-level prefix for comparison; retain case, Unicode spelling, duplicate names and file types. Reject unsafe absolute/parent-traversal members, unexpected duplicates or collisions, and inappropriate link targets before extracting. Do not run included files.

Reconcile every relevant source/contract entry:

```text
source path | required/optional/excluded | rule and ancestor decision
actual member/type | source-to-archive transformation | result/reason
```

Check required files and exact content relationships, authorized exclusions, unexpected members, symlinks/executable modes where relevant, and substitution/conversion results. A file can be present with the wrong bytes. Conversely, expected EOL or placeholder conversion is not unexplained corruption if it was part of the approved contract and verified.

For a membership-only request, do not install, build or execute the source. If safe extraction is useful and authorized, use a fresh owned directory and an extractor with appropriate path/link protections. An archive listing can establish membership without establishing portability, safe execution or a successful build.

Handle special sources explicitly:

- A submodule entry does not establish bundled submodule contents; identify the required separate source and whether the chosen route includes it
- An LFS pointer is not the large object's payload. Inspect the actual member and route. GitHub's source-archive LFS behavior depends on repository settings and tracking rules; changing those settings can affect bandwidth cost and needs separate authority. See [GitHub's archive LFS guidance](https://github.com/github/docs/blob/main/content/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/managing-git-lfs-objects-in-archives-of-your-repository.md)
- A local archive result does not prove a hosted download. If that download is the acceptance target, inspect the actual authorized download for the exact commit or report the hosted layer unverified

GitHub documents that compressed archive bytes can change even when extracted contents remain stable, and mutable branch/tag names can point to different commits. Keep archive SHA-256, source commit and content-member evidence separate; none alone authenticates an unknown publisher. See [GitHub's source-archive stability guidance](https://github.com/github/docs/blob/main/content/repositories/working-with-files/using-files/downloading-source-code-archives.md).

## Deliverable, acceptance and recovery

Return the patch, contract manifest and, when created, the actual archive with filename, size/digest and evidence. Label policy inspection, local-preview membership, committed-tree membership and hosted-download inspection separately. Do not call the proposed policy active or a release published without that evidence.

Acceptance requires all mandatory source/license/resource paths to be present as intended, all agreed exclusions absent, unexplained additions or conversions resolved, and the original repository/worktree preserved. State incomplete source inventories and unavailable filter/LFS/provider checks explicitly.

If a required file disappears, inspect both its own rule and its ancestors before broadening the archive. Revise the minimal candidate and regenerate into a new output; preserve the failed manifest comparison. If filters or missing objects prevent generation, deliver the policy and exact blocked dependency without fetching/installing or changing global settings. If an output or save is uncertain, inspect it before retrying. Never weaken the required-file contract simply to make the result pass.

Stop when the requested policy and archive boundary have an evidenced result, or the remaining step needs a specific source, decision or authorization. No release publication is implied.

## Illustration: fictional and unexecuted

A fictional source snapshot must include `LICENSE`, `README.md`, `src/main.py` and `schemas/request.json`. Its author explicitly excludes internal planning notes and editor backup files. A proposed root patch is:

```gitattributes
/planning/** export-ignore
*.bak export-ignore
```

The paper manifest retains all four required files, excludes `planning/notes.md` and `src/main.py.bak`, and leaves tests unchanged because no test exclusion was requested. A new uncommitted patch would need a clearly labeled working-tree-attributes preview; archiving the old commit normally would still use that commit's old rules.

This is a fictional, unexecuted illustration. It supplies no generated archive, observed Git output, hosted-download result or proof of program buildability.
