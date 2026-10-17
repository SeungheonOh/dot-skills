---
name: prepare-product-demo
description: "Prepare a presenter-ready demonstration of an existing product or workflow, with an audience-specific scenario, action-and-observation cues, required sample state, timed cuts and an honest fallback. Use for a demo packet, not slide creation, user research, functional QA or executing a live demonstration."
---

# Prepare a product demo the presenter can actually follow

Deliver a usable demonstration packet that connects what the audience needs to understand to specific actions and observable results. It should tell the presenter what to say, what to show, what must be ready and how to continue truthfully if the planned path is unavailable. A list of features or a marketing script without a working route is insufficient.

Use [source-backed-presentation](../source-backed-presentation/SKILL.md) for a slide deck, [test-user-journey](../test-user-journey/SKILL.md) for executing functional checks, and [prepare-user-research](../prepare-user-research/SKILL.md) for neutral tasks that study participants attempt. A demonstration teaches or explains a selected path; it is not evidence of unaided usability, overall product quality or production readiness.

## Establish the audience and demonstrated claim

Read the user's brief and the existing product material. Identify the audience, their task or decision, current familiarity, available time, delivery setting, and requested artifact. Preserve a specified product, scenario and level of technical detail. Ask only when a missing audience or outcome changes which path is useful.

Choose the smallest coherent scenario that shows the requested value. Write its starting situation and the outcome the viewer should understand. Include required limitations next to the claim they qualify; do not convert a prototype, configured workaround or planned feature into a generally available capability.

Pin the available product version/build, environment, account role, feature configuration and source evidence as far as supplied. Distinguish official behavior descriptions, existing screenshots or recordings, reports of a prior rehearsal and current observations. Read current official documentation when a version-specific control or claim needs it; do not invent a menu path or success state from a familiar product name.

If only static material is available, prepare a clearly labeled narrated walkthrough. If the user requires a live path that cannot be established, deliver the usable script and precise live-readiness gap. Do not substitute a mock screen and describe it as a functioning product.

## Write the scenario and presenter cues together

Build the narrative around the audience's task rather than a tour of every control. Establish the problem briefly, show the consequential action, inspect its result and explain what changed. Choose an appropriate level of detail: a new user needs orientation, while an integrating engineer may need the exact input, output and boundary condition.

For each meaningful beat, provide enough information for another presenter to follow it:

- Purpose or audience takeaway
- Starting screen/state and exact sample object or prepared material
- Presenter action, including the relevant control or step when established
- Short spoken cue that explains why the action matters
- Expected visible result and the evidence that supports expecting it
- Any side effect, wait/completion signal, branch or stop point
- Fallback reference and what it can honestly demonstrate

Keep narration and operating instructions visually distinct. An action such as “show the result” needs a recognizable result; a success toast may not establish saved content or completion. Make preparation dependencies explicit so a presenter does not discover halfway through that a sample must already exist or another role must act first.

Preserve the difference between input and outcome. A pre-populated record is sample setup, not something created during the demonstration. A recorded result belongs to its recorded version and conditions. A diagram can explain a process without proving that the product performed it. Name these distinctions in the cue where the audience could otherwise be misled.

Prepare an essential route and optional extensions only when useful. If time is reduced, cuts must preserve the setup and result needed to understand the claim. Do not skip an unseen prerequisite and pretend the shortened route still demonstrates the same end-to-end behavior.

## Prepare safe and repeatable sample conditions

List the required starting state, approved sample records/assets, account role and known environment dependencies. Prefer fictional or explicitly approved minimized data appropriate to the audience. Keep sample identities consistent across the scenario; do not reuse a real customer's name simply because the screenshot looks convincing.

Describe how the starting state could be restored using supported, authorized steps. A reset plan must identify what it would change and preserve. Do not propose deleting arbitrary records, clearing an entire workspace or undoing other people's edits merely to make another rehearsal easy. If reset behavior is unknown, plan a fresh isolated sample or a read-only route and label the dependency.

Treat every demo action according to its real effects. A sandbox label does not establish that payments, email, webhooks, publication or integrations are disconnected. Mark any action that could affect another person or a live system, and hold it until the specific authority and suitable environment are established. A preparation request does not authorize creating accounts, uploading data, changing permissions, disabling integrations or running the scenario.

Keep authentication out of the visible narrative where possible. Never place passwords, tokens, recovery codes or credential-bearing URLs in the runbook or backup materials. Describe access prerequisites without collecting secrets. If a live sign-in is unavoidable, identify a private pause or handoff; do not write instructions to bypass a warning or display a credential.

Inspect the proposed display and fallback material for unintended disclosure: other tabs, notifications, recent items, search results, personal paths, collaborator names, speaker notes and hidden metadata can expose unrelated content. Propose a limited display surface within the user's supported setup. Do not change notification, privacy or recording settings merely because the packet recommends checking them. Recording and audience sharing require their actual approval.

## Design an honest fallback and question boundary

For the likely blockers that matter to this demo, give an observable trigger and a bounded response. Examples include unavailable network access, expired session, changed UI, delayed processing or a missing sample. Distinguish a supported retry from a possible duplicate operation; after an uncertain write, inspect its outcome before any repeat.

A fallback should identify the exact approved screenshot, recording, artifact or explanation and what claim it supports. Include its version/date and known differences from the planned live path. If no fallback material exists, give the wording that acknowledges the limit and the next supported topic; do not claim a recording is ready.

Never present prerecorded material as live execution, edit out a consequential failure to imply a successful uninterrupted run, or use fabricated data as a real customer result. A fallback can preserve the explanation while leaving the live claim unverified.

Prepare a short question sheet for likely audience needs grounded in the scenario: prerequisites, availability, limits, data handling and next steps. Separate an answer supported by evidence from a question to take away. Do not invent a roadmap date, delivery promise, price, contractual assurance or security certification to make the demonstration persuasive.

## Fit the packet to the real time budget

When a duration is known, allocate room for setup/context, the essential path, explanation of results, and requested questions. Label durations as estimates unless measured from a real supplied rehearsal. Check their total and preserve any fixed ending time. Reading speed estimates do not establish actual click, load or discussion timing.

Give the presenter usable cut points and a recovery cue if a wait exceeds the available budget. A cut point should leave the audience with a complete supported takeaway. Avoid brittle instructions such as waiting a fixed number of seconds and then announcing success without observing a completion signal.

Provide a rehearsal checklist or blank observation record when it helps: exact version and sample, start state, step attempted, actual result, timing, unexpected disclosure, remaining state and revision needed. Keep it blank unless real rehearsal evidence is supplied. A desk review of instructions is not an executed demo, and an executed demo is not a broad functional test.

## Deliver, check and maintain the exact packet

Return the presenter script/runbook, setup checklist, essential/optional route, fallback references and concise unresolved readiness items. Combine them into a compact document for a short demo. Include an audience-facing handout only if requested; private operating instructions and evidence notes need not travel with it.

Walk through the document from the actual stated starting conditions. Check that:

- Every claimed takeaway has a demonstrable observation or a clearly labeled explanatory substitute
- Every step's input or starting state is available, derived from a prior step or explicitly pending
- Spoken cues match the shown capability, version and sample status
- Consequential actions and reset steps preserve their authority and side-effect boundaries
- Time cuts preserve the selected claim, and fallback material is real or explicitly still needed
- No invented rehearsal result, user reaction, performance gain or production guarantee appears

Save to the authorized destination, reopen the actual copy, and check referenced assets, link targets, cue ordering and version/status labels. Verify that any intended audience may receive the included content without broadening permissions. If a save is uncertain, inspect the destination before retrying. Preserve the prior packet and actual rehearsal records when revising for a changed build, audience or duration; refresh only the affected claims and steps.

Stop at the requested preparation or evidence-based revision. Conducting the demo, contacting attendees, recording, publishing assets, changing the product or running a rehearsal with external effects needs its own scope and authority. A completed packet establishes prepared materials, not a successful live demonstration.

## Fictional, unexecuted illustration

A fictional team wants a six-minute demo of an existing review tool. The selected scenario is finding an overdue sample item and reading its review history. The supplied product notes say the final “Send reminder” action emails a real address, even in the training workspace.

The essential route shows the sample filter and history, then stops before sending. The cue describes the email action as available but unexecuted. A supplied recording from the prior build can explain the reminder screen only if its older version is disclosed; it cannot prove today's live delivery. The packet reserves a short question period and lists current-build rehearsal as pending.

No account, setting, sample record, email or recording was changed. This invented plan illustrates a usable demo that preserves an important action boundary without pretending the blocked step succeeded.
