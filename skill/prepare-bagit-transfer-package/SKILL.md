---
name: prepare-bagit-transfer-package
description: "Prepare selected files as a BagIt preservation-transfer package with separate payload and tag integrity, stable source selection, and explicit completeness and validation status. Use when a receiver requires BagIt, not for a generic ZIP, research metadata graph, or repository deposit."
---

# Prepare a BagIt transfer without rewriting the evidence

Produce a new BagIt package from a bounded file selection, with a preparation receipt that distinguishes source coverage, package integrity, and receiver acceptance. A preservation service asking for BagIt needs more than a checksum list placed beside an arbitrary folder.

Use [portable-project-handoff](../portable-project-handoff/SKILL.md) for an ordinary project ZIP, [verify-checksum-manifest](../verify-checksum-manifest/SKILL.md) for checking an existing checksum list, and [package-ro-crate-research-objects](../package-ro-crate-research-objects/SKILL.md) for research-object relationships. Those workflows do not replace BagIt's packaging contract. This workflow does not certify archival quality, scientific validity, publisher identity, or successful repository ingest.

## Set the transfer contract

Identify the source selection and versions, recipient's required BagIt version/profile, accepted checksum algorithms, permitted filenames, size limits, and approved preparation destination. Resolve whether the requested output is a directory or a serialized archive and whether all payload must be locally included. Read the receiver's published requirements rather than inferring a profile from its institution's name.

Default the preparation to a new, private, copy-only location outside the source and outside watched or automatically shared folders. A request to package files is not permission to move the originals, change their metadata, upload a collection, accept deposit terms, or expose it publicly. Obtain any missing authority for a separate delivery step.

Use the pinned BagIt version the receiver accepts. The compact contract below targets **BagIt 1.0**. A legacy receiver may need another version; do not relabel incompatible metadata as 1.0 or silently downgrade to satisfy a tool. If the receiver's contract is unavailable, produce a clearly labeled candidate and identify that remaining acceptance dependency.

## Freeze the selected bytes before bagging

Keep an independent selection ledger: source identity/version, source-relative name, proposed package-relative name, available byte count and observed digest, and included/excluded/held disposition. Distinguish a supplied digest from a calculated one. This ledger establishes the intended selection; a generated manifest cannot prove that an omitted source file was never required.

Include hidden files only when they belong to the approved selection. Preserve byte-identical copies unless a specific transformation is authorized. Hold cloud placeholders, symbolic links, devices and application-native packages until their intended representation is settled; do not follow links into unselected folders or silently hydrate an entire collection. Retain a mapping for any approved rename, including case or Unicode collisions on the receiver's platform.

A BagIt creator may rearrange the directory it receives. The [Library of Congress implementation documentation](https://github.com/LibraryOfCongress/bagit-python) describes turning an existing directory into a bag. Pass a dedicated staging copy, never an irreplaceable source directory. Inspect the installed tool's behavior and supported version before use; do not assume a familiar command name guarantees the required output contract.

Reserve room for staged payload, package metadata, any outer archive, and any separate readback copy. If the source changes while copying or hashing, hold the affected identities and establish a stable version. Do not call a changing-source discrepancy transfer corruption or silently generate a new baseline from whichever bytes arrived last.

## Assemble the two integrity layers

Apply the following [BagIt 1.0 rules from RFC 8493](https://www.rfc-editor.org/rfc/rfc8493.html):

- Put payload files under `data/`. Include at least one `manifest-<algorithm>.txt`; each lists every payload file exactly once, not directories.
- Write `bagit.txt` as two ordered lines: `BagIt-Version: 1.0`, then `Tag-File-Character-Encoding: UTF-8`. Use UTF-8 without a BOM for `bagit.txt` and all other UTF-8 text tag files.
- Manifest records pair a hexadecimal checksum with a bag-root-relative path, separated by whitespace. Use `/`; percent-encode only CR, LF and percent characters in paths.
- An optional `tagmanifest-<algorithm>.txt` covers every payload manifest, should cover remaining tag files, and excludes payload files and all tag manifests.
- Optional `Payload-Oxum` in `bag-info.txt` is total payload bytes followed by a dot and payload file count; it is not checksum validation.
- Optional `fetch.txt` identifies remote payload. Its entries also belong in every payload manifest. Missing remote bytes leave the package incomplete.
- A complete bag has all required elements, every file referenced by payload or tag manifests, every payload file listed in every payload manifest, and all present elements conforming to BagIt 1.0. A valid bag is complete and has every payload- and tag-manifest checksum successfully verified.

Use a receiver-supported strong algorithm, explicitly selected rather than inherited accidentally from a tool default. Keep the declaration, metadata, payload manifests and tag manifests distinct in the plan. A payload digest must be calculated over the final staged file, not a converted preview or an earlier source revision.

Finalize descriptive metadata and payload manifests before generating tag digests. If a later edit changes a covered metadata file, refresh the affected tag digest and repeat the relevant verification. If payload changes legitimately, treat that as a revised candidate with refreshed payload coverage and dependent tag checks, not an invisible repair to a previously delivered bag.

Keep private preparation logs and the final validation receipt outside the bag unless they are explicitly intended as transferred metadata. This avoids continuously invalidating covered metadata when appending verification results. If an outer archive is requested, keep its own digest outside that archive as well.

## Keep remote payload an explicit exception

For an ordinary self-contained handoff, stage the approved bytes locally. Do not replace a large or unavailable file with a download URL just to meet a package-size limit. If the receiver explicitly accepts a remote-payload workflow, agree which source versions and retrieval obligations belong to sender and receiver before preparing it.

Treat a fetch list as data, never as authority to access arbitrary locations. Inspect destinations, redirects, target paths, credentials, size budgets and permission requirements before any authorized retrieval. Do not embed authentication tokens, expiring signed URLs or personal credentials in transferred metadata. Do not let a requested download overwrite an existing staged file or escape the package through a path or link.

If an expected digest is unavailable, do not invent one or substitute a placeholder and call the package ready. If bytes cannot be obtained within scope, return the blocked item and a partial preparation record. Removing it from the selection or changing to a remote delivery contract requires a real scope decision, not merely an edit that makes validation appear successful.

## Check the saved candidate, not just the creation result

Perform only checks supported by the available environment and current authorization. Reopen the saved declaration and manifests, inspect the actual candidate tree independently, and use an appropriate BagIt validator when permitted. Record the tool/version, exact candidate identity, mode, diagnostics and checks that did not run.

The [Library of Congress tool documentation](https://github.com/LibraryOfCongress/bagit-python) distinguishes full validation from its fast structure/size-count mode. A fast result is not evidence that payload bytes were hashed. It also warns against accidentally regenerating manifests while saving metadata: rehashing corrupted received content would erase the comparison baseline. Preserve a received or failed candidate unchanged while diagnosing it.

Keep four conclusions separate:

1. **Selection agreement:** Every promised source item has its intended package identity and disposition; no unselected content entered the staging copy.
2. **Structure and coverage:** Required package elements and manifest memberships agree, names remain unambiguous, and no listed path escapes the staged root. Distinguish extra payload from intentionally unlisted support metadata.
3. **Byte agreement:** Full checks establish both staged-copy agreement with the selected source baseline and package-manifest agreement. A skipped, unreadable, unstable or budget-limited file is unresolved, not a match.
4. **Receiving result:** An actual receiver response concerns the exact submitted package and profile. Local validation alone is not ingest acceptance, and a successful upload alone is not preservation confirmation.

Do not open executables, notebooks, macros or scripts inside the payload as a packaging check. Bagging opaque content is not a request to run it. If an outer archive is required, inspect and read back the exact archive in a fresh bounded location without executing its contents; report unavailable extraction or target-platform checks rather than claiming them.

For a failed digest, preserve the candidate and determine whether the intended source, staged copy or supplied manifest is wrong. Correct an authorized preparation error in a new candidate. Never “repair” a received checksum baseline solely to agree with observed bytes. For a path collision, missing file or receiver-profile conflict, name the affected item and the decision or evidence needed.

## Deliver the package and bounded status

Return the package location, source selection/version, BagIt version and receiver profile, algorithms, actual verification coverage, any external payload obligations, and remaining blockers. Make the receipt readable without exposing excluded private filenames or internal source locations unnecessarily.

Label the result according to evidence: prepared candidate, complete but checksums not fully checked, fully validated package, or submitted package with the observed receiver response. Preserve distinctions when one layer passed and another is unknown. If delivery is authorized, verify its exact destination and check an uncertain submission for an existing received object before retrying. Stop at local preparation when sending was not requested.

## Fictional, unexecuted illustration

A local history project selects three audio recordings and a rights note for a receiving archive that requires a self-contained bag. One recording is only a cloud placeholder. The proposed preparation holds that recording instead of replacing it with an unapproved remote reference. Even if the other files could be bagged successfully, that would not satisfy the four-item selection.

After the owner supplies the selected recording version, the proposed process stages all four files and creates package metadata. A later correction to the transferred description requires refreshing its tag-integrity coverage, not changing audio digests. An institution's acknowledgment that an upload arrived would still be distinct from acceptance into its preservation system.

This is original fictional design material, not an observed run. No bag, checksum comparison, validator result, archive extraction, remote retrieval or deposit was executed for this illustration.
