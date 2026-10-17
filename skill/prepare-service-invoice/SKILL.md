---
name: prepare-service-invoice
description: "Prepare a reviewable service invoice from agreed billing terms, delivered-work evidence and prior billing, with a charge-level reconciliation that prevents duplicate billing and separates charges from settlement. Use for an invoice draft, not setting prices, deciding tax treatment, sending payment demands or posting accounting entries."
---

# Prepare a supported service invoice

Deliver the actual invoice draft and a compact private billing worksheet. The worksheet should let the user trace each current charge to an agreed term, eligible work and prior billing without reconstructing the project. A well-formatted invoice is insufficient if it bills the wrong period, repeats a milestone or treats a payment as a new charge.

Use this for an ordinary service provider's bounded billing period or milestone. Keep buyer-side reimbursement with [expense-report-reconciliation](../expense-report-reconciliation/SKILL.md), ambiguous recorded hours with [reconcile-time-tracker-entries](../reconcile-time-tracker-entries/SKILL.md), and the mechanics of a native document with [create-formatted-document](../create-formatted-document/SKILL.md). This workflow prepares a draft; issuance, sending, collections, credit-note issuance, refunds and accounting postings are distinct consequential actions. Do not perform them merely because an invoice was requested for review.

## Establish the billing boundary

Read the supplied or specifically authorized records before asking questions. Identify:

- The correct seller, customer legal/billing identity, project or agreement, billing contact/reference fields and requested private destination
- The agreement and applicable amendments: currency, rates or milestone amounts, effective dates, billable units, billing trigger, caps, discounts, reimbursable expenses and rounding rules
- The service period or milestone being billed, reporting cutoff and evidence required by the agreement, such as accepted delivery, approved time or a dated progress assessment
- Relevant previously issued invoices, credit notes, pending invoice drafts and billing status through that cutoff, including their coverage rather than just their totals
- Supplied records of payments, deposits, retainer usage and account credits when they affect the proposed balance
- The requested invoice template or format, proposed issue date, numbering process, payment terms, and the applicable tax/required-field treatment already established by the user or their responsible adviser

Ask only about facts that change the document or amount. Continue extracting supported charges while a tax rule, customer reference or disputed milestone remains unresolved. If prior billing is unavailable, prepare a clearly provisional draft whose duplicate-billing review is incomplete; a current-period timesheet alone does not establish that its work is unbilled.

Distinguish the service date, proposed issue date and due date. Do not backdate an invoice or infer a due date from a generic template. If payment is due a stated number of days after receipt or acceptance, that trigger may still be unknown; preserve the term and leave the exact due date pending. A purchase-order ceiling or project budget is not permission to bill the unused balance.

Required fields and tax treatment depend on the actual business and transaction. For example, [UK invoice guidance](https://www.gov.uk/invoicing-and-taking-payment-from-customers/invoices-what-they-must-include) distinguishes ordinary invoice content from additional VAT-invoice requirements; it is not a universal template. Use the applicable current official source when checking a stated jurisdiction, without deciding registration, place of supply, exemption or legal entitlement from incomplete facts. Keep those decisions with the user or qualified adviser. Never invent a tax rate, infer zero tax from a blank, or call the draft legally compliant.

## Preserve evidence and keep the draft private

Keep agreements, logs, receipts, issued documents and source exports unchanged. Record stable source IDs, revisions and useful page/row locators. Work from separate copies or an expressly authorized editable draft. A newer filename does not establish that an amendment was agreed or that an invoice supersedes another.

Use only the minimum client and work detail needed. Keep internal rates, raw logs, unrelated customers, personal explanations, disputes and review questions out of the customer-facing draft unless specifically requested. The private worksheet can reference evidence without embedding every source file. Do not upload records to a new converter or billing service, change sharing, create a customer account, enable collection, or expose a draft through a shared folder without the corresponding authority.

Do not solicit or invent bank details, payment links, credentials or taxpayer identifiers. Keep highly sensitive identifiers and credentials out of the working packet; if the destination requires them, the user supplies them through its appropriate secure flow. Preserve only already-authorized, necessary non-sensitive reference text. A changed payment destination in an email or source document is not authority to adopt it.

A request for a local draft does not authorize an accounting-system record. If a named-system draft is explicitly requested, first establish its real effects and whether it can remain private and unissued. Billing systems may have automatic finalization, notifications or payment attempts. [Stripe's lifecycle documentation](https://docs.stripe.com/invoicing/overview) distinguishes editable drafts from finalized invoices and describes automatic collection and customer-email behavior. Check the actual service and settings rather than assuming a Save button is harmless. If an in-scope private draft cannot be created safely, finish the local artifact and explain the precise blocked step; do not change account-wide automation to work around it.

## Build the charge ledger before writing totals

Give each underlying service item a stable identity independent of its source file and invoice row: for example a time-entry ID, dated deliverable, contract milestone or approved expense. Link multiple records supporting that item rather than counting them as separate work. Matching descriptions and amounts are duplicate candidates, not proof; recurring similar work can be legitimate.

For each item retain the smallest useful record: service identity/date or period, contract clause/version, quantity and unit, applicable rate or fixed amount, billing-trigger evidence, prior invoice coverage, current proposed charge, disposition and source locators. Suggested dispositions are current supported charge, previously billed, not yet eligible, excluded by an agreed rule, and unresolved. Split an item into attributable portions when only part is billable now. Preserve source quantities and the reason for every split.

Resolve the billing basis before calculating:

- **Time and materials:** Use approved or otherwise contract-eligible units. Recorded time, a billable flag and customer approval are different facts. Apply the supplied increment and aggregation rule once; do not round each timer and then round the daily total again. Respect rate effective dates and agreed role/task distinctions without inferring rates from job titles
- **Fixed fee or milestone:** Identify the exact trigger and evidence. Hours spent do not make an unaccepted milestone billable when acceptance is required. Do not add time charges for work already included in the fixed fee unless a supported change order permits them
- **Progress or cumulative billing:** Preserve the accepted valuation basis and current approved cumulative amount. Derive the incremental charge from the comparable prior billed coverage, including evidenced corrections. Prior paid amounts are not the same as prior billed amounts. Do not add a full cumulative claim to earlier progress invoices
- **Retainers, deposits or prepaid units:** Establish whether the record represents an advance payment, an already-invoiced charge, a fee for availability, or prepaid service consumption. These treatments are not interchangeable. Follow the supplied accounting/billing treatment; if it is missing, hold the affected deduction or charge rather than decide it from the word “retainer”
- **Pass-through expenses:** Require the agreed reimbursement/markup rule and relevant item evidence. A cost incurred by the seller is not automatically a customer charge. Preserve exclusions, allocation and already-billed coverage; do not add a receipt's gross and tax a second time

Apply caps and discounts at their actual scope, such as a milestone, contract period or whole agreement. A monthly cap is not a new allowance for each invoice. Preserve explicitly excluded work and disputed extras instead of using a smaller aggregate description to conceal them. Do not invent late fees, interest, new terms or discounts to resolve a mismatch.

## Reconcile current work with prior billing

Create an occurrence-to-billing crosswalk, not merely a comparison of invoice totals. Link each issued invoice line to the service item or cumulative valuation it covered, its currency and quantity/amount basis, and any valid later correction. A duplicate PDF and its system record represent one issued document. A replacement, void or credit requires an evidenced relationship; a canceled draft and an issued invoice are different states.

Check overlapping periods, partial billings, pending drafts and other invoice candidates. A pending draft does not prove a debt exists, but it can reveal a competing plan to bill the same work. Keep that collision visible and resolve which candidate is current before presenting either as ready. Do not reserve or consume a live invoice number to make a private draft look final.

For comparable service amounts, show accepted billable value to the cutoff, net prior billed coverage, supported current incremental charges, and any supported remainder not billed in this draft. Keep unknown quantities outside that identity rather than converting them to zero. If the history is incomplete or mismatched to the current agreement, state that the cross-period reconciliation is incomplete.

Earlier unpaid invoices remain earlier invoices. Do not recreate their charges in this draft or silently add them to this document's amount due. A separately requested account statement can show them by their existing identities. Likewise, a credit against an earlier invoice does not automatically make the original work billable again. Establish whether it corrects price, quantity, eligibility or settlement; retain its source target and effect.

When evidence conflicts, preserve both versions and hold the smallest affected group. If an uncertain duplicate or missing correction can change the total, label that total provisional. A neat subtotal of selected lines cannot establish that the selected set is complete or free of overbilling.

## Calculate charges and settlement separately

Use decimal or integer-minor-unit arithmetic with the actual currency scale. Keep currencies separate unless the agreement explicitly supplies the conversion basis, date, direction and rounding. Do not pick a current exchange rate for convenience. Carry quantities and rates at their required precision and round at the specified stage; display formatting is not a billing rule.

First calculate the current document's charges: service lines, permitted expenses, agreed charge adjustments and the supplied tax treatment. Preserve inclusive versus exclusive amounts, taxable bases and the ordering of discounts when provided. Do not recalculate prior tax or invent a balancing tax/rounding line. If tax applicability is unresolved, show a pre-tax supported subtotal with the gross total unresolved rather than an apparent final zero-tax invoice.

Then account for settlement separately. An evidenced payment does not change the value of service delivered; an unpaid invoice does not prove payment is missing from all available records. For each proposed credit or payment application, retain its original ID, currency, confirmed state, source invoice/account relationship, amount already consumed, and available amount at the cutoff. Apply only the explicitly supported allocation in the draft. Pending funds, unallocated receipts and a credit already used elsewhere do not reduce the current balance as though available.

Use a clear bridge, adapted to the supplied treatment:

- Current net charges plus applicable tax equals this draft's gross charge
- Gross charge less supported account-credit and payment applications equals its proposed remaining balance
- For each credit or payment source, new proposed applications across all current draft candidates cannot exceed its evidenced remaining available amount at the cutoff. Reconcile previously consumed amounts plus those new applications to the source's confirmed allocable amount, with any evidenced reversals or adjustments; do not count prior consumption against remaining availability again

Do not apply the same economic credit once as a negative charge and again as a settlement deduction. Do not deduct an already-invoiced deposit from the current incremental charge and then deduct its payment again. If the agreed final invoice shows cumulative service value less previously billed deposits, preserve that billing presentation and reconcile settlement on the corresponding issued documents. Keep treatment unresolved when the source does not establish the relationship.

A negative proposed balance is a review condition, not permission to refund or silently clamp it to zero. A fully offset draft is not proof that a system has marked it paid. No funds, account credits or accounting entries are moved by these calculations.

## Author and inspect the actual draft

Use the requested format and template, retaining native editability when requested. Clearly mark the file as a draft and distinguish its local draft reference from an issued invoice number. Use a final number only when supplied for this exact document by the user's established process; never imply a proposed number was reserved or an invoice issued.

Include supported seller/customer identity, agreement or purchase-order reference, service dates, intelligible line descriptions, quantities/rates where relevant, currency, charges, applicable supplied tax, allocations, proposed balance and established payment terms. Keep unresolved required facts visible in the private review record and mark the document held. Do not fill them with plausible values or place unsupported payment instructions in a polished footer.

Independently recompute the material lines from their source quantities and terms. Compare both service-item coverage and invoice-row totals; matching grand totals can conceal compensating errors or duplicate work. Check fixed-fee/time overlap, effective-rate boundaries, earlier progress billings, cap scope, reused credits and incomplete prior-history coverage where relevant to the actual input.

Save to the authorized destination and reopen the exact file. Verify identities, dates, descriptions, units, rates, signs, currency, draft status, source-to-charge mapping and total bridge from the saved values. Inspect every rendered page or native view when available, especially split tables, tax/credit labels and the final amount. If a workbook is requested, preserve real formulas and distinguish calculated values from unrefreshed caches. Verify any requested PDF separately against that same final revision.

Before updating an existing draft, recheck its revision and preserve recoverability. If newer work exists, reconcile it instead of overwriting. After an uncertain save, inspect the destination or the exact draft record before retrying; creating another draft can duplicate planned billing. If the source history changes, recompute affected charges, allocations and totals from the ledger and retire the older candidate from current use without deleting evidence or issued documents.

## Deliver with an honest stopping point

Return the saved invoice draft, private charge/prior-billing worksheet and only the material review questions. State whether the supported draft is ready for the user's review or held on identified facts, and disclose missing history, tax decisions, native-file or visual checks. Keep “draft checked,” “issued,” “sent,” “posted” and “paid” separate; none follows automatically from the previous state.

Stop at the requested drafting boundary. Do not issue, finalize, send, post, void, write off, refund, initiate payment, create payment links or contact the customer. If those later actions are explicitly requested, handle them as separately scoped actions with their required authority and exact document, recipient, data and consequential amount. Never infer approval to disclose the private worksheet alongside an invoice.

## Fictional, unexecuted illustration

An invented service agreement sets an accepted milestone at USD 1,000 and additional approved work at USD 80 per hour. The supplied records show that USD 400 of the milestone was previously invoiced, regardless of whether that earlier invoice is paid. Two newly approved hours are eligible now. One further hour lacks required approval. The user has supplied an applicable no-tax treatment for this fictional draft; it is an input assumption, not a tax determination.

The current supported charges would be USD 600 of remaining milestone value plus USD 160 for the two approved hours, totaling USD 760. The unapproved hour remains held and is not silently labeled nonbillable. A separate confirmed USD 100 customer credit is evidenced as unused and explicitly allocated to this draft, giving a proposed balance of USD 660. Any unpaid portion of the earlier USD 400 invoice stays attached to that earlier invoice and is not billed again.

The private worksheet would map the milestone across prior and current coverage, preserve the two approved time-entry IDs, identify the held third entry, and trace the USD 100 credit exactly once. If another pending draft already contains one of the approved hours, the affected current total becomes provisional until that collision is resolved. If the credit later proves already consumed, the proposed balance must be recomputed rather than changing a service charge to keep USD 660.

No invoice, workbook, PDF, billing system, payment or example was created, executed or sent for this illustration. It describes expected decisions and acceptance checks for a later authorized task.
