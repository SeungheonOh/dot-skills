---
name: cancel-service-subscription
description: "Prepare or complete an explicitly requested cancellation of an ordinary non-regulated service subscription, resolving the actual biller, end date, remaining charges and access effects, then verifying the saved renewal state. Use for subscription exit, not cost inventory, refund negotiation, payment blocking or account deletion."
---

# Cancel a service subscription with a checked outcome

Complete the user's chosen subscription exit through the actual billing provider, or deliver the exact blocked decision and usable next step. Establish what will stop, when it will stop, what remains payable and which benefits or data may be affected. A clicked cancellation link, missing app or expired payment card is not evidence that renewal stopped.

Keep [subscription cost inventory](../subscription-cost-inventory/SKILL.md) for comparing recurring costs, [tool-switch planning](../plan-tool-switch/SKILL.md) for replacing a workflow, and [connected-app access review](../review-connected-app-access/SKILL.md) for a separate authorization grant. Canceling billing does not itself migrate files, remove an app's access, close the account or erase retained information.

Limit this workflow to ordinary non-regulated subscriptions, such as software, media or an optional consumer service. Do not use it to terminate financial products, insurance, healthcare arrangements, legal or education accounts, essential utilities, employment benefits or negotiated enterprise contracts. Those actions need their own domain-specific handling and authority. Do not infer that every product called a “membership” falls within this scope.

## Establish the intended exit

Recover these inputs from the request and relevant authorized records:

- Exact service, plan and account/workspace; which subscription or add-on is in scope
- Desired result: stop the next renewal, end service now, or prepare the cancellation for review
- Any required access-through date, data-preservation need, other affected users and approved cancellation-fee limit
- Evidence of the billing provider and purchase channel, current status, commitment period, payment frequency and next renewal
- Existing access route, applicable country/region and where the private confirmation should be retained

Ask only about a gap that changes the action or its consequences. When the user says “cancel” and the sole ordinary no-fee path stops renewal while retaining paid access, that may satisfy the request without another preference question. If immediate termination and end-of-term nonrenewal have materially different outcomes, resolve the choice instead of silently picking one. A request to investigate charges or reduce costs does not authorize cancellation.

Keep the desired outcome distinct from the provider's control label. A “Cancel” button may open a retention screen, submit a request for later handling, end access immediately, or merely turn off renewal. “Pause” may resume billing later. A downgrade or discount can create a new price or commitment. Choose a supported action because its documented and displayed effects match the user's instruction, not because its label sounds close.

## 1. Resolve the exact subscription and billing route

Use the relevant connected account read or verified official subscription-management interface. Match the service, plan, account, purchase channel and non-secret subscription/order identity where available. Keep similarly named plans, separate purchases, add-ons and household members' subscriptions distinct. Paying for a family purchase does not establish control of another person's account.

Trace the biller through a relevant receipt, the provider's management page or a selected payment record already available within scope. The company providing the app can differ from the app store, reseller or carrier collecting payment. An app-store installation is not proof that the store bills this subscription. Do not try cancellation in several accounts merely because the brand matches.

[Apple's cancellation guidance](https://support.apple.com/en-us/118428) directs users to identify the purchasing account from their receipt and to the actual billing company for subscriptions purchased elsewhere. Treat this as a route-finding example, not permission to sign into a family member's account or contact an unidentified merchant. If the current source cannot establish the correct purchase, leave identity unresolved and ask for the smallest useful receipt detail.

Record source and observation time. A stale renewal email can describe an earlier plan; a current service badge can lag billing. Preserve the conflict until the exact subscription is reconciled. A missing item in one list might reflect the wrong account, a filter, another biller or an incomplete listing, rather than an already completed cancellation.

Use secure supported sign-in if needed. Never request passwords, card numbers, recovery codes or full statements in chat. Do not create a new account, OAuth grant, payment method or administrative role just to reach a cancellation screen. Keep private receipt links, account IDs and payment references out of public searches and broadly shared reports.

## 2. Read the applicable cancellation effects before committing

Inspect the account-specific cancellation preview and relevant current official terms. Record product, plan, region, billing channel and effective version; generic public guidance may not describe an older or special offer. If sources disagree on a material effect, preserve both and hold that choice rather than declaring a legal interpretation.

Build a short effect record:

| Property | Establish from the applicable evidence |
| --- | --- |
| Billing commitment | Monthly/annual or other term, separately from how frequently installments are charged |
| Requested change | Renewal off, cancellation effective on a date, immediate termination, or request awaiting provider action |
| Dates | Cancellation cutoff if stated, next renewal, benefit end, remaining installment dates and any preservation deadline |
| Money | Displayed cancellation charge, currency, remaining committed payments and any automatically shown refund; distinguish quoted from posted |
| Access | Features, shared benefits, seats, storage limits, downloads/exports and affected people |
| Data | Evidenced read-only, retention or deletion effects, available preservation route and unresolved requirements |

Do not infer a month-to-month commitment from monthly billing. [Google Play distinguishes stopping renewal from remaining payments on a payment plan](https://support.google.com/googleplay/answer/7018481?co=GENIE.Platform%3DDesktop&hl=en). [Adobe's US plan guidance distinguishes annual paid-monthly, annual prepaid and month-to-month terms](https://helpx.adobe.com/account/individual/terms-policies-and-regulations/adobe-subscription-terms.html). These examples establish why the exact plan matters; do not copy their fees or refund rules to another account or region.

Preserve date-only information without inventing a midnight cutoff. For a precise deadline, establish its timezone and whether it governs receipt of a request or completed cancellation. A displayed renewal date alone does not prove the latest safe cancellation time. Check trial terms separately: Apple's linked guidance, for example, calls for trial cancellation at least 24 hours before expiry. Do not apply that interval universally or delay an authorized cancellation until the last possible moment.

Keep service access and stored data separate. An account can remain open with lower limits after paid benefits end. [Microsoft's cancellation guidance describes reduced storage and possible file or email disruption for over-quota accounts, including affected shared users](https://support.microsoft.com/en-us/accounts-billing/subscriptions/cancel-a-microsoft-365-subscription). Use the selected provider's actual rules and current relevant usage when available. Do not claim “your files are safe” because a login still works.

If a required file, export or shared dependency may become unavailable, surface the concrete effect and preservation decision before the change. Do not silently download a whole account, upload data elsewhere, delete files to fit a free tier or contact other users. Preservation work needs its own source, destination and authority. Continue the independent cancellation preparation while that decision is pending.

## 3. Check authority against the exact final effect

Carry forward the user's specific cancellation instruction and previously approved consequences. Do not manufacture an extra approval for an unchanged, already authorized no-fee cancellation. A provider's final confirmation step is part of that action when its actual effects remain within scope.

Pause only for a missing decision or required permission, identifying the exact subscription and consequence:

- An unapproved fee, amount above the user's limit, new paid plan, renewed commitment or materially changed effective date
- Immediate loss of access or shared benefits that conflicts with the user's instruction or was not covered by the approved scope
- A material data-loss consequence, required data transmission to a new recipient or a new legal agreement requiring acceptance
- An operation that also permanently deletes data or closes an account; keep it outside this workflow and obtain the separately required action-time confirmation or handoff
- A required contact or support message not already authorized for this cancellation, or a required reason that cannot be answered truthfully from the user's instruction

For any charge requiring approval, state the provider, exact subscription/action, total and currency, payment type, one-time versus recurring commitment, effective service end and visible cancellation/refund restrictions. Use a saved payment method only within its existing authority; never enter highly sensitive payment data yourself. Link any new required agreement and disclose it before acceptance. Do not accept a waiver, settlement or disputed liability as routine cancellation navigation.

Treat refunds as a separate outcome. Record an automatic refund shown by the approved cancellation path, with its amount and conditions, but do not promise account receipt or seek a discretionary refund without a request. If taking a refund requires ending access sooner, accepting store credit, releasing a claim or making another material choice, ask for that choice. A request to cancel does not authorize a chargeback, bank payment block, payment-method removal or negotiation.

## 4. Perform only the supported cancellation path

Immediately before the committing action, recheck the account, exact plan, final effective date and charges. If a new plan revision, renewal or concurrent user change alters those facts, update the effect record and resolve any material difference before proceeding.

Use the native cancellation or nonrenewal route. Keep unrelated plans and add-ons unchanged unless the user named them or the provider makes an inseparable bundle effect explicit and it is approved. Do not cancel an entire bundle to remove one component silently. [Adobe's cancellation instructions](https://helpx.adobe.com/account/individual/subscriptions-and-plans/renewals-and-cancellations/cancel-adobe-subscription.html) illustrate that independently billed plans require separate cancellation; the selected provider's actual relationships control the real task.

Continue through the necessary review and confirmation screens while preserving the intended result. Decline a retention offer rather than accepting a discount, pause, extension or replacement plan just to get past the screen. Do not use a plan switch as a workaround for a fee. If a cancellation reason is optional, omit it; if required, use a truthful supported choice or ask. Do not invent dissatisfaction, hardship or a technical fault.

Do not delete the app, disable notifications, revoke connected-app access or remove payment details as a substitute. Google's linked guidance explicitly notes that uninstalling an app does not cancel its subscription. A failed payment or suspended service is also not evidence of completed cancellation or extinguished obligations.

If the service requires human support, use its verified route. Prepare the minimal request with the exact plan and desired effective date. Send it only when that contact and the necessary account-data sharing are already authorized; otherwise ask for the missing approval. Do not upload a full statement or identity document to explain an ordinary cancellation. If the final step requires unsupported identity verification or sensitive information, hand over that step and retain the prepared context.

Record whether the action was submitted, accepted for processing or confirmed effective. A support case number establishes a request, not its completion. A success toast without a durable account result remains unverified.

## 5. Read back renewal and service state independently

Reopen or refresh the exact subscription's management view through the same trusted account route. Check the saved renewal setting, current lifecycle status, effective end date and any remaining-charge information. Retain a minimal confirmation reference or relevant screenshot privately when needed. A cancellation email can corroborate the result; its absence alone does not override a clear provider readback.

Use the provider's documented status meaning. [Microsoft distinguishes a plan set to expire from one with recurring billing enabled](https://support.microsoft.com/en-US/accounts-billing/subscriptions/turn-recurring-billing-on-or-off-for-a-microsoft-subscription). Do not generalize the presence or absence of a particular button across services. A still-active paid entitlement can coexist with renewal turned off.

Report separate supported states, rather than one ambiguous “done”:

- **Prepared for review:** the exact target, supported action, effects and remaining decisions are ready; no cancellation has been submitted
- **No change needed:** the exact subscription was already set to end in the way and on the date required by the user's request, with current evidence
- **Renewal stopped:** saved nonrenewal/cancellation evidence is confirmed; paid access may continue until the evidenced end date
- **Service ended:** the provider confirms termination effective now or on the stated past date; data retention is separately reported
- **Request pending:** the provider accepted the request but has not established the final renewal/end state
- **Outcome unverified:** submission may have happened, but a durable result could not be established
- **Held:** identity, consequences, permission or a required provider step prevents commitment

Do not claim no future charges when known installments, final usage charges, fees or unresolved billing remain. Show those separately from the renewal being stopped. Do not label an estimated avoided renewal as money refunded or achieved cash savings. A promised refund is not a posted credit; if receipt verification is requested, use only the bounded authorized payment evidence and preserve unmatched amounts.

## Acceptance, interruption and recovery

For preparation-only work, finish with the exact target, supported cancellation route, effect record and unresolved decisions; label the result prepared and make clear that no cancellation was submitted. For an authorized cancellation, completion requires matching the exact provider/subscription and requested exit, verifying the provider's saved result, and reporting its effective date, remaining obligations and relevant access/data limits. It is unnecessary to wait for already-paid access to expire merely to establish that renewal is off. If the user asks to track actual termination or refund receipt, keep that narrower outcome open until its evidence or an explicit stopping condition is reached.

- **Timeout after submission:** inspect the same target before retrying. If the change already took effect, do not submit again. If the unchanged state is established and retrying the same action is supported and safe, retry within the existing authority. If the result stays uncertain, stop mutations and report what can and cannot be verified.
- **Request awaiting processing:** preserve the request ID, provider's stated processing window and next useful read-only check. Continue authorized checks toward the requested completion condition when feasible; do not relabel unchanged pending evidence as completion or invent a processing deadline. Surface a missing capability or decision that prevents progress.
- **Wrong account or missing plan:** return to the evidenced billing route. Do not cancel a similar subscription, create a replacement account or access someone else's credentials.
- **Unexpected fee or collateral effect:** stop before the changed commitment, preserve the preview and ask one precise question. Continue independent preparation for other explicitly selected subscriptions.
- **Unexpected charge after a verified change:** match it to the exact plan, service period and payment stage before concluding failure. Keep a remaining installment, pending hold, another plan and an unexplained new renewal distinct. Do not dispute the charge automatically.
- **User changes their mind:** explain the supported reactivation route and its current price/term effects. Do not turn renewal back on to test recovery or assume the old price, trial or data can be restored. Re-subscription is a new commitment requiring its own authority.

Return a concise private receipt: service/plan, actual biller, change made or held, verified state and observation time, benefit end date, known remaining amounts, data/shared-use effects, confirmation reference and exact unresolved next step. Link the relevant official management item when safe. Include only the account detail needed to distinguish the purchase; avoid signed links or screenshots exposing unrelated subscriptions.

If an artifact was requested, save it to the authorized destination and read back its actual statuses, dates and references. Do not silently update a budget, subscription tracker or other account. A one-time cancellation does not create standing permission to cancel other services or monitor all future spending.

## Fictional, unexecuted illustration

The user names an optional fictional service, “Maple Notes Plus,” and asks to stop its next renewal while keeping paid access through 30 November. A supplied receipt identifies Store A as the biller; the app's own settings only link to Store A. The selected plan's fictional preview says renewal will stop, access ends on 30 November, there is no fee, and the account remains open. A second, similarly named plan belongs to a separate purchase and is out of scope.

The expected path is to change only the receipt-matched subscription, then read back Store A's saved nonrenewal state and the 30 November end date. Continued app access is consistent with that result. If the final page instead changes to immediate termination, the instruction to preserve access blocks commitment until the user decides. If submission times out, the next step is readback, not another click.

In a separate invented payment-plan variation, two USD 9 installments remain before the commitment ends. Stopping the next renewal would not erase those USD 18 of stated remaining payments. The handoff would show renewal stopped and the two remaining installments separately; it would not claim that all charges ended or that USD 18 was refunded.

All names, sources, dates, amounts and expected states in this illustration are invented. No account was accessed, subscription canceled, fee accepted, message sent, refund requested or payment made. This is an authored illustration, not an executed service test.
