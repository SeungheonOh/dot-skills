---
name: validate-svg-print-geometry
description: "Check a supplied generated SVG for physical page size, geometric bounds and independent render behavior before print handoff."
---

# Validate SVG print geometry

## When to use

A vector export looks correct in one preview but needs a reproducible check for intended paper size, margins and paths.

## Required inputs

- The authorized SVG and intended page dimensions/units
- Margin and clipping expectations, including stroke widths
- A permitted independent renderer and output destination

## Workflow

1. Inspect physical width/height, viewBox and coordinate transforms. Distinguish millimeters from user units and avoid assuming a screen pixel equals a physical print unit.
2. Compute or inspect path and stroke bounds under the actual transforms. A centerline inside the margin can still put half its stroke outside; state which bound is being tested.
3. Check for external resources, scripts and missing fonts. Do not execute active SVG content or fetch referenced private resources simply to render it.
4. Render with an independent suitable renderer and inspect actual pixels for clipped paths, missing labels and unexpected scale. A successful XML parse is not visual verification.
5. Return the unchanged original or an explicitly requested corrected copy, plus the page/margin result and unsupported renderer features. Physical printer scaling remains a separate check.

### Separate geometry, rendering and physical output

List the properties being checked and the method for each: physical page size from SVG dimensions, geometric bounds from path/transforms, stroke extents from style, and visible output from the independent renderer. Unsupported filters, clipping or font substitution should create an explicit gap rather than a blanket pass.

Do not render a supplied active SVG in a context that executes scripts or resolves external resources. Use an appropriate restricted renderer, and preserve the original if a corrected copy is requested. Name any unit conversion and avoid silently fitting the result to a new page.

### Resolve the page mapping before measuring margins

Resolve the effective outer viewport size, including relevant CSS or embedding overrides; percentage-only sizing without a known container does not establish a physical page. Carry the viewBox origin, `preserveAspectRatio` alignment and nested transforms into page coordinates. With `meet`, unequal aspect ratios leave unused space; `slice` can extend content outside the viewport; `none` can scale the axes differently. Do not infer one millimeter per user unit from a matching width alone. The [SVG viewport transformation rules](https://www.w3.org/TR/SVG2/coords.html#ComputingAViewportsTransform) define this mapping. If the page reference remains unresolved, report the supported user-space bounds and hold physical-margin conclusions.

A path-coordinate box expanded by half the stroke width is not a general painted-bound calculation. Include end caps, joins and their miter limit, markers and any applicable vector effect; [SVG stroke and marker rules](https://www.w3.org/TR/SVG2/painting.html) explain why these can extend or change the visible shape. Nonuniform transforms and `non-scaling-stroke` require their actual stroke behavior. Identify whether a reported box includes fill, stroke and markers, and whether it is before or after clipping. A clipped preview may hide an out-of-margin object; if unclipped content is required, clipping is not a correction. Leave unsupported extents unresolved rather than silently dropping the decoration.

Fictional, unexecuted illustration: a standalone 200 mm by 100 mm page has viewBox `10 20 100 100`, default `xMidYMid meet`, no sizing overrides and no other transforms. Uniform scale is 1 mm per user unit, with 50 mm of unused space at each horizontal side. The point (10,20) maps to page position (50,0) mm, not (10,20) mm. A margin check must use the mapped position and painted extent. This is a paper reasoning example; no SVG was generated, rendered or printed.

## Output

A print-geometry report and preview with exact page units, tested bounds and remaining renderer/printer limitations.

## Verification and limits

Check at least one known-dimension shape, full page bounds and stroke extents. Do not claim physical print fidelity from a screen preview alone.

## Suggested handoff fields

Page size and units; viewBox; tested objects; centerline and stroke bounds; external-resource policy; renderer/version; visible anomalies; physical-print checks not performed.

## Worked example

A fictional SVG declares 210 mm×297 mm with viewBox 0 0 210 297. A line’s centerline lies at x=18 and has a 2 mmstroke. Its leftmost stroke extent is 17 mm, so it does not satisfy an 18 mmprinted-content margin even though the centerline does.

The review reports “centerline margin 18 mm; visible stroke margin 17 mm.” If the user permits a correction, moving the line center to 19 mmrestores an 18 mmleft stroke margin, subject to checking its other bounds.

An independently rendered preview can corroborate clipping and placement. It cannot prove that a physical printer will use 100%scale or preserve color; those remain separate checks.

## Evidence status

The worked example illustrates the stated inputs and reasoning. Unless an execution result is explicitly identified, it is not a claim that external services, real devices or user data were tested. Report actual checks and unrun stages on each use.
