---
name: create-feed-subscription-outline
description: Prepare an OPML feed-subscription file from selected lists or exports, preserving folder occurrences, exact endpoints and unsupported metadata in a sidecar. Use for a reader-side subscription handoff, not article archiving, feed publication or automatic account import.
---

# Prepare a portable feed-subscription outline

Create a real `.opml` candidate and a compact preservation report. The useful result is a list another reader can attempt to import, with every selected subscription accounted for and any loss stated before import.

This is the reader's subscription collection. [author-atom-feed](../author-atom-feed/SKILL.md) creates a publisher's feed; [compare-public-feed-snapshots](../compare-public-feed-snapshots/SKILL.md) compares feed contents. Browser bookmarks and individual saved articles are different objects. A subscription file does not preserve downloaded articles, reading progress or an account's complete state.

## Input and output contract

Use the supplied OPML/export or selected source rows, requested folders, target reader/version when known, required metadata and approved private output location. Clarify only missing choices that affect selection, required fidelity or the destination. For a file-only task, an unknown target account does not block preparation; reader compatibility stays untested.

Return:

- A UTF-8 OPML candidate containing the representable approved subset, or a clear explanation when no valid candidate can be produced
- A source-to-output map and small exception list, combined in one sidecar if convenient
- Counts of folder occurrences, subscription occurrences and distinct exact endpoint strings, plus preservation and untested-import limits

Preserve original files. Read XML as data with DTDs, external entities, network retrieval and include expansion disabled. Set bounded size/depth limits for the supplied collection rather than recursively downloading referenced outlines. Do not fetch feeds, load icons, subscribe an account or send the file to an online validator as an incidental check.

Subscription names and endpoints can disclose private interests or internal systems. Keep owner emails, private notes and account identifiers out of the candidate unless specifically requested for its audience; preserve private non-secret metadata only in the approved private view. Screen labels, `xmlUrl`, `htmlUrl`, all original attributes and unknown extensions for authentication material. Hold credential-bearing, signed access, reset or invitation links and other secret-bearing values. This exclusion applies to every derived artifact, including inventory, sidecar, preview and exception report: retain only a safe source locator and reason, never the secret-bearing value. Leave the untouched original private. Ordinary non-secret query parameters are not grounds for stripping or rewriting an endpoint.

## 1. Inventory the selected tree

Record source file/version and capture time separately from feed publication dates. Assign each selected folder and subscription occurrence a stable local locator using native IDs when available or a documented parent-plus-ordinal path. A title or URL alone cannot distinguish repeated placements.

Retain the following fields, subject to the secret exclusions above:

```text
source locator; parent locator; sibling order; node kind;
display label; exact feed endpoint; supplied website URL;
original attributes; disposition; output locator; preservation notes
```

Keep identical feeds placed in different folders and repeated folder names distinct. Do not deduplicate, sort or flatten unless requested. When the user requests deduplication, establish whether it means identical occurrences within one folder or one subscription across the entire tree; record each removed occurrence's surviving target. Similar names, HTTP/HTTPS variants, redirects and tracking variants are not established identity matches.

Classify unsupported outline types, include/link nodes, XML comments and extension fields explicitly. OPML's `isComment="true"` is a separate semantic status: under the specification's convention, it comments the node and its descendants. Carry that inherited status even when the commented ancestor lies above the selected subtree; a child without the attribute is not evidence that it is active. Hold commented subscription occurrences unless the target documents a faithful inactive representation or the user explicitly chooses to include them as active. Never move the status into a sidecar while silently emitting active descendants. An ambiguous comment value remains unresolved.

Do not silently convert a website URL into a feed endpoint or expand an included remote collection. An endpoint-shaped string with no evidence that it identifies a feed remains a candidate, not a confirmed subscription.

Compare the selected source tree with export coverage only when independent source evidence is available. An export's own counts establish its internal contents, not completeness of the live account. For example, [Feedly's export documentation](https://docs.feedly.com/article/52-how-can-i-export-my-sources-and-feeds-through-opml) excludes Boards, Read Later articles and some feed types; do not describe that OPML as an account backup.

## 2. Select a conservative interchange profile

Use the [OPML 2.0 specification](https://opml.org/spec2.opml) for the format and the intended reader's official documentation for accepted subscription conventions. Keep the core format profile small:

- An `opml` root has version `2.0`, a `head` and a `body`; core elements have no XML namespace
- The body contains at least one outline. Each outline has a `text` attribute, and nesting represents the tree
- RSS subscription outlines use `type="rss"`, `text` and `xmlUrl`; `htmlUrl` identifies the associated website when supplied
- Optional metadata must have a supported mapping; preserve unknown extensions separately rather than inventing their meaning

Do not infer that an Atom endpoint requires an invented `type="atom"`; use the target's documented subscription representation. Do not invent a feed format/version attribute from the filename. If no subscriptions remain after holds, provide the inventory and exceptions instead of labeling an empty unsupported document import-ready.

Preserve source labels separately from publisher titles. A user-renamed subscription can legitimately differ from the feed's title. Do not fetch and replace names to make the export appear current. Preserve empty labels when the source permits them; if the target requires a nonempty label, mark any proposed fallback for review.

Record a field-level map: directly represented, kept only in sidecar, deliberately excluded, or unresolved. Reading state, saved items, tags, filters, rules and folder order may have reader-specific behavior; their presence in an export does not prove the target preserves them. A required loss blocks a fidelity claim even when all endpoints fit.

## 3. Serialize without changing destinations

Use an XML serializer instead of concatenating attributes. Escape XML syntax and verify the decoded values against source strings. Preserve meaningful query strings, fragments, percent escapes and case; do not resolve redirects or replace URLs with guessed canonical versions.

Build folder outlines from occurrence IDs so two same-named sibling folders cannot merge accidentally. Preserve empty selected folders where the format permits them, while marking target retention untested. Keep foreign outline types out of a subscription-only candidate unless the target's documented contract supports them.

Use an explicit endpoint policy for the target, normally absolute HTTP(S) feed addresses. Hold malformed, relative, local-file, executable and unsupported endpoints without activating them. A private network address needs a destination-specific decision before disclosure; a syntactically valid public URL is still not proof of reachability or safe content.

Produce new output files outside originals and application import/watch locations. A sanitized subset must state its exclusions. Do not add account-owner fields or build-time timestamps merely to fill optional metadata. If timestamps are needed, use their specified meaning and format instead of relabeling feed dates as export dates.

## 4. Reopen and reconcile the saved artifacts

Parse the saved candidate with the same non-networking precautions, then compare its decoded tree to the approved output plan:

1. Each included source subscription occurrence maps to exactly one output occurrence; each held or intentionally merged occurrence has a reason
2. Parent relationships, sibling order, repeated placements and labels match the planned tree
3. Endpoints and supported metadata match exactly after XML decoding, including ampersands and Unicode
4. The sidecar accounts for required fields the interchange file cannot carry; inherited commented/inactive subscriptions have not become active through omission of their status
5. No credential, owner detail, private note or unapproved extension leaked through attributes or comments

Check selected occurrences = included occurrences + held occurrences + explicitly merged occurrences. Count distinct endpoint strings separately; that smaller count does not show that duplicates were lost. If folder representation differs intentionally, list the exact relocation or flattening rule.

When a target reader is available under separate import authorization, record its documented import behavior before use. [Feedly's import guide](https://docs.feedly.com/article/51-how-to-import-opml-into-feedly) describes additive import and distinguishes subscriptions from saved articles; do not generalize that behavior to other readers. Importing may fetch feeds and sync subscriptions. File preparation alone grants neither action.

An actual import needs a bounded target identity, preservation of existing subscriptions and target readback. Compare the reader's resulting folders and endpoints with the plan, including any deduplication or flattening. Never retry an uncertain additive import without inspecting current state. If only the file was checked, say `prepared and statically checked; not imported`.

## Failure handling and completion

- **Malformed XML or ambiguous encoding:** hold the affected input; retain original bytes and request a supported re-export rather than repairing silently
- **Unknown extension or required state loss:** deliver the clear subset and exact mapping decision; do not call it a full migration
- **Missing target documentation:** deliver the standards-based candidate, with compatibility unverified
- **Endpoint contains access material:** hold it and request a safe destination-specific replacement; never expose it in a public checker
- **Readback differs from the plan:** correct a new candidate and repeat semantic checks; leave the prior checked file intact

Stop when the requested file and accounting are delivered, or a specific missing fact prevents them. Do not treat this result as authorization to unsubscribe from the source, cancel an account or remove originals.

## Fictional example, not executed

An invented export contains `Design/Workshop` and `Weekend/Workshop`, both pointing to `https://journal.example/feed.xml`, plus a third subscription whose endpoint is marked access-bearing. The first two placements are intentional.

The proposed candidate keeps two occurrences under their original folders. Its report would say three selected subscriptions, two included, one held, and one distinct included endpoint. A private reading-status field stays in the sidecar; it is not advertised as imported reader state. The held row is identified only by its source locator.

This is an authored illustration. No OPML file was generated, endpoint fetched, reader imported into or account modified for the example.
