---
name: reconcile-address-book-contacts
description: "Review duplicate or conflicting address-book records, produce a field-preserving consolidation plan, and apply specifically authorized contact edits with source-identity and recovery checks. Use for contact cleanup, not finding people, enriching profiles or migrating an entire account."
---

# Reconcile an address book without combining the wrong people

Deliver a reviewable contact-consolidation result: supported duplicate groups, distinct or unresolved records, exact field choices and, when requested, verified changes in the named address book. Reducing the visible card count is not evidence that the right records were merged or all useful details survived.

[Create a contact card](../create-contact-card/SKILL.md) handles a small portable business-card artifact. [Spreadsheet cleanup](../spreadsheet-cleanup-reconciliation/SKILL.md) handles tabular normalization. This workflow resolves address-book source records and their contact-specific preservation requirements; it does not discover identities through public people searches or contact anyone to test their details.

## Establish the requested boundary

Identify the selected account/address book or supplied export, record population, symptom, destination and allowed actions. Distinguish a duplicate review, a proposed cleaned copy, a specifically requested live merge, and a cross-account transfer. “Find duplicates” permits review, not deletion or importing. A vague cleanup request is enough to prepare a plan, but not to choose which conflicting person or field should survive.

Inspect the available source before asking questions. Obtain only consequential missing choices: which account owns the editable records, whether a named pair represents the same person, or which conflicting detail should be preferred. Keep independent groups moving while uncertain groups remain unchanged.

Use only task-relevant names and contact fields. Do not retrieve biographies, private notes, birthdays, photographs, family relationships or message history merely because an API can return them. When such fields exist, preserve them through a supported native operation without unnecessarily reproducing them in the report; if preservation cannot be established without additional access, identify that limit. Do not upload an address book to an online deduplication service, broaden sync, or copy personal details into a new account without authorization for the data and destination. Never include passwords, tokens or authentication links in a cleanup artifact.

## 1. Inventory underlying records, not just displayed cards

Record source account, stable record ID, revision or retrieval time, source type and editability. For a file, retain its original bytes and record identity within that file. Keep a private source-to-disposition map; the user-facing summary usually needs only enough identity detail to distinguish the records.

A displayed person may combine an editable contact, an organization-directory entry and another account's card. Expand those relationships when the interface supports it. Do not mistake a directory projection or a linked display card for a disposable duplicate. Record inaccessible source layers and incomplete pagination as unknown coverage.

Check current provider behavior before selecting a merge route. [Apple distinguishes merging cards from linking cards across accounts](https://support.apple.com/guide/contacts/merge-contact-cards-adrbk1456/mac); [Google does not merge contacts saved in different Google Accounts](https://support.google.com/contacts/answer/7078226?co=GENIE.Platform%3DDesktop&hl=en). Do not move records to a different account just to make a merge button available.

For each editable record, establish which relevant fields the actual interface preserves: repeated emails and phones, labels, preferred values, name components, organization, notes, photographs, custom fields and group membership. A CSV export that omits some of these is not a complete rollback copy. Prefer a supported recoverable native route; otherwise finish the review and hold the destructive step.

## 2. Separate candidate resemblance from identity

Build candidate groups from the bounded source using useful comparison keys while retaining every original value. Preserve Unicode spelling, phone extensions and labels. Do not infer a country code, strip email plus-tags or dots, or treat every email local part as case-insensitive. Comparison-only normalization must not overwrite stored contact values.

Evaluate candidates together, with supporting anchors and contradictions:

- The user's explicit identification or a documented duplicate import can establish a same-person relationship for the specified records
- Matching names, a shared company, a household phone or a role mailbox can suggest a candidate but cannot establish one person
- Even an exact email or phone needs context when it could be shared, reassigned or stale; a provider's suggestion is evidence to review, not an instruction to accept every suggestion
- Different email addresses can belong to one person, and different people can share a display name; neither observation settles the group alone
- A–B and B–C resemblance does not justify merging A, B and C. Check the whole proposed group for incompatible identity evidence

Use dispositions such as supported same person, retain separately, and unresolved. State the decisive evidence or smallest resolving question. Do not assign unsupported percentage confidence or infer that an old job, old number or infrequent contact makes a record disposable.

For supplied exports without adequate identity evidence, a candidate worksheet is a complete useful result. Do not claim an exhaustive duplicate search if pages, accounts or source types were unavailable.

## 3. Resolve fields separately from the merge decision

For every supported group, prepare a compact field plan containing the source IDs, proposed destination/survivor, each retained value and label, preferred value if established, conflicts, expected removals and recovery route. Preserve all distinct supported details unless the user approved their removal. Being the same person does not decide which address is current or which phone should be primary.

Keep these cases explicit:

- Two differently labeled equal values may carry useful context. Do not erase their labels merely to achieve one row
- Conflicting names, birthdays, photographs, notes or singleton fields need a supported precedence rule or a user decision. “Newest record” and “most complete card” are not blanket authority
- An empty field in one record does not erase another record's value. A deliberate source correction or deletion is different from a missing export field
- Read-only profile or directory fields may display beside a contact but cannot necessarily be stored or edited as that contact's own data
- Group membership and source IDs may change during native merging. Record their supported mapping; do not promise downstream favorites, shortcuts or application references will follow automatically

Do not concatenate unrelated notes or store disputed personal facts in an arbitrary field as a lossless workaround. When the target cannot represent the required result, retain the separate records and explain the exact unsupported field. For a cleaned-file request, make a new candidate and identify import limitations; file creation does not update the live address book.

## 4. Apply only the reviewed, authorized scope

An explicit instruction to merge identified records with established preservation rules can cover the ordinary merge; do not add redundant approval. Ask when the actual operation would discard unresolved content, cross accounts, change sync, remove unrelated records or otherwise exceed that instruction. Permanently deleting unrecoverable records requires the applicable action-time confirmation; never empty Trash as cleanup housekeeping.

Before writing, re-read the exact records and compare revisions and field values with the plan. Rebase unaffected field changes only when their meaning is still clear; hold new conflicts. Use the provider's supported merge or narrow edit operation. Do not replace a whole contact from a partial read or accept “merge all” for a subset task.

When a provider replaces complete field lists, include all intended retained list members. For example, [Google People API updates replace specified fields and reject stale source etags](https://developers.google.com/people/api/rest/v1/people/updateContact). A one-email patch must not accidentally erase a second email. Sequence dependent edits and retain each confirmed revision.

For a non-atomic consolidation, verify that the intended survivor contains all approved fields before any separately authorized retirement of source records. Do not label a copy-plus-delete procedure as a native merge. Keep a per-operation result so an interruption does not trigger the whole batch again.

## 5. Read back preservation and recover narrowly

Fetch the saved records from the owning service or reopen the actual output file. Compare decoded values and labels, preferred fields, supported group memberships and identity mapping against the plan. Verify that distinct and unresolved records are unchanged. A success toast or a lower card count is insufficient.

Account for every in-scope source record exactly once as unchanged, updated, absorbed into a verified survivor, separately authorized retired, or unresolved. Keep source records, displayed cards and proposed people as different counting units. Reconcile output identities without inventing new people to balance a count.

If an operation times out, inspect the group and survivor state before retrying. If partial fields were saved, use current evidence to complete only authorized missing work or report the unresolved state. Do not reimport the entire export as a recovery test.

If a merge loses information, stop that batch and prefer a targeted supported undo or restoration after checking its effects. A global restore can remove newer unrelated contacts: [Google's Undo changes is account-wide over the selected time interval](https://support.google.com/contacts/answer/7280886?co=GENIE.Platform%3DDesktop&hl=en-CA). Obtain authority for that broader consequence rather than treating it as an incidental retry. Preserve current work before an approved recovery; recheck the restored records afterward.

## Deliverable and acceptance

Return the private review artifact or verified destination, source cutoff and coverage, group decisions, field-preservation plan, actual changes, unresolved questions and recovery limits. A small review can be one table; a substantial batch needs a reusable worksheet or equivalent saved record.

Completion requires that every promised source record is accounted for, every applied merge has supported identity and field choices, unchanged records remain outside the mutation scope, and saved readback supports the preservation claim. Distinguish review completed, candidate saved, live changes verified, and device synchronization untested. One service's readback does not prove every connected device has refreshed.

## Fictional illustration, not executed

In a fictional account, records C11 and C24 are both “Sam Chen.” The user explicitly confirms they are the same colleague. C11 has a work email and a labeled mobile number; C24 has a different personal email and a project group. C31 is a different Sam Chen with a shared office phone. The request authorizes merging C11 and C24 in that account while preserving all fields, with no changes to C31.

The plan retains both distinct emails, the labeled mobile number and the project group, provided the native merge supports them. It maps both source IDs to the observed survivor rather than assuming C11 survives. C31 remains separate despite the name match. If the interface cannot preserve the project group, the merge stays held pending a supported route or an explicit revised choice.

For these three input records, a fully verified native merge would account for one survivor, one absorbed source and one unchanged record. This is an unexecuted example of the decision and accounting rules, not evidence of an actual contact read, merge, saved worksheet or successful undo.
