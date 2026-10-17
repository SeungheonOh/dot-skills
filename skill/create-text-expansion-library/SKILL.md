---
name: create-text-expansion-library
description: Prepare a reusable library of literal text snippets with stable IDs, exact multiline content, collision-aware triggers and a documented target-app export. Use for static text replacement artifacts, not dynamic macros, credential storage, global keyboard changes or sending messages.
---

# Create a text-expansion library that preserves what it inserts

Produce a reusable snippet library from approved wording or an existing export. The result must preserve literal content and trigger intent, identify conflicts, and distinguish a portable content archive from a file the named application actually accepts.

This workflow creates static replacement artifacts. [create-email-signature](../create-email-signature/SKILL.md) handles mail-client footers, while [diagnose-cross-app-paste](../diagnose-cross-app-paste/SKILL.md) investigates a failing transfer. Do not turn a snippet request into a background macro service or treat preparation as permission to modify the user's active keyboard utilities.

## Input and output contract

Use the selected source phrases/export, approved trigger naming scheme if any, intended application/version, existing trigger inventory when supplied, required scopes, and private output destination. Resolve whether text is supplied for exact reuse or the user wants wording drafted first. Preserve approved wording; do not invent commitments, personal details or opinions to make a template sound complete.

Return:

- A portable UTF-8 content archive, normally JSON, with stable snippet IDs and exact string values
- A target-native candidate only when the target's documented format and literal behavior are established
- A short mapping/collision/held-item report and a clearly labeled activation handoff

For a very small plain-text-only request, separate `.txt` snippets plus the map can suffice. JSON here is a content-preservation format, not a universal text-expander import standard. If no target is named, complete that neutral archive and leave native export pending rather than picking an application for the user.

Use a private staging folder outside every active app configuration, watched import folder and synced snippet directory. Writing a file into such a location can activate or distribute it. Do not install an expander, enable accessibility/input-monitoring permissions, alter shortcuts, start a service or paste into an external message as a format check.

Do not store passwords, recovery codes, private keys, payment data or access-bearing URLs as snippets. Hold those rows without reproducing secrets in reports. For ordinary personal/team text, establish the intended audience before sync, upload or sharing; local preparation is not permission to transmit it.

## 1. Freeze literal content and identify nonliteral behavior

Keep originals unchanged and record their file/version plus per-snippet source locator. Give each snippet a stable local ID unrelated to its position, title or trigger. Reuse existing IDs when updating a library. Multiple aliases can refer to one snippet; repeated trigger strings do not prove that two records are duplicates.

Use this minimal record, adding target-specific fields only where needed:

```text
id; label; exact replacement string; proposed/existing trigger aliases;
intended application scope; source locator; literal/held classification;
mapping status; output locator; unresolved decision
```

Preserve leading/trailing spaces, tabs, blank lines, newline presence, Unicode and punctuation. Do not silently trim, normalize typography, change casing or remove a trailing newline. Retain the original line-ending convention in provenance when the target representation must use another convention; make that conversion explicit.

Distinguish literal text from behavior embedded in an existing export: variables, dates, clipboard reads, cursor markers, placeholders, forms, nested snippets, regular expressions, scripts, shell actions and rich content. Do not evaluate those constructs during extraction or guess their current expansion. Keep them held with the specific missing mapping.

A visible token such as `[recipient]` can intentionally be literal instructional text. Record that intent; do not fill it with a real person or assume the expander will prompt. When the requested output needs prompting or executable logic, identify it as beyond this static workflow instead of reducing it silently to a frozen result.

## 2. Review trigger collisions in the actual scope

Preserve existing triggers unless renaming is requested. For new ones, propose a consistent delimiter/prefix suitable for the user's typing habits and target behavior; no prefix is universally collision-free.

Compare aliases within the candidate and against the supplied existing library. Check:

- Exact same trigger with different replacements
- Same trigger under overlapping versus truly separate application scopes
- Prefix overlap where typing a longer trigger could activate a shorter one first
- Case-insensitive or case-propagating behavior that may merge apparently distinct aliases
- Word-boundary rules and ordinary words or shortcuts likely to activate accidentally

Classify a collision as supported intentional selection, resolvable scope distinction, or blocked ambiguity. Some tools provide a chooser for repeated triggers; others overwrite or select differently. Do not impose global uniqueness as a claimed format rule, but never silently choose which replacement wins.

If the active library was not supplied, report `candidate checked internally; existing-library conflicts unassessed`. Do not scan unrelated application profiles to obtain it. An overlap is a risk to investigate, not proof of a specific runtime outcome without the target's matching rules.

## 3. Map only documented static features

Read the current official format/import documentation for the named product and version. Map strings, trigger boundaries, case behavior and application scope separately. Mark required features that cannot be represented; stripping an app scope to make an export load can turn a restricted snippet into a global one.

For an Espanso candidate, [Matches Basics](https://espanso.org/docs/matches/basics/) documents trigger/replacement pairs, multiline YAML, word-boundary behavior, case propagation and repeated-trigger disambiguation. Literal and folded YAML blocks differ; a folded block is unsuitable when line breaks must survive. Espanso also interprets variables and cursor markers, so a string that looks like plain text may need a documented literal representation or must remain held. Do not infer inertness from valid YAML alone.

Use [Espanso's configuration documentation](https://espanso.org/docs/configuration/basics/) to distinguish snippet definitions from behavior/profile configuration. A minimal static match file uses a top-level `matches` list with string `trigger` and `replace` values, as shown in its [getting-started guide](https://espanso.org/docs/get-started/). This workflow should not generate global behavior changes merely to transport content. Its [extension documentation](https://espanso.org/docs/matches/extensions) describes clipboard, shell and script features; exclude those features and imported package dependencies from this static candidate.

For another application, use its actual format rather than renaming a CSV, JSON or YAML file. Some applications expose only manual entry or a platform-specific export. If a supported native route cannot be established, deliver exact text and a small manual-entry map, explicitly marking installation unperformed.

Serialize values using a suitable safe serializer. In JSON, preserve strings and reject duplicate object keys; in YAML, use a safe data loader, string-safe quoting and no custom object constructors. Avoid accidental booleans, numbers, aliases or folded newlines. Do not execute source macros to discover their results. A literal shell command can remain approved text, but must never become an execution action or be tested in a terminal.

## 4. Verify saved strings and behavior boundaries

Reopen the neutral archive and target candidate as data. Compare decoded replacements character-for-character with the approved source, including whitespace and final newline. Display escaped whitespace or code points only where needed to explain a real mismatch; do not replace the usable text with an unreadable audit dump.

Verify:

1. Every selected source record is included, intentionally mapped to an alias, or held with a reason
2. Snippet IDs remain stable, aliases point to the intended content and no source revision is silently lost
3. Trigger conflicts and scope changes are visible, with no undocumented first/last-record winner
4. Serialized strings retain exact content; target metacharacters cannot accidentally invoke variables, cursor movement or actions
5. No imported executable feature, include path, network fetch or secret entered the static candidate
6. Original files and active app settings are unchanged

If the user separately authorizes activation, inspect and preserve the current destination library before using the supported import route. Add only the reviewed subset and preserve existing IDs/settings. Resolve any newly observed sync audience or permission prompt before continuing. A request to create the library alone ends with the files and activation handoff.

Runtime checks, when authorized and supported, belong in an unsent disposable local text surface, never a terminal, password field, live form or recipient conversation. Use the intended app scope and representative ordinary text. Compare the resulting characters, trigger consumption, word boundaries and cursor position. Inspect clipboard-related effects before overwriting useful clipboard contents. A parser pass is not a trigger test, and a successful trigger in one app does not establish every app's behavior.

## Failure handling and delivery

- **Unknown dynamic syntax:** hold the affected snippet; request its intended literal content or a separately scoped macro task
- **Collision with an existing trigger:** keep both records in the archive, hold the ambiguous native entry and ask for the smallest rename/scope decision
- **Target strips newlines or required scope:** disclose the precise loss and offer the faithful archive; do not call the native candidate equivalent
- **Parser reads a string differently:** fix the serialization layer in a new candidate, then compare decoded strings again
- **Activation response uncertain:** inspect the live library before retrying; never import repeatedly or replace concurrent edits
- **No target app or safe test surface:** deliver the checked artifacts and mark expansion behavior untested

Return the actual files, included/held counts, target/version, known collision scope, preservation exceptions and checks performed. Use separate statuses for `prepared`, `parsed and compared`, `activated` and `expanded in tested app`. Stop at the requested stage or a specific unresolved mapping/authorization; do not leave an unrequested monitoring service running.

## Fictional example, not executed

An invented team supplies three snippets: `;agenda` with two exact lines, `;closing` with a final newline, and another `;closing` with different text. No active library is available. A fourth source uses a dynamic clipboard variable.

The proposed neutral archive keeps all four source identities. A static native candidate can include the unambiguous agenda snippet, while the conflicting closing records and dynamic item remain held until their mapping is resolved. The report distinguishes four selected source records from one candidate entry and says existing-library collisions are unassessed. It never freezes today's clipboard into reusable text.

This is an authored illustration. No library was activated, snippet expanded, clipboard read or external message created for the example.
