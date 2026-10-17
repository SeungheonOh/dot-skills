---
name: record-architecture-decision
description: Create or revise a source-linked architecture decision record that preserves the decision's scope, rationale, status, consequences and relationship to earlier decisions. Use for a durable decision history, not an open-ended options recommendation or implementation plan.
---

# Record an Architecture Decision

Turn an agreed or proposed technical choice into a short record that a future teammate can understand without the original conversation. Explain what was chosen, why it made sense under the stated constraints, what it costs, and what evidence establishes its status. An architecture decision record (ADR) records a choice; it does not approve, implement or validate it.

Use [decision-source-brief](../decision-source-brief/SKILL.md) when the main task is choosing between options. Use [code-review-handoff](../code-review-handoff/SKILL.md) when the main task is explaining one patch to a reviewer. An ADR may link both artifacts without duplicating their full analysis.

## Inputs and output boundary

Find these in the request and authorized material:

- The system or component, one decision to record, and the intended readers
- Relevant requirements, dated discussion or decision notes, and the actual alternatives considered
- Any existing ADR, identifier convention, template and decision-authority rules
- Evidence of acceptance, rejection or replacement, if a completed decision is claimed
- The requested destination and whether this is a private draft or an authorized repository/document edit

Do not require a full architecture document to record a narrow decision. If sources are incomplete, draft the supported parts and mark the specific gap. If there is no evidence of a decision, use the project's proposal status or clearly label the result a proposed record. Do not invent consensus, an approver, a meeting date or an explanation for someone else's choice.

Read relevant authorized sources directly. Keep private discussion, vulnerabilities, customer examples and operational details within the approved audience. Prefer a restricted source reference and a minimal factual summary over copying a confidential conversation. Remove credentials and credential-bearing URLs entirely. Publishing the record or changing an accepted record needs authority for that destination and scope; preparing it does not contact participants.

## 1. Pin the decision and its history

Write the question as a bounded choice: for example, where one service keeps short-lived export jobs, rather than how the entire platform should be built. Identify the affected component and version or time window when relevant. Separate the decision date from the date the record is being written. A retrospective record must say it was reconstructed later.

Inspect nearby records before assigning an ID. Follow the repository's convention, preserve stable identifiers and do not renumber old records for tidiness. If another author may allocate the next number concurrently, use a clearly provisional filename until the destination can be rechecked. Verify references to earlier decisions rather than guessing their titles or status.

Use the team's actual lifecycle. As a common reference, [AWS's ADR process](https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/adr-process.html) distinguishes proposed, accepted, rejected and superseded records, keeps context/decision/consequences together, and treats a changed accepted decision as a new reviewed record. That is a useful model, not permission to impose a new governance process on this project.

Record the status evidence separately from implementation evidence:

- An authorized decision or recorded approval can establish acceptance within its stated scope
- Merged code can establish that a change landed, without proving who agreed to its architecture
- An accepted ADR can remain partly unimplemented
- Silence, positive reactions from unspecified people, or an author's preferred wording do not establish team acceptance

Where sources conflict, preserve the disputed scope and dates. Ask only for the missing decision authority or fact that changes the record's status; continue the supported content meanwhile.

## 2. Extract the reasoning without rewriting history

Build the smallest evidence chain that explains the choice:

1. **Context:** the requirement or constraint that forced a choice, including relevant scale, compatibility, operational or team limits supplied in the sources
2. **Decision:** the selected or proposed approach, its affected boundary, and any explicit exclusions
3. **Alternatives:** the real options considered and the consequential reason each was not selected; include keeping the current approach if it was genuinely considered
4. **Consequences:** benefits, costs, new responsibilities, limitations and accepted risks
5. **Revisit conditions:** an observed change or unresolved assumption that would justify reopening the decision, if the sources or requested analysis support one

Attribute historical reasons. If an alternative's rejection rationale is absent, write that it was not recorded. Do not make the final choice appear inevitable by inventing a weak alternative. Keep a new observation or recommendation distinct from what was known at the decision time.

Separate demonstrated facts from expectations. A benchmark needs its actual version and conditions; a forecast remains a forecast. “Will reduce latency” should not replace “chosen to reduce latency; measurement pending.” Do not turn a design preference into a contractual guarantee, a compliance claim or a new service commitment.

Give technical terms a short plain-language explanation where the audience needs it. Preserve the precise tradeoff: “jobs survive a worker restart but need a cleanup owner” is more useful than “robust and scalable.” Keep implementation detail only when it explains the decision boundary or a consequence; link longer designs and task lists.

## 3. Preserve accepted decisions when revising

Distinguish three requests before editing:

- **Clarify wording or repair a source link:** keep the decision and its original status/date intact, follow local amendment conventions, and record a material clarification when required
- **Fill missing historical evidence:** add attributed evidence and its discovery date without pretending it was recorded earlier
- **Change the decision:** prepare a new proposal with the exact earlier decision it would replace and the new reason; do not silently rewrite the old rationale

For a replacement, distinguish “proposes to supersede” from “supersedes.” Apply the latter only when the new decision has the required acceptance evidence and the edits are authorized. Keep the old content reachable, add the reciprocal relationship where the project's convention calls for it, and check that no record points back to itself or creates a replacement cycle. A partial replacement must name the affected scope; it must not retire unrelated parts of the earlier decision.

If no existing convention addresses partial replacement or amendments, propose a small explicit representation rather than changing the whole decision log. Writing an ADR does not authorize code changes, tickets, reviewer invitations, branch changes or a new recurring review schedule.

## 4. Save a usable record and check it

Deliver the actual editable Markdown or the requested native document. A compact record normally contains:

- Stable/provisional ID, useful title, status and decision/record dates
- Component and scope, decision owner or owner unknown, and status evidence
- Context, decision, real alternatives and consequences
- Unresolved assumptions or revisit conditions that materially affect use
- Source references and any earlier/later record relationship

Reuse the local template when present. Do not add empty ceremony to a one-page decision. Read back the saved artifact and verify:

1. A new reader can identify the choice, its boundary and its most important tradeoff
2. Each claimed approval, historical reason and decisive fact has an appropriate source or visible uncertainty
3. The status does not overstate either acceptance or implementation
4. IDs, dates, titles and replacement links agree with the referenced records
5. The requested audience can access the sources needed to interpret the record, or missing access is explicitly identified without widening permissions
6. No private conversation, secret, unapproved promise or unrelated system detail has been copied into the deliverable

If saving fails, retain the private draft and report the exact blocked destination. If an existing record changed concurrently, compare the newer version and reconcile only the requested edits; do not overwrite it from an older copy. If a source is unavailable, retain its locator and the unresolved claim instead of fabricating a quotation or status. Stop when the record is usable and its remaining decision gaps are clear; implementation is a separate outcome.

## Illustration: fictional and unexecuted

Suppose the supplied notes say that the team discussed a shared queue versus an in-process job list for export jobs. A designated owner approved the shared queue for exports only on 2026-10-12; a separate analytics service was outside the discussion. The notes say exports should survive worker restarts, but no recovery test result is supplied.

The record would state the scoped accepted decision and cite that approval, explain the durability goal as rationale, and list recovery verification as pending. It would not assert that recovery works or apply the choice to analytics. If a later note merely proposes replacing the queue, the existing record remains accepted while the new record is proposed.

This is an authored illustration, not a performed review, source inspection, approval or implementation. Record the actual evidence and checks for each real use.
