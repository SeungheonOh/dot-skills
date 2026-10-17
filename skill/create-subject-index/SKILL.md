---
name: create-subject-index
description: "Create an editorial subject index for a handbook, report or book, with useful headwords, subentries, cross-references and locators tied to the delivered edition. Use for a back-of-book or linked topic index, not a full-text search engine, bibliography or table of contents."
---

# Create a reader-oriented subject index

Deliver the actual index in the requested document or reading-copy format, together with maintainable entry marks or an anchor map when continued updates are needed. The index should help readers find substantive discussions under the words they are likely to look for, including concepts whose names differ from the source's wording.

An alphabetical word-frequency list, a list of chapter titles and a taxonomy are different deliverables. Full-text search matches expressions; this workflow selects useful topics and connects them to the right passages. A classification scheme can inform terminology but cannot supply final page locators. A bibliography points to cited works, not necessarily the places a subject is explained.

## Establish the edition and reader task

Identify the selected source/revision, intended audience, index scope, requested destination/format, current pagination status and any house style. Determine whether the index is for the whole work or named sections, whether names/figures/tables/notes should be included, and whether the reader needs printed page references, clickable section links or both. Respect an established word- or letter-order convention and language; choose and disclose a consistent default when no style is supplied.

Inspect the complete in-scope source before declaring the index complete. Include captions, substantive notes and table content when relevant. Record inaccessible or unsettled portions explicitly. If layout is not final, draft the entries and anchors now but label page locators provisional. Do not promise edition-specific page numbers from a body-text extraction or an application's cached page count.

Preserve the original and work in a new candidate or the explicitly authorized version-aware editing route. An index request permits the necessary local index construction; it does not authorize rewriting the body, accepting tracked changes or uploading the manuscript to an external indexing service. Resolve competing revisions or unresolved changes that alter inclusion before assigning final locators.

### Privacy and publication boundary

An index can make sensitive subjects easier to discover and can reveal words not visible in its printed pages through hidden entry fields. Keep the index, source marks and working map under the source's approved access. Do not include restricted appendices, private reviewer comments, hidden deleted passages or unsupplied people/topic associations just to improve coverage. Hidden text is not a privacy control.

Use neutral labels that preserve the source's meaning. An index heading must not turn a hypothetical failure, allegation or proposed policy into an established fact. If a publishable edition excludes material, build its index from that edition and remove the corresponding marks from its derivative; merely hiding the printed entry is insufficient. Publication, sharing and changing the document's audience require their own authority unless already requested.

## 1. Select discussions, not every occurrence

Read in coherent sections and collect candidate concepts alongside the passage that earns the entry. The selection decision is whether a reader following that term would find useful treatment: an explanation, procedure, comparison, definition, exception or substantial example. Incidental mentions, running headers and a topic named only in the contents usually do not earn a locator.

Keep enough context to distinguish similarly named concepts. “Storage” might mean keeping physical materials or retaining computer files; do not merge them because the word matches. A discussion can earn multiple access points when readers would reasonably approach it in different ways. A repeated exact term can have no index value in one place and a useful explanation in another.

For each accepted occurrence record a compact entry map:

```text
entry/concept ID; preferred headword; optional subentry;
source revision and passage anchor or start/end anchors;
why this passage is useful; locator kind;
aliases/cross-reference target IDs; final locator after generation
```

Keep the map proportional; a small handbook may use a short table. Do not copy whole private paragraphs merely to populate a ledger. Stable IDs are useful when labels change; filenames, page numbers and current sort positions alone are weak identities.

Read neighboring passages before choosing a range. A range represents sustained treatment, not the minimum and maximum pages on which a word appears. Use separate locators for disconnected discussions. Include qualifications and exceptions in the selected passage; do not lead the reader to an isolated conclusion whose condition is elsewhere.

## 2. Build useful headwords and cross-references

Choose concise terms suited to the reader. Retain required technical terms and proper names; add a common-language access point when supported. Prefer a clear subentry over a long undifferentiated string of page numbers. Use consistent phrasing across sibling subentries, and make each useful without forcing the reader through a deep hierarchy.

Use these editorial relationships deliberately:

- **Direct entry:** A headword or subentry with real discussion locators
- **See:** An alternate term redirects to a preferred entry that exists and contains useful locators or subentries
- **See also:** An entry retains its own useful material and points to related, distinct material

Resolve cross-references by entry ID while editing and by exact displayed destination when generating. Remove dead targets, self-links, circular redirects and avoidable chains. “See also” is not a substitute for absent source coverage. A broad reference such as “See Maintenance” may be unhelpful if that entry has twenty subentries; point to the relevant subentry when the format permits it.

Apply the chosen collation to headwords and subentries, including accents, punctuation, numbers and abbreviations. Review the actual order rather than using raw code-point sorting as a language-neutral solution. Keep disambiguating qualifiers when two entries would otherwise display identically. Do not strip diacritics or rename a person merely to simplify sorting.

Check the balance against the reader's task. Selective indexing should make the work findable without listing every noun. If space is constrained, prune weak entries and improve subentries; do not omit critical topics solely because their labels are long. Ask before sacrificing a required subject or changing the agreed scope.

## 3. Attach entries to the maintainable source

Choose the route that matches the deliverable. Do not construct a parallel search application when the user asked for an index in an existing manuscript.

### Native paginated document

Use the authoring application's native index marks where available. In Word, [Microsoft's index workflow](https://support.microsoft.com/en-gb/word/create-and-update-an-index) uses References → Mark Entry, followed by Insert Index and Update Index. Mark the inspected occurrence and supply the chosen headword/subentry. Avoid Mark All unless every matching occurrence has been reviewed; word equality does not establish editorial relevance. Make corrections in the entry marks and regenerate, rather than editing generated lines that the next update will replace.

For continuous treatment, mark the actual passage range with a uniquely named bookmark and associate the index entry with it. [Word's XE documentation](https://support.microsoft.com/en-us/office/field-codes-xe-index-entry-field-abaf7c78-6e21-418d-bf8b-f8186d2e4d08) distinguishes the `\r` bookmark range from `\t` cross-reference text. Fields must be real native fields, not typed braces that merely resemble them. Preserve existing marks and bookmarks outside the requested scope.

Create a properly styled index heading and index body at the requested position. Choose readable indentation, leaders and columns appropriate to the page; use the native styles rather than spaces or hard-coded tabs as a layout hack. Native generation supplies locators only after the document has actually been laid out. An API that inserts field XML but cannot evaluate layout has prepared a marked source, not final page numbers.

### Linked digital index

For HTML, an ebook source or another supported linked format, attach stable IDs to the relevant discussions and generate links from the same entry map. Use chapter/section labels that remain meaningful without a page number. Include the document-file path when targets span files; resolve links from the delivered directory layout, not the creator's working folder.

Give each headword a target for cross-references, preserve subentry grouping and use a logical reading order. An alphabet jump list can help a long index, but the complete index must remain available without scripts, hover or a search field. Use descriptive link text so repeated “12” links are not the only context available. A readable single-column version is a useful alternative to a dense print layout.

Word [bookmarks and internal links](https://support.microsoft.com/en-us/word/add-or-delete-bookmarks-in-a-word-document-or-outlook-message) can support a linked companion, but do not assume a generated native index is clickable. Likewise, PDF export does not prove that every index locator became a link. Implement and check the requested interaction explicitly or state the limit.

## 4. Regenerate after final layout and reconcile locators

Finish the allowed layout changes, then regenerate the index using the actual authoring/layout engine. Record the source revision and final rendered edition. If inserting the index, changing its columns or updating the contents affects pagination, refresh the dependent locators and render again until the relevant pagination/locators are stable. Do not shift all locators by a guessed offset.

Check the document's displayed page labels, not merely its physical PDF page positions. Front matter or chapter numbering can differ. For a fixed PDF-only source, a separately authored index can refer to that exact edition, but it is static; disclose that a future layout change requires reindexing and do not call the source maintainable through native marks.

Do not globally refresh unrelated fields, external data or linked objects just to refresh the index. Use the narrow supported index/contents operation and inspect any dependent changes. Never accept review changes or enable macros as an incidental update step. If no layout engine can evaluate the required fields, deliver the marked draft plus the precise remaining update step, not invented locators.

## 5. Check retrieval usefulness and the saved artifact

Verify these distinct properties against the final source and reading copy:

1. **Editorial coverage:** The in-scope work was inspected; important reader questions have useful entries; inaccessible portions and deliberate exclusions are named. A count of headwords does not establish coverage
2. **Locator truth:** Every generated locator/range resolves to its intended substantive passage in the delivered edition. Range starts and ends are real; separated mentions have not become one continuous range. Check digital fragments and native marks as well as visible numbers
3. **Reference integrity:** Every See/See also target exists with the exact intended meaning, and redirects terminate usefully. Repeated labels remain distinguishable. Sorting and subentry indentation match the chosen convention
4. **Reader use:** Try concrete lookups, including a familiar synonym, an ambiguous term and a topic spanning sections. Follow the actual final links or pages and assess whether the needed explanation is there. Do not label a self-review as an independent usability study
5. **Saved presentation:** Reopen the source and final reading copy. Inspect all index pages or reflowing sections for clipping, orphaned alphabet headings, ambiguous wraps, missing glyphs and awkward column breaks. Ensure hidden index fields are not exposed in the intended reading copy and unrelated content is preserved

For a large index, keep structural checks complete where supported and report any sampled passage/interaction review honestly. A valid fragment target can still identify the wrong paragraph. If even selected important locators are unresolved, identify them as incomplete rather than presenting the whole index as ready.

## Recovery and handoff

Repair the entry map, native mark or bookmark that caused the error, regenerate and repeat affected checks. Do not repair only the visible page number. If a source edit deletes a marked range or splits a discussion, re-read the material before remapping it; the old label may no longer be valid. Keep the prior usable edition intact when a candidate fails.

Return the indexed document or index file requested, any necessary maintainable entry map, and a brief note stating edition, scope, locator type, actual checks and remaining decisions. Keep working extracts private unless included in the requested handoff. Stop when the saved index answers the agreed lookup tasks and its locators match the delivered edition, or when a required source, application or editorial decision is unavailable.

## Fictional, unexecuted example

A fictional bicycle-care handbook discusses tire puncture repair on body pages 14–16, pressure checks on page 6, and long-term storage on pages 31–32. “Flat tire” appears in a glossary and once in an anecdote. The reader-facing plan includes:

- Flat tires. See Punctures, repairing
- Punctures, repairing, 14–16
- Storage, long-term, 31–32
- Tires, pressure checks, 6; repairing punctures, 14–16

The anecdote earns no locator because it gives no repair information. The repair range is anchored to the procedure, not to the first and last occurrence of “tire” in the book. If a later layout moves the procedure, native marks would generate new locators; a linked edition would retain a stable procedure target.

Acceptance would reject a redirect to nonexistent “Tyre repair,” a range spanning unrelated pages 6–16, or a copied old page number after repagination. This is an original fictional design example; no document, field evaluation, application interaction or retrieval test has been executed.
