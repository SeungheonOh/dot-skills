---
name: create-github-issue-form
description: "Turn an agreed intake or handoff process into a reviewable GitHub issue-form YAML file, checking field semantics, repository defaults and publication boundaries. Use for authoring reusable forms, not filing a particular issue or diagnosing its contents."
---

# Create a GitHub issue form people can finish

Produce the actual form definition and a concise review of how answers become an issue. The useful outcome is a reusable intake interface for work requests, project handoffs or bug reports. A prose questionnaire or one completed ticket does not replace the YAML configuration.

Use this when GitHub is the chosen intake destination and the questions are substantially agreed. If the main problem is deciding what to ask, use [questionnaire design](../design-questionnaire/SKILL.md) first. For one reported defect, use [bug reproduction triage](../bug-reproduction-triage/SKILL.md). Issue forms are not pull-request forms; GitHub describes their responses as editable Markdown issue content, not a permanent structured database record. See [issue-form syntax](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-issue-forms).

## Establish the target and action boundary

Resolve from the request and repository:

- Repository, GitHub product/version when relevant, visibility, default branch and existing `.github/ISSUE_TEMPLATE` files
- Form purpose, intended respondents, settled questions, needed answer distinctions and any approved default values
- Whether the deliverable is a local draft, a repository change or an activated form; identify the permitted branch and publication route
- Existing labels, assignees, issue types, projects and support/security links that the user actually wants this form to use
- Any downstream reader that relies on current headings, field IDs, title prefixes or option spelling

Read current templates and relevant contribution instructions before adding a competing form. Inspect repository facts through available read-only tools; do not ask the user to restate discoverable configuration. If no repository is available, produce a neutral local definition without guessed labels, people or links, and mark repository checks unverified.

Do not change issue access, disable blank issues, remove an existing template, create labels, assign people, add projects or introduce agreements merely to make the new form feel complete. Those are separate effects. A draft request does not authorize committing, merging, opening a test issue or collecting responses. Honor existing authorization for the requested file change without repeatedly asking for it.

## Map answers to the next action

Create a small field map: stable ID, visible label, control type, answer meaning, requiredness and any downstream dependency. Preserve agreed wording and semantics; do not turn a suggested deadline into a commitment or a requester's self-assessment into an approval.

Use short text for a single fact, a textarea for a meaningful narrative, and a dropdown only when the alternatives are genuinely bounded. Offer an explicit unknown/not-applicable option when the intake must accept it. A required field must not force a requester to invent an identifier, run a risky command or disclose private records.

Keep placeholders as examples, not pre-filled answers. Defaults that look like real answers can survive submission unnoticed. Use an unchecked optional checkbox for an optional assertion; never silently add a mandatory policy acceptance, legal declaration or consent claim.

If answers require conditional branching, repeated rows, arithmetic or cross-field validation, check the current native schema before promising it. Do not invent YAML keys to simulate unsupported behavior. Offer a simpler explicit instruction, an agreed split into separate forms, or a different implementation only when that choice materially matters.

Put an appropriate privacy warning near logs/screenshots. Do not request tokens, passwords, full environment dumps or private customer content. If confidential reports need another route, use a verified existing destination; do not invent an address or promise that ordinary issues are confidential.

## Write the actual YAML

Save a new, deliberately named `.yml` or `.yaml` under the proposed `.github/ISSUE_TEMPLATE/` path. Preserve unrelated templates and `config.yml`. Use ordinary scalar strings, mappings and lists, without custom tags or unnecessary anchors.

Implement the verified schema:

- Include `name`, `description` and a `body` array; keep the chooser name distinct from existing templates
- Give each input a stable unique ID using the supported character set; use visibly distinct labels so the eventual issue remains understandable
- Put control settings under `attributes` and applicable checks under `validations`; check each control's supported keys independently
- Keep explanatory Markdown separate from answer fields. Static Markdown helps the respondent but is not submitted as an answer
- Use YAML quoting or block scalars for punctuation, multiline instructions and values that could otherwise become booleans or numbers
- Set checkbox-option requiredness at the documented option location, rather than assuming it has the same shape as a text field's validation

Consult the current [form schema](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-githubs-form-schema); it is marked public preview. GitHub currently documents `required` for several input types as applying only to public repositories. Do not promise equivalent enforcement in a private repository or an older Enterprise Server version without checking that target.

Optional routing defaults must reflect verified repository objects and user intent. A label name in YAML does not create the label. Omitting unrequested assignees and project settings is preferable to guessing a team or imposing automatic work assignment. Preserve IDs and headings used by downstream consumers unless the requested change covers that migration.

## Review syntax, meaning and activation separately

Read the saved file, not only the proposed text. Use an available safe YAML parser when execution is authorized, rejecting duplicate mapping keys. If only static inspection is permitted, report that limit and do not call it parser-validated.

Check the parsed or inspected structure against GitHub's current documented keys. Check at least one input field, unique IDs, appropriate types, nonempty labels, valid options and default values, indentation and unexpected coercion. GitHub's [validation-error guide](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/common-validation-errors-when-creating-issue-forms) is useful for duplicate or similar labels, checkbox labels and invalid body entries. A generic YAML parse does not establish GitHub acceptance.

Walk the form with fictional answers without submitting them:

1. An ordinary request supplies enough evidence for the intended next step
2. A valid requester with an unknown answer can finish truthfully
3. An optional blank stays optional, and no default becomes a false assertion
4. The proposed issue body keeps the important labels and answer distinctions

A hand-written body preview is a prediction. Label it as such. A real GitHub preview, if available and within scope, gives stronger rendering evidence but still does not prove submission or every validation rule. Creating a test issue can notify people and trigger automations; do it only when that action is authorized, with synthetic data and the exact destination established.

For publication already requested, use the approved change route and read back the exact saved file and revision. A branch or pull request is not an active default-branch template. GitHub's [configuration guide](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository) explains template activation and chooser configuration. Do not merge merely to test activation unless merging is authorized.

## Failure handling and deliverable

If GitHub rejects the form, preserve the error and file revision, map it to the affected field, and correct that cause within scope. Do not remove required meaning or disable validation blindly. If publication returns an uncertain result, inspect the destination branch before retrying. Do not create another issue, commit or pull request to discover whether the first one succeeded.

Return the actual YAML file or reviewed repository diff, intended path, field/behavior summary and exact verification level. Name unresolved repository dependencies and whether the form is only drafted, present on a branch, or observed in the active chooser. Stop at that requested boundary; response collection and issue handling are separate work.

## Fictional example, not executed

A team asks for a reusable work-handoff form. Its settled questions are the requested outcome, relevant artifact links and anything still blocked. No automatic assignee, label or project is requested. A candidate definition is:

```yaml
name: "Work handoff"
description: "Describe an outcome and the material needed to continue it."
title: "[Handoff] "
body:
  - type: markdown
    attributes:
      value: "Include only material appropriate for this repository's audience."
  - type: textarea
    id: requested-outcome
    attributes:
      label: "Requested outcome"
      description: "What should the next person be able to finish?"
    validations:
      required: true
  - type: textarea
    id: artifact-links
    attributes:
      label: "Relevant artifacts"
      description: "Link the reviewed versions, or state that none are available yet."
    validations:
      required: true
  - type: textarea
    id: blockers
    attributes:
      label: "Open decisions or blockers"
      description: "Leave blank if there are none."
    validations:
      required: false
```

This illustrates a draft at `.github/ISSUE_TEMPLATE/work-handoff.yml`. It has not been parsed, committed, previewed or submitted. An eventual report must distinguish those actual checks, and must not describe the form as live merely because this example exists.
