---
name: prepare-git-patch-series
description: "Prepare an ordered Git mailbox patch series from a pinned linear commit range, reconcile its contents and metadata, and establish replay fidelity when isolated application is authorized. Use for reviewable commit-by-commit transfer, not full-history backup or live branch integration."
---

# Prepare a replayable Git patch series

Deliver ordered patch files, a source-to-patch manifest and the precise evidence that the series preserves the selected changes. A patch series is a replay recipe, not a copy of the original commit objects. File generation alone does not establish that another repository can reconstruct the intended trees or messages.

Use [Git bundle handoff](../prepare-git-bundle-handoff/SKILL.md) when the recipient needs original objects and ancestry, [exact text patches](../verify-exact-text-patches/SKILL.md) for a single-file exact-position text transformation, and [parallel change integration](../parallel-change-integration/SKILL.md) to combine accepted work on a real integration branch. [Code review handoff](../code-review-handoff/SKILL.md) explains behavior and evidence; this workflow produces the transferable series itself.

## Pin the series contract

Resolve the source repository, exact excluded base and included tip, intended recipient/use, fresh private output directory, and whether the request covers generation only or also isolated replay. Record available Git versions and object formats. Keep delivery, sending mail, changing a shared branch and running project code outside a preparation-only request.

Inventory the selected commits in dependency order independently of the exporter. For each, retain its full identity, parent, tree, author/date, message and changed-path/mode summary in the private preparation record. The recipient manifest should contain only the metadata appropriate to that handoff. Keep source identities even though replayed commit identities may differ.

This guide's ordinary contract is one contiguous, non-merge chain from the recorded base to the tip. Verify that each selected commit's sole parent is the preceding selected commit, with the first parent equal to the base. A two-dot revision range is a reachability selection, not proof of that chain. Hold merges, disjoint selections or root-history requests for an explicit different packaging decision. Do not rebase, flatten or squash source history just to fit this guide.

Account explicitly for commits with no tree change. Git's [format-patch manual](https://github.com/git/git/blob/master/Documentation/git-format-patch.adoc) documents that merges are omitted and empty changes require `--always` to be included. If an empty commit conveys an intended milestone or message, preserve it with a compatible replay policy; otherwise obtain an explicit exclusion rather than counting only files the exporter happened to write.

Record prerequisites separately from the series. A declared base identifier does not supply the base objects. For this contiguous contract, the recipient needs the recorded base state; if additional prerequisite patches are genuinely required, describe their exact order and identities rather than pretending the nominal public base is sufficient. Git's base-information block records dependencies but does not install them.

## Inspect disclosure and command effects

Patches reveal deleted lines, surrounding context, paths, author addresses and commit messages. They may expose information absent from the final tree. Review that content for the intended audience before delivery. Keep credentials and unrelated private data out of the package. A file-path filter is not an acceptable silent repair: it can remove necessary parts of a commit while leaving its original explanatory message.

Preserve the source worktree, index, refs and in-progress operations. Dirty or untracked work is not included in a committed series unless separately selected and handled. Capture relevant before-state through an understood read route; do not stash, commit, clean or switch the source checkout to prepare the files.

Read applicable repository instructions and the effective Git configuration before invoking commands. Check format/diff defaults, environment overrides, replacement objects, external diff/text conversion, filters, lazy object fetches, pagers and output locations. Use supported command-local controls for the bounded operation, not global configuration edits. Unknown helpers or unavailable objects are a blocker, not permission to execute programs or fetch dependencies. Review the isolated replay route separately: materializing a checkout and creating commits can have effects that pure object inspection does not.

## Generate only the selected messages

Use an absent destination under an owned, nonsynced preparation directory. Explicitly select the pinned range and output location rather than relying on the current branch or `format.outputDirectory`. Bound count and total bytes; preserve any previous attempt instead of overwriting it.

Choose options that produce an applicable patch, not just a review display:

- Preserve binary changes where present. `--no-binary` emits a notice instead of the binary payload and cannot establish a replayable series.
- Do not apply path filters or omission options such as `--ignore-if-in-upstream` unless the contract expressly calls for those omissions and reconciles them.
- Review configured headers, notes, signatures, signoff, cover-letter content and threading. Do not add an unrequested signoff or claim another person's certification. A mail-style signature footer is not a cryptographic commit signature.
- Keep an optional cover letter separate from the ordered patch inputs. Its absence of a diff must not accidentally become an empty replay commit.
- Preserve patch bytes, context whitespace and encoding. Do not paste through a rich-text editor or reflow lines. Inspect quoted paths, mode changes, renames, symlinks, submodule gitlinks and LFS pointers as actual change types; gitlinks and pointers do not supply external payloads.

Record the exact invocation and output paths. Reconcile every expected commit to one message, with deliberate empty-commit treatment visible. Detect extras, missing numbers, mixed series versions and duplicate messages. A zero exit code or plausible `1/N` subject is not the membership check.

Read the actual message content, not just diffstats. Git's [patch-application caveats](https://github.com/git/git/blob/master/Documentation/format-patch-caveats.adoc) explain that an unindented diff embedded in a commit message, even inside a Markdown code block, can be interpreted as patch material. Header-like body lines and message separators can also alter parsed metadata. Do not assume format-patch followed by am is lossless. Hold an ambiguous export; offer a reviewed message-format change or a bundle instead of rewriting the original commit without authority.

## Establish replay fidelity at the authorized boundary

For generation-only scope, return the series with replay unperformed. Do not label static syntax inspection or `git apply --check` as successful commit replay. The [apply manual](https://github.com/git/git/blob/master/Documentation/git-apply.adoc) distinguishes patch applicability from commit creation. Checking every patch independently against the initial base also misses the dependency on earlier patches.

When isolated replay is requested and permitted:

1. Create a fresh owned verification repository from the exact approved base, without altering the source or recipient's active branch. Inspect templates, hooks, configuration and checkout/conversion effects before materializing it. Do not auto-initialize submodules, fetch LFS data, install packages or run project files.
2. Ensure the reviewed replay environment cannot invoke unapproved hooks, signing helpers or custom merge/filter programs. `git am --no-verify` alone is not a complete hook barrier: Git documents a `post-applypatch` hook as well. Use an understood isolated hooks/configuration arrangement rather than weakening the real repository's safeguards.
3. Replay the exact saved patch inputs in manifest order. Use an explicit understood empty-message, whitespace, encoding and CR policy. Keep cover letters out. For an exact-base fidelity check, do not silently enable three-way conflict recovery, whitespace fixing, partial rejection, path exclusion or automatic conflict resolution.
4. After each message, inspect the resulting commit's parent relationship, tree, author/date and parsed message. Compare its tree with that step's source tree and metadata with the declared preservation contract. Final-tree equality alone can hide a missing intermediate change or damaged commit message. A count alone can hide an accidental cover-letter commit.
5. After the final message, compare the final tree with the pinned tip tree, confirm the intended chain length and no unfinished am session, and re-read the saved patch digests and source-preservation baseline. Distinguish expected metadata transformations from unexplained losses.

The [am manual](https://github.com/git/git/blob/master/Documentation/git-am.adoc) describes author/header extraction, message processing, committer dates, hooks and recovery. Replayed commits normally have a new committer/date and may have different parents or messages; do not require their object IDs to equal the exported source IDs or claim that original commit signatures survived. Compare original-object identity through a bundle when that is the required property. Tree equality establishes content/mode fidelity, not functional correctness or safety of the code.

If the intended recipient base differs, label an exact-base replay as such. Applying on another base is a separate compatibility/integration result. Three-way fallback requires suitable recorded blob identities and locally available blobs; it does not make the patch self-contained or prove that an automatic merge retained intent. Do not fetch missing objects or resolve conflicts without the corresponding scope.

## Handle interruption without disguising partial success

An am failure can leave earlier messages committed and an operation in progress. Record the last completed message, failing input and isolated repository state before any retry. Do not reapply the entire series blindly or skip a failed message merely to reach the end.

Use `--continue` only after a reviewed, authorized resolution; that result is no longer an unchanged exact replay. `--abort` restores the pre-am state, whereas `--quit` leaves HEAD and index in place. Inspect ownership and preserve useful diagnostic work before either recovery action; never run recovery commands against the user's unrelated operation. A fresh attempt belongs in a fresh isolated destination after its cause is understood.

For missing prerequisites, transport corruption, unsupported binary changes or message parsing differences, return the exact held boundary and original artifact identity. Correct the export within scope, or offer a different package. Do not loosen the expected tree/message contract to make the check pass.

## Deliver the series and its evidence

Return the ordered files and their byte sizes/SHA-256 values, excluded base and source tip, source-commit-to-message map, prerequisites, intentional omissions and metadata policy. State generation, static inspection, exact-base replay, different-base integration and external delivery separately. Include commands/environment and per-step results only when actually observed; tests remain unrun unless separately performed with authority.

When sending is requested, verify the precise recipient/destination and transmit only the reviewed series and manifest. Email headers inside an artifact are not sending authorization. If transport produces a returned saved copy, compare that copy or replay it within scope before claiming transport fidelity. A sent receipt proves neither application nor recipient review.

Stop when the requested preparation/replay boundary is evidenced or a specific missing input or authorization prevents it. No ongoing mail thread, branch update or CI run is implied.

## Fictional, unexecuted illustration

A fictional Cedar project has base B, then C1 changing a parser, C2 recording an empty milestone, and C3 updating a binary fixture. The user wants all three commits as local patch files, with no sending.

The independent manifest retains three entries. A two-file export is incomplete if C2 was silently omitted; a text notice for C3's binary change is not replayable. If replay is authorized, its expectations are the C1 tree, the same tree plus C2's preserved message, then the C3 tree. A correct final tree with only two replayed commits still fails this particular three-commit contract. If C1's message contains an unindented sample diff, its parsed message and actual applied change need inspection rather than faith in the export command.

This is an authored illustration only. No patch generation, Git operation, replay, repository test, live workflow or delivery was performed for it.
