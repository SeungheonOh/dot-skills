---
name: prepare-texture-atlas-handoff
description: "Pack approved raster sprites into matching texture pages and consumer metadata while preserving frame identities, trim offsets, pivots and animation alignment. Use for atlas asset delivery, not drawing sprites, implementing a renderer or optimizing a complete game."
---

# Prepare a texture atlas that preserves sprite placement

Deliver the selected sprite images as a coherent atlas package for a named consumer: texture pages, matching frame metadata and concise import notes. A tightly packed PNG alone is not a usable atlas. The recipient needs to recover each frame's identity, orientation and placement without guessing from its visible bounds.

Use [visual asset creation](../create-visual-asset/SKILL.md) for artwork changes and [SVG icon packaging](../package-svg-icon-library/SKILL.md) for vector symbols and their references. This workflow concerns raster frame extraction and placement, not scene-component implementation or a new game framework.

## Establish the consumer contract

Identify the authorized source set, output destination, existing public frame names and target engine/library version. Inspect the actual sources and preserve originals. Establish only the choices that affect this package:

- Consumer's atlas format and loader, including whether it accepts rotated, trimmed or multipage frames
- Intended logical dimensions, anchor/pivot convention and any animation frame order or durations that must survive
- Texture-size limits, permitted scaling, transparency, filtering and required resolution variants
- Required source/provenance files, attribution and whether the consumer already has an atlas being replaced

Do not infer the consumer from a `.json` extension. [Phaser's texture documentation](https://docs.phaser.io/phaser/concepts/textures) distinguishes uniform-cell sprite sheets from arbitrarily positioned atlas frames and provides separate atlas and multiatlas loading routes. Select the format for the actual loader rather than asking it to interpret a packer's default export.

If the target is unknown, prepare a source inventory and proposed contract; do not label invented metadata engine-ready. If only documentation is requested, return the specification without claiming texture pages exist. Use an already available authorized tool for production; installing a packer, acquiring a license or uploading private art is separate from preparing the handoff.

## 1. Keep frame identity independent of packing order

Map each selected source to its public frame name before packing. Resolve duplicate basenames, case-only differences and stripped extensions under the target's naming rules. Preserve established names unless a rename is requested. Do not use page position or an incidental directory enumeration as the public identity.

Record sequence order explicitly when animations are included. Alphabetical order can place frame 10 before frame 2; packing order need not be playback order. Retain repeated or fully transparent frames when they represent a deliberate hold or blank interval. If the packer cannot retain an empty frame, resolve its representation with the consumer rather than silently removing elapsed animation time.

Pixel-identical frames may share a packed rectangle if supported, but their public names and sequence entries must remain addressable. Treat aliases as intentional shared storage, not proof of an accidental duplicate. Exclude source drafts and unrelated assets deliberately rather than packing every reachable file.

## 2. Separate stored rectangles from logical sprites

For each frame distinguish:

1. Its rectangle on a particular texture page
2. Its retained image dimensions and orientation before packing rotation
3. Its offset within the original logical canvas
4. Its original canvas size and pivot in the declared coordinate frame

These values are not interchangeable. TexturePacker's [exporter data model](https://www.codeandweb.com/texturepacker/documentation/custom-exporter) distinguishes packed frame rectangles, source offsets and untrimmed sizes. Its packed rectangle excludes extrusion and swaps width/height for rotated sprites. That is a documented convention for that exporter model, not a universal schema for every atlas format.

Choose trimming only when the exporter and importer preserve the needed logical placement. A tight crop that becomes a new logical canvas is a different operation. Keep faint shadows and antialiased edges unless their removal is approved; inspect the actual trimming threshold rather than assuming only exactly transparent pixels disappear.

Define whether pivots are normalized or measured in pixels, which canvas they refer to, the origin and axis directions. Do not recompute every pivot from the center of each trimmed rectangle. In an animation, that can move a planted foot even when the original canvases align correctly. Preserve intentional per-frame pivot differences instead of imposing identical pivots universally.

Enable packing rotation only for a supported exporter/importer pair. Record the rotation convention; a Boolean flag without its format's interpretation is insufficient for a custom consumer. A non-square, asymmetrical frame is useful for detecting incorrect width/height or orientation handling. If support is uncertain, retain unrotated storage rather than hand-editing flags to make import appear successful.

## 3. Choose packing and sampling together

Use the target's page-size limits and image/compression constraints. Do not shrink artwork merely to fit one page if multipage output is supported and preserving resolution is required. Conversely, do not emit several pages to a single-page importer. If neither supported option meets the request, report the concrete size-versus-resolution decision.

Distinguish transparent spacing from repeated edge pixels. [TexturePacker's settings reference](https://www.codeandweb.com/texturepacker/documentation/texture-settings) describes shape padding between sprites, border padding at the sheet edge and extrusion that repeats sprite edges without changing sprite size. Keep these outside the logical content rectangle according to the chosen format; counting extrusion as artwork can enlarge or misalign frames.

Record the intended filtering and mipmap behavior instead of promising that an arbitrary padding value prevents every seam. The consumer may offer its own region-boundary handling: [Godot's AtlasTexture reference](https://docs.godotengine.org/en/stable/classes/class_atlastexture.html) documents `filter_clip` for clipping sampling outside a region. Such an option is consumer-specific, not a field to invent in another engine's metadata.

Keep alpha representation, color handling and permitted lossy changes explicit at the exporter/importer boundary. Do not add a premultiplication step simply because edge fringes are visible; first identify whether export, upload or blending already performs that conversion. Preserve pixel-art scaling requirements. Compression size and page occupancy are not evidence of better runtime performance.

For multiple resolution variants, bind each metadata file to its own pages, scale and logical-size interpretation. Never pair full-resolution coordinates with a half-resolution page. A repack can change every rectangle, so stable names do not imply stable coordinates. Do not reuse an old data file after changing any packed image.

## 4. Export a coherent package and inspect it

Write into a new destination and keep the previous usable package intact. Save page images and metadata from the same export revision, plus the packer project/settings when requested and portable. Record the selected source revision and output identities. Resolve page references from the consumer's expected base path, not merely the current working directory.

Reopen the saved files and reconcile the package:

- Every requested public frame and sequence entry resolves; omissions and approved aliases are explicit
- Every referenced page is present, and its actual dimensions agree with the metadata
- Stored frame regions fit their pages, with orientation and extrusion interpreted by the declared format
- Trim offsets, retained dimensions and logical canvases reconstruct the intended placements
- Pivots, frame timing and scale conventions survive; no packer debug outlines or unintended drafts entered the final pages

Inspect reconstructed frames from the final pages and metadata, not only a contact sheet of the original images. Compare a trimmed off-center frame, an asymmetrical rotated frame if used, a translucent edge and an animation sequence with a fixed reference point. Inspect transparent edges on contrasting backgrounds. Check the requested output, not an unrelated exporter preset.

When authorized and available, import the exact package in the named consumer and inspect frame lookup, orientation, animation alignment and edges at intended scales and filtering. Exercise every page when multipage delivery matters. A successful parse or a visually plausible atlas overview cannot establish that the consumer restores offsets correctly. Keep package inspection, visual reconstruction and target-consumer evidence separate; if the last step is unavailable, label compatibility unverified.

## Recover and deliver without mismatched revisions

For a missing frame, wrong page or moving anchor, trace the source-to-name-to-region-to-logical-placement path before changing artwork. Correct the responsible export setting or mapping and regenerate dependent pages and metadata together. Do not repair a symptom by shifting the user's source images or manually patching a packed PNG while retaining stale coordinates.

Deliver the actual pages, matching metadata, requested editable settings/source, and short import notes naming the consumer/version, public naming scheme, scale, trim/rotation support and sampling expectations. Include sequence data when requested and verification limits. A replacement handoff does not authorize installing it into a live application, publishing assets or deleting the previous revision.

Stop when the requested package is complete at its authorized boundary, or identify the exact missing source, importer capability or user choice. Do not claim loading-time, draw-call or memory savings without measurements from the relevant application.

## Fictional, unexecuted illustration

An invented two-frame character animation uses 64-by-64 logical canvases and a foot pivot at (32, 56), in top-left-origin pixel coordinates. Frame A retains a 20-by-40 image starting at (22, 16); frame B retains a 24-by-38 image starting at (20, 18). The logical pivot remains (32, 56), while its position relative to the retained image is (10, 40) in A and (12, 38) in B. Centering both trimmed images would discard that placement information.

If B is stored rotated, its packed rectangle has exchanged dimensions under the chosen rotation-aware format; that does not change its logical 64-by-64 canvas. If a later repack moves B to page two, the frame-to-page association must change with the pixels. Shipping the old metadata beside the new pages is a failed handoff even if all filenames still exist.

These are authored coordinates and expected decisions, not observed results. No packer, image transformation, parser, renderer, test, consumer import, live workflow or deployment was run for this illustration.
