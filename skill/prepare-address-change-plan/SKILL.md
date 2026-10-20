---
name: prepare-address-change-plan
description: "Prepare a move-related address-change handoff across selected providers, separating mailing, billing, delivery and service-location fields, effective dates and evidence of completion. Use for a bounded transition plan, not automatic account updates or legal-residency advice."
---

# Plan an address change without changing the wrong location

Deliver a concise, source-backed list of address records that need attention, the exact purpose of each change, when it should apply and how completion can be checked. An address is not one global setting. A move date alone does not determine when every account, shipment or property record should change.

Use [box-inventory-handoff](../box-inventory-handoff/SKILL.md) for physical packing records, [reconcile-address-book-contacts](../reconcile-address-book-contacts/SKILL.md) for other people's contact cards and [source-backed-form-fill](../source-backed-form-fill/SKILL.md) for a separately requested form draft. This workflow prepares the user's cross-provider transition plan. It does not submit changes, redirect mail or transfer services.

## Establish the actual transition

Read the user's move details and the selected provider records or authorized relevant sources. Identify who is moving, the old and new locations, whether the arrangement is temporary or permanent, and the relevant dates: access to the new location, departure from the old one, any overlap and the intended mailing transition. Keep uncertain dates conditional.

Preserve apartment/unit, building and country components exactly from supported facts. A normalized spelling is not proof that an address is deliverable or that the user occupies it. Do not infer a missing unit number, replace an address with a map pin or send it to an external validator without authority for that disclosure.

Separate a household member's move from a whole-household move. A shared surname or account does not establish that everyone is leaving, and a provider may distinguish account holder, recipient and service user. Do not request unrelated family information to make a comprehensive-looking checklist.

Keep the plan private by default. Use neutral account and address labels where full values are unnecessary; retain the exact authorized values in the smallest private reference needed. Exclude passwords, identity-document numbers, full financial account identifiers and access-bearing confirmation links. An address-change checklist should not become a dossier of every account the user owns.

## Inventory the relevant records by purpose

Build from the selected evidence, not an assumed list of accounts. Common categories can prompt a gap question, but mark them as possible until the user or source establishes that they apply. A recent bill can identify a sender; it does not prove that its displayed address is the only editable field.

For each applicable provider, distinguish as needed:

- Mailing or correspondence address
- Payment billing address
- Default address for future deliveries
- Address on an existing order or recurring delivery
- Physical service, installation or insured-property location
- Employer or agency address records with their own declared purpose

Do not copy the new home address into every field. A correspondence address for a retained property can change while the property's location does not. An existing order may retain its own destination after a profile change. Record what the actual provider says rather than assuming that fields synchronize or remain independent.

A small plan can be one table: provider/account label, field purpose, current evidence, intended address label, effective date, official route, next action and status. Add separate rows only where a different purpose, date, person or confirmation requirement changes the task.

## Verify the route and timing

Use current official provider instructions for the relevant country, account type and kind of move. Find the route through the known official site or existing account, not a sponsored address-change intermediary or an unexpected email link. Record the applicable page and retrieval date; do not copy session URLs into the plan.

Keep postal forwarding separate from updating senders. [USPS explains](https://www.usps.com/manage/forward.htm) that its change-of-address order changes the postal mailing arrangement and that the mover is responsible for notifying other senders. Forwarding also has exceptions. A forwarding confirmation is therefore not evidence that a bank, employer, merchant or government record has changed. For U.S. planning, [USAGov lists separate agency routes](https://www.usa.gov/change-address); that list is a starting point, not proof that every listed service applies to this person.

Do not transplant one jurisdiction's deadlines or forwarding rules to another. For a relevant deadline, retain the exact trigger, duration, jurisdiction and official source. Distinguish a mandatory deadline, provider processing estimate and user's preferred completion date. If applicability depends on legal residence, immigration, tax, insurance or another consequential status that is not established, identify the question and appropriate official route rather than deciding the status from the move date.

Check whether the provider supports a future effective date. If only an immediate change is available, do not describe a saved draft as scheduled or silently advance the user's transition. Record when the user should return to that step. A planned reminder is not a reminder already created.

## Expose dependencies and choices

Order work by real consequences and supported dependencies, not by a universal checklist. Examples include a pending delivery that may arrive before new-location access, a verification item sent to an old address, or a service transfer that would stop an existing connection. Read the provider's actual behavior before asserting any of those effects.

Keep an address-field correction separate from a service transfer, cancellation, new contract, payment-method change or account closure. If the available route bundles them, show the additional consequence and leave that action pending the necessary decision and authority. Do not treat a changed price, coverage area or service availability as an incidental address edit.

For each blocker, give the smallest useful next step: confirm one address component, select the intended effective date, check an existing order's destination, or review a provider's required verification. Continue preparing independent rows. Do not require all accounts to be accessible before returning a useful partial plan.

## Track progress at the field's actual scope

Use distinguishable states such as needs decision, ready for user action, submitted, accepted for a future date, current value verified and unresolved. Record the supporting evidence and its date. A page opened, form filled or button clicked does not establish completion. A generic success message may confirm a request without showing which field changed.

When the user supplies a completion report, preserve it as reported unless available evidence verifies the relevant provider, field, value and effective date. Confirmation of one mailing address must not close a delivery-address row or another person's account. Likewise, a current profile readback does not establish that an already-dispatched item was rerouted.

On a changed move plan, identify only the affected rows, compare their prior intended dates with current evidence and distinguish edits still possible from changes already effective. Do not cancel or reverse anything automatically. If an earlier action has an uncertain outcome, inspect its supported status before proposing a duplicate submission.

## Deliver and check the handoff

Lead with the few decisions or near-term consequences that matter, then provide the ready-to-use provider list and official routes. Keep exact address details out of a shared copy unless that recipient and disclosure are authorized. The plan should remain usable without exposing private account information to a moving company or helper.

Reopen the saved result and check that:

- Every evidenced in-scope provider and materially distinct address purpose is accounted for
- Address components and person/account identities match the source
- Different effective dates, retained property locations and existing-order exceptions remain visible
- Postal forwarding has not been counted as completion of other records
- Each completion claim has evidence at the same field and date scope
- Unknown applicability, inaccessible records and additional commitments are not hidden by a blanket “done” status

Preserve concurrent user edits and inspect the destination after an uncertain save before retrying. Return the completed planning artifact even if some live records cannot be inspected, with those coverage limits explicit.

Preparation ends here. A later request to apply changes must identify the intended data and destinations and follow each action's approval, identity-verification and handoff requirements. Do not submit forms, pay verification fees, alter service, contact providers or create monitoring merely to complete this plan.

## Fictional, unexecuted illustration

A fictional user gains access to New Home on June 12 and leaves Old Home on June 15. They retain a separate workshop. Selected records show a retailer's saved delivery address, an order expected June 10, and the workshop utility's service-location and correspondence fields.

The plan treats the June 10 order separately from the retailer's future default. The desired default-change date remains a user choice; no parcel is assumed rerouted. The workshop location stays unchanged while its correspondence-address row can target New Home on the user's chosen date. A postal-forwarding request reported as submitted remains a separate row and closes none of these provider updates.

These are invented planning inputs, not completed account changes, verified delivery behavior or measured skill effectiveness.
