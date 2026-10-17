---
name: add-pdf-navigation
description: "Add or repair a PDF's bookmark hierarchy and logical page labels without changing its pages, using a source-grounded destination map and saved-file navigation checks. Use for reader navigation in an existing PDF, not merging pages, OCR or adding printed page numbers."
---

# Add navigation to an existing PDF

Deliver the same document with a usable navigation layer: meaningful bookmarks that land at the intended sections and, when requested, page labels that correspond to the document's numbering. Include a concise contents/page map for readers whose viewer does not expose those features. An attractive bookmark list is insufficient if its links land one page late or hide the heading above the viewport.

Keep this task distinct from page assembly, visible contents-page insertion, OCR, document rewriting and full accessibility remediation. Bookmarks and labels do not add a PDF tag tree or make a scan readable to a screen reader. Do not change page order, visible numbers or content merely to make navigation arithmetic easier.

## Inputs and scope

Identify the exact PDF/revision, requested section depth, existing contents or heading evidence, any supplied outline, intended viewer if known, and output location. Determine whether existing navigation should be preserved and extended, repaired in a named subtree, or replaced. A general request to add bookmarks is not permission to discard working ones. Ask only when the source or requested numbering is genuinely ambiguous.

Keep the original bytes and record a digest, page count and existing navigation snapshot. Save a separate candidate unless replacing this exact destination was requested. Source headings, extraction records, filenames and contents maps inherit the document's privacy. Do not upload to a web PDF editor, publish the map or send the file to recipients without the relevant authority. Reading existing URI targets does not require opening them.

Inspect encryption, signature indicators, forms, attachments, annotations, named destinations, page labels, outlines, tags and unusual actions before choosing a tool. Do not bypass protection, strip signatures or present a changed derivative as still signed by the original signer. For a signed original, establish whether an explicitly labeled unsigned derivative is appropriate; otherwise deliver a separate navigation map without modifying it. A security flag inventory is not signature validation.

Do not activate JavaScript, submit actions, external-file launches or embedded content while inspecting navigation. Adding ordinary in-document bookmarks does not authorize executing an existing action. If a supported safe inspection/editing route cannot preserve a required feature, stop that route and report the feature rather than silently flattening or rasterizing the file.

## 1. Resolve page identity and section destinations

Keep three values separate for every target:

- **Physical page:** its one-based position in this saved PDF
- **Tool index:** the API's page index, often zero-based; derive it once from the physical page
- **Document label:** the printed or intended logical label, such as `iv`, `1` or `A-3`

Inspect actual pages at section starts and numbering transitions. Do not infer one global offset from the first body page: inserted plates, unnumbered covers, appendices and numbering restarts can break it. A scanned contents page can supply candidates, but its printed page numbers and OCR text need reconciliation against the actual destination headings.

Prepare a destination map before writing:

```text
entry ID; parent ID; sibling order; bookmark label;
physical page; existing/desired logical page label;
heading evidence; desired view/position;
action: preserve / add / repair / remove as authorized
```

Use stable local entry IDs so repeated headings such as “Notes” do not collapse. Preserve source wording when it is useful; use brief distinguishing context when identical labels would confuse readers. Do not infer a hierarchy from font size alone. Keep a chapter's children under that chapter and in source order; exclude decorative headings and ordinary running headers.

A bookmark normally lands at a point/view, not a selectable page range. If the user wants “print chapter 2,” include the physical start/end range in the companion map; do not imply one bookmark encodes that printing operation.

For a long page, choose a view that reveals the heading and the beginning of its content. Prefer a native editor's supported destination-setting operation when coordinate conventions are uncertain. Programmatic coordinates must account for the tool's origin, page rotation, CropBox and scaling; never reuse screenshot pixels as PDF coordinates. If only a page-level destination is reliable, use it and disclose the granularity.

## 2. Construct bookmarks without disturbing existing content

Use an installed PDF-aware editor or library with suitable preservation support. Record the version and save method. [Adobe's bookmark instructions](https://helpx.adobe.com/acrobat/using/page-thumbnails-bookmarks-pdfs.html) describe creating an entry from the intended view and setting its destination. Verify the current interface rather than relying on an old menu screenshot.

For each new entry, set its label, parent, sibling position and in-document destination from the map. Keep parent handles/identities distinct from label text. Create parents before their children when the API requires it. Set expansion state for a useful starting view; do not force extreme zoom or a screen layout that makes reading harder. Avoid adding external or active actions when an internal destination suffices.

Preserve existing bookmarks, named destinations, link annotations and their actions unless an exact change was requested. When repairing an entry, change that entry rather than appending a second lookalike. Removing a parent in some editors also removes its children; confirm the requested scope before doing so. Do not rename named destinations casually, because existing links may depend on them.

For a library route, copy the whole document through the supported preservation mechanism rather than rebuilding it from rendered pages or page objects alone. The [pypdf writer documentation](https://pypdf.readthedocs.io/en/stable/modules/PdfWriter.html) describes document cloning, `add_outline_item` and page-label operations. Check the installed version's API and destination semantics. Cloning support is a method, not a guarantee that every feature survived this file.

Save to a fresh candidate and reopen it before continuing. A failed or interrupted write must not be treated as applied; inspect the resulting file before retrying. Avoid running the same append operation twice on an uncertain candidate. Regenerate from the unchanged original and the map when that is the clearest reversible route.

## 3. Add page labels only when requested

Build an explicit range plan from observed numbering boundaries: physical start/end, numbering style, prefix, starting value and expected first/last labels. Include covers or unnumbered sections with the agreed display convention. Where printed labels are repeated, retain the ambiguity in the map or ask for a useful disambiguating prefix; do not silently invent new printed numbering.

[Adobe's page-label workflow](https://helpx.adobe.com/uk/acrobat/desktop/edit-documents/organize-pages/renumber-pages.html?screen=classic) separates a new numbering section from extending the preceding one. Its page labels affect navigation, not numbers printed on the page. Apply the chosen ranges using the actual editor/API conventions and then expand the saved label sequence to one value per physical page.

For a numeric range, set the starting number explicitly. Confirm the first and last page and both sides of every transition; an inclusive-versus-exclusive API endpoint mistake can relabel the first appendix page as body text. Preserve unaffected label ranges. Never “fix” a label mismatch by moving or deleting pages. Adding visible headers/footers is another content-editing request.

## 4. Verify saved structure, preservation and reader behavior

Reopen the exact output bytes and compare with the original and destination map:

1. **Navigation:** Reconcile every intended entry, parent, sibling order, label and destination. Resolve each saved destination to the expected physical page and heading. Check all requested page labels, including duplicate-label decisions and boundary pages. Confirm no extra duplicate bookmarks appeared
2. **Preservation:** Compare page count/order, page boxes, rotation and retained document features. Check existing outlines and named destinations outside the edit scope, links, forms and attachments. A matching bookmark count cannot show that an unrelated link was preserved
3. **Appearance:** Render original and candidate with the same settings and compare every page for a navigation-only change; inspect any differences. Check every target heading at readable size. Byte identity is not expected for an edited PDF, and one renderer's agreement does not prove every interactive feature is intact
4. **Interaction:** In the intended authorized viewer when available, open the saved file and activate the new/repaired bookmarks, including nested entries and repeated-title cases. Verify that the target heading is visible and page-label navigation selects the right page. Distinguish a real viewer check from structural API inspection

If the document is too large for complete visual or interaction coverage in the available task, state exactly which checks are complete and which are sampled or blocked. Do not call full preservation or all destinations visually verified. A viewer that ignores labels does not justify rewriting correct labels; identify the compatibility limit and retain the physical-page map.

Give the companion map a meaningful heading hierarchy, readable labels and both physical pages and logical labels. A plain-text version can still help without bookmark-panel access. It is a navigation alternative, not an accessible replacement for inaccessible page contents. If screen-reader reading or tagged-PDF conformance is required, keep that remediation/check as an explicit additional requirement.

## Recover and deliver

Correct the map or the smallest affected navigation entries, save a fresh candidate and repeat relevant checks. Wrong-page destinations usually call for mapping/index review; wrong vertical positions call for coordinate/view review; lost unrelated features call for abandoning the preservation route. Do not keep tuning navigation on a file whose content preservation failed.

Deliver the new PDF and compact contents/page map, identifying the source revision, number of entries added/repaired, label ranges changed, checks performed and viewer limits. Verify any authorized final save is the reviewed candidate. Retain the original and explain the exact blocker if only the map or a partial candidate can be completed. Publishing or sending the file remains a separate action unless already requested.

## Fictional, unexecuted example

A fictional 14-page workshop manual has a cover at physical page 1, front matter labeled `i` and `ii` at pages 2–3, body labels `1`–`9` at pages 4–12 and appendix labels `A-1`–`A-2` at pages 13–14. “Setup” begins at physical page 4 and “Troubleshooting” at page 9. An existing “Downloads” bookmark has an external destination and is outside the requested edits.

The planned copy adds “Setup,” “Troubleshooting” and an “Appendix” parent with two children, preserves “Downloads” without opening it, and assigns the agreed label ranges. “Troubleshooting” maps to physical page 9, tool index 8 and body label `6`; these are not interchangeable inputs.

Acceptance would reject a target on physical page 6, a lost external bookmark, an appendix labeled `10`, or changed page pixels. The companion map would let a reader navigate by physical page if their viewer ignores labels. This is a fictional construction plan; no PDF or viewer interaction has been executed.
