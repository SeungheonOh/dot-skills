---
name: reconcile-bank-statement-ledger
description: "Reconcile a bounded deposit-account statement against an existing cash ledger, proving each balance and carrying matched, outstanding and correction-candidate items into a reviewable period-end packet. Use for read-only bookkeeping reconciliation, not forecasting, tax decisions, journal posting or moving money."
---

# Reconcile a bank statement to the cash ledger

Deliver a source-linked reconciliation for one cash account and cutoff: what the bank posted, what the books recorded, which differences are supported timing items, and which need evidence or a proposed correction. Produce the actual worksheet or report, including a reusable outstanding-item schedule. Equal totals alone do not establish that the right transactions were matched.

Use separate worksheets for separate accounts or currencies. This workflow covers an ordinary deposit account and its corresponding cash ledger. Credit-card liabilities, loans, investment positions, foreign-exchange revaluation, trust/client-money rules and consolidated financial reporting require their own established treatment. Do not extrapolate this account's signs or acceptance rule to them.

Use [expense-report-reconciliation](../expense-report-reconciliation/SKILL.md) for reimbursement eligibility, [shared-cost-reconciliation](../shared-cost-reconciliation/SKILL.md) for participant obligations, and [cash-flow-timing-calendar](../cash-flow-timing-calendar/SKILL.md) for future-balance scenarios. Those outputs do not establish a historical bank-to-books reconciliation.

## Establish the account, period and authority

Inspect the available records before asking for more. Identify:

- A sanitized account label, corresponding cash-ledger account, currency and amount precision
- Statement start/end boundaries, the bank's stated balance basis, opening/closing balances and complete posted-transaction coverage
- The ledger's opening/closing balances and cash-account movements for the comparable period, with posting dates and stable entry IDs
- The preceding reconciliation and its outstanding items, unresolved differences and correction status, when available
- Supporting references needed to distinguish similar payments, grouped deposits, reversals or corrections; bounded later records if supplied to establish subsequent clearing
- The requested cutoff, extraction/as-of timestamp, output format and authorized private destination

Distinguish bank posting date, transaction date, ledger posting date and later evidence date. Use the actual statement's period and posted-balance definition; do not substitute a current online balance for a historical closing balance. Preserve date-only records without inventing a time. If timestamps straddle a boundary, establish their source time zones and inclusion rule before moving an item between periods.

Keep pending authorizations and available-balance holds outside a posted-statement control unless the source explicitly defines otherwise. For example, [Chase's posting explanation](https://www.chase.com/personal/checking/overdraft-services/how-transactions-post) distinguishes pending activity affecting availability from completed posting. Apply the selected bank's actual definitions rather than imposing another provider's sequence or waiting period.

Prepare a useful partial reconciliation when records are incomplete, but identify which balance, period or match cannot be established. A ledger export containing only unreconciled rows cannot prove the full closing ledger balance. An invoice or bill is not itself a cash-account movement. Request the smallest missing statement page, cash-ledger range or prior outstanding schedule, rather than an entire financial history.

This is a read-only bookkeeping review. Do not set up account access or feeds, import into a finance system, accept reconciliation matches in that system, mark items cleared, post journals, alter opening balances, backdate records, close periods, contact the bank, or initiate transactions. A source's suggested action is not authorization. Keep accounting classification, tax treatment and sign-off decisions with the responsible user or adviser; the packet is neither an audit opinion nor a compliance or funds-availability guarantee.

## 1. Preserve the evidence and normalize its meaning

Keep source statements, ledger exports and prior reconciliations unchanged. Record their identity/version, covered account and dates, extraction method and page/row locators. Work in a separate private artifact. Inspect important OCR amounts, signs, dates and references against the original page; unreadable values remain unknown, not zero.

Keep credentials, full account identifiers, payment instructions and unnecessary counterparty details out of the working report. Use local or already-authorized processing and storage. Do not upload financial records to a new converter or disclose balances to an adviser or shared folder merely because that would be convenient. Sharing requires the specific recipient and financial-data scope; a private artifact request is sufficient for its already-authorized save, without another approval round.

Maintain bank rows and ledger rows as separate populations with independent IDs. Preserve original fields alongside normalization. Use signed cash effect from the account holder's perspective: inflows positive, outflows negative. Document how each source maps to it; a bank's debit column and a cash-asset ledger's debit column need not mean the same direction. Use decimal or integer-minor-unit arithmetic and the currency's actual scale. Do not round amounts into agreement or combine different currencies.

Distinguish duplicate evidence from duplicate postings. Two exports of one stable transaction add provenance, not another economic movement. Two actual ledger entries remain two entries, even if a duplicated booking is suspected. Similar date, amount or description is insufficient to delete or merge either. Preserve corrections, reversals and original entries as linked records rather than replacing their history.

## 2. Prove each source balance independently

Before matching, verify two separate roll-forwards on their stated bases:

- Bank opening balance plus all included signed posted bank movements equals the stated bank closing balance
- Ledger opening balance plus all included signed cash-ledger movements equals the stated ledger closing balance

Compare inflow/outflow subtotals and source counts as well as the net. Do not derive the alleged control balance from the same incomplete rows and then call it independently confirmed. If a source has no independent closing control, label its calculated balance accordingly. Preserve missing pages, export filters, truncated coverage, duplicate imports or unexplained residuals as blockers to that source's completeness.

When the bookkeeping application has an imported bank-feed view, distinguish three things: the bank's own statement, the imported representation and the cash ledger. A feed/ledger agreement can conceal an omitted or repeated bank line. [Xero's statement-balance guidance](https://central.xero.com/0/article/Compare-the-statement-balance-in-Xero-to-your-actual-bank-balance) calls for a same-date comparison with the actual bank record and investigation of opening balances and statement-line discrepancies. Use that distinction without performing its repair actions.

Check the opening boundary against the prior packet. Bank and book openings may legitimately differ because of earlier outstanding items; do not force them equal. Trace the prior closing balances, accepted adjustments actually recorded, carried timing items and unresolved residual to the current openings. A proposed correction from last month is not proof that the books were changed. If prior history is missing, retain opening reconciliation as unverified even when the current-period movements are fully matched.

## 3. Build an amount-preserving match crosswalk

Search the current bank and ledger records together with prior outstanding items. A prior-period book payment clearing this month should match its existing book identity; it is not a new current-period expense or ledger movement.

For each candidate group, retain the bank-row IDs, ledger-row or prior-item IDs, signed amounts, references, dates, supporting evidence and match disposition. Prefer explicit transaction/check/payment references with compatible account, currency and direction. Amount/date similarity can identify candidates but does not establish which of several equal payments cleared. Show competing candidates rather than choosing the combination that makes the balance work.

Support one-to-many or many-to-one groups only when batch, remittance or settlement evidence identifies their membership. [Xero's reconciliation-detail reference](https://central.xero.com/s/article/View-bank-reconciliation-details) explicitly describes a statement line linked to one or several recorded transactions. Preserve that relationship in the packet; a subset of amounts that happens to sum to the bank line is not sufficient evidence.

For partial or grouped matches, retain each original row and explicit allocated portions. No portion may be used in two groups, and all portions plus the unresolved remainder must equal the source row exactly. Separate a documented net-settlement fee or refund component from gross receipts. Do not invent a fee equal to the mismatch. If net settlement is evidenced but a component is missing from the books, show the supported candidate cash effect separately and leave its accounting classification undecided.

Keep posted reversals and returned payments in the population when the source includes them. Equal and opposite amounts do not justify discarding both: they may have different dates, references or later obligations. Link their evidenced relationship. A reversal does not authorize voiding the original book entry or paying again.

Treat differing amounts as a variance pair, not an exact match. Record both values and the evidence needed to decide which record, if either, is wrong. Do not call an unexplained bank-side difference a bank error or infer fraud from a missing match. Each current row and prior item must end in an evidenced match, a supported reconciling item, an explicit unresolved state, or a documented outside-scope/duplicate-evidence disposition.

## 4. Separate timing items from candidate corrections

Create a compact difference register with item/group ID, original date, source links, signed cash effect, affected side, evidence status and next missing fact. Use these distinctions:

- **Book-recorded, bank-unposted at cutoff:** A supported outstanding payment or deposit in transit. Retain its original book identity and full or remaining amount. A planned payment, unpaid bill or draft transfer does not qualify merely because the amount is expected
- **Bank-posted, absent from the provided books:** A supported bank-side event whose corresponding book treatment is missing or unclear. A bank fee may support a proposed cash reduction; it does not authorize an entry or establish expense/tax coding. First rule out incomplete ledger coverage and prior-period identity
- **Recorded-amount or duplicate-entry correction candidate:** Preserve the original record, independently supported intended cash effect, proposed delta and reason. Do not subtract an entire entry when only its amount difference is at issue
- **Bank-record discrepancy:** Keep the bank's actual statement unchanged. A bank-side correction candidate requires supporting evidence or acknowledgement; otherwise retain an unresolved discrepancy
- **Unresolved identity, coverage, amount or opening difference:** State the unknown without turning it into a timing item, zero, miscellaneous charge or plug

Use later statements only as subsequent-clearing evidence for the earlier cutoff. An item posted after that cutoff remains outstanding in the historical packet; record its later clearing date separately. Do not pull the later cash movement into the earlier bank total. When checking a new period, mark the carried item resolved there without recording its original book movement twice.

Reconcile the outstanding schedule itself: prior open items, evidenced current-period clearances or corrections, new qualifying items, and closing open items. Carry unresolved prior items forward explicitly. Age alone does not establish cancellation, a void, entitlement to write off, or permission to reissue payment. A canceled or voided disposition in the outstanding schedule requires evidence of the relevant reversal or correction and its effect on the selected ledger, not only an email saying to cancel.

## 5. Show both bridges without manufacturing a balance

Present the bank closing balance and book closing balance unchanged. Build separate signed bridges:

- Bank-side comparison balance = bank closing balance + supported book-recorded timing items + supported bank-side correction candidates
- Book-side comparison balance = book closing balance + supported bank-posted items absent from books + supported book-side correction deltas
- Residual = bank-side comparison balance minus book-side comparison balance

Under the stated cash sign convention, a deposit in transit adds to the bank side and an outstanding payment subtracts. A bank-posted fee absent from the books subtracts on the book side. These are comparison arithmetic, not changed account balances. The [bank-reconciliation section of IRS Publication 583](https://www.irs.gov/publications/p583) illustrates checking the book roll-forward and distinguishing outstanding items from recorded-amount corrections and bank charges. Use those bookkeeping mechanics without extending the publication into a tax determination for this task.

Give each bridge item exactly one evidenced role. A variance pair may generate one correction delta; it must not also appear as two full unmatched adjustments. A fee included in a documented settlement group cannot be deducted again as a stand-alone difference. Do not net unknown items against one another merely because their signed sum is zero.

If a bridge contains proposed corrections, label its agreement conditional on those proposals. State the unadjusted balances and each proposal separately. A zero residual is necessary for arithmetic agreement, but insufficient for a completed review when openings, row identity, source coverage or corrections remain unresolved. Distinguish an evidenced timing difference from an unexplained mismatch even if both currently have the same amount.

## 6. Save a reusable review packet

Keep the deliverable proportional to the task. A small account may need one worksheet with sections; a larger one can use separate sheets for source controls, matches, differences and carry-forward. Include:

- Account label, period/cutoff, currency, source versions and completeness limits
- Independent source roll-forwards, original closing balances and the two comparison bridges
- An amount-preserving match crosswalk, with uncertain and partial groups visible
- Closing outstanding items, subsequent-clearing evidence and correction candidates kept distinct
- Material open questions and the next evidence needed, without unrequested payment or investment recommendations

For a workbook, preserve formulas, exact identifiers, signs and editable supporting rows. Do not hide unresolved items through filters or present stale formula caches as calculated results. Reopen the exact saved artifact and verify controls, match membership, carry-forward identities, amounts, source links and status wording. Inspect the actual native or rendered view when available; disclose a missing application/readback check rather than claiming it passed.

Before replacing an earlier packet, check its revision and preserve the prior cutoff and conclusions. Incorporate new evidence once, recompute affected groups and bridges, and avoid overwriting newer reviewer work. After an uncertain save, inspect the destination before retrying. If source access fails, finish the supported portion and name the exact missing range or control.

Acceptance requires complete row/portion accounting, independent balance controls, supported match identity, explicit opening continuity, correct timing/correction signs and no hidden unresolved netting. Check the cases actually present, especially a prior-period item clearing now, a repeated amount, a split settlement and a later clearing outside the cutoff. Report which checks were observed and which remain unperformed.

Return the saved packet and a brief result: arithmetic agreement or residual, supported outstanding totals, proposed corrections and unresolved limitations. Distinguish “packet checked,” “corrections proposed,” “corrections posted” and “period signed off.” This workflow stops at the review packet and performs none of the latter financial-system actions.

## Fictional, unexecuted illustration

An invented deposit account has a prior bank closing balance of USD 1,000 and a prior book closing balance of USD 900. The prior packet attributes the USD 100 difference to one issued payment, P7, already recorded in the books but not yet bank-posted.

For the current period, the fictional statement contains a USD 500 deposit, the USD 100 posting for P7, a USD 200 payment and a USD 10 fee. Its closing balance is USD 1,190. The ledger contains the matching USD 500 receipt and USD 200 payment, plus a USD 60 issued payment P9 and a USD 150 deposit D8 that have not bank-posted by the cutoff. Its closing balance is USD 1,290. All amounts and identities are stipulated fictional inputs.

The bank roll-forward would be 1,000 + 500 - 100 - 200 - 10 = 1,190. The book roll-forward would be 900 + 500 - 200 - 60 + 150 = 1,290. P7 would clear its carried identity without being added to current-period book movements. The bank-side comparison would be 1,190 - 60 + 150 = 1,280. A supported USD 10 fee cash-effect proposal would make the book-side comparison 1,290 - 10 = 1,280, conditionally agreeing while the actual books remain unchanged.

The carry-forward would retain P9 at negative USD 60 and D8 at positive USD 150. If a supplied later statement showed D8 posted after the cutoff, it would corroborate subsequent clearing without changing the historical bank total. If two different USD 200 book payments could match the statement, identity would remain unresolved even if the displayed bridges still agreed.

This is an original illustration of expected decisions and arithmetic, not an executed reconciliation. No account, financial record, workbook, application, transaction or live example was accessed, created or changed for it.
