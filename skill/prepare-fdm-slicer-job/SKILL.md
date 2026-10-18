---
name: prepare-fdm-slicer-job
description: "Prepare a bounded single-material FDM/FFF print job in an existing desktop slicer, bind approved geometry to the intended printer and material profiles, and deliver a reopened project plus checked local toolpath export. Use for slicing preparation, not model design, printer calibration, resin printing, machine operation or physical-safety approval."
---

# Prepare a model-specific slicer job

Turn an approved benign model into a revisitable slicer project and a local printer-specific instruction file. The useful result preserves the model's intended size and features while making orientation, supports, effective settings and unresolved print assumptions explicit. A solid-looking model preview is not evidence that its sliced layers contain those features.

Use [create-3d-asset](../create-3d-asset/SKILL.md) for modeling, [review-parametric-part-fit](../review-parametric-part-fit/SKILL.md) for supplied dimensional relationships, and [prepare-dimensioned-part-drawings](../prepare-dimensioned-part-drawings/SKILL.md) for human-readable part drawings. This workflow owns the separate transformation from established geometry and supported machine settings to a reviewed slicing project and local toolpath candidate.

## Establish the preparation contract

Limit the job to one build plate, one filament material and one extrusion tool, printing ordinary benign objects layer by layer. Examples include decorative shapes, desk-organizer inserts and visual prototypes. Exclude weapons, dangerous devices, safety-critical or load-bearing parts, medical devices, protective equipment and claimed food-contact or electrical suitability. Multi-material jobs, sequential object-by-object printing, resin workflows, firmware changes and physical printer operation need a different scope.

Find the available evidence before asking for missing inputs:

- Exact model revision, intended units and one known dimension; selected objects and required copy count
- Printer model and relevant hardware configuration, including nozzle diameter/type, build surface and available build volume
- Intended filament identity and an applicable existing supported printer/filament/print profile combination
- Installed slicer version, any existing project to preserve, and the output format supported by the intended printer/firmware route
- Important visible faces, small details, holes or clearances to preserve, permitted orientation changes, and any supplied time/material limits
- Approved local output folder and whether the request is for a review project only or also a printer-specific toolpath file

Do not choose a near-enough printer profile from a similar bed size. If machine or material identity is unresolved, prepare the useful geometry review and questions, but hold toolpath export. A requested quality/time tradeoff can usually start from an applicable vendor profile; it does not require inventing temperatures, acceleration limits or extrusion settings.

Work in new files and preserve the original model, earlier project and unrelated presets. Use the existing authorized desktop application; this guide does not grant computer access, installation authority or permission to upload private designs. Keep the destination local and outside watched printer queues. Do not connect, send to a printer/cloud service, heat, home, move axes, calibrate or start printing under this preparation task.

## 1. Start from known geometry and effective settings

Record source identity, slicer version and the selected profile identities. Save another open job before replacing its workspace. Distinguish geometry imports from project imports: a PrusaSlicer 3MF can bring printer, filament and print settings with it, not only shapes. Consult the installed version's import behavior; the [PrusaSlicer introductory route](https://help.prusa3d.com/article/first-print-with-prusaslicer-3-0-0_1079761) makes this replacement explicit, but its 3.0 interface is not a menu map for older releases.

For received projects, use a supported geometry-only route when their configuration is not trusted or applicable. Preserve object relationships and disclose settings intentionally not carried over. Do not blindly accept a bundled profile, substitute a newer model or enable a suggested plug-in. If the tool cannot separate the needed geometry from unreviewed executable behavior, stop at that input and request an appropriate geometry export.

Before slicing or exporting, inspect the effective configuration for post-processing commands, custom machine instructions, per-layer actions and unexpected network destinations. Keep this workflow on existing supported machine profiles without additional scripts or machine-code edits. In PrusaSlicer, [post-processing scripts](https://help.prusa3d.com/article/post-processing-scripts_283913) run programs and modify the generated file; an ordinary export is therefore not necessarily passive. Hold unexpected scripts or required custom behavior rather than running it or silently removing a dependency and claiming equivalent output.

Compare imported overall dimensions with the known source dimension. Resolve unit/scale differences before placement. Do not use automatic fit-to-bed scaling to disguise an oversized part, and do not infer size from the viewport zoom. Distinguish independent objects, multipart components, copies, negative volumes and modifier meshes; a modifier is not necessarily another item to fabricate. Retain source-to-object correspondence and the intended count.

Inspect reported mesh issues and missing parts. A repair message alone does not establish preserved geometry. If a supported local repair is within scope, keep a separate candidate and compare the affected openings, walls and dimensions afterward. Structural edits, cutting the model, adding joints or changing a dimension need the user's design intent; do not make them merely to obtain a successful slice.

## 2. Choose orientation and placement deliberately

Compare only orientations that matter to the task. Weigh first-layer contact, unsupported regions, visible-face quality, access for support removal and preservation of fine features. State an unresolved tradeoff instead of promising a strongest or flawless orientation. Digital slicing cannot establish physical strength or dimensional fit.

Use the intended face as the base, then inspect actual contact in the layer preview. PrusaSlicer's [Place on Face tool](https://help.prusa3d.com/article/place-on-face-tool_1781) aligns a selected plane to the bed; it does not prove the selected face was the intended one or that the whole object has a useful first layer. Check for tilted contact, floating components and geometry sunk below the bed. Moving an object through the bed can omit geometry from the job.

Place the requested copies without overlaps, within the selected machine's usable region. Account for the generated support, brim/skirt and other profile-generated paths, not just model bounding boxes. Preserve critical separations and the approved copy count. Stay in ordinary all-objects layer-by-layer mode; do not enable sequential printing to save time or avoid travel, because its head-clearance problem changes the task.

If a model does not fit at the required scale, return the exact incompatibility. A different orientation may be an acceptable preparation choice; scaling, splitting, changing the printer or dropping a copy is a separate decision when it changes the brief.

## 3. Set the small number of controls that change the result

Begin with the applicable existing profile combination and record deviations, including object- and height-range overrides. A visible global value may not be the value used for every region. Do not overwrite a shared preset just to preserve one job; use the native project or a separate scoped preset when needed.

Choose layer height within the selected nozzle/profile's supported range and the user's detail/time priorities. Inspect small XY features separately: a smaller layer height does not itself recover narrower lettering or holes. The [layers and perimeters reference](https://help.prusa3d.com/article/layers-and-perimeters_1748) distinguishes vertical resolution, shell paths and top/bottom layers. Do not turn a rule of thumb into a universal machine limit or claim strength from infill percentage alone.

Keep perimeter, top/bottom and infill choices coherent with the intended shape. Examine whether small walls disappear or merge and whether a nominally closed top actually receives covering paths. Do not silently enable vase mode, hollow a solid or remove top/bottom layers for a quicker estimate. Those choices can change the object the user requested.

Choose support scope after orientation. Automatic supports, build-plate-only supports and marked enforcers have different reach. [Prusa's support documentation](https://help.prusa3d.com/article/support-material_1698) distinguishes those modes. Check whether generated support reaches the intended underside and whether it would be trapped inside a closed cavity. A painted support mark is not evidence of an actual support toolpath. Preserve intentional bridges only when the applicable process guidance and requested quality support that choice; do not label every gap a defect or assume every span will bridge successfully.

Use applicable preset guidance for adhesion aids and support interfaces rather than universal distances or temperatures. If supports would mark a protected face, or a required feature cannot survive the chosen process settings, report the tradeoff and hold the affected acceptance decision. A pleasant outer preview cannot waive it.

## 4. Slice and inspect the layer sequence

Slice the current candidate, capture warnings and confirm they concern the intended model/profile combination. Classify each warning as resolved with evidence, knowingly outside the accepted requirement, or still blocking. Do not dismiss all warnings or suppress a machine mismatch to reach export.

Use the sliced-path view rather than only the model view. Inspect the whole sequence with the layer slider and look closely at the first layer, the start of disconnected regions, bridge/support transitions, small text or walls, hole closures and top surfaces. Check:

1. Correct object count, overall dimensions, placement and complete intended height
2. Intended first-layer footprints and no unnoticed below-bed truncation
3. New regions connected to earlier geometry, supported by generated paths, or explicitly reviewed as bridges
4. Preserved openings, walls and visible details in actual extrusion paths
5. Supports and adhesion paths within the usable region, with no unexpected material/tool changes or per-layer actions

Record a few useful layer heights or views where the decisive findings appear. This is not a requirement to save hundreds of screenshots. Distinguish a warning-free slice, inspected path continuity and any unresolved physical assumptions.

Read the slicer's material and duration estimates for this exact candidate. Include support and adhesion consumption as represented by the tool; do not count only the model volume. An estimated mass, time or cost is not a measured print result, a guarantee of spool sufficiency or a purchase quote. If a limit is exceeded, vary an authorized choice and compare the new paths and estimate. Do not hide the shortfall by deleting features or selecting unsupported speeds.

Any change to source geometry, orientation, copies, profiles or overrides invalidates affected preview findings. Slice again and repeat the relevant checks before retaining an accepted candidate.

## 5. Save the project and check the exact export

Save the requested native project under a new, descriptive name and reopen it. Reconcile the source objects, scale, placement, profiles, overrides and support settings. In PrusaSlicer, [Save Project as 3MF](https://help.prusa3d.com/article/saving-projects-as-3mf_1773) retains objects, settings and modifiers; a plate exported as STL is not a substitute for that project. Record the slicer/profile versions because a later re-slice is not guaranteed byte-identical across software changes.

Select a local file destination explicitly. Inspect the actual action and path immediately before export: a remembered network destination may instead send the job elsewhere. Do not select an upload-and-print route or use physical-printer connection setup as a way to save a local file.

Match the output encoding to the established consumer route. [Binary G-code](https://help.prusa3d.com/article/binary-g-code_646763) requires compatible printer firmware and may also depend on intervening software. Renaming a binary file to a text extension does not convert it. If compatibility is unknown, hold the export decision; do not update firmware or install a bridge to force acceptance.

Open the exact saved instruction file in an available supported local G-code viewer, not through a connected printer host. Check that it is the new file, its reported printer/material/settings agree where exposed, and its layers, count, extent and critical features match the accepted preview. This saved-file readback matters even when export reports success. Prusa's [G-code viewer](https://help.prusa3d.com/article/prusaslicer-g-code-viewer_193152) interprets external files but can lack information and uses the same preview implementation as the slicer; it is not an independent machine-safety validator.

Do not infer complete firmware behavior from rendered extrusion paths. Uninterpreted commands, unsupported annotations or an unexplained difference between project and exported file require a hold. When an applicable viewer is unavailable, deliver the project and clearly marked unverified export only if that partial handoff is useful; do not call the toolpath checked.

Keep credentials and unrelated configuration out of delivery. PrusaSlicer's [profile export documentation](https://help.prusa3d.com/article/how-to-import-and-export-custom-profiles-in-prusaslicer_382766) notes that a bundle with physical printers includes an API key and IP address. Do not attach such a bundle. Inspect project metadata and saved source-path disclosures before any separately authorized sharing.

## Handoff, acceptance and recovery

Deliver the native project, the exact local toolpath file when requested and supported, and a compact note identifying:

- Model revision/count/size; intended printer, nozzle, surface and material; slicer and profile identities
- Orientation, support policy and meaningful deviations from the base profiles
- Decisive preview and reopened-file checks, warnings and estimate limits
- Remaining decisions and the explicit boundary that no printer was operated or physical part verified

Report project prepared, project reopened, exported file inspected and physical print observed as separate states. Completion for this guide is a consistent preparation package with honest holds, not a guarantee of adhesion, strength, tolerance, safety or successful fabrication. An actual print requires its own authorized operator procedure and checks.

If slicing fails or required details vanish, preserve the source and last known-good project. Narrow the problem to geometry, effective settings or an unsupported feature; make only permitted changes and re-slice. Do not install repair software, send geometry to an online service or run arbitrary post-processing as an automatic recovery.

After an interrupted or uncertain save/export, inspect the destination before retrying. Keep partial or obsolete candidates distinct from the accepted output, and do not overwrite concurrent work. When a profile changes after review, reconcile the effective settings and repeat affected slicing/readback rather than relying on an unchanged preset name.

## Fictional, unexecuted illustration

A fictional user requests a slicer project and local toolpath for two copies of an approved decorative tile, each 60 by 40 by 3 mm, with shallow lettering on its top face. They supply their printer/nozzle/material identities and an applicable installed profile. The model size, copy count and lettering are locked; orientation and ordinary support choices may change.

Suppose an authored review scenario says the flat-back orientation yields the intended footprints, but the sliced preview omits one narrow letter stroke. Lowering layer height alone would not establish that this XY feature is restored. The affected feature remains held while an allowed profile choice is investigated; widening the lettering or scaling the tile would require a design decision. The two matching model thumbnails cannot override the missing path.

If that issue is later resolved within scope, the saved project and freshly exported file would need their own readback. A pre-existing project for another nozzle, an inherited export script or an unexplained network destination would block the corresponding action. No estimates or acceptance observations in this scenario are real measurements. No model was loaded, slicer executed, toolpath generated, program run, file uploaded or printer operated for this illustration.
