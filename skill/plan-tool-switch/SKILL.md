---
name: plan-tool-switch
description: "Prepare a reversible transition between already chosen apps or services, mapping the user's real workflows, data and dependencies to a bounded pilot, cutover gates and a change-preserving fallback. Use for a switching plan, not product selection, file conversion, live migration or account closure."
---

# Plan a tool switch without losing the work between tools

Deliver a practical transition packet for moving a defined activity from one chosen tool to another. Cover what must remain usable, where work is authoritative during each phase, what evidence permits a cutover, and what happens to new work if the user must return. A feature checklist or instruction to export and import does not establish a workable transition.

Use [decision-source-brief](../decision-source-brief/SKILL.md) if the destination is still being chosen. Use [account-export-audit](../account-export-audit/SKILL.md) to examine downloaded source exports and [service-import-rehearsal](../service-import-rehearsal/SKILL.md) for a concrete import's row-level behavior. This guide connects those narrower checks to the user's ongoing activity. It prepares decisions and instructions; it does not perform the switch.

## Establish the chosen activity and boundary

Identify the exact source and destination product, workspace/account boundaries, affected people or roles, reason for switching, intended date or trigger, and output destination. Start with the user-selected scope, such as a personal reading collection or one team's review queue. Do not expand a bounded switch into an organization-wide migration.

Inspect the supplied workflow examples, existing inventories, provider documentation, prior export/import results and requirements. Distinguish planned capabilities, documented support and behavior already observed in the user's environment. Verify version- or plan-dependent details against current official sources when needed, keeping URLs and applicable dates. Do not assume two products with the same feature label preserve the same meaning.

Recover must-preserve requirements and acceptable tradeoffs from the user rather than choosing them silently. A missing convenience and loss of required history are different decisions. Ask only about a gap that changes feasibility or the safe transition path. When a product identity or data requirement is unresolved, finish the unaffected inventory and show the dependency.

Keep credentials, password vaults, identity-provider changes and security-critical infrastructure outside this general workflow. Do not copy secrets into a plan. For regulated or safety-critical activities, document the supplied dependency and responsible owner rather than certifying a transition or inventing professional requirements.

## Inventory work that depends on the current tool

Begin with concrete user activities, not every setting. For each important activity, identify its input, ordinary result, users/roles, frequency or trigger, and what would be unacceptable during the switch. Follow the dependencies that make that activity possible:

- Records and their identity, relationships, attachments, current state and required history
- Templates, saved views, tags, formulas or other behavior the user relies on
- Incoming channels, integrations, scheduled jobs, notifications and outbound effects
- Links or references from other documents, bookmarks, shared packets or external collaborators
- Access scope, ownership, collaborators and permissions needed for the actual task
- Offline use, search, export and continued access where required by this user

Distinguish shared ownership from personal access. Being able to read an object does not establish permission to transfer or redistribute it. Record only necessary identifying detail, keeping restricted records and private URLs out of a broadly shared plan. Prefer a minimal dependency description to copying live content.

Assign each in-scope item or class a disposition: transfer, recreate, retain in the source, intentionally omit with a recorded decision, or unresolved. Do not equate “not present in the export” with “unneeded.” Map old-to-new identities where a plan can establish them, and leave generated destination IDs unknown until there is actual evidence. A renamed folder is not evidence that internal links or collaborators survived.

## Define acceptance before designing the cutover

For each essential activity, specify a representative start, action and expected result in the destination, plus the exact evidence needed. Include meaningful exceptions, such as a historical item, an attachment, a shared item, a long-running item or a cross-reference, when they matter to the scope.

Check different properties separately:

- **Content:** required fields, attachments, relationships and history are preserved or explicitly retained elsewhere
- **Behavior:** the user can complete the important activity with the intended roles and configuration
- **Continuity:** new incoming work has a known route, and nothing depends on an unattended source queue
- **Audience:** access is appropriate for each affected role; a link opening for the planner is insufficient
- **Recoverability:** the plan accounts for work created or changed after the initial snapshot

Keep documented support, local artifact inspection, service preview and an actual observed task as different evidence levels. A successful export or equal row count does not prove a working destination. A pilot cannot establish the completeness of the remaining population; identify the later full-scope accounting needed.

Create a loss-and-gap list for unsupported properties. State the effect on the user's activity, available alternative, decision owner if known, and whether it blocks a particular gate. Do not silently flatten history, discard comments, broaden access or accept a workaround that changes a must-preserve requirement.

## Plan a bounded pilot and explicit authority for edits

Choose a small, representative scope that exercises the important risks while preserving ordinary work. Prefer approved synthetic or separately copied material when it can answer the question. A copy may prove format behavior without proving real account permissions or actual integration behavior; retain that limit.

For each phase, record which tool is authoritative for each affected class of work, who may edit it, how new changes are captured and what clears the next gate. A useful default is a single authoritative write location for a given class. If both tools must accept edits, define identity matching, conflict handling, delta capture and reconciliation before proposing coexistence; “sync later” is not a method.

Describe the phases in terms of outcomes rather than mandatory dates:

1. Preparation: required sources and dependencies are identified; unknown contracts remain visible
2. Pilot: selected tasks and preservation properties have recorded results in an isolated scope
3. Reconciliation: the full selected population and changes since the baseline have a supported disposition
4. Cutover decision: the designated authority reviews evidence and chooses the next writable location
5. Stabilization and handback: actual use and incoming-work routing are checked; unresolved issues have a fallback

Adapt this structure to the scale of the switch. A personal app may need one concise checklist. A team switch needs accepted responsibilities and an explicit decision route; naming a person in the packet does not obtain their agreement or capacity.

Capture dependencies such as export availability, importer limits, supported account access and provider retention windows from applicable evidence. Identify known overlapping costs or cancellation deadlines only as planning facts; do not buy, cancel or accept terms. A proposed edit freeze, disabled integration or changed forwarding route is a future gated action, not something a written plan has configured.

## Make rollback preserve new work

Define the fallback separately for a pilot failure and a post-cutover failure. During an isolated pilot, ordinary source work may continue unchanged. After cutover, the destination may hold new or changed records that the old snapshot lacks. Returning to the source must account for those changes before making it authoritative again.

For a material failure, specify:

- The observable trigger and affected activity
- What further work should be paused or redirected, subject to actual authority
- Which source and destination versions or logs must be preserved
- How additions, edits, deletions and external effects since the cutover would be identified
- The supported reconciliation path, unresolved conflicts and who decides which values to keep
- The condition for resuming work, or the precise reason a safe rollback is not established

Do not assume that a reverse import exists, that it is lossless, or that a backup can absorb later changes. Deleting a destination copy does not retract messages already sent from it. If the available evidence cannot establish a change-preserving return route, mark rollback unproven and propose a smaller pilot, deferred cutover or explicit user decision rather than calling the switch reversible.

Preserve original sources, export snapshots and prior plan versions. Keeping access to the source does not establish that it can remain writable, that retention is guaranteed or that every link will continue to work. Account closure, deletion and subscription cancellation remain separate decisions with their own evidence and authority; they are not automatic cleanup at the end of this plan.

## Deliver and verify the transition packet

Return the requested plan with the shortest useful combination of:

- Scope and workflow/dependency map
- Transfer, recreate, retain, omit and unresolved dispositions
- Pilot cases and acceptance evidence required at each gate
- Phase-by-phase write authority, change capture and incoming-work routing
- Cutover conditions, accepted/proposed owners and open decisions
- Fallback steps with their new-work reconciliation limits

Walk the paper plan through an ordinary switch, a pilot failure, a change arriving during transition, and a post-cutover return when those cases apply. A reader should be able to identify the authoritative copy and the next permitted decision at each point. Label this a plan review, not an executed migration.

Check that every essential activity has an acceptance path, every in-scope item class has a disposition, and every irreversible or externally visible step has a real authority boundary. Confirm that a source-only check has not become a destination-readiness claim, and that a stale snapshot cannot silently overwrite newer work.

Save to the authorized destination and read back the actual plan, links, gate status and unresolved decisions. Reconcile concurrent edits before replacing an existing plan; inspect uncertain saves before retrying. Revise affected steps if the product contract, source scope or chosen date changes. If a prerequisite remains unavailable, deliver the independent preparation and exact blocked gate.

Stop when the requested packet is usable and its remaining decisions are explicit. No export, upload, account creation, permission change, integration change, cutover, deletion or cancellation is implied by preparing it. A request to perform any of those actions needs its own applicable scope and authority.

## Fictional, unexecuted illustration

A fictional editorial group has already chosen to replace its review tool. A supplied export preserves article text and attachments but omits comments; the group requires unresolved comments to remain available. The destination's reverse import is undocumented.

The plan pilots one completed article and one with open comments, retains the source as the authoritative review location during that pilot, and lists comment continuity as a cutover gate. It does not label the export complete merely because article counts match. Before a real cutover, the group needs a supported comment disposition and a way to preserve destination changes if it returns.

No files were transferred, accounts accessed or edit routes changed. This invented paper path demonstrates why an attractive destination and a readable export do not establish a reversible switch.
