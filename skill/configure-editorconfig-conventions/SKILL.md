---
name: configure-editorconfig-conventions
description: Create or revise .editorconfig files from a repository's actual editing conventions, resolve inherited settings per path, and preserve syntax-sensitive exceptions. Use for portable editor configuration, not bulk formatting or formatter implementation.
---

# Configure Portable Editor Conventions

Produce a small `.editorconfig` patch and a resolved-settings map that explain how owned files should be edited across the named editors. Preserve intentional differences between file families. A syntactically valid file, a parser's resolved values and an editor's actual save behavior are three separate results.

Use [build-source-formatter](../build-source-formatter/SKILL.md) for language-specific printing or layout. Use [configure-git-line-endings](../configure-git-line-endings/SKILL.md) for Git's index/checkout conversion. EditorConfig does not define Git normalization, lint enforcement or a complete language style.

## Inputs and action boundary

Establish the repository/root and revision, requested file scope, existing local changes, root/nested `.editorconfig` files, and relevant parent-directory configuration. Identify the editors/plugins and format-on-save tools whose behavior matters when supplied; an unknown editor is a coverage limit rather than a reason to install one.

Read authoritative project conventions and representative **owned** files. Distinguish source, generated output, vendored dependencies and exact-byte fixtures before deriving defaults. Sample the exceptions as well as common files: make recipes, Markdown hard breaks, mixed-language directories, BOM/legacy encodings and files intentionally lacking a final newline can change the right settings.

Resolve whether the deliverable is a proposal, a saved repository configuration, or additionally a scoped formatting migration. A request for configuration alone does not authorize re-saving all source files, installing plugins, changing a user's editor profile, enabling format-on-save, or publishing a commit. Preserve all pre-existing changes and do not alter a parent/home configuration to make the repository appear consistent.

Use explicit user/project decisions before majority style. Several old files using spaces do not prove that tabs are a defect. When evidence conflicts, provide the proposed file-family choice and the precise unsettled question; continue the unaffected sections.

## 1. Reconstruct inheritance before choosing defaults

Apply the [EditorConfig specification](https://github.com/editorconfig/specification/blob/master/index.rst), using the relevant supported version:

1. For each selected path, look in its directory and ancestors for lowercase `.editorconfig`
2. Stop the upward search at an applicable `root = true` in the preamble, or at the filesystem root
3. Within a file, later matching sections take precedence **per key**
4. Matching keys in a nearer configuration override the same keys in more distant files; unmentioned keys continue to inherit

Adding `root = true` changes the inheritance boundary. Use it when the repository is meant to be self-contained, not merely as boilerplate. If ancestor settings cannot be read, report that limitation; do not assume there are none. A nested `root = true` can intentionally isolate a component and must not be silently removed.

Build a compact matrix:

```text
representative path | matching files/sections in order | effective keys
winning source per changed key | intended convention | unresolved conflict
```

Include new-file paths as well as existing ones, since the configuration governs future editing too. Preserve case and path spelling. Do not use an ad hoc regular expression or shell glob result as proof of the EditorConfig match.

## 2. Choose properties that express the actual convention

Prefer a few supported properties with clear ownership: `indent_style`, `indent_size`, `tab_width`, `end_of_line`, `charset`, `trim_trailing_whitespace`, and `insert_final_newline`. Leave a property unspecified when the project has no decision; do not fill every key with a personal preference.

- `indent_size` is indentation columns; `tab_width` is the display width of a hard tab. `indent_size = tab` delegates to the effective tab size. Do not assume these settings convert existing leading whitespace
- `charset` distinguishes UTF-8 from UTF-8 with a BOM. Do not impose an encoding change on legacy or byte-sensitive files because UTF-8 is common
- `end_of_line` is an editor preference. Reconcile it with `.gitattributes` and formatter settings, while retaining their separate responsibilities
- `trim_trailing_whitespace = true` can remove meaningful bytes. In CommonMark, two or more trailing spaces can encode a hard line break; preserve that convention where used. See the hard-line-break section of the [CommonMark specification](https://github.com/commonmark/commonmark-spec/blob/master/spec.txt)
- Keep make recipe indentation consistent with the actual dialect and `.RECIPEPREFIX` usage. Do not mechanically convert tabs because another language uses spaces; the [GNU Make manual source](https://github.com/mirror/make/blob/master/doc/make.texi) describes recipe-prefix requirements
- `insert_final_newline` is a save instruction; `false` is not a universal request to leave every existing file untouched. Check the chosen editor's behavior before claiming preservation

The value `unset` removes that key's inherited EditorConfig effect. It restores dependence on other editor defaults/settings; it is not a read-only or ignore directive. EditorConfig has no general exclusion switch that freezes a file's bytes. To avoid applying a new convention to generated/vendor/fixture files, scope the new rules to owned paths where possible and document the edit boundary. If an inherited key needs clearing, clear it specifically and report what remains uncontrolled.

Do not add tool-specific properties as though every plugin supports them. Unknown keys and unsupported values may be ignored by plugins even when a core reports them. If an extension is essential, identify the actual consumer and keep portable behavior separate from its extension.

## 3. Write correct patterns and preserve exceptions

Use the smallest useful hierarchy. A root file with a few specific sections often suffices; nested files are appropriate when a component genuinely owns different conventions. Keep existing comments, unrelated keys and intentional local rules.

Important format rules from the [specification](https://github.com/editorconfig/specification/blob/master/index.rst):

- The file is UTF-8 and uses LF or CRLF line separators
- `root` belongs in the preamble; ordinary properties belong in sections
- Comments occupy their own lines. A trailing `# explanation` or `; explanation` becomes part of a property's value
- Patterns use `/` path separators on every platform. `*` does not cross `/`; `**` can
- A pattern containing a path separator is relative to that `.editorconfig` directory; a pattern without one can match names below it at multiple depths
- A section ending with `/` does not match files. Use the actual intended file/subtree glob instead

For a selector change, inspect intended matches and near misses: root versus nested file, sibling component, same extension in generated output, and any nested override. Brace expansion and character-class syntax must be interpreted by an EditorConfig implementation/specification, not a generic INI parser.

Use an exact patch rather than regenerating the file and losing comments. Save under the approved destination and read it back. Recompute the effective-key map after the patch; do not assume the textually last section wins every key if it does not match the path.

## 4. Verify at the level actually available

Perform static inspection even if no EditorConfig core or editor is installed. Check valid sections/values, source precedence, path coverage, and unchanged protected configuration. State this as a static result.

When an already available, permitted EditorConfig core is usable, resolve representative paths through that core and record its name/version, inputs and returned keys. Compare to the intended matrix, including a nested override and a protected near miss. Do not install a parser merely to claim a pass. A generic INI load is not adequate because EditorConfig has its own glob and inheritance semantics.

When the user requested real editor verification and that editor is available, use new disposable files/copies under a matching authorized hierarchy. Exercise the relevant typing/save behavior and inspect saved bytes, including indentation, line-ending sequences, BOM and final newline. Keep source files out of autosave experiments. Check active format-on-save behavior, since another tool may rewrite the file after EditorConfig values are applied.

A core resolving `indent_style = tab` does not prove that an editor preserves a make recipe. A successful save in one editor/plugin version does not establish every editor's support. No editor available means that layer remains untested; deliver the useful configuration anyway.

If formatting was also requested, treat it as a separately bounded transformation with its own before/after evidence. Do not run `make`, execute project scripts, compile source or trigger a build merely to validate editor settings. Use already authorized inert checks that address the actual formatting change.

## Deliverable, acceptance and recovery

Return the `.editorconfig` patch or saved files, a short rationale per convention/exception, the effective-settings matrix, and separate static/core/editor results. Include the named editor coverage and any settings whose behavior remains unsupported or unresolved.

Acceptance requires:

- All requested file families have the intended effective keys, with no accidental loss of unrelated inherited keys
- Protected paths are outside the new rule scope or have a clearly stated, limited override; no claim that `unset` freezes content
- Encoding, whitespace and newline decisions reflect the source/consumer contract
- No bulk source changes, personal settings, installations or publication occurred outside the requested scope
- The final saved patch matches what was inspected, and unperformed editor checks are explicit

For an overly broad pattern, narrow the candidate and re-resolve affected paths. For parser/plugin disagreement, retain both observations and use the actual supported consumer behavior to resolve the conflict; do not silently weaken the project's requirement. If a test save changes protected content, preserve the comparison and restore only task-owned copies. If real source was inadvertently changed, stop and reconcile against the captured baseline without discarding the user's edits.

Stop when the requested configuration and available checks are delivered, or a material convention/consumer decision blocks the remaining work. Do not turn a two-line convention change into a repository-wide style migration.

## Illustration: fictional and unexecuted

A fictional project agrees on two-space JSON in its owned `config` tree, four-space Python in `src`, and preserving Markdown hard-break spaces in `docs`. Its proposed self-contained root file is:

```editorconfig
root = true

[config/**.json]
indent_style = space
indent_size = 2

[src/**.py]
indent_style = space
indent_size = 4

[docs/**.md]
trim_trailing_whitespace = false
```

The paper map covers `config/app.json`, `config/local/app.json`, `src/main.py` and `docs/start.md`. It predicts no matching section for `vendor/app.json` or `fixtures/raw.json`. No universal charset, newline or indentation rule is added without evidence. The decision to stop ancestor inheritance is explicit; other editor defaults can still affect every file.

This is a fictional, unexecuted configuration illustration. No parser, editor save, repository migration or publication has been performed by the example.
