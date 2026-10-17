---
name: prepare-link-share-metadata
description: Prepare page-specific link-sharing metadata, an approved preview-image mapping and integration-ready head fragments for existing web pages. Reconcile duplicate tags and page identity, and distinguish source checks from a platform's actual cached preview.
---

# Prepare truthful link-sharing metadata

Deliver the actual metadata candidate for the selected pages, with the approved title, summary, identity URL and image associated with each page. A generic attractive card or a list of recommended tags is insufficient. The useful outcome is a maintainable page-to-metadata mapping and a concrete insertion/replacement artifact that does not misrepresent the page or expose private material.

Use this for ordinary page previews when links are shared. [Atom feed authoring](../author-atom-feed/SKILL.md) prepares syndication entries with feed identity and update semantics. [Visual asset creation](../create-visual-asset/SKILL.md) creates the artwork itself. This workflow coordinates existing page content and preview assets; it does not publish social posts, build a full website, implement authenticated unfurl integrations or promise traffic, ranking or engagement improvements.

## Establish the page and audience contract

Identify the exact page set and revisions, final intended URLs, current metadata/template ownership, approved public content, selected social/chat consumers, existing image assets and output destination. Distinguish a generic Open Graph candidate from a request for verified rendering in named platforms. If no consumer is named, prepare the interoperable base and state that platform-specific presentation is untested.

Resolve whether the work is file-only preparation, editing a supplied source, authorized publication, or a requested platform check. Inspect current primary documentation for any consumer-specific extension, supported image format, byte/dimension limits or refresh mechanism. Do not treat an old documentation link, search snippet or online preview generator as a current universal standard. If the official requirement cannot be established, keep that extension provisional and continue the base work.

Record a concise per-page input row:

```text
page ID and revision; intended URL and audience; page title/summary evidence;
language; existing tag/template sources; selected image identity and rights;
permitted transformations; target consumers; requested completion stage
```

### Privacy and external-fetch boundary

Preview metadata is part of the published response even when it is absent from the visible body. A private title, customer name, embargoed screenshot or confidential image can leak through a link preview. Use only information approved for the intended audience. Exclude secrets, signed URLs and private source-system locators from metadata and recipient-facing manifests.

A crawler may fetch and cache a page and its image when a URL is submitted to a validator, composer or chat service. Such a submission is an external disclosure, not a purely local check. Obtain any missing authority for the actual URL/content and recipient service. Do not publish a test post, message a channel, upload an image, open link access or disable authentication merely to make a preview appear. `noindex`, an obscure path and a hidden tag are not access controls.

For restricted pages, establish an explicitly approved public-safe preview or leave the rich-preview goal unresolved. An authenticated browser opening the page does not prove that an unauthenticated crawler can or should read it. Do not move a private image onto a public CDN as an incidental repair.

## 1. Reconcile page identity and metadata ownership

Inspect the existing document head or provided source output, including tags emitted by the layout, CMS, plugin and page template. Keep a source revision and before-state. Identify which layer owns each property before editing; adding another tag below an old one can leave the old value effective.

Choose the publisher's approved stable page URL for the preview identity. Keep the served URL, intended identity URL, redirect destination and any HTML canonical declaration distinguishable until reconciled. An edit to `og:url` does not install a redirect or change page access. Do not point every article to the homepage, copy a staging hostname into production metadata, or silently collapse language/version pages whose content differs.

Remove tracking only when it is truly a non-identifying parameter and the approved canonical policy supports removal. Preserve consequential content selectors. Hold authentication-bearing URLs for an approved safe replacement instead of shortening them until they look public. If the final hostname is not assigned, a symbolic value may appear in the private mapping, but do not call the dependent head fragment publication-ready.

For multiple languages, map each actual page and its language deliberately. Do not claim a translated version exists because an alternate locale code was added. Distinguish the format expected by a metadata property from the document's language tag, and verify that syntax in the applicable specification.

## 2. Compose a small, evidenced metadata profile

The [Open Graph protocol](https://ogp.me/) defines `og:title`, `og:type`, `og:image` and `og:url` as its base properties. It also defines optional descriptions, locale/site labels and image dimensions, media type and alternative text. Put image subproperties immediately after the image they describe; multiple root images are an ordered choice, not an unordered bag. Keep this base concise and consult type-specific requirements before selecting a specialized type.

Write a page-specific title and short summary grounded in the approved page. Keep qualifications that change meaning. Do not invent availability, prices, publication dates, authorship, endorsements or completion claims to make a card appealing. Keep the browser title and social title separately editable when their purposes differ, while ensuring they still identify the same page.

Choose the least-specialized accurate type. An ordinary service page should not acquire article-author or product-price fields solely because the template supports them. Use evidenced dates only when required by the selected profile; a build timestamp is not a publication date. Resolve conflicting source facts before producing final values.

For named consumers, add only the supported extension fields needed for the request. Preserve their documented attribute names and value syntax rather than copying Open Graph syntax to every tag family. Do not assume every consumer uses the same fallback order, truncation length, crop or cache behavior. Record any intentionally inherited base values so later page edits cannot create contradictory copies.

## 3. Associate a real, approved image

Select an image that represents the actual page and that the user is allowed to reuse. Inspect its pixels as well as its filename; an asset named “final” may still show a draft, private sidebar or obsolete product state. If artwork must be created or edited, perform that as an explicitly scoped asset task and retain its provenance. Do not use an arbitrary remote image or another publisher's logo as a placeholder in a finished candidate.

Record actual image bytes/revision, dimensions, media type, crop and the intended image URL. Use a stable approved absolute HTTPS address when the publishing contract supports it; an HTML attachment page, local filesystem path or expiring download link is not an interchangeable image endpoint. If upload has not happened, label the hosted asset dependency as pending.

Derive sizes and formats from the selected consumers' current documented needs. A convenient wide canvas is a design choice, not a universal requirement. Keep important text and the subject clear across the required crop variants; avoid baking the entire article into tiny text. Write descriptive image alternative text, not a second promotional slogan. Metadata cannot ensure that every platform exposes that text accessibly.

Retain the original asset and create separate approved derivatives when cropping or removing private metadata is needed. Inspect recipient-facing filenames and embedded metadata as appropriate. Deleting an image from the source later may not remove copies already cached by a third party; do not promise immediate recall.

## 4. Author the exact candidate and integration map

Produce the requested source/template edit or a per-page head fragment, plus a compact mapping of values to page and image identities. Escape values for the actual HTML attribute or template context. Literal quotes, ampersands and angle brackets must remain data; do not concatenate them into executable markup. Re-read decoded values to catch double escaping and truncation.

Replace the intended existing definitions at their owning layer, preserving unrelated head content, scripts and policies. Do not overwrite security headers, authentication, robots rules or consent behavior. A shared template must use page-specific values where required; check that a later route does not inherit the previous page's card.

For the static base, ensure the required values are present in the response/head output the target consumer can inspect. Tags appearing only after client-side navigation are a separate compatibility question. If the actual server output is unavailable, distinguish “template candidate prepared” from “served head verified.” Do not assert that every crawler executes or ignores JavaScript in the same way.

Keep preview mockups clearly illustrative. A locally rendered card can help assess wording and crop, but it is not a screenshot or observation of the named platform. Do not manufacture a platform check by drawing its logo around the candidate.

## 5. Separate source, delivery and consumer evidence

Check the saved work in layers, reporting each layer independently:

1. **Content:** Selected page coverage, faithful titles/summaries, accurate identities, language and approved audience
2. **Source structure:** Expected properties, no unintended conflicting duplicates, correct image grouping and decoded literal values
3. **Asset:** Actual image identity, visible content, rights, measured dimensions/format and the intended URL mapping
4. **Served response, when available:** Correct route-specific head, expected status and asset response; a login page or HTML error body is not the requested image
5. **Named consumer, when authorized:** Exact URL, platform, time and observed title/image/destination, with cache and crop differences recorded

Use passive local parsing for source checks; do not execute supplied scripts or automatically load linked resources. A check that receives HTTP 200 alone cannot establish that it received the intended page or image. A platform-success claim needs actual platform evidence, not the base specification or a local mockup.

When a consumer shows stale content, first compare the current served head and image revision with the observation. Investigate duplicate definitions, wrong URL identity, blocked fetch, redirect destination and cache separately. Use only a supported, authorized refresh route. Changing the page's identity URL or appending random tracking strings to force a refresh can create a different shared object; do not do it casually.

## Recovery and exact deliverables

- Missing title fact, final URL or approved image: finish independent rows and mark the dependent page held
- Conflicting templates: repair the responsible definition; do not stack more tags until one wins
- Wrong image crop or private detail: revise an approved derivative and repeat asset/source checks before publication
- Public fetch blocked: report the boundary; do not weaken access or add credentials to the URL
- Platform check unavailable or stale: deliver verified source evidence and the remaining consumer uncertainty without claiming a matching preview
- Publication timeout: inspect the current revision before retrying; preserve newer changes and verify an authorized rollback separately

Return the actual head fragments/source changes, the page-to-image/value map, any requested image derivatives and a brief status note with held dependencies and observed checks. A file-only request completes at prepared artifacts. If publishing is authorized, verify the served candidate after publication; if consumer verification is requested, retain its separate result. Do not send the link to other people as an unrequested test.

## Fictional illustration, not executed

A fictional pottery studio has an approved public workshop page and a private planning page. Its layout currently emits the homepage image on every route. The workshop source states “Beginner glazing, Saturday 14 November”; its approved photo shows the class table, but a separate screenshot includes private attendee names.

The proposed workshop fragment uses the workshop identity URL, the evidenced wording and the approved photo. The private planning page and attendee screenshot are excluded. The integration map replaces the layout's default on that route instead of adding a conflicting image tag. A local card drawing would be labeled illustrative; the named chat platform's cached preview would remain untested until an authorized observation.

This is an original fictional example. No image was published, external validator contacted, message sent or platform preview verified.
