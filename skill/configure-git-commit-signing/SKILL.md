---
name: configure-git-commit-signing
description: "Configure one local Git repository to sign future commits with an established signing identity, distinguish signature validity from verifier trust, and verify the intended client without rewriting history. Use for existing-key signing setup or repair, not key enrollment, remote access, release signing or branch-policy administration."
---

# Configure Git commit signing with an existing identity

Deliver a scoped configuration candidate or authorized applied settings, a verified route to signing a new commit, and a clear account of who can verify it. Preserve existing history and work. A configured key name, successful push authentication and a hosting site's verification badge establish different things.

Use [existing SSH access](../connect-existing-ssh-session/SKILL.md) for remote login and [release-artifact verification](../release-artifact-verification/SKILL.md) for a distributed package's signature. [Missing Git work recovery](../recover-missing-git-work/SKILL.md) preserves historical objects; this workflow configures creation and verification of future signed commit objects. It does not generate, import, rotate, upload or revoke keys, change branch rules, re-sign old commits, publish commits or set up unattended signing.

## Establish the signing contract

Resolve from the request, project guidance and existing non-secret settings:

- The local repository and worktree, actual computer, Git executable/version, intended terminal or graphical Git client, and signing backend already installed
- The required signing format and approved existing key identity, identified by its full public fingerprint and owner rather than a filename or comment alone
- Intended author/committer identity, the specific commits or synthetic local check permitted, and whether future commits should sign by default or only on request
- The verifier that matters: local Git under an existing trust policy, a named recipient's documented policy, or an already configured hosting account
- Requested scope: preparation, exact local setting changes, bounded signing check, or a particular real commit
- Existing edits, index state, in-progress operations, configuration overrides and other linked worktrees that must remain unaffected

If no established signing identity exists, return a setup prerequisite. Do not make a new identity to finish this task. If the verifier or format is unknown, inspect the existing policy and prepare the unresolved choices; do not select a convenient key and call it authorized.

## 1. Separate selection, signing and trust

Treat these as independent checkpoints:

1. Git selects the intended backend and key
2. That backend can access the existing signing capability in this client session
3. A specific new commit contains a cryptographically valid signature
4. The relevant verifier accepts that key under its own trust policy
5. The signed object's identity and content meet the user's intended commit contract

An SSH key used to authenticate a remote connection is not automatically approved for signing. A public key comment or commit email does not authenticate the owner. Obtain the identity binding from the existing approved source. Keep the full public fingerprint in private evidence when needed, but omit unrelated identities, keyring inventories and machine paths from a shared handoff.

Choose the already required backend rather than changing formats to work around a failure:

- **OpenPGP:** identify the intended signing-capable key/subkey and its existing availability, expiry and revocation context. Prefer an unambiguous fingerprint selection. GnuPG documents fingerprint and explicit subkey selection in [Specify a User ID](https://www.gnupg.org/documentation/manuals/gnupg/Specify-a-User-ID.html). Do not force a particular subkey unless that is the approved policy
- **SSH:** establish the approved public key and existing signing agent or supported key route. Local verification also needs an authorized allowed-signers policy. Use the [OpenSSH allowed-signers documentation](https://man.openbsd.org/ssh-keygen.1#ALLOWED_SIGNERS) to interpret principals, namespace restrictions and validity intervals; do not invent a trust entry from the key presented by an untrusted commit
- **X.509 or a managed signer:** retain the organization's established certificate/backend route. If the required provider, certificate chain or supported client instructions are unavailable, prepare the exact prerequisite instead of exporting credentials or converting formats

Git supports openpgp, ssh and x509 formats, backend program selection and an explicit user.signingKey. For SSH, a public-key file can select an existing agent-held identity. Its allowed-signers and revocation files participate in local verification; a mathematically valid signature without accepted trust can still fail verification. See [Git signing configuration](https://git-scm.com/docs/git-config#Documentation/git-config.txt-gpgformat).

## 2. Inspect effective settings without disclosing secrets

Before baseline status, index or content inspection, review applicable core.fsmonitor behavior: it can execute a configured hook. Use an installed-version-supported, nonpersistent override that disables it for observation, or another understood nonmutating read route; do not change persistent settings to inspect them. Suppress unintended pagers, external diff/text-conversion helpers and implicit lazy fetching during the bounded inspection. Verify option support in the installed client rather than assuming current upstream syntax applies. See [Git's observation controls](https://git-scm.com/docs/git) and [filesystem-monitor configuration](https://git-scm.com/docs/git-config#Documentation/git-config.txt-corefsmonitor). If a safe observation route is unavailable, report that preservation baseline as unverified and hold dependent writes.

Bind payload and signature evidence to unreplaced object reads, using the supported nonpersistent --no-replace-objects route. Existing replacement refs can otherwise change the viewed content behind a named object; preserve them rather than deleting them to simplify verification. See [Git replacement behavior](https://git-scm.com/docs/git-replace).

Read only the relevant configuration keys and their origins. Include signing format/program, selected key reference, automatic commit signing, existing trust/revocation references, identity overrides and applicable includes. Do not dump all Git configuration or environment variables: unrelated values can contain credentials or private endpoints. A conditional include may select different identities for different repositories or branches.

Record each affected key's original state, including absence, repeated entries, origin and scope. Inspect any command-valued signer or key-selection helper before invoking it. A verification command can run a configured external program; it is not necessarily a passive parser. Treat a repository-supplied wrapper as executable code and establish its effects before using it.

Determine which client will actually invoke Git. A terminal, editor, container and graphical client can use different executables, configuration sources, agent sockets and protected-prompt routes. Do not forward an agent into a container, mount a key directory or change a global login profile to reconcile them. Resolve the actual requested client or return its missing prerequisite.

Prefer a repository-local candidate for one repository. Linked worktrees commonly share repository configuration; --worktree is not automatically isolated unless the worktree configuration extension is enabled. Inspect the current arrangement and do not enable a repository extension incidentally. See [Git worktree configuration](https://git-scm.com/docs/git-worktree#_configuration_file). If one worktree needs a different identity but the existing scope is shared, hold that decision rather than changing the identity for every worktree.

Before any real commit, inspect relevant hooks, templates, filters and automatic client actions. Git's [hook reference](https://git-scm.com/docs/githooks) describes commit hooks and their invocation. A signing check does not authorize running unknown project hooks, staging files, invoking networked filters or triggering an editor's automatic push.

## 3. Prepare and approve the minimal configuration

Produce a small before/after map: exact configuration location, each changed key, old value or absence, new non-secret value, reason and expected affected clients/worktrees. Keep private key material, passphrases, PINs and access tokens out of files, arguments and messages. Use a public fingerprint or an existing non-secret key reference; never copy private credentials into a project.

The candidate normally addresses gpg.format, user.signingKey and, only if requested, commit.gpgSign. Preserve an already working backend program and trust policy. Do not change tag-signing behavior, merge verification, global defaults or author/email identity unless that exact change belongs to the request. The [GitHub setup instructions](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key) illustrate backend-specific Git configuration; scope examples to the actual repository rather than blindly copying global commands.

Changing signing or verifier-trust settings is security-sensitive. Obtain the required action-time confirmation for the exact change before applying it, even when the broad goal is approved. New persistent credential access, agent enrollment, key uploads, trust-store additions and relaxed verification are separate boundaries. They are not implied by preparing a candidate or by an existing public key being readable. When approval is unavailable, deliver the usable candidate and leave activation pending.

After approval, apply only the reviewed settings using syntax supported by the installed Git. Read back effective values and origins from the target context. Do not use a broad replace-all or remove-section operation to erase multiple entries that have not been reconciled. Preserve unrelated configuration and concurrent edits.

If the signer requests a passphrase, PIN or hardware confirmation, have the owner complete the protected interaction for this identified signing attempt. Never ask for secrets in chat or supply them through a command line. Do not add keys to agents, save unlocking information, extend caching or enable unattended signing as a convenience.

## 4. Verify a new object without consuming existing work

Agree on the smallest meaningful check before invoking the signer. Configuration-only authority ends at readback and a check plan. A signing check requires authority for the exact local payload and execution; it must not accidentally commit the user's staged work.

For an isolated check, prepare a fresh private scratch repository only when authorized, with no remote, no source-project files and an understood empty template/hooks arrangement. Account for inherited Git configuration; a new directory alone is not isolation. Use the same approved Git/backend/key route, a clearly labeled synthetic message and an intentionally empty tree. Never run an empty-commit example in the real repository: --allow-empty permits emptiness but does not discard already staged content. The [commit reference](https://git-scm.com/docs/git-commit) documents signed commits, empty commits and the index's role.

A scratch signing success establishes that route's capability, not the target repository's hooks or graphical client's behavior. Reconcile target effective settings separately. If a real commit is explicitly requested, identify its intended parent, staged paths/content, author/committer and message first. Preserve staging boundaries; do not add -a, amend, reset or substitute another branch. A setup request alone is not approval for that commit.

After an authorized attempt:

- Resolve the exact resulting full commit ID and inspect its actual tree, parent, message and identity against the approved payload
- Verify that exact ID with the intended backend and existing accepted public-key/trust inputs. Use [git verify-commit](https://git-scm.com/docs/git-verify-commit), retaining meaningful output and exit status without secrets
- Record signature format, actual signer fingerprint, validity result and trust/identity conclusion separately. A success under an improvised self-trust file would not establish the intended verifier's acceptance
- Observe the requested client's signing path if that is part of acceptance. A shell success is insufficient evidence for a graphical-client request; do not manufacture a real commit solely to obtain that extra observation
- Reconcile the original repository's HEAD, staged/unstaged work, operation state and unaffected settings with the initial observations

Do not push a synthetic commit to obtain a badge. If a hosting site's status is part of the request, inspect an already available authorized object or wait for a separately authorized publication of the intended real commit. GitHub distinguishes its verification records and conditions in [About commit signature verification](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification). A local pass does not prove account association or remote policy acceptance, and a signature does not establish code safety.

## Recover at the failed boundary

- **Wrong key selected:** inspect the effective origin, client overrides and explicit selection; do not try every available key or silently substitute another identity
- **Signer unavailable:** distinguish missing executable, unavailable existing agent, locked device and unsupported format. Return the precise prerequisite; do not install software, copy keys or expand access without authority
- **Protected prompt unavailable:** preserve the failed attempt and use the established owner-side prompt route. Do not disable passphrase protection or repeatedly prompt the device
- **Valid signature, unaccepted trust:** report both facts and identify the missing verifier policy. Do not lower trust thresholds, add a key or remove revocation evidence merely to obtain success
- **Commit attempt failed or timed out:** inspect HEAD and the specific object/result before retrying. Failure after object creation or in a subsequent client action may leave a commit present; do not create a duplicate or amend it blindly
- **Remote status differs:** check exact object identity, format and documented account association without uploading keys or rewriting history. Local and hosted verification are separate evidence
- **Bad configuration change:** reconcile current settings against the captured baseline, then restore only task-owned entries within the approved recovery scope. Restore original absence when appropriate; do not replace an entire configuration file over concurrent work

Keep signed check objects private. Remove only task-owned scratch resources when cleanup is authorized; no global keyring cleanup, agent reset or repository garbage collection. Existing unsigned or differently signed commits remain untouched. Adding a signature to an old commit changes its object identity and is a separate history-rewrite decision.

## Accept and deliver

Return the actual settings candidate or applied change, scope, backend/key reference, default-versus-explicit signing choice, verification policy, check object ID when one exists, observed client and recovery instructions. Use accurate stages: prepared, settings applied/read back, signing exercised, signature verified, trust accepted, client checked, remote status observed. Leave unrun stages explicit.

Accept the requested level only when the selected identity matches the approved identity, the intended configuration scope is established, the specific signed object and verifier result are evidenced where execution was requested, and unrelated work/settings remain preserved. Stop at that outcome or the exact missing capability, permission or owner-side action. Do not expand completion into key management or publishing.

## Fictional, unexecuted illustration

A fictional developer wants future commits in one repository signed using an existing SSH signing identity, but has unrelated staged edits. Their established local verifier already trusts the approved public key. The terminal sees that agent-held key; a graphical client started earlier does not.

The candidate would select the existing public-key reference and enable signing only in the approved repository scope, after the required settings confirmation. The staged edits would remain untouched. An authorized empty-tree scratch commit could establish terminal signing and local verification; it would not establish graphical-client readiness or a hosted badge. The graphical-client stage would remain held for its documented existing-agent connection, without mounting credentials, uploading a key or committing the staged files.

If the scratch signature were mathematically valid but the actual intended verifier lacked accepted trust, the result would remain trust-unresolved. Creating an ad hoc allowed-signers entry would not be an acceptable shortcut. This illustration is original and unexecuted: no key, configuration, agent, repository, commit, signing operation, verification command or remote service was used or changed for it.
