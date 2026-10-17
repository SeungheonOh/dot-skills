---
name: reconcile-retail-order-status
description: "Reconcile selected retail orders into an item-level record of what remains to arrive, be returned, replaced or financially resolved, using order changes, package events and refund evidence. Use for split-order follow-through, not shopping, initiating returns, filing disputes or making payments."
---

# Find what is still outstanding on a retail order

Deliver a current, source-linked answer for each purchased item: what was ordered, what the seller says it shipped, what the user actually reports receiving, and which return, replacement or refund step remains open. Keep quantities, physical custody and money in separate views so a green order badge cannot hide an unfinished obligation.

Use [purchase-offer-comparison](../purchase-offer-comparison/SKILL.md) before buying, [return-deadline-evidence](../return-deadline-evidence/SKILL.md) for a policy-bound return cutoff, [warranty-evidence-packet](../warranty-evidence-packet/SKILL.md) for a coverage claim, and [prepare-support-case-handoff](../prepare-support-case-handoff/SKILL.md) when the main need is continuity across support contacts. This workflow reconciles existing records without ordering, canceling, returning, exchanging, accepting a settlement or contacting anyone on its own.

## Bound the order review

Identify the selected merchant/account and orders, exact variants and quantities, available order confirmations/changes, shipment records, user receipt notes, return authorizations and payment/refund evidence. Establish an as-of date and the user's practical question, such as “What is still missing?” or “Which refunds have only been promised?” Reuse available records rather than requesting an entire mailbox or financial statement.

Read current order and carrier records through authorized connectors or verified official interfaces when the question needs current status. A supplied email-only review remains useful but must disclose its cutoff and missing portal coverage. Verify consequential OCR fields against the original receipt or page. Preserve originals; do not modify merchant records to match the ledger.

Keep the output private by default. Order links and tracking URLs can carry access tokens or reveal addresses, household purchases and delivery locations. Retain necessary identities in a private source register, minimize them in the summary, and do not paste tracking numbers or signed order URLs into a public search engine. Use the merchant's verified account/order route or the identified carrier's official tracking interface; follow any required personal-data transmission approval. Do not request card numbers, credentials or unrelated balances.

A private reconciliation request does not authorize a support message, refund request, change of delivery address, carrier release instruction, claim, payment dispute or extra purchase. If a separate action is already specifically authorized, carry its exact authority forward through its own appropriate workflow. Missing evidence can be a question for the user without creating a merchant contact.

## 1. Reconstruct the order lines and their revisions

Namespace each order by merchant/seller and account. A marketplace is not necessarily the seller, and the same displayed order number can occur in different services. Bind every source to the appropriate order or leave the match unresolved.

Build canonical line identities from the actual order line ID where available, with product, variant, condition, ordered unit and quantity. Retain separate lines for separate purchases of the same SKU. Distinguish one pack from its contained pieces, a bundle from its components, and a replacement from an additional paid purchase. Do not compare three retail packs with three individual pieces without the evidenced conversion.

Record order changes as dated events: accepted addition, accepted cancellation, quantity change, substitution, backorder update or correction. Preserve the original commitment and the change evidence. A customer's cancellation request is not a confirmed cancellation; a vanished line in a partial screenshot is not proof it was canceled. An order edit should not erase an already dispatched item from the physical history.

Reconcile duplicated evidence before counting. A merchant email, order-page row and carrier notice can describe one shipment. Forwarded confirmations do not create new purchases. Same amount and date alone do not prove two charges or orders are duplicates. Retain the source links supporting each canonical fact.

For each line, retain a gross ordered quantity after evidenced additions or quantity corrections but before cancellation. Account for that quantity at the cutoff with mutually exclusive allocations where evidence permits: canceled before dispatch, dispatched against the original obligation, still unshipped, or allocation unresolved. These allocations must sum to the gross ordered quantity; show the net uncanceled quantity separately. If a source already reports a net quantity, do not subtract its cancellation a second time. If later evidence contradicts the allocation, expose it rather than forcing a balancing “missing” quantity. A dispatched item can later be returned; do not subtract that return from the historical dispatched quantity.

## 2. Map packages to exact items and stages

Create a package-to-line allocation using the merchant's actual shipment contents or packing evidence. One order can use several packages; one package can contain several lines or even several orders. Preserve those many-to-many relationships. Do not infer every item in an order arrived merely because one tracking number says delivered.

For each package record carrier, supported shipment identity, allocated line quantities, event/source timestamp, destination match at the minimum necessary granularity, promised or estimated dates, and current reported state. Distinguish:

- Label or tracking number created
- Carrier acceptance or pickup evidenced
- In transit or out for delivery
- Delivery attempted, exception, collection available or return-to-sender
- Carrier-reported delivered
- User-reported received, including which items and quantities were actually inside

These observations can conflict and must retain attribution. A created label does not prove physical handoff, and a missing acceptance scan does not prove that handoff has not occurred. Use “dispatch not evidenced” unless a source specifically supports an unshipped state; retain that source's attribution. A carrier delivery scan does not prove the expected contents, correct variant, condition or the user's possession. A parcel delivered to a collection point still has a different next action from one the user has collected. Do not infer theft, fraud or seller fault from a missing parcel.

Keep scan/event time separate from retrieval time and from an estimated arrival date. Preserve the provider's timezone when supplied. A stale “arriving tomorrow” email is not a fresh promise. If the record gives only a date range, carry that range without inventing a precise deadline. A changed estimate updates planning but does not prove a contractual breach.

Interpret status labels using that service's current documentation. For example, Shopify's [order-status reference](https://help.shopify.com/en/manual/fulfillment/managing-orders/order-status) separates order, payment, fulfillment and return states; fulfillment is not a universal statement that the customer inspected all items. Its [customer order-status guidance](https://help.shopify.com/en/manual/fulfillment/setup/order-status-page/understanding-order-status-pages) describes separate sections for multiple fulfillments and carrier-dependent tracking. These are examples of why the underlying records matter, not definitions to impose on another merchant.

If contents cannot be allocated, report “one package delivered; item coverage unresolved” rather than assigning the earliest lines until the count fits. Ask for the packing list or a bounded user receipt count only when it would change the result. Physical inspection remains user-reported unless actually observed through authorized evidence.

## 3. Keep returns and replacements as linked lifecycles

Link each return or exchange to the original line, quantity and specific fulfillment when available. Track the actual stages independently:

`requested; authorized; label issued; handed to carrier; carrier-reported received by destination; merchant acknowledged/inspected; remedy decided; remedy completed`

A label is not evidence that the user shipped the item. A carrier scan at the return warehouse is not merchant inspection, and an approved return does not establish a refund. Preserve declined, withdrawn, expired and uncertain requests instead of converting them into completed returns. Record any documented request-by, ship-by or received-by date without inventing a policy interpretation; route consequential date calculation to the return-deadline workflow.

A replacement needs its own fulfillment identity linked to the original issue and evidence of authorization. It may have a new order number or no additional charge; neither fact should be assumed. Keep its shipped and received quantities separate from the original purchase quantity. An original that later arrives does not automatically cancel the replacement, create a new purchase or authorize keeping/discarding it.

Track return obligations and replacement progress separately. For a conditional exchange, record any requirement to return the original, evidenced deadline, and stated charge condition. Do not infer acceptance of that condition from a support suggestion. A replacement received before the original is returned can leave an important task open.

When a substitution, store-credit remedy, fee or settlement changes what the user would receive, distinguish offered from accepted and completed. Do not choose a remedy to make the ledger close. Keep a wrong or damaged item separate from an undelivered item and preserve the user's reported condition without manufacturing evidence or a diagnosis.

## 4. Reconcile money without confusing promises with postings

Use decimal arithmetic in each stated currency. Record the order's evidenced item subtotal, discounts, tax, shipping and fees, plus later adjustments where available. A quoted total without a breakdown remains a quoted total; do not manufacture tax or per-item discount allocations.

Maintain separate money stages:

- Authorization/hold, captured or posted charge, and released/voided authorization
- Refund requested or promised, merchant-issued/pending/completed status, and a matched credit on the user's payment record
- Store credit, gift-card credit or replacement value, kept separate from money returned to the original payment method

A released hold is not both a refund and a negative purchase. A charge confirmation and matching statement posting are evidence for one charge. A refund email and matching posted credit are likewise one refund. Match by available transaction/reference, amount, currency, merchant and plausible timing, leaving ambiguous matches unresolved. Do not require a whole statement when a selected relevant transaction is sufficient.

Where posted payment evidence is available, calculate observed net cash outlay per currency and payment method as posted charges minus posted refunds. Keep pending holds and promised refunds outside that total. Where only merchant records are available, label the result merchant-reported net charged/refunded and leave payment-account receipt unverified. Do not call an issued refund “received” merely because a portal says complete.

For a specific refund, retain item quantities, amount/currency, any evidenced shipping/tax/discount adjustments, destination payment type, provider status and its stated processing window. Partial refunds may not equal unit price multiplied by quantity. A refund without item allocation can be reconciled at the order level while the line-level amount remains unknown. Do not apply one aggregate credit to several lines and then sum it again.

Shopify's [payment-refund guidance](https://help.shopify.com/en/manual/payments/shopify-payments/payouts/refunds) distinguishes processing from the customer's bank receipt and offers transaction-reference tracing. Use the actual provider's current guidance for the selected order rather than copying a generic wait period. A pending record or missing credit in an incomplete statement is not proof that a refund failed.

Keep currency conversions separate. A foreign-currency charge and refund can have different posted home-currency amounts; do not reuse the purchase rate to declare a discrepancy. This workflow records transactions and open evidence, not legal entitlement, compensation, chargeback eligibility or investment/financial advice.

## 5. Produce the current next-action view

Lead with the answer the user needs, then provide compact line, package, remedy and money views only as needed by the complexity. Each open item needs a source-supported next condition, such as awaiting carrier acceptance, item receipt unconfirmed, awaiting merchant inspection, or refund issued with account credit unverified.

For every open row include the responsible party only when supported, the last evidenced update, any actual date/processing window, the next useful check and the exact missing fact. Keep a proposed action distinct from an action taken. If a provider promises an update by a date, retain that promise with its source; do not invent a standard escalation interval.

An order is fully reconciled when its selected purchase quantities, physical outcomes and financial dispositions are all accounted for under the user's scope. A report can be complete while the order itself remains open. A seller's archived/closed badge does not settle unresolved receipt or credit evidence.

For an update, preserve stable row identities and the prior cutoff, incorporate newly evidenced events once, and recompute affected views. Do not reopen a resolved item simply because an old forwarded message arrived later. Conversely, a later contradictory receipt report can change the current conclusion even if the merchant previously marked the case closed.

If the user requests continuing tracking, establish the selected orders, authorized sources, bounded completion condition and useful notification events. A one-time status request ends with the snapshot. Do not create a recurring monitor, send nudges or accept delivery instructions solely because a row remains open.

## Acceptance, preservation and recovery

Before delivery, check the saved report against the source records:

- Every selected order line and revision is represented, with pack/unit meaning and quantity allocation reconciled
- Package coverage is evidence-backed; carrier delivery and item receipt remain distinct
- Returns, replacements and original shipments retain their links and do not inflate purchased quantities
- Each money event is counted once, by currency and stage; unknown fees or missing credits never become zero
- Offered remedies, requests, approvals, dispatch, receipt and completed credits are not collapsed into one “done” state
- Conflicts, unavailable sources and the as-of cutoff remain visible in both the summary and detail
- No original records, account settings or merchant state were changed by the review

Save to the authorized private destination and reopen the exact version to check quantities, signs, dates, source links and status wording. If saving is uncertain, inspect before retrying. Preserve newer edits in an existing tracker; do not replace it from a stale export. If access to a provider is blocked, finish the supported records and identify the exact missing observation without guessing current status.

Return the artifact or concise ledger, the few actionable outstanding items, verified completed portions and limitations. Finish at the requested snapshot or tracking condition. A ready follow-up question is useful; it is not permission to send it or submit a claim.

## Fictional, unexecuted illustration

A fictional order contains three identical lamps. The seller confirms one lamp canceled before dispatch. Package P1 is allocated one lamp and the user reports receiving it. Package P2 is allocated the other lamp and has only a label-created event. The original three units therefore reconcile as one canceled, one dispatched and received, and one with dispatch not evidenced in the unresolved allocation. The label alone proves neither dispatch nor that the lamp is still at the seller.

The user returns the received lamp. A return-carrier receipt shows it reached the merchant, but no inspection is evidenced. The seller separately reports issuing a USD 24 credit for the canceled lamp; no payment-account evidence is supplied. The report leaves P2's carrier acceptance, the returned lamp's remedy and the USD 24 credit's account receipt open. It does not label the order complete or count the return as a fourth purchased lamp.

All names, identifiers, quantities and amounts are invented. No account was accessed, package tracked, item returned, message sent, refund requested or payment made for this illustration.
