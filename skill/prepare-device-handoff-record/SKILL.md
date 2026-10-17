---
name: prepare-device-handoff-record
description: Build a password-free handoff packet for selected computers or personal devices, reconciling device identity, accessories, observed condition and evidence of data/account preparation. Use for a practical transfer record, not device erasure, account release, hardware diagnosis or proof of ownership.
---

# Prepare a device handoff without passing secrets

Produce a usable private preparation record and a minimal recipient sheet for the exact device being handed over. The packet separates physical contents from data/account readiness and from actual receipt. A checked box in a planning document is not evidence that a device was erased or released.

This is more specific than a [box inventory](../box-inventory-handoff/SKILL.md): a device can be physically present yet still tied to an account or organization. It does not test a [backup restore](../backup-restore-spot-check/SKILL.md), transfer project files, establish legal ownership or app-license rights, or execute any reset procedure.

## Input and output contract

Identify the selected device or small collection, intended recipient or bounded internal team, purpose of handoff, existing asset IDs, supplied photos/notes, desired date and approved private destination. Use the user's terms for sale, loan, reassignment, return or donation without inventing contract conditions. These labels describe the request; they are not a legal determination.

Use only inputs that affect the transfer:

- Evidenced make, model, asset/serial identifier and identifying marks
- Included and retained accessories, removable media and separately tracked components
- Reported or observed physical condition, with dates and source locators
- User's data-retention decision and available backup/migration evidence references
- Supplied evidence of reset, account association, device-management status and setup state
- Fields authorized for the recipient sheet versus the private working record

Return one Markdown packet or equivalent requested format containing a device manifest, preparation-status matrix, unresolved blockers and a recipient checklist. A printable derivative is optional. Do not search unrelated account inventories or collect credentials to fill blanks.

Never include passwords, PINs, recovery keys, authentication codes, saved sessions, Wi-Fi secrets or password-vault exports. Record `owner action required` rather than a secret field. Do not capture screenshots that expose recovery material; if supplied evidence contains it, omit that material from derived artifacts and retain only a safe locator to the private original. Full serials, names and device associations also need audience-aware minimization; use an approved asset label or masked suffix on the recipient sheet when sufficient.

## 1. Establish which physical device each source describes

Create a stable packet device ID and associate it with observed or supplied identifiers. Keep native asset tags and serial strings exact, including leading zeros. Do not silently correct an OCR character. Compare important identifiers against the source image or supplied record; unresolved `0/O` or `1/I` ambiguity is an identity blocker.

Two devices with the same model are not interchangeable. Match by a reliable identifier plus source context, not a nickname such as “old laptop.” A product box's label identifies the box; it does not prove the device inside has that serial. Keep any mismatch visible before combining evidence.

Give accessories individual IDs only when their identity matters; otherwise use counted pools with units. Preserve whether a charger, cable, dock, adapter, stylus or case is included, retained or unresolved. A connector that fits does not establish the accessory's compatibility or safe rating. Record supplied model/rating evidence without conducting an improvised electrical test.

Do not count a removable storage device both as an included accessory and as media to retain. Track its disposition explicitly. A reported empty memory-card slot is different from a slot that was not inspected.

## 2. Separate three independent status dimensions

Use a compact matrix; add rows only for the actual device and transfer context:

| Dimension | Examples | What supports the status |
| --- | --- | --- |
| Physical package | Device identity, included accessories, visible condition, removable media | Dated source observation or attributed report |
| Data/account preparation | Retention decision, backup evidence, reset result, account association, management release | Specific evidence for that device and step, with scope and time |
| Transfer event | Planned destination, dispatched, received, discrepancy reported | Explicit event report or receipt; not a proposed checklist |

For each relevant preparation row record the requirement/source, responsible person or `owner unknown`, state, evidence locator/date and next action. Useful states are `not assessed`, `planned`, `reported complete`, `observed for this check`, `blocked` and `not applicable with reason`. Keep the evidence description beside the state; do not collapse them into a single unexplained green badge.

Keep `not needed` decisions explicit. If the user says no data needs retaining, record that exact bounded decision instead of inventing a successful backup. If backup is required, a job-success notification is not a restore check. Link existing verification evidence when available; otherwise leave recoverability unverified.

Do not infer account release, management removal or erasure from a setup/welcome screen alone. Record the screen as the observed state and leave separate requirements unresolved unless the relevant official process and evidence support them. A powered-off device supplies no evidence about its storage or account state.

## 3. Select preparation references for the exact platform

Use current official guidance for the identified device, operating-system version and transfer purpose. Link the applicable procedure rather than writing one generic reset recipe for all equipment. Establish which steps apply before assigning them in the checklist.

For example, [Apple's Mac handoff guidance](https://support.apple.com/en-us/102773) distinguishes models that support Erase All Content and Settings from other paths and warns that reset removes data. [Microsoft's Windows handoff guidance](https://support.microsoft.com/en-us/accounts-billing/security/before-you-recycle-sell-or-gift-your-xbox-or-windows-pc) treats backup, reset and account-device removal as separate steps. These references justify separate evidence rows; they do not establish that any step happened on the selected device.

For a managed work device, record the organization's supplied release procedure and responsible team. User possession is not proof of authority to remove management or reassign equipment. Do not bypass enrollment, activation locks, firmware locks or security controls. If the procedure is unavailable, finish the inventory and identify the specific owner decision.

Treat license transfer, service-plan transfer and sale/payment terms as unresolved or outside scope unless separately supplied. Do not label a paid app or warranty transferable merely because it appears installed or registered. This packet makes no legal or financial recommendation.

## 4. Build two views from one reconciled revision

The private preparation record may include exact approved identifiers, evidence references, unresolved associations and the user's retention decision. Avoid copying underlying personal files or screenshots into it when a narrow evidence reference suffices.

The recipient sheet should contain only what that recipient needs:

```text
Packet revision and device ID
Approved identifying details
Included items with counts; expressly retained items when useful
Condition observations with dates and reported/observed attribution
Preparation status supported by evidence; unresolved restrictions
Setup instructions or official reference appropriate to the handoff
Blank received/date/discrepancy fields, or later sourced actual receipt
```

Do not expose the former user's account email, personal file locations, backup paths, recovery contacts or full evidence screenshots by default. A signed URL to a private record is not a suitable replacement for its contents. Share neither view until that audience and data are authorized; preparing a sheet is not sending it.

Leave receipt fields blank unless a real receipt event exists. Do not invent a signature, recipient acceptance or “factory reset complete” statement. If the recipient would need a password to use the device, mark the preparation blocked rather than solving it by placing the password in the packet.

Keep a plan's handoff date separate from dispatch and receipt dates. Later receipt of the package does not confirm that its contents, account release or condition were checked.

## 5. Reopen, verify and update without rewriting history

Check the saved packet against the source record:

1. Device IDs and approved identifier fragments refer to the same physical unit in every view
2. Included, retained and unresolved accessory quantities reconcile without double counting
3. Condition claims remain attributed; photos establish only what is visible
4. Every completion claim has device-specific evidence, and missing/stale evidence remains visible
5. Backup, erasure, account association, management release and receipt stay separate
6. Recipient fields contain no secrets or unnecessary account/personal data
7. The output revision is clear and originals remain unchanged

When new evidence arrives, attach it to the affected device/step and date, retaining the earlier state as history. A later login, restore, re-enrollment or use after reset can invalidate earlier readiness evidence; do not retain an unconditional completed badge. An updated packet should identify exactly which claim changed.

Save in a new file or update only the authorized existing record after checking its current revision. Preserve intervening edits. For an uncertain save, inspect the destination before retrying. If readback is unavailable, label the saved result unverified and return the reviewable draft.

## Failures and stopping condition

- **Identity conflict:** hold the affected device's readiness conclusion; ask for the specific label or record needed
- **Dead or inaccessible device:** record unavailable checks; do not infer erasure, safety or recoverability
- **Management/account-release evidence missing:** retain the blocker and official next owner step; do not collect a password or bypass a lock
- **Physical hazard reported or visible:** stop handling/testing recommendations and direct the user to the manufacturer's appropriate safety/support route; document existing evidence only
- **Recipient asks for additional sensitive information:** obtain the required authorization rather than expanding the sheet automatically

Finish when the requested packet is accurate and usable, even if it records unresolved preparation. Call it `packet prepared` rather than `device ready` unless the defined preparation criteria are evidenced; actual transfer still needs its own event evidence. Resetting, deleting data, signing out, releasing accounts, changing management, shipping and contacting recipients are separate actions with their own permissions.

## Fictional example, not executed

A fictional studio is passing laptop D07 and one charger to a teammate. An inventory lists two chargers, but a later scoped note says one remains at the desk. A photo shows a setup screen, while no account-release evidence is supplied.

The proposed sheet includes D07 and one charger, with the other marked retained in the private record. It describes the setup screen as a dated observation and leaves account release unresolved. Receipt fields remain blank. It does not claim a verified wipe, transferable software license or completed delivery.

No device, account, credential, reset flow or transfer was accessed or performed for this authored illustration.
