---
name: configure-email-away-reply
description: "Prepare or configure a bounded email away reply with the correct mailbox, audience, message and schedule, preserving existing settings and distinguishing saved configuration from observed replies. Use for native out-of-office setup, not forwarding, mailbox delegation or a custom autoresponder."
---

# Configure an away reply that reaches the intended audience

Deliver the requested native email responder, or a complete provider-specific setup proposal when activation is not authorized or supported. The result must say which mailbox can reply, to whom, with what information, and during which interval. Writing an absence message alone does not establish those effects.

Use [draft-professional-message](../draft-professional-message/SKILL.md) when only wording is requested, [prepare-work-absence-handoff](../prepare-work-absence-handoff/SKILL.md) for coverage instructions, and [configure-email-filing-rules](../configure-email-filing-rules/SKILL.md) for incoming-message routing. This workflow does not implement a reply bot, forward mail, grant delegation, decline meetings or change availability in other systems.

## Establish the bounded reply instruction

Read the user's request and current mailbox settings before asking for missing details. Identify:

- Exact mailbox/account, provider and account type; distinguish a personal mailbox, shared mailbox, alias and delegated mailbox
- Preparation versus saving or enabling the responder, including whether an existing responder is being replaced
- Start and end boundary, intended timezone, and when the user actually becomes available again
- Authorized reply audience: internal organization, selected supported contacts-only audience, all incoming senders, or another representable scope
- Content the responder may disclose, including any approved contact route and its audience
- Existing responder state, message, schedule and relevant linked behavior

Enabling a responder is standing communication. The user's instruction must cover the account, audience and bounded category of information; a request for a draft or a remark about taking time off is insufficient. If the audience is unresolved, ask rather than silently enabling replies to every external sender. Ordinary availability information can be enough; do not demand a personal reason for the absence.

Keep personal travel, health details, home vacancy, private phone numbers and confidential work out of automatic replies unless their disclosure is specifically authorized to an appropriate audience. Verify a substitute contact from supplied context without promising that they accepted new duties. An internal escalation address may be unsuitable for external senders. Do not disclose credentials or access links.

Use an already connected settings tool when it supports the operation; otherwise use the authorized provider interface. Read access to mail does not establish permission or capability to change settings. Do not add new OAuth grants, create credentials, install an add-in or obtain administrator access as an invisible setup step. An unsupported mutation can still produce a usable proposal.

## Translate dates into the provider's actual schedule

Separate the user's availability statement from the sending interval. “Back Monday” does not by itself specify whether the responder ends Sunday night or at Monday's start of work. Resolve that only if it changes the requested behavior. Preserve the intended local timezone; do not interpret an absent timezone as the cloud computer's zone.

Inspect the exact provider's controls and current documentation. Determine whether its boundary is a date, local date/time or explicit timezone-bearing instant, whether the final date is inclusive, and which account/UI timezone applies. Check both ends across daylight-saving changes where relevant. An ambiguous repeated local time needs a supported offset or a clarified boundary; do not silently choose one.

Gmail's [vacation-responder guidance](https://support.google.com/mail/answer/25922?hl=en) describes date-level activation from midnight on the first date through the end of the last date. It also documents contacts-only replies, an appended signature, repeat replies after four days or message edits, and suppressed replies to spam and subscribed mailing lists. Confirm the effective timezone separately because those date labels alone do not establish it. Do not claim exact hour-level coverage from date-only controls.

For an exact-hour request a provider cannot represent, prepare the supported interval and expose the discrepancy. Do not broaden the window or invent a scheduled job without agreement. A manually switched responder is not an automatically expiring one. If no supported end boundary exists, hold unattended activation unless the user explicitly accepts manual shutdown and its owner is clear.

Microsoft's [automatic-reply settings model](https://learn.microsoft.com/en-us/graph/api/resources/automaticrepliessetting?view=graph-rest-1.0) separates disabled, always-enabled and scheduled states, internal/external messages, external audience and timezone-bearing schedule fields. Use the semantics actually exposed by the connected account, rather than copying API field names into an unsupported client.

## Match the audience and content before saving

Map each authorized audience to the native option and its actual definition. “Contacts only” means the provider's contact set, not everyone the user remembers emailing. A sender in a thread, directory entry or autocomplete suggestion may not belong to that set. Do not add people to contacts to make them eligible without separate authority. If the requested recipient set cannot be expressed, leave that mismatch visible.

Prepare short internal and external versions when the account supports and the request needs them. State availability and a verified alternative route without adding deadlines, guarantees of a reply, or a claim that the inbox is unmonitored. Keep return dates consistent with the actual schedule, while allowing an approved difference such as a responder remaining on during a catch-up morning.

Inspect the final body, subject, formatting, links and automatic signature. A private number in a preexisting signature can broaden the disclosure even when the new body is harmless. Do not edit the global signature to solve this under an away-reply request; use a supported responder-specific control, obtain the needed scoped approval, or hold activation. Do not insert remote images or tracking content merely for appearance.

Read the existing responder and relevant overlapping settings before replacing anything. Another client or connected product may expose the same underlying setting. Microsoft's [Teams out-of-office guidance](https://support.microsoft.com/en-us/teams/notifications-settings/schedule-an-out-of-office-status-in-microsoft-teams) describes synchronization with Outlook. Identify such linked effects and disclose any material audience or display change not already covered; do not treat every visible copy as an independent responder to enable.

Check for existing native replies or already configured reply rules that could overlap. Read-only inspection is sufficient to flag uncertainty; do not clear unrelated rules. Prefer the account's native server-side responder. [Outlook's setup guidance](https://support.microsoft.com/en-us/outlook/mail/how-to-set-up-out-of-office-automatic-replies-in-outlook) distinguishes supported account types from client-based alternatives. A rule that depends on leaving the desktop client running is a materially different workflow, not a silent substitute.

## Save the narrow change and read it back

Capture the prior responder values and enabled state in a private change record. Retain enough to restore the previous configuration without saving unrelated mailbox contents. Re-read immediately before writing; reconcile a concurrent edit instead of overwriting it with the earlier snapshot.

Set only the approved account, audience, content and schedule. Leave optional calendar blocking, invitation decline/cancellation, forwarding and status-message features unchanged unless separately authorized. Outlook's [signature and automatic-reply reference](https://support.microsoft.com/en-au/outlook/officeweb/create-a-signature-and-automatic-reply) lists calendar actions that can appear alongside the responder controls; an away-reply request does not authorize them.

If saving an in-progress form would activate the responder immediately, finish the content and schedule before that save. Do not enable an empty or broad-audience version merely to test the interface. When the user asked only for preparation, keep the proposal in the assistant's output rather than creating account state.

After saving, reopen the exact mailbox's responder settings. Compare:

1. Account identity and effective enabled/scheduled state
2. Both boundaries and their timezone interpretation
3. Internal/external audience options and final messages
4. Signature or other appended content when observable
5. Relevant neighboring settings and any known linked display effects

Distinguish a saved schedule from a currently active responder. A future schedule can be correct while no reply is currently expected. A success banner without matching readback is weaker evidence; report the missing verification rather than assuming the configuration.

## Check sending behavior without creating surprise mail

Configuration readback is the normal immediate acceptance boundary. Do not email coworkers, message an external test address, or switch the responder on outside its approved window to manufacture evidence.

If the user explicitly requests a delivery test, establish the test sender and recipient accounts, permitted message and timing. Use only that authorized exchange. Check the resulting reply's sender, audience-specific body, signature and source message relationship. A test from an internal account does not establish external behavior, and a contacts-only test does not establish exclusion of other senders.

Native suppression and repeat limits can make a second test produce no reply. Inspect the documented conditions and available message evidence before calling that failure. Do not repeatedly edit, disable/re-enable or replace the responder to defeat suppression; that can change who receives another message. A test proves the observed case, not every future reply or delivery to every provider.

If a shutdown check at the end of the interval is requested, retain the bounded end condition and authorized observation source. Otherwise report the saved expiry and leave future expiry execution unobserved. Do not promise that a future event already occurred.

## Recovery and completion

On an uncertain save, inspect the actual responder before retrying. Preserve differences and the previous state. If the wrong audience, content or interval was saved, stop dependent testing and perform only an already-authorized correction or ask for the specific one needed. Turning off future replies cannot retract copies already delivered.

Restore only the changed fields and only after checking for later user edits. Restoring a formerly active responder can itself resume communication; include that effect in the recovery decision rather than treating rollback as harmless. Do not replace the whole mailbox configuration or turn off unrelated rules.

Return a concise setup record: mailbox, audience, approved message(s), local schedule and timezone, actual saved/active state, readback result, any observed test, unresolved limits, and the supported way to edit or stop this responder. Call the result prepared, saved scheduled, active and read back, observed for a named test, or blocked as supported by evidence. Finish when the requested configuration and checks are complete, or one exact authority/capability gap blocks activation.

## Fictional, unexecuted illustration

A fictional user asks to schedule a work-mailbox reply for November 2 at 09:00 through November 6 at 17:00 in a specified timezone. Internal coworkers may see a team queue address; external contacts may receive only the return date. The account supports separate messages, a contacts-only external audience and exact schedule fields. A calendar-cancellation option is present but outside the request.

The intended setup preserves that option, records the old responder, saves the two messages and time range, then reopens the same mailbox's settings. The completion would say “scheduled and read back; delivery unobserved.” An internal test, if separately authorized, would not clear the external-delivery check.

All details are invented. No mailbox, setting, message, calendar or future schedule was accessed or changed for this illustration.
