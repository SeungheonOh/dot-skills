---
name: create-annotated-diagram-explorer
description: "Create an explorable diagram or image with correctly anchored hotspots, linked explanations, optional guided views and a complete text alternative. Use for inspecting parts and relationships in a supplied or established visual, not diagnosing an image, authoring a whole lesson or merely adding decorative labels."
---

# Create an annotated diagram explorer

Deliver a visual the reader can inspect by selecting meaningful parts, with explanations anchored to the right locations at every supported size. Include an equivalent ordered text view. The useful artifact connects spatial context to explanation; hiding ordinary prose behind arbitrary dots is not a reason to add interaction.

Use this for a system schematic, equipment orientation diagram, interface anatomy or another bounded visual whose meaning is already established. [Visualize information](../visualize-information/SKILL.md) can establish a new diagram; [learning materials](../create-learning-materials/SKILL.md) can supply a larger lesson. Keep this workflow focused on linking regions, explanations and navigation, without claiming image recognition, diagnosis or physical safety verification.

## Establish the asset and content contract

Inspect the actual visual and source explanations before placing markers. Identify:

- The reader's locating or understanding task and intended display context
- Exact asset/version, dimensions or SVG coordinate system, orientation and any existing crop
- Approved labels, explanations, relationships and evidence for each region
- Whether the reader needs free exploration, a short guided order, zoom or alternate views
- Output format, offline needs, authorized audience/destination and whether editable source is required

Use the supplied visual when it is fit for the task. Do not silently replace a precise schematic with generated artwork, infer invisible components or turn a conceptual drawing into a scale diagram. If a critical region is illegible or its meaning is unknown, request the missing source or label that limitation rather than guessing.

Confirm the asset can be reused in the intended deliverable and retain required attribution. Images and screenshots can expose faces, locations, identifiers, hidden metadata or confidential interfaces. Prepare a sanitized derivative within the approved environment when needed; do not change the original. A hosted preview or remotely loaded image can disclose information before a visitor clicks anything. Do not upload assets, add tracking or publish the explorer without the necessary authority.

## Create a single annotation map

Keep content and placement in an editable map rather than burying explanation text inside drawing code. Give each annotation a stable ID and record:

| Field | Meaning |
| --- | --- |
| Asset/view ID and version | Which visual the annotation belongs to |
| Anchor or region geometry | Point, rectangle or polygon in a declared coordinate system |
| Visible label and full name | A short marker label plus the name used by the text view |
| Explanation and source | Supported meaning, uncertainty and relevant reference |
| Related annotation IDs | Explicit relationships without relying only on proximity |
| Reading order and optional tour position | Intentional navigation rather than accidental array or spatial order |

Use a point when only a location matters, a region when a component's extent is meaningful, and an independent callout when a tiny component cannot carry a usable target. Keep selectable hit areas separate from the depicted physical extent so a larger target does not imply a larger component. Do not infer process direction from left-to-right placement; label actual connections and their meaning.

Check duplicate IDs, missing references, bounds and unsupported geometry before building the view. If the asset changes, invalidate or review its annotations. A marker that remains within bounds can still point to the wrong part after a crop or redesign.

## Preserve geometry through resizing and alternate views

Choose one coordinate model and apply the same transformation to the image and its overlays:

- For raster assets, record intrinsic width/height and anchor coordinates in those source pixels or documented normalized fractions
- For SVG assets, use the actual viewBox origin, width and height; a nonzero origin matters
- Preserve aspect ratio unless intentional distortion is part of the task. Account for letterboxing or crop offsets, not merely the outer container width
- For zoom/pan, transform the image and anchors together while keeping control labels and hit targets usable

MDN's [viewBox reference](https://developer.mozilla.org/en-US/docs/Web/SVG/Reference/Attribute/viewBox) and [preserveAspectRatio reference](https://developer.mozilla.org/en-US/docs/Web/SVG/Reference/Attribute/preserveAspectRatio) describe the relationship between an SVG's coordinate space and its viewport. Verify the actual rendered placement rather than assuming a responsive width makes overlays align.

For multiple views, record explicit mappings. A front and rear photograph, or expanded and collapsed schematic, generally needs its own anchors; resizing one set is not enough. Keep a selected annotation only when a corresponding region exists in the new view. Otherwise explain that it is not visible and offer a supported view, rather than highlighting an unrelated location.

Avoid cropping an essential region just to fit a narrow screen. Use a full overview with an optional detail view, a wrapping label list or a usable zoom route. Keep a Reset view control if zoom/pan is present. Dragging must not be the only way to reach detail; provide buttons or named-region navigation.

## Build selection, detail and guided navigation together

Use the requested platform and an available, authorized renderer. A self-contained browser artifact is appropriate when the content is local and no service is needed; do not introduce a framework, backend or CDN by default. Preserve a useful first view before any interaction.

Selection should update one shared annotation ID. Use it to coordinate the marker highlight, selected label in the list and detail content. Activate with click, tap or keyboard. Hover may preview supplementary content, but essential explanation must remain available after deliberate selection. Clearly distinguish the selected region from keyboard focus.

Prefer native HTML controls for the region list and navigation. If the visual cannot expose robust keyboard targets, the equivalent list must perform the same selection and reveal the same content. Keep marker names meaningful, not merely “button 4.” Provide a predictable way to close or clear details, and restore focus if opening/closing a panel removes the active control. Follow the appropriate [WAI keyboard conventions](https://www.w3.org/WAI/ARIA/apg/practices/keyboard-interface/) rather than assigning an ARIA role without its behavior.

For an optional guided order, Next and Previous select the authored sequence without changing the underlying facts. Show the current topic and allow returning to free exploration. Do not lock content behind completion, a score or a timer. Avoid automatic zooming or motion when a static highlight communicates the same point.

Render imported titles and descriptions safely as text or through the host's approved sanitization path. Do not inject untrusted SVG, active HTML, scripts or arbitrary link schemes into the artifact. Inspect supplied SVGs for active/external content and use a safe supported representation when necessary. Links to sources should not require the learner to send private region data to an external site.

## Provide a complete accessible and noninteractive version

Include a concise overall description of the image's purpose and a structured long description with the important parts and relationships. WAI's [complex-image guidance](https://www.w3.org/WAI/tutorials/images/complex/) explains the need for more than a short image label when the graphic carries substantial information. Make that description available to everyone through normal document navigation.

Generate the full text view from the annotation map. Preserve headings, labels, relationships, caveats and references; a list of region names alone is insufficient. Do not require a hover, spatial guess or script to read essential information. A single giant accessible-name string is a poor substitute for navigable sections.

Keep text readable at the actual output size, with sufficient contrast and redundant cues beyond color. Let small-screen layouts stack the diagram and descriptions rather than shrinking every label. If visual fidelity requires an image-only view, deliver the text description as an adjacent accessible document rather than claiming the image itself is interactive or fully accessible.

## Acceptance checks and failure recovery

Check the actual delivered artifact within the available permission boundary:

1. **Semantic mapping:** each marker, list entry and detail points to the intended annotation and source; relationships and uncertainty remain accurate
2. **Spatial mapping:** inspect representative center and edge regions at supported widths, after zoom/reset and in each alternate view; overlays must remain on their intended parts
3. **Interaction parity:** pointer, touch where available, and keyboard routes reach the same explanation; selection, focus and expanded state remain understandable
4. **Fallback parity:** every essential annotation and relationship is present in the noninteractive version, even with the image missing
5. **Packaging:** the saved artifact opens through the declared route with its required assets; check offline behavior only if it was requested and actually exercised

Report static, visual and interaction checks separately. An anchor within numeric bounds does not prove correct placement, and a screenshot does not prove keyboard navigation. Do not claim accessibility conformance from a few manual checks.

If overlays drift, repair the coordinate transformation or asset mapping rather than nudging markers independently for one screen size. If markers overlap, use a list, leader lines or a clearer detail view; do not conceal parts or make targets too small. If the asset fails to load, show the full explanations and a useful missing-asset message instead of an empty canvas. If a preview is unavailable or denied, deliver the content map and static description with the interactive/visual checks explicitly unrun; do not circumvent the restriction.

Return the explorer, necessary authorized assets, editable annotation map and full text alternative. State how to change content without breaking anchors, which asset revision it uses and what remains unverified. Stop at the agreed artifact; publication, collecting user behavior and operational instructions for real equipment are separate scopes.

## Fictional example, not executed

A fictional parcel-sorting diagram has a 1000 × 600 source canvas. Its approved teaching content names an intake at source point (150, 300), a decision gate at (500, 300) and two output lanes. An annotation for the gate explains that the illustrated label rule chooses a lane; the drawing does not establish physical dimensions or machine safety.

In a 500 × 300 rendered image with no crop or padding, the gate's planned anchor is (250, 150). In a 500 × 400 container that centers that same 500 × 300 image, the 50-pixel top offset must also be included. Selecting “Decision gate” from the text list should reveal the same content as selecting its marker. A rear-view image would require a separate verified anchor map.

These are fictional design inputs and expected relationships. No explorer, geometry implementation, rendered file or assistive-technology interaction has been created or executed by this example.
