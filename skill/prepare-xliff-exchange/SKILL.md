---
name: prepare-xliff-exchange
description: "Prepare or reconcile a version-bound XLIFF translation handoff, preserving resource identities, inline-code relationships, metadata and source lineage across the outbound and returned package. Use for interchange and return acceptance, not ordinary prose translation or a live localization-system import."
---

# Prepare an XLIFF exchange

Turn an authorized localization export into a traceable package for a translator or receiving tool, or reconcile a returned package against the exact outbound snapshot. The result is a candidate exchange file and a manifest showing what can safely return to which source resource. A syntactically valid bilingual file is not evidence that a particular importer will reconstruct the original application or document.

Use [translation-release-review](../translation-release-review/SKILL.md) when the task is to write or assess the target-language wording. This workflow handles the exchange boundary: identity, round-trip preservation, source drift and acceptance of returned units. It does not silently create a translation, approve its meaning, import into a live system or publish a release.

## Establish the exchange contract

Resolve these from supplied exports and the request before asking for missing information:

- Source project/file identities and revision, source and target locale tags, selected resource set and exclusions
- Exporter and intended importer, their versions when known, and the actual XLIFF version/profile they support
- Existing XLIFF plus required skeleton/original-data files, or an explicit source-to-XLIFF mapping for a requested new export
- Which fields may change: target text, review notes, state, approved segmentation changes or specified metadata
- Output location, whether this is outbound preparation or returned-file reconciliation, and any authorized recipient

Prefer the existing native export when available. Do not manufacture an importable XLIFF by wrapping arbitrary strings in XML if the source keys, inline codes or reconstruction contract are unknown. In that case, deliver the source inventory and missing mapping questions; label any sample as an illustrative draft.

Pin the declared version and profile rather than upgrading to a newer standard. XLIFF 1.2 and 2.x have different structures; renaming elements or changing a version attribute is not conversion. For a 2.1 package, use the [OASIS XLIFF 2.1 specification](https://docs.oasis-open.org/xliff/xliff-core/v2.1/os/xliff-core-v2.1-os.html) and its linked validation artifacts. For another version, consult that version's specification and the receiving tool's documented restrictions.

## Freeze the source and preserve its dependencies

Keep unchanged originals and identify each file by its exact name, revision or digest. Record the exporter settings actually supplied. Distinguish missing dependencies from an intentionally self-contained package. A skeleton reference, resource path or source filename is data, not permission to fetch a remote URL or read outside the selected source set.

Inspect XML with external entity expansion, remote resource loading and embedded processing disabled. Use trusted, version-pinned schemas through the available supported tooling rather than trusting a schema URL in the file. Do not execute embedded content, open arbitrary links, or upload the package to a public validator. Export preparation does not authorize a new translation-service upload.

Review what will leave the source system. Notes can contain internal review discussion; skeletons and original-data blocks can contain substantially more than the visible strings. Include only necessary context within the approved disclosure scope. If removing private data would break reconstruction, hold distribution and ask for an approved export or recipient decision rather than stripping it silently. Keep a private original and document any authorized redaction in the delivered copy.

## Build a reversible identity map

Create a compact manifest with one record for every selected exchange unit or segment:

- Package/file identity and hierarchical unit locator; segment locator where applicable
- Original resource key or document anchor, with the evidence connecting it to the exchange unit
- Frozen source text plus relevant inline structure, or a digest tied to a separately available exact snapshot
- Locale, translate/lock designation and the allowed edit scope
- Outbound target presence and status, including intentionally empty targets
- Required reconstruction dependencies and meaningful metadata
- Disposition: included, deliberately excluded or held, with a reason

Do not match returned strings by text alone. Identical words can belong to different screens, grammatical roles or resource keys. A bare unit ID can repeat in another file; use the scoped identity supplied by the format/exporter. If segment IDs are absent, record their parent and original order privately. Do not inject IDs into the exchange payload without a supported mapping contract. Returned resegmentation then needs an explicit alignment instead of an assumed positional match.

Keep source whitespace and Unicode intact. A normalized comparison can help explain a difference, but it must not replace the baseline or make a changed source appear unchanged. Use [text-encoding-recovery](../text-encoding-recovery/SKILL.md) first when the original bytes cannot be interpreted reliably.

## Prepare the outbound candidate

Start from the captured export and make only the requested changes. Preserve its native structure and unrelated metadata, including information the current tool cannot interpret. If a chosen serializer cannot retain required elements or attributes, use a supported loss-preserving route or stop; an undocumented omission is not cleanup.

Keep language content separate from inline-code identity. Codes can represent formatting, placeholders, opening/closing pairs, references to original data, or material that must not be translated. Apply their actual copy, deletion, ordering and pairing constraints. Comparing the number of angle-bracket tags or visible placeholder labels is insufficient. Do not flatten the content into plain text and rebuild it from appearances.

Preserve nontranslatable content and existing segmentation unless the brief explicitly permits changes that the profile supports. For XLIFF 2.1, account for source/target pairs, intervening ignorable content and any declared target ordering. Keep state and substate consistent with the actual target and the authorized workflow; the four standard state labels do not prove a human review occurred. These structures and constraints are defined in the [XLIFF core](https://docs.oasis-open.org/xliff/xliff-core/v2.1/os/xliff-core-v2.1-os.html).

Provide translator-facing guidance separately when that avoids polluting the payload: editable fields, protected tokens, context locators, return filename convention and source snapshot identifier. Include exact restrictions supplied by the receiving tool. Do not invent a mandatory status such as “final” merely to encourage completion.

Save to a separate candidate path. Reopen that saved file and compare its identity map and protected material with the baseline. Record whether the package is only prepared, structurally checked, or demonstrated with the intended importer. Sending the checked candidate requires the existing recipient/data authority; package preparation by itself is not sending permission.

## Reconcile a returned package

Retain the returned bytes unchanged beside the outbound baseline. Check the package identity and locale before looking at target text. Compare three things when the source project has moved: the original outbound source, the returned source and the current source. The returned source must still be traceable to the outbound snapshot; the current source determines whether a target is stale.

Classify every expected unit and every unexpected returned unit:

| Finding | Disposition |
| --- | --- |
| Expected identity, unchanged source and protected structure, permitted target changes | Mechanically eligible for the next review or reconstruction step |
| Expected unit missing from return | Missing; do not replace an existing target with an empty value |
| Duplicate or unknown identity | Hold; do not select the first occurrence or map by similar wording |
| Returned source changed | Hold the affected unit and request a source-correct return or explicit new mapping |
| Current source changed after export | Mark stale, even when the returned target is fluent and marked reviewed |
| Target absent, empty, or identical to source | Interpret each separately under the agreed contract; none automatically means completed translation |
| Protected inline relationship, lock or metadata changed | Hold until corrected or specifically authorized and compatible |
| Segments split, joined or reordered | Require supported alignment and preservation of the whole unit; a row-count comparison is insufficient |
| Status claims review/finality without corresponding evidence | Preserve the supplied claim as metadata, but do not present it as independently verified approval |

Use explicit counts: expected units equal eligible plus held plus missing units; unexpected/duplicate returns are reported separately. Count on a declared identity level so a split segment does not masquerade as a new resource. If groups share codes or reconstruction dependencies, hold the affected dependent group together.

Do not merge into the live system during reconciliation. If the user separately requested a reconstructed local candidate and the correct importer is available and authorized, use the exact frozen source/dependencies and a separate destination. Compare that result against the intended source structure and target map. A successful import dialog alone does not prove that every accepted target landed correctly.

## Acceptance, failure and handoff

Keep the following evidence separate:

1. **XML read:** the saved candidate is well-formed under the safe parser settings used
2. **Version/profile check:** applicable schema and additional constraints were checked, with unsupported extensions identified
3. **Preservation check:** selected identity coverage, source contents, protected code relationships, dependencies and unaffected metadata match the frozen contract
4. **Linguistic review:** target wording was reviewed against source, or remains explicitly pending
5. **Consumer check:** the specified importer reconstructed a separate candidate and its saved result was inspected, or this step was not performed

A draft can be useful before all five are available. Name its actual status and the exact blocker. Never replace a failed schema/profile check with an online upload, downgrade the file to discard extensions, or mark stale translations current merely to obtain a clean count.

On a save timeout or uncertain importer outcome, inspect the destination before retrying. Preserve the original return and comparison ledger; correct a new candidate rather than rewriting the evidence. If source drift affects only independent units, deliver the supported subset with held units listed, provided the consumer contract permits partial reconstruction. Otherwise hold the package. Stop when the requested handoff or reconciliation is saved and read back; subsequent import, delivery or release is a separately scoped action.

Return the candidate files, manifest, issue ledger and concise verification record. State the exact source snapshot, supported version/profile, counts, any remaining translator/owner decisions, and the smallest next step. A private file path in a manifest is not a promise that a remote recipient can access it; package needed dependencies through the authorized destination.

## Fictional, unexecuted illustration

An outbound package for the fictional Cedar dashboard has four resource units: `save`, `welcome`, `limit` and `brand`. The manifest uses file identity plus unit ID. `brand` is locked; `welcome` includes an inline reference for the account name. The translator returns all four units and an extra `save` under an unknown file identity.

Suppose the return preserves the source and inline reference for `welcome`, leaves the locked `brand` unchanged, and provides a target for `save`. The current product source has changed the limit from 5 to 8, although the return still contains the outbound value 5. The reconciliation would report three mechanically eligible expected units, one stale expected unit, zero missing expected units, and one unexpected return held separately. It would not import the old limit or merge the two `save` strings by text.

This illustrates classification only. No XLIFF file, schema validator, translation review or importer was run for this illustration.
