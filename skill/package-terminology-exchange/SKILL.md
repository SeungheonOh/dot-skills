---
name: package-terminology-exchange
description: "Turn authorized terminology sources into a concept-based, locale-scoped exchange package with stable term identities, status provenance and an explicit TBX or recipient-field mapping. Use for termbase handoff and loss review, not sentence translation or automatic terminology approval."
---

# Package a terminology exchange

Create a portable termbase candidate and a human-reviewable record of what its concepts, terms and usage decisions mean. The important transformation is from scattered rows or existing termbase records to an exchange that preserves distinctions: the same spelling can name different concepts, and one concept can have several terms in one locale.

Use [translation-release-review](../translation-release-review/SKILL.md) to apply an established glossary while translating a document. This workflow prepares the glossary itself for transfer, including unresolved equivalence, status and field-mapping decisions. It does not establish new official vocabulary, rewrite product copy or authorize importing into a shared termbase.

## Inputs and deliverables

Start with the authorized glossary files/exports and their revisions, the relevant domain/product, requested language or locale scope, source authority for usage decisions, and the receiving tool's documented import format. Existing stable concept and term IDs matter; preserve them. A spreadsheet containing `English` and `French` columns is not enough to establish regional scope or approval.

Clarify only consequential gaps. If no receiver is known, produce a neutral review package with explicit fields and unresolved mappings; do not call it universally importable TBX. If the request is comparison-only, return the mapping/loss ledger without writing a new target termbase. If the recipient needs a particular legacy format, honor it rather than silently modernizing.

Return, proportionately to the source size:

- A candidate exchange file in the agreed format, or a clearly labeled review dataset when serialization is blocked
- A concept/term register preserving stable IDs, locale scope, source locators and approval evidence
- A field mapping with source level, destination level, transformations and losses
- An exception ledger and a saved-file verification summary

Keep the original export unchanged. Record the baseline's byte digest or immutable revision and treat source instructions, URLs and embedded formulas as data. A read or local packaging request does not authorize uploading internal terminology, confidential product plans or source excerpts to a new terminology service.

## Establish concepts before pairing translations

Inventory every selected source row or record, including excluded and held entries. Give new provisional IDs only where the source has no usable identity, and retain the source-row-to-ID map. These IDs are local handoff identities, not evidence of an authoritative termbase record.

Separate three levels:

1. **Concept:** the meaning in its domain, definition or distinguishing context, existing concept ID and related concepts when evidenced
2. **Language/locale:** the language section and any documented regional or product scope
3. **Term:** the exact expression, stable term ID, grammatical/context fields, usage status and its supporting source

This mirrors the concept, language and term organization described by the [TBX elements reference](https://www.tbxinfo.net/developer-resources/tbx-elements-reference/). Preserve the supplied level rather than putting all metadata on every synonym.

Do not merge on normalized spelling alone. “Port” as a hardware connector and “port” as a network endpoint need distinct meanings even in the same product. Conversely, an acronym and full form may be terms of the same concept when the source says so. Row adjacency, an identical definition copied across files, or a machine-suggested translation is only a lead.

For a table with several language columns, establish whether each row is one concept, one term pair, or a flattened multi-term record. A cell containing slashes or semicolons may be one valid term rather than several synonyms. Preserve it intact until the source convention supports splitting. Avoid a Cartesian product that pairs every synonym in one language with every term in another as independently approved translations.

Use definition, subject field, context and source lineage to propose alignments. Mark uncertain cross-language equivalence as unresolved and leave it out of the approved exchange subset. Do not fabricate a target-language term to fill a blank cell. Record whether a missing value means unknown, intentionally absent or not applicable; the file format may not preserve that distinction without a sidecar.

## Carry usage decisions with their authority

Record status on the term and scope to which it actually applies. A term preferred in one locale, product generation or customer glossary is not automatically preferred everywhere. Keep “preferred,” “allowed,” “deprecated,” “do not translate,” “case sensitive,” and “pending review” as separate concepts unless the receiver explicitly defines an equivalent mapping.

For each consequential designation, retain the exact source locator, authority and effective scope if supplied. A frequency count or a recent email mention is not an approval decision. A reviewer comment is proposed until accepted. Do not resolve conflicting owners by seniority, majority spelling or the newest file timestamp without an applicable precedence rule.

Where the sources disagree, preserve both assertions in the review record and hold the affected status or term. State a narrow question, such as which product scope a preferred term governs. Do not downgrade “forbidden” to “deprecated” or “unreviewed” to “admitted” merely because the receiver offers fewer choices. Propose the mapping and document its consequence.

Preserve exact spelling, case, accents and punctuation, including nonbreaking spaces where meaningful. Store an optional normalized search key separately. Do not remove diacritics or conflate script variants to increase apparent deduplication. Keep permitted inflection, grammatical gender and part of speech as supplied; an exact protected product name and an ordinary term allowed to inflect need different instructions.

Context excerpts should be just long enough to disambiguate usage. Check that examples, customer subsets, reviewer names, source links and references may be included for the intended receiver. Retain necessary private provenance locally when the exported package must omit it, and make the resulting evidence limitation explicit. Do not attach the full source document merely because one term came from it.

## Choose and map the exchange profile

For TBX, identify the receiver's supported generation, dialect, style and schema revision. TBX 2008-era and 2019-era documents are not the same structure. Within modern TBX, DCA and DCT represent data categories differently; a style conversion is more than replacing a header label. Consult the maintained [TBX dialect documentation](https://www.tbxinfo.net/tbx-dialects/) and [DCA/DCT explanation](https://www.tbxinfo.net/dca-v-dct/) for the exact profile in scope.

Build a field-by-field mapping before serializing:

| Source field | Mapping question |
| --- | --- |
| Concept ID, definition, subject field | Is the identity preserved and is the destination category valid at this level? |
| Language/region | Does the receiver preserve the exact locale or collapse it to a broader language? |
| Term ID and text | Does the receiver retain multiple independent terms in one language section? |
| Status and scope | Is the meaning equivalent, and can its effective scope be represented? |
| Grammar, context and source | Are these supported categories at the required level, with allowed values? |
| Internal note, custom field or relation | Is it preserved natively, intentionally omitted, or retained in a sidecar with an explicit import loss? |

Use the selected dialect's actual categories and allowed values. For example, the maintained [TBX-Basic category listing](https://www.tbxinfo.net/ns/dct/basic) distinguishes administrative term status and defines the levels on which categories belong. A free-form column named `status` cannot be copied directly into a restricted value field without a meaning-preserving mapping.

Do not claim that a note sidecar fixes receiver behavior. If the receiving tool ignores a prohibition or regional distinction, the termbase it imports will still lack that behavior. Hold the affected entries or obtain an explicit loss decision. Do not invent a private TBX dialect for an ordinary handoff when the recipient cannot use it.

For a recipient-specific delimited table, specify encoding, delimiter, quoting, headers, required field order, multi-value representation and empty-value semantics. Keep IDs and locale tags as text. If a spreadsheet review copy is needed, prevent formula-like values from being evaluated through a safe text import or supported cell type; any review-only escaping must not change the canonical term text delivered to the importer. A CSV opened and resaved by an office app can alter values and is a new candidate to verify.

## Serialize and inspect the saved candidate

Write to a separate authorized path. Keep a record of any renumbering the receiving format forces so the source relationship remains reversible. Preserve unknown fields in the unchanged source and loss ledger; do not discard them from the evidence just because the export format cannot carry them.

For XML, use a safe parser without external entity expansion or automatic remote fetches. Select trusted schema material for the exact dialect/style rather than following arbitrary processing instructions in an input file. The [TBX validation guide](https://www.tbxinfo.net/validating-a-tbx-file/) distinguishes structural schemas and additional constraints; an XML parse alone is not dialect validation. Use available permitted tooling and state any checks that cannot be performed. Do not upload the termbase to an online validator without data/recipient approval.

Reopen the saved artifact and compare its semantic records against the reviewed register:

- Every in-scope source record is represented, deliberately excluded or held, with no unexplained loss
- Concept and term identities remain distinct; joins and splits have explicit source mappings
- Exact term strings, locale tags, multiple-term relationships and required statuses survived
- Definitions, contexts and provenance remain on the right concept/language/term level
- Unsupported fields and decisions remain visible, and private material excluded from delivery is absent
- Counts are declared separately for source rows, concepts, language sections and terms; they are not assumed equal

If an authorized disposable import preview is available, inspect how the receiver actually represents homographs, synonyms, locale tags, prohibited terms and empty fields, and re-export that preview when supported. Compare semantics, not serializer whitespace. Do not overwrite a shared termbase for this check. If no preview was performed, report “exchange file checked; recipient import unverified.”

## Recovery and completion

If a receiver rejects a category, identify the exact field/profile mismatch before changing it. Do not delete all unsupported fields or choose a different locale to obtain a passing import. Correct a new candidate, update the mapping/loss ledger and repeat affected saved-file checks.

If the source changed during preparation, compare changed records against the frozen register. Revalidate affected concept joins, status assertions and exports. Preserve unchanged work, but do not label the entire package current until its source relationship is restored. On an uncertain save or import response, inspect the destination before retrying; duplicate concepts from a repeated import are not harmless.

Stop with the requested verified candidate and unresolved decisions. State whether terminology approval, schema/profile validation and recipient import were actually completed. Updating a shared termbase, publishing the glossary, approving proposed terms and sending it to a new vendor remain separately authorized actions.

## Fictional, unexecuted illustration

A fictional device glossary has three source rows. Row A defines `port` specifically as this device's USB-C connector and supplies one English term and one French term. Row B defines `port` as a network endpoint with a different concept ID and its own two terms. Row C gives `USB-C port` as an additional English term for A's concept, marked preferred for one product generation only.

The proposed register has two concepts, four language sections and five terms, with all three source rows mapped. It retains the two English `port` entries under their different concepts. If the recipient can keep only one preferred English term without product scope, Row C's scoped preference becomes a held mapping decision; it does not silently replace the broader term.

The illustration describes an expected handoff, not an observed import. No TBX serializer, schema check, terminology approval or receiving application was executed here.
