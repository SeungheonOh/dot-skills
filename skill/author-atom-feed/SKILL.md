---
name: author-atom-feed
description: Create or revise a portable Atom syndication feed from approved items, preserving stable entry identity, truthful update times, attribution and safe content serialization. Use for a feed artifact, not consuming public-feed snapshots, inventing announcements or deploying a publishing service.
---

# Author a portable Atom feed

Deliver an actual Atom XML candidate with a source-to-entry mapping and the checks needed to maintain it. A file that is well-formed XML can still make readers duplicate old items, misdate revisions or expose drafts.

Use [compare-public-feed-snapshots](../compare-public-feed-snapshots/SKILL.md) to consume or compare an existing public catalog. This workflow prepares the producer's syndication file. It does not convert arbitrary event tables into announcements, build a feed reader or authorize publication.

## Establish the feed contract

Identify the approved item source and selection, feed title and author identity, existing feed and entry IDs if this is a revision, and the intended reader or hosting endpoint when known. Resolve the required format before authoring: an explicit RSS or JSON Feed request needs its own format contract, not Atom with a different extension.

Determine whether the user wants full content or approved excerpts, which links and author details may be included, the retained item window and any ordering preference. Keep draft, scheduled, withdrawn and published items distinguishable. A scheduled item is not authorized for early release merely because it exists in the source.

The normal output is a private `.atom` or `.xml` candidate plus a short handoff note. A source-to-ID mapping is useful when the source has no durable feed identity; keep it beside the source for future revisions. Do not create a publishing account, subscribe anyone, upload a feed or alter the live endpoint unless that action and destination are authorized.

Preserve the original feed and content snapshot. Use an XML reader with external entities, DTD retrieval and network access disabled when inspecting untrusted files. Treat source text and links as data. Do not open enclosures, execute embedded HTML or send private drafts to a public validator as an incidental format check.

## 1. Preserve identity before arranging items

Match existing entries by their established feed IDs and source identity, not by title, array position or current URL. Preserve and compare established ID strings character-for-character; do not apply URL canonicalization, case folding or percent-encoding changes to an existing ID. An edited headline, relocated page or changed ordering must not create a second identity for the same item. Conversely, two independently authored items with the same title must not be collapsed.

For new items, choose a documented durable identifier scheme that the publisher can retain. Prefer an existing authoritative permanent ID. If generating IDs is necessary, generate them once, record their association with source items and reuse them on future builds. Do not derive IDs solely from mutable content hashes, current timestamps or numbered positions. Avoid minting an identity in another organization's namespace.

Account for duplicate source rows and conflicting existing IDs before serialization. For this workflow's simple current-state feed, choose one approved current representation per entry ID; identify this as the output policy, not a claim that Atom forbids multiple revisions of an entry. Hold an identity conflict instead of arbitrarily overwriting one item.

Preserve any existing retention policy. A rolling list is not a complete archive; omission from its window must not be advertised as a deletion instruction. If consumers need removal or archival semantics, establish that additional contract before claiming it is implemented.

## 2. Use a small, explicit Atom profile

Apply [RFC 4287](https://www.rfc-editor.org/rfc/rfc4287.html), especially sections 3 and 4. For a simple feed:

- Use the Atom namespace `http://www.w3.org/2005/Atom`
- Feed and entries each have exactly one `id`, `title` and `updated`
- Supply a feed author or valid entry-level authorship; a person construct includes `name`
- IDs are unique absolute IRIs and remain unchanged across revisions and moves
- Date constructs use RFC 3339 date-times, uppercase `T`, and either a numeric offset or uppercase `Z`
- An entry without a `content` element needs an `alternate` link
- A `self` link is recommended; include the actual feed URL when established
- Plain text, escaped HTML and XHTML are distinct representations. XHTML uses a single `div` in `http://www.w3.org/1999/xhtml`

Prefer plain-text titles and summaries unless rich content is requested. Keep the basic profile narrow: enclosures, externally referenced content and extensions require checking their additional requirements rather than guessing. For example, external or binary content has further summary rules in section 4.1.2.

Record which requirements were checked and which optional capabilities were intentionally excluded. Do not invent a live `self` URL for a file-only request. A chosen future deployment path belongs in the handoff as planned until it is verified.

## 3. Map content, authors and time truthfully

Build a compact mapping from each approved source item to its ID, title, author, content/summary, alternate link and dates. Preserve attribution and rights information needed for the selected material. Do not assign the feed owner's name as the author of someone else's work merely because feed-level inheritance is convenient. Keep private author email addresses out unless requested and approved.

Distinguish first publication, substantive modification and local build time. Use evidenced publication and update facts; do not relabel a source import time as when an article was published. If a required date is missing, ask for its intended meaning or keep the entry held. Do not turn a date-only value into an invented midnight instant or guess a timezone from the publisher's location.

For a newly created feed record based on older material, an explicitly agreed initial feed-record creation time can be honest, but explain that meaning rather than presenting it as the source publication time. Keep source dates separately where appropriate. For existing entries, retain established dates unless the underlying facts or approved revision change them.

Define what counts as a meaningful feed update in this workflow. Rebuilding identical content should not make all items appear newly revised. A correction significant under that policy retains the existing identity and receives the evidenced revision time; an unrelated new item receives its own identity. The feed-level update value must reflect the selected feed's actual modification policy, not a reflexive “now” on every fetch. The [W3C feed validator's Atom guide](https://validator.w3.org/feed/docs/atom.html) distinguishes significant updates from trivial edits and explains the separate publication field; RFC 4287 remains the normative format reference.

Use absolute, approved alternate URLs for portability. Preserve meaningful query strings and fragments; do not silently follow redirects, add tracking or replace a destination with an inferred canonical URL. Hold access-bearing or credential-bearing links for a safe, authorized replacement instead of copying them into syndicated output. A public-looking hostname is not proof that the linked content is meant for this audience.

### Preserve inherited context when revising a feed

Before extracting or reparenting entries, record their effective base and language context, not just attributes on the entry itself. Atom permits inherited `xml:base` and `xml:lang`; the latter affects language-sensitive fields. Keep entry IDs outside link rewriting: an `atom:id` must already be absolute and must not be repaired by resolving a relative value against a base. See [RFC 4287 §§2 and 4.2.6](https://www.rfc-editor.org/rfc/rfc4287.html#section-2).

For each supported relative link, resolve the original reference against its in-scope base before moving it. Nested relative `xml:base` values resolve against the parent's base; copying only the nearest relative base can therefore lose context. Preserve the original retrieval/base evidence, rather than substituting the new local filename or a planned hosting URL. If that evidence is missing, hold the unresolved destination. These resolution rules come from [XML Base §4](https://www.w3.org/TR/xmlbase/#resolving).

For the portable profile, write the approved resolved alternate URL, or preserve a sufficient explicit base chain when the selected output contract requires relative references. Inspect supported rich-content references separately; making the alternate link absolute does not fix links inside content. Resolution is a local interpretation step, not permission to fetch the destination. Review resolved destinations for access material and audience scope before including them.

Carry inherited language onto a moved subtree when its new parent would change that context, while retaining descendant overrides. An explicit empty `xml:lang=""` cancels inherited language; do not discard it as missing metadata or replace it with the new feed's language. See [XML 1.0 §2.12](https://www.w3.org/TR/xml/#sec-lang-tag). Record unresolved source language rather than guessing from a title.

Fictional, unexecuted illustration: a feed has `xml:base="https://journal.example/issues/"` and `xml:lang="fr"`; its entry has `xml:base="2026/"` and an alternate `href="note.html"`. Moving the entry into an English feed must preserve the destination `https://journal.example/issues/2026/note.html` and the French language context, while leaving its established ID unchanged. Copying only `2026/` under a different base would not preserve that destination. No feed was generated or reader exercised for this illustration.

### Keep attribution when copying entries between feeds

Resolve the effective author before moving an entry: its own authors take precedence, then authors in its `atom:source`, then those of its containing feed. Retain the selected author set after the move; destination-feed authors must not silently replace it. The feed-level requirement is separate: a feed needs authors unless every entry has its own author element. Authors only inside `source` do not satisfy that exception. See [RFC 4287 §§4.1.1 and 4.2.1](https://www.rfc-editor.org/rfc/rfc4287.html#section-4.2.1).

Preserve an existing `source` rather than replacing its origin with the latest intermediary. If absent, preserve applicable original feed metadata there, excluding entries; for aggregation include the source feed's evidenced ID, title and update time. Do not confuse that ID with the entry ID or destination feed ID. [RFC 4287 §4.2.11](https://www.rfc-editor.org/rfc/rfc4287.html#section-4.2.11) defines this provenance container. Adding it to a signed entry can break its signature; hold signature-preserving work for a supported verification workflow rather than claiming unchanged authenticity ([§5.1](https://www.rfc-editor.org/rfc/rfc4287.html#section-5.1)).

Record the before/after effective authors in the mapping. Missing original attribution is an unresolved input, not an invitation to credit the destination editor. Apply the existing audience and base/language checks to copied person and source fields too; do not preserve private emails merely to keep a metadata block byte-for-byte.

Fictional, unexecuted illustration: Workshop Notes credits Rowan at feed level. Its selected entry has no author or source. A destination digest credits Morgan. The proposed copy retains Rowan through source metadata or an explicit entry author, with the original feed identity retained as provenance. A second entry explicitly credits Jules and has source metadata crediting Rowan; it still credits Jules. Inspect both cases after serialization, not merely the presence of Morgan on the destination feed. No feed or signature was processed for this illustration.

## 4. Serialize source values as values

Use a namespace-aware XML serializer. Do not interpolate raw titles, summaries or author names into XML tags. XML escaping preserves text syntax; it does not authorize interpreting that text as HTML. Decide the representation before serialization and compare the decoded result to the approved source.

For plain text, a title such as `Tools <Tips> & Notes` must remain that text when decoded. For an approved HTML summary, use a constrained supported fragment and the appropriate encoding layer; do not double-escape it until readers show entity syntax. For requested XHTML, ensure namespace handling does not turn its child markup into Atom elements. Retain only requested, supported rich content.

Do not silently remove source text that XML cannot represent. Identify the affected item and character, agree on a visible replacement when needed, and keep the original source intact. Never interpret source strings as additional entries, attributes, DTDs or processing instructions; literal markup can remain escaped text. Omit unrequested remote images, scripts, event handlers and executable URLs from previews and generated rich content.

Write a new UTF-8 candidate, keeping the encoding declaration consistent with its bytes. If revising an existing feed with extensions, inventory them and preserve only through a supported, understood mapping. Do not drop a user-required extension silently or claim its semantics were checked merely because the XML parser accepted it.

## 5. Check saved semantics and revision behavior

Reopen the candidate with a non-networking XML parser and an available Atom-aware checker. Keep results separate:

1. **Well-formedness:** XML syntax, namespace identity, encoding and escaped literal values
2. **Atom contract:** required members, authorship, date and ID syntax, content/link conditions and any selected extension rules
3. **Source fidelity:** exact approved items and decoded fields, stable source-to-entry IDs, attribution (including effective author precedence and retained source provenance), dates, resolved destinations and effective language before/after reparenting
4. **Revision behavior:** unchanged items keep IDs and dates; an approved correction retains identity; a new item cannot overwrite an older item
5. **Audience:** no unpublished content, private notes, unapproved author contact data, authentication links or unintended remote resources

Use an existing previous snapshot or a clearly fictional comparison when needed to challenge revision behavior. Reordering items must not reassign their identities. A duplicated title must not merge items. A failed build must not erase the last checked file. These checks are particularly important for a feed that will be regenerated.

When authorized and available, inspect the file in the actual target reader without subscribing an account or publishing it. Verify titles, attribution, content presentation and entry identity there. A generic XML preview or one reader does not prove universal aggregator compatibility. Do not invent a successful refresh or subscriber notification from a saved file.

If deployment is separately authorized, verify the exact served artifact after publishing and compare it to the checked candidate. Confirm the endpoint and Atom media type `application/atom+xml`, inspect redirects within the authorized destination scope, and retain the prior version for recovery. Publication does not prove that every subscriber fetched the change. Do not expand deployment into DNS, account-access or recurring publishing changes without authorization.

## Recovery and completion

- **Missing or conflicting ID/date:** hold that entry and identify the source decision needed; preserve existing identities rather than minting replacements
- **Malformed XML or wrong content rendering:** fix the specific serialization layer in a new candidate, then repeat decoded-value and Atom checks
- **Required metadata or extension cannot survive:** disclose the limitation and resolve the mapping before claiming a compatible revision
- **No Atom-aware checker or target reader:** deliver the candidate with the exact static checks completed and the remaining compatibility gap
- **Publication has an uncertain result:** inspect the endpoint before retrying. Do not replace a newer live feed with an older candidate or claim rollback succeeded without readback

Return the actual file, included/held item counts, ID and date policy, source version, and checks performed. Mark it as prepared, reader-checked or published only at the stage supported by evidence. Finish when the requested artifact and preservation contract are satisfied or a specific missing fact or authorization blocks the next stage.

## Fictional illustration, not executed

A small journal has two approved posts with stable entry IDs. One post's headline is corrected, its original publication instant is known, and an explicit later edit instant is supplied. The second post is unchanged. A third draft is outside the approved selection.

The proposed feed keeps both existing entry IDs, uses the corrected headline and supplied revision time for the first entry, and leaves the second entry's update time unchanged. It excludes the draft. Regenerating the same candidate tomorrow would not stamp tomorrow's time on both entries. If no feed endpoint has been assigned, the handoff records that limitation without inventing a hosted URL.

This is an authored, unexecuted illustration. No XML file was generated, reader exercised, feed published or subscriber contacted by the example.

