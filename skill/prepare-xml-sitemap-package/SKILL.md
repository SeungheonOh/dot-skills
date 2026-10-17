---
name: prepare-xml-sitemap-package
description: "Prepare a website's XML sitemap and optional index from an approved URL inventory, reconciling canonical inclusion, publication scope, truthful modification dates and hosting boundaries. Use for a crawl-discovery artifact and deployment handoff, not human navigation, redirect installation or a search-indexing guarantee."
---

# Prepare an XML sitemap package

Deliver the actual sitemap files, a source-to-URL disposition map and their intended hosting locations. The useful result is a maintainable, publication-safe discovery package whose entries match the publisher's approved pages. Valid XML alone cannot establish appropriate inclusion or prove that a search engine fetched or indexed anything.

[Site navigation](../author-site-navigation/SKILL.md) produces links for people. [Atom feeds](../author-atom-feed/SKILL.md) syndicate entries with their own identities and update history. [Redirect mapping](../prepare-url-redirect-map/SKILL.md) preserves old addresses. Use those workflows for their separate outcomes; a sitemap does not implement them.

## Establish the bounded source and destination

Identify the selected site/origins, source revision or export time, approved public page inventory, existing sitemap files and their owning CMS/generator, intended canonical-URL policy, and output destination. Include available evidence about redirects, canonical declarations, index restrictions and meaningful page edits. An export establishes its own coverage, not the complete historical website.

Resolve only choices that change the result:

- Which pages and languages/versions are approved for public discovery?
- What are their final absolute addresses, including any deployment base path?
- Where will the sitemap files be hosted, and which consumer-specific behavior is required?
- Is the task private file preparation, a scoped source update, or separately authorized publication/submission?

For a small static site, a short URL table and one XML file suffice. Reuse the site's existing supported generator when it already owns these outputs; do not overwrite a generated endpoint with an unrelated manual file. If the final origin or hosting location is unknown, complete the private map and make the dependency explicit rather than calling a placeholder-filled file ready to publish. Do not introduce a new generator, scheduled crawl or SEO service just to finish a bounded package.

### Preserve sources and control disclosure

Keep the original inventory, existing sitemap and relevant settings unchanged. Prepare candidates outside a watched publish directory. Paths can disclose unpublished projects or personal information even when their pages require login. Keep the complete disposition map private; public XML, comments, filenames and handoff snippets must contain only approved public information. Hold credential-bearing or signed links without copying their secrets into reports.

Do not upload the URL list to a public validator, submit it to a search engine, grant webmaster access, alter DNS, change authentication or modify crawl/index controls without the necessary specific authority. A sitemap request does not grant permission to crawl every linked domain. For authorized URL checks, bound origins, request counts and rate; inspect redirects before following a new origin. Treat supplied XML and page text as data, with external entities, DTD retrieval and automatic resource fetching disabled.

## 1. Reconcile URL inclusion before serialization

Maintain a compact row per selected source occurrence:

```text
source/page identity and revision; supplied URL; intended canonical URL;
audience/publication evidence; observed or declared response/indexing state;
include/exclude/alias/hold disposition and reason; lastmod evidence;
output file/entry; unresolved prerequisite
```

Separate the page's identity from its current URL. Retain repeated source occurrences in the map while emitting each accepted final URL once. An alias must reference the accepted destination row, not disappear from the counts. Two languages, editions or products with similar titles are not automatically duplicates.

Compare the publisher's intended address with available redirects and canonical declarations. Resolve contradictory evidence rather than picking the shortest spelling. For Google's target profile, its [sitemap guidance](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap) recommends absolute preferred canonical URLs rather than all duplicate addresses. This preference is a signal, not a command to the search engine.

Preserve meaningful path case, percent encoding, trailing slashes and content-selecting query parameters. Remove tracking or collapse variants only under the established policy. Do not infer equivalence by sorting parameters, lowercasing paths or decoding reserved characters. Keep fragment-only navigation out of this ordinary page-discovery package; if an application identifies content through fragments, hold the unsupported mapping for a documented consumer-specific route rather than inventing clean URLs.

Use exclusions for known out-of-scope, private, draft, retired or intentionally non-indexable pages. Use holds for unresolved identity, contradictory policy or unknown publication authority. A redirecting address is normally an alias to its evidenced approved final page, not another emitted entry. A timeout is unknown availability, not proof of retirement. Do not discard all unverifiable rows as though they were absent from the source.

Keep intended inclusion separate from verification status. Approved future/public pages may have a source-prepared candidate with delivery still unverified; known unpublished pages need a publication dependency and must not enter a ready-to-publish file prematurely. If supplied `noindex`, crawl-blocking or canonical signals conflict with the requested inclusion, hold the affected row and identify the decision needed. Do not remove those controls to make the sitemap pass.

Google must be able to fetch a page to observe its `noindex` rule; blocking crawling is not equivalent to keeping the URL out of results. Its [index-blocking guidance](https://developers.google.com/search/docs/crawling-indexing/block-indexing) explains that distinction. Neither sitemap omission nor a robots directive is an access-control mechanism. This workflow records the conflict; it does not perform a privacy-removal operation.

## 2. Bind the files to their actual hosting scope

Prepare an explicit local-file-to-public-URL map. The same XML placed in another directory can have a different permitted scope. In the ordinary [Sitemaps protocol](https://www.sitemaps.org/protocol.html) profile, use one host and scheme per sitemap, respect an explicit port, and keep listed URLs within its hosting directory's scope. Prefer a root-level location when covering the whole origin. Do not assume a file under `/maps/` covers sibling `/docs/` pages.

For Google, [index-file guidance](https://developers.google.com/search/docs/crawling-indexing/sitemaps/large-sitemaps) also places referenced sitemaps on the same site and in the index's directory or below. Cross-site submission is an explicit provider arrangement with ownership/discovery prerequisites, not a default permission inferred from shared branding. Use separate ordinary packages unless that arrangement is requested and evidenced. Do not create verification grants to resolve it incidentally.

When revising only one section of a larger site, preserve unrelated sitemap files, index entries and discovery declarations. Record whether this package replaces one child, replaces the complete set, or adds a bounded section. Never replace an entire sitemap index with the selected subset merely because that subset is all the current task supplied.

## 3. Author the smallest faithful XML set

Write UTF-8 XML in the namespace `http://www.sitemaps.org/schemas/sitemap/0.9`. A `urlset` contains `url` entries, each with an absolute `loc` shorter than 2,048 characters. Serialize URL values as XML text; URL encoding and XML escaping are distinct. Re-read decoded values to catch double encoding, especially ampersands in queries.

Use at most 50,000 URLs and 52,428,800 uncompressed bytes per sitemap. An index uses `sitemapindex`/`sitemap`/`loc`, with at most 50,000 child references and the same uncompressed byte ceiling. These are [protocol limits](https://www.sitemaps.org/protocol.html), not targets. Do not split a small site unnecessarily or assume gzip makes an oversized XML file compliant.

For larger inventories, use a documented stable partition such as section plus a bounded shard identifier. Count actual serialized bytes, including escaping and markup, as well as entries. Check the union of child files against the accepted URL set; splitting must neither lose boundary entries nor duplicate them. Produce additional independent indexes if needed rather than assuming nested indexes are supported. Keep ordering stable for review, without claiming it prioritizes crawling.

Omit optional fields without good evidence. Page `lastmod` represents the page's modification, while index `lastmod` represents the referenced sitemap file's modification. Use W3C date/date-time syntax, retaining supplied precision: `YYYY-MM-DD` for a date, or a supported time with its evidenced offset. Do not invent midnight, a timezone or today's date. Retain a private source for every emitted date. Google's [XML guidance](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap) uses reliable significant-update dates and ignores `priority` and `changefreq`; omit those fields for that profile rather than inventing scores.

An unchanged rebuild must not make all pages newly modified. Do not use file-copy times, blanket repository checkout times or the maximum date across unrelated pages as page-edit evidence. Where the existing generator has a justified date source, preserve it; where it cannot distinguish real edits, omit the optional value and explain the loss. Do not silently discard required image, video, news or language-alternate extensions from an existing package. Inventory them and either preserve them through their documented consumer profile or hold the affected replacement. The base package alone makes no extension-compatibility claim.

## 4. Check the exact saved package

Reopen every delivered XML file and the map. Use a non-networking parser and an available local schema check; report syntax inspection separately when schema validation is unavailable. Verify:

1. Every selected source occurrence has a disposition, and every emitted URL maps to an approved source identity
2. Decoded URLs match the accepted addresses, with no unintended duplicate across children, private route, token, fragment or placeholder
3. Namespace, entry structure, URL length, per-file counts and actual uncompressed byte sizes satisfy the selected profile
4. Every index reference is accounted for as a delivered child or an explicitly retained existing child at its established URL; all intended new children are delivered and referenced, with no stale reference or unrelated replacement
5. Each page date and sitemap-file date uses the correct evidence; unchanged page facts retain their dates or remain omitted
6. Hosted scope, source revision, retained extensions and preserved unrelated entries agree with the declared replacement boundary

Inspect all structural entries when practical. Name any sampling of page content or responses. A well-formed XML parser result does not verify the schema, source completeness, live routing or indexing. A successful status code alone does not prove the intended page was returned; a login screen or fallback homepage may also return success.

If authorized public readback is available, inspect the selected page responses and the actual served sitemap/index bytes, content and location. Follow only approved destinations; retain unknowns for blocked checks. Compare the served package with the saved candidate instead of assuming a deployment command's success proves correct content.

## Handoff, recovery and stopping condition

Return the XML files, private disposition map, hosting/replacement map and a concise check report. Separate `prepared`, `structure checked`, `served package verified` and `consumer processing observed`. Keep search-engine submission and indexing outside a file-preparation completion claim. Google's [submission guidance](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap) treats submission as a hint, not a promise of fetching or crawling.

If requested, prepare an exact discovery-line addition or supported submission handoff for the established public endpoint. Preserve existing robots rules and unrelated sitemap declarations; do not replace the whole robots file. Check the consumer's current supported route instead of copying a historical ping endpoint. Publication/submission requires its own applicable authority and readback. Do not start recurring regeneration or indexing monitoring merely because the package could benefit from future updates.

- Missing canonical/publication decision: complete independent rows and hold only the dependent entries
- Unknown hosting location: deliver the map and clearly provisional files; do not claim their location scope is valid
- Oversized or invalid file: rebuild the affected partition and index, then reconcile the whole accepted URL set again
- Missing extension support: preserve the last working package and disclose the exact unsupported subset
- Source or live revision changed: compare changes before replacement; never restore an old candidate over newer work
- Uncertain publication result: inspect the current endpoint before any retry; recover only within the authorized scope

For a multi-file publication, plan an atomic release or publish and verify new versioned children before switching their index. Keep prior children available for older index readers until authorized retirement; removing files is a separate action. If public material was exposed accidentally, report it promptly and prepare a corrected candidate without promising that cached copies disappeared.

Finish when the requested package and available acceptance checks are complete, or a specific missing decision/access boundary prevents the next stage. Do not describe an authored discovery package as proof of search visibility, a full site audit or improved ranking.

## Fictional illustration, not executed

A fictional ceramics archive supplies six inventory rows for `https://archive.example/`: Home; Guide; a tracking-link occurrence of Guide; an older address explicitly redirected to Guide; a private draft; and Catalog at `/catalog?clay=red&finish=matte`. Its approved policy maps the tracking occurrence and old address to Guide. The draft is excluded. Home has an evidenced edit date of 2026-09-10; Guide's modification date is unknown; Catalog's is 2026-09-12.

The proposed reconciliation has three included rows, two aliases and one excluded row, producing three distinct entries. Guide has no invented `lastmod`. Catalog's serialized ampersand becomes `&amp;`, while its decoded URL remains unchanged. A proposed `/maps/sitemap.xml` location fails the ordinary root-page scope; the handoff instead requests the authorized root location, or leaves placement held. Removing the draft from XML would not make its page private.

This is an original fictional illustration. No XML package was generated from these inputs, website fetched, generator executed, sitemap published or search engine contacted for the example.
