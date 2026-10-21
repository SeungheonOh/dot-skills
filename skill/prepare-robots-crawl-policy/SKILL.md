---
name: prepare-robots-crawl-policy
description: "Prepare a robots.txt candidate and an explained before/after crawl-decision map for a bounded website policy change. Use for crawler-specific path rules and deployment handoff, not access control, search-result removal or a sitemap alone."
---

# Prepare a robots.txt crawl-policy change

Deliver the candidate file and a compact decision map showing which selected URLs become crawlable or blocked for which crawler. A plausible directive list is insufficient: the effective group and winning rule must implement the publisher's actual intent without changing unrelated paths.

[Sitemap preparation](../prepare-xml-sitemap-package/SKILL.md) prepares discovery URLs. [Redirect mapping](../prepare-url-redirect-map/SKILL.md) preserves moved addresses. This workflow instead owns voluntary crawler access instructions. It does not authenticate visitors, remove content, enforce a firewall or guarantee indexing outcomes.

## Establish intent, origin and ownership

Identify the exact origin or separately selected origins, current robots source and revision, responsible CMS/generator, target crawler product tokens, requested path policy and output destination. Determine whether the request is file preparation or also an authorized source change/publication. Preserve the existing file, including unrelated rules and sitemap declarations; do not overwrite a generated endpoint with a competing manual file.

Ask only for unresolved decisions that change behavior. “Hide these pages” needs clarification between crawl avoidance, search-index exclusion and confidentiality. For Google, a crawl block can prevent discovery of a page's `noindex` directive; `noindex` in robots.txt itself is unsupported. See [Google's indexing-control guidance](https://developers.google.com/search/docs/crawling-indexing/block-indexing). Do not remove a crawl block or add indexing controls incidentally to resolve that conflict.

Keep private inventories and rationale separate from the public candidate. Robots rules publicly reveal named paths and are not a security boundary, as [RFC 9309 section 3](https://www.rfc-editor.org/rfc/rfc9309.html#section-3) explains. Do not put private project names, secret-bearing URLs or internal comments in a publishable file. If the requested rule itself discloses confidential information, hold it for an appropriate access-control decision rather than claiming robots protection.

## 1. Define intended decisions before writing patterns

Use a short table or equivalent notes:

```text
origin; crawler; selected URL/path; intended allow/disallow;
policy evidence; current result and deciding group/rule;
candidate result and deciding group/rule; change/unchanged/hold
```

Include representative public pages, the affected paths, required rendering resources when known, and nearby routes that must remain unchanged. Preserve case, trailing slash, query and encoding distinctions until the chosen matcher establishes their meaning. An inventory is a bounded source, not evidence that every route is covered.

Distinguish a directory prefix from a single endpoint. Include the bare directory name, a child, a similarly named sibling and relevant query variants. Choose exact end-anchored rules when the policy truly concerns one spelling; do not generalize a handful of examples into a whole-site wildcard. Keep unknown future routes as an explicit pattern consequence, not an exhaustive tested population.

## 2. Resolve effective groups and matching

Choose the consumer profile and an available compatible local parser before claiming executable validation. A generic parser's successful load does not establish the target crawler's group selection. Do not build an ad hoc substring matcher and label it standards-compliant.

Under [RFC 9309 sections 2.2–2.3](https://www.rfc-editor.org/rfc/rfc9309.html#section-2.2), prepare UTF-8 text for root `/robots.txt`, served as `text/plain`. Matching starts at the path's beginning; the most specific match wins, not the last line. Preserve the protocol's percent-encoding comparisons. `*` matches zero or more characters, `$` anchors the end, and `#` starts a comment. These are not general regular expressions. Unmatched paths are allowed. Equivalent allow/disallow rules favor allow. Empty rules do not mean a whole-site block.

For [Google's documented profile](https://developers.google.com/crawling/docs/robots-txt/robots-txt-spec), origin scope includes scheme, host and port. The most specific matching user-agent group is selected; equally applicable specific groups combine, but the wildcard group is not inherited. Group order is irrelevant. Adding a crawler-specific exception can therefore remove that crawler's previous wildcard restrictions. Preserve required restrictions explicitly in its effective group rather than assuming inheritance. Google uses case-sensitive path matching and the least restrictive rule for equal-specificity conflicts. Keep the file below its 500 KiB parsing ceiling; unsupported fields such as `crawl-delay` do not implement the requested behavior.

Treat blank lines and comments as presentation, not a reliable way to force a new group. Check the parser's actual grouping after every edit; an ignored extension line must not be used as a group delimiter. Retain supported sitemap declarations as discovery metadata, not path permissions. If existing crawler-specific extensions matter, consult that consumer's documentation and preserve or hold them rather than silently discarding them.

### Keep URI comparison separate from blanket decoding

Use [RFC 9309 §§2.2.2–2.2.3](https://www.rfc-editor.org/rfc/rfc9309.html#section-2.2.2) when explaining encoded paths. Decode percent-encoded ASCII unreserved octets for comparison, but do not decode reserved octets indiscriminately: `%2F` must not become a structural slash. Non-ASCII characters need their UTF-8 percent-encoded comparison form. Compare octets, not displayed-character counts, for specificity.

Literal robots metacharacters need percent encoding in patterns: `%2A` for a literal asterisk and `%24` for a literal dollar sign. Shell quoting or a backslash is not an equivalent robots escape. Preserve source spelling alongside the comparison explanation.

**Fictional, unexecuted boundary cases:** consider each rule alone in the applicable user-agent group. For `Disallow: /notes/~draft$`, `/notes/%7Edraft` matches. For `Disallow: /notes/a/b$`, `/notes/a%2Fb` does not. For `Disallow: /notes/item%2A.txt$`, the literal-star item is blocked but `/notes/item7.txt` is not. These are authored expectations, not parser observations.

## 3. Compare the saved candidate against intent

Save outside a watched publishing directory. Reopen the exact bytes, inspect the decoded rules and group boundaries, and compare every selected decision before and after. For each changed result, identify the responsible rule or group-selection change. Confirm unchanged public routes and unrelated crawler policies remain intact.

When a compatible offline parser is available and its use authorized, evaluate the bounded decision set against both files. Record its identity/version and any unsupported syntax. Include encoded/unencoded boundary pairs and literal metacharacters when present; hold unexplained matcher disagreements rather than rewriting expected decisions. Include the meaningful boundaries from step 1 and cases where a specific agent overrides the fallback. If only source inspection is possible, say so; do not claim a parser run, live crawler test or complete rule-space proof.

Check the candidate for accidental `Disallow: /`, unapproved widening, misplaced rules, unresolved placeholders and private comments. Separate the intended policy from the parser's output: if they disagree, repair the candidate or hold the conflicting request. Do not revise the expected decisions just to match what the file happens to do.

## Handoff and optional authorized publication

Return the candidate, concise before/after decisions, exact origin and owning source to update, preserved settings, unresolved choices and actual checks. A preparation request ends here. It does not authorize changing CMS visibility, authentication, DNS, firewall rules or webmaster access, submitting private URL lists to online testers, or launching a crawl.

For a separately authorized publication, compare the current source revision before replacement and use its established narrow deployment route. Read back the exact public endpoint's status, media type and body, not just a deployment success message. A login page or HTML fallback is not the intended file. Keep request scope bounded; stop at unexpected destinations rather than forwarding credentials.

Google's [status and caching rules](https://developers.google.com/crawling/docs/robots-txt/robots-txt-spec#handling-of-errors-and-http-status-codes) distinguish `429` and server/network failures from ordinary `4xx` results. Do not infer successful policy installation from an unsuccessful fetch. Caches can delay effective changes. Report served-file verification separately from crawler adoption, and do not promise immediate recovery after rollback.

If publication is uncertain, inspect the current endpoint and source before retrying. If newer edits conflict, preserve them and hold the replacement. Correct or roll back only the authorized scope, then read back again. Finish at the requested stage or report the precise missing decision/access; do not start ongoing indexing monitoring as incidental follow-up.

## Fictional illustration, not executed

A publisher asks to discourage crawling under `/drafts/` for fallback crawlers and Googlebot, except the approved `/drafts/guide.html` page for Googlebot. The existing file has only a wildcard group blocking `/drafts/`. A proposed candidate is:

```text
User-agent: *
Disallow: /drafts/

User-agent: Googlebot
Disallow: /drafts/
Allow: /drafts/guide.html$
```

The authored decision map expects `/drafts/item.html` to remain blocked for both profiles, the guide to become allowed only for Googlebot, and `/draftsmanship/` to remain allowed. Under the selected Google profile, `/drafts/guide.html?print=1` remains blocked: the exact exception does not cover that variant. The bare `/drafts` also lies outside the slash-terminated prefix and needs an explicit policy decision if it is a real route.

Adding only the Googlebot `Allow` line would not inherit the wildcard block and would fail the intended restriction. The example exposes that group-selection failure rather than implying a site-wide crawl test. No file was deployed, parser executed, URL fetched or crawler behavior observed for this illustration.
