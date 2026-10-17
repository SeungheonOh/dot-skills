---
name: prepare-print-production-package
description: "Prepare approved artwork for a named print-production contract, delivering a production PDF or requested native package with trim/bleed, color, font and preflight evidence. Use for commercial-print handoff, not new artwork, ordinary document export, ordering printing or guaranteeing physical color."
---

# Prepare a print-production package

Turn approved artwork into the exact files a specified print provider or production workflow requires. Deliver the production candidate and a compact job specification tied to its revision. “High quality PDF” is not a complete production contract.

Use [create-visual-asset](../create-visual-asset/SKILL.md) when the artwork still needs creating. [document-export-check](../document-export-check/SKILL.md) preserves an approved document through ordinary PDF conversion, while [validate-svg-print-geometry](../validate-svg-print-geometry/SKILL.md) checks SVG bounds. This workflow adds the production-specific decisions for finished size, bleed, separations, output condition and recipient handoff.

## Input and output contract

Identify the approved artwork/version, selected pages or sides, native sources and linked resources. Obtain the provider's supplied or current official specification for this product and process, with its date or revision. Relevant requirements include:

- Finished dimensions and units, orientation, page/side order, single pages versus spreads, and any folding/binding or dieline template
- Bleed by edge, safe-content requirements, expected page boxes and requested printer marks
- Accepted file format and PDF/X variant if specified, transparency handling, color spaces, output condition/profile and spot-color treatment
- Minimum effective image resolution or line/detail limits for the intended size, supplied by the provider rather than a universal preset
- Font embedding or native-package requirements, permitted supporting assets and delivery size/naming limits
- Authorized destination and whether the task ends at preparation, includes transmission, or also involves a separately approved order

Ask only for missing requirements that change production. With no named provider, prepare a labeled candidate and unresolved specification list; do not choose CMYK, 300 ppi, 3 mm bleed or PDF/X-4 as if they were universal requirements. Do not contact a printer on the user's behalf unless requested or otherwise authorized.

Return the actual production PDF or requested native package, a human-readable job ticket, a version-matched preflight record, and a review preview when useful. Label previews as review copies, not contract color proofs. Include native sources or fonts only when requested and permitted; they are not automatic companions to a PDF delivery.

## 1. Freeze the approved revision

Preserve source bytes and work in a separate candidate. Record source identities and available revisions/digests, page selection and the production contract. Inspect linked artwork, fonts, hidden layers, annotations and production guides. Distinguish intended print content from guides, dielines, foil/varnish plates and nonprinting notes; do not decide their printing behavior from a layer name alone.

Resolve missing or stale linked files before claiming the package is complete. Relinking to a similarly named asset may change approved content. Keep exact copy, barcodes, URLs, logos and required legal text intact; a production pass does not authorize rewriting them or claiming that a barcode was scanned.

Keep proofs and job tickets as private as the artwork. Do not send files to online converters, public preview hosts or support portals without authorization for that destination and data. Check whether a preparation folder is already shared or synced before placing private sources there.

## 2. Reconcile page geometry with the physical product

Build the candidate at the intended finished size. Distinguish the trim boundary, artwork extending into bleed, safe placement for essential content, and additional space for marks. Confirm the actual trim/bleed/media boxes and rotation in the saved PDF, not merely the document's displayed canvas size.

Extend only content that is meant to reach the cut edge. Increasing a PDF's bleed box does not create missing artwork. Do not stretch the whole design, mirror an edge, move a logo or crop text to manufacture bleed without an authorized content/layout change. If a supplied source ends at trim, identify the exact edges that need source work.

Use the provider's single-page/spread, duplex orientation and page-order rules. Do not perform imposition, add blank pages, compensate for binding creep or rearrange panels unless that treatment is specified. A flat width can be correct while fold-panel order is wrong; compare against the actual template when one is supplied.

Add only the requested marks and offsets, keeping them outside required live artwork. Adobe's [printer-mark guidance](https://helpx.adobe.com/indesign/desktop/print/page-set-up-and-printer-marks/set-printer-marks.html) distinguishes marks from bleed setup and calls for confirming the provider's expectations. A checkbox named “include bleed” is not evidence that edge artwork reaches the required boundary.

## 3. Preserve color and resources deliberately

Compare source color spaces, embedded profiles, spot names and overprint behavior with the production contract. Keep intentional spots separate from process colors when required. Do not replace a named ink with an arbitrary process approximation, merge similarly named spots, use registration color as ordinary black, or apply a blanket rich-black recipe.

Separate conversion from output-intent metadata. An output intent describes the intended output condition; adding one does not itself convert object colors, as [Adobe explains](https://helpx.adobe.com/acrobat/using/output-intents-pdfs-acrobat-pro.html). Use the provider's requested profile and conversion policy, preserving tagged inputs when appropriate. Never assign a guessed profile to unknown source values and call the result color-correct.

If conversion, transparency flattening, rasterization or outlining is needed, identify what changes and preserve the editable original. Resolve appearance or editability tradeoffs that are not already approved. A flattened derivative may be appropriate for a particular production requirement; it is not a universally safer export.

Inspect font availability and the saved PDF's embedding/subsetting against the agreed contract. Do not accept substituted glyphs, altered line breaks or changed logo lettering silently. Font embedding and font redistribution are different permissions. Do not bypass embedding restrictions, package font files without permission, or outline all text as an unrequested workaround.

Evaluate raster resolution at the placed physical size, not just the source file's resolution tag. For a simple unrotated image, effective pixels per inch is pixel width divided by placed width in inches; inspect both axes and actual transforms when relevant. Upsampling does not restore missing detail. Preserve a low-resolution finding and ask for a better source or accepted compromise rather than claiming a new metadata value fixed it.

## 4. Export a bounded production candidate

Use an available supported exporter and the exact provider preset/options when supplied. Record application/version, selected pages, format variant, geometry, marks, color/conversion choices, font handling and warnings. Save to a fresh filename; do not replace the approved source or an existing production release while investigating.

For a native package, use the application's supported packaging route and reconcile the included links, source version and permitted resources. Do not add unrelated drafts or assume a packaged font is licensed for the recipient. When native packaging is unavailable, identify that limit and ask whether a supported PDF-only handoff meets the request.

After export, open the exact saved candidate. Confirm it is newly produced and contains the intended pages/sides. If conversion fails, preserve the error and partial output separately. Correct the implicated setting within scope and make a new candidate; do not install an unapproved tool, upload elsewhere or disable security controls to finish.

## 5. Preflight and inspect the final bytes

Use the provider's supplied preflight profile or an available checker whose scope matches the contract. Inspect the profile before running it; distinguish analysis from automatic fixups. Adobe's [preflight documentation](https://helpx.adobe.com/acrobat/using/analyzing-documents-preflight-tool-acrobat.html) describes profile-dependent checks and corrections. Record the actual checker/profile/version and remaining warnings. A preset name or PDF metadata label is not proof of PDF/X conformance.

Reconcile these independent properties:

1. **Geometry and order:** Finished dimensions, page boxes, bleed content, safe placement, orientation, sides/panels and expected marks
2. **Resources:** Intended images, effective resolution, fonts/glyphs and absence of missing or accidentally substituted content
3. **Color and plates:** Required output condition, object color spaces, spot plates and overprint behavior using an appropriate separation/output preview where available
4. **Appearance:** Render every delivered page/side and inspect clipping, transparency seams, fine text, logos, lines and transformed regions at useful magnification
5. **Contract:** The requested format/profile checks actually performed, unsupported features and any provider-specific requirement still unverified

Inspect separations when the job depends on spots or overprint; an ordinary RGB preview cannot establish plate behavior. Do not claim calibrated color, physical trimming, press output, barcode scanning or recipient acceptance from a screen rendering. If a proof is requested, distinguish a local review image, printer-produced proof and physical proof approval.

If preflight fixups change the file, treat it as a new candidate and repeat affected structural checks plus the page review. If a material requirement fails, deliver the finding with the candidate clearly held. Do not remove required content to obtain a green preflight report.

## Handoff and stopping point

Make the job ticket identify the exact file/revision, finished size, pages/sides, color/spot policy, provider specification, export settings, performed checks and outstanding decisions. Reconcile every delivered file with the intended package; obsolete proofs and earlier candidates should not be mistaken for the production file.

Stop at a checked preparation package when transmission was not requested. If delivery is authorized, verify the recipient and destination, send only the reviewed files and retain available receipt/version evidence. An upload receipt is not a printer's production approval. Purchasing, accepting changed terms or approving a proof that commits the job requires the applicable separate authorization.

Report three statuses separately: preparation, checks against the documented contract, and provider/physical-proof acceptance. When a required checker or profile is unavailable, say which requirement remains unverified and give the smallest needed next step. Avoid an unqualified “print-ready” claim.

## Fictional, unexecuted illustration

This invented scenario is not a completed export, preflight, print order or physical proof.

**Inputs:** A fictional provider requests a two-sided card, 148 by 105 mm finished size, 3 mm bleed on every edge, separate pages in front/back order and no printer marks. Its supplied profile and PDF/X variant are explicit. The approved source has complete front artwork but the back background stops at trim on its right edge. One raster image is 600 pixels wide and placed 3 inches wide; the provider's stated minimum is 250 ppi.

**Expected decisions:** The required bleed extent is 154 by 111 mm before any additional outer area. Do not confuse that extent with finished size. Hold the missing back-edge artwork for an authorized source extension; enlarging a box is insufficient. Report the image's 200 ppi effective horizontal resolution and request a better source or approved exception. Do not silently upsample it or add marks.

**Expected handoff:** A candidate and job ticket can be prepared, but acceptance remains held for the back-edge bleed and image requirement. After an authorized source repair, record the revised source identity, regenerate the candidate, rerun the relevant preflight and inspect both sides. Provider acceptance and physical color remain untested even if those local checks later pass.
