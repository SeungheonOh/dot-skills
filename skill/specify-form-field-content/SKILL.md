---
name: specify-form-field-content
description: "Prepare a field-by-field content contract for an established product form, binding labels, hints, choices, units and validation messages to settled answer rules and stable control identities. Use for implementation copy handoff, not questionnaire design, form filling or building controls."
---

# Specify form content that matches the accepted answers

Deliver the actual strings an implementer needs, with the rule each string explains and its exact field association. The artifact is a content contract for an already defined form: it keeps labels, persistent help, choices, conditional instructions and validation copy consistent with the underlying answer meaning. It does not redesign what information the form collects.

Use [design-questionnaire](../design-questionnaire/SKILL.md) when deciding what to ask or what answers mean. Use [source-backed-form-fill](../source-backed-form-fill/SKILL.md) to enter someone's answers. Use [keyboard-form-completion-check](../keyboard-form-completion-check/SKILL.md) for an actual completed journey. This handoff authors product copy and records implementation obligations without creating a form or claiming live accessibility.

## Inputs and preservation

Identify the form/flow and revision, audience and locale, existing controls/resource keys, accepted question/answer specification, field constraints and branch rules. Include approved terminology, mandatory exact wording, screenshots or design references, existing error conditions and the requested editable destination. Separate supplied rules from observed implementation and proposed copy.

Use those sources before asking questions. Missing brand tone need not block a plain-language draft. Missing requiredness, units, a date convention or allowed choices can change meaning; hold that dependent string and ask the smallest question. If the field specification and validator disagree, expose the disagreement rather than selecting the more convenient rule.

Preserve field IDs, storage/export values, input types, existing resource keys, approved wording and unrelated editorial work. A content request does not authorize changing validation, requiredness, defaults, data collection or consent. Do not type sample values into live forms, submit responses, modify collection settings or upload screenshots to a new service. Use synthetic samples and keep source excerpts within the approved audience.

## 1. Establish one identity per answer

Create one contract row or compact section per logical answer. Use existing stable control/field IDs, with page/group and repeated-item context. Repeated labels such as “Title” need distinct bindings when they describe different objects. Separate a logical answer from several controls that represent it, such as a date's day, month and year inputs.

Record only relevant columns:

- Field identity, source locator and question/answer meaning
- Visible label or group legend; any component labels
- Required, optional, conditional or read-only status and its evidenced trigger
- Persistent help, units/format guidance and optional example
- Displayed choice labels mapped to unchanged stored values
- Validation-condition IDs, exact messages and applicable summary references
- Resource keys, parameter definitions, translator context and supported length constraints
- Placement/association notes, unresolved decisions and proposed-versus-approved status

Do not confuse unknown, blank, explicit none, zero and not applicable. Copy must communicate the distinctions already defined by the instrument. An empty dropdown option is not automatically an answer called “None,” and an example must not become a default submitted value.

## 2. Allocate each piece of meaning to the right text

Make the label identify what answer is being requested. Put a short essential unit or disambiguator there when needed, and keep longer instructions in persistent help. Use group wording to establish shared context and component wording to distinguish the individual inputs. Do not repeat an entire paragraph in every accessible name.

Keep essential help available while the person reviews an entered answer. [WAI's form-instruction guidance](https://www.w3.org/WAI/tutorials/forms/instructions/) explains why a disappearing placeholder cannot carry the only format instruction. Treat examples as examples, not proof of the only accepted syntax or a hidden default. Do not force every field to have placeholder text.

Write requiredness consistently with the product's existing convention. If a field becomes required only for an active branch, bind the text to that branch. A required marker must not survive after the field becomes optional or irrelevant. Do not use an unexplained symbol as the entire instruction.

For choice controls, preserve exact answer distinctions and stored-code mappings while improving approved display wording. Never merge two options merely because their labels seem similar. Keep an exclusive option such as “None of these” distinct from an unanswered multi-select, using the already settled selection rule. If that rule is absent, report it rather than solving it in copy.

Use the [WAI labeling guidance](https://www.w3.org/WAI/tutorials/forms/labels/) as a basis for the intended label/control association. Record which text names the field and which text describes it. For controls with visible text, the accessible name should retain that wording rather than introduce a contradictory synonym. Leave exact platform markup and computed-name verification to the implementer; a string inventory alone does not establish the result.

## 3. Preserve the actual input contract

Translate each established constraint into only the guidance needed to enter a valid answer. Check meaning against the rule, not against what a typical form usually accepts:

| Constraint | Content decision |
| --- | --- |
| Quantity | State the unit and meaningful precision; distinguish an amount from a count |
| Range | Preserve inclusive/exclusive boundaries and whether the range is fixed or contextual |
| Date or time | State the supplied interpretation and timezone when needed; do not infer a numeric date format from language alone |
| Identifier | Preserve leading zeroes, case and permitted separators; do not describe it as an arithmetic number merely because it uses digits |
| Length | Use the actual measurement unit, such as characters or bytes, and an owner decision when that unit is unspecified |
| File | Keep accepted types, size units and per-file versus total limits distinct |
| Sensitive input | Preserve approved rationale and handling language; do not invent retention, encryption or anonymity promises |

If a UI label says “characters” but the validator counts bytes, mark that mismatch. Do not silently rewrite the rule or imply every writing system has the same length behavior. A character count also does not establish a rendered-width limit. Keep conservative copy pending the owner's chosen contract when ambiguity affects acceptance.

Clarify whether punctuation or spacing is accepted, normalized or prohibited only when established. Do not forbid reasonable names, international addresses or formats by extrapolating from one example. Conversely, do not promise flexible input that the current consumer rejects. Keep unsupported compatibility improvements as separate proposals.

Do not add privacy-policy, attestation or consent language casually. Carry exact approved consequential wording and its reference unchanged unless a revision is specifically requested and appropriately reviewed. Optional data must not be described as compulsory to nudge completion.

## 4. Match guidance and validation across states

Derive validation messages from actual conditions: missing required answer, unsupported format, out-of-range value or cross-field mismatch. A single “Invalid value” does not explain correction. Name the relevant field using the label people can find, and preserve the same rule in help and error text.

Record the existing validation timing and precedence where they affect copy. A newly focused empty field is not necessarily an error; an optional blank differs from a nonblank invalid answer. Do not add on-every-keystroke validation or reorder checks through the content specification. If multiple conditions can apply and no selection rule exists, identify that integration decision.

For a grouped or cross-field constraint, state which controls the message describes and the supported correction. Do not arbitrarily blame the final field when either answer could be revised. Keep the error summary, inline text and association locators aligned. Avoid messages that rely only on “above,” color or visual position.

Conditional fields need two distinct rules: whether the answer is currently applicable and whether a previous value is retained. Copy such as “Your previous answer is saved” requires evidence of that retention and its scope. If a branch hides a field, its prior value must not silently become an active answer in the handoff. Record the existing treatment without changing it.

Keep field validation separate from service failure and submission outcome. A locally valid answer is not necessarily accepted by the server. A summary can say which answers need correction, but cannot claim that the submission was received. Use the established operation-level contract for those outcomes.

## 5. Package and check the content handoff

Provide actual copy, not only writing advice. For each selected field, give the resource identity or proposed identity, full strings, condition-specific variants and association notes. Keep editor questions outside ready-to-use strings. Reuse a resource only when meaning, grammatical role and future revision ownership genuinely match; two controls with the same English label may still need separate keys.

Include translator context for units, placeholders, option meaning and gender/plural requirements that matter. Preserve existing interpolation syntax. Do not generate a target-language resource or import package unless requested; [translation-release-review](../translation-release-review/SKILL.md) handles translation and its separate checks.

Read the saved artifact back and reconcile it to the accepted field specification:

1. Every selected logical answer and control has the required content binding or an explicit gap
2. Labels, hints, examples, choices and messages express the same units, range and answer meaning
3. Choice labels preserve stored values, and optional/conditional/absence states remain distinct
4. Persistent help carries essential instructions; error and summary references identify the right field
5. Protected wording, keys, parameters and unrelated content remain intact
6. No unknown rule or unverified privacy claim appears as finalized copy

Prepare downstream cases for the ordinary answer, each meaningful constraint boundary and a changed conditional branch where present. State synthetic inputs, expected copy variant, preserved answers and intended field association. These are acceptance instructions, not executed validator, layout, keyboard or assistive-technology results.

If the source changes, revise affected help and error strings together and flag downstream translations that may be stale. On an uncertain save, inspect before retrying; preserve parallel edits. If a requested length cannot preserve essential meaning, return the complete candidate and the specific space/meaning conflict rather than truncating a rule. Stop with a usable content contract and named holds; implementation, collection and publication require their own scope.

## Fictional, unexecuted illustration

A fictional workshop form already defines `tool_code` as six digits with leading zeroes preserved. `pickup_note` is optional and applies only when the agreed delivery choice is collection; the source says inactive notes remain draft-only.

The candidate label is “Tool code,” its persistent hint is “Enter the six-digit code shown on the tool,” and the example is `001274`. Missing and wrong-length messages refer to “Tool code” separately. The pickup note is marked optional only in the active branch, and the contract states that an inactive saved draft note is excluded from the current answer set. None of these copy choices changes the validator or creates a new default.

This is an authored content illustration. No form, validator, resource file, browser, submission or user test was created or executed.
