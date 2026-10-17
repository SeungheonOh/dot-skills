---
name: route-document-approval
description: "Prepare, send when authorized, and reconcile a native content-approval request for an existing document, keeping reviewer rules, request rounds and approved versions distinct. Use for ordinary document review routing, not signing, making the approval decision, publishing content or building an approval automation."
---

# Route a document approval to the right version

Deliver the requested native approval setup or verified request, with a compact record that identifies what content is being reviewed, whose responses count and what remains pending. When asked to follow it through, reconcile the actual provider history through the agreed stopping condition. A file's green status does not by itself establish approval of its current contents.

Use [prepare-async-decision-packet](../prepare-async-decision-packet/SKILL.md) when the decision question, options or response process need authoring. Use [document-revision-reconciliation](../document-revision-reconciliation/SKILL.md) for combining accepted edits and [prepare-document-signing-packet](../prepare-document-signing-packet/SKILL.md) for signature preparation. This workflow coordinates an established ordinary content-review process. It never casts an Approve or Reject response on another person's behalf, accepts an agreement, releases funds or publishes the reviewed material.

## Establish the request, content and authority

Resolve the following from the user's request and existing process before asking for missing choices:

- Exact service/account, file ID and revision or identifiable content snapshot; existing approval request ID when continuing one
- The review purpose, bounded content and any attachments or linked material that are actually part of approval
- Verified approvers, their roles, required versus advisory participation, and the established completion rule
- Parallel versus sequential review, any explicit delegation rule, and the intended treatment of rejection or requested changes
- Deadline as the provider represents it, including timezone or date-only meaning, and any separately authorized reminder behavior
- Whether the task is preparation, submission, a status snapshot, a specified request change, or follow-through to a stated outcome
- Permitted file sharing, upload, lock/unlock and notification effects, plus the private destination for the handoff record

Do not invent approvers, infer authority from seniority, or substitute a majority rule for an all-reviewers requirement. A file owner is not necessarily an approver. If the desired rule is unknown, prepare the content and recipient mapping while holding submission. Ordinary cosmetic choices need not block preparation.

A specific request to ask named reviewers to approve identified ordinary content can authorize that communication. A request to prepare a packet does not authorize sending it. Check sensitive disclosures and consequential commitments separately: naming a file does not make every embedded private appendix appropriate for every reviewer. Keep legal acceptance, employment decisions, financial authorization and similar consequential workflows outside this ordinary content-routing guide.

Inspect available capabilities and actual account eligibility. A tool that edits a file may not read approval history or create native requests. Use an existing supported route, or return the exact unsent specification and missing operation. Do not enable a tenant-wide feature, install an approval app, create credentials, upgrade a plan or build an automation to bypass a missing capability.

## Bind one approval round to reviewable content

Read the selected document and enough native history to establish the review boundary. Record the stable file identity, selected revision, existing approval round, present content state and relevant lock state. Keep the current file, a request's attachment and an earlier approved version distinct even when their titles match.

Establish what the provider actually binds: an immutable attachment, a native file version, or a mutable file whose edits affect the request. Retain a provider revision/version locator when available. For ordinary downloaded files, a digest can identify captured bytes; it cannot establish which native version a reviewer saw. Do not label an exported copy as the approval subject unless the request really uses that copy.

Preserve the source's content, comments, suggestions, history and existing approvals. Do not tidy a filename, accept tracked changes, refresh linked data or edit a metadata field during review without inspecting its effect. Such a change can invalidate an active request even if the visible prose stays the same. If the file changed since preparation, resolve the new revision before submitting rather than sending a stale description of it.

Check whether an active or completed request already covers this exact purpose and content. Inspect the stable request identity and history, not just a same-named card. Continue an existing round when that is the user's intent; do not create a duplicate because one reviewer is still pending. Separate a resubmitted round from the earlier rejected, cancelled or superseded round so prior responses are not counted twice.

For a document set, establish whether the provider supports one request covering the full set or separate requests. Do not treat approval of a cover note as approval of unseen attachments. Do not combine or split the set merely to fit a tool if doing so changes the review unit.

## Match the provider's completion and edit rules

Inspect current official guidance and the actual request controls. Record the few settings that determine the outcome: who must respond, order, rejection behavior, edit/reset behavior, lock state, and any built-in notices or downstream actions. A copied template's defaults are not the user's instructions.

For example, [Microsoft's modern approvals guidance](https://support.microsoft.com/en-us/sharepoint/data-and-lists/approvals-in-lists-document-libraries) describes a default in which one approver can grant a request unless all responses are required. It also describes cancellation of in-progress file approvals after saved edits, and status reset after metadata changes. Check the actual request configuration before sending; a list of several names alone does not establish an all-person requirement. Modern approvals is distinct from SharePoint content approval and request sign-off, so do not transfer behavior between those mechanisms.

For [Google Drive approvals](https://support.google.com/drive/answer/9387535?hl=en), whether edits reset responses depends on the same-content setting. Locking also prevents comments and suggestions. During an active review, unlocking can reset approvals under the reset-on-edit mode; after completion, the final approvals can remain while the file is unlocked and changed. Consequently, retain the approved version separately from the file's current version. Check actual account support and settings rather than assuming every Drive file supports the same workflow.

Choose only the established review rule. If the requested semantics cannot be represented, expose the mismatch and hold submission rather than silently weakening the requirement. A sequential process must not become parallel merely because that is easier; advisory readers must not become required decision makers to obtain access.

Locking, changing the same-content rule and changing approvers can disrupt existing work or invalidate responses. Apply those changes only within the user's authorized request. Do not unlock a document just to inspect it, or turn off response resets to keep a desired green status. Where the process permits changing content during review, record how the resulting responses bind to versions rather than claiming everyone reviewed identical text.

Keep request creation separate from downstream effects. Inspect relevant existing automation or template behavior when available; approval status may feed other workflows. Do not enable publishing, purchasing, record updates or automatic reminders as incidental setup. If an unavoidable consequence exceeds the approved scope, identify it before submission.

## Verify the reviewer and information boundaries

Resolve each recipient to the intended account using authorized context. A display name, distribution address or inherited template entry may not identify the right reviewer. Do not expand an unknown group, add substitutes or forward a request to obtain faster completion. Reassignment needs its own permitted target and role.

Check file access and request visibility independently. A person listed as an approver may lack file access; a person who can view the file may not be entitled to see the full request history or other reviewers' comments. Use [shared-link-access-verification](../shared-link-access-verification/SKILL.md) for a detailed access question. Grant only specifically authorized file access, never parent-folder or organization-wide access as a shortcut.

Inspect where the request appears: an individual approval hub, a chat/channel, a shared list or another shared surface. Request titles, messages, previews, attachments and reviewer comments can disclose information beyond the document itself. Preserve the intended audience; a private file link in a public request is not a complete privacy boundary. Do not reproduce a private rationale or internal reviewer disagreement in a broadly visible status note.

Use minimal sufficient content in the request: what is being reviewed, exact file/version or native reference, the decision requested, relevant deadline and the established route for changes. Do not insert approval wording as if the recipient already agreed. Keep a missing-access issue visible rather than asking the provider to send an automatic access request or creating a public copy.

## Submit only the prepared request, then read it back

For preparation-only work, save a private request specification containing the exact content reference, recipients, rule, order, message, deadline and blocked settings. Do not click a final action to discover whether it sends. If the provider does not support an unsent draft, deliver the specification rather than creating a real request as a substitute.

For an authorized submission:

1. Refresh the file identity/revision and existing request state immediately before sending. Reconcile intervening changes or a newly created request
2. Inspect the actual recipients, attachments, rule, order, notices and sharing prompts. Keep unrelated defaults unchanged and hold any newly discovered effect outside scope
3. Submit once through the supported interface and capture the returned request identity, file association and observed time
4. Reopen the request from its native saved location, independently of the preparation form. Check its recorded recipients, settings, subject/content binding, deadline and initial state
5. Read back any specifically authorized file-permission or lock changes separately, and preserve their prior state for a possible scoped recovery

[Microsoft's Teams request workflow](https://support.microsoft.com/en-au/teams/shifts/create-an-approval) explicitly ends with Send and provides a Sent view for subsequent inspection. Treat that as a communication boundary, not a harmless draft-save action. A success notification establishes neither that every reviewer can open the file nor that they read the request.

Verify without producing dummy responses, changing the file to provoke a reset, or signing in as another reviewer. Configuration readback, delivery evidence, reviewer access and actual approval are separate claims. Mark unavailable checks precisely.

## Reconcile status without manufacturing agreement

For a snapshot request, read the current round and return the result at its observation time. For requested follow-through, continue supported checks until the agreed outcome, cancellation, or a blocker requiring a decision. Do not call submission complete fulfillment of a request to obtain all required responses. Use only authorized follow-up messages and reminder settings; read-only tracking does not authorize chasing reviewers.

Maintain a compact record, proportional to the request:

```text
file ID / selected revision / current revision
request ID / round / previous round if any
completion rule / reviewer order / edit-reset and lock behavior
reviewer account / current response / response time / reviewed version evidence
provider state / content-validity state / unresolved access or decision
observation time / source link / next permitted action
```

Use provider history to distinguish pending, approved, rejected, cancelled, reassigned and superseded responses. Preserve comments that qualify an apparent approval; do not decide that a condition is met without the required evidence or convert a request for changes into consent. A chat reaction, silence or resolved document comment is not a native approval unless the established process explicitly makes it one.

Compare the actual responses with the configured rule, not with the result you hoped for. Report the provider's status separately from whether the requested content/version and reviewer requirements are satisfied. If any-one approval completed a request that was supposed to require everyone, report the misconfiguration; do not rewrite its history or claim unanimity.

When a file changes, inspect the active round and version history before attributing a cancellation or reset to a person. Microsoft documents that automatic cancellation can be recorded under the request creator's identity. Preserve the observed event and its supported cause rather than asserting that this person intentionally withdrew the request. The same guidance says visible SharePoint approval columns reflect the latest activity; use available detailed history for earlier rounds.

For completed approval, identify the approved content and compare it with the current file. If the current content differs or version correspondence is unavailable, report the older approval and the present gap. Do not imply publication readiness, legal acceptance, signature completion or substantive correctness from a content-approval status.

## Acceptance, partial completion and recovery

Deliver the exact prepared specification or verified request link, its content binding, current rule and state, required outstanding responses, and material access/version gaps. Include the compact record when it helps the user resume; a simple request need not acquire a large audit workbook.

Acceptance follows the user's endpoint:

- **Prepared:** complete unsent settings and content references, with missing decisions isolated
- **Submitted:** the intended native request is saved and read back with the authorized recipients, content and rule
- **Status checked:** the named round and relevant history are reconciled at a stated observation time
- **Follow-through:** the requested stopping condition is evidenced for the correct version. A missing decision or access requirement is a pending/held outcome, not completion; identify it and retain the unresolved request

After a timeout, inspect the existing request by returned ID or supported file/request history before retrying. If creation remains uncertain, stop duplicate submission and report uncertainty. A matching title alone is insufficient. For partial updates, reconcile each requested setting as saved, unchanged, blocked or unknown; continue only the still-needed authorized changes using current preconditions.

If the wrong recipients, content or rule were submitted, stop further disclosure and report the exact request and observed effects promptly. Cancellation, replacement requests, access removal, correction messages and file restoration each need their applicable authority. Do not assume cancelling retracts email previews or downloaded copies. Do not restore an old document over concurrent work to regain a previous approval status.

If a request was cancelled by an edit, preserve its history and identify the new content requiring review. Resubmit only under authority covering the new round and content. Do not disable the approval feature as a cancellation shortcut: Microsoft's guidance notes that hiding the feature's columns leaves active requests actionable. Keep useful completed preparation when a live action is blocked; never label an unsent specification as a created request.

## Fictional, unexecuted illustration

A fictional Cedar team asks for a native review of handbook revision 12 by two verified reviewers, with both required to approve. The user authorizes submission of that ordinary content to those accounts and read-only follow-through, but no reminders, document edits or permission changes.

The preparation would select the all-reviewers rule rather than leaving an any-reviewer default. Suppose the first reviewer approves revision 12 and the second remains pending. A later saved edit produces revision 13 and the service cancels the active request. The record must retain the first response with its old round, identify the new revision, and report that the requested two-reviewer outcome remains incomplete. It must not treat the first response as approval of revision 13 or silently send another request.

If a different provider retains completed approvals after subsequent edits, the equivalent check is the approved-version/current-version comparison, not the continued green status. These are authored handling expectations. No document, request, reviewer response, notification, lock, permission or live workflow was created, read or changed for this illustration.
