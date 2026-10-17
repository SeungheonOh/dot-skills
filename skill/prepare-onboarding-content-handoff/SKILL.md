---
name: prepare-onboarding-content-handoff
description: "Author an implementation-ready onboarding content packet for an established product flow, binding each instruction and action to eligibility, completion evidence, skip/resume rules and contextual anchors. Use for first-use or feature-learning content, not flow design, marketing copy or live onboarding execution."
---

# Prepare onboarding content that matches the person's actual progress

Deliver the exact first-use or feature-learning copy and the conditions that make it applicable. The packet connects each explanation, action label and progress statement to an existing product capability and checkpoint. Reading a tip, dismissing a tour, configuring a feature and successfully using it are different outcomes; the content must not collapse them into “Done.”

Use [design-user-interface](../design-user-interface/SKILL.md) when the entry points, sequence or interaction behavior still need deciding. Use [write-technical-guide](../write-technical-guide/SKILL.md) for a standalone how-to, and [change-log-release-notes](../change-log-release-notes/SKILL.md) for a release announcement. This workflow supplies state-bound in-product content for an accepted flow; it does not invent that flow, build a tutorial or measure activation.

## Establish the learning task and authority

Identify the product/version, audience, platform/locale, selected task, entry points and the observable useful outcome. Read the accepted flow, capability/availability rules, existing terms and labels, current onboarding content, checkpoints and interruption behavior. Include approved screenshots or component anchors, supplied length limits and the requested private destination.

Separate an instructional objective from a business effect. “Learn where exports are” can complete after a documented instructional interaction; “Create an export” needs the defined creation result. A product goal such as increasing activation does not establish what an individual has learned or authorize persuasive claims.

Preserve the agreed steps, permissions, optionality, terminology and exact policy wording. If a necessary rule is missing, produce the supported content and name the unresolved dependency. Do not invent eligibility, trial periods, storage lifetime, first-use tracking or a reminder schedule to finish the packet.

Use synthetic names and data in illustrations. Source screenshots can disclose customer records, accounts or unreleased features; include only approved context. Do not launch the application, create an account, request permissions, activate analytics, send invitations, import data or publish the content during this preparation task. Keep all copy and reviewer notes within the authorized audience.

## 1. Map applicability before drafting a sequence

Build a compact entry-and-eligibility map from the existing rules. Distinguish first app use, first use of a feature, an invitation into an already configured workspace, a returning incomplete session and an explicitly reopened tutorial. They may need different copy without requiring different product behavior.

For each entry, record the supported audience/role, feature availability, prerequisite state, owning account/workspace/device scope and evidence that selects the variant. A fresh device is not necessarily a new account; a new workspace is not necessarily a first-time person. Do not infer prior experience from age, demographic attributes or unrelated personal data.

Keep ineligible, temporarily unavailable and not-yet-configured distinct. A feature hidden by plan or role must not be taught as immediately usable. If the accepted design offers a supported alternative or a route to an owner, give its exact destination and effect; otherwise hold that action wording. Do not turn a learning step into an unrequested upgrade or invitation campaign.

Use the accepted content form: a short guided sequence, contextual tips, a setup checklist or a first-use empty state. Do not add all four. [Apple's onboarding guidance](https://developer.apple.com/design/human-interface-guidelines/onboarding) describes focused contextual instruction and optional tutorials as useful choices. Those principles support checking relevance, not imposing a new tour on an established product.

## 2. Bind each content unit to an action and checkpoint

Give each unit a stable ID and source reference. Include only fields needed by the chosen form:

- Entry condition and precise audience/state variant
- Content purpose and the single task or concept it explains
- Exact heading, body, primary action, secondary action and progress/status wording
- Existing screen/control anchor or verified destination; what to do when that anchor is absent
- Action effect, prerequisite and whether it can change real data or notify someone
- Completion evidence and the scope of the checkpoint
- Skip, dismiss, Back, resume and revisit rules as established
- Resource keys, parameters, translator context, owner decisions and revision

Use action labels that say what happens. “Continue” can advance instruction, but should not conceal sending invitations, granting access or committing a setup change. Distinguish a button that opens a settings screen from one that applies a setting. A deep link must match the supported platform and available capability; a plausible path is not verified navigation.

Separate essential setup from optional education. If the source makes a step skippable, preserve a clear skip label without guilt or a misleading consequence. If a prerequisite is genuinely required, explain what it enables and leave the decision rule with the accepted flow. Content cannot quietly make a mandatory requirement optional or an optional lesson mandatory.

Keep instructions local to the action they explain. An anchored tip needs an exact component reference and a supported alternate route when the anchor is hidden by layout, permission or state. Do not say “click the green button on the right” as the only identification. Include the exact control name and retain the task meaning across supported screen sizes.

Do not describe a real destructive or external action as safe practice. If the accepted flow uses sample data or a sandbox, identify that scope and its reset behavior. If it operates on real data, state the actual effect and use the established confirmation path. A playful tutorial label does not make an invitation or permission grant reversible.

## 3. Keep progress truthful across interruption

Create a small checkpoint-to-copy table. Use the product's real states rather than a compulsory universal vocabulary, but preserve distinctions such as unseen, displayed, dismissed, skipped, started, awaiting confirmation and confirmed complete when relevant.

Write down what can establish each state. Advancing a carousel proves only that the next slide was shown. Opening a configuration page does not prove it was saved. A recorded action may establish feature use without proving understanding. Never label a person proficient or a task complete from a view count alone.

For a checklist, distinguish the items that count toward setup completion from optional learning and unavailable items. Do not count skipped or excluded items as completed unless the accepted contract defines and explains that interpretation. A “3 of 4” denominator must identify whether it describes personal tasks, an eligible feature path or whole-workspace setup. A required owner task can remain a pending dependency in workspace progress even when the current member cannot perform it; do not silently omit it and claim the workspace is ready. If the number of future steps depends on an unsettled branch, use the supplied approximate/branch-aware pattern rather than inventing a fixed count. [WAI's multi-page form guidance](https://www.w3.org/WAI/tutorials/forms/multi-page/) discusses progress information for known and conditional sequences.

Resume copy must match actual retained state. Specify whether progress is stored only in the session, on the device or for the account/workspace, and what source establishes that. “Pick up where you left off” is unsupported if re-entry resets the flow. A changed workspace, revoked permission or deleted object can invalidate a prior checkpoint without erasing the historical action; keep current readiness separate from past completion.

Record the existing treatment of Back, close, interruption, sign-out and reopening only when those affect the content. Dismissal is not necessarily permanent suppression, and skipping a lesson is not completion of the underlying setup. If replay is supported, identify where it can be found and whether replay changes a real configuration or only instructional state.

For a later product revision, bind checkpoints to meaning as well as version. A punctuation edit should not automatically reset every person's progress; a new mandatory prerequisite may require a new state decision. Record the owner's migration rule or hold it. Do not implement a reset policy in the content document.

## 4. Keep explanations and variants implementable

Write complete strings with the established resource conventions. Include only necessary parameters, their sources and safe fallbacks. An unknown workspace name should not create empty quotation marks, and a missing completion count should not become zero. Keep complete translatable messages instead of concatenated fragments; mark genuinely protected product/control labels.

Make visible and accessible text equivalent in task meaning. A visually short step title may need context, but the accessible version must not promise a stronger outcome. Record intended heading/description associations and useful reading order without claiming that a tooltip or overlay is keyboard-accessible. Focus handling, announcement behavior and actual assistive-technology support need implementation checks.

Preserve system-owned permission text. App-authored explanations may describe the specific supported need, but must not imitate the operating system's approval dialog or claim that permission has been granted. State the known route after refusal without pressuring the person or directing an unsupported settings change. Do not introduce data access or terms acceptance as an editorial convenience.

Use measured time or burden estimates only when evidence supports the applicable task and audience. “Takes 30 seconds,” “never lose your work” and “ready for everyone” are product claims. If the source does not establish them, omit them or hold the claim rather than making onboarding sound effortless at the expense of accuracy.

## Acceptance and recovery

Return an editable content inventory, applicability/checkpoint map and a concise list of open decisions. A small flow can fit in one file. Keep operator conditions and review comments separate from ready-to-use strings.

Read the saved packet back and trace representative paper paths: eligible first use, skip/dismiss, interrupted return and a relevant unavailable or already-completed case. At each step, compare the copy, actual permitted action, retained state and next checkpoint. These are specification walkthroughs, not observed user journeys.

Check that:

1. Every selected unit has exact copy, an applicability rule and a real anchor/destination or explicit hold
2. Every completion/progress statement has the right evidence and identity scope
3. Optional education and required setup retain their accepted distinction
4. Skip, resume and revisit wording agrees with persistence and suppression behavior
5. Capability, permission, data-loss and time claims remain supported
6. Resource IDs, parameters and task meaning survive all audience/state variants

Prepare downstream acceptance cases with starting state, synthetic values, expected content, action effect, completion evidence and restoration obligations. Mark rendering, navigation, storage, keyboard, assistive-technology and participant-comprehension checks unrun until actually performed. Do not claim improved conversion or reduced support burden from a well-formed packet.

If the flow changes, refresh the affected anchor, action and checkpoint together; do not update only the welcome paragraph. Preserve earlier revisions and concurrent editorial work. Inspect an uncertain save before retrying. If an anchor or persistence rule is unknown, deliver supported strings with the exact missing dependency rather than silently inventing behavior. Stop when the content handoff is usable; implementation, notification, experimentation and publication need their own scope.

## Fictional, unexecuted illustration

A fictional planning app has two required setup tasks and one optional tutorial. Its supplied rules say that workspace members can name a draft, only owners can configure sharing, and tutorial dismissal is remembered per account. Setup completion requires acknowledgments for both required tasks; the tutorial does not count.

The member variant offers “Name your draft” and explains that an owner must complete sharing setup, using an existing owner-contact route only if supplied. Dismissing the tutorial records no setup success. On return after a confirmed saved name, the copy identifies that task as complete and the remaining setup as pending. It does not announce “You're all set” because a tutorial was dismissed or a settings page was viewed.

This is an authored illustration. No app, account, checkpoint store, permission dialog, analytics event or user study was accessed or executed.
