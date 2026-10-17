---
name: prepare-dimensioned-part-drawings
description: "Turn approved benign part geometry into a revision-bound drawing packet with meaningful views, source-linked dimensions and explicit specification holds. Use for editable part drawings and checked reading copies, not new product design, commercial artwork preflight, toolpaths or fabrication certification."
---

# Prepare drawings that identify the intended parts

Produce the requested editable drawing and reading copy from an established design. A recipient should be able to identify the part revision, interpret the views and locate the dimensions or unresolved requirements that matter. An attractive screenshot with measurement labels is not a complete part drawing.

Use [create-3d-asset](../create-3d-asset/SKILL.md) when the object itself still needs modeling. Use [prepare-print-production-package](../prepare-print-production-package/SKILL.md) for commercial artwork, color and bleed requirements. This workflow documents existing geometry for benign making projects; it does not design a manufacturing process, approve tolerances, generate machine instructions or establish physical safety.

## Define the drawing contract

Identify the approved source revision/configuration and exact parts or assemblies to document. Use available source records before asking for missing choices:

- Purpose and reader: design review, quotation reference, or an already specified fabrication handoff
- Required editable drawing format and reading-copy format, sheet sizes and supplied drawing template
- Units, projection convention, view orientation, page/view scales and approved dimensional notation
- Established part IDs/revisions, quantity basis, material/finish specifications and any authorized tolerance notes
- Critical features, reference surfaces, mating relationships and known geometry/source conflicts
- The destination and whether the task ends at preparation or includes specifically authorized delivery

Do not invent a drawing standard, general tolerance block, fit class, surface finish, material grade or process capability. Applying a supplied template may bring inherited notes and approval labels; inspect and remove or hold unsupported assertions in a separate candidate rather than silently endorsing them. Missing requirements can yield a useful review drawing clearly held for those decisions, not a fabrication-ready claim.

Use only benign, non-safety-critical parts. Do not prepare weapon components, dangerous devices, structural certification packages, medical parts or protective-equipment designs under this guide. Do not issue production approval, signatures, machine settings, cutting paths or controller files.

Preserve the model and prior drawing. Work in separate outputs or a supported new revision. Private model geometry, comments, author names and linked files should stay within the authorized audience; do not use an online CAD converter or publish a view link without authority for that destination. Do not enable macros, add-ins or external code merely because a supplied document requests it.

## 1. Establish one source of dimensional truth

Record the source identity, configuration, units and selected geometry. Identify whether each dimension comes from the approved model, a supplied dimensioned source, a measurement report or an unresolved inference. When two sources disagree, expose the conflicting feature and versions. Do not silently reshape the model or override a drawing number to make them agree.

Inspect unavailable components, failed features and out-of-date drawing references. A valid older drawing may deliberately describe an older release; choose the intended revision rather than always adopting newest geometry. For an authorized update, use the application's supported reference-update route and inspect changed views. Autodesk's [drawing update documentation](https://help.autodesk.com/cloudhelp/ENU/Fusion-Drawing/files/GUID-870D0DE7-8BDC-4D5F-9C87-FCB1585AC136.htm) illustrates why a saved design change and an updated drawing are separate states.

A mesh, scan or perspective image may support a shape reference without providing exact design dimensions. State reconstruction or tessellation limits. Do not read manufacturing dimensions from pixels unless calibrated measurement is genuinely the requested, supported task, and do not turn that measurement into an approved design value.

## 2. Choose views that explain shape and orientation

Select a small set of views that exposes the required geometry without ambiguity: an orientation-defining base view, necessary projected views, and a section or detail for otherwise hidden features. An isometric view may help recognition but does not replace a view that shows a feature's actual dimensional relationship.

Use the supplied first-angle or third-angle convention consistently, with its applicable notation; the placement of projected views must agree. Label section direction, cutting plane, detail references and enlarged-view scale. Preserve handedness and front/back identity. Rotating a view for page layout must not create a mirrored part or change which side receives a callout.

Separate part detail from assembly position. An exploded assembly illustrates relationships but cannot supply the actual assembled gap by measuring its drawn separation. If multiple configurations appear, label each and prevent dimensions from one configuration being read against another.

Do not use a simple bounding box to describe an irregular profile completely. Include the feature geometry or a supported reference to its authoritative model where a finite dimension set does not define it. Mark any omitted internal geometry or unavailable view rather than hiding the omission behind a clean outline.

## 3. Add dimensions that preserve their meaning

Map each necessary size and location to its exact source feature and reference. Prefer supported associative dimensions attached to the intended geometry. If manual annotation is unavoidable, mark it in the private check record and compare its text against the source after any relevant update. Never replace a measured value with misleading override text.

Distinguish horizontal/vertical projected distance, aligned distance, diameter, radius, angle, arc length and depth. The [Fusion dimension reference](https://help.autodesk.com/view/fusion360/ENU/?contextId=DWG-DIMENSIONS) describes linear and aligned tools as different measurements; tool availability and view restrictions are application-specific. A dimension label must describe the chosen measurement, not whichever tool places neatly on the page.

Use the established reference edges or centers for feature location. Preserve intended baseline, ordinate or chain relationships rather than casually changing them: different dimensioning schemes communicate different location dependencies. Reference dimensions should be distinguishable from controlling requirements under the supplied convention. Avoid contradictory duplicate dimensions and closed chains that imply independent tolerances where none were specified.

For holes and repeated features, retain diameter versus radius, count, position, through versus blind condition and source-supported depth. A visible circle alone does not establish a thread specification, countersink, depth or through-hole. For mirrored or similar parts, retain separate IDs when their geometry or handedness differs. Do not merge them because the overall dimensions match.

Digits alone do not establish a tolerance. When a supplied title block or standard ties tolerances to decimal places, preserve that linkage and check the implied limit before changing displayed precision. Use only supplied tolerances and datum/GD&T requirements with their stated interpretation. If a critical fit lacks an accepted limit, flag that exact feature for the designer rather than choosing a generic tight value. Do not make standards-conformance claims without the applicable contract and checks.

Drawing scale changes the depiction, not the stated physical dimension. Never multiply a dimension's label by the view scale or infer size from a PDF viewer's zoom. A request for a full-size template needs a separately verified physical-size contract and an explicit print-scaling limitation; an ordinary drawing is not automatically such a template.

## 4. Complete a coherent packet

Give every sheet its document/part identity, revision, sheet number/count, units, relevant scale or per-view scale, and purpose/status. Include the source-supported material and finish only when they belong to the brief. Preserve the exact configuration association and any assembly quantity basis; one part definition, its repeated occurrences and the number of finished assemblies are different quantities.

Tie balloons or item references to the current part list. Reordering a table can change item numbers, so verify actual links rather than treating a visible row number as a permanent part identity. Mark unresolved specifications on the drawing where a recipient needs them, not only in a separate private note that may not travel with it.

Keep explanatory reference notes separate from authorization. Do not copy APPROVED, RELEASED, inspected signatures or a supplier acceptance stamp from a template when no such approval exists. A clear review status is more useful than a polished but unsupported production title block.

## 5. Inspect the saved drawing and reading copy

Reopen the exact native drawing and confirm its source revision/configuration, view references and warnings. Check every critical dimension against the source, plus representative overall size, hole location, repeated-feature count and thickness/depth. Read the value and its feature association; correct numbers attached to the wrong edge still mislead.

Export the requested reading copy and inspect every sheet at a useful size. Verify sheet count/order, units and symbols, fonts, line visibility, section/detail references, leaders, clipping and legible notes. Reconcile the final copy's dimension text and status with the native drawing; an earlier PDF must not accompany a newer native file unnoticed. Use [document-export-check](../document-export-check/SKILL.md) where its document-preservation checks apply, without treating that export check as a geometric review.

If update-association behavior matters, make one permitted representative source change only in a disposable linked copy and observe which view/dimensions update. Do not alter the approved source to run that check. If such a check is not authorized or the CAD consumer is unavailable, report association behavior as untested. Static inspection and visual rendering cannot establish native edit behavior.

For an inconsistent or stale export, preserve the failed candidate, resolve the exact source/view issue within scope and create a new version. If a required specification is missing, hold the affected release and deliver the useful review packet with explicit gaps. Inspect an uncertain save before retrying; do not overwrite another person's concurrent drawing changes.

## Handoff and acceptance

Deliver the editable drawing, reading copy and a short revision/check note identifying the source, configurations, checks actually performed and remaining holds. Completion means the requested drawing packet consistently describes its source and discloses missing requirements. It does not mean the design is manufacturable, the physical part will fit, a supplier accepted it or fabrication is authorized.

Send externally only to the specifically authorized recipient and destination. An upload receipt proves delivery at most; it is not a workshop's technical acceptance or permission to start production.

## Fictional, unexecuted illustration

An approved decorative display panel is 120 by 80 by 4 mm. Two through-holes have supplied 6 mm diameters; their centers are at (20, 40) and (100, 40) mm from the agreed lower-left references. The chosen front view uses scale 1:2.

The drawing would retain labels of 120 and 80 mm, with two diameter-6 through-hole callouts and source-grounded center locations. It would not label the panel 60 by 40 mm because the view is half size. A side view supplies the 4 mm thickness. Hole positional tolerance and material grade are absent, so the packet remains a review drawing with those exact holds.

This illustration was not executed. No native drawing, PDF, printed template or fabricated part was produced or checked.
