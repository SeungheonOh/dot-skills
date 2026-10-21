---
name: configure-git-identity-profiles
description: "Configure approved author and committer defaults for selected Git repositories or directory groups, trace conditional configuration and client overrides, and verify identity resolution without making a commit. Use for future attribution, not mailmap display, signing, authentication or history repair."
---

# Keep future Git commits under the intended identity

Deliver a minimal identity configuration candidate or authorized applied change, with a repository-to-identity map and evidence from the actual intended client context. Success means the selected contexts resolve the approved identity while unrelated contexts retain their intended behavior. A correctly edited configuration file is not sufficient evidence of the identity a client will use.

Use [mailmap configuration](../configure-git-mailmap/SKILL.md) for historical display aliases and [commit signing](../configure-git-commit-signing/SKILL.md) for cryptographic signatures. Use [linked worktree creation](../create-linked-git-worktree/SKILL.md) when another checkout is needed. This workflow changes future attribution defaults; it does not authenticate a person, log into a host, repair old commits or create a demonstration commit.

## Establish the identity and affected contexts

Determine the approved name/address pair for each context from the user's request or established project policy. Do not derive a personal address from a login, remote URL, recent contributor list or operating-system account. Keep an approved project no-reply address when that is the intended identity. If the address is unknown, prepare the scope decision without inventing it.

Resolve:

- The repositories or directory group to cover, plus a nearby repository that must remain unaffected
- The actual computer, Git version and terminal, editor, container or graphical client that will make commits
- Whether every linked worktree should share the identity, and whether bare repositories matter
- Whether the request is a proposal, a one-repository change or a reusable profile
- The desired behavior outside covered contexts: preserve an existing default or leave identity unresolved

Prefer one repository-local change for a one-repository request. Do not turn that request into a global profile migration. A reusable profile needs an explicit boundary and an agreed fallback; a directory name alone is not proof that every project below it belongs to one employer or identity.

Saving local attribution settings is not permission to add an email to a hosting account, change credentials or signing trust, stage or commit work, push, publish the profile, or rewrite history. A name and address may become public in later published commits; confirm the intended attribution rather than silently substituting a private address.

## 1. Inspect the effective identity, not just one file

Read repository instructions and identify the real checkout, Git directory and shared common directory through an understood read-only route. Do not assume `.git` is a directory. Preserve existing index, working files, refs and in-progress operations; identity configuration does not require stashing or cleaning them.

Inspect only relevant settings and origins: user, author and committer name/email; `user.useConfigOnly`; applicable includes; and client-provided overrides. Keep credentials, full environment dumps and unrelated remote URLs out of the report. Record original values, absence, repeated entries and the exact files a proposed edit would affect. Check whether those files are symlinks or shared with other contexts before writing.

Git's [configuration reference](https://git-scm.com/docs/git-config) establishes that includes are processed where encountered, later values can override earlier ones, and repository settings can supersede global values. Author/committer-specific settings and environment variables can override user defaults. `user.useConfigOnly` prevents guessed defaults; it does not remove an already configured fallback or enforce the chosen profile against overrides.

Therefore, trace an unexpected identity to its source before proposing a fix. Adding the same desired value repeatedly at different scopes hides the cause. An obsolete repository-local email needs a specific keep/change decision, not an unexplained new global value. Inspect the actual client's launch context when its result differs from a terminal; do not change shell startup files or restart unrelated applications as a shortcut.

## 2. Choose a scope that matches the requested boundary

Use the smallest understandable arrangement:

- **One repository, all its worktrees:** consider repository-local identity settings after confirming that shared effect
- **Existing per-worktree configuration:** use it only when already supported and appropriate; do not enable a repository extension incidentally
- **A directory group:** consider a small conditional include and a separate identity-only profile, with positive and negative contexts identified in advance
- **Unclear ownership or overlapping groups:** keep the candidate unapplied until the ambiguous contexts have an identity decision

Git's [worktree documentation](https://git-scm.com/docs/git-worktree#_configuration_file) explains shared repository configuration and the worktree configuration extension. Without that extension, `--worktree` does not provide the isolation its spelling might suggest. Enabling it can require configuration migration and is outside an ordinary identity edit. Keep sibling worktrees in the impact map.

For conditional profiles, consult installed-version documentation, not only the latest online manual. The [conditional-include reference](https://git-scm.com/docs/git-config#_conditional_includes) distinguishes Git-directory matching from worktree-path matching. A `gitdir:` condition follows the administrative Git directory, not a linked checkout's visible folder. A trailing slash expands recursively; `gitdir/i:` ignores case. Newer condition types must be supported by every intended client. Do not use an unsupported condition and interpret a silent nonmatch as success.

Avoid branch- or remote-dependent selection unless that is the requested policy. If such an existing condition affects the task, account for its matching contexts without changing branches or endpoints merely to exercise it. For remote-conditioned includes, Git prohibits remote URL definitions in files included through that condition. Keep the new profile identity-only rather than copying an unrelated configuration bundle.

For a fail-unconfigured policy, identify any existing fallback that would defeat that goal. Removing it can affect unrelated projects, so propose the removal and impact explicitly. Do not claim `user.useConfigOnly=true` alone implements that policy. If fallback removal is outside authority, leave it intact and report the narrower result honestly.

## 3. Prepare and apply only the agreed change

Return a short before/after map first when the scope needs a decision:

```text
context | approved author/committer default | current winning source
proposed file/key or include | affected siblings | fallback behavior
```

Keep profile files in an approved private configuration location, not in a tracked project directory by convenience. Preserve comments, unrelated sections and existing include ordering. Do not add credentials, signing helpers, hooks or remote settings to an identity profile. Do not overwrite an existing file with the same proposed name without inspecting it.

When the exact ordinary configuration change is authorized, apply it using the installed Git's supported interface or a precise file edit. Resolve repeated/conflicting entries rather than using a broad remove-section or replace-all. If touching several files, plan the intermediate state: do not leave an active include pointing to an incomplete profile. Retain recoverable original values without copying unrelated sensitive configuration into a shared artifact.

Read back the changed bytes and effective origins from the target context. A write success is only the application stage. If a save is uncertain or interrupted, inspect the current files before retrying; do not append a second copy of the include.

## 4. Verify identity resolution without creating a commit

Use [git var](https://git-scm.com/docs/git-var) to inspect the logical author and committer identities separately. These invocation shapes are examples only, not executed checks; replace `REPO` with the safely supplied verified path and use the intended executable and client environment:

```text
git --no-pager -C REPO var GIT_AUTHOR_IDENT
git --no-pager -C REPO var GIT_COMMITTER_IDENT
```

Record the exit status and exact name/address result privately. The identity output also contains a date/time component; compare the intended attribution fields rather than treating timestamp differences as an identity failure. Query specific variables, not `git var -l`, which also lists configuration. A failed resolution is evidence, not a reason to fabricate a default.

Check the relevant boundary cases proportionately:

1. The intended repository resolves both roles as approved, with the expected configuration origin
2. The nearby excluded repository preserves its prior intended result
3. A linked worktree resolves according to the real administrative path and shared-scope decision, not the assumption made from its visible directory
4. Every known overlapping include or local override has a reconciled outcome
5. The intended client agrees, or client-specific resolution remains explicitly unverified
6. Changed files contain only the agreed settings; source work, index and refs remain unaffected

Do not create repositories, move checkouts or switch branches solely to fill the matrix without authority. Use existing authorized contexts; otherwise document the unexercised boundary. An isolated parse of a candidate can check syntax but not prove the actual client's winning identity.

Scope the claim to new ordinary commits. [Git commit](https://git-scm.com/docs/git-commit) supports explicit author overrides and reuse of existing authorship; amend/reuse workflows can retain an earlier author. Identity defaults are not a promise that every future command will replace both roles. Do not use `--reset-author` or amend an old commit as an identity-configuration check.

No test commit is needed for this workflow. In particular, `--allow-empty` is not protection for staged content, and invoking commit may introduce hooks, signing and client actions unrelated to identity readback. If the user separately requests a real commit, inspect its actual payload and attribution under that task's authority.

## Deliver, recover and stop

Return the actual candidate or applied settings, affected contexts, winning sources, author/committer results, preserved fallback and any unverified client. Separate static review, settings applied, identity resolution observed and real commit attribution observed; the last is normally outside this task. A terminal result does not establish hosting-account association or a graphical client's behavior.

If the wrong identity persists, inspect the winning local setting, include order, environment and client override before broadening scope. If a linked worktree matches unexpectedly, revisit its administrative path and shared configuration. Do not change remote URLs, signing keys or account emails to force attribution agreement.

For rollback, reconcile current settings with the baseline and restore only task-owned changes, including original absence when relevant. Preserve concurrent edits and existing profile consumers. Do not delete a shared profile merely because this task no longer needs its include. Old commits remain unchanged; repairing an accidentally published identity is a separate history/privacy decision, not automatic cleanup.

Stop when the requested configuration boundary and available resolution evidence are complete, or identify the exact missing identity, scope approval or client access. No periodic enforcement, repository migration or publication is implied.

## Fictional, unexecuted illustration

Mira wants the approved work address for existing repositories under `~/client-work/`, while an unrelated personal repository keeps its current identity. The proposed private profile contains only:

```gitconfig
[user]
    name = Mira Vale
    email = mira@work.example.invalid
```

A candidate include in the approved user configuration is:

```gitconfig
[includeIf "gitdir:~/client-work/"]
    path = ~/.config/git/mira-work.inc
```

One work repository already has an explicit local personal email. The candidate is not called successful merely because the include matches: that local entry needs a specific correction decision and subsequent readback. A linked checkout in `~/personal/review/` whose administrative Git directory remains under the work repository also needs the worktree scope reviewed. Moving its visible folder is not assumed to change its profile.

The expected acceptance is the approved work identity for covered contexts, the unchanged personal identity for the unrelated repository, and an explicit outcome for that linked checkout. Adding `user.useConfigOnly` would not eliminate an existing global fallback. These are authored expectations only: no configuration was applied, identity query run, repository changed, commit created or service contacted for this illustration.
