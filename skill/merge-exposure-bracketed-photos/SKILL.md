---
name: merge-exposure-bracketed-photos
description: "Merge an authorized exposure-bracketed photo set into a source-derived HDR master and a deliberately rendered delivery image. Use for retaining highlight and shadow detail across exposures, with alignment and deghost review; not focus stacking, panoramas, synthetic detail recovery or HDR video conversion."
---

# Merge exposure-bracketed photographs

Deliver a saved exposure merge and the requested viewing copy, with enough source and processing information to distinguish recovered photographic detail from tonal interpretation. Merging a bracket, making an attractive SDR image and delivering an HDR-display image are different outcomes. Do not substitute one for another because each may be called “HDR.”

[blend-focus-bracketed-photos](../blend-focus-bracketed-photos/SKILL.md) combines changing focus distances; [stitch-photo-panorama](../stitch-photo-panorama/SKILL.md) combines overlapping views. This workflow combines exposures of substantially the same composition. Use [create-visual-asset](../create-visual-asset/SKILL.md) for a requested artistic or generative edit rather than presenting invented detail as a photographic merge.

## Establish the delivery and source contract

Identify the supplied bracket, important highlight/shadow regions, allowed crop, intended appearance, output dimensions/format and whether the user needs a merged master, an ordinary SDR viewing copy, a named HDR-display delivery, or a combination. Use the request and existing files first. Ask only where a missing choice materially changes the result, especially a documentary restriction or an unspecified HDR destination.

Check that the available application supports the actual inputs and requested merge/export. The Adobe references below provide a concrete route, not an instruction to buy software or assume an installed edition. If processing is unavailable, return source findings and the proposed handoff, clearly stating that no merge was made. An online processing service or cloud-synced import must not receive private photographs without authorization for those files and destination.

## 1. Decide whether the bracket contains the needed information

Preserve originals and work separately. Identify exact source filenames/versions; separate alternate compositions, repeated attempts, focus brackets and previously merged images. Inspect photographs and capture metadata together. Consecutive filenames do not establish a bracket, and a metadata exposure offset alone does not establish usable detail.

For each important bright and dark region, locate a source that actually shows the required texture or wording. Distinguish a clipped preview rendering from irretrievable source clipping by inspecting the available raw data through the supported development application. Do not claim all highlights are lost based only on an embedded thumbnail. Equally, lowering brightness on a featureless bright patch does not prove detail was recovered.

Adobe's [bracket guidance](https://helpx.adobe.com/lightroom/desktop/edit-photos/hdr-panorama.html) emphasizes covering scene regions with usable exposures rather than maximizing frame count. Choose the smallest useful supported set without discarding the only frame that resolves a required region. If one exposure already meets the brief, a single-source development may be preferable; label it honestly rather than manufacturing a merge requirement.

Inspect focus, blur, framing, white-balance changes, moving subjects and changing illumination. A long exposure may contain shadow information but blurred leaves; a short exposure may preserve a window but not the room. Check whether changed aperture or focus produces incompatible depth-of-field regions. Keep unknown capture settings unknown instead of inventing exposure values to satisfy an importer.

Do not create a supposed bracket by exporting several brightness variants from the same photograph. Those variants do not introduce independently captured highlight or shadow information. If all usable sources lack required detail, report that source limitation and offer a narrower deliverable or replacement capture.

## 2. Merge without confusing alignment, tone and motion

Use original supported raw inputs when available. If conversion is necessary, preserve the originals and document the compatible working copies and development choices. Avoid independently applied crops, local tone edits or inconsistent corrections that impede correspondence. Renaming a rendered file to a raw extension is not conversion.

In [Lightroom Classic's documented procedure](https://helpx.adobe.com/lightroom-classic/desktop/process-and-develop-photos/hdr-photo-merge.html), select the bracket and choose Photo > Photo Merge > HDR. Auto Align addresses small inter-frame displacement; Auto Tone supplies an initial tonal rendering. Keep those decisions separate. Adobe recommends starting with low deghosting when needed, increasing only for remaining motion artifacts, and leaving it off when unnecessary. Inspect the overlay when useful. The merge creates a DNG; retain the source bracket as well.

Inspect stable features across the candidate, including both foreground and background. A sharp central edge does not clear displaced near objects or an alignment crop that loses a required boundary. Distinguish:

- Doubled static edges: investigate registration, viewpoint changes and incompatible input corrections.
- Transparent or repeated moving objects: investigate ghosting and the selected representation of motion.
- Missing texture in an otherwise coherent region: compare the contributing sources before changing tone controls.
- Haloed edges or implausibly bright shadows: inspect the rendering choices as well as the merge.

If a subset aligns better, recheck its exposure coverage before accepting it. Do not cure a doubled window frame by dropping the only exposure with readable exterior detail and then claim full coverage.

## 3. Resolve motion with a coherent source choice

Compare the deghosted region against the actual exposures. Review moving people, foliage, water, flags, reflections and transitions around the corrected area. A less visible ghost can still leave an interrupted limb, repeated object, unexpected color patch or noisy region.

Where the application permits a reference/source choice or source-based mask, select a coherent supported moment and inspect its boundary. Do not assume every merge application exposes the same controls. If a local correction requires another editor, preserve a recoverable working file and identify the source used for the material repair.

Do not silently remove an important subject, switch a sign's wording or alter evidence of an object's condition to make the blend easier. If the only faithful moving-subject source lacks the requested tonal detail, explain the tradeoff. An acceptable single exposure can be offered as an alternative, not mislabeled as a fully resolved HDR composite. Unresolvable motion or parallax is a stop condition when it prevents the requested fidelity.

## 4. Render for the actual viewing path

Preserve the merged master before producing a delivery derivative. Adjust overall tone and local contrast to the intended appearance; compare required regions against their source support. Making every shadow bright and every highlight dark is not itself a correctness goal. Avoid halos, unnatural edge contrast, loss of highlight color or exaggerated noise that obscures the subject.

For ordinary SDR delivery, deliberately render the merged information into the requested SDR file and profile. For HDR-display delivery, establish the destination's supported encoding, color handling and viewing path rather than picking a filename extension by reputation. Wide gamut, high sample depth and high dynamic range are distinct properties; none alone proves the others.

Adobe's [Camera Raw HDR output guidance](https://helpx.adobe.com/camera-raw/desktop/hdr-and-advanced-output/hdr-output.html) separates HDR merging from HDR output and documents compatible-display requirements, export controls and an SDR preview. It also notes that its merge dialogs do not display HDR even when the main image view can. Inspect the final rendering in the appropriate view, not solely the merge preview. Check current application and destination support instead of assuming any listed format renders as HDR everywhere.

If an HDR viewing path is unavailable, distinguish file preparation from visual HDR verification. Provide an SDR companion only when requested or agreed, clearly labeled so it cannot be mistaken for the HDR master. Do not describe an ordinary screenshot as proof of HDR brightness or recipient-device behavior.

## 5. Inspect the saved outputs and hand off

Reopen the exact exported file rather than relying on the unsaved editor view. Confirm the format, pixel dimensions, crop, profile/output mode and the intended file's location. Review both intended viewing size and useful detail magnification:

- Required bright and dark regions remain supported and legible where the sources permit.
- Static edges align; moving content and corrected boundaries remain coherent.
- Tone transitions have no distracting halos, banding, abrupt color changes or unjustified detail loss.
- Required scene boundaries survive crop and alignment.
- The delivered viewing copy has the intended SDR or HDR behavior on the path actually checked.

If editable delivery is requested, confirm what editability survives: a merged DNG is not a layered document with individually adjustable source masks. Include only requested, authorized dependencies and settings. Keep the source bracket and master recoverable; a flattened viewing export is not a replacement for either.

Return the selected files with a short note naming the bracket, merge application/version, material exclusions or motion choices, master versus viewing-copy roles, checks performed and limitations. Identify the result as a multi-exposure composite where that matters. Finish when the saved outputs meet the agreed contract, or when a specific missing source, capability or decision blocks them. Local export, HDR display review and external publication are separate claims.

## Fictional, unexecuted illustration

An invented three-exposure room bracket must retain a wall inscription and the view through a window. The shortest exposure supports the exterior; the longest reveals the inscription but blurs a curtain. The requested deliverable is an ordinary SDR listing image, not an HDR-display file.

The expected approach is to retain complementary exposure coverage, inspect the curtain's coherent source options and render a separate SDR copy from the merge. If the curtain cannot be represented without losing a required detail, that tradeoff stays unresolved rather than being hidden by aggressive deghosting. A bright SDR preview does not prove HDR-display delivery, and the resulting file is not evidence that an online listing accepted it.

This is an authored decision illustration only. No photographs, merge, deghosting, tonal edit, export, file reopening, display review or publication was executed for it.
