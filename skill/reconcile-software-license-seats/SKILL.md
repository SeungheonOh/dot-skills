---
name: reconcile-software-license-seats
description: "Reconcile a bounded software subscription's purchased capacity, effective seat consumption and billing population into a source-linked allocation handoff. Use for explaining seat-count discrepancies and preparing cleanup decisions, not usage surveillance, access changes, price comparison or a license-compliance certification."
---

# Reconcile software license seats

Explain why a software subscription's seat numbers differ, what capacity is actually available under the evidenced rules, and which precise decisions would resolve the remaining discrepancies. Deliver a private pool summary, attributable allocation register and small decision queue. Counting accounts, subtracting a directory headcount from an invoice quantity, or sorting people by last login does not answer this task.

[Subscription cost inventory](../subscription-cost-inventory/SKILL.md) handles recurring prices and charge calendars. [Connected-app access review](../review-connected-app-access/SKILL.md) handles grants held by third-party applications. This workflow reconciles the units consumed by a named software product against its purchased or metered entitlement. It does not establish whether anyone is productive, determine legal license compliance, or change access.

## Establish the exact question and evidence boundary

Read the request and available records before asking questions. Identify:

- The provider, tenant or enterprise, billing account, named product/SKU, subscription and relevant seat pool; include reseller or parent-organization boundaries when they affect the records
- Whether the question concerns assignable capacity now, a past invoice's quantity, a renewal proposal, or a specific mismatch between two views
- A fixed snapshot cutoff and timezone for current allocation, plus the exact billing/service period when historical charges are involved
- Authorized entitlement or subscription records, license-use exports, account/assignment metadata, invitation records, applicable billing terms and an existing reconciliation if available
- Source capture times, filters, pagination/completeness, report effective dates and known processing delays
- The requested private destination, intended reviewers and any user-stated reserve or proposed additions that matter to capacity planning

Prefer the provider's existing license report or a small supplied export over collecting every employee's activity. A billing summary alone supports a capacity/charge record, not an account-level allocation inventory. A directory alone supports observed accounts, not which product each account consumes. Continue the supported parts and name the smallest missing report or fact.

Use only already-authorized read access. Do not create an administrative grant, change roles, generate credentials, install an audit agent or trigger license reprocessing to obtain a cleaner report. If the necessary page or report is inaccessible, use a supplied export or return a bounded coverage gap. A denied read is not permission to try another identity or interface.

This is a preparation workflow. Do not buy or reduce seats, cancel a subscription, accept renewal terms, revoke licenses, suspend or delete accounts, alter group membership, resend invitations, remove app grants, transfer owned data, contact a vendor or notify users. An assignment recommendation is not authority to execute it. Later actions need their own exact target, scope, consequence and applicable confirmation.

## 1. Define what a seat means for this product

Build a short counting contract from the actual subscription records and current official product documentation. Record the document/version, applicable plan and observation date beside each rule. Product marketing names are not stable billing identities, and one vendor's definition must not be applied to another SKU.

Keep these quantities distinct:

1. **Purchased or committed quantity:** the contracted or purchased units for a stated term, including any explicit minimum
2. **Currently usable capacity:** the units the provider currently makes assignable under that pool's status and rules, if a bounded pool exists
3. **Effective consumption:** the unique provider-defined units consuming seats at the snapshot
4. **Requested or pending allocation:** invitations, group assignments or provisioning requests not yet established as effective; their billability requires its own rule
5. **Billing-period population or units:** the users, peaks, days or other measure the applicable billing rule uses for that period
6. **Observed activity:** optional bounded usage evidence, which is neither a seat count nor proof of business need

Identify whether the unit is a user, named account, device, concurrent session, company-wide entitlement or another documented unit. Limit the reconciliation to supported units. Do not force device licenses, concurrent-use pools or consumption credits into a person-per-seat model; a product needing different source data may remain outside this pass.

Record whether separate subscriptions feed a common pool and whether a bundle includes multiple service plans under one product license. Keep base products and add-ons separate unless the provider explicitly defines a shared counting unit. A disabled service inside a suite is not automatically a released suite seat. Do not add service-plan rows to a product-seat total.

Use official examples as reasons to check the rule, not as defaults:

- [Microsoft Graph's subscribed SKU record](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-1.0) distinguishes assigned-license counts, prepaid-unit status, service plans, subscription IDs and SKU identity. Preserve these dimensions rather than treating every number as available seats
- [GitHub's license-consumption reference](https://docs.github.com/en/billing/reference/github-license-users) distinguishes plan and billing modes, roles and invitations. For Enterprise Cloud usage-based billing, a user who consumed a license during the cycle can remain billable for that cycle after removal or suspension; pending invitations do not consume a license under that mode. Confirm the inspected enterprise's mode before applying either rule
- [Google Workspace's billing guidance](https://knowledge.workspace.google.com/admin/billing/understand-google-workspace-bills-and-charges) distinguishes Flexible and Annual/Fixed-Term plans. Suspended users can still be charged, and committed licenses can remain payable until renewal. A smaller active-user list therefore does not by itself establish an overcharge or immediate savings

Actual negotiated or reseller terms may differ from a generic product page. Preserve a conflict and its affected quantity rather than deciding contractual precedence or making a legal interpretation. Do not infer a refund, reduction right, prorating rule or renewal date from a common practice.

## 2. Preserve pool, account and assignment identities

Create one pool record for each distinct counting boundary. Retain the provider's non-secret tenant, subscription and SKU identifiers when necessary, with readable private labels. If one report aggregates several subscriptions, preserve the membership map; do not count both that aggregate and its constituent subscriptions as additional capacity.

Create an allocation record at the product's actual consumption grain. For a per-user product this is often a stable provider account ID plus SKU and pool, but establish the rule rather than assuming it. Keep the underlying source rows and their lineage separate from this effective-unit register.

For each relevant allocation retain only what changes the decision:

- Stable account/device/unit reference, product and pool; necessary display label separately
- Provider role and account status, preserving invited, active, suspended, archived, deleted or unknown exactly as supported
- Direct assignment, source group or other allocation route, with route identity when available
- Effective license state, pending/error state and available error detail
- Relevant effective/capture dates and links or row locators for evidence
- Supported dependency or stated purpose, plus the owner decision still needed

Do not merge accounts solely because names or email addresses match. A renamed identity, alias, contractor account, automation identity and second legitimate account can look similar. Cross-organization or cloud/server deduplication requires the provider's identity linkage and counting rule. An unresolved candidate pair must retain both records and the range or uncertainty it introduces.

Conversely, repeated exports or multiple assignment routes to the same effective unit are not automatically extra consumed seats. Preserve direct and group routes even when the documented counting rule yields one consumption unit; they can matter to a later cleanup decision. Do not assume removing one route would remove the entitlement if another route remains.

[Microsoft's assignment-state reference](https://learn.microsoft.com/en-us/graph/api/resources/licenseassignmentstate?view=graph-rest-1.0) exposes route, disabled-plan, state and error information separately. Its [group-licensing guidance](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-group-licenses) also describes asynchronous failures and processing. Group membership or a requested assignment alone is insufficient evidence of a successfully provisioned entitlement. Keep effective allocation, processing state and product usability distinct; none proves the user can currently complete every task.

## 3. Reconcile like-for-like counts

First map every in-scope source row to an effective unit, a repeated observation, a supported exclusion or a localized unknown. Preserve reasons for exclusions. A filtered report that omits suspended accounts or guests cannot establish a full tenant total. Report unread pages and inaccessible organizations explicitly.

Compute the reconstructed effective count using the documented unit and deduplication rule. Compare it with the provider's reported consumption only when product, pool, cutoff and counting definition are comparable. Show the signed difference and its source versions. Do not insert an anonymous adjustment to force the totals to agree.

Useful explanations include a different SKU, aggregated subscriptions, duplicate route rows, omitted roles, an invitation rule, failed provisioning, delayed reporting or different capture times. Each explanation needs evidence. A plausible reason is a candidate investigation, not a reconciled difference. If current source views change while being read, preserve both observations and obtain a compatible snapshot if available rather than combining them into a fictitious simultaneous state.

For a finite, comparable pool, calculate capacity less effective consumption only after establishing which capacity statuses are usable and which consumption units belong to it. Label the result arithmetic headroom, with any restrictions. Keep requested reservations or approved upcoming additions separate; do not subtract a speculative hire as though a seat were already consumed. A negative difference is a discrepancy or supported over-allocation, not a value to clamp to zero. If the product is metered without a fixed pool, state that a spare-seat calculation does not apply.

Reconcile a historical bill on its own time basis. Today's allocation is not a reconstruction of last month's bill. Obtain the necessary history or period report and apply the documented union-of-users, daily, peak, minimum-commitment or other actual rule. Account for effective changes and invitation/role transitions only where evidenced. Do not sum daily active counts when billing counts unique users, or use an average when billing uses a peak.

Keep quantity reconciliation separate from monetary reconciliation. Taxes, discounts, credits, price changes and proration can make the amount unsuitable as a way to infer seats. If the user also requests a cost scenario, use only supported price and effective-date terms, label it hypothetical and separate current-period liability from future reducible commitment. Freed assignment capacity is not achieved savings; a prepared reduction is not a saved billing change.

## 4. Turn discrepancies into specific decisions

Give each observed allocation a primary review state such as explained/retain for stated need, assignment failure to investigate, identity/counting unresolved, or candidate for owner review. Keep separate diagnostic tags where needed; do not add overlapping categories and call that sum a seat total.

Make the queue concrete. Each row should identify the exact pool and unit, supporting evidence, proposed next decision, known dependency, possible service/data consequence and missing fact. Examples include confirming two identities, locating the missing subscription report, reviewing an unused reserved allocation, or deciding whether an invitation is still wanted. Do not label a person unnecessary or recommend dismissal based on product telemetry.

Treat last-use information cautiously if the user supplied it for this review. Record what the timestamp measures and its covered period. No recent interactive login can coexist with a needed service account, background integration, infrequent role or planned return. Missing telemetry is unknown, not zero use. A usage threshold may select candidates for review, but it must not make the final access or staffing decision. Do not collect message contents, browsing history, keystrokes or unrelated personal information.

Before describing a seat as reclaimable, distinguish these separate questions:

- Is the present consumption itself established?
- Has the user or responsible owner established that the allocation is no longer needed?
- Do ownership, retention, dependency or alternative-assignment conditions still need resolution?
- Would the proposed change release current capacity, reduce a later bill, both or neither under the applicable terms?
- Would an automatic group or provisioning rule recreate the assignment?

If any answer is unknown, keep that limitation in the action row. A report can identify a decision without authorizing it. Do not invent an owner response, treat silence as approval or contact the owner as an incidental part of a read-only reconciliation.

## Deliverable, acceptance and recovery

Return one maintainable private document or workbook containing:

- A pool-by-pool summary of the question, cutoff/period, counting rule, reported capacity/consumption, reconstructed counts and explained or unresolved differences
- The effective-unit register with source-row and assignment-route lineage, plus bounded coverage limitations
- The decision queue, separating possible capacity release from any supported future cost scenario

Use pseudonymous labels in a general summary and keep exact identifiers only where the authorized reviewer needs them. Do not publish roster exports, commercial terms or staff usage details. Store imported names, identifiers and text as literal data in a workbook, not formulas or external connections. Preserve original exports; do not modify a provider report to make it agree with the working register.

Before delivery, independently trace the material totals from source rows through effective units to each pool. Check a repeated route, any combined subscription pool, status-dependent consumption, unsupported identities, error/pending assignments and historical/current cutoff differences where present. Confirm that every headline total has an explicit unit and completeness label, unresolved counts were not turned into zero, and no claimed savings depend solely on a lower assignment count.

Reopen the exact saved artifact. Inspect IDs, joins, counts, formulas if used, source links, permissions and private-detail boundaries. State which checks actually occurred; a static report does not demonstrate a successful login, functioning integration, full billing audit or licensing compliance. Finish when the requested comparison is saved and checked, or the remaining discrepancy is held on a specific unavailable fact or decision.

For an incomplete or contradictory report, keep the supported subtotal and affected scope, then request the smallest compatible missing source. For newer evidence, retain the old source/cutoff and revise affected pool, unit and decision records together. Do not append another copy of the same export as new consumption. Recheck the destination revision before replacing an existing report; reconcile concurrent edits. After an uncertain save, inspect the same destination before retrying. Recovery here restores or corrects the reconciliation artifact, never account access or billing settings.

## Fictional, unexecuted illustration

An invented product, HarborDesk Team, has supplied fictional rules: a fixed annual commitment of 12 seats; each distinct account with an effective assignment consumes one seat; multiple routes to the same account consume one seat; suspended accounts retain their assignment; pending invitations do not consume seats; quantity can be reduced only at renewal. These are scenario inputs, not claims about a real vendor.

At the same cutoff, the provider reports 9 consumed and 3 unassigned seats. The assignment export has 11 successful route rows, mapping to 9 distinct accounts: two accounts each have both a direct and group route. One of the 9 accounts is suspended. Two further invitation rows are pending and have no effective assignment. A filtered people view shows only the 8 active assigned accounts.

The handoff would reconcile 11 route rows to 9 effective units, keep the suspended account in consumption, exclude the two invitations under the supplied rule, and explain why the active-only view shows 8. It would report 3 seats of current arithmetic headroom and all 12 committed seats still payable under the fictional terms. It would not report 4 spare seats from the active-only view or 14 consumed seats by adding routes and invitations.

The suspended account's owner decision remains pending. Even if a later approved removal released its seat, the report would separate 4 units of resulting capacity from a potential renewal reduction; it would claim no immediate saving. If the source group could recreate that assignment, the queue would preserve the group dependency rather than recommend removing only the direct route. A different-period invoice would remain unreconciled without that period's applicable evidence.

All names, quantities, rules and records above are invented. No service was accessed, report downloaded, calculation program run, workbook created, account changed, invitation sent, purchase made or billing reduction executed for this illustration. It describes expected handling, not an executed check.
