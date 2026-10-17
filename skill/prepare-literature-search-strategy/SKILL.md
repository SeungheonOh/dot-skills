---
name: prepare-literature-search-strategy
description: "Prepare a reusable literature-search strategy for a defined research question, with database-specific query text, justified limits, known-reference checks and an honest search-run record. Use for a search-method handoff, not a research synthesis, bibliography conversion or screening decisions."
---

# Prepare a reproducible literature-search strategy

Deliver a searcher-ready package that explains what to search, where, how the query means what it is intended to mean, and how to record an actual run. Its core artifact is the literal strategy for each named database and platform, accompanied by a compact concept map and verification record. A topic description and a list of databases are not sufficient.

Use [synthesize-research](../synthesize-research/SKILL.md) when the user needs an answer from the literature, [export-bibliographic-records](../export-bibliographic-records/SKILL.md) for reference-file conversion, and [prepare-literature-screening-handoff](../prepare-literature-screening-handoff/SKILL.md) for preserving selection decisions after retrieval. This workflow does not establish study quality, clinical recommendations or a completed systematic review.

## Establish the search contract

Recover from the request and existing protocol:

- The question and intended use, including relevant subject, setting and evidence types
- Eligibility rules and their revision, with date, language or publication-type restrictions and their reasons
- Selected databases and exact interfaces; when selection is open, the subject coverage and access constraints needed to choose them
- Any earlier strategies, run histories, result exports and independently known relevant references
- Whether the task is strategy preparation only, revision of an existing strategy, or preparation plus a bounded authorized search
- Requested artifact format, audience and destination

Ask only when a missing choice materially changes the strategy. If the database platform is unknown, prepare the concept map and identify the missing target; do not label generic Boolean text ready to paste into every service. A small exploratory question does not require a systematic-review protocol. If the requested evidence claim requires broader searching than the permitted scope, state that gap without silently expanding access or sources.

Preserve earlier strategies and run records. Treat protocol changes as versioned decisions, not retrospective corrections to what was searched. Search content can reveal private interests or unpublished work: use approved public-topic wording, and obtain authorization before transmitting sensitive personal or confidential terms to a named provider. Never insert patient identifiers, participant details, credentials or internal project names merely to make a search more specific. Reading source material does not authorize uploading it to a query-writing service.

## 1. Separate eligibility from searchable concepts

Translate the question into a few meaningful concept groups. Keep synonyms and alternative labels within a group distinct from the intersection between groups. Do not automatically require every element of the question to appear in a title or abstract; an outcome, setting or comparison may be poorly reported even in relevant work.

Create a compact map with concept ID, intended meaning, candidate words, controlled-vocabulary candidates, and whether the concept is required in the query or checked later during screening. Give a reason for a search restriction that could exclude relevant evidence. Do not add a narrow outcome term simply to reduce the number of results to a convenient workload.

Derive terms from the supplied question, inspected relevant records and the selected database's actual vocabulary. Distinguish observed terminology from proposed synonyms. Confirm a subject heading and its scope before calling it a valid controlled term; the same words used as free text are not an equivalent replacement. Record decisions about narrower-term expansion, historical headings and ambiguous abbreviations when they affect retrieval.

An ineligible topic mentioned alongside the eligible topic may still occur in a relevant record. Treat exclusions such as NOT as consequential choices: inspect what they remove when testing is in scope, or mark the exclusion unverified. Keep access convenience separate from eligibility. A full-text-available filter is not a neutral substitute for arranging later document retrieval.

## 2. Bind each translation to its actual search interface

Identify the database separately from the platform providing it. Record the collection or index selection, coverage limits and exact search mode. A multi-database session must retain which collections were selected; do not attribute its combined result to a single database.

Read the current official search documentation for the chosen interface. Map the concept strategy deliberately rather than replacing field tags mechanically. Resolve the features actually used:

| Feature | Decision to retain in the handoff |
| --- | --- |
| Text fields | Exact fields searched and whether an all-fields default adds unintended content |
| Subject headings | Vocabulary, exact heading, expansion behavior and any restriction to a major topic |
| Phrases and proximity | Word order, distance meaning, punctuation handling and fallback behavior |
| Wildcards | Supported character, position and expansion restrictions; relevant singular/plural or spelling effects |
| Boolean groups | Explicit grouping and operator meaning, including every exclusion |
| Limits | Exact field or interface filter, boundary values and justification |
| Session features | Dependencies on saved sets, selected indexes, implicit filters or a transient history |

For example, the [PubMed User Guide](https://pubmed.ncbi.nlm.nih.gov/help/) documents search translation, phrase handling and persistent applied filters. Inspect Search Details rather than assuming entered text is the executed interpretation. PubMed warns when a quoted phrase is absent from its phrase index, and its filters can remain active for subsequent searches. These are platform-specific checks, not behavior to assume in another database.

Produce complete literal query text for each platform. If a strategy uses numbered search lines, include every definition and its combination order; a final expression such as `#3 AND #7` alone is not portable. Provide an expanded expression when supported, or clear instructions to recreate the line history. Keep copyable query characters separate from commentary and typography that might alter them.

Do not hide an unsupported proximity operator or field behind a supposedly equivalent translation. Describe the loss and propose a supported broader search plus later screening, or hold that target for a decision when equivalence matters. Keep source links and access dates for consequential syntax choices; a screenshot without selectable query text is supplementary evidence, not the whole strategy.

## 3. Make limits and update behavior explicit

Record the selected date field and inclusive or exclusive boundary behavior. Publication date, database entry date and record-update date answer different questions. A relative window must retain its literal expression and run date; a reusable fixed-cutoff search needs explicit dates. Do not silently convert one into the other.

For an update, identify the earlier query revision, source coverage, last run and retained results. New records can have old publication dates, so searching only publications newer than the last run cannot by itself establish an update without omissions. Choose a documented update field and overlap policy when appropriate, or rerun the full bounded strategy and compare record identities. Leave coverage unresolved when the provider cannot support the required history. A new strategy is not merely a continuation of the old one if its concepts or limits changed.

Keep language, date, document-type and other limits in the package even when applied outside the search box. Retain their rationale and any indexing-related blind spot. Do not add restrictions because a database returns many results or remove accepted restrictions without authority. Propose changes visibly, with the affected question or coverage consequence.

Separate database querying from supplementary routes such as forward citation searching, reference-list checking or a named website search. If included, define their seed records, direction, boundary and recording method. Do not count an unperformed route as covered or describe a search engine's estimated total as retrieved records.

## 4. Check retrieval behavior without tuning to a desired answer

First inspect the strategy against the concept map: all intended groups are represented, alternatives are grouped correctly, exclusions are deliberate, and each platform has a supported translation. Check both positive and boundary cases. A syntax-valid string can still ask the wrong question.

When search execution is within scope and access is available, perform a bounded pilot using the intended interface. Record the exact submitted query, actual interpretation or warning messages, active filters, run time and observed count. Check line-level behavior where it helps locate a defect. Do not report a successful live check from documentation reading alone, and do not make account changes, buy access, create alerts or contact authors merely to complete a pilot.

Use independently known relevant references as diagnostic probes when available. For each one, first establish whether the database contains the intended record and whether the stated limits make it eligible for retrieval. Then distinguish retrieved, missed by the strategy, excluded by a documented limit, not indexed there, and unresolved. Investigate a miss at the responsible concept, field, indexing or limit rather than adding that paper's identifier to force a pass. Keep probes obtained during strategy development distinguishable from references held out for a later check.

The [Cochrane search guidance](https://www.cochrane.org/authors/handbooks-and-manuals/handbook/current/chapter-04) describes known-publication checks and warns that retrieving only the already-known records can conceal a biased strategy. Use probe results to identify defects; they do not prove field-wide recall. Report a probe ratio only with its inspectable, database-eligible denominator, and label it as probe retrieval rather than search sensitivity. Without suitable probes, record the missing check instead of inventing reference papers.

Inspect a bounded sample of unexpected results to diagnose a term's meaning or field choice. Record how the sample was selected; ranked top results do not establish precision across the whole set. Changing a strategy to favor a conclusion or an arbitrary result count is not acceptable. Retain each meaningful revision, its reason and the checks repeated after it. If specialist review is required by the user's process, provide the exact candidate for that review and keep approval pending until evidenced.

For preparation-only work, stop at the static strategy and planned checks. Leave counts, execution times and observed probe outcomes blank or explicitly not run. A draft can be useful without claiming execution readiness that has not been established.

## 5. Package the strategy and run record together

Deliver one manageable document or a small set of text files. Include the actual queries, not only a narrative of how they could be constructed. A reusable record can use the following fields, omitting genuinely irrelevant ones:

```text
Strategy ID / revision / question and eligibility revision:
Database / provider platform / selected collections / search mode:
Concept map and consequential term decisions:
Complete query or ordered line definitions:
Limits, date-field semantics and rationale:
Official syntax sources and checked dates:
Known-reference checks and unresolved translation issues:

Run ID / strategy revision / observed run time and zone:
Exact submitted query / interpreted query or warnings:
Actual filters and database coverage shown:
Displayed result count and whether exact or estimated:
Export scope, format, part identifiers and observed row counts:
Coverage gaps, export truncation or interrupted steps:
Verification performed / not performed:
```

Maintain the distinction between a proposed query, one accepted by the interface, and a completed retrieval/export. A displayed count does not prove every record was exported. If exports are requested, preserve their unmodified source parts and per-run identities. Reconcile export limits, page/batch boundaries and repeated records before claiming completeness; do not manufacture a historical total from today's file. Keep occurrence counts separate from unique references and later included studies.

Use the applicable [PRISMA-Search reporting guidance](https://www.prisma-statement.org/prisma-search) when a systematic-review search report is requested. It is reporting guidance, not evidence that the strategy was executed, independently reviewed or exhaustive. Do not fill a completed-methods paragraph with proposed dates or blank run-record fields.

Avoid session tokens and credential-bearing links in the portable packet. A public query URL may be useful when verified, but retain the text and configuration needed to understand it without relying on a transient session. Sharing a search packet, importing references, or distributing licensed full texts requires its own authorized destination and scope.

## Acceptance, recovery and completion

Read back the saved artifact and inspect its query text as a recipient would. Accept the preparation when every selected target has either a usable supported strategy with its evidence status or a precise unresolved blocker; the concept map, limits and revisions agree; and planned actions cannot be confused with observed runs. Identify the remaining verification needed before someone relies on an untested translation.

For an executed search, additionally verify actual query interpretation, relevant probe outcomes and requested export coverage against the retained run evidence. A rerun may return different records as the source changes. Preserve both runs, explain their identity and timing, and do not rewrite the earlier result to make the counts match.

If a platform rejects a query, retain the submitted text and error, isolate the unsupported feature, and revise only that target with a new version. If it is unavailable or access is denied, leave it blocked; do not substitute a different collection as equivalent or evade restrictions. For an interrupted read-only search, inspect retained history and export parts before repeating work; label a fresh run separately when the original result set cannot be recovered. Never clear the user's saved searches or history as a repair.

Before updating an existing strategy artifact, check for intervening edits and preserve conflicting revisions. If saving is uncertain, inspect the intended destination before retrying. Report a prepared but unverified save honestly. Finish with the actual package, target-by-target readiness, meaningful gaps and the exact execution/export status. Further searching, screening, recurring surveillance or publication is not implied.

## Fictional illustration, not executed

A fictional team wants a search handoff about spaced practice in adult workplace learning. Its approved scope includes retention measures, but the supplied probe descriptions show that authors use varied names for those outcomes. The draft therefore proposes two required concept groups, spaced practice and workplace learning, while retaining retention as a screening criterion. That choice is labeled proposed until accepted under the team's process.

One early text-word candidate for PubMed, with a fictional approved 2015–2025 publication window, is:

```text
(((spaced[tiab] OR distributed[tiab]) AND (practice[tiab] OR learning[tiab])) AND (workplace[tiab] OR occupational[tiab])) AND 2015/01/01:2025/12/31[dp]
```

This is an unrun draft, not a recommended comprehensive strategy. Its record says `adult population and retention: later screening`, `controlled vocabulary: not yet reviewed`, `query interpretation: not checked`, and `result count: not run`. Those holds matter even though the string is copyable.

The fictional probe checklist has four references: two expected within the selected database and limits, one known to fall outside the approved date range, and one whose database presence is unknown. The last two cannot silently enter an eligible-retrieval denominator, and neither of the first two is labeled retrieved before an actual run.

In a separate fictional translation case, the source strategy uses a proximity feature absent from the second target. Its handoff records the difference and a proposed broader alternative; it does not claim the two queries are equivalent. If a future operator sees 240 results but exports only one 100-record part, the expected record says 240 displayed and 100 exported with remaining coverage unresolved, rather than 240 records delivered.

All details and numbers are original and fictional. No literature query, database session, probe lookup, export, account change or end-to-end workflow was executed for this illustration.
