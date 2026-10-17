---
name: capture-paper-document-batch
description: "Capture a bounded set of paper documents through an existing scanner into checked digital files, preserving sheet-side identity, document boundaries and recoverable rescan history. Use for paper-to-file acquisition, not OCR repair, assembling existing PDFs, scanner installation or destroying originals."
---

# Capture paper documents without losing pages

Produce the requested digital copies and a compact capture record that accounts for the original documents, required sides, saved files and unresolved rescans. The result is a readable, correctly ordered capture of the supplied paper. A completed scanner progress bar does not establish that every original was fed once or that faint content survived.

Use [searchable-pdf-review](../searchable-pdf-review/SKILL.md) for a requested reviewed OCR layer after acquisition, [pdf-packet-assembly](../pdf-packet-assembly/SKILL.md) for selecting pages from existing PDFs, and [document-filing-pass](../document-filing-pass/SKILL.md) for organizing an existing digital collection. Keep those downstream tasks separate unless the request includes them. This workflow does not certify an archival or legally equivalent replacement for paper.

## Establish the originals, operator and destination

Identify only the inputs that change the capture:

- Bounded original documents, their intended grouping/order and any excluded material
- Available scanner/model, computer, scanning application/version and supported flatbed or feeder route
- A person who can identify, load, turn, remove and account for the physical originals
- Required front/back coverage, intentional blanks, color-dependent information and difficult originals
- Requested output format, one-file-per-document versus another explicit grouping, naming and authorized save location
- Intended use and meaningful quality constraints, such as readable small annotations or a maximum delivery size

Keep physical observation, user-reported inventory and application evidence distinct. Remote control of a scan app is not access to the paper. If no one can prepare the originals, return the settings and loading checklist with that exact blocker; do not claim capture occurred. If only previously scanned files are available, work from those files under the relevant downstream workflow.

Confirm the selected scanner corresponds to the intended physical device, especially for shared multifunction printers with similar names. Do not start a scan until the operator has confirmed that the selected originals are in place and the device is free for this task. Reading a saved device entry is not proof of present readiness. Use the existing supported connection; installation, new accounts, firmware, network discovery beyond the selected device, and security changes are separate work.

Check where the selected scan action sends data before starting. A device shortcut may email, fax, upload, or save to a shared folder rather than save privately to this computer. Existing access to that shortcut does not authorize a new disclosure. Keep document content, destination and effective audience within the user's request; obtain required approval before any new upload, recipient or sensitive-data transmission. Do not enter credentials into improvised scan paths or copy them into the capture record. Preserve unrelated jobs, presets and device-wide defaults.

## 1. Account for sheets and sides before capture

Have the operator keep documents in their original order and record their boundaries. For a small simple item, a brief note is enough. For mixed or multi-pass work, assign a neutral document ID and sheet position, then distinguish its front and back, for example `D2-S3-front`. Keep printed page numbers as secondary locators: a cover may be unnumbered, numbers can restart, and one sheet can have two required images.

Record for each document:

| Original unit | Capture obligation | Useful evidence |
| --- | --- | --- |
| Single-sided sheets with confirmed empty backs | Front of each sheet; retain backs if requested | Sheet count and operator's back-side inspection |
| Double-sided or mixed-sided sheets | Each required side in reading order | Sheet/side map, including blank-side disposition |
| Insert, foldout, envelope or attached slip | Explicit selected surfaces and placement | Operator's description; supported handling route |
| Unknown backs or uncertain original count | Unresolved coverage | Specific inspection needed; no completeness claim |

Do not infer a blank back from a single-sided setting or infer original count from the output count. Preserve intentional blank pages unless their omission is authorized. Excluding a known blank changes the expected output count; record the omitted side rather than treating it as missing. Keep physical documents separate while scanning if automatic batch separation is unproven. Divider sheets and barcode separators are not inherently part of the document and must not silently become extra delivered pages.

Check the model's media restrictions before selecting the feeder. The operator should use the manufacturer's supported loading and jam-clearing instructions, not a generic face-up or face-down rule. [Epson's ADF guidance for one supported device family](https://files.support.epson.com/docid/cpd6/cpd63499/source/placing_originals/tasks/placing_originals_adf_lcd_anim.html) explicitly excludes several fragile, bound, attached and irregular originals from its feeder. That is a reason to consult the actual model's manual, not a universal specification for every scanner. Use an appropriate supported flatbed route or hold the item when safe handling cannot be established. Do not dismantle a binding, remove meaningful attachments, feed unsupported media or ask someone to reach into moving equipment.

## 2. Bind scan settings to the required images

Inspect the selected app's available controls and current settings. Set the narrow job options that the request requires; avoid overwriting a shared preset. Record source, sides, size/crop, color mode, resolution, format, grouping and destination so a rescan can be matched to the same job.

Choose settings by content and intended use:

- Select the actual flatbed or feeder source. Automatic selection is acceptable only when its behavior matches the prepared originals
- Enable duplex only when both the device and application support the intended two-sided capture. Duplex printing capability does not establish duplex scanning capability
- Preserve meaningful color, pale pencil, highlights, stamps and shaded diagrams. A high-contrast text mode may be unsuitable; assess a saved pilot rather than promising that a fixed resolution or mode fits all documents
- Capture the full required area, including marginal notes, edge marks and foldout content. Automatic crop, deskew, background removal, orientation and blank suppression need scrutiny because they can change membership or visible content
- Keep each required side as its intended output page. Disable side-stitching or other layout transformations unless the user actually wants that representation
- Select a genuine supported output format and grouping. A filename extension does not convert an image into a PDF, and a multi-page setting is not available in every app

[Apple's scanner instructions](https://support.apple.com/en-gb/guide/mac-help/mh28032/26/mac/26) describe source, resolution, duplex, destination and format controls, while warning that available options depend on the scanner. They also distinguish flatbed detection of separate images from a single enclosing area. A sparse page that is split into several detected objects needs a different crop choice, not an unexplained increase in page count.

[Microsoft's Windows Scan instructions](https://support.microsoft.com/en-us/windows/hardware/printer/install-and-use-a-scanner-in-windows) identify scanner/source selection, image format and an explicit save folder; their documented file choices are JPEG, PNG, TIFF and Bitmap. Do not promise a native multi-page PDF from that route. Use another already-available authorized app that actually supports the requested format, or agree on an image-set handoff or separately scoped conversion. Do not silently install a utility or upload the scans to obtain a PDF.

[Epson Scan 2's additional settings](https://files.support.epson.com/docid/cpd5/cpd58715/source/scanners/source/scanning_software/reference/epson_scan_2/escan2_main_additional_spc.html) illustrate separate controls for side stitching, blank-page omission, page editing and double-feed detection, and distinguish multi-page-capable formats from one-file-per-image output. Inspect the actual installed route instead of assuming those features are universal. Detection is a useful signal, not proof of page completeness.

For uncertain blanks or faint originals, retain all requested sides in the initial capture where supported. Omit a side only from evidence and the agreed blank policy. If the route cannot expose what automatic suppression removed, turn that job option off or hold completeness until a supported comparison resolves it.

Use a unique private job folder or filename group at the approved destination. Check collisions and available storage; do not overwrite an earlier scan simply because its name matches. Keep a prior verified file until the replacement has passed its checks. If the app necessarily autosaves, establish the folder and disclosure boundary before the first scan.

## 3. Check a representative pilot

For a batch, unfamiliar settings or manual two-pass duplex, scan a small representative portion before committing all originals. Include the feature most likely to fail: a back side, faint annotation, edge content, color key or a different paper size. Keep the pilot in the same authorized data boundary as the full capture.

Let the app finish saving, then reopen the actual saved image or file. Compare it with the identified original, with operator assistance where physical comparison is necessary. Check:

- Correct document and side, complete edges, intended orientation and readable smallest required content
- No blank replacement, clipping, divided page, doubled image, unintended side stitching or missing reverse side
- Actual saved format, image/page count, intended grouping and accessible destination
- Whether the feed order and front/back order match the planned map

A preview establishes only its displayed content. The saved result may use different settings or grouping. Do not call OCR correctness, searchable text, physical dimensional accuracy or color calibration verified from a readable scan.

For manual two-pass capture, record the actual first-pass order and a demonstrated mapping for the second pass. Do not assume the backs should be reversed or paired solely by filenames. Keep each physical sheet identifiable across turning and reloading, and verify front/back pairing using source content. If that cannot be done reliably, use a supported one-sheet-at-a-time route or stop for the needed physical assistance. Never mark or modify original documents just to create tracking labels without approval.

Correct the smallest job setting that explains a pilot failure, then repeat that representative check. A successful pilot may be retained as part of the final document only when its exact coverage, order and settings are compatible; otherwise keep it distinct so it cannot be appended twice.

## 4. Capture in recoverable groups

Work one document or explicitly mapped group at a time. Have the operator maintain separate unscanned, captured and unresolved originals, without losing their original order. Reconfirm the source, sides and destination after changing apps, reopening a job or switching paper types. A saved app preference may carry over from the previous document.

After each group, record the observed capture state and saved result before loading the next group. Use the app's supported add-pages or finish action deliberately: continuing a job may append to the current document, while finishing may create a new file. Verify the resulting boundary rather than inferring it from the button label.

If a feed error, timeout, app crash or uncertain save occurs:

1. Stop further submissions and preserve the current originals and candidate files. Do not repeatedly press Scan or force-close an app that may still be saving
2. Establish which originals moved and which images actually reached a finalized saved file. Attribute physical observations to the operator; a feeder counter alone does not identify saved sides
3. Reconcile saved images to the sheet-side map. Equal counts can conceal one missing side plus one duplicate
4. Resume or rescan only the established missing/damaged portion through the supported route, with a new attempt identity. If the boundary cannot be established, retain the partial and recapture that bounded document as a separate candidate after the operator safely resets its order
5. Compare the candidate before replacing the failed occurrence in the delivery copy. Keep the change traceable; do not append every retry or delete partials automatically

Follow the selected model's instructions for a physical jam or device error. Stop when safe paper handling, device ownership or recovery behavior is unclear. Do not disable protective detection, reset shared equipment or clear other people's jobs as an automatic recovery step.

## 5. Reconcile the final files with the paper

Open the exact saved delivery files, not only thumbnails or the app's unsaved review pane. For the bounded batch, inspect every output image/page at readable size and reconcile every required sheet-side occurrence. Use clear source content and the operator's comparison when direct access to paper is unavailable. A unique hash can identify a saved file but cannot prove it represents every original.

Acceptance requires:

- Each requested document has the correct separate file or agreed grouping, with no neighbor's pages mixed in
- Every required side is represented once in the intended order; deliberate repeats, omitted blanks and held items are explicit
- All required content is legible and included, especially marginal marks, light text, signatures as visible ink and color-dependent distinctions
- Rescans replace the intended defective occurrence without losing a neighboring page or silently changing another document
- The final format opens in the intended available viewer, filenames match the document map, and the saved destination is the approved one

If OCR was automatically added, label its review status separately; readable images do not validate recognized text. If only a subset of pages or originals could be checked, name that subset and retain an incomplete-coverage status for the remainder. Do not guess illegible wording or replace source marks with reconstructed text. Preserve a usable partial result while identifying the exact side needing a better capture.

Deliver the actual files plus a short record: document IDs/titles, physical coverage basis, output filenames/page counts, settings needed for rescans, excluded or unresolved sides, and checks performed. For a simple two-page document, this may be only a few lines; a mixed batch needs the fuller map. Verify any final copy or requested upload at its actual destination, under the applicable authorization.

Confirm the scan job has finished and the operator has recovered the originals. Restore task-only settings if necessary without overwriting concurrent changes or a requested reusable preset. Report leftover draft scans and any cleanup decision. Scanning does not authorize shredding, discarding, mailing, signing or certifying the originals, and successful delivery does not establish a retention policy.

## Fictional, unexecuted illustration

A fictional user asks for two separate PDFs from a four-sheet instruction leaflet and a two-sheet annotated note. The leaflet requires all eight sides, including an intentional blank. The note requires three written sides; its fourth side is confirmed empty and explicitly excluded. Expected delivery is therefore eight pages and three pages, not six pages or an assumed twelve.

In the illustration, the pilot's automatic blank suppression omits a faint reverse-side pencil annotation from the note. That setting would fail the capture requirement even though the app reports success. The operator would retain the draft, capture the note's required sides without suppression through a supported route, and compare the resulting three-page candidate with those exact physical sides. The leaflet's intentional blank would remain a separate mapped page. An equal total page count would still require identity and ordering checks.

This is an original authored illustration, not an observed result. No scanner, paper, application, PDF, settings, save operation or viewer was exercised for it.
