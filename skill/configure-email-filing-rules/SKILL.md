---
name: configure-email-filing-rules
description: "Design, review or configure scoped automatic email filing rules with exact match conditions, competing-rule analysis, message-level checks and a recovery plan. Use for future label or folder routing, not one-time inbox triage, forwarding, automatic replies, spam-policy changes or account-wide cleanup."
---

# Configure email filing that matches the intended messages

Deliver a usable, provider-specific rule set and an honest account of whether it is only prepared, saved, enabled or observed on incoming mail. The essential work is translating the user's filing intent into precise message predicates and understanding the combined effects of existing rules. A search that finds one newsletter does not prove a safe future rule.

Use [inbox-action-triage](../inbox-action-triage/SKILL.md) for a bounded set of current messages and human commitments, or [automate-repeatable-task](../automate-repeatable-task/SKILL.md) for a broader repeated workflow. This skill handles ordinary same-account labels, categories, folder moves or skip-Inbox behavior. It does not create forwarding, replies, deletion, unsubscribe/block actions, security exceptions or new account access.

## Establish the intent and action boundary

Identify the exact account, provider, client/version, existing rules, desired destination and examples of messages that should and should not match. Reuse known folder/label IDs rather than creating similar names. Distinguish a mailbox folder from a local-only folder and a display name from an actual email address.

Clarify the intended effects separately:

- Add a label/category while retaining Inbox membership
- Move to a named folder or skip Inbox
- Preserve or intentionally change read/unread, star/flag and other labels
- Apply only to newly arriving messages, or also a precisely bounded historical set
- Prepare a proposal versus save/enable the actual rule

A request to configure a specific filing rule can authorize that setting change. A general complaint about clutter or a one-time cleanup does not authorize ongoing rules. Confirm missing action scope before activation; do not create a disabled rule as a supposed read-only fallback because saving it still changes account state.

Persistent routing can hide important incoming mail. Keep exceptions grounded in the user's intent, such as separating an exact weekly digest from direct replies by the same sender. Do not invent a broad "low priority" classifier from a few examples or infer consent to archive all mail from an organization.

Use the connected service's supported rule tools where available; otherwise use its actual authorized settings interface. Do not add OAuth grants, install a browser extension, connect another mail client or change tenant policies to obtain a missing capability. Keep exports and evidence private because rule criteria and folder names can reveal contacts and projects.

## Translate intent into native match conditions

Read the provider's current documented condition and action semantics for the exact client/account. Build a small rule record:

- Stable existing rule ID or proposed name
- Conditions, grouping, exceptions and the header/message property each tests
- Action and exact destination identity
- Position/priority or combined-effect behavior
- Enabled state, execution location and any client-running requirement
- Historical application scope, if any
- Original configuration for the rule being changed

Use exact addresses, list identifiers or stable supplied metadata when they represent the request. A From display name is not an identity, and an apparent sender address match is not sender authentication. Do not turn a filing rule into a phishing or security verdict.

Make AND, OR and NOT grouping explicit. Confirm whether subject criteria mean words, phrase containment, equality or another provider-defined comparison; do not assume regular expressions, wildcards or case behavior. Preserve punctuation meaningful to the matching engine. Avoid predicates that rely on state created only after arrival unless the rule engine supports that lifecycle.

For Gmail, use [documented search operators](https://support.google.com/mail/answer/7190?hl=en) as a starting point, then confirm the actual filter accepts the chosen criteria. A conversation-level search display can include nonmatching messages from a thread. Inspect the individual matching messages and keep them distinct from the returned thread count. [Gmail's filter guidance](https://support.google.com/mail/answer/6579?hl=en) also states that a later reply is filtered only if it satisfies the criteria itself.

For Outlook, inspect the actual conditions, exceptions and rule order in the named version. [Stop processing more rules](https://support.microsoft.com/en-us/outlook/mail/stop-processing-more-rules-in-outlook) changes whether later matching rules run. Do not transplant that ordered/stop-processing behavior onto another provider without evidence.

Keep a precise unsupported state when the requested predicate cannot be represented. A broader approximate rule that silently hides extra mail is not a successful fallback. Offer the exact narrower rule or a proposal for the user's choice, while completing supported rules independently.

## Inspect interactions before activation

Read every existing rule that can overlap the proposed population or destination. Preserve unrelated rules. Work out the combined effects on representative messages, including existing actions that remove Inbox membership, move to another folder or stop processing.

Check at least the meaningful cases present in the source material:

- A clear intended match
- A similar sender/subject that must stay in the Inbox
- A reply in the same conversation that does not independently match
- A message matching two relevant rules
- A required exception and a missing field when those change the result

Use bounded authorized historical messages for a read-only preview. Record actual message IDs, the applicable conditions and predicted effects with minimal content. Do not send fabricated test messages or contact a sender without authority. An offline export supports manual reasoning about supplied samples; it does not prove live rule-engine behavior.

Compare expected positives and negatives against the provider's actual search/preview where available. Investigate every mismatch before enabling a rule that moves mail or skips the Inbox. Sample agreement establishes only the sampled cases, not complete future accuracy. If broad search results exceed the reviewed scope, do not apply the rule to them as a historical cleanup.

For Outlook, distinguish server execution from client-only behavior. Microsoft's [rule troubleshooting reference](https://support.microsoft.com/en-us/outlook/mail/edit-or-fix-a-broken-rule-in-outlook) describes unsupported client-side rules in new/web Outlook. A rule visible after migration may still be unusable in the target client. Do not silently drop a condition to make it save.

If interacting rule semantics are unobservable, document the uncertainty and hold activation of materially conflicting changes. A label-only trial can be a proposed lower-impact option, but is still a changed action requiring the user's agreement when it differs from the request.

## Save only the approved rule changes

Capture the exact current values of edited rules, relevant order, destination and enabled state. An export is useful when supported, but do not reimport an entire rule set to change one entry. Re-read the target immediately before mutation to detect concurrent edits.

Apply the smallest supported change. Reordering or enabling a stop condition may change other rules' behavior; include those effects in the approved scope. Preserve existing settings outside that scope.

Keep historical backfill separate from activation. A checkbox such as "also apply to matching conversations" or a "run now" action can immediately change old mail. Leave it unselected for a future-only request. If historical application was requested, pin the actual message population, inspect thread-wide effects and record original folder/label/read state before applying it. Do not treat a changing search result count as an immutable target list.

After saving, read the rule back by stable ID where supported. Compare conditions, exceptions, order, actions, destination and enabled state with the approved record. Inspect relevant neighboring rules to verify that their settings were preserved. A UI success message establishes less than a configuration readback.

If the provider exposes only creation and no safe disabled state, do not create a live rule merely to test its syntax. Finish the proposal and explain the exact validation or authority gap.

## Verify effects without overclaiming

Report configuration verification separately from delivery observation:

- Prepared: the provider-specific proposal exists, with no account mutation
- Saved inactive: the intended rule is stored but does not run
- Enabled and read back: the actual configuration matches, but no new-message result has been observed
- Observed: a particular authorized incoming message received the expected effects, with its ID/time and the scope of the observation

A historical search is not proof that a new incoming message passed through the filter. If the user requested observation of a future arrival, establish the bounded observation condition and permitted duration; otherwise finish with future execution unobserved rather than silently starting monitoring.

For an authorized historical backfill, re-read every affected message or the exact provider operation scope, preserving unrelated labels and read states. Reconcile matched, changed, excluded, failed and uncertain items. A thread containing an important new reply must not be archived merely because an older digest matched.

Distinguish provider limitations from denied access. Continue with the complete proposal when mutation is unavailable, and identify the precise unsupported operation. Do not claim configuration or recovery was completed from instructions alone.

## Recovery and handoff

On an uncertain save, inspect existing rule IDs and values before retrying; avoid duplicate filters. On a wrong match or unexpected combined effect, stop the affected change and report it. Disable or revert only within existing authority, or ask for the exact correction required.

Undoing a rule does not necessarily undo its prior message changes. Recover historical effects only from the recorded message identities and prior state, with authority for the restoration. Do not move every message in a destination folder back to Inbox: many may have belonged there before the rule, and concurrent edits may be legitimate. Preserve the evidence when a prior state is unknown.

Return the account/client, concise rule description, exact destination, actual saved/enabled state, preview/readback/observation evidence, historical changes if any, and the supported way to edit or disable this specific rule. Include a compact rule map only when multiple rules or conflicts make it useful.

Stop when the requested proposal or configuration and its immediate checks are complete, or a concrete permission/semantic conflict needs a decision. Do not extend filing into forwarding, replies, deletion, spam bypass, subscriptions or unrelated cleanup.

## Fictional example, not executed

A fictional user wants future weekly digests from digest@example.invalid labeled "Reading" while keeping Inbox and unread state. The new rule must leave direct replies alone. An existing rule applies a "Community" label to all messages from that sender and is to remain unchanged.

The proposed rule uses the provider-supported combination of the exact address and the evidenced digest identifier, preserving both labels when a digest matches. The review set includes a digest, a direct reply in the same thread and another sender using the same subject. The plan leaves any historical-application option off and does not treat the whole conversation as a match.

The intended handoff would distinguish a prepared proposal from an enabled, read-back rule, and would leave incoming-message behavior unobserved until there is actual evidence. No mailbox was read, filter created, message moved, test email sent or future arrival observed for this illustration.

