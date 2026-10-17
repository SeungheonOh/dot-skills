---
name: create-visual-asset
description: Create or edit a raster image, illustration, icon, or vector artwork from a visual brief, and deliver a usable saved asset. Use for making artwork or changing an existing asset; charts and explanatory diagrams, selecting existing photos, and complete websites or presentations have separate primary workflows.
---

# Create a Visual Asset

Turn the user's brief into a usable visual file, with the requested appearance, content, format, and practical constraints. A prompt, style recommendation, or mood board alone is not the deliverable unless that is what the user requested.

Use `visualize-information` when the main task is encoding data, processes, timelines, or system relationships. Use `photo-selection-caption-review` when the main task is choosing existing photos and grounding captions. Creating an illustration or editing a selected image belongs here; it does not replace those workflows or authorize publication.

## Establish the asset's job

Use the request and supplied references to establish what the asset depicts, where it will be used, and which properties are fixed. Relevant constraints include dimensions or aspect ratio, intended display or print size, background or transparency, required wording, brand elements, file type, and later editability. Ask only about missing information that would materially change the result. A simple, clear request does not need a design interview or a set of alternatives.

Inspect supplied artwork before editing or treating it as a reference. Separate the exact source to modify from examples that only suggest a style. Identify what may change and what must survive: composition, geometry, subject details, lettering, colors, margins, or layer structure. If the required source is missing or too limited to support the requested fidelity, ask for that source rather than silently reconstructing it.

## Choose a production method that fits

Check the authoring, generation, editing, rendering, and export capabilities actually available, and follow their tool instructions. Honor a requested medium or native format. When the choice is open:

- Use raster production for photographic, painted, textured, or other pixel-based results. Choose generation when interpretation or synthesis fits the brief; do not assume it will preserve exact details in a constrained edit
- Use vector or an appropriate native authoring format for scalable geometric artwork, precise paths, controlled lettering, or meaningful object-level editing. Extend an existing vector or native source when its structure is part of the requirement
- Use a mixed workflow when it serves the asset, such as placing generated artwork within a precise layout. Verify the composition after assembly

Choose the method from the required result, not from the availability of a favorite tool. An image embedded in an SVG or a layered document is still a raster image; a flattened export is not an editable source. Do not claim unsupported native editability or invent a conversion that preserves it.

Match the output to its use. Pixel dimensions, aspect ratio, transparency, and print dimensions are different constraints. Do not stretch artwork to fit a ratio, crop away protected content, or treat a resolution metadata change as added image detail. If exact geometry or a required export cannot be achieved with available tools, explain the specific limitation and resolve that tradeoff before substituting a materially different result.

## Create or make the bounded edit

For a new asset, translate the brief into composition, subject, palette, and treatment without adding unrequested slogans, labels, logos, or variants. Use approved brand assets and supplied wording faithfully. Include text when the brief calls for it; choose a method that can produce and verify that text accurately. There is no mandatory style exercise, reference search, or number of drafts.

For an edit, retain the original and work on a separate version unless replacement is explicitly requested. Apply the requested change at the smallest appropriate scope. Use supported selections, masks, paths, or layers when they help protect untouched content. Do not silently redraw a logo, reshape a product, alter a person's features, or change the overall layout as a side effect of a local correction.

Compare the result to the source, including regions meant to remain unchanged. Generative resemblance does not establish exact preservation. Where exact pixels, coordinates, dimensions, or wording matter, check those properties directly when possible. If a method keeps introducing drift, change to a supported method that can meet the constraint or report the remaining limitation; do not relax the user's requirement to finish.

For a tightly bounded edit, make preservation testable before changing the asset: name the editable objects or region and the protected content, using layer IDs, coordinates or a marked reference where useful. Distinguish exact pixel preservation from unchanged wording, geometry or visual appearance. For a pixel-exact requirement, compare decoded samples in protected regions on the same pixel grid with the relevant channels and sample depth preserved; do not resize the comparison or add an arbitrary tolerance to conceal drift. For vector edits, check protected paths, transforms and text as well as their rendering. A whole-image resemblance score cannot establish that a small protected label survived.

## Check the saved result

Save the actual deliverable, then reopen or render that saved file. Inspect it at its intended viewing size and at a useful detail scale. Check the parts that matter for this request:

- Content and appearance: required elements, exact text, brand fidelity, composition, clipping, edge artifacts, and legibility
- File properties: actual format, dimensions, aspect ratio, transparency where requested, and whether the recipient can open the result
- Edit fidelity: requested changes are present, protected content remains intact, and any required geometry or source structure is preserved
- Export integrity: fonts, linked images, masks, effects, and other relevant dependencies survive the export or are packaged appropriately

For transparency, inspect both the alpha data when available and the appearance against contrasting backgrounds; a painted checkerboard is not a transparent background. For vector or native files, inspect a rendered view as well as the relevant source properties. A successful save command or source-code review alone does not establish visual quality.

Correct observed problems and check the revised output. Distinguish checks actually performed from properties that remain unverified. If visual inspection or a required export is unavailable, say exactly what is missing; do not describe the asset as fully checked.

When an export fails preservation, return to the untouched source or last verified version and isolate the failing edit/export step. Keep the failed candidate distinct; do not repeatedly repair its drifted regions from memory. Recheck the protected content after the repair, not only the area just changed.

Check required source dependencies from the delivered copy, not only the working document. For example, an SVG [image element can reference another file](https://www.w3.org/TR/SVG2/embedded.html#ImageElement); the SVG filename alone does not establish that the artwork is self-contained. Package or embed authorized dependencies when the requested format permits, and reopen the packaged result. Keep a missing dependency unresolved if inclusion or substitution is not authorized. Outlining text or flattening effects is a delivery choice when it changes requested editability, not an automatic repair.

## Deliver the usable asset

Return the saved file through the available private delivery route, with a viewable preview when useful. Include genuine editable source when requested, along with dependencies needed to use it. Keep source and exported versions consistent. Do not add hosting, public links, uploads to unrelated services, or publication merely to deliver the work.

Keep the handoff proportional: identify the final file, relevant dimensions or format, what changed for an edit, and any material limitation. A single requested image usually needs one finished asset and a brief reply. Do not burden it with extra variants, process logs, or unsupported claims of production readiness.

## Fictional bounded edit, not executed

A fictional 800 × 800 PNG badge needs only its small orange star recolored teal. The user requires every decoded pixel outside the supplied star mask, including the words “NORTH PIER,” to remain identical. A candidate with a shifted letter fails even if the star looks right and the canvas size is unchanged. The expected recovery is to return to the original, apply the recolor within the mask using a supported precise method, and compare protected samples again in the saved PNG.

The transparent background must also survive: inspect transparency data and the edge appearance on contrasting backgrounds. PNG supports multiple [transparency representations](https://www.w3.org/TR/png-3/#6AlphaRepresentation), so checking only for a channel named “alpha” is insufficient. These are expected checks for invented assets; no image was edited, rendered or inspected.
