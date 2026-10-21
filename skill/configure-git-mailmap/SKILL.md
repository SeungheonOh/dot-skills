---
name: configure-git-mailmap
description: "Prepare or revise a Git mailmap that consolidates confirmed contributor aliases in history reports without rewriting commits. Use for canonical author/committer display identities, not identity authentication, account association, privacy erasure or contribution scoring."
---

# Consolidate confirmed Git contributor aliases

Deliver a small `.mailmap` patch, an evidence-backed alias decision list and a comparison of raw versus mapped identities for the intended report. Preserve distinctions between different people and leave uncertain aliases unmapped. A tidier contributor list is not success if it assigns someone else's work to the wrong person.

Use [blame exclusions](../configure-git-blame-exclusions/SKILL.md) to look past mechanical revisions, [commit signing](../configure-git-commit-signing/SKILL.md) for future cryptographic signing, and [release notes](../change-log-release-notes/SKILL.md) for audience-facing descriptions of shipped changes. This workflow changes identity presentation; it does not change old commit metadata, authenticate contributors or publish acknowledgments.

## Establish the mapping's purpose

Identify the repository, intended consumer and bounded history endpoint or release range. Determine whether the request covers a proposal, a local `.mailmap` edit, a private report-specific mapping or publication. Read the existing map before proposing a new one. For a single confirmed alias, do not require an organization-wide identity census.

Resolve the approved display name/address and the evidence that links each old identity to it. Prefer a contributor's explicit declaration or an established maintained project record over guesses from similar names. A matching avatar, commit style, email local part or company domain is not enough. Preserve pseudonyms and project-approved no-reply addresses rather than substituting a supposedly more professional personal address.

Mapping can publicly connect previously separate identities. A readable old address is not permission to publish a new personal address or reveal a private alias relationship. Keep supporting evidence private when appropriate; obtain the needed authority before sharing it. If the desired display identity is unsettled, prepare the unambiguous subset and ask only about the disputed mapping.

Do not change `user.name`, `user.email`, account settings, signing trust, commit messages or history to implement this request. Saving a map does not authorize staging, committing, pushing, sending mail or editing a public contributor page. Never claim a mailmap removes an address from repository history.

## 1. Inventory raw identities before deduplicating

Pin the inspected revisions. Record author and committer identities separately for the relevant commits, retaining their full object IDs. A release integrator can be the committer of another person's authored change; combining those roles loses information. Avoid reading or exporting unrelated history when a bounded window answers the request.

Use an authorized nonmutating read route. Before native commands, account for implicit fetching, replacement objects, pagers and configured helpers. Use supported command-local controls to avoid unintended acquisition or execution, including signature-verifier invocation in log output. Do not run repository programs, relax security settings or fetch missing history for a display cleanup. If the available source is only an export, label missing history/configuration evidence instead of inventing it.

Git's [pretty-format reference](https://git-scm.com/docs/pretty-formats) distinguishes raw `%an`/`%ae` and `%cn`/`%ce` from mailmap-aware `%aN`/`%aE` and `%cN`/`%cE`. Use raw fields for the starting inventory, not an already normalized report. Retain names with spaces and non-ASCII characters intact; use an unambiguous record format rather than splitting on whitespace. Do not put names or email values into shell commands without safe argument handling.

Keep a compact decision list:

```text
raw name/address | role and example commit IDs | proposed display identity
identity-binding evidence | map / leave unchanged / unresolved | reason
```

For each proposed merge, inspect every distinct observed name associated with the source address in the declared range. Shared service accounts, recycled addresses and automated submitters need special care. If two people used exactly the same name/address, this format cannot distinguish them by date or commit; leave the ambiguous case alone rather than pretending it has a time-qualified rule.

A report's bounded range does not bound the reach of a saved repository map. Before activating a general map, inspect the affected aliases across the available history that its consumers will use and resolve any wider collisions. When only a release window has been reviewed, keep the candidate report-specific and label that limit instead of claiming it is safe for all history. Missing or shallow history remains an explicit gap.

## 2. Choose the narrowest rule that expresses the evidence

The [mailmap syntax reference](https://git-scm.com/docs/gitmailmap) defines these shapes:

```text
Display Name <old@example.invalid>
<display@example.invalid> <old@example.invalid>
Display Name <display@example.invalid> <old@example.invalid>
Display Name <display@example.invalid> Old Name <old@example.invalid>
```

They change, respectively, the name, the address, both fields for an address, or both fields for a matching name/address pair. Angle brackets matter. Names and addresses match case-insensitively, so capitalization is not a way to distinguish two people. A `#` begins a comment; blank lines are ignored. Do not treat these as wildcard, regular-expression or date-range rules.

Prefer the name/address-qualified form where an address alone would overreach. A name-only correction should not incidentally replace an address. Make each observed source alias point directly to its approved result; do not depend on chains of mappings to reach the final identity.

Preserve existing comments and unrelated mappings. Investigate duplicate or conflicting entries instead of relying on a convenient ordering to hide the conflict. Explain each new relationship briefly without embedding private biographical details. A mapping file is a presentation policy, not proof of legal identity, employment, copyright ownership or permission to contact the mapped address.

## 3. Control which mapping sources the consumer reads

Distinguish a tracked root `.mailmap` from an extra local map and a map selected from a Git blob. Inspect only relevant configuration values and origins, not the complete configuration or environment. The [configuration reference](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mailmapfile) says `mailmap.file` augments the default map; `mailmap.blob` can supply another source, with the file taking precedence over the blob. A bare repository defaults its blob source to `HEAD:.mailmap`; a non-bare repository does not. A file override is therefore not automatically a candidate-only isolation mechanism.

For a proposal, save the candidate outside the active location. For an authorized edit, reconcile current bytes with the captured baseline and change only the reviewed entries. Do not overwrite concurrent edits or create a second conflicting policy because an existing source is inconvenient. Inspect the actual file type before writing; do not replace a symlink or write through it as a shortcut. Git's mailmap reference notes that Git does not follow a working-tree `.mailmap` symlink.

For a private report, use a supported nonpersistent selection route or an authorized isolated context with all mapping sources understood. Do not change global configuration to make one report work. A linked worktree or editor may have a different effective context; document the actual consumer rather than assuming every client honors the same map.

Pin the mapping as well as the history. Reporting on an old commit while using today's working-tree map is legitimate if intentional, but it is not the same as using the map stored in that old revision. Record the exact map bytes or blob identity and active overrides used by the comparison.

## 4. Verify individual mappings, then the real report

When native inspection is authorized and available, use [git check-mailmap](https://git-scm.com/docs/git-check-mailmap) with safely supplied contacts. It returns the canonical identity when a mapping applies and otherwise preserves the input. Its `--stdin` interface accepts one contact per line. On versions supporting `--mailmap-file`, that option adds a higher-priority map rather than excluding other configured maps. Inspect installed help instead of assuming a newer option exists.

Check the complete changed alias set, not only one favorable example:

- Every approved raw alias reaches the exact intended display identity
- A different person with the same address is unaffected when the rule should be name-qualified
- An unrelated person with the same name but a different address is unaffected
- Case variants have the documented matching behavior, and canonical identities remain as intended
- Existing mappings outside the requested change retain their previous results

Compare baseline and candidate against the same raw identity inputs and the same declared source layers. Explicitly label whether the baseline is raw identity or the existing effective mapping. Do not describe a candidate-augmented existing map as an isolated candidate test. If a safe complete context cannot be established, return static expectations with native mapping unrun.

Then inspect the user's actual report route. The [log reference](https://git-scm.com/docs/git-log) provides explicit mailmap-enabled and disabled views; do not rely on ambient defaults. When using custom formats, choose the documented raw/mapped placeholders deliberately. Compare exact commit membership, roles and display fields, not just the number of displayed names. Historical commit IDs, parent relationships and source contents must not change as part of this workflow.

If the consumer is a contributor summary, use a pinned range and explicit grouping. [Shortlog](https://git-scm.com/docs/git-shortlog) distinguishes author, committer and trailer groups; parsed identity trailers can be mapped too. Multiple groups or co-author trailers can associate a commit with more than one contributor, so summed credits need not equal the number of commits. Explain that policy rather than treating every count difference as a mapping defect. A contribution count is not a measure of effort, quality or employee performance.

A local command's result does not establish a hosting site's account association, graph, blame page or acknowledgments. If one of those is the acceptance target, verify its documented support and actual authorized view separately; do not publish a trial map or add an email to an account to force agreement.

## Deliver and recover

Return the minimal patch or saved file, approved/held alias decisions, exact history and map sources, and a short before/after comparison. Distinguish prepared, edited locally, parsed by the named Git version, consumed by the target report, and published. Keep publication pending unless separately authorized. Acceptance requires correct approved mappings, preserved unrelated identities and work, unchanged history, and honest limitations on the consumer evidence.

If two contributors collapse unexpectedly, inspect address-only rules and competing map sources first. Narrow or remove only the task-owned entry after reconciling current edits; do not rewrite commits to repair a presentation mistake. If an alias remains unchanged, check exact input, syntax, selected source and client support before broadening the match. An uncertain write needs readback before retrying. Preserve the decision evidence for a later reviewer without distributing unnecessary personal data.

Stop when the requested mapping and report boundary are evidenced, or identify the precise unresolved identity, access or consumer-support decision. A proposal can be complete while activation and native verification remain unperformed.

## Fictional, unexecuted illustration

A project has confirmed that `M. Vale <mvale@old.example.invalid>` and `Mira Vale <mira@project.example.invalid>` refer to one contributor who wants the latter display identity. Two different people also used the shared address `build@project.example.invalid`; only the identity named `Mira V.` is confirmed as Mira.

The candidate contains:

```text
Mira Vale <mira@project.example.invalid> <mvale@old.example.invalid>
Mira Vale <mira@project.example.invalid> Mira V. <build@project.example.invalid>
```

The expected comparison maps the old personal alias and the name-qualified shared alias, while `Oren Dale <build@project.example.invalid>` remains unchanged. An unknown `Contributor <build@project.example.invalid>` remains unresolved. A broad address-only mapping for the build address would fail the preservation requirement. If both people had used the identical `Mira V.` tuple, the second rule could not separate them and would be held.

This is an original paper illustration, not a run result. No Git command, repository edit, report generation, identity verification, account change or publication was performed for it.
