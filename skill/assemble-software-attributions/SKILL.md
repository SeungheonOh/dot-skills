---
name: assemble-software-attributions
description: "Assemble a distribution-specific third-party attribution and notice packet from identified components and supplied licensing records. Use for preserving provenance and notice text in a delivery artifact, not legal advice, license selection, vulnerability scanning or a compliance certification."
---

# Assemble a traceable software attribution packet

Produce the actual attribution document and referenced notice/license files for an identified software distribution, with a component-to-evidence map and unresolved items. Preserve what the sources say. Do not convert a package inventory or license scanner result into an assurance that distribution is legally permitted.

Use [release-artifact-verification](../release-artifact-verification/SKILL.md) for installation/runtime checks and [portable-project-handoff](../portable-project-handoff/SKILL.md) to prepare a broader transfer package. This workflow assembles the provenance and notice material; it does not rebuild, install or release the software.

## Input and output contract

Establish:

- Exact product release/candidate, distribution variant, source revision where known, and the bounded delivery contents or trustworthy membership record
- Components actually included, their resolved identities/versions, supplied SBOM or dependency records, vendored sources and bundled non-code assets
- Applicable existing attribution policy or owner-approved inclusion decisions, if any
- Component license declarations, copyright notices, NOTICE files, custom terms and source locations for those exact revisions
- Intended packet format, audience and authorized destination, plus whether the task is preparation or also requested placement into a delivery copy

Use metadata and records to find evidence, not to bypass missing source identity. A manifest range is not a resolved version; an SBOM for another build is not this distribution's inventory. Ask for the exact variant when desktop, server, web and source releases contain different components.

Return a readable attribution index, preserved source notice/license files when the requested packet requires them, a coverage ledger and a precise unresolved-item list. A Markdown document can link the packet's local files; a link-only list is insufficient when the agreed deliverable includes their text. Keep confidential evidence outside a public-facing packet.

## 1. Establish the distribution boundary

Record artifact identity and the basis for membership: inspected archive list, supplied build manifest, package metadata, or owner attestation. Label each method and its completeness. Preserve the original artifact and source records; work in a new preparation directory or authorized copy.

Inventory direct and transitive components, vendored snippets, embedded runtimes, fonts, icons, images, templates, generated code and other third-party material that the identified distribution actually contains. Do not assume all lockfile entries ship, or that only runtime dependencies ship. A build tool may contribute output or embedded material; a dependency labeled “dev” may still be bundled.

Give each included component a stable row with its canonical name, resolved version/revision, origin, locations in the distribution and membership evidence. Keep forks and locally modified copies distinct from their upstream release. For a supplied component with uncertain membership, retain an unresolved row rather than dropping it. Record confirmed non-shipped items separately with the evidence for exclusion.

Do not fetch arbitrary repositories or package archives by guessed name. Use verified upstream origins, exact release references and already-authorized sources. Reading a package's metadata does not authorize installing it, running lifecycle scripts, pulling containers or executing a scanner.

## 2. Collect and preserve component-specific notices

For each included identity, inspect the supplied package/source license declaration and relevant license, copyright, NOTICE and asset-specific files. Follow explicit file-level or directory-level attribution scope. A top-level license label may not cover every bundled asset or vendored file.

Capture:

| Field | Required distinction |
| --- | --- |
| Component ID | Exact component/version or revision, including fork/modification status |
| Applies to | Relevant shipped paths or component scope |
| Declared expression | Literal license identifier/expression, or “not found” |
| Text evidence | Source file/section, revision, and preserved destination |
| Owner decision | Existing approved choice or interpretation, if provided |
| Status | Collected, conflicting, missing, ambiguous scope, or pending owner review |

Copy source texts required by the supplied attribution policy or requested packet faithfully into the preparation packet. Preserve copyright holders, years, disclaimers, attribution wording, exceptions and modification notices. Do not rewrite a license for readability, translate it as a replacement, substitute a generic template, or delete notices because they look redundant.

Preserve expression structure. SPDX's [license-expression specification](https://spdx.github.io/spdx-spec/v2.3.1/SPDX-license-expressions/) gives distinct meanings to `AND`, `OR` and `WITH`; flattening them to a comma-separated list loses information. Retain parentheses, exception identifiers and custom `LicenseRef` associations. An `OR` declaration is not a recorded organizational choice; preserve the options and seek an authorized decision only if the requested packet depends on selecting one.

Use standard license texts from a verified authoritative source only when the identified declaration and task justify that substitution, and record that provenance. Never replace a modified/custom text with a standard text merely because their names look similar. Missing license text remains missing evidence, not implicit permission or a reason to label the component proprietary.

If the project uses REUSE metadata, apply the versioned [REUSE specification](https://reuse.software/spec-3.3/) to the file/header/sidecar/annotation relationships actually present. Do not assume one root declaration settles every file. This is an evidence-reading aid; using those records does not certify the project under REUSE or establish legal compliance.

## 3. Reconcile contradictions without making legal decisions

Compare package metadata, source headers, license files and versioned upstream records for the same component. Resolve ordinary identity errors first: another version, a fork, a generated copy or an asset with different terms can explain an apparent mismatch. Preserve the conflicting sources if that does not settle it.

Distinguish a source declaration, an existing owner-approved interpretation and an unresolved question. Do not independently decide compatibility between licenses, whether a linking arrangement creates an obligation, whether terms are enforceable, or whether a source offer is legally sufficient. Those questions need the responsible owner or qualified legal review. Continue assembling unaffected material while holding the dependent claim.

Do not invent missing copyright holders, remove an unfamiliar clause, select a preferred license, or relicense the user's project. If the supplied policy requires an action beyond notices, such as a source-delivery item, record the existing requirement, evidence and missing artifact; do not silently treat the notice packet as satisfying it. Do not claim that an unresolved item blocks a release as a matter of law; say which packet acceptance condition or owner decision is unresolved.

Keep attribution work separate from vulnerability or authenticity analysis. A matching name/version does not establish a safe package, and a complete notice packet does not establish provenance of binary bytes. Record the limits rather than expanding into unrequested audits.

## 4. Assemble a navigable packet

Use the requested structure or the product's established attribution format. A simple packet can contain `THIRD-PARTY-NOTICES.md` plus a `licenses/` directory. In the index, identify the product/candidate, each included component/version, its source, declared terms and the local notice/text files that apply to it.

Use collision-free filenames tied to component identity. Two packages can both contain `LICENSE`; do not let the second overwrite the first. Share identical standard text only when identity and contents are established, retaining every component's mapping and separate copyright/NOTICE material. Same license name is insufficient to deduplicate custom files.

Keep verbatim source text visually separate from editorial labels. Do not insert explanatory prose inside a legal text. Preserve source bytes when the delivery format allows it. If format conversion is requested, retain originals in the preparation evidence, document the conversion and check that meaningful text and scope survive. Do not claim byte identity after normalization.

The recipient-facing document should not reveal private registry URLs, internal paths, employee email addresses from logs, private repository names or security-sensitive architecture details. Public attribution names contained in source notices are not interchangeable with unnecessary private metadata. If a required notice itself contains information that the user says must not be disclosed, hold that notice's delivery and ask for an authorized resolution rather than silently redacting it or publishing it anyway.

Do not upload the packet, change sharing permissions, modify a signed archive or overwrite a published release merely because it is ready. Placement into a new authorized delivery copy is distinct from distribution to recipients. Publishing or sharing must be covered by the request and applicable authority.

## Acceptance and recovery

Reconcile in both directions:

1. Every identified shipped component maps to its collected notices or an explicit unresolved item
2. Every packet text maps back to a component and exact source; unrelated dependency files have not been copied without a reason
3. Declared terms, notices, exceptions and local modifications have retained their scope
4. Index links resolve to the intended local file, including similar names and case differences
5. Private evidence stays within its authorized audience

Check the preservation method actually used: compare copied files with their inputs when tools permit, or perform a labeled text inspection for a bounded textual packet. Do not claim hashes, scanner coverage or successful archive inclusion unless established. Report the inventory basis, actual checks, unresolved items and explicit limits. “Packet complete against supplied membership record” is narrower than “all legal obligations satisfied.”

Before updating an existing packet, preserve the prior version and identify which component identities changed. Do not retain old-version notices merely because the project name stayed the same, and do not delete useful historical records. Re-read a changed target before overwriting it; preserve unrelated owner edits.

If source text is unavailable, deliver the completed subset and a missing-text manifest instead of fabricating a substitute. If a copy or upload result is uncertain, inspect the target before retrying. If the build variant changes, invalidate the affected membership conclusions and reassemble only after the new boundary is known. Stop when the requested packet is ready for review with honest gaps, or the dependent next step requires an owner decision or new authority.

## Fictional, unexecuted example

Everything in this example is invented. No package, scanner, build, legal review or distribution was executed. The two quoted notice lines are synthetic author-created text, not a complete real-world license.

**Inputs:** A supplied membership record for Birch Desk 2.0 lists `glyph-panel@1.4`, vendored `line-fold` revision `r17`, and `Meadow Icons` revision `icons-6`. A development lockfile also names `bundle-check@5`, while the supplied build record states it contributes no shipped bytes. The attribution policy requests a review packet for included components.

`glyph-panel@1.4` has a supplied standard-license declaration and complete corresponding text, plus the notice “Copyright 2026 Glyph Panel contributors.” `line-fold` declares `MIT OR Apache-2.0`; its supplied text files and notice are complete, but no license choice is recorded. Meadow Icons has only “Copyright 2026 Meadow Studio” in the supplied asset record and no licensing text or permission record.

**Expected packet:** Preserve both complete glyph-panel records and map them to its shipped paths. Preserve line-fold's full declared expression, both supplied texts and its own notice; do not claim the organization selected an option. Retain Meadow Icons as included with missing licensing evidence, keeping its available notice rather than fabricating terms. Exclude bundle-check from the recipient index using the stated non-shipped evidence, while retaining that decision in the review ledger.

**Expected result:** “Attribution packet prepared against the supplied Birch Desk 2.0 membership record. Meadow Icons' licensing evidence is unresolved; the packet is incomplete for that component. The line-fold declaration is preserved without selecting a license. No legal-compliance or distribution-approval conclusion is made.” The recovery step is to obtain version-matched Meadow evidence and update that row and packet, not remove the asset or ship a guessed license.
