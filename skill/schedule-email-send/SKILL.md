---
name: schedule-email-send
description: "Schedule, reschedule or cancel a specific email using the mailbox's native send-later feature, checking the exact message, effective time and queued state. Use for one-time delayed dispatch, not message drafting alone, recurring campaigns, conditional follow-ups or recalling delivered mail."
---

# Schedule an email without losing control of its queued state

Deliver the requested one-time send schedule, change or cancellation, with evidence of the actual saved state. The useful result is an identified message queued for the intended time, or a verified cancellation that preserves the requested content. A draft, scheduled item, submitted message and delivered message are different outcomes.

Use [professional-message drafting](../draft-professional-message/SKILL.md) for wording and recipient-context decisions, [private follow-up reminders](../awaiting-reply-user-followup/SKILL.md) for a nudge to the user, and [email-delivery tracing](../trace-email-delivery/SKILL.md) once dispatch or receipt is uncertain. This workflow does not create an autoresponder, a recurring send rule, a campaign, or a promise to recall mail after submission.

## Establish the message and the intended dispatch

Resolve from the request and authorized context:

- The sending mailbox, From identity and actual provider/client edition
- The exact draft or queued item, or the approved new message and attachment versions
- To, Cc and any authorized Bcc recipients; the source thread for a reply
- The requested action: prepare only, schedule, change a specified schedule, or cancel it
- Full send date, local clock time and timezone, plus any explicitly stated condition or expiry

Ask only for a missing detail that changes the action. Do not make the user repeat an already clear instruction to send a particular message later. However, “draft this for tomorrow” is not necessarily permission to queue an automatic send. Scheduling commits to a future external communication; the authorization must cover the recipients, purpose, allowed content and timing, with any additional approval required for consequential content.

Treat “send at 09:00” differently from “send at 09:00 if they have not replied” or “send only after approval.” A native time-based queue does not establish those conditions. Do not substitute an unconditional send. Explain the unsupported condition and keep the message unqueued unless an authorized mechanism can actually enforce it.

Before creating a new item, inspect the relevant existing draft/schedule so a repeated request cannot queue a second copy. Match the mailbox and supported item ID, not just the subject. When IDs are unavailable, compare recipients, content, attachments and the intended occurrence; unresolved lookalikes need clarification. Keep this inspection scoped to the relevant message.

## Choose the actual native mechanism

Prefer a connected tool when it supports scheduling and reading back the scheduled state. A tool that can create drafts or send immediately does not necessarily support delayed sending. Otherwise use the authorized client interface. Do not invent a scheduling API field, install an add-in, add persistent credentials or create a custom background service merely to approximate a missing feature.

Consult the current official guidance for the exact client and account type. These examples describe different queue semantics, not interchangeable button sequences:

- [Gmail on a computer](https://support.google.com/mail/answer/9214606?co=GENIE.Platform%3DDesktop&hl=en) exposes Schedule send beside Send and keeps queued items in Scheduled. Cancel send returns an item to a draft; editing the draft does not requeue it. Gmail states that sending uses the scheduling timezone and may occur a few minutes after the chosen time.
- [New Outlook and Outlook on the web](https://support.microsoft.com/en-us/outlook/mail/delay-or-schedule-sending-email-messages-in-outlook) use Schedule send and retain the scheduled message in Drafts. The same guidance says new Outlook's feature is unavailable for IMAP/POP accounts. A Drafts folder entry is therefore insufficient to distinguish an ordinary draft from scheduled mail.
- The [classic Outlook instructions](https://support.microsoft.com/en-us/outlook/mail/delay-or-schedule-sending-email-messages-in-outlook) instead use Do not deliver before, followed by Send, and hold the message in Outbox. Microsoft states that Outlook must be online and connected. Do not describe that as an unattended server-held schedule or alter power/network settings to keep it running without authority.
- [Outlook for Mac](https://support.microsoft.com/en-us/outlook/use-schedule-send-in-outlook-for-mac) documents an eligible-account Schedule Send route that retains the item in Drafts and can dispatch with Outlook closed. Verify the account/version requirements; the guide excludes IMAP/POP accounts.
- [Apple Mail on Mac](https://support.apple.com/guide/mail/mlhlp1098/mac) uses the Send Later mailbox, supports editing the scheduled time there, and documents deleting that selected item to prevent sending. Cancellation therefore does not universally mean “return to Drafts.” Check content-preservation and deletion effects before choosing the route.

Establish any client-running, connectivity or account prerequisites that matter to the requested time. A feature's name or a successful save is not proof that it works while a device is shut down. If the chosen mechanism cannot satisfy the request, preserve the prepared message and explain the specific limit. Propose another authorized account/interface only when it preserves the requested sender and effects; do not silently switch identities.

## Map the intended time into the scheduling control

Resolve relative wording such as “tomorrow morning” to an actual date and time in the user's intended zone. Use the recipient's zone only when that is what the user requested; an email address or language is not timezone evidence. Retain a named regional zone where appropriate, and use that date's offset rather than today's.

Identify which zone the scheduling control actually uses: an explicit picker, account setting, client/device zone or another documented source. Do not assume the assistant's computer matches the user's. Compare the intended instant with the control's displayed date and time, including any day change. A repeated or nonexistent daylight-saving hour needs a supported unambiguous choice or clarification.

Check the final time immediately before queuing. If preparation has passed it, do not convert the instruction into an immediate send or roll it to the next day. Use any already-authorized late-send rule; otherwise ask for the new time while leaving the message unqueued. Do not change a global timezone setting to make one picker look right.

Expose material timing limits before committing. Native scheduling is not a guarantee of exact recipient arrival. If the user requires “never after the deadline,” verify a real expiry mechanism; a scheduled time alone does not establish a cutoff. A separate reminder to cancel later cannot be represented as an enforced expiry.

## Queue the reviewed message once and read it back

Check the actual composed item before the scheduling action: sender, full recipient fields, reply audience, subject, body, signature, attachments and important links. Preserve the approved content. A reply-all audience, an automatically appended phone number or a cloud-attachment permission prompt can change the disclosure. Resolve that change instead of accepting it as a harmless scheduling step.

Ensure attachments have finished uploading and identify whether each is a captured file or a link to mutable content. A scheduled email does not freeze the later contents or access rights of a linked document. Do not replace an attachment with a shared link or widen document permissions to make scheduling succeed without the needed authority.

Select the supported send-later route, enter the checked date/time and perform its final queue action. Do not use ordinary Send to test whether a delay is present. In a client whose documented delayed route itself ends with Send, first verify the delay control on that exact item.

After the action, reopen the same account's scheduled-item view through the supported inspection route. Confirm:

1. The exact item is pending with the intended full date, time and effective zone
2. Sender, recipients, content and attachment selections still match the reviewed message
3. No extra pending copy of this requested send was created
4. Any relevant dispatch prerequisites remain explicit

Retain a supported item reference or a private description sufficient to find and cancel it. A toast alone is weaker than the queued-item readback. If inspection itself opens an edit or removes a queued state, account for that transition before claiming the message remains scheduled.

Do not send a test message, move the real schedule to an earlier time, or enable a global delay rule to manufacture evidence. The immediate acceptance check is the saved queue state, not an observed future send.

## Change or cancel the existing item, not a lookalike copy

Freshly read the current item and schedule before changing them. Reconcile intervening user edits rather than overwriting the message from an old snapshot. A request to change the time does not authorize rewriting the body or adding recipients.

Use a supported in-place time edit when available. If the product requires cancellation and requeuing, cancel the old schedule first and verify the resulting unqueued state before queuing the replacement. Recheck the retained content and attachments, then apply the new time and repeat the queue readback. Do not create the replacement first while the old send is still active.

If cancellation succeeds but requeuing fails, report the actual state: the old schedule was canceled and the message is now unscheduled, if that is what readback establishes. Do not silently restore the old time after the user replaced it, and do not claim that a saved draft will still send.

For cancellation-only requests, stop after verifying the requested item no longer has an active schedule and identifying where its content remains. Preserve a draft when supported and desired. When the native cancellation route deletes the item, resolve any material conflict with the user's retention instruction before that action; do not empty Trash or remove other queued messages.

Close to the send time, state can change during the operation. Reinspect the same item and available sent/submission evidence if it leaves the queue. Its disappearance alone does not prove cancellation. If it was already submitted, do not claim it was stopped or attempt recall, a corrective email or a second send under the original cancellation instruction.

## Handle uncertain results and finish at the evidenced boundary

After an ambiguous queue, cancellation or time-edit result, inspect the actual item, relevant pending state and available submission evidence before retrying. A remaining draft or an empty search result alone cannot establish that nothing was queued or submitted. Retry only when the operation is known not to have taken effect or a supported duplicate-safe mechanism applies. Otherwise preserve the uncertainty and the exact next evidence needed.

Report the action, message reference or safe identifying summary, account, intended local time/zone, actual pending/canceled/unscheduled state, and the supported way to change or stop it. Include a specific client dependency or verification gap when relevant, without copying private message content unnecessarily.

“Scheduled and read back” is a complete result for a setup-only request; it is not “sent” or “delivered.” If the user also requested verification after the scheduled time, use the established account and exact item identity to check the resulting submission, pending or failure state. Do not infer recipient receipt or reading from a sent record, and do not resend overdue mail merely because the queue has not cleared.

## Fictional, unexecuted illustration

A fictional user has approved a workshop email and one PDF attachment for two named recipients. They ask to move its existing Gmail schedule from October 22 at 09:00 UTC to October 23 at 14:00 UTC, without changing its content.

The planned operation finds the exact scheduled item, cancels its old schedule, checks the resulting draft and requeues that draft for the new instant. If the new scheduling action has an uncertain result, the next step is to inspect that item's current state, not create a second message. If readback instead establishes that cancellation succeeded and requeuing failed, the truthful outcome is “old schedule canceled; draft retained; new schedule not saved.”

All details are invented. No mailbox, draft, queue, attachment, send or cancellation was exercised for this illustration. Provider documentation supports the described controls, not an end-to-end execution or effectiveness claim.
