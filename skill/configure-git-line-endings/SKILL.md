---
name: configure-git-line-endings
description: Create or revise a repository's .gitattributes text and line-ending policy, map its effective rules, and prepare a scoped normalization migration when requested. Use for checkout/index EOL conventions, not unknown-encoding recovery or wholesale formatting.
---

# Configure Git Line Endings Without Incidental Rewrites

Deliver a minimal `.gitattributes` change and a path-level explanation of what Git will store and check out. Keep the policy change separate from any normalization of existing tracked files. A configuration file can be complete while the migration remains deliberately unperformed.

Use [text-encoding-recovery](../text-encoding-recovery/SKILL.md) when the intended characters or encoding are unknown. Use [build-source-formatter](../build-source-formatter/SKILL.md) for language-aware layout work. This workflow does not change indentation, trim trailing spaces, add final newlines or repair source text.

## Establish the boundary

Resolve from the request and repository:

- Repository/root, branch or commit, selected owned paths, existing local changes and relevant Git implementations/versions
- Required index representation and working-tree line endings for each meaningful file family, including consumer-specific exceptions
- Existing root/nested `.gitattributes`, pertinent local/global overrides, and formatter or EditorConfig rules that also write line endings
- Byte-sensitive fixtures, binary assets, generated/vendor directories, signed files, and known non-ASCII-compatible encodings
- Whether the request covers a proposal, saving the configuration, normalization of named tracked files, or publication

Do not infer CRLF solely from a Windows filename or LF solely from the current machine. Prefer an established project/consumer requirement; otherwise propose the narrowest consistent policy and identify the unsettled exception. Inspect bytes before calling a suspicious file ordinary text.

Preserve unrelated rules and all pre-existing staged/unstaged work. Do not change global Git configuration, reset the index, rewrite history, force a checkout, or stage/commit/push merely because an EOL policy was requested. A normalization explicitly included in the request may proceed within its reviewed path scope; it need not receive a redundant approval.

## 1. Capture observed bytes and effective attributes

Record the inspected revision and whether findings concern committed blobs, the index or the working tree. These are different sources. A checked-out file with CRLF may correctly correspond to an LF index blob.

With an available authorized Git installation, useful read-only queries include:

```text
git --literal-pathspecs ls-files --eol -z -- <bounded-paths>
git check-attr text eol working-tree-encoding filter ident -- <representative-paths>
git check-attr --cached text eol -- <representative-paths>
```

Replace placeholders with reviewed paths and use the actual command interface safely. For unusual filenames, use supported NUL-delimited input/output rather than splitting on whitespace or newlines. `ls-files --eol` reports separate index/worktree classifications and attribute information; `mixed`, `none`, `-text`, and unavailable information are not interchangeable. Neither command establishes a file's intended character encoding. See [Git's EOL inspection](https://github.com/git/git/blob/master/Documentation/git-ls-files.adoc) and [attribute-query documentation](https://github.com/git/git/blob/master/Documentation/git-check-attr.adoc).

For an exported tree without Git metadata, read the rules and representative file bytes directly. Mark index state and machine-local overrides unknown. Do not manufacture successful Git observations from a static export.

Inspect only relevant configuration keys and their origins: `core.autocrlf`, `core.eol`, `core.safecrlf`, attribute-file locations, and named conversion drivers when present. Avoid dumping the complete configuration because it can contain credentials or unrelated private settings. Record unavailable ambient layers as a limit on the effective-policy claim.

Before Git operations that can trigger configured helpers, also inspect command-valued `core.fsmonitor` and the effective hook location, including `core.hooksPath`. An index write can invoke `post-index-change`; `git add --renormalize` is not limited to content filters. Run those helpers only when their effects are reviewed and authorized, or return the static map/migration plan without changing persistent settings. See [Git's filesystem-monitor configuration](https://github.com/git/git/blob/master/Documentation/config/core.adoc) and [index-change hook documentation](https://github.com/git/git/blob/master/Documentation/githooks.adoc).

## 2. Derive the policy per attribute

Apply [Git's attribute semantics](https://github.com/git/git/blob/master/Documentation/gitattributes.adoc):

- Later matching lines override earlier ones **per attribute**; they do not replace an entire earlier rule
- A nearer directory's `.gitattributes` takes precedence over parent files; repository-local `info/attributes` has still higher precedence, and global/system sources have lower precedence
- Attribute patterns are not interchangeable with shell globs or EditorConfig globs. Negative path patterns are forbidden; a directory pattern does not recursively assign attributes to its children. Use a reviewed subtree pattern such as `fixtures/**` when that is the intent
- `text` enables normalization to LF on addition to the index; `text=auto` asks Git to classify text and has special handling for files already stored with CRLF
- `eol=lf` or `eol=crlf` controls checkout representation for applicable text files. `eol` can imply `text` when text is unspecified, but does not override an explicitly unset `text`
- `-text` disables EOL conversion. `!text` restores the unspecified state, allowing other configuration to matter; those instructions are not equivalent

Choose broad defaults only when the inventory supports them. Explicit patterns for known owned text can be safer than classifying every file. Preserve binary and byte-sensitive exceptions. Do not label `-text` a universal byte-preservation guarantee: `filter`, `ident`, or encoding conversion may still alter content.

Do not introduce `working-tree-encoding` as a quick fix for unusual files. It changes stored/working-tree encoding and requires a separate known-encoding and client-compatibility decision. Keep unknown encoding, mixed endings and exact-byte fixture semantics visible instead of guessing.

Maintain a compact mapping for representative paths and every exception:

```text
path/family | observed index/worktree EOL | effective text/eol
winning source lines | desired index/checkout representation
other conversions | policy-only or migration-needed | unresolved decision
```

Include a nested override, a sibling that should not match, a binary asset, a byte-sensitive text fixture and any explicit CRLF consumer when present. Expand the mapping across all proposed changed paths before normalization; examples alone do not define its scope.

## 3. Write the smallest configuration patch

Edit existing `.gitattributes` in place when authorized, retaining comments and unrelated attributes such as LFS filters, diff/merge drivers and archive rules. Place broad rules before specific exceptions only after checking the actual precedence chain. Avoid rewriting every rule into a preferred ordering.

Save a proposal separately when activation is not requested. Include why each changed pattern exists and the exact scope of its effect. Reconcile the intended checkout EOL with relevant editor/formatter settings; do not silently edit those settings as collateral work.

Re-read the saved candidate and compare current versus proposed effective attributes. If using Git to check a candidate, place it in an authorized isolated copy with the relevant hierarchy represented. Label omitted ambient overrides. Do not copy credentials or rely on another repository's global configuration as though it were the target's policy.

Adding `.gitattributes` alone does not retroactively normalize every existing index entry or rewrite every current working-tree file. State when the new rule will take effect and whether tracked content still needs migration.

## 4. Normalize only when that transformation is requested

Before migration, capture the approved file list, each source's bytes or recoverable baseline, and existing index/worktree state. Stop the affected part for unmerged entries, unexplained changes, unknown encodings or unresolved byte-sensitive files. Complete an independent policy proposal if it remains useful.

`git add --renormalize` reapplies the clean process to tracked files and updates the index; it is not a preview. That process can invoke configured clean/process filters. Inspect those drivers and their effects before executing them; do not run a networked LFS fetch, unknown converter or external program under a presumed newline-only permission. See [Git's add options](https://github.com/git/git/blob/master/Documentation/git-add.adoc).

Use a bounded reviewed path set and preferably a disposable copy for the migration comparison. Do not run repository-wide `git add --renormalize .` in a dirty working tree as a convenience. Preserve original staging boundaries; if they cannot be safely maintained, return the policy plus a migration patch/plan instead of replacing the user's index.

### Keep the migration file list literal

A list of approved filenames is not an approved Git pattern. Shell quoting and the `--` option separator do not disable Git's own pathspec interpretation. For filename-driven queries and migration, use the supported invocation-local [`--literal-pathspecs` option](https://git-scm.com/docs/git) before the subcommand, with safely passed arguments. Do not change persistent environment or repository settings to obtain this behavior.

For a longer list, `git add` supports `--pathspec-from-file` with `--pathspec-file-nul`. NUL framing preserves filename boundaries, including embedded newlines; it is not a substitute for literal pathspec mode. Keep the manifest outside the selected tree and bind it to the reviewed file list. See [Git's pathspec-input options](https://git-scm.com/docs/git-add).

Run from the established repository root with repository-relative file names. Literal mode does not make a directory entry mean one file: do not substitute a containing directory, `.` or an empty selection for the enumerated approved files. If the user intentionally selected a pattern or subtree, expand its scope through a permitted read-only inventory first and review the resulting files before migration. [Git's pathspec definition](https://git-scm.com/docs/gitglossary) distinguishes directory-prefix scope, wildcard matching and magic forms.

Reconcile the selected set against the current tracked entries immediately before staging. A missing worktree file is not an EOL conversion: `--renormalize` implies `-u`, which can record a tracked removal. Hold unexpected deletions or type changes instead of including them in a newline-only migration. Compare before/after index changes against the approved set, retaining the existing staged baseline; a restricted diff must not hide an out-of-scope change.

For every changed file, compare the actual before/after bytes under the specific allowed transformation. A newline-only change should preserve all non-line-ending bytes, final-newline presence, encoding/signature, permissions and path identity. Do not delete lone carriage returns as though they were necessarily CRLF pairs. A whitespace-ignoring diff alone cannot prove this invariant.

Inspect the staged diff without external diff/text-conversion helpers when appropriate, and account for all changed paths. Keep content edits separate from mechanical normalization. A file that remains unchanged may already comply; do not manufacture a diff to demonstrate activity.

## Acceptance, delivery and recovery

Return the configuration or proposed patch, effective-rule map, exact normalization scope/status, and remaining exceptions. Distinguish:

1. Rules inspected and saved
2. Effective attributes checked, with tool/version and actual sources
3. Existing tracked files normalized, if requested and actually performed
4. Checkout representation observed in a named environment, or untested

Acceptance requires that all intended paths resolve correctly, nearby exclusions remain unaffected, protected bytes and pre-existing work remain intact, and the saved diff contains only authorized changes. A current-platform observation does not establish every supported client/platform.

If a pattern is too broad, revise the candidate before migration. If normalization produces unexpected bytes, retain the failure comparison and restore only task-owned changes from the captured baseline; never use a blanket hard reset or checkout to discard concurrent work. If a save or staging result is uncertain, inspect the current state before retrying. Stop when the policy and requested migration have an evidenced result, or the next dependent step needs an identified decision/access boundary.

## Illustration: fictional and unexecuted

A fictional repository requires LF shell sources, CRLF checkout of two Windows command files, and exact-byte protocol fixtures. Its candidate rules are:

```gitattributes
src/** text eol=lf
scripts/*.cmd text eol=crlf
fixtures/protocol/** -text !eol
assets/*.png -text
```

The proposed map says `src/main.sh` is normalized as text with LF checkout; `scripts/setup.cmd` is normalized to LF in the index with CRLF checkout; protocol fixtures receive no EOL conversion. The asset and fixture claims still depend on the absence of other conversion attributes. No global default is added because unclassified files have not been reviewed.

A second fictional boundary case selects only the literal file `src/report[1].txt`, with `src/report1.txt` present but excluded. Treating the selected name as a pattern can also match the excluded file; quoting it in the shell does not prevent that Git-level match. The migration plan must preserve the literal selection. If the selected file disappears before staging, hold it rather than staging its removal. These are unexecuted decision cases, not observed Git results.

This is an unexecuted paper illustration. It is not evidence that files were normalized, a Git client resolved these rules, or either operating system was tested.
