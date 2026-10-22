---
name: stitch-photo-panorama
description: "Combine an authorized overlapping photo set into a panorama with an editable stitching project, deliberate projection and crop, and inspected seams. Use for photo-derived panoramic imagery, not image generation, photogrammetry, map orthorectification, HDR merging or hosting a virtual tour."
---

# Stitch overlapping photos into a panorama

Deliver a saved panorama derived from the supplied photographs, together with the stitching project when requested and a short account of coverage, corrections and unresolved defects. A successful alignment or attractive small preview is not a finished stitch.

[create-visual-asset](../create-visual-asset/SKILL.md) covers general artwork creation and bounded image edits. [photo-selection-caption-review](../photo-selection-caption-review/SKILL.md) covers selecting existing photos and grounding captions. This workflow adds multi-image correspondence, projection, overlap masks and seam review. [prepare-print-production-package](../prepare-print-production-package/SKILL.md) handles a later printer-specific production contract; a large panorama alone is not print approval.

## Establish the intended image

Use the request and available files to identify:

- Exact source set and permitted exclusions, whether originals or previously processed copies are available, and any source that must remain represented
- A flat panoramic picture versus a spherical image for a named viewer; intended framing, important subjects and acceptable crop
- Output format, dimensions or practical size limit, transparency needs, and whether editable project/source handoff is required
- Known capture conditions, lens changes, exposure brackets, prior crops or corrections, and areas containing movement
- Whether ordinary alignment, blending and tonal matching are intended, versus a documentary use that requires stricter disclosure or prohibits removing a subject

Ask only for missing choices that materially affect the result. Do not demand capture settings before inspecting an ordinary set. Preserve unknown metadata as unknown. With no usable overlap or missing central views, return a coverage finding rather than inventing connecting scenery.

Use an available supported stitching application. The Hugin documentation below supplies a concrete reference, not a requirement to install Hugin or to assume its historical tab names match the current interface. If the environment has no stitching capability, prepare the source/coverage plan and report that no panorama was rendered. Do not upload private photographs to a third-party stitching service without authorization for those files and that destination.

## 1. Preserve and understand the source set

Keep originals unchanged and create a separate project/output location. Map each input to its exact filename/version; distinguish alternate captures, exposure brackets and duplicates. Inspect full images rather than relying only on filenames or thumbnails. Note orientation, pixel dimensions, lens/projection metadata when available, missing borders, severe blur and areas whose content changes across shots.

Build a simple overlap map: which views share identifiable static scene features, and which views form a connected sequence. Include a first/last overlap only if those photographs actually meet. A numbered series can contain a missing view, while nonadjacent filenames can overlap.

Check whether the source was cropped or lens-corrected before import. Do not assume surviving EXIF still describes the transformed pixels. Hugin's [overview](https://hugin.sourceforge.io/tutorials/overview/en.shtml) explains the relationship between source field of view, lens information and alignment, and warns about repeated patterns and foreground parallax. Use supplied capture information or a supported model-estimation route; do not manufacture a focal length or label an estimated lens value as measured.

A rotational landscape panorama, a translated close-up document mosaic and an aerial mapping task are not interchangeable. If perspective changes cannot be represented by the chosen stitcher's model, explain that limit. Do not claim survey accuracy, dimensions, seamless reconstruction of unseen surfaces or a metrically correct map from a decorative panorama.

## 2. Align corresponding features before blending

Import only the selected sources. Set the actual input lens type and group parameters only for images that share the applicable camera/lens setup. Distinguish an anchor for geometry from any exposure/color reference. Keep a recoverable project before major alignment changes.

Create automatic matches where supported, then inspect weak or surprising connections. A normal correspondence must identify the same static feature in both images. Repeated windows, moving foliage, reflections and a person who moved between frames are not interchangeable anchors. Distribute usable matches across overlaps rather than concentrating every point on one tiny patch.

Hugin's [control-point guidance](https://hugin.sourceforge.io/docs/manual/Hugin_Control_Points_tab.html) distinguishes point correspondences used to match images from line constraints used to orient the output. Do not use the two ends of a vertical line as though they were the same scene point in two views. Add or correct only matches supported by the actual photographs.

Run the supported geometric alignment and inspect the result. Review individual outliers and disconnected views, not only a mean error or a green status. Improve a clearly incorrect match; do not delete inconvenient correct matches simply to lower a score. Compare the disputed region in both originals when foreground and background cannot align together.

Treat persistent parallax as an input/model limitation, not a reason to keep adding increasingly flexible correction parameters. Options include an authorized smaller crop, a different subset with genuine coverage, a carefully chosen seam where geometry allows, or a request for a replacement capture. Preserve the unresolved defect when none meets the requested scene fidelity.

## 3. Choose projection, leveling and crop together

Select the output geometry for the intended viewing mode. Hugin's [stitcher reference](https://hugin.sourceforge.io/docs/manual/Hugin_Stitcher_tab.html) describes rectilinear output for narrower views, cylindrical output for wide panoramas and equirectangular output for spherical coverage. Rectilinear projection cannot encompass a 180-degree field in either axis. Do not force a wide sweep into it merely to keep a rectangular canvas.

Preview the chosen projection and center direction. Check important structures, horizon and edge stretching. Level from trustworthy scene features rather than assuming that every roofline is horizontal or every natural feature is vertical. If preserving one structure would materially distort another, present that tradeoff instead of asserting that one view is objectively undistorted.

Set the crop after alignment and projection. Check its actual retained content, not just the automatic crop result. Do not crop away a required subject to hide a seam without resolving that change. Where coverage ends, keep an agreed transparent boundary or use an authorized tighter crop. Generative fill, cloned scenery and content-aware extension are separate content changes, not routine stitching.

For spherical delivery, verify complete required angular coverage, the wrap boundary and any pole coverage required by the target viewer. A 2:1 rectangle or an equirectangular setting does not prove that the camera captured a full sphere. If only a partial scene exists, label its coverage honestly and use a supported partial-panorama delivery rather than stretching it to pretend completeness.

## 4. Resolve seams and tonal transitions deliberately

First separate geometry defects from brightness/color differences. Hugin's [Photos tab documentation](https://hugin.sourceforge.io/docs/manual/Hugin_Photos_tab.html) distinguishes geometric alignment from photometric adjustment. A bright stripe may need tonal work; a doubled railing needs a geometry or seam decision. Blending is not proof that either is correct.

Use supported exposure/white-balance matching when the request allows ordinary photographic normalization. Retain a sensible reference and inspect sky gradients, neutral surfaces and highlights afterward. Hugin's [exposure guidance](https://hugin.sourceforge.io/docs/manual/Hugin_Exposure_tab.html) explains its exposure, white-balance and vignetting controls; inferred correction parameters are not measurements of the actual lighting. Do not claim clipped detail was recovered or that color is calibrated because transitions look smoother.

Do not enable exposure fusion or HDR merging solely because neighboring frames have different brightness. If the input contains deliberate brackets and that result is requested, resolve the stack/merging workflow separately. Ordinary overlapping views are not automatically exposure stacks.

For moving content, choose a coherent supported source region, consistent with the user's intended representation. Avoid half a person, duplicate limbs, discontinuous vehicles or repeating waves caused by a seam. Do not silently remove an important subject in a documentary image.

Use inclusion/exclusion masks where supported, and confirm that another input covers a region before excluding it. Hugin's [mask documentation](https://hugin.sourceforge.io/docs/manual/Hugin_Mask_tab.html) warns that blend masks guide seam placement rather than guaranteeing a literal cutout, and that excluding uncovered content creates holes. It also distinguishes masks from control-point removal: existing matches in a masked region can still influence geometry. Inspect both the final blend and the alignment constraints after mask changes.

## 5. Render and inspect the saved deliverable

Save the project and render a new candidate to a fresh filename. Choose output dimensions appropriate to actual source detail and the requested use, not simply the largest permitted canvas. Record the application/version, projection, crop, format and any material corrections. A successful render message does not show whether the output contains the intended content.

Reopen the exact saved file. Inspect the whole composition at intended viewing size, then examine all overlap/seam regions at a useful pixel-level view. Pay particular attention to:

- Doubled, bent or interrupted edges, rooflines, fences and readable signs
- Moving subjects, reflections, repetitive textures and areas affected by masks
- Exposure bands, color jumps, halos, softened regions and sky transitions
- Crop edges, missing coverage, unexpected opaque fill and transparency if requested
- Final dimensions, format, profile handling and the required subject coverage

For a spherical deliverable, also inspect in the intended supported viewer, including the wrap seam and required poles. If viewer use is unavailable, distinguish a checked flat export from untested spherical presentation. Do not upload or host a tour just to perform that check without authorization.

If an output fails, return to the saved project and correct the implicated alignment, mask, tone or crop choice. Regenerate a new candidate and recheck affected seams plus the overall composition. Do not keep touching up a failed flattened image until its connection to the project is lost. Unsupported repairs remain explicit limitations.

When editable delivery is requested, confirm the project opens from the handed-off location and resolves its permitted source dependencies. A project file may reference photographs rather than contain them. Package only the requested authorized sources, preserving useful paths or using the application's supported packaging route. Do not replace missing inputs with similarly named files or include the rest of the user's photo library.

## Handoff and stop conditions

Return the panorama and, when requested, the editable project with necessary permitted dependencies. Keep the note short: source set, final projection/coverage, dimensions/format, meaningful crop or mask choices, checks performed and remaining limitations. Describe it as a stitched composite rather than a single exposure when that distinction matters.

Finish when the saved image meets the requested framing and file contract and the meaningful seams have been inspected, or when a specific missing source, capability or decision blocks that result. A partial usable crop may be offered without claiming it fulfills a wider requested scene. Separate local file preparation from recipient delivery, publication and viewer acceptance. Do not claim an unchecked image is seamless, a preview is color proof, or metadata is privacy-clean without the corresponding evidence.

## Fictional, unexecuted illustration

An invented set contains five overlapping photographs of a harbor wall. The requested result is a flat banner retaining both a red gate at the left and a lighthouse at the right. A cyclist moves across the middle overlap; a foreground railing shifts relative to the distant skyline. The sources do not cover a full circle.

The expected approach is to inspect the static overlap chain, avoid using the moving cyclist as an alignment feature, and compare projection/crop choices while retaining both required landmarks. If an alternate frame covers the cyclist's region coherently, a permitted mask can guide the seam there, but the saved blend still needs inspection. A low alignment score does not clear the railing if it remains doubled. If only a tighter crop removes the defect and that crop loses the gate, the banner remains held for the user's tradeoff rather than being labeled complete.

The expected handoff would identify partial horizontal coverage and the exact exported candidate; it would not call a wide rectangle a 360-degree tour. This is an authored decision example only. No photographs, stitcher, project, render, viewer, upload or seam inspection was executed for it.
