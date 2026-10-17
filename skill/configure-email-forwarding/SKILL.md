---
name: configure-email-forwarding
description: "Prepare or configure native forwarding of a defined incoming-mail population to a named destination, preserving source-copy policy and separating destination verification, saved routing and observed delivery. Use for an ongoing one-way mail route, not mailbox delegation, one-message forwarding, account migration or organization-wide mail-flow changes."
---

# Set up an email route with an explicit disclosure boundary

Deliver a usable native forwarding configuration, or an exact proposal when authority, recipient verification or provider policy prevents activation. The result must identify what can leave which mailbox, where it goes, what remains at the source and how the route can be stopped. A verified destination, enabled rule and received message establish different things.

Use [email filing rules](../configure-email-filing-rules/SKILL.md) for same-account organization, [mailbox delegation](../configure-mailbox-delegation/SKILL.md) for another person's access to the original mailbox, and [delivery tracing](../trace-email-delivery/SKILL.md) when the task is diagnosing a selected message. This workflow establishes a one-way native route. It does not create a shared inbox, synchronize read/deleted state, backfill history, send replies under another identity or bypass an organization's forwarding controls.

## Establish the route and information being shared

Recover the necessary inputs from the request and authorized settings:

- Exact source mailbox/account, provider, organization, primary address and client/version
- Exact destination address and its actual recipient or service; whether it is an individual mailbox, shared inbox, group, alias or processing address
- Bounded future-message category, inclusion conditions and meaningful exclusions; distinguish an exact sender/list from every message containing a project word
- Information the destination may receive, including bodies, quoted history, attachments and ordinary identifying headers, and the purpose of that disclosure
- Account-wide forwarding versus selected-message forwarding, desired native forward/redirect behavior and source-copy disposition
- Preparation, creation, adjustment or shutdown; existing routes that must remain; any end boundary and requested delivery observation

Resolve the full destination through trusted supplied context or an authorized account/contact record. Autocomplete, a display name or an address embedded in an incoming request is not sufficient authority. For a group or intake service, establish the relevant audience and downstream purpose before treating the address as one private recipient. Do not infer consent to another service's storage, processing or onward distribution from a familiar domain.

Ask only about gaps that change the route or disclosure. A request for easier inbox management does not authorize exporting future mail. A whole-mailbox request must be explicit about that breadth; a narrow category must remain narrow even if a simpler all-mail control is available. If the provider cannot express a material exclusion, deliver a blocked proposal rather than widening the population.

Forwarding is standing data sharing. Before activation, the user must approve the named destination and bounded category of information. Sensitive information needs the specific recipient and purpose; do not infer approval for health, financial-asset, child-related or other sensitive content from a generic request. Native filters do not sanitize quoted conversations or attachments. If the selected population includes information outside the approved disclosure, narrow it through a genuinely supported rule or hold it. Do not automate transmission of passwords, access tokens, payment-card details or other highly sensitive data; use the required user handoff for that transmission.

Keep this disclosure approval separate from action-time confirmation required for an account-security change or new/materially expanded persistent access. Determine what the actual operation changes before saving. A native forwarding action does not authorize new OAuth grants, administrator roles, credentials, authentication changes or app installation. Destination verification proves a technical prerequisite, not the user's consent to disclose mail or the recipient's agreement to do work.

## Inspect the existing routes and choose the mechanism

Use a connected settings tool if it exposes the actual controls; otherwise use the supported provider interface in the authorized environment. Mail-reading capability alone does not establish settings-write capability. Missing access can still yield a complete setup proposal.

Inspect account-level forwarding and relevant forwarding/filter rules separately. Record the source and destination identities, conditions/exceptions, enabled state, source-copy behavior, rule order/stop effects, destination-verification state and execution location. Preserve unrelated filing and reply settings. A route visible in one panel does not prove that no second route exists.

Map only the known hops needed for this request. Check whether the proposed destination returns mail to the source, expands to a group containing it, or already receives the same category through another route. If destination settings are not authorized, use supplied evidence and mark the missing hop unknown; do not enter another person's account. Hold a known loop or unresolved material duplicate route rather than relying on provider loop suppression. Never send repeated test mail to discover a loop by amplification.

Compare the requested behavior with the native mechanism:

- Account-wide forwarding can expose unrelated future mail and may have a separate keep-copy switch
- A selective rule carries exact predicates, exceptions and competing-rule effects; its forwarding action does not inherit the user's informal intent
- Forwarding, redirecting and forwarding as an attached message can change sender presentation, reply destination and recipient usability differently
- A client-only rule requires the relevant client session; a server-side rule and a desktop rule are not interchangeable availability promises

Do not use an address change, alias, POP import, custom relay or third-party automation as an invisible substitute. Preserve the selected account and native route. Organization controls can prevent delivery even when a rule saves. Microsoft's [external-forwarding reference](https://learn.microsoft.com/en-us/defender-office-365/outbound-spam-policies-external-email-forwarding?view=o365-worldwide) describes interactions between outbound policy, remote domains and mail-flow rules; a blocking control can override an allowing one. Record the applicable result rather than assuming a universal default or changing security policy.

For a time-limited request, establish whether the selected control truly supports the requested start/end boundary. A date in a rule name does not expire it. If native expiry is unavailable, obtain agreement to the manual-stop responsibility before unattended activation. Do not silently install a scheduled job or promise future shutdown from a written reminder.

## Translate the scope before enabling it

For a selective route, write a compact contract containing the exact condition fields and AND/OR/NOT relationships, destination, action, exclusions and source-copy effects. Confirm the provider's actual matching semantics. A sender-address condition is not authentication, and a subject fragment is not proof that a message belongs to an approved confidential project.

Use a bounded metadata-first preview of already authorized messages. Include an intended match, a similar nonmatch, a reply that changes the criteria, and any known overlapping rule. Inspect message identity rather than treating every message in a search-result conversation as a match. Record only enough evidence to explain a mismatch; do not export full mail for a settings review.

Read-only sample agreement supports the predicate review, not future delivery. Do not forward historical messages to test it, enable a broad route temporarily, or select a run-now/backfill option for a future-only instruction. If another action in the same rule moves, marks read, deletes or replies, remove it from the proposal unless separately requested; changing an established rule's unrelated action needs its own scope decision.

### Gmail

Google's [forwarding instructions](https://support.google.com/mail/answer/10957?hl=en) use Settings → See all settings → Forwarding/Forwarding and POP/IMAP. Adding an address sends a verification message to it. After the supported verification, the destination can be selected for forwarding; retain the approved source-copy choice and save. Account-wide forwarding concerns new non-spam messages. For selective forwarding, the account-wide route must not remain as an unintended broader route: use the filter's forwarding action to the verified address, resolving any existing broad route before changing it.

Do not enable all-mail forwarding just to make the address available to a filter. Have the intended recipient complete verification when their mailbox is outside authorized access. Use the official matching flow for an authorized destination; never copy verification links or codes into reports, borrow a recipient session or bypass verification with an administrator-only API.

[Gmail's filter documentation](https://support.google.com/mail/answer/6579?hl=en) states that forwarding filters affect new messages; replies must independently meet the criteria. An existing-mail search or historical-application checkbox is not evidence that old messages were forwarded. Reopen both the exact filter and the separate account-wide forwarding setting after saving.

### Outlook

Use the actual account and client. Microsoft's [native forwarding settings](https://support.microsoft.com/en-us/outlook/mail/turn-automatic-forwarding-on-or-off-in-outlook) distinguish the Mail → Forwarding route in new/web Outlook from Outlook.com's Forwarding and IMAP panel. Preserve the requested keep-copy setting; do not let an unchecked default remove the source's expected copy. A renewed sign-in prompt does not authorize changing authentication.

For selected messages, use Mail → Rules in the applicable new/web client, or the matching classic client's rule interface. Microsoft's [forwarding-rule guidance](https://support.microsoft.com/en-us/outlook/mail/use-rules-to-automatically-forward-messages) distinguishes Forward to from Redirect to: ordinary rule forwarding presents the forwarder and directs replies there; redirection preserves the original sender presentation and directs replies to that sender. Select the intended action rather than treating these labels as synonyms. Forward as attachment is a separate representation. Rules retain source copies unless another action changes them; verify combined effects.

Inspect order and [Stop processing more rules](https://support.microsoft.com/en-us/outlook/mail/stop-processing-more-rules-in-outlook) before changing either, because later matching rules can be skipped. Confirm [client/server rule support](https://support.microsoft.com/en-us/outlook/mail/edit-or-fix-a-broken-rule-in-outlook) in the chosen version. Do not remove a required condition, keep a computer running indefinitely or weaken external-forwarding policy to make a rule appear successful.

## Save the smallest authorized change

Capture the prior values of affected settings and stable rule identity where available. Before any operation, resolve its standing-sharing authority, required security/access confirmation and foreseeable verification-email effect. An approved setup may include the provider's necessary verification message when that effect and destination are clear; it does not authorize an additional explanatory email or test exchange.

Immediately before saving, reread the source, exact destination and affected route. Reconcile concurrent edits. A disabled rule is still saved account state; do not create one under a proposal-only request. If saving activates immediately, complete the scope and consent checks first.

Apply only the approved delta. Separate adding a destination, recipient verification, saving a rule and enabling it; these can finish independently. Record each as absent, pending, saved, enabled, blocked or unknown. Do not call a pending verification a working route.

Reopen the exact settings and compare destination, conditions/exceptions, selected native action, enabled state, source-copy behavior and affected rule interactions. Check for an accidental all-mail route or duplicate rule. Preserve unrelated filters, read state, folders and prior mail. A success banner without readback is an accepted operation with an unverified result.

## Verify delivery at the right boundary

Return separate evidence levels:

1. **Prepared:** a provider-specific route is defined, with no saved configuration claimed
2. **Destination verified:** the provider reports the destination eligible; no claim that routing is enabled or authorized solely from this state
3. **Enabled and read back:** the saved route matches the approved contract; actual delivery may remain unobserved
4. **Observed for a named message:** an authorized source arrival and destination copy establish that particular delivery, alongside source retention and actual sender/reply presentation

Use existing authorized arrival evidence when sufficient. If a live test is requested, establish its sender, source mailbox, destination, benign content and timing. Do not send to a colleague, vendor or arbitrary test inbox without that authority. Prefer a separate approved sender when testing an incoming route; a message sent from the forwarding mailbox to itself can exercise different provider behavior and must not be treated as an independent acceptance test.

Correlate source and destination with available provider IDs, message headers, timestamps and the approved test marker. Forwarding can wrap or rewrite identity, so equal subjects or a shared thread are insufficient. Inspect destination evidence only where access is already authorized or the recipient supplies it. Verify the requested body/attachment presence without opening executable content, and inspect the source's retained copy. A retained source copy does not establish forwarding, and a destination copy does not prove exclusion of nonmatching mail.

Keep Inbox placement, spam placement, transport acceptance and human reading distinct. Missing destination evidence may require [delivery tracing](../trace-email-delivery/SKILL.md), not another send or a spam-policy exception. For excluded sample messages, report the inspected destination search/window; absence in a partial view is not a guarantee that nothing was disclosed.

If the requested outcome includes observing an arrival, use the named message or expected category and agreed observation window. Continue the authorized check until that outcome/window is resolved or a precise access/recipient action blocks it. Otherwise finish setup with delivery explicitly unobserved; do not add ongoing inbox monitoring.

## Stop or recover without losing mail

After an uncertain save, inspect the existing destination and exact rule before retrying; do not generate repeated verification messages or duplicate routes. On an unintended destination or overbroad route, stop dependent tests, report the discrepancy and perform only authorized targeted containment. Restoring an earlier route can resume disclosure and needs the applicable current authority.

For a requested shutdown, identify whether to disable one rule, remove its forwarding action, disable account-wide forwarding or remove an unused verified destination. These are different changes. Inspect all relevant routes before claiming forwarding to that address ended. Disabling the broad setting alone is not proof that filtered forwarding stopped; deleting one rule is not proof that the account-wide route stopped. Remove a destination only after checking dependent routes and the approved removal scope.

Read the changed configuration back. Account for concurrent edits and partial completion rather than restoring a whole stale rules export. Stopping future routing cannot retract copies, attachments or notifications already delivered, nor does it delete the destination's history. Do not delete source mail, bulk-clean destination copies or change retention to simulate rollback.

If a policy blocks forwarding, preserve the exact provider error and the narrow owner/admin decision needed. Do not fall back to manual forwarding, a new relay, alternate domain, whitelisting or altered authentication to evade the block. A supported configuration proposal and precise policy blocker are an honest result.

Return the source and destination identities privately, the message-category contract, native action and source-copy policy, actual configuration/verification state, observation evidence or its limit, unresolved dependency and supported stop route. Finish at the requested proposal, setup, bounded observation or shutdown result. Historical mail transfer, recipient replies and continuing operational ownership remain separate requests.

## Fictional, unexecuted illustration

An invented user asks for future public workshop bulletins from a particular list in their Gmail account to reach their own named secondary mailbox, while retaining the source copies. Private replies and attachments from unrelated senders are excluded. The destination has not yet been verified, and a preexisting account-wide route to a different address is visible.

The proposal resolves the precise bulletin criterion and previews a bulletin, a same-subject private reply and an unrelated sender. It does not treat one matching conversation as permission to forward all replies. It records the old broad route as a separate scope decision, obtains the disclosure authority for the named destination, and leaves all-mail forwarding untouched until that decision is resolved. Recipient verification would establish destination eligibility only; the selective route would still need saving and readback. A later approved bulletin copy could establish one observed delivery, while a future stop date would remain manual unless real expiry support existed.

All accounts, messages, settings and outcomes are invented. No mailbox was accessed, route configured, verification requested, email sent, application used, policy changed or delivery observed for this illustration.
