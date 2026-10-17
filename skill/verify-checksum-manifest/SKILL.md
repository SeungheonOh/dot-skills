---
name: verify-checksum-manifest
description: "Verify a supplied checksum manifest against a bounded received file set, preserving filename syntax, baseline provenance, exact coverage and unreadable or unstable results. Use for a byte-integrity receipt, not creating a transfer package, authenticating a publisher or validating dataset meaning."
---

# Verify the files behind a checksum manifest

Deliver a receipt that answers which received file identities agree with the supplied byte baseline and whether the required set is complete. A checksum utility reporting several successful lines is not sufficient when it skipped malformed entries, followed an out-of-scope path or never examined extra files.

Use [portable-project-handoff](../portable-project-handoff/SKILL.md) to select and build a project package, [account-export-audit](../account-export-audit/SKILL.md) to assess an export against independent account coverage, and [validate-dataset](../validate-dataset/SKILL.md) for data-rule conformance. This workflow reads an existing manifest and received ordinary files. It neither repairs their bytes nor proves that the manifest is trustworthy.

## Establish the baseline and selected population

Resolve the supplied manifest's exact identity, origin and intended delivery/version; the authorized received root or explicit file selection; and the expected manifest format, digest algorithm and representation. Record whether the task checks only listed files or requires exact membership of a defined directory tree. Include recursion, exclusions, hidden files and treatment of empty directories when those affect coverage.

Keep three independent questions visible:

- **Baseline provenance:** Who supplied the expected values, and what binds them to the intended delivery? A checksum downloaded beside a payload is not independent publisher authentication
- **Listed-byte agreement:** Do the actual selected bytes match every accepted manifest entry?
- **Set coverage:** Are all required identities present, and are unexpected files allowed? A manifest can establish its listed set; it cannot establish an unseen account or project is complete

If only a file is supplied without expected values, offer an observed digest inventory with that narrower label. Do not compute a checksum from the received file and then call comparison with itself verification. If authenticity is required, obtain the accepted signature/key or other trust evidence through the appropriate workflow; no match here substitutes for it.

Use existing supported read access and an approved private report location. A read request does not authorize uploads to online hash checkers, downloads, replacements, renames, permission changes or deletion. Paths and digests can identify private material; share the detailed receipt only with the authorized audience. Keep credentials and authentication-bearing URLs out of it.

## 1. Read the manifest as a format, not whitespace

Preserve the original manifest bytes and record its size and observed digest separately from payload digests. Read its documented grammar before dispatching a checksum utility. Establish character encoding, record terminator, digest encoding, filename escaping and any text/binary marker. A file named `SHA256SUMS` is a hint, not the full grammar.

For example, GNU SHA-2 utilities use a defined untagged output format; GNU checksum formats have distinct tagging, escaping and separator behavior. A naive whitespace split loses filenames containing spaces, while treating literal escapes as filenames can select the wrong file. Consult the actual producer and verifier's version and [GNU checksum documentation](https://www.gnu.org/software/coreutils/manual/coreutils.html#Summarizing-files). Do not assume a NUL-delimited output option means every checker can read that same representation.

Account for every physical record: valid entry, grammar-defined non-entry, malformed entry or undecodable span. Retain locators and parser diagnostics. Do not accept a readable prefix as the complete manifest, skip unknown algorithm labels, trim significant filename characters, strip a byte-order marker without a format rule, or reinterpret ambiguous names until matches appear.

Validate digest length and alphabet for the declared algorithm/encoding. Normalize only representation differences the grammar permits, such as hexadecimal letter case. If expected size is supplied, retain its unit and integer meaning as a separate check. Do not treat a platform's unspecified ETag, object ID or multipart checksum as a whole-file SHA-256.

Detect repeated entries before collapsing them. Same-path/same-digest duplicates remain visible as duplicate assertions; same-path/conflicting-digest entries leave that identity ambiguous. Different paths with equal hashes remain different required files. A duplicate row must not inflate matched-file counts or fill a missing identity.

## 2. Bind each accepted name to an in-scope file

Resolve names relative to the declared payload root, never the process's incidental working directory. Reject absolute, drive-relative, parent-escaping or otherwise unsupported path forms before opening files. Do not expand shell variables, globs, command substitutions or URLs. A filename beginning with a dash must remain a filename, not an option; a special standard-input marker must not silently select standard input.

Use the target filesystem's evidenced naming behavior. Preserve exact spelling and detect case, normalization and file/directory collisions without silently choosing a winner. Do not URL-decode or sanitize manifest names to produce a match. An approved source-to-received rename map can be used when supplied, but its exact identity mapping becomes part of the receipt.

For ordinary-file verification, inspect object type without following links and include ancestor links/reparse points in the boundary check. Hold symbolic links, cloud placeholders, special files and unsupported native objects rather than opening devices, blocking on pipes, hydrating a cloud collection or escaping through a symlink. If links are explicitly part of the task, establish whether the baseline covers link text or target bytes; this ordinary-file contract cannot guess that.

Before handing a manifest to a general checker, ensure every path it may open belongs to this approved set. A tool's strict parser mode is not a filesystem sandbox. Use a supported bounded/no-follow read route or a stable isolated input snapshot. When concurrent path replacement cannot be excluded, report that limitation instead of claiming race-proof containment.

## 3. Hash the actual complete byte streams

Read each resolved ordinary file in binary mode with the accepted algorithm. Do not decode text, normalize line endings, unpack containers or strip headers. Hashing an archive checks the archive bytes; hashing its extracted files is a different comparison. [GNU's SHA-2 utility documentation](https://www.gnu.org/s/coreutils/manual/html_node/sha2-utilities.html) distinguishes these named digest algorithms and file checking.

Confirm that the producer's recorded mode covered those same bytes. On a platform where text-mode reading transforms the stream, a text-mode baseline is not automatically a raw-byte baseline. Hold an unresolved representation difference or obtain the intended byte-mode values; do not silently normalize the received file or label that difference transfer corruption.

Set a proportional per-file and total byte/time budget before reading. Count actual bytes read, retain errors, and distinguish a zero-byte file from an unreadable one. A limit, cancellation, incomplete read or unsupported algorithm is an incomplete check, never a matching result. Do not increase limits silently or omit a large file from the denominator.

Bind the result to a stable source observation using available file identity/version and before/after metadata or snapshot evidence. Ordinary size and timestamp checks can detect some changes but do not prove a coherent snapshot under active writers. Hold changed files; re-read only after a stable version or accepted quiescent interval is established. Do not label a concurrent edit corruption.

If using a native verifier, record the exact version, inputs, mode, exit status and relevant diagnostics. Inspect invalid-line, skipped-file and read-error results, not just lines ending in `OK`. An independent size check and manifest/inventory reconciliation are still needed when the contract requires them. Preserve per-file evidence even if another entry fails.

## 4. Reconcile the manifest, filesystem and verdict

Use one file row per accepted identity with the manifest locator, exact relative path, expected algorithm/digest and optional size, resolved object identity, observed size/digest, and one result:

- **Matched:** All required byte and size comparisons completed against a stable accepted baseline
- **Mismatched:** A completed comparison disagreed; identify the exact property
- **Missing:** The required path is absent in a complete observed scope
- **Held:** A malformed/conflicting entry, unsafe identity, unsupported object, read failure, budget limit or changing source prevented the required comparison

Retain malformed or unbound manifest records separately rather than forcing them into a valid-file row. For exact-set requests, enumerate the bounded received tree independently and classify unexpected files and excluded support files. Never infer no extras from verifying only the manifest. If enumeration is incomplete, report coverage unknown even when every readable listed file matches.

Reconcile counts in their own units: raw manifest records, valid assertions, distinct accepted identities, and matched/mismatched/missing/held files. State the exact-set result separately. An empty manifest does not prove an empty delivery unless the independently defined scope and contract support that conclusion.

An overall accepted receipt requires a settled parse, no unresolved conflicting assertions, all required files matched, complete required coverage and compliance with the agreed extra-file rule. A known mismatch can establish failure while other checks remain unknown. Expected exclusions need not become defects; explain them without widening the accepted set after seeing the results.

## Deliver, preserve and recover

Return the private receipt with baseline provenance, manifest identity, selected root/version and comparison policy; per-file results; set reconciliation; actual tools/checks; and the exact remaining evidence or replacement needed. Read back the saved report and ensure its verdict matches its rows. An uncertain save calls for checking the intended output before retrying, without overwriting an unrelated report.

Leave the manifest, received files and failed evidence unchanged. A mismatch does not identify whether the sender, transfer, disk or baseline caused it. Check the intended version and parser first. If corrected files or a corrected manifest are later supplied, record the new identities and issue a new receipt; retain the earlier result. Do not repair expected hashes to match observed data or obtain replacement data from an unapproved source.

Stop when the scoped byte/set result is established or a specific evidence, access or resource gap blocks it. Matching digests do not establish malware safety, successful import, correct subject matter, preserved filesystem metadata or recipient use.

## Illustration: fictional and unexecuted

A fictional handoff expects exactly `notes.txt`, `image.bin` and `empty.txt`, with its checksum list excluded from the payload scope. The supplied paper observations say `notes.txt` matches, `image.bin` differs, and the zero-byte `empty.txt` matches its expected empty-file digest. A complete directory listing also includes `old-notes.txt`.

The receipt records three distinct expected files: two matched, one mismatched, none missing and none held. Exact-set coverage fails because of the unexpected fourth file. It preserves the conflicting digest observations and asks for the intended `image.bin` version; it neither deletes `old-notes.txt` nor rewrites the manifest. If the listing were incomplete, extra-file coverage would instead remain unknown.

This is a fictional, unexecuted illustration. It supplies no calculated hashes, inspected user files, observed utility output or verified transfer.
