---
name: configure-git-ignore-rules
description: "Create or repair scoped Git ignore rules for intentionally untracked files, explaining each match and preserving required source, local bytes and existing staging. Use for repository noise and future add-discovery policy, not deleting files, untracking existing content, removing secrets from history or shrinking a checkout."
---

# Configure ignore rules without hiding required work

Deliver the smallest justified ignore-policy change and a path-by-path explanation of its effects. Fewer entries in status is not sufficient: required new source must remain discoverable, already tracked files must be identified accurately, and local files must survive.

[Git sparse checkout](../configure-git-sparse-checkout/SKILL.md) changes which tracked source is materialized. [Git LFS tracking](../configure-git-lfs-tracking/SKILL.md) changes storage representation for versioned assets. [Git archive contents](../define-git-archive-contents/SKILL.md) controls source exports. This workflow decides which intentionally untracked paths Git should ordinarily ignore. None of those outcomes substitutes for the others.

## Establish what should remain local

Read the repository instructions and existing ignore policy. Identify the exact checkout, installed Git version, selected directories, and the reason for each requested exclusion. Resolve whether the goal is a shared project convention, a personal exception for this repository, or a user-wide convention. Prefer the narrowest scope that actually fits; a local request does not authorize changing every repository.

Build a small independent classification before writing patterns:

- Paths or future path families that should remain untracked, with their producer or purpose
- Required source, fixtures, templates, licenses and configuration examples that must remain eligible
- Current tracked, untracked and ignored state for the selected paths
- An adjacent near-match that should not be excluded
- The requested stopping point: proposal, applied ignore-file edit, or separately authorized staging/publication

Do not infer that every generated file is disposable or that every dependency lock should be ignored. Some projects intentionally version generated assets. Read the relevant producer and consumer definitions as data, without running them. If a path contains unique user work, flag the loss of ordinary Git visibility and establish its intended preservation route. Ignoring a file does not back it up.

Keep secret values and private filenames out of shareable explanations. A rule for a local secret file is useful prevention, but is not a confidentiality boundary or evidence that past exposure is repaired. If the file is already tracked, report that fact discreetly and hold any promised secrecy outcome. Credential revocation, historical removal and recipient notification are separate decisions.

## Preserve present state and resolve effective policy

Establish the real worktree, Git directory and common directory. Linked worktrees can share administrative files; do not assume `.git` is a directory or a local exclude file affects only one working tree. Inspect relevant configuration origins and environment overrides without printing full configurations or credentials.

Before status/index commands, inspect configured executable helpers such as filesystem monitors and use an understood permitted read route. Avoid external diff/text-conversion helpers and implicit network acquisition. Do not bypass denied controls or install a tool to make inspection possible. If safe native inspection is unavailable, return the candidate with its verification boundary.

Capture HEAD, index path/mode/object identities, staged and unstaged differences, existing ignore-file bytes and identities of valuable affected local files. Preserve comments, encoding and unrelated rules. A digest is comparison evidence, not a recoverable copy; retain exact before-text for files this task will edit in an authorized private location. Do not reset, stash, clean or unstage anything.

Read root and relevant nested `.gitignore` files, the repository's resolved exclude file and applicable user exclusion file. Git's [ignore reference](https://git-scm.com/docs/gitignore) defines their precedence and scope. Shared patterns belong in versioned ignore files; personal repository exceptions belong in the repository exclusion source; user-wide rules require that broader intent. Record which source actually decides each selected path rather than attributing a global exclusion to the proposed patch.

Use [Git's index listing](https://git-scm.com/docs/git-ls-files) to distinguish tracked entries from untracked files. Its ignored-file mode requires a tracked or untracked selection and explicit exclusion sources such as `--exclude-standard`; a default listing is not an ignore audit. Preserve path boundaries with NUL-aware handling and account for unresolved index stages or sparse entries. Do not follow symlinks outside the authorized tree or recursively inspect separate submodule repositories without scope.

## Author narrow rules with explicit exceptions

Choose rules from the independent classification, not a generic template dump. Prefer exact project-relative directories when only one output location is intended. A broadly named pattern can hide new source in another package months later. Keep comments about purpose, not private machine paths or sensitive data.

Under Git's ignore syntax, patterns are relative to their ignore-file location; a trailing slash limits a match to directories. Negation cannot restore a child of an excluded parent directory. Later and more-local rules can change a result. Literal leading `!` or `#`, spaces and wildcard characters need deliberate escaping. Consult the ignore reference rather than transferring `.gitattributes` or shell-glob assumptions.

When retaining a file inside an output directory, design the directory traversal and exception together. Do not exclude the whole parent and assume a child exception works. Review all ancestor directories and intermediate exclusions, especially with nested ignore files. A pattern's intended purpose and its actual path coverage are separate facts.

Do not add rules to conceal modifications to tracked configuration. Ignore files do not stop tracking indexed content. Do not use assume-unchanged or skip-worktree flags as a workaround, or run repository-wide `rm --cached` and re-add operations. Untracking selected current files has index and collaboration consequences and requires its own explicit change scope.

Prepare a scoped patch or write only the authorized ignore source. Recheck its current contents immediately before editing; reconcile concurrent changes. If a shared policy is requested but only a personal exclusion can be written, deliver the shared candidate instead of claiming the local workaround was distributed.

## Check decisions, not just command success

Read back final bytes. Evaluate both positive and negative cases: intended exclusions, required eligible files, near-matches, ancestor boundaries and any already tracked path the user expected to disappear. Keep expectations independent of actual output.

Use the installed [check-ignore interface](https://git-scm.com/docs/git-check-ignore) for path-level explanation when native inspection is authorized. Verbose output identifies the winning source, line and pattern. A negated match means inclusion, so printed output alone is not proof of exclusion. The nonmatching option with verbose output can retain a row for every input; NUL input/output avoids whitespace ambiguity.

Tracked files are omitted by default. Use a deliberate `--no-index` query only to answer the hypothetical pattern question, and label it separately from real tracked status. A pattern match under that option does not mean the file stopped being tracked. Interpret documented exit statuses: no matching ignored paths is a normal negative result, distinct from a fatal error. For several paths, one aggregate exit status cannot establish each row's disposition.

A useful result record is:

```text
path | intended disposition | tracked state | winning source/line/pattern
actual rule decision | effective current status | discrepancy or limit
```

Inspect existing paths directly. For future families, use safely representable hypothetical names only where the interface can model their type and ancestors; otherwise label a static expectation or use an authorized isolated fixture with the same rule hierarchy. Do not create fake output or secret files inside the user's project to manufacture a test. An isolated fixture without the real user exclusions proves the candidate rules only, not the effective live policy.

Reinspect index identities, source-file identities and the exact ignore patch. Acceptance requires only intended policy edits, unchanged prior staging, preserved affected bytes, the expected ignored new paths, and required new files still eligible. Do not use `git add`, commit or force-add as a test of visibility. Do not run a build merely to generate more sample paths.

If native execution is unavailable, return the reviewed patch, classification and expected decisions with live matching explicitly unrun. A plausible pattern is not observed Git behavior. Passing a small fixture does not establish every future filename or platform.

## Explain effects, recovery and completion

Deliver the exact patch or file, policy scope, matching evidence, tracked-file exceptions, preserved state and any missing decision. Distinguish prepared, applied, staged, committed and shared; this workflow does not advance the last three without separate authority.

An ignored-file designation must never become permission to delete. Future cleanup tools may treat ignored paths differently, so keep valuable local assets and backup requirements visible in the handoff. Do not run `git clean`, clear caches or claim storage savings. Use [storage cleanup](../storage-cleanup-accounting/SKILL.md) for an explicitly requested removal decision.

If a required new file becomes hidden, inspect the winning rule and its ancestors before broadening an exception. If a proposed rule appears ineffective, check tracked state and overriding sources before changing it. Restore only this task's rule edit after comparing current bytes; preserve later user changes. Restoring ignore text does not undo any separately performed staging, deletion or publication.

After an uncertain save, read the file and compare with the candidate before retrying. Stop when the intended local policy and preservation are established, or identify the exact unavailable path, conflicting convention or authority needed. Do not keep expanding the ignore list to make status empty.

## Fictional, unexecuted example

A fictional Cedar project generates disposable previews under root-level `preview-output`, but keeps `preview-output/README.md` as an instruction file. A new `src/preview-output.js` must remain eligible, and a previously tracked `preview-output/old-preview.svg` is a separate issue.

The proposed root `.gitignore` entries are:

```gitignore
/preview-output/*
!/preview-output/README.md
```

The authored expectations are that an untracked direct preview file is ignored, the README remains eligible, and the source file is unaffected. The parent directory itself is not excluded by the first rule. A new nested output directory is ignored as a child; preserving a file deeper inside it would require a deliberate intermediate-directory exception. The already tracked SVG remains tracked even if a no-index query matches it.

If a user-wide rule still hides the README, the effective result must be investigated rather than reported from this patch alone. No file would be deleted or unstaged to make the example pass. This is a fictional decision walkthrough: no ignore file was applied, Git command run, fixture created, project executed or live behavior verified for the illustration.
