---
name: maintain-source-linked-flashcards
description: "Update an existing source-linked flashcard collection when its references or content change, reconciling source claims, note fields, generated cards and review-history treatment. Use for a checked content-update packet and authorized scoped edits, not creating a new course, generic flashcard authoring or changing study algorithms."
---

# Update flashcards without changing what their history means

Maintain a selected existing collection against revised references or identified corrections. Deliver the actual proposed content, a source-to-note-to-card change map, and an applicable update artifact or checked native edit. The central decision is whether a revised card still asks the same thing: preserving a database identity can preserve old study history even when the recalled answer has changed.

Use [learning materials](../create-learning-materials/SKILL.md) for a new lesson, [deliberate practice](../deliberate-practice-workbook/SKILL.md) for focused exercises, and [study scheduling](../plan-adaptive-study-schedule/SKILL.md) for time allocation. Use [service import rehearsal](../service-import-rehearsal/SKILL.md) for general field mapping, row accounting and uncertain-import recovery. This guide adds the semantic and generated-card decisions those workflows do not establish.

## Fix the collection, source and editing boundary

Establish the selected deck, notes or source topic; the actual application/client version and collection/profile; the previous and revised references; and the requested destination. Distinguish a review packet, an import-ready update, and permission to change specified live notes. A named deck can contain only some cards of a note whose other cards are elsewhere. Do not assume a deck selection bounds every effect of a note edit.

Gather only what the selected work needs:

- Current note fields with stable note identity, note type and original field order
- Generated cards and their directions/templates or cloze assignments, native card IDs where available, and deck membership
- The review/scheduling state that must survive, through an authorized supported export or inspection; content-only exports may omit it
- The prior source version or last maintained content, revised source version and exact claim locators
- Existing personal annotations, examples, tags, media references and protected fields
- The user's intended treatment of substantive changes, if already stated, and a private noncolliding save location

Keep source identity, native note identity, native card identity and a sidecar tracking key distinct. Never claim that a locally assigned row number is an application ID. If available evidence cannot bind a proposed change to one current note and its affected cards, prepare the content comparison but hold the executable update for that item.

Ask only about a missing decision that changes the work. With no old source or maintained baseline, compare the current card to the new reference and mark the lineage gap. Do not invent what changed or overwrite a learner's addition as though it were generated from the old source. New source material need not become new cards unless expansion is requested.

## Trace source changes to the cards they affect

Read the relevant source passages with enough context to retain conditions, versions, exceptions and units. Separate corrected facts, changed policies, added context, changed terminology and moved locators. A newer edition is not automatically the authority for a card deliberately studying an older version. A missing passage is not proof that its former claim is false or should be deleted.

Build a compact crosswalk, one row per affected retrieval target: old/new source locator, note identity, relevant fields, generated card identity or assignment, current prompt and accepted answer, proposed prompt and answer, reason, history treatment and action status. Link all supporting passages when the card synthesizes more than one claim. Preserve ambiguous or contradictory references as holds rather than choosing whichever makes the update simplest.

Inspect every sibling card generated from a changed field, including reverse cards and cards in other decks. A field shown only as an explanation on one card may be the answer on another. Source references, hints, examples and media can also leak an answer onto the front. Review the actual front/back composition rather than checking field text in isolation.

When a previous maintained version exists, compare three states: that baseline, the learner's current note, and the source-derived proposal. Carry forward unrelated personal notes and supported local corrections. Hold same-field conflicts for a decision; do not let a recent source edit erase the user's mnemonic or silently promote it to a sourced fact. Keep source-derived content and personal commentary distinguishable after merging.

## Decide whether review history still belongs to the revised task

Classify the effect per generated card, not merely per note or changed line:

| Change | Content treatment | Review-history decision |
| --- | --- | --- |
| Locator repair, spelling or layout correction with unchanged cue meaning, accepted answer and recall demand | Narrow update retaining established identity | Preserve existing state within the requested edit; record why the retrieval target is unchanged |
| Corrected answer, new qualifying condition, altered hint or materially different wording | Show the exact old/new target and source evidence | Hold application until the user chooses how to handle prior study state, unless an explicit existing instruction already covers it |
| One target split into several, several merged, or a target replaced | Prepare distinct proposed targets and their lineage | Do not copy one history to several cards, combine histories, or reuse an old identity as evidence of learning a different target |
| Removed or disputed source claim | Retain the previous content and mark the issue in the packet | Propose retirement/review separately; do not delete or suspend cards from source absence alone |
| Same-looking wording but unknown correspondence | Preserve both candidates and explain the ambiguity | Hold identity-dependent updates; a matching title or row position is insufficient |

A user may choose to retain historical records while separately bringing revised cards back for review, create new cards while preserving old ones, or make another supported change. Explain the exact card-level effect before acting. A request to correct content does not automatically authorize resetting progress, altering due dates, changing scheduler presets, suspending or deleting cards. Do not assume a control named “Forget” or “Reset” has the same history effects across products or versions.

Preserved history remains evidence of past attempts under the old wording and conditions. It does not establish that the revised answer is known. [Anki's statistics documentation](https://docs.ankiweb.net/manual/stats) explicitly notes that a card can change after a linked review was recorded. Do not rate cards, manufacture a review attempt, promise a learning gain, or diagnose ability from a history export. A content maintenance packet needs no learner ranking or complete study-history dump.

## Preserve the application's note-to-card contract

Inspect the actual note types and templates within scope. [Anki's note/card model](https://docs.ankiweb.net/manual/getting-started) separates stored fields from generated question/answer cards; recognition and production may be different cards. Other applications need their own documented identity model. Do not impose Anki semantics on an unrelated importer.

For Anki, maintain an explicit correspondence between each existing cloze number and its recall target. [Card generation](https://docs.ankiweb.net/manual/templates/generation) depends on templates and fields; distinct cloze numbers produce distinct cards. Do not renumber surviving clozes to close a gap, reuse a retired number for a different target, or reorder templates as harmless cleanup. Adding a new target needs a supported new-card mapping; a content diff alone cannot establish its scheduling identity.

Two deletions sharing one cloze number are one combined recall task. Splitting that number changes the task even if all words stay present. Likewise, removing a required field or cloze can leave an existing card blank rather than safely retiring it. Treat blank/empty-card findings as decisions, not permission to run collection-wide cleanup.

Keep note-type, template and field-schema changes separate from content edits: [shared templates](https://docs.ankiweb.net/manual/templates/intro) can affect unselected notes. If a requested update requires such a change, enumerate its wider scope and obtain the necessary authorization. Prefer the existing supported representation for an ordinary correction. Do not write directly into the application's database, install an add-on, rewrite internal card identifiers or bypass a protected export.

## Prepare the exact update and preservation record

Use supported native edits for a small selected set or a documented import format when a reusable handoff is requested. Bind the payload to the inspected collection snapshot and note-type schema. Include only unambiguous, permitted changes; retain holds in the readable packet. Separate new-card proposals from existing-note updates and preserve every untouched field that the chosen route would otherwise clear.

A held card also blocks a shared note-field or import operation that would change its content or state. Do not apply a mixed ready/held note as one update. An independent field-only correction may proceed only when the supported route leaves all held content and affected sibling state unchanged; otherwise hold the coupled operation.

For Anki text imports, the [official import contract](https://docs.ankiweb.net/manual/importing/text-files) supports first-field matching within the configured scope or an unchanged GUID exported by Anki. Do not invent GUIDs or replace a meaningful first field with a new ID to force matching. Record the chosen duplicate/update mode and scope. In-place updates preserve scheduling, so importer success does not resolve a substantive history decision. Changing the import deck does not necessarily move existing cards.

Use the documented encoding, separator, quoting, field order and HTML mode. Preserve literal markup, Unicode, multiline content and media references; inspect previewed fields rather than trusting a filename extension. Omitted/blank fields, tags and shared templates need explicit preservation checks. Never place review-status instructions in an ordinary text column and assume the importer will execute them. If the available route cannot preserve identity and unrelated content, return a field-level edit sheet with the exact blocker instead of a purportedly safe import.

For a revised image or audio answer, preserve the original asset and inspect every affected reference. Replacing bytes under a shared media name can change other cards without changing their fields. Prefer a new noncolliding asset identity with scoped references when the application's supported route permits it. Hold unsupported image-occlusion or generated-card mappings rather than guessing which mask owns a review history.

Preserve a supported pre-change snapshot before a live mutation. Confirm what it actually contains. [Anki export options](https://docs.ankiweb.net/manual/exporting) distinguish content, scheduling, media and collection packages; a content-only file is not a complete recovery copy. Do not use a collection-replacement package as a routine incremental update. Keep any backup within the approved private location and scope; a whole-collection copy can include unrelated private material.

## Check the saved packet, then apply only authorized changes

Reopen the saved update file and change map. Verify the exact source versions, field mapping, note identities, generated-card correspondence and unchanged personal content. Account for every selected existing target as unchanged, ready to update, proposed replacement/retirement, or held. Count notes and cards separately. A two-card note is not two independently editable records unless the application actually models it that way.

When an authorized isolated consumer check is available, use the actual supported client in a separate, unsynced profile or copy whose creation is within scope. Do not connect it to the live sync account. Compare rendered fronts and backs, sibling cards, new/blank-card counts, native identities and retained study state against the baseline. Use preview, not rated study sessions, to inspect content. Keep application use unrun if only static preparation was authorized; do not install or enable tools to improve a verification label.

Inspect templates and linked resources before previewing. Active code, remote media, external lookups or add-on dependencies require an understood, authorized execution route; an unsynced profile is not a security sandbox. Do not fetch credential-bearing links or transmit private text merely to render a card. Continue static field and source review when those checks are blocked.

Before a live edit, refresh the affected notes and study state. Reconcile intervening learner edits and new reviews; do not overwrite them with an earlier export. Apply only the approved content changes and separately authorized state changes through the supported interface. Read back exact affected notes and cards afterward. Confirm the intended answers and source references, preserved identities, unaffected siblings and history treatment. An import receipt without this readback is incomplete evidence.

For a timeout or ambiguous result, inspect the exact target before retrying. Preserve confirmed changes and hold unknown items; do not reimport the whole batch hoping duplicates will sort themselves out. If a preview or import generates unexpected cards, changes unrelated notes, or loses fields, stop further application and retain the baseline, submitted bytes and observed result. Correct only the demonstrated issue within scope.

Recovery must preserve work done after the baseline. [Anki's backup guidance](https://docs.ankiweb.net/manual/backups) warns that restoring an older backup loses subsequent changes, and its automatic backups omit media. Do not roll back an entire live collection to undo one failed content update without a separately approved recovery plan. A suspected loss may need an isolated restore and selective reconciliation instead. Do not force a one-way sync, clear history or delete media as cleanup.

## Deliver and stop

Return the updated content or verified collection reference, the source-to-note-to-card map, the exact import file or native-edit record when applicable, and the remaining semantic/history decisions. A small set can combine the map and review notes in one file. State separately what was source-reviewed, file-checked, previewed in the target client, actually applied and read back. Unavailable card IDs or scheduling evidence limit the preservation claim explicitly.

Keep source excerpts proportionate and attributed. Do not reproduce an entire restricted textbook or upload private notes to a deck-generation service. Media and private annotations retain their access boundaries; source links are not permission to fetch new private material. Sharing a deck, changing synchronization, creating reminders and enrolling in a study program remain separate actions.

Stop when the requested update packet or authorized edits are complete and the held decisions are clear. Neither successful import nor preserved review history proves that the learner knows the revised material.

## Fictional, unexecuted illustration

A fictional equipment handbook formerly says that the Mira camera loans last seven days and require a blue return slip. One existing cloze note asks for the duration as c1 and the slip color as c2. The revised handbook changes the duration to ten days but leaves the slip rule unchanged. The learner has also added a personal reminder to photograph the packed case.

The proposed packet retains that personal reminder and maps c1 to the changed duration. It shows seven → ten with the revised source locator and holds application pending the user's review-history choice. It does not treat the old successful answers as knowledge of ten days. The c2 target remains the slip color; it must not be renumbered to c1 or assigned the duration's history. Its rendered prompt still needs review because it displays the changed duration as context. A separate source-link typo can be corrected without inventing a new recall target.

These are original invented sources, note assignments and decisions. No deck, import file, application preview, study session, live edit or recovery operation was executed for this illustration.
