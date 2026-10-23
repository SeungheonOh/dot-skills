---
name: georeference-scanned-map
description: "Align an unreferenced map scan to evidenced geographic control, delivering a georeferenced raster and reusable control-point record with explicit fit and positional-check limits. Use for scan registration, not ordinary raster reprojection, vector digitizing, aerial orthorectification or survey certification."
---

# Georeference a scanned map

Turn a selected map image into a spatially interpretable raster without confusing a convincing overlay with established accuracy. Deliver the saved raster or agreed image-and-sidecar package, the control points needed to reproduce its placement, and a concise account of where the alignment is supported or uncertain.

Use [geospatial analysis](../analyze-geospatial-data/SKILL.md) for questions about already referenced layers, raster alignment or spatial measurements. Use [image measurement](../measure-image-features/SKILL.md) for pixel-based quantities without geographic registration. This workflow establishes a pixel-to-map relationship; it does not extract vector boundaries or turn historical cartography into a current authoritative map.

## Establish the source and intended use

Identify the exact scan/page, image dimensions and orientation, map date and any printed grid, projection, scale or datum information. Inspect existing embedded georeferencing and sidecars before treating the image as unreferenced. A misplaced layer with valid coordinates may need an interpretation repair, not a newly fitted transform.

Resolve the reference source, target coordinate reference system (CRS), requested output format, useful geographic extent and purpose. Ask for a positional tolerance only when acceptance depends on one; do not invent a universal metre threshold. An illustrative historical overlay and an input to boundary measurement need different evidence. If suitable reference coordinates are unavailable, deliver the inspected source and missing-control requirement rather than guessing from a place name or screen position.

Preserve the original. Bind all point coordinates to one working image representation: record any crop, resize or orientation change before selecting points. Points measured on a thumbnail cannot be silently applied to the full-resolution scan. Keep preparation private; opening a remote basemap, uploading imagery or sharing sensitive locations must stay within the authorized source and destination scope.

## Build an explainable control-point set

Use identifiable correspondences, such as a printed grid intersection with established coordinates or an unchanged feature in a suitable reference layer. For each point retain an ID, image position, map coordinates and CRS, reference locator, fit/check role and any ambiguity. Preserve disabled or rejected points with the reason instead of deleting the evidence behind a better-looking result.

Check the actual correspondence, not merely proximity. A road junction may have moved between map dates; a building corner and its roof edge may differ. Do not force historical features onto a modern reference when change is a credible explanation. A printed grid may support the map's intended coordinate geometry while modern landmarks answer a different ground-alignment question. Resolve that purpose before mixing the two.

Spread useful controls across the requested area, including its perimeter and interior where possible. Many points clustered around one landmark do not supply broad coverage. Avoid a nearly collinear arrangement for a two-dimensional fit. Keep unsupported margins visible; do not extrapolate the confidence of a central cluster to the whole sheet.

Verify axis order, units, datum and coordinate transcription. A map canvas may display coordinates in a different CRS from its reference layer. Record the coordinates actually passed to the fitter and their interpretation, not just the project's display CRS. Do not label all numbers with the target CRS without performing any required coordinate conversion.

Reserve suitable points as checks before fitting when enough independent correspondences exist. Do not count them as independent checks after using them to choose, tune or repair the model. If all available points are needed for fitting, report that independent positional checks are unavailable rather than manufacturing a holdout that leaves the fit unsupported.

## Choose the transformation, not just the smallest residual

Use the simplest supported model appropriate to the scan's distortions. In [QGIS's documented models](https://docs.qgis.org/3.44/en/docs/user_manual/managing_data_source/georeferencer.html#available-transformation-algorithms), Helmert permits rotation with uniform scale, first-order polynomial is affine, projective addresses planar perspective, and higher-order polynomials permit bending. Thin plate spline can match controls exactly while distorting between them. A minimum point count is not evidence of a well-supported fit.

Do not escalate model flexibility solely to reduce training residuals. Investigate a bad point's identity, transcription and reference first. Keep model choice and rejected points explainable. A photograph of uneven paper may need a better source; ordinary map registration is not a terrain/camera model for orthorectifying raw aerial imagery.

Inspect the residual pattern, not only one average. Record the units and direction of mismatches alongside any summary. QGIS supports residual display in pixels or map units; neither is automatically metres. Separate discrepancies at fitted controls, discrepancies at withheld checks and disagreement with real-world positions. Shared reference error can affect all three.

When checkpoints exist, compare transformed image locations with their withheld reference coordinates using an appropriate distance measure. State which checks cover the requested region and whether their discrepancies meet its supplied tolerance. A check derived from the same reference layer is independent of fitting, not an independent survey of that layer's accuracy. If checks fail, hold the affected use; do not silently remove the worst checks or redefine the tolerance.

## Define what the saved raster represents

Decide whether the recipient needs unchanged image samples with supported georeferencing sidecars or a resampled raster on a target grid. A world file and a warped GeoTIFF are different deliverables. Keep the CRS declaration and any required sidecars with a sidecar-based package; six positioning numbers alone do not identify the coordinate system.

Record target extent, pixel spacing and units, resampling, band interpretation, transparency/NoData and compression. [GDAL's warping documentation](https://gdal.org/en/stable/programs/gdalwarp.html) distinguishes output resolution, extent, interpolation and validity controls. Choose them explicitly rather than inheriting a tiny grid spacing or an automatic model. Bound the expected pixel count and output storage before processing. Smaller output pixels do not improve the source map's positional accuracy.

Use nearest-neighbour treatment when preserving category codes is required; smooth interpolation can create values that are not source categories. A scanned colored map is not automatically a classified raster: retain its intended image use and inspect the legibility of fine lines and text after any resampling. Do not set every zero-valued sample transparent without establishing that zero is invalid; it may be meaningful black artwork. Preserve a distinct mask or supported alpha channel where that is the agreed representation.

Write to a fresh output and save the exact point set, enabled-point states, model and settings. Record application/version and warnings. Avoid silently overwriting a previous candidate or adding output to a shared project. If a source or point set changes, create an identifiable new candidate and repeat affected checks.

## Read back placement and inspect the result

Reopen the actual saved file through a spatially aware reader, not only the still-open georeferencing session. Check its CRS, dimensions, bands, extent, transform, validity representation and the complete intended image area. Reopen the point record too and confirm that it refers to this source and candidate.

For an affine output, inspect the coordinate convention before interpreting coefficients. [GDAL geotransforms](https://gdal.org/en/stable/tutorials/geotransforms_tut.html) locate the upper-left pixel corner and include rotation terms; the first pixel centre is at image coordinates 0.5, 0.5. A [world file](https://gdal.org/en/stable/drivers/raster/wld.html) uses the upper-left pixel centre and a different coefficient order. Copying one six-number sequence into the other representation can shift or distort placement. Check several known image positions, not just the upper-left origin.

Inspect the saved raster against the selected reference at readable scales, with controls and withheld checks distinguishable. Review the centre, edges, corners and any region remote from controls for drift, reversed axes, unexpected bending, clipped content or invalid borders. Check text and line appearance separately from positional agreement. A screenshot can reveal a problem but does not replace the saved transform and point evidence.

If only metadata or point inspection is available, report that narrower result. A complete claim needs the relevant saved-file and alignment checks; an exporter success message, a zero fit residual or an image opening without error is insufficient. Do not claim survey accuracy, cadastral authority, safe navigation or current physical access from this derivative.

## Handoff and stopping point

Return the candidate and necessary companions, source identity, reference provenance, target CRS, model/grid choices, control/check counts, observed discrepancies and held regions or uses. Include the meaningful accepted/rejected-point decisions, not an unnecessary copy of every private reference dataset. State preparation, readback and positional acceptance separately.

On failure, retain the source and point record, identify the actual mismatch and regenerate only after correcting its cause. Do not recover by relabeling coordinates, deleting failed checks or overwriting a usable earlier version. Stop when the requested registration and its stated checks are complete, or name the missing control, reference or acceptance decision. Publishing a web layer, digitizing features, uploading the map or changing another project remains separate work.

## Fictional illustration, not executed

An invented town-map scan has eight identifiable grid intersections. Six distributed points are selected for an affine fit; two are reserved as checks. The requested use is a historical display overlay, not parcel measurement. The eastern sheet edge lies beyond the reliable controls.

Suppose a candidate report shows small fitted residuals but a large east-side checkpoint discrepancy. The proposed disposition is to hold that region, inspect the point/reference interpretation and source distortion, and preserve the failed check. Switching to a flexible model and consuming that checkpoint as another control would remove its independence, not prove the region accurate. The unsupported outer margin remains labeled even if the central overlay is useful.

These are authored decisions and hypothetical findings only. No scan was processed, GIS application opened, transform fitted, raster exported, positional check executed or map published for this illustration.
