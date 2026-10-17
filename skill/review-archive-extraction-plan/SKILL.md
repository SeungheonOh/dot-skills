---
name: review-archive-extraction-plan
description: "Review a received archive before extraction and produce a member-level hold or bounded extraction plan tied to an exact archive, target filesystem and installed extractor. Use for pre-write path, type, collision and resource decisions; this workflow does not extract or execute payloads."
---

# Review an archive before it writes files

Produce a concrete decision about a received archive: which members could be written under the requested policy, which must be held, and what a later extraction would have to enforce. The deliverable is a reviewed plan, not an extracted directory or a safety certificate. A familiar extension, valid container checksum or clean member listing cannot establish that opening the contents is safe.

Use [portable-project-handoff](../portable-project-handoff/SKILL.md) to author and exercise a selected project package. Use [define-git-archive-contents](../define-git-archive-contents/SKILL.md) for a Git source inclusion policy. [bound-stream-transforms](../bound-stream-transforms/SKILL.md) handles bounded byte expansion without filesystem member placement. This workflow starts with an existing potentially untrusted archive and ends before extraction.

## Establish the planned destination and policy

Identify the exact archive bytes and provenance, intended contents/use, selected members or whole-archive requirement, target operating system/filesystem, proposed private destination and existing extractor/version. Set limits for compressed input, listing work, member count, per-member and aggregate expanded bytes, path length/depth and time. Scale limits to the task rather than imposing one universal size cap.

Resolve whether the destination is required to be new and empty, how existing files would be treated, and which object types are actually needed. For an ordinary document bundle, a conservative profile permits only regular files and directories and requires exclusive/no-overwrite creation. A request to review an archive does not authorize creating that destination, extracting files, installing an extractor, changing permissions or uploading contents to a scanning service.

If the target is unknown, produce target-independent findings and hold platform-specific acceptance. If the archive is unavailable and only a listing is supplied, label the result a listing review: it is not bound to independently inspected archive bytes, and omitted fields remain unknown. Keep passwords out of chat and reports; encryption without an existing supported authorized read route is a hold, not permission to break it.

## 1. Inspect bounded container metadata

Preserve the source. Use an existing format-aware read-only interface, without launching a self-extracting executable, opening documents or running bundled helpers. Identify the actual container and method rather than trusting its suffix. Record archive size/digest, reader/version, observed format, available feature flags and inspection completeness.

Apply resource bounds while listing too. A compressed tar can require decompression to reach later headers; a “list” operation is not necessarily cheap. Stop on time, input, memory or metadata-count limits and retain the readable prefix as partial evidence. Do not infer the remainder is empty or harmless. Never recurse into nested archives automatically.

Retain every member occurrence in archive order, including duplicates. For each, capture its occurrence/offset identifier, stored and interpreted name, object type, declared sizes where available, compression method, link target, encryption flag and consequential metadata such as mode, ownership or extended path fields. Record raw names safely when control characters would make a report misleading; do not emit terminal-control sequences directly.

Resolve effective metadata according to the format, including long-name or override records. If the reader cannot expose a field that could change placement or type, hold that uncertainty. Do not claim one listing represents the extractor's interpretation when encoding, header inconsistencies or parser differences are unresolved. [Python's ZIP documentation](https://docs.python.org/3.14/library/zipfile.html) describes member-level metadata, duplicate-name handling and method-dependent support; check the actual tool used rather than assuming all ZIP readers behave alike.

## 2. Build a member-to-destination map

Treat every member name as untrusted data. Interpret path syntax under both the archive format and the intended extractor/target. Retain the original name, effective relative name, proposed destination and finding. A string-prefix test is not a containment check: `bundle-other` is not inside `bundle`.

For the ordinary conservative profile, hold:

- Absolute paths, UNC/device forms, drive-qualified or drive-relative names, and any parent traversal component
- Alternate path separators or encodings whose target interpretation is uncertain, embedded NULs, misleading controls, and unsupported reserved names or stream syntax
- Names that would collide after the target's case, normalization, trailing-character or other evidenced name rules
- Duplicate member destinations, including identical-name duplicates whose bytes happen to match
- File/directory conflicts such as a regular file `docs` and a second member `docs/readme.txt`
- Paths that exceed the actual destination's supported component, total-length or depth limits

Rejecting all parent components is this profile's conservative choice; it is not a claim that every archive containing an internal `..` violates its format. Do not fix suspicious names by stripping prefixes, flattening folders, decoding twice or renaming on the fly. Such edits create a different mapping and can overwrite, merge or break logical references.

Inspect implied parent directories as well as explicit directory members. A conflict can arise even when the archive has no directory entry for a parent. On Windows, names and path rules vary beyond a simple forbidden-character screen; use [Microsoft's file-naming guidance](https://learn.microsoft.com/en-us/windows/win32/fileio/naming-a-file) and the known extractor's behavior. A Linux-only comparison cannot establish Windows acceptance.

## 3. Resolve types, links and expansion hazards

Under the ordinary-file profile, hold symbolic links, hard links, reparse-like entries, devices, pipes, sockets and unsupported special types. Do not follow a link to inspect its target. A member that installs a link can redirect later writes, so checking each apparent path independently is insufficient.

If links are genuinely required, return that requirement for a different explicitly supported plan covering link targets, earlier/later members, ancestry, cycles and existing-destination state. A fresh directory alone is not enough if the archive itself creates links. Do not silently fall back to copying target content or enabling an extractor's fully trusted mode.

Separate declared from enforced resource bounds. Sum declared regular-member sizes where available, but treat unknown sizes, sparse logical lengths, nested compressed members and unsupported methods explicitly. A compression-ratio warning is useful evidence, not an output limit. A future extraction must stop on actual per-member and total output bytes and satisfy its CPU/memory/disk bounds even when metadata lies. Sparse allocation and logical size are different quantities.

Record requested restoration of ownership, modes, ACLs, timestamps or extended attributes separately from file placement. Do not authorize privileged ownership, security contexts, capabilities, set-ID behavior or executable activation merely because those fields are in the archive. A data-only extraction can intentionally omit metadata only if that matches the user's preservation needs; otherwise mark the incompatibility.

Python's [tar extraction-filter guidance](https://docs.python.org/3.14/library/tarfile.html#extraction-filters) warns that filters do not prevent every dangerous feature or denial of service and that source/destination changes matter. An extractor's protective mode is evidence for selected controls, not permission to omit the plan's collision, type and resource checks.

## 4. Produce an actionable extraction contract

Use a compact plan containing:

- Archive identity and inspection coverage; exact target and extractor/version
- Allowed member occurrence IDs and their exact relative destination mapping
- Held/rejected occurrences, reasons, and dependencies that make other members unusable
- Required object-type policy, no-follow/containment behavior and exclusive-creation rule
- Enforced input/output/count/time bounds and the control that would enforce each
- Metadata retention/loss policy and required permissions already available
- Source revalidation, fresh-destination prerequisites and concurrency assumptions
- Post-extraction membership/byte checks and the precise completion/partial-failure reporting needed

Keep a conditional plan distinct from execution approval. If a safe enforcement mechanism is unavailable or its semantics cannot be established, the plan remains held. Do not recommend a command that merely lists checks but then invokes unrestricted bulk extraction. Do not install tools or change security settings to satisfy the plan.

For a whole-archive request, one rejected or uninspectable required member prevents full acceptance. For an explicitly selected subset, independent eligible members may have a conditional plan, but preserve all original findings and check whether selection omits required dependencies. Do not quietly shrink a whole-archive request to a convenient subset.

Define what later work would need to observe without performing it here: exact archive still matches; approved destination is fresh and controlled; no overwritten or outside-root files; every allowed occurrence has one intended output; actual output remains within limits; retained bytes and required metadata agree; rejected members remain unwritten. CRC or internal integrity checks do not authenticate a sender or establish application safety.

## Acceptance, recovery and delivery

Accept the review artifact when every observed occurrence is accounted for, inspection gaps are explicit, target-dependent conflicts are resolved or held, and each proposed effect has an enforceable prerequisite. Return `held`, `conditional plan ready`, or `partial review` with its exact scope. Never label a plan “extraction succeeded” or an archive “safe to run.”

Read back the saved private plan and verify its member counts and mappings against the source observations. Do not include private payload contents or unnecessary original names in a broader summary. No extracted copies, downloads or third-party reports are implied.

If the archive, extractor, destination or selection changes, invalidate the affected plan and inspect the new state. Preserve the earlier findings. A later interrupted extraction must keep its partial directory separate and inspect actual effects before retrying; this review does not authorize deleting those files or overwriting them on restart. If metadata is unreadable or the inspection budget expires, request a bounded replacement or a specific authorized capability rather than treating an incomplete listing as approval.

## Illustration: fictional and unexecuted

A fictional received ZIP is intended for a case-insensitive Windows destination. Its supplied member listing has five regular-file occurrences: `docs/readme.txt`, `docs/Readme.txt`, `../outside.txt`, `assets/logo.png`, and `assets`. The last member is a regular file, not a directory.

The review holds both readme occurrences for destination collision, holds the traversal member, and holds both `assets` occurrences for a file/parent conflict. Zero members receive a ready extraction mapping under the declared whole-archive profile. It requests a corrected archive that preserves the intended five identities or an explicit revised selection; it does not choose duplicate winners or flatten paths.

This is a fictional, unexecuted listing review. No archive was opened, extracted, scanned for malware or exercised in a target application.
