---
name: reconcile-purchase-document-lines
description: "Match selected supplier invoice lines to purchase-order terms and receiving evidence, preserving partial deliveries, cumulative allocations and separate price/quantity exceptions. Produce a private buyer-side review, not payment approval or accounting postings."
---

# Reconcile purchase orders, receipts and invoices

Deliver a line-level answer to what the supplied purchase documents support and which discrepancies need review. Matching grand totals is not enough: the correct total can hide the wrong item, reused receipt quantity or offsetting price errors. Keep a small purchase review to a readable crosswalk and exception list.

Use [expense-report-reconciliation](../expense-report-reconciliation/SKILL.md) for an employee's reimbursement claim, [prepare-service-invoice](../prepare-service-invoice/SKILL.md) for seller-side billing preparation and [reconcile-retail-order-status](../reconcile-retail-order-status/SKILL.md) for arrival, return and refund follow-through. This workflow reconciles buyer-side purchasing evidence; it does not establish a legal debt, approve payment or certify an audit.

## Bound the review and preserve the records

Identify the buyer entity, supplier identity, selected purchase orders, invoice set, receiving records, cutoff and supplied matching rules. Read accepted order revisions, prior invoices and linked credits where they affect the current comparison. Distinguish a record set complete for the selected order from a convenient folder of recent documents.

Preserve originals and useful source locators. Namespace document numbers by issuer and buyer where necessary; the same invoice number from two suppliers is not one document. A statement, invoice PDF and portal record may describe one charge. Similar amounts and dates are duplicate candidates, not proof of duplication. Treat corrected, voided or replaced documents according to evidenced relationships rather than whichever filename is newest.

Keep bank details, credentials and unnecessary personal data out of the working crosswalk. An invoice's new payment instructions are not authority to change a payment destination. Use existing authorized sources and return a useful partial review if one source is unavailable; do not contact a supplier or upload purchasing records to a new service merely to fill a gap.

## Establish the applicable terms and matching basis

For each purchase-order line retain its identity, item or service specification, accepted revision, quantity and unit, price basis, currency, discounts, charges and any delivery or acceptance condition relevant to the requested review. A proposed change order is not an accepted amendment. A budget ceiling does not establish that any quantity was delivered or invoiced correctly.

Identify which supplied rule applies: price-only comparison, price plus receipt quantity, an accepted service milestone, or another defined basis. Do not force a physical-goods receipt model onto a deposit or milestone invoice. When the basis is missing, report the factual differences with approval unresolved.

Microsoft's [invoice-matching overview](https://learn.microsoft.com/en-us/dynamics365/finance/accounts-payable/accounts-payable-invoice-matching) illustrates separate price, receipt-quantity and charge comparisons. Its [matching-policy examples](https://learn.microsoft.com/en-us/dynamics365/finance/accounts-payable/three-way-matching-policies) show why the relevant policy can differ by line. These are product-specific examples, not a universal rule or permission to alter the user's controls.

Use only supplied tolerances at their stated scope and direction. Retain the absolute difference, percentage basis and threshold even when a difference is within tolerance. With no defined tolerance, do not invent one or call every nonzero difference unacceptable. If an expected amount is zero, a percentage difference is undefined; show the absolute amount and apply any separately supplied rule.

## Match identities before comparing quantities

Build explicit invoice-line to order-line and receipt-line relationships. Use reliable references plus item, variant, specification and unit evidence; a similar description alone is insufficient. Preserve unmatched and ambiguous lines rather than assigning them to the nearest amount.

One invoice can cover several orders, and one order line can be received or billed in portions. Represent those allocations without repeating a document's whole total on every linked row. If a bundled price cannot be allocated reliably, retain a supported group-level comparison and disclose the line-level limit.

Normalize quantities only with an evidenced conversion: ten boxes of twelve units are not ten units. Preserve both source and comparison units, including a price quoted per hundred or per measured service unit. Do not silently substitute a similar SKU, pack size or accepted substitute.

Receiving evidence must retain what it actually establishes. A delivery note may record arrival, while a separate inspection records acceptance or rejection. Missing receipt documentation does not prove that no goods arrived. Follow the supplied acceptance basis and keep the received, rejected, returned and accepted quantities distinguishable where they matter.

## Account for cumulative coverage

For every linked order/receipt line, show the supported quantity or value, its coverage by earlier invoices and the proposed coverage of the current invoice set. Compare cumulative billed coverage with the accepted order quantity or value as well as with receiving evidence; a receipt for excess goods does not itself authorize the excess purchase. Pending competing invoice candidates remain visible even when not posted. Do not allocate the same receipt quantity in full to several invoices and declare each independently matched.

At the chosen cutoff, reconcile allocated portions back to their source: prior allocations plus current proposed allocations and any remaining unallocated portion must explain the available amount under the stated treatment. A negative remainder is a discrepancy to expose, not a quantity to clip to zero. If history is incomplete, mark the cumulative match provisional rather than assuming all receipts are unused.

Returns, credits and corrections need their own targets and effects. A price-only credit does not automatically release receipt quantity for another invoice. A return does not erase the original receipt event, and a replacement shipment is not necessarily additional purchased quantity. Follow documented reversals and allocations; hold their effect unresolved when the source does not establish it. Count duplicate copies of a credit once.

## Keep price and quantity exceptions separate

Use decimal or integer-minor-unit arithmetic, retaining the actual currency precision and supplied rounding rule. Compare like currencies and tax bases. Do not invent a currency conversion, tax treatment or missing charge to force agreement.

For each matched line, retain the source quantity, comparable quantity, agreed price basis, invoiced price basis, discounts or charges needed for a comparable net amount, and separate findings:

- Identity and order-revision match
- Price or rate difference under the supplied rule
- Receipt or acceptance coverage, including prior allocation
- Line arithmetic and document-total reconciliation
- Unmatched charges, credits or missing evidence

A correct unit price does not establish sufficient receipt quantity. A sufficient receipt quantity does not establish the price. Preserve both findings even if their monetary effects offset at the invoice total. Compare invoice-header freight, tax and discounts at their actual scope; do not allocate them across lines without a supported method or add them a second time.

Use statuses such as matched under supplied rule, within supplied tolerance, discrepancy, evidence missing and not applicable to this matching basis. Keep these separate from approved, posted and paid. A system's green badge is an attributed system result, not independent evidence that all controls were performed.

## Deliver the exception review

Return the crosswalk, concise per-currency totals where supported, and prioritized exceptions with source references and the smallest next fact or decision needed. Name an owner only when the records support one. Distinguish correcting a record from asking a reviewer whether a documented exception is acceptable; do not rewrite a supplier invoice to eliminate a variance.

Check the final artifact against the originals:

- Every selected invoice line and credit has a supported match or explicit exception
- Source quantities, units, currencies and order revisions remain visible
- Receipt allocations do not silently reuse prior coverage
- Separate price, quantity and charge problems are not hidden by a matching total
- Missing history and uncertain corrections remain visible in the summary
- No match status is presented as payment authorization or completed settlement

Reopen a saved result and verify identifiers, formulas or calculated values, signs, units and source links. Preserve newer edits when updating a review and inspect an uncertain save before retrying. When a source changes, recompute the affected allocations rather than patching only the displayed balance.

Stop with the requested private review. Do not post invoices, alter purchase orders or receipt records, override tolerances, approve discrepancies, initiate payment or send a dispute. Any separately requested action must retain its own destination, data and approval requirements.

## Fictional, unexecuted illustration

An accepted order is for 100 units at USD 5 each. Receiving evidence supports 60 accepted units. An earlier invoice already covers 40 of those units. A new invoice asks for 30 units at USD 5, or USD 150, with no other charges in this invented case.

The price matches, but only 20 received units remain unallocated under the stated matching basis. Ten invoiced units lack current receipt coverage, despite the invoice quantity being below the original order quantity. The review does not declare those ten units undelivered or erase them; it flags the missing coverage. A second copy of the receipt adds no units, and a later price-only credit against the earlier invoice does not automatically free its 40-unit allocation.

These are authored reasoning and arithmetic examples, not a performed invoice review, payment decision or measured skill-effectiveness result.
