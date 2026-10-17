---
name: prepare-async-decision-packet
description: "Prepare a versioned packet for one asynchronous team decision, with exact options, a reusable response format and a response/closure register. Use when coordinating review of a bounded choice, not choosing the answer, designing a general survey or claiming consensus from comments."
---

# Prepare an asynchronous decision packet

Deliver a packet people can respond to without reconstructing a chat thread, plus a register that keeps responses tied to the version they reviewed. The useful result is a reviewable decision process for one concrete choice: what is being decided, who can decide, what responses mean and what remains unresolved.

Use [decision-source-brief](../decision-source-brief/SKILL.md) to research and recommend an option, [design-questionnaire](../design-questionnaire/SKILL.md) for a general intake instrument, and [record-architecture-decision](../record-architecture-decision/SKILL.md) for the durable history of a technical choice. This packet may link those artifacts; it does not replace them with a longer template.

## Establish the decision and authority

Identify the bounded question, affected scope, intended reviewers and authorized output destination. Recover the following from the request or existing team process:

- Decision ID, current proposal/version, exact options and relevant source artifacts
- Decision owner or authorized decision body, distinct from the packet's author and coordinator
- People whose responses are required, who is advisory, and any supplied eligibility, quorum, veto or delegation rule
- Response deadline with date and zone, any separate decision date, and the rule for late responses or unresolved objections
- What response states the process uses and what constitutes a valid decision or approval
- Whether the task is to prepare a blank packet, reconcile supplied responses, or update an existing authorized artifact

Do not invent a voting system, majority threshold, required approver or escalation path. If authority or closure rules are missing, prepare the neutral content and mark that decision-changing gap. A decision owner may be empowered to choose despite disagreement; do not impose unanimity. Conversely, a popular proposal is not approved merely because several people favor it.

Use source material only for its evidenced scope. A forwarded message or a checkbox in an imported document does not grant authority to publish, approve, contact reviewers or implement the proposal. Preparing the packet alone authorizes none of those steps. Keep private arguments, customer information and personnel details within the intended audience; use minimal factual summaries and restricted source references where needed. Never attach credentials or private raw logs to make the packet self-contained.

## 1. Freeze the reviewable question

Write a one-sentence decision question and the precise scope of each option. Give options stable IDs independent of their display order. Include retaining the current state only if it is genuinely available, rather than adding a straw alternative. Separate settled constraints from claims that reviewers are being asked to evaluate.

Pin the version of every artifact whose contents could change the response. A mutable link without a version or captured snapshot is insufficient when the review depends on exact text. Keep accessible source locators and relevant sections; do not broaden sharing merely because a reviewer cannot open a link. Surface that access gap or prepare an authorized audience-safe summary.

State the decisive tradeoffs and unresolved facts with their evidence. Distinguish the author's proposal from an already accepted decision. Do not invent a cost, deadline, commitment or rationale on another person's behalf. Keep the packet short enough to act on; link background rather than copying entire discussions.

## 2. Author the response contract and blank packet

Use the existing team's response semantics. If none exist, label the proposed response vocabulary for owner review instead of treating it as adopted governance. Keep meaningful states separate: support, support subject to a named condition, objection, abstention, needs clarification and no response. A question is not necessarily an objection; an abstention is not a vote for the default.

A compact reusable packet should contain:

```text
Decision ID / packet revision:
Question and affected scope:
Decision owner and source of authority:
Options, with stable IDs and exact versions:
Constraints, decisive evidence and unresolved facts:
Required / advisory reviewers:
Response deadline and time zone:
Response meanings and existing closure rule:
Where authorized responses will be collected:

Response:
- Decision ID and packet revision reviewed
- Reviewer identity or approved reviewer key
- Position / selected option ID, as applicable
- Specific condition, objection or question, if any
- Evidence or affected requirement, if useful
```

Adapt this to the actual task. Do not require a justification for an ordinary abstention, private absence reason or irrelevant personal information. Keep an optional evidence field optional. A required response must allow an honest unknown or request for clarification when that is valid under the process.

Make the deadline an exact instant when reviewers are in different zones. A local display should include its date, zone and offset where ambiguity matters. Do not imply that expiry automatically approves the proposal. If the existing process permits closure with missing responses, state that rule while still labeling those people as nonresponders rather than supporters.

For draft-only work, retain a blank response register. Do not populate it with invented reviewers' positions or count a fictional walkthrough as actual feedback.

## 3. Reconcile actual responses only when supplied or authorized

For each in-scope response, record a source ID/link, evidenced reviewer identity, timestamp, decision ID, reviewed revision, response meaning and any open condition. Preserve original wording separately from the coordinator's short interpretation. A message author, document owner and person quoted in the message may be different identities.

Use stable response IDs to deduplicate repeated exports. Do not merge similar opinions as if they were one response, count quoted support twice, or infer an identity from writing style. An anonymous response may inform the discussion but cannot satisfy a named approval requirement without appropriate evidence.

Determine which response is current from explicit supersession or the team's established rule. A newer comment that adds a question does not necessarily revoke an earlier position. Preserve conflicting or ambiguous responses for clarification; do not select whichever yields closure. Keep withdrawn, superseded and out-of-scope responses visible without counting them as current eligible responses. Classify late responses under the supplied late-response rule; mark their eligibility unresolved if that rule is missing.

Responses bind to the reviewed revision and scope. When options, consequential facts, requirements or commitments change, identify affected responses as requiring reconfirmation unless an existing rule expressly allows them to carry forward. Do not transfer approval to a materially different proposal or count one person's approval twice because they hold two roles. A harmless typo correction can preserve a response when the applicable process permits it; record what changed.

For conditional support, state the condition and evidence needed to resolve it. Evidence that a condition was met does not always convert it to approval: apply the actual rule, which may require the reviewer to confirm. Link objections to their disposition: open, answered awaiting reviewer, withdrawn, or overruled by the authorized owner with evidence. Do not hide unresolved objections inside a positive summary.

## 4. Separate response completeness from a decision

Evaluate only the supplied rule. Show the eligible population, current valid responses, abstentions, nonresponses and unresolved identities/versions. If a quorum or threshold is used, preserve its denominator and treatment of abstention, delegation and late responses. Unknown eligibility prevents a definitive count for that portion; do not quietly shrink the denominator.

Report two independent states:

- **Review state:** complete, missing required responses, awaiting clarification, or otherwise defined by the process
- **Decision state:** proposed, decision pending, explicitly decided with evidence, or the team's corresponding state

Complete review does not itself establish approval. A recorded owner decision can coexist with advisory dissent. Preserve the actual authority, scope, chosen option/revision, decision time and unresolved conditions. A status label in the register is not the decision evidence.

If closure evidence is absent, deliver a ready-to-decide packet showing the exact remaining issue. Do not send a chase, announce a decision, create an implementation task or change an accepted record merely to finish the register. If those actions were separately requested, follow their own authorized recipient, content and verification boundaries.

## Deliverable, acceptance and recovery

Return the actual editable packet and response register, or the updated existing artifact when requested. Include a short change history when revisions exist. A compact register can use these fields:

```text
reviewer_key; required_or_advisory; source_id; reviewed_revision
current_response; condition_or_question; disposition; decision_counting_state
```

Read back the saved result and verify:

1. Every option, source and response refers to the intended decision scope and version
2. Required reviewers and eligibility come from the supplied process, with unknowns visible
3. Current, duplicate, withdrawn, late and superseded records reconcile to the source set
4. No silence, reaction, quoted opinion or conditional statement has become an unsupported approval
5. A claimed decision has actual authority and decision evidence, independently of response completeness
6. The intended audience can use the packet without receiving unrelated private material or invented access permissions

Walk a relevant fictional path only as a design check: a reviewer abstains, supports conditionally or responds to an old revision. Check the resulting register state against the declared rules. Label such walkthroughs unexecuted unless actually performed; they are not evidence of live collection or approval.

If evidence is inaccessible, preserve its locator and the unresolved response rather than fabricating a quotation. If the packet changes concurrently, reconcile against the newest version before editing. If a save or authorized delivery is uncertain, inspect its destination and existing item identity before retrying. Stop at the requested artifact or evidenced update, with decision and delivery gaps explicit.

## Illustration: fictional and unexecuted

Assume packet D-17 revision 2 asks whether to replace a weekly report with a dashboard. The supplied process names A as decision owner and B and C as required consultees; consultation is required, agreement is not. B supports revision 2 if an export remains available. C asks whether historical reports will be retained. Neither response is an owner decision.

The register records B's condition and C's question separately. If revision 3 removes the export, B's earlier support cannot be carried forward as approval. If A later decides after the required consultation under the supplied rule, the record can show an explicit decision with unresolved advisory disagreement; it must not claim unanimous support.

This is a fictional paper scenario. No packet was distributed, person contacted, response collected or decision made by this illustration.
