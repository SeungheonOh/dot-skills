---
name: recover-mistaken-email-send
description: "Stop a just-triggered email with an available Undo Send control or attempt an authorized native message recall, then establish the exact message's recipient-level outcome. Use after a mistaken send, not for scheduling, deleting a Sent copy, or promising that disclosed information can be erased."
---

# Recover from a mistaken email send

Use the remaining native recovery option for the exact send and report what it actually accomplished. The result may be a canceled submission with a retained draft, a submitted recall with mixed recipient outcomes, or a verified limit requiring the user's next decision. Do not promise universal “unsending.”

For an item still waiting on a future schedule, use [schedule-email-send](../schedule-email-send/SKILL.md). Use [trace-email-delivery](../trace-email-delivery/SKILL.md) when submission itself is unclear, and [draft-professional-message](../draft-professional-message/SKILL.md) for a separately requested correction. A recall request does not authorize sending a replacement, contacting recipients, changing document access, or changing future mail settings.

## Use a live Undo window before investigating a delivered-message recall

When the user clearly asks to stop the exact send, and its still-visible Undo Send control is identifiable in an already authorized interface, use that control promptly. Do not consume the short window searching unrelated mail, changing delay settings, or composing a correction. Do not click an unrelated generic Undo control or guess which of several recent sends it targets.

The sending application matters. [Gmail's computer instructions](https://support.google.com/mail/answer/2819488?hl=en) describe the immediate Undo prompt and configurable cancellation periods of 5, 10, 20 or 30 seconds. [Mail on Mac](https://support.apple.com/guide/mail/mlhlp1098/mac) documents Undo Send at the bottom of the sidebar within its delay window. Neither instruction establishes a way to retract any older message from a recipient's mailbox. Increasing a delay afterward does not reopen an expired window.

After Undo, inspect the product's result and the identified compose/draft state. Confirm that the canceled operation belongs to the requested sender, recipients and message, and retain its content without resending. A draft alone is not proof of cancellation: it might be another copy. If the control expired or the outcome was ambiguous, preserve that uncertainty and inspect submission evidence before attempting another action.

If immediate Undo is unavailable, continue below. Do not delete the sender's Sent-folder item as a substitute for removing a recipient's copy.

## Identify one send and its available recovery mechanism

Establish from the request and scoped authorized evidence:

- Sending account, From identity, client edition and underlying mail service
- The exact sent item, supported item/message identifiers, send time and actual recipients, including relevant Cc/Bcc
- Whether the user wants recall only, an eligibility explanation, or recall plus a separately approved replacement
- Any prior recall attempt and its report, so a repeated request does not create a duplicate

A thread or subject is not one send. Match the particular occurrence using its item identity and relevant recipient/content/attachment details. Avoid opening or copying the full body when metadata settles the identity. If a forwarded or resent copy is involved, identify which send the user actually controls.

Prefer a connected tool that genuinely exposes the native operation and its result. A send/delete endpoint is not a recall endpoint. Otherwise use the authorized application interface and its current official instructions. Do not install a recall add-in, obtain new administrative access, alter tenant policy, or use a recipient's mailbox without separate authority.

For Outlook, distinguish personal accounts, legacy Exchange behavior and Exchange Online cloud recall. [Microsoft's client instructions](https://support.microsoft.com/en-us/outlook/mail/how-to-recall-an-email-in-outlook-requirements-limitations-steps) provide the version-specific Sent Items → open message → Recall route and report access. Personal Outlook.com mail has a send-delay Undo mechanism, not post-delivery recall.

Consult the [cloud-recall service guidance](https://learn.microsoft.com/en-us/exchange/mail-flow-best-practices/work-with-cloud-based-message-recall) rather than applying a blanket “unread only” rule: read-message eligibility, age limits and recipient alerts are configurable. Cross-tenant recall requires the receiving Exchange Online tenant to allow the sender's tenant; it is not general internet recall. A matching email domain or an Outlook-branded client does not establish eligibility.

Use only existing accessible evidence for these checks. If settings are unknown, say so. Do not promise success before the actual report, or change policy to make this message eligible.

## Confirm the real deletion scope before initiating recall

Recall is not merely a read-only request for information. Microsoft's cloud mechanism attempts to hard-delete recipient copies. Before that action, obtain action-time confirmation for the identified message and affected recipients, disclosing that deletion may be permanent and recall may notify them. An initial “unsend it” instruction does not replace this confirmation. Also resolve any actual client warning before accepting it.

Check the action's recipient scope. If the user asks to recall from one person but the native operation acts on all recipients, do not silently broaden it. Explain the available scope and obtain the needed decision. Do not “edit” the recipients of the old Sent copy to simulate a selective recall.

Keep recall-only separate from recall-and-replace. Choose the non-replacement route when that is the authorized task. If a replacement is requested, verify the new recipients, content and attachments under its own sending authority; the old message's recipients or content need not be correct. Do not assume a replacement is conditional on every recall succeeding. If the user requires that condition, establish the recall outcomes before sending rather than using a bundled route that cannot enforce it.

After the required confirmation, invoke the supported action once for the selected item. Retain the attempt/report reference and time. Do not send a test, create a second recall because the first is slow, or remove the original Sent item to make the interface appear clean.

## Read the report, not just the submission acknowledgment

Use the provider's report for that exact attempt. Verify the report's message identity, account and recipient coverage; a similarly titled report from a previous attempt is not the result. Open only a verified provider destination, with supported authentication if needed. Do not trust a sender display name or paste credentials into an arbitrary report link.

Preserve each recipient's actual status and observation time:

- Recall succeeded for that recipient, according to the provider
- Recall pending
- Recall failed or unsupported, with the provided reason
- Outcome unavailable, such as an inaccessible report or omitted recipient

A request acknowledgment means recall was requested, not completed. Mixed outcomes must remain mixed. Do not conceal an external or Bcc recipient whose status differs, and do not expose Bcc identities in any report shared beyond the user.

Microsoft's service can retry for up to 24 hours. If authorized trace evidence is needed, its top-level `Failed` status alone is not a recall verdict: the recall message can be dropped after either outcome. Inspect the recipient-correlated Drop-event result as documented in the [service guidance](https://learn.microsoft.com/en-us/exchange/mail-flow-best-practices/work-with-cloud-based-message-recall#use-message-trace-to-verify-recall).

Use trace only through access already available. A shared/delegated mailbox's report may be inaccessible even when recall was attempted. Do not create credentials or sign in as a shared mailbox to force access; report the precise verification gap.

If an action returned an uncertain result, inspect the existing attempt/report before retrying. Retry only when non-execution is established or the provider explicitly supports a duplicate-safe retry. A missing report, persistent Sent copy or stale search result does not establish non-execution.

## Explain what is still exposed and finish at the requested boundary

A successful provider recall does not establish that nobody saw, downloaded, copied or acted on the content. It also does not undo an earlier disclosure, commitment or decision. Manually forwarded copies are outside Microsoft's cloud recall; do not represent one successful recipient row as recovery of all downstream copies.

Identify any remaining action without performing it under recall-only authority. Examples include a correction to the right audience, a request to disregard an attachment, or removal of a specific shared-link permission. Those actions have their own destinations and consequences. Do not change broad sharing, contact an administrator or recipient, or assert a confidentiality incident is resolved merely because recall finished.

Lead the result with:

1. The exact send, identified without unnecessarily reproducing its private content
2. What was canceled or requested, and what the evidence actually confirms
3. Mixed, pending or unverifiable recipient outcomes
4. The remaining decision or verification boundary

For a request to attempt recall only, the verified submission and current report can be the handoff, clearly labeled if still pending. For a request to complete or track the recovery, keep following the same accessible report until terminal results or a specific access blocker, respecting the service's processing window. Do not silently stop on “pending,” and do not promise monitoring if the source cannot be accessed.

## Fictional, unexecuted illustration

A user identifies one mistaken workshop email and asks for recall only. Its native action covers two recipients. After the required deletion confirmation, suppose the report marks recipient A successful and recipient B pending. The appropriate interim result is “Recall succeeded for A according to the provider; B is still pending,” not “The email is unsent.” No correction or replacement is sent.

If B later fails, that failure remains in the final result even though A succeeded. If the report instead becomes inaccessible, the last observed pending status and the access gap remain visible. These are hypothetical branches, not observed outcomes. No mailbox, Undo control, recall, report, trace or recipient was exercised for this illustration.
