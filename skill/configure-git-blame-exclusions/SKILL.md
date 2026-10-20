---
name: configure-git-blame-exclusions
description: "Prepare a reviewed ignore-revision file for mechanical Git changes and compare filtered with unfiltered line attribution. Use to make history easier to investigate without rewriting commits; not file ignore rules, author identity changes or proof of code ownership."
---

# Look past mechanical commits without losing their history

Deliver a small, explained blame-exclusion policy and an honest account of its effect on selected lines. The goal is to make useful earlier changes easier to find after a formatting or normalization commit, not to remove an inconvenient author or hide a behavior change.

[Git ignore rules](../configure-git-ignore-rules/SKILL.md) concern untracked paths, not historical revisions. [Git line-ending configuration](../configure-git-line-endings/SKILL.md) owns normalization itself. [Code review](../review-code-change/SKILL.md) owns judging a proposed change. This workflow changes how existing line history is presented, leaving source and commit history intact.

## Establish the intended view

Identify the repository, exact history endpoint, candidate mechanical commits and representative files. Resolve whether the user wants a proposal, an ignore-file edit, activation for one local repository or a shared hosting convention. Inspect existing policy and relevant configuration origins before adding another source. Do not require an elaborate intake for one known formatting commit.

Keep the original policy bytes and existing local changes. Do not stage, commit, push, rebase, amend author metadata or change user-wide settings merely to improve a blame view. A private command-line investigation does not require a published policy.

Use a permitted read route for history. Inspect relevant configured helpers before native Git commands; attribution is not necessarily inert when text-conversion drivers are configured. Git's [blame implementation](https://github.com/git/git/blob/master/builtin/blame.c) enables text conversion. For ordinary source text, use supported inspection with text conversion and external diff helpers disabled, or deliver a static proposal if a safe route is unavailable. Do not fetch missing history, run a formatter or execute repository programs as a side effect.

## 1. Select revisions from their changes, not their titles

Resolve each candidate to its full commit object identity. Review its complete changed-path inventory and actual differences against the appropriate parent context. A subject such as “format only” is a lead, not evidence. Look for changed constants, conditions, strings, generated outputs, permissions or configuration mixed with the intended transformation. Whitespace can be meaningful in source and data.

For every candidate, retain a brief decision: include with reason, exclude because substantive, or hold because the evidence is incomplete. A merge needs its relevant parent comparisons and conflict-resolution changes understood; a single convenient diff is insufficient. Do not automatically select all commits by an author, bot, date range or large change count.

Exclude a mixed semantic/mechanical commit from this narrow policy rather than pretending the file can ignore only its formatting hunks. Offer a one-off history investigation for the affected region instead. Do not rewrite old commits to separate them without a different explicit task.

Keep inaccessible parents, shallow history and missing objects visible. Absence of evidence before a boundary is not proof that the oldest available author introduced the behavior. Do not fabricate full hashes from short labels or replace unavailable revisions with similar-looking ones.

## 2. Write the smallest portable policy

Use one unabbreviated object name per entry and a short purpose comment. Preserve established entries unless changing them is part of the request. The [Git configuration reference](https://git-scm.com/docs/git-config#Documentation/git-config.txt-blameignoreRevsFile) documents ignored comments/whitespace, multiple ignore files and their ordering. Use the installed version's supported syntax; reject unresolved entries rather than silently dropping them to obtain output.

Separate three scopes:

- A candidate file used explicitly for a single comparison
- A repository-local `blame.ignoreRevsFile` setting, only when persistent local activation is requested
- A versioned root `.git-blame-ignore-revs` convention for consumers that support it

Inspect all effective values before changing local configuration. Preserve unrelated settings and consider shared linked-worktree configuration. Do not replace an existing list or set global configuration for convenience. Record the actual configuration file and prior values needed to reverse this task's change.

GitHub documents automatic use of the root `.git-blame-ignore-revs` file in its [file-history view](https://docs.github.com/en/repositories/working-with-files/using-files/viewing-and-understanding-files#ignore-commits-in-the-blame-view). That does not prove every local Git client or editor automatically uses the same file. A local candidate also does not establish that a hosted view has received it. Publication remains a separately authorized step.

## 3. Compare the same lines with and without the policy

Pin the source commit, path and selected line ranges. Use committed content for both views rather than silently comparing one view of a dirty working file with another view of HEAD. Keep whitespace, movement, copy and traversal options identical. Compare against a genuinely unfiltered baseline, not an ambient configuration that already ignores revisions.

The [Git blame reference](https://git-scm.com/docs/git-blame) defines `--ignore-revs-file`, including an empty filename that clears previously processed ignore-file lists. For a controlled comparison, clear those lists for the baseline; for the candidate, clear them first and then supply only the reviewed file. Do not also supply explicit `--ignore-rev` arguments to the baseline. Record the exact effective invocation and version when it is actually run.

Enable the supported ignored/unblamable indicators for the comparison. Git can reassign ignored lines to earlier or nearby changes; it cannot always identify another revision. The configuration reference documents `?` for reassigned ignored lines and `*` for unblamable ones; porcelain output has corresponding metadata. Keep these distinctions rather than presenting every displayed author as a certain original author.

Inspect a small, meaningful selection:

- Lines touched only by the approved mechanical commit
- A nearby genuine behavior change that must remain visible
- Newly introduced or extensively rewritten lines where attribution may be unresolved
- A representative renamed or moved region when the candidate affects one

For changed attribution, open the referenced earlier patch and surrounding source. Check whether it is useful for the investigation, not merely whether the mechanical hash disappeared. Record source location, baseline attribution, candidate attribution/marker and explanation. Retain ambiguous results honestly; do not broaden the ignore list until the display looks clean.

If execution is unavailable, deliver the candidate and these expected comparison cases with native attribution explicitly unrun. Reading a policy file is not evidence that a client accepted it or that its heuristics produced a useful result.

## Deliver, recover and stop

Return the exact policy patch, included/held revision decisions, requested activation status and concise comparison findings. Re-read the saved file and confirm only intended policy/configuration changed; preserve existing source and staging. Distinguish prepared, applied locally, published and observed on a host.

Provide an unfiltered route for future investigation. GitHub's documented bypass appends `~` to the SHA in the blame URL when its ignore banner is present; verify the actual page and endpoint rather than inventing a link. Local investigations can clear ignore-file lists as above. Neither view substitutes for reading the actual diff, and blame should not be used as an employee-contribution score or proof of sole ownership.

If attribution is misleading, remove only the task's new exclusion after checking for concurrent edits, or leave it proposed. If an ID later becomes unavailable after rewritten history, re-review the replacement identity and change before updating the file; do not infer equivalence from the commit subject. After an uncertain save, inspect current bytes before retrying. Stop when the requested policy/view has an evidenced result or a specific history, client or authorization gap remains.

## Fictional, unexecuted illustration

A project has a reviewed newline-only commit M and a later commit B that changes a retry limit while reformatting the function. The proposed policy includes the resolved full identity of M with a normalization comment, but not B. The comparison selects a line affected by M, the retry-limit line changed by B and one newly introduced line.

The expected useful outcome is an earlier patch for the mechanically changed line while the retry-limit change remains attributable to B. A reassigned or unblamable marker would be retained, not counted as a failure to make the display tidy. M and B are explanatory labels, not valid policy entries. This is a paper walkthrough only: no ignore file was activated, Git command executed, attribution observed or history rewritten.
