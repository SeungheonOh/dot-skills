---
name: prepare-pseudolocalization-review
description: "Prepare a resource-bound pseudolocalization review packet with explicit stress profiles, protected syntax, UI-state coverage and evidence criteria. Use to plan synthetic localization checks before translation; this skill prepares the handoff and does not run builds, alter device settings or certify a translated release."
---

# Prepare a pseudolocalization review

Produce an executable-by-a-reviewer plan for exposing extraction, length, character and direction problems before real translation. The deliverable is a bounded review packet: source/resource inventory, transformation contract, scenario matrix and evidence/defect record. “Executable” here means sufficiently precise for an authorized reviewer to carry out; preparing the packet does not execute the application or tests.

This is distinct from [translation-release-review](../translation-release-review/SKILL.md), which checks actual translated wording and its consumer. Pseudolocalization deliberately uses synthetic text. It can reveal localizability problems, but it cannot establish idiomatic translation, appropriate terminology or complete real-language support. Microsoft describes this boundary in its [pseudolocalization guidance](https://learn.microsoft.com/en-us/globalization/methodology/pseudolocalization).

## Define the planned review and its evidence

Use the supplied resource export, screen/state descriptions, screenshots or design references and known framework/platform documentation. Record the source revision, target build identity if one exists, supported device/viewport range, resource syntax, locale-switch mechanism and destination for the packet. Do not infer live application behavior from a screenshot.

Resolve the review scope: selected flow/screens, resource IDs, high-risk states and required output. A small product flow may need a short matrix; do not expand it into every theoretical locale/device combination. Ask only when missing information prevents a meaningful case, such as whether an apparent label comes from an editable resource or a server response.

Separate available evidence from later obligations:

- Resource text inspected: exact files/revisions and extraction limits
- Design or screenshot reviewed: exact reference and represented state
- Platform/profile documented: source and relevant version
- Application rendered or interacted with: pending unless actually performed in a separately authorized task

If only screenshots are available, produce a screen-based risk plan and list the resource mapping as unknown. Do not invent keys or claim an extraction gap. If only strings are available, produce a resource-focused plan with screen coverage awaiting an owner. A useful partial plan must state which conclusions it cannot support.

## Map visible content to its origin

Create stable case/resource references without rewriting the source. Distinguish app-owned localizable literals from protected tokens, runtime values, server-provided messages, user content, platform UI and images containing text. Each origin needs a different expectation: an unchanged brand can be intentional, whereas an untranslated app label may be a missing resource or a fallback.

For each selected message, record its key/locator, complete source unit, render location or unknown status, argument names/types, plural/select branches, markup, escape rules and translatable literal spans. Include accessible names, descriptions, validation errors and empty/loading states when those are part of the chosen flow; visible labels alone do not cover them.

Look for relationships that should survive the stress: warning beside its action, number beside its unit, label beside its field, link label with its destination, and clauses that must remain one message rather than concatenated fragments. Identify suspected assembly seams as review questions, not confirmed defects.

Keep supplied strings and screenshots private within the approved scope. Screenshots may reveal accounts, messages or unreleased content. Use synthetic data in planned scenarios, crop or redact only authorized review copies, and retain enough unredacted layout evidence privately to explain the test. Do not upload resources to a new online pseudo-translation tool.

## Specify stress profiles that can be distinguished

Prefer the platform's existing supported pseudolocale mechanism when available. Record its name and documented behavior rather than assuming all platforms use the same IDs or transformations. For example, Android documents `en-XA` and `ar-XB` with different stress behavior in its [pseudolocale guide](https://developer.android.com/guide/topics/resources/pseudolocales). This is a platform example, not a universal locale contract or permission to change a device's locale.

Choose a small set of profiles with clear diagnostic purposes:

| Profile | Planned signal | What it does not establish |
| --- | --- | --- |
| Unmodified baseline | Capture the same state and data for comparison | Correctness in another language |
| Marked/accented literals | Identify which app-owned strings were transformed and inspect character handling | Correct shaping or font coverage for all scripts |
| Expanded literals | Expose clipping, overlap, inaccessible overflow and fragile assembly | A maximum length for all future translations |
| Direction stress | Inspect a documented RTL/bidi route with mixed-direction values | That reversing characters produces correct Arabic or Hebrew |
| Long runtime values | Exercise caller-supplied data separately from template text | Resource extraction completeness |

Use isolated profiles where combining effects would obscure a failure; a final combined case can follow when useful. Do not invent a universal expansion percentage. Use the existing generator's documented settings or state an explicit project stress choice, with its length metric and treatment of spaces, protected tokens and added markers. For short labels, consider a separate long-label case instead of assuming one proportional factor stresses them adequately.

If a deterministic custom transformation is requested, specify the recipe and expected protected structure, not just “add accents.” State which literal spans are transformed, the replacement/padding convention, marker placement, repeatability settings and maximum output bounds. The future implementation must understand the actual message grammar. Braces, plural/select selectors, argument names, rich-text tags, escaped characters, URLs, IDs and code snippets must not be altered by a blind whole-file substitution.

Apply expansion within complete translatable units or grammar branches as appropriate, leaving syntax intact. Record whether lengths count code points, grapheme clusters or another documented unit. A character count is a diagnostic; it does not predict rendered width. Do not change numeric values, actual deadlines or the meaning of a safety instruction to create a larger sample. Use separate fictional input data where those values need stress.

If the available mechanism cannot transform the resource grammar safely, hold pseudo-resource generation and keep the review plan. Do not replace the app's localization framework with a homegrown formatter merely to make a demonstration run.

## Plan direction, branches and fallback separately

Use the platform-supported direction mode rather than manually reversing source strings or file order. Record expected container direction, mixed-direction inserted values and direction-sensitive layout decisions. A URL, product code or number embedded in RTL text may need isolation rather than reversal; follow the target's documented markup/text route. The [W3C bidi guidance](https://www.w3.org/International/questions/qa-bidi-controls) explains why direction handling depends on the context.

Do not require every icon or control to mirror. Distinguish navigation direction from universal symbols, media controls and brand artwork; identify the intended behavior from design/platform guidance or leave it as an owner decision. Record text order, alignment, focus sequence and clipping observations separately.

Pseudolocale branch behavior need not match a real target locale. Derive plural/select cases from the actual resource grammar and reachable application inputs. Include an explicit plan for target-language plural categories when real-language support is in scope; do not assume 0, 1 and 2 exercise all categories. [Unicode CLDR plural rules](https://cldr.unicode.org/index/cldr-spec/plural-rules) explain that categories vary by language and that fractions can matter. Keep this as a distinct language/formatter check rather than claiming accent expansion covers it.

Make fallback observable. For each relevant case, the future reviewer should record requested locale, resource/profile actually loaded and why an unchanged string is expected or suspicious. Do not label every unaccented string “hardcoded”: it could be a protected brand, runtime data, an unvisited branch, a server string or fallback. Require tracing the origin before assigning a root cause.

## Build a bounded scenario matrix

Each case should specify:

1. Stable case ID, relevant screen/state and resource IDs or unresolved mapping
2. Baseline version, chosen profile, viewport/device class, text-size/zoom setting and synthetic data values
3. Exact navigation/state setup and what the reviewer must observe
4. Acceptance criteria tied to the user's requirements, plus any owner decision still needed
5. Evidence to capture, restoration steps and current status

Choose cases by risk: shortest button with little spare width, longest sentence, dense table/card, modal, multiline error, long name/value, dynamic plural branch, mixed-direction text and an accessible label not shown visually. Include only states relevant to the selected flow. For repeated controls, use a representative case plus exceptions rather than hundreds of indistinguishable screenshots.

Make expected behavior observable. “Looks fine” is weak; “the complete warning remains available beside the action at the specified text size, with no overlap and an operable dismissal” is reviewable. Do not mandate that all text remain single-line. Wrapping, scrolling, truncation with an accessible full value or a layout change may be legitimate under the product's actual design rules. Mark unknown design rules instead of choosing one silently.

Pair before/after evidence using the same screen, data and viewport. Capture enough context to locate a defect and, where permitted, the actual displayed/accessibility text. A screenshot alone cannot establish focus order or what an assistive technology announces. Avoid claiming functional checks from static images.

Provide a concise defect record: case/profile, actual build/source identity, resource/call-site origin if known, expected versus observed result, evidence reference, severity basis and smallest reproduction. Keep “not run,” “blocked,” “observed pass,” and “observed defect” distinct. An unreachable state is blocked, not passed.

## Keep execution and cleanup explicit

The packet must identify the proposed execution environment and effects. Preparing it does not authorize a build, installation, device setting change, new account, source rewrite or live application operation. A later executor should use its applicable authorization and existing supported workflow. Do not embed instructions that enable pseudo-resources in production, change a real user's locale permanently or publish synthetic text.

Plan a separate disposable resource copy or developer build where supported. Record the original locale/settings, intended reset, and evidence that the normal configuration is restored after the review. Synthetic strings should be clearly labeled and excluded from release artifacts. If the platform cannot isolate the change, list that limitation before execution rather than assuming a safe rollback.

If the source or build changes before review, refresh the affected resource mappings and cases. Retain old evidence under its original identity; do not relabel a screenshot from an earlier build. If a generator corrupts syntax, stop that profile and preserve diagnostics; do not edit the damaged output until it appears plausible and then call the generation valid.

## Acceptance and stopping point

Before delivering the packet, inspect it as a reviewer would:

- Selected messages and states have explicit coverage or named gaps
- Each profile has a reproducible definition and protected-syntax contract
- Every planned observation has a setup, acceptance basis and evidence requirement
- Synthetic input values are safe and distinguish template stress from runtime-data stress
- Source/build versions, unknowns, pending execution and cleanup requirements are visible
- No planned result is reported as an observed pass, and no real-language certification is implied

Return the saved packet with the highest-risk cases and blockers summarized. The task is complete when the plan is internally coherent, saved and read back. If the user later requests execution, report each actual evidence layer separately: generation, native load, rendered layout, interaction/accessibility, restoration and real-language follow-on checks. A successful plan review is not a successful UI test.

For actual missing-glyph analysis, [audit-font-character-coverage](../audit-font-character-coverage/SKILL.md) provides a narrower mapping check; its result still does not prove shaping. For timed captions, use [caption-delivery-pass](../caption-delivery-pass/SKILL.md) rather than treating on-screen pseudo text as a synchronized caption track.

## Fictional, unexecuted illustration

A fictional Harbor file-picker has a `Save` button, a count-dependent summary and an error message containing a supplied filename. The proposed packet includes four case groups: baseline compact viewport, expanded button label, each reachable summary branch, and direction stress with the synthetic filename `report-17.txt`. The count argument and filename placeholder remain unchanged in the resource recipe; a separate long filename exercises runtime data.

The error screenshot reference is missing, so its layout check is marked pending screen mapping. The plan asks the future reviewer to capture full warning availability, actual resource/profile and dismissal behavior. It does not report clipping, a working RTL layout or a passing branch case.

No generator, application, device, build, screenshot capture or assistive-technology test was executed for this illustration.
