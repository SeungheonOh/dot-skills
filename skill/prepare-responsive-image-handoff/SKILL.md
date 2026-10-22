---
name: prepare-responsive-image-handoff
description: "Prepare web-image derivatives and a placement-specific source-selection handoff, preserving approved crops and reconciling actual files with srcset, sizes and picture branches. Use for existing imagery, not new artwork, a complete website, live deployment or a performance certification."
---

# Prepare responsive images that match their placement

Deliver the selected image derivatives, a compact asset-to-placement map and integration instructions that agree with the real files and layout. A folder of differently sized pictures is not yet a responsive-image handoff: the consumer must know which candidates preserve the same composition, when a different crop applies, and how large the image is meant to render.

Use [visual asset creation](../create-visual-asset/SKILL.md) for new artwork or substantive image edits, [image text alternatives](../prepare-image-text-alternatives/SKILL.md) for placement-specific meaning, and [website creation](../build-usable-website/SKILL.md) for a complete site. This workflow packages existing approved imagery for established web placements. It does not authorize a site change, upload or CDN configuration.

## Establish the placement contract

Start with the exact source images, intended placements, available layout/CSS or design measurements, required crops, supported delivery formats and output destination. Identify protected details, transparency, color expectations, attribution and any byte budget. Ask only for a missing choice that changes the output; a single fixed-size image need not become a many-breakpoint project.

Record source identity and preserve originals. Inspect the actual image rather than inferring dimensions or content from a filename. If the request is a proposal only, deliver the proposed map without pretending derivative files exist. For production, use an available authorized image tool and new output paths. Private images must not be sent to an external optimization service merely for convenience.

Distinguish three jobs before choosing variants:

- **Resolution selection:** The same composition at different pixel dimensions for one placement.
- **Art direction:** Different approved crops or compositions for different layout conditions.
- **Format alternatives:** Equivalent content encoded in different supported formats.

Do not put unrelated crops into one resolution ladder and let density determine the subject shown. A small screen does not itself establish a low-density display. If no alternate crop is approved, preserve the composition and hold any proposed content-changing crop.

## 1. Map displayed space before choosing export sizes

For each placement, record its rendered width rule in CSS pixels, relevant breakpoints and aspect ratio. Distinguish viewport width from image-slot width: a card in a multi-column grid may occupy only a fraction of the viewport. Include container limits and gutters where they change that rule. If the layout is unknown, label candidate widths provisional rather than inventing a universal sizes string.

Choose a small useful set of derivative widths from the placement's size range and intended display-density coverage, capped by the usable approved source. Do not enlarge a small source just to meet a nominal high-density target or claim that an enlarged export gains detail. Explain an unresolved sharpness-versus-byte-budget tradeoff instead of silently reducing the intended coverage.

Keep image sizing and selection separate. CSS controls layout; the sizes attribute describes the source-size expectation used for selection, not a CSS layout command. Google's [responsive-image guidance](https://web.dev/learn/design/responsive-images) explains responsive sizing, aspect-ratio preservation and fitting. Record whether the actual component scales the full image or uses a cropped display box. A correctly prepared crop can still lose protected detail under a later object-fit/object-position rule.

## 2. Produce and inspect the actual candidates

Build each resolution family from the same approved master/crop rather than repeatedly resizing an already compressed derivative. Retain the crop identity separately from the encoded width. Use deliberate output names that distinguish placement, crop, width and format without exposing private source names.

For every saved candidate, inspect actual format, decoded dimensions, byte count and relevant transparency/orientation/color behavior. Compare the saved image with its approved crop at the expected viewing size and at a useful detail scale. Check faces or subject edges, labels, fine lines and transparency against relevant backgrounds where those properties matter. A successful encoder exit is not a visual-quality check. Do not silently strip required attribution metadata or retain unnecessary sensitive metadata in a public-facing derivative.

Keep a compact manifest: source/crop identity, output path, actual width and height, format, bytes, digest, intended source set and any accepted loss. A width in the filename is a label, not measurement. If a planned export is missing, corrupt or over budget, hold its dependent references; do not leave plausible URLs for nonexistent files.

## 3. Describe source selection without promising a specific download

For variable-width placements, use width-descriptor candidates with an explicit sizes rule that matches the layout. For a genuinely fixed rendered size, density-descriptor alternatives may be simpler. The [HTML source-set requirements](https://html.spec.whatwg.org/multipage/images.html#srcset-attributes) prohibit mixing width and density descriptors in one set and duplicate descriptor values. Width descriptors must match the resource's natural width. Check actual asset geometry, not just the written markup.

Supply the intended img fallback and preserve the placement's text-alternative decision. For art direction or format selection, provide ordered picture/source branches, each with its media/type conditions, candidate set and applicable sizes rule. The [HTML picture/source definitions](https://html.spec.whatwg.org/multipage/embedded-content.html#the-picture-element) place source elements before the contained img; picture sources use srcset, not src. Order conditions deliberately so a broad branch does not mask a narrower intended branch. Format alternatives must preserve the right crop within each layout condition.

Do not describe picture as retry-on-error delivery. A supported selected resource that fails to load is not guaranteed to cause the browser to try the next source or img URL. Include every referenced fallback asset in the package and distinguish format fallback from network resilience. The HTML [image processing model](https://html.spec.whatwg.org/multipage/images.html#updating-the-image-data) describes broken requests separately from source selection.

Carry width/height or an appropriate layout reservation for the selected aspect ratios, not blindly the master image's ratio. MDN's [img reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/img) explains dimension attributes and loading behavior. Do not apply lazy loading indiscriminately to the placement's immediately needed hero image. Keep loading priorities, preloads and site-wide performance tuning outside this asset handoff unless explicitly requested.

Resolve paths relative to the actual consuming document or component convention, including an intended hosted subdirectory when relevant. An asset opening from the preparation folder does not prove that its published URL will exist. If the consumer is a CMS or framework image component, map to its supported inputs instead of adding a second competing transformation/selection layer. Generated destination URLs remain unverified until that system produces them.

## 4. Reconcile files, meaning and integration evidence

Read back the saved handoff and reconcile all selected placements and branches:

1. Each referenced file exists in the prepared package. Width descriptors match inspected resource widths; density descriptors agree with the intended fixed rendered size. Neither set contains accidental duplicate candidates.
2. Each resolution family preserves its declared crop; every art-direction branch retains the information required by the placement and its alternative text.
3. Source conditions and their order cover the intended layouts, and sizes agrees with the supplied slot rules rather than an assumed full-width image.
4. Fallbacks, reserved aspect ratios, approved metadata treatment and byte-budget exceptions are explicit.
5. The unchanged originals and final output identities are distinguishable, and obsolete candidates are not accidentally included as final assets.

These are package and integration-specification checks. If a browser preview is separately authorized and available, inspect the consuming component at representative widths, just around an art-direction boundary, and relevant densities. Record browser/version, viewport, rendered slot width, selected URL and visible crop. MDN documents that [currentSrc](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement/currentSrc) identifies the selected URL regardless of whether loading succeeded; pair it with actual load/render evidence. Do not use it alone as proof of success.

Expect selection flexibility: the [HTML image guidance](https://html.spec.whatwg.org/multipage/images.html#introduction-3) allows browser decisions informed by density, zoom and other conditions. A hand-calculated slot-times-density target is a planning aid, not a guarantee of one exact downloaded file. Inspect fresh loads as well as relevant layout changes when needed; record cache conditions without clearing the user's unrelated browsing data. Never claim transfer-byte savings, loading performance or target-browser compatibility from static markup alone.

## Deliver and stop at the evidenced boundary

Return actual derivative files, the placement/source-set map, copy-ready integration markup or exact component-field instructions, and material exceptions. Distinguish source inspection, export inspection, static integration review, browser selection/rendering and deployment. No runtime checks means no runtime success claim.

If a crop removes needed information, return to the approved master and revise within scope; do not repair its alternative text to disguise the content loss. If layout measurements change, update dependent sizes/branch requirements rather than recompressing everything blindly. If the destination rejects a format or rewrites URLs, retain the valid assets and identify the exact integration decision still needed.

Stop when the requested package is complete at its authorized boundary or a concrete source, layout or capability gap prevents completion. Publication, shared-library replacement and ongoing image optimization are separate work.

## Fictional, unexecuted illustration

An invented workshop page has an approved 3:2 photograph and a 600 CSS-pixel maximum content column. Its layout specification says the image is viewport width minus 32 pixels below a 632-pixel viewport, and 600 pixels thereafter. The proposed width family is 600 by 400 and 1200 by 800, with sizes written as `(max-width: 632px) calc(100vw - 32px), 600px`. The filenames and candidate descriptors would have to match the actual exports before delivery.

At a 400-pixel viewport, the declared slot is 368 CSS pixels, not 400. A later design request for a square mobile crop is a separate art-direction decision, not permission to mix a 600 by 600 crop into the existing resolution family. If that crop removes the workshop's identifying sign, its visual meaning and existing alternative need review. Neither the arithmetic nor a proposed candidate set proves which file a browser downloaded.

These are fictional inputs and proposed decisions only. No image export, parser, browser, program, test, live workflow, upload or deployment was run for this illustration.
