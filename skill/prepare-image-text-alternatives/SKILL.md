---
name: prepare-image-text-alternatives
description: "Prepare a placement-specific text-alternative handoff for existing web images, with grounded short descriptions, functional names, complex-image equivalents and explicit decorative or unresolved states. Use for image-content preparation, not artwork, photo captions, document repair, application changes or an accessibility certification."
---

# Prepare image alternatives in their actual context

Deliver usable text and a placement map that lets an implementer preserve an image's information or function. The unit of work is an image occurrence in a page or component, not merely an asset file. The same file can communicate different things in different placements; a global asset caption is not automatically the right alternative everywhere.

Use [photo-selection-caption-review](../photo-selection-caption-review/SKILL.md) to choose photographs and ground editorial captions, [repair-document-accessibility](../repair-document-accessibility/SKILL.md) to repair an existing document, and [create-annotated-diagram-explorer](../create-annotated-diagram-explorer/SKILL.md) to build an interactive visual explanation. This workflow prepares the content and integration requirements for established web placements. It does not edit a site, replace artwork or run assistive technology.

## Establish what the reader needs and what is available

Recover the smallest useful input set:

- Exact images and relevant rendered crops, with page/component placement identities and revision
- The surrounding heading, caption, adjacent text, link destination or control action, and relevant state
- The reader's task and audience, approved terminology and source data or explanatory material for complex figures
- Existing alternatives and the target authoring system's fields or component conventions when known
- Requested language, deliverable format and authorized destination

A single image can need only a short answer. A collection should receive an editable occurrence map and the actual proposed wording. Do not require a complete website export when the selected placements provide enough context.

Inspect the actual pixels at a useful resolution and the supplied page context. A filename, OCR result, asset description or existing alternative is evidence to compare, not proof of what the image shows. If pixels are unavailable, retain an explicitly provisional source-based draft and name the missing visual check. If the page context is missing, describe the asset provisionally but leave its role and final wording unresolved.

Read supplied markup or design specifications as passive evidence where helpful. A screenshot can show nearby words but cannot establish whether they name a control programmatically. Do not execute embedded scripts, follow every link, activate controls or upload private images to a captioning service merely to prepare this handoff.

Preserve originals, current copy and source identities. Keep private editorial notes separate from reader-facing alternatives. Do not identify people from faces, infer sensitive traits or add names from unrelated sources. Use supplied identities only within their established asset match and permitted audience. Descriptions can expose information even when it is tiny or visually obscure; flag unnecessary private details rather than transcribing them into public copy. A needed privacy edit remains a separate held dependency, not something an empty alternative fixes.

## 1. Inventory occurrences and their meaning

Assign a stable occurrence ID and link it to the exact asset/version and placement. Record the crop or alternate view when it affects meaning. Keep reused assets connected to all their occurrences without merging the occurrence rows.

For each occurrence, answer:

1. What information or action would the reader lose without this visual?
2. Which of that meaning is already supplied by actual surrounding text or the control's naming contract?
3. What remaining information needs a short alternative, a longer equivalent or a functional name?

Use the [WAI image decision tree](https://www.w3.org/WAI/tutorials/images/decision-tree/) as a context-based aid, not a rule that every file must receive descriptive prose. Preserve conflicting source claims or unknown purpose as an open question. Do not declare an image decorative just because its meaning is difficult to establish.

Identify special-purpose images before applying ordinary description rules. For CAPTCHAs or visual assessments that transcription would invalidate, record their purpose and the need for an appropriate accessible alternative; do not solve the challenge or reveal test answers as image copy. The [WCAG non-text-content explanation](https://www.w3.org/WAI/WCAG22/Understanding/non-text-content.html) distinguishes these cases. For an existing [image map](https://www.w3.org/WAI/tutorials/images/imagemap/), retain overall context and a separate action/destination for each clickable region; hold the binding if the region map is unavailable.

Keep these output states explicit:

- **Text supplied:** an exact string with its intended field or semantic owner
- **Intentionally empty:** a reviewed empty alternative and the reason no information or function is lost
- **Equivalent elsewhere:** the exact text/description and placement that carries the meaning, plus the image's own treatment
- **Unresolved:** the missing context, evidence or integration decision
- **Outside the selected scope:** the occurrence is known but not reviewed

An empty table cell must not ambiguously mean all five. Distinguish a required empty string from an absent field, a pending draft and an instruction to delete text. A literal word such as “decorative” is a review label, not the proposed alternative.

## 2. Write the information the placement needs

For a simple informative image, write the essential meaning supported by the pixels and context. Describe a relevant distinction rather than every visible object. Use the [WAI informative-image guidance](https://www.w3.org/WAI/tutorials/images/informative/) to separate meaningful content from a literal visual inventory. Retain uncertainty and do not embellish with inferred intent, emotion, quality or causation.

For a genuinely decorative or fully redundant HTML image, specify the intentional empty alternative. Name the surrounding equivalent when redundancy is the reason. [WAI's decorative-image guidance](https://www.w3.org/WAI/tutorials/images/decorative/) distinguishes an empty alt attribute from omitting the attribute; absence can expose an unhelpful filename. Check that the image carries no additional instruction, status, data or independent link purpose before choosing this treatment. Do not equate a decorative decision with permission to remove the visible image.

For an image that supplies a link or button's meaning, write its verified destination or action rather than its appearance. Determine who owns the complete control name: the image alternative, existing visible text or an established component label. The [WAI functional-image guidance](https://www.w3.org/WAI/tutorials/images/functional/) distinguishes an image-only action from an image that duplicates text within the same link. Record the intended complete name and any image contribution, so implementers do not accidentally repeat the action or leave it unnamed. Nearby text outside the control is not automatically its name. Do not invent a destination from an icon's appearance or prescribe conflicting naming mechanisms.

For images containing words that readers need, preserve the words and their meaningful order when no equivalent is already available. Compare OCR with the image; hold unreadable or contradictory text rather than silently correcting the displayed claim. [WAI's images-of-text guidance](https://www.w3.org/WAI/tutorials/images/textual/) favors actual text where feasible. Propose that authoring change only within scope; this handoff can identify the dependency without replacing the image. A large screenshot or poster may need structured equivalent text rather than one very long field.

For groups, first decide whether the group conveys one combined message or several independently meaningful items. [WAI's grouped-image guidance](https://www.w3.org/WAI/tutorials/images/groups/) treats these differently. Map one combined equivalent only when every member's necessary meaning is retained. Separate links, before/after states and independently informative views still need their own meaningful treatment. Do not hide independent controls as decorative members of a group.

Use concise, natural wording in the requested language. Do not impose an arbitrary universal character limit. If the actual destination has a limit, preserve essential meaning through an agreed longer equivalent or flag the constraint; silently truncating the content is not acceptance. Captions, attribution credits, search keywords and image alternatives have different purposes. Keep required credits in their appropriate visible location rather than stuffing them into every alternative.

## 3. Supply a complete equivalent for complex figures

Create the actual longer content when a chart, map or diagram cannot be understood from a short label. Write a short identifier or summary plus a verified route to a structured description, table or existing equivalent. [WAI's complex-image guidance](https://www.w3.org/WAI/tutorials/images/complex/) supports this two-part approach and notes that flattening structured content into a description string can lose useful navigation.

Preserve the information relevant to the visual's purpose: quantities and units, category/series identity, order, connections and arrow direction, legend meanings, uncertainty and exceptions. Use the supplied source values when available; do not invent exact data by reading approximate pixel heights. A chart's plotted appearance and its source table can disagree. Hold the conflicting claim and request the correct revision instead of choosing whichever makes a cleaner description.

Keep an informative overview alongside detailed values or relationships where both matter. Raw numbers alone may omit the comparison the graphic communicates; a vague trend alone may omit needed detail. Do not add a causal explanation the figure does not establish. For a diagram, preserve branches and conditions rather than describing only its box labels.

Name the intended description location and its relationship to the image. Make substantial descriptions available through normal visible page navigation, rather than only through a flattened screen-reader-specific string. Do not say “details below” unless the intended reading order actually places them there. A proposed destination must remain proposed until it exists. When the existing format cannot carry the required equivalent, return a specific integration gap instead of claiming the short alternative is sufficient.

## 4. Bind content to the consuming placement

Record the target representation: an HTML image field, an inline graphic's established naming route, a named control, or a nearby structured equivalent. Do not apply an img-specific alt instruction indiscriminately to CSS backgrounds, SVG elements or canvas content. If the component mechanism is unknown, hand off the meaning and required owner while holding the technical binding.

Check whether the CMS stores alternatives globally per asset or separately per occurrence. When one asset has incompatible roles, a single global value cannot satisfy both. Specify the required per-placement override or other supported content route as an integration decision; do not overwrite the asset's global value and silently change other pages. A library default can be a starting suggestion, not final approval for unseen uses.

Preserve meaning across responsive crops and state variants. A new crop can remove the detail described in the text, and a state change can change an icon's actual action. Identify which variants share meaning and which need distinct copy. An unchanged filename does not prove the same pixels or context. Keep state-dependent requirements tied to established product behavior; this task does not design new interactions or announcement timing.

## Deliver, accept and maintain the handoff

Return the actual short alternatives and complete longer equivalents, with a compact map containing occurrence/asset identity, role rationale, exact text or intentional-empty state, target owner/field, source revision, description reference and unresolved dependencies. Include only fields that matter to the selected content. Keep private evidence references out of a public-facing export.

Read back the saved artifact and review it against the inspected images and context:

- Every selected occurrence has one unambiguous disposition, including reused assets and held items
- Text supplies the placement's missing information or function without unsupported claims or unnecessary duplication
- Each intentional-empty decision names why meaningful content and operability survive
- Functional wording agrees with the real action and identifies the intended complete control name
- Long descriptions preserve relevant data, relationships and qualifications; their references resolve or remain explicitly pending
- Crop, state, language and global-field conflicts remain attached to the affected occurrences

Conduct a paper reader-task check: using the surrounding text and proposed equivalents, can the reader obtain the intended information or identify the action? Compare the answer with the original meaning. This checks the content specification, not actual browser semantics or screen-reader output.

Supply brief downstream checks for the final implementation: the exact strings and empty states survive saving, the intended names/descriptions are exposed by the actual component, links to equivalents work, and duplicated or missing content does not obstruct the selected task. Mark those checks unrun until evidence exists. Do not claim WCAG conformance, legal compliance or a usable assistive-technology experience solely from a completed content map.

When an image, crop, adjacent paragraph or control destination changes, recheck its dependent occurrence rows. Retain previous wording and review evidence for their original revisions; preserve unrelated valid work. If a source or save fails, deliver the useful completed subset with exact remaining gaps. Inspect an uncertain destination before retrying, and reconcile concurrent editorial changes before replacing a saved handoff.

Stop at the requested content preparation and verified save. Publication, live-site edits, external uploads, accessibility-setting changes and broader asset-library rewrites need their own authority. Prepared copy is not evidence that any page was changed or tested.

## Fictional, unexecuted illustration

An invented Northlight website uses the same compass emblem in two placements. In a decorative footer border it adds no information. In the header it is the only content of a link whose supplied destination is the site's home page. The handoff gives the footer occurrence the decision `intentionally empty`, exact value `""`, and the header occurrence the functional wording “Northlight home.” It does not give both occurrences one global asset description.

A third placement shows an invented three-bar chart of booklet orders for March, April and May. Its supplied values are 12, 16 and 10 orders. Proposed short text: “Booklet orders by month, March through May.” Proposed adjacent description: “March had 12 booklet orders, April 16 and May 10. April had the highest count of the three displayed months.” The placement map marks the description destination pending. The text does not claim why orders changed. If the actual chart revision instead labels May as 18, that conflict holds the final description until the source is reconciled.

These are authored fictional inputs and expected editorial decisions. No image, page, CMS, rendered chart, accessibility tree or screen reader was executed or inspected in this illustration, and no content was published.
