---
name: prepare-laser-cut-vector-handoff
description: "Prepare approved benign flat-part geometry as a provider-specific laser-cut vector candidate, preserving physical scale, operation intent, material identity and kerf responsibility. Deliver editable sources, checked exchange files and a review ticket, not machine instructions, an order or fabrication approval."
---

# Prepare vector geometry for a laser-cutting handoff

Turn an established flat design into a small, revision-bound package that a named service or workshop can interpret without guessing which lines to cut. A rendered silhouette does not establish a usable cutting file: overlapping paths, unconnected islands or imported scale can change the physical result while the preview looks convincing.

Use [prepare-dimensioned-part-drawings](../prepare-dimensioned-part-drawings/SKILL.md) for human-readable drawings and [reconcile-design-cut-list](../reconcile-design-cut-list/SKILL.md) for piece demand and stock accounting. [validate-svg-print-geometry](../validate-svg-print-geometry/SKILL.md) concerns printed appearance, not fabrication-path intent. This workflow owns the separate conversion from approved planar geometry to a recipient-specific vector exchange package. It does not replace design work, nesting optimization or machine operation.

## Establish the handoff contract

Limit the task to benign decorative panels, labels, organizer inserts and similar non-safety-critical flat parts. Exclude weapons, dangerous devices, structural or protective parts and claims about food, medical or electrical suitability. Do not select laser power, speed, passes, focus, ventilation, workholding or machine-safety procedures. Do not generate controller files, connect to a cutter, frame a job, fire a laser or initiate fabrication.

Find the approved design revision, part IDs, required quantities, intended physical dimensions/units, material and thickness. Identify the front face, any directional finish or grain, and whether rotation or mirroring is allowed. Keep nominal thickness distinct from any supplied measured thickness or tolerance.

Obtain the intended recipient's current specification for the exact material and service:

- Accepted vector format/version and supported entity types
- Cut-through, line-marking and area-engraving capabilities, with their required layer/color conventions
- Whether the file represents nominal finished boundaries or compensated beam paths, and who applies kerf compensation
- Applicable part, hole, bridge, spacing and sheet/layout limits
- Whether the recipient wants one part definition per file or a supplied sheet layout, and where quantities are specified

Ask only for missing choices that affect the result. Without a provider or process contract, prepare an explicitly provisional geometry review; do not invent universal line colors, bridge widths, material suitability or a production-ready label. A provider's accepted material catalogue is not permission to substitute an unknown sheet of similar appearance.

Keep originals unchanged and work in new local files outside watched fabrication queues. Use an available authorized editor; do not install software or upload designs to a converter automatically. Treat active content, external resources and bundled scripts as untrusted. Saving a candidate is not authority to order, accept commercial terms or share private geometry.

## 1. Separate design geometry from the reading drawing

Record source identity, selected part/configuration and the dimensional reference. Make each output traceable to that source. Distinguish part contours, intended marks, construction lines, dimensions, registration references and purely explanatory artwork before changing anything.

Keep a reading copy with labels separate from the exchange file unless the recipient expressly requires those objects. A page border must not become an extra cut. Conversely, a deliberate part outline must not disappear because it resembles a border. Remove only objects whose exclusion is established, and retain the editable source for recovery.

Identify how every operation is represented. A filled black shape, a thick stroke and the outline of that stroke can describe three different requests. Expanding a stroke may produce two closed contours where the user intended one marked centerline. Do not use a blanket "outline everything" conversion without resolving that intent.

When lettering must become geometry, preserve its approved glyph shapes and spacing in a separate derivative. Check internal counters and disconnected decorative pieces against the intended retained material. If a cut-out letter needs a bridge to keep an island attached, adding that bridge changes the design: flag the feature for an authorized revision rather than silently stencilizing it. An engraved letter does not have the same retention problem as a through-cut letter.

The [SendCutSend sheet-cutting requirements](https://sendcutsend.com/guidelines/sheet-cutting/) illustrate a specific contract: actual-size geometry, removal of annotations, outlined text, retained islands and closed ordinary cut contours. Apply the selected provider's rules, not these as a universal file format.

## 2. Preserve physical scale through conversion

Use a known overall dimension and an independent internal feature or spacing to establish the imported scale. Inspect geometry coordinates, document units and export/import options, not just a dimension label or page size. A correct width with an incorrect height can indicate a nonuniform transform.

For SVG, resolve physical dimensions, viewBox mapping and nested transforms; for DXF, reconcile the declared or selected drawing units with the receiving application. If the format or importer leaves units ambiguous, include the intended units in the ticket and hold acceptance until the actual imported dimensions are checked. Never fix uncertainty with automatic fit-to-page or fit-to-bed scaling.

Import settings can matter: [LightBurn's settings reference](https://docs.lightburnsoftware.com/latest/Reference/SettingsPreferences/) documents alternative SVG DPI interpretations. Inspect the actual source and installed consumer behavior rather than choosing an option solely from an application name. A global preference change can affect unrelated jobs; prefer a scoped import setting or record and restore the prior setting when an authorized change is necessary.

If a correction changes coordinates, record its basis and compare both reference dimensions afterward. Preserve the approved geometry; do not change the design's width to compensate for a wrong importer. Keep rotation separate from mirroring, especially for an asymmetric part or one-sided marking.

## 3. Assign operations and inspect contour topology

Map each intended operation to the recipient's exact supported layer, color or other convention. Include an explicit operation legend in the ticket. Do not assume red always means cut or that a hidden layer is excluded from export. If the consumer cannot preserve the required distinction, hold the mixed-operation export or use a recipient-approved separation into files.

Inspect the actual vector objects in outline/entity view and review the resulting filled/retained regions separately. Look for:

1. Duplicate or partially overlapping segments that could represent repeated processing
2. Unexpected open endpoints, zero-length entities, self-intersections and tiny stray objects
3. Missing outer boundaries, holes merged into the outer profile, or islands that will not stay attached
4. Reversed face orientation, missing text details or curves altered by conversion
5. Objects that belong only in the reading copy but remain in processing geometry

Do not close every path automatically. Open lines can be intentional marks or a specifically supported slit service; ordinary closed-profile cutting and those operations have different contracts. [SendCutSend's single-line service guidance](https://sendcutsend.com/blog/setting-up-your-design-for-single-line-etching-or-single-line-no-kerf-through-cuts/) distinguishes etching from open through-cuts without kerf compensation. Its service and material restrictions are not permission to interpret every open contour as intentional.

If geometry is repaired within the approved scope, preserve a before/after candidate and compare the affected feature. Snapping nearly coincident endpoints, simplifying curves or deleting "duplicates" can remove intended gaps or change dimensions. Do not infer equality from a shared bounding box or visual overlap. Hold ambiguous repairs for the designer rather than accepting a clean checker result that describes a different part.

## 4. Resolve compensation, features and copy accounting

Make kerf responsibility explicit before any offset. Retain nominal finished geometry separately from an explicitly requested compensated derivative. Do not apply a guessed offset or compensate twice because both the file author and provider use a kerf setting.

Process rules can differ even within one provider: [Ponoko's kerf guidance](https://help.ponoko.com/en/articles/4442594-how-much-material-does-the-laser-burn-away) distinguishes its automatically compensated metal service from other materials and directs users to material-specific information. A published average is not a measured result for the user's job. Preserve uncertainty about physical fit, material thickness and edge variation; a digital offset cannot certify them.

If compensation is explicitly supplied and authorized, record the material/process basis, amount, units, intended side and whether the value denotes full cut width or a one-sided offset. Compare outer boundaries and inner openings separately after conversion. Check for collapsed narrow features and topology changes. Do not automatically offset marks or apply a single scale factor to simulate a contour offset. Missing fit requirements remain a design hold, not an invitation to invent a press-fit allowance.

Compare critical holes, narrow webs and retained islands with the selected material/service limits. Report the affected feature and source requirement, not simply "too small." Do not widen a bridge, enlarge a hole or change material to obtain acceptance without authorization for the design change.

Reconcile quantities once. One file containing three copies and a requested quantity of three may mean nine pieces in the recipient's ordering model. State whether each file is one part, one assembly set or one sheet layout. Keep mirrored variants distinct. If a layout is requested, preserve allowed orientation and required separation; do not introduce common-line cutting, pack parts into holes or claim optimal yield without the corresponding process/layout contract. When the recipient performs nesting, deliver part definitions rather than imposing an unnecessary sheet arrangement.

## 5. Reopen the exact exchange files

Save the editable candidate and export only the requested format. Record editor/version and relevant conversion settings. Reopen or import the exact saved exchange file into an available compatible local consumer, without a machine connection or execution route. A successful save dialog is not evidence that paths survived conversion.

Compare the imported result with the accepted source:

- Overall and internal reference dimensions, units, orientation and part count
- Operation assignments and retained/excluded objects
- Outer/inner contours, intentional open paths, duplicate segments and important small features
- Any compensated versus nominal geometry distinction
- Warnings, unsupported entities and changed curves or text

Check geometry as well as appearance. A screenshot alone cannot show duplicate coincident paths or prove a closed contour. Conversely, a topology report cannot establish that the correct words or face were retained. If another consumer is unavailable, report only the checks actually performed and hold recipient-import compatibility.

Recheck after any export setting, source geometry, material, operation or compensation change. Preserve failed candidates separately. Inspect the destination after an interrupted save before retrying, and do not overwrite a concurrent revision. Avoid enabling scripts, removing security protections or sending the design to another service as a recovery shortcut.

## Deliver a review package, not fabrication approval

Return the editable candidate, exact exchange file(s), a clearly marked reading preview when useful, and a concise ticket: source revision; part/quantity basis; material/thickness; units and known dimensions; front/orientation rules; operation legend; kerf responsibility; recipient specification; checks performed; and unresolved decisions. Keep obsolete candidates and explanatory geometry out of the processing package.

Label geometry prepared, saved-file readback checked, provider interpretation accepted and physical part verified as separate states. Stop at preparation unless external delivery is specifically authorized. Even then, an upload receipt or automatic preview is not production approval, an accepted purchase or evidence that the part fits. Any actual cutting needs the responsible operator's separate process and safety checks.

## Fictional, unexecuted illustration

A fictional workshop requests one DXF per nominal part, millimeter units, with a specified separate layer for surface marking. It applies its own kerf compensation. The approved decorative plaque is 100 by 60 mm with two 5 mm holes and one marked word. The user wants four identical plaques.

The candidate would contain one part definition, with quantity four recorded separately. It would keep nominal boundaries unchanged, preserve the marking as the specified operation and exclude the reading drawing's dimensions. If a conversion turns the marked word into through-cut outlines, the export is held despite a correct 100 mm width. If the imported height becomes 45 mm, scaling the whole part until the width looks right is not a valid repair.

A second design variant contains a through-cut letter O whose center is intended to remain attached. That variant needs an authorized bridge/design decision; it cannot be passed merely because both circles are closed. After any correction, the exact saved exchange file needs another geometry and operation readback.

This illustration is authored reasoning only. No CAD/vector application, checker, export, provider upload, order, machine preview or physical cutting was performed, and no dimensional fit or material safety was verified.
