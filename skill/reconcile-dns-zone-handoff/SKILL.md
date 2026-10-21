---
name: reconcile-dns-zone-handoff
description: "Reconcile an authorized DNS zone export with a candidate import package, preserving expanded record names, typed data and RRset membership while exposing provider-managed exceptions. Use for offline migration preparation, not live DNS changes, delegation cutover or connection diagnosis."
---

# Reconcile a DNS zone before handing it over

Deliver a candidate zone package and a record-level account of what it preserves, changes or cannot represent. A file that parses, a matching record count and a successful lookup of the homepage are different evidence. None proves that a zone migration preserves mail, delegated children, verification records or provider-specific behavior.

Use [configuration drift inventory](../configuration-drift-inventory/SKILL.md) for generic environment differences, [integration configuration handoff](../prepare-integration-config-handoff/SKILL.md) for application setup templates, and [web connection diagnosis](../trace-web-connection-failure/SKILL.md) for a currently failing request. This workflow handles DNS master-file interpretation and import parity. It does not activate a zone, change nameservers, update registrar records, provision signing keys or run network probes.

## Establish the export and destination contract

Identify the exact zone apex and class, source export time and completeness, source view or environment, intended target provider/import format and requested destination for private preparation. Distinguish a complete authoritative export from selected dashboard rows, a recursive resolver answer or an old working copy. Do not infer absent records from a partial snapshot.

Obtain the target's current official import rules: accepted record types, relative-name syntax, TTL handling, replacement versus additive import, and treatment of apex NS/SOA records and provider features. Record the documentation version/date. If the target is unknown, prepare an expanded record ledger and decision queue, not a supposedly portable ready-to-import file.

Use supplied or already authorized exports. Do not request a zone transfer, query private names through public resolvers, enumerate subdomains or connect to the DNS control plane merely to complete an offline inventory. A public-looking hostname does not authorize disclosure of an internal zone. Keep private topology and verification values in the approved local destination; omit authentication material and signing keys entirely. If an export includes a credential, stop processing that input and request a sanitized replacement without reproducing the value.

Record whether the request includes authoring the candidate or only comparison. Preparation does not authorize uploading it to an import preview: that can disclose the whole zone even before activation. Ask for the missing target/data-sharing decision when it matters, not a redundant approval for already authorized local work.

## 1. Resolve master-file context before comparing rows

Preserve the original file and its byte identity. Process entries in source order before any sorting. Keep source locations and an explicit context record for the initial origin, current origin, previous owner, default TTL, class and approved included files. A missing initial origin or required include leaves affected records unresolved.

[RFC 1035 section 5.1](https://www.rfc-editor.org/rfc/rfc1035.html#section-5.1) defines master-file owner inheritance, relative names, origin directives, quoting and multiline entries. Expand a relative owner or domain-name-valued field under its applicable origin; a trailing dot denotes an absolute name. A leading-blank entry can reuse the previous owner. Do not split on whitespace or remove semicolon suffixes without respecting quoted/escaped data and parentheses. Preserve the original representation alongside the expanded meaning.

Resolve default TTLs using the actual exporter/parser rules, including `$TTL` where supported. Do not substitute the last SOA field as a generic record default. BIND's [zone-file documentation](https://bind9.readthedocs.io/en/stable/chapter3.html) illustrates default TTL and origin handling; [RFC 2308 section 4](https://www.rfc-editor.org/rfc/rfc2308.html#section-4) distinguishes the SOA minimum field's negative-caching role. Keep an unresolved TTL unknown rather than assigning a convenient value.

Inventory directives before invoking any parser. `$INCLUDE` can read another file, and implementation extensions can generate many records. Limit includes to reviewed files under the authorized source boundary, with cycle, depth, record-count and size limits. Never follow an arbitrary include into unrelated files. Either expand supported directives with provenance and bounded semantics or request a flattened export. Do not silently discard directives that the target cannot import. A parser run that reads undeclared files is not an isolated file check.

Build a ledger of each expanded owner, class, type, effective TTL, typed RDATA, source location and interpretation status. Retain duplicate occurrences for diagnosis even when they resolve to one logical record. A set built too early can conceal conflicting TTLs or incomplete parsing.

## 2. Compare record meaning, not convenient strings

Group records by expanded owner, class and type, retaining the distinct RDATA members and all source occurrences. Compare RRset membership independently of file order. Within an RRset, inconsistent TTLs are a hold rather than permission to choose a winner. [RFC 2181 section 5](https://www.rfc-editor.org/rfc/rfc2181.html#section-5) defines RRsets and their TTL consistency.

Use a type-aware comparison. For domain-name fields, apply DNS name comparison rules without lowercasing arbitrary text or binary RDATA. Preserve MX preferences, SRV priorities/weights/ports, TXT character-string boundaries and bytes, and other type-specific fields. One TXT record containing two strings is not two TXT records. Do not concatenate or re-chunk text merely to make a provider's screen look similar; establish its import representation first. RFC 1035's [record definitions](https://www.rfc-editor.org/rfc/rfc1035.html#section-3.3) are the starting point for the types defined there; use the relevant specification for other types.

Keep unknown types explicit. [RFC 3597](https://www.rfc-editor.org/rfc/rfc3597.html) specifies a generic representation for unknown record types; this does not prove that a particular import service accepts it. Preserve the data and mark target support unresolved rather than dropping the record or reinterpreting its bytes as text.

Classify each source RRset as preserved, intentionally changed, target-managed with a documented replacement, unsupported, or unresolved. Identify candidate-only records separately. Every change needs its exact before/after meaning and the requested or documented reason. A source row cannot disappear merely because the destination does not display it.

Review important relationships, not just individual syntax:

- Apex SOA and NS belong in the comparison even when the target manages them; state the target's documented handling instead of copying old provider values blindly.
- Child delegations and related glue need an explicit disposition. Do not confuse a child NS RRset inside this zone with the parent delegation for this zone.
- Ordinary CNAME data must not coexist with unrelated data at the same owner. Apply the protocol's DNSSEC exceptions rather than banning all associated metadata. [RFC 2181 section 10.1](https://www.rfc-editor.org/rfc/rfc2181.html#section-10.1) explains the alias constraint.
- Provider aliases, flattening, proxying, routing policies and health checks need a separate feature mapping. An exported address or familiar record label does not establish equivalent behavior at the target.
- Mark signed data and key/parent-DS dependencies for a separately reviewed DNSSEC transition. Do not copy stale signatures, remove DS records or generate keys as a formatting fix.

Keep the review proportional. A small static zone can have a compact ledger; a policy-driven provider export may remain a partially mapped handoff until its behavior is documented. Do not claim application availability from record parity.

## 3. Keep serials and timing claims honest

Preserve the supplied SOA serial unless an authorized candidate change and the target's management rules call for another. Record who controls it. A date-shaped serial is a convention, not an instruction to overwrite it with today's date. [RFC 1982](https://www.rfc-editor.org/rfc/rfc1982.html) defines 32-bit serial arithmetic, including wraparound and undefined half-range comparisons. Use those rules when comparing revisions; ordinary integer ordering can misclassify a valid successor. An ambiguous ordering requires owner reconciliation, not an invented reset.

Separate source TTL, candidate TTL and already-cached data. A lower value in an unsent candidate has changed nothing live. Even an eventual lower published TTL does not retroactively shorten earlier cached responses. Negative answers have their own cache lifetime under [RFC 2308](https://www.rfc-editor.org/rfc/rfc2308.html). Do not promise a universal propagation deadline or a cutover time from a file alone. This handoff can list timing inputs for the operator; scheduling or executing the migration is separate.

## 4. Author and inspect the exact candidate

Write a new candidate, never over the original. Use the target's documented syntax and explicitly named zone context. Where supported, expanded absolute names and explicit TTLs make context changes easier to inspect, but do not invent a universal import convention. Preserve type-specific quoting and escaping. Do not add fabricated missing records or provider placeholders that look ready to activate.

Re-read the saved candidate independently of the generation map and reconstruct its record meanings using the declared target interpretation. Reconcile in both directions: every source record is preserved or has a visible disposition, and every candidate record has an authorized origin. Compare full RRset membership, TTLs and typed data, not only total row counts. Retain parser failures and unresolved mappings in the acceptance result.

If an installed permitted offline checker is available, inspect its actual behavior and options first. BIND's [named-checkzone documentation](https://bind9.readthedocs.io/en/stable/manpages.html#named-checkzone-zone-file-validation-tool) describes syntax and integrity checks. Restrict the check to the reviewed candidate and approved includes; avoid unrequested journals, configuration files or generated output. Do not install tooling, start an authoritative server, import into a provider or issue DNS queries just to obtain a green check. Without a safe checker, finish a static review and label parser acceptance unverified.

A BIND checker accepting a master file does not prove a provider accepts it, nor that the provider retains every imported record. Reserve those claims for separately authorized observed import/readback. Keep static interpretation, local parser acceptance, provider import parity, delegation state, DNSSEC validation and live resolution as separate statuses.

## Deliver, recover and stop

Deliver the actual candidate when ready, source/candidate identities, apex/view context, target contract, compact parity ledger, provider-feature decisions and verification limits. If unresolved items prevent a safe import, label the package blocked or review-only; do not hide exceptions in a success footer. Keep private records out of a public report.

For a failed or interrupted local save, inspect the current candidate before retrying. Regenerate to a fresh path when necessary and retain the original. If the source export changes, rebase the comparison on the new evidence rather than overwriting the candidate from an obsolete snapshot. No rollback of live DNS is needed because this workflow does not change it; reverting a deployed migration is a separate operational decision.

Stop when the agreed candidate and parity result are delivered, or identify the precise missing export, target behavior or owner decision. Do not establish ongoing monitoring, perform a registrar cutover or use a live lookup as a substitute for the missing source inventory.

## Fictional, unexecuted illustration

An offline export for `cedar.example.` contains this selected excerpt:

```text
$ORIGIN cedar.example.
$TTL 3600
www     IN CNAME edge.vendor.example.
mail    IN A 192.0.2.20
@       IN MX 10 mail
note    IN TXT "alpha" "beta"
```

This is not a complete zone. Its expected interpretation includes `cedar.example.` MX preference 10 targeting `mail.cedar.example.`, and one `note.cedar.example.` TXT record with two character strings. A candidate MX target of `mail.` is not equivalent. Two separate TXT rows containing `"alpha"` and `"beta"` also change the record set even if a dashboard seems to show the same words.

A review would hold those changes, retain the explicit absolute external CNAME target and the 3600-second effective TTL, and request the complete export before claiming whole-zone parity. It would not infer SOA, NS, delegation or DNSSEC readiness from this excerpt. These are authored expected decisions only. No parser, DNS query, provider import, zone transfer, repository test or live change was executed for this illustration.
