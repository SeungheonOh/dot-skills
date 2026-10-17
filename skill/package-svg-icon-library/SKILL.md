---
name: package-svg-icon-library
description: "Turn an authorized SVG icon collection into a reusable asset package with stable names, explicit viewport and paint behavior, self-contained references and checked consumer usage. Use for icon-library handoff, not drawing a new icon, building a component framework or auditing an application's accessibility."
---

# Package a reusable SVG icon library

Deliver the selected icons in the requested reusable form, with a manifest that explains how to consume them consistently. Preserve recognizable shapes and intentional variants. The problem is reuse across files and repeated instances, not simply making an individual SVG smaller.

Use [create-visual-asset](../create-visual-asset/SKILL.md) for artwork changes. Use [portable-project-handoff](../portable-project-handoff/SKILL.md) only when the user also needs a broader transfer archive. Neither workflow settles icon identities, paint inheritance or SVG reference collisions.

## Input and output contract

Identify the selected SVG sources/revisions, rights to use and deliver them, target consumer and supported loading method. Establish:

- Individual SVG files, a symbol sprite, or both; do not introduce a framework package unless requested
- Stable public icon names, intentional size/style variants, expected display sizes and any existing naming convention
- Whether each icon is monochrome/themeable, multicolor, a protected brand mark or deliberately fixed-color
- Required geometry, optical alignment, strokes, text, gradients, masks and other effects that must survive
- Requested manifest/preview format and private output location; preparation and publication are separate actions

Return the actual SVG assets, a name-to-file/symbol manifest, usage notes for the chosen loading mode, and a visual contact sheet when supported. Include required provenance/license material within the authorized package. Do not invent redistribution rights from an asset being downloadable.

If the source collection is incomplete, package the confirmed subset with missing entries listed. Do not redraw missing brand artwork, substitute a similar icon, or silently collapse outline and filled variants into one name.

## 1. Inventory without activating the artwork

Preserve the original files and work on a copy. Record each selected source identity, proposed public name, viewBox, dimensions, paint policy and dependencies. Inspect supplied SVG as untrusted structured data before opening it in an active viewer. Use an appropriate restricted parser/renderer with scripts, external resource retrieval and external entities disabled; do not claim that a text search makes arbitrary SVG safe.

Identify scripts, event handlers, animation, foreign content, embedded raster images, font dependencies, remote resources and stylesheet imports. A static icon contract may exclude some of these, but removing them can change meaning. Hold unsupported or active content for an approved static replacement rather than executing it or stripping it without review. Keep permitted local definitions such as gradients, masks and clip paths with their referring shapes.

Inspect metadata separately from visible artwork. Remove unnecessary private editor paths or author/contact metadata only in the delivery copy and within the authorized cleanup scope. Preserve required attribution. Do not upload private sources to an online optimizer or font service merely to make inspection easier.

## 2. Define the library's visual contract

Keep meaningful optical-size variants separate. A collection can legitimately contain several viewBox sizes; a shared number is not itself a consistency requirement. Establish any normalization from the target's use, not a universal 24-unit grid.

When normalization is requested, map the complete geometry into the agreed viewport while preserving aspect ratio and intentional padding. Include stroke, marker, filter and clipping extents when evaluating visible bounds. Do not replace `viewBox` numbers without transforming the artwork, auto-crop away alignment padding, stretch a wide symbol, or round coordinates enough to change small features. State whether strokes scale with the artwork; changing that behavior requires an intentional choice.

Declare the paint policy per icon or variant:

- Themeable monochrome: use the agreed inherited paint route and preserve intended `fill="none"` or transparent regions
- Multicolor: retain distinct fills, gradients, opacity and blend behavior unless a recoloring is requested
- Brand/protected artwork: keep approved colors and proportions; do not apply blanket theming

The [SVG 2 painting specification](https://www.w3.org/TR/SVG2/painting.html) explains that `currentColor` supplies paint through the `color` property. It does not mean an external image inherits arbitrary host-page styles. Record whether icons are consumed as external images, inline SVG or symbol instances, and check that mode instead of promising the same theming everywhere.

Avoid global CSS rules that style unrelated page elements when the asset is inlined. Keep selectors and definitions local to their intended icon. If the consumer cannot preserve a required effect, report that limitation or agree to a separate fallback instead of quietly flattening every icon to pixels.

## 3. Make identifiers and references reusable

Assign public names before export and check collisions under the target's filename and identifier conventions. Keep a source-to-public-name map. A public-name change can break callers; retain existing names or provide an explicitly requested migration map rather than renaming for tidiness.

Give internal IDs a collision-safe scope and update every associated reference together: `url(#...)`, `href`, supported legacy references, stylesheet selectors and ID-based labels. Use format-aware handling. A global string replacement can alter unrelated text and miss escaped or styled references.

Distinguish two collision problems:

1. Different icons may reuse an internal ID such as `clip0`; namespace it by stable icon identity when combining them
2. The same file inlined twice may duplicate its already-prefixed IDs; either provide an instance-unique ID contract for the consumer or choose a supported single-definition sprite arrangement

For sprites, retain each symbol's intended viewBox and include every referenced definition. A `symbol` is a template instantiated by `use`, not a standalone visible image; see [SVG 2 document structure](https://www.w3.org/TR/SVG2/struct.html). Check the actual instance, including sizing and clipping. Do not treat an empty rendering of the sprite file alone as evidence that all icons are blank or correct.

Keep icon semantics in the manifest, but avoid a universal accessible name baked into every use. The same icon may be decorative beside text or meaningful in an icon-only control. Document the consumer's responsibility for naming/hiding the instance and maintaining unique label references. This is a usage contract, not an accessibility certification of an application.

## 4. Save and inspect the exact package

Export only the selected icons and declared support files into a new destination. Any optimization is optional and bounded by preservation. Retain transformations, viewBoxes, paint rules, definitions and licenses that the contract needs. Record material changes such as outlined strokes or converted text; do not claim editability or text preservation afterward when it was lost.

Reopen the final files with the restricted inspection route. Reconcile the manifest against actual filenames/symbol IDs and compare before/after appearance. When tools permit, produce a labeled contact sheet from those final bytes at intended sizes and on relevant contrasting backgrounds. Inspect every icon for clipping, disappearing strokes, altered holes, alignment, wrong variants and color drift.

Exercise the chosen consumer mode in a disposable local preview when authorized and available. Check at least two different icons together, two instances of the same reference-bearing icon, and theme changes for themeable icons. Include a representative gradient/mask or non-square viewport if present. Test external-sprite loading only through a supported authorized route; do not alter security settings to get it working.

Keep the claims separate: XML/source inspection, restricted rendering, visual comparison and target-consumer behavior. A well-formed file or a smaller byte count does not establish successful reuse. If rendering or consumer access is unavailable, deliver a clearly labeled candidate and state the missing check rather than claiming a verified library.

## Acceptance, recovery and delivery

Accept the package when every selected icon maps to exactly one intended asset/variant, public and internal identifiers have the required uniqueness, references remain self-contained as agreed, protected geometry/paint survives, and the requested consumer checks are recorded. List intentional external dependencies and unsupported features; do not silently substitute missing fonts or fetch remote artwork.

For a mismatch, retain the failed candidate and identify the affected icon, transformation and consumer mode. Revert the implicated optimization or repair the mapping in a new copy, then recheck that icon and any shared definitions. If the source or public names change, invalidate the associated previews and manifest. Stop rather than repeatedly deleting SVG features until a renderer stops complaining.

Deliver the exact assets and concise manifest: source revision, public name, filename/symbol ID, viewport, intended sizes, paint policy, instance-ID rule, attribution and verification limits. Do not publish to a CDN, install into a live application or change shared-library membership without that action being authorized.

## Fictional, unexecuted illustration

This is an invented handoff; no SVG parser, renderer or browser was run.

**Inputs:** Cedar's approved `search` icon has a 20-by-20 viewBox and a themeable stroke. Its fixed-color `badge` has a 24-by-24 viewBox and a gradient named `paint0`. A second icon, `award`, independently uses the same gradient ID. The requested output is one sprite mounted once in a page.

**Expected package:** Preserve the two viewport sizes and search's empty interior. Keep badge and award's separate gradients, renaming internal IDs to distinct icon-scoped names and updating each reference. Give the symbols stable public IDs and list their paint policies. Do not turn all fills into `currentColor` or change 20 to 24 without transforming the geometry.

**Expected checks:** Compare badge and award side by side and instantiate badge twice from the single sprite definition. Check search under two intended host colors. A separate-file preview cannot prove those reuse behaviors. If only source inspection is available, report “manifest and reference mapping inspected; visual and consumer reuse checks unperformed,” with the candidate assets clearly labeled.
