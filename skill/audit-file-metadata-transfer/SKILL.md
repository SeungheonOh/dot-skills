---
name: audit-file-metadata-transfer
description: "Audit whether an existing file copy or transfer preserved the requested non-byte properties, using source-to-copy identities, filesystem capabilities and property-level evidence. Use for metadata and link-relationship acceptance, not moving files, restoring backups, changing access or proving application compatibility."
---

# Check what survived beyond the file bytes

Deliver a property-level transfer report: which required attributes and relationships survived, which were intentionally changed, and which cannot be established. Two matching file digests say nothing by themselves about ownership, timestamps, alternate streams, hard-link relationships or effective access.

Use [portable-project-handoff](../portable-project-handoff/SKILL.md) to build a package, [backup-restore-spot-check](../backup-restore-spot-check/SKILL.md) to retrieve historical copies, and [build-folder-synchronizer](../build-folder-synchronizer/SKILL.md) to reconcile ongoing edits. This skill audits an already-created copy or supplied transfer evidence without performing the transfer or repairing attributes. [storage-cleanup-accounting](../storage-cleanup-accounting/SKILL.md) addresses space reclaimed rather than preservation.

## Define the preservation requirement

Identify the source and destination roots or stable item IDs, exact selected population, known source-to-copy map, transfer time/version and relevant tool/options if supplied. Record the actual platforms, filesystems or service representations, mount/context differences, available read methods and the approved private report destination. Keep native cloud-document history, application package semantics and live databases outside an ordinary filesystem-attribute comparison unless their supported evidence is explicitly available.

Choose the properties that matter to the intended use; do not demand every possible attribute. For each, state whether the contract requires exact preservation, a defined equivalent representation, an intentional new value or no preservation. Resolve only consequential missing choices. A data handoff may deliberately assign new ownership while an operational replica requires an executable bit and hard-link grouping.

Establish the right baseline. A pre-transfer source snapshot can support a historical preservation claim. A current source that changed afterward supports only a current comparison unless lineage is known. A screenshot of a file-properties dialog may be useful but cannot establish attributes it does not display. When only logs exist, return an evidence audit and identify the missing readbacks; do not claim files were directly inspected.

Read only the authorized source and copy. Do not change ACLs, owners, security labels, flags or timestamps, run copied programs, follow external links, hydrate online-only files, mount devices, create snapshots, elevate privileges or repeat a transfer under this audit. If preserving a requested property would expose data or weaken access controls, report the conflict rather than proposing an automatic repair.

## 1. Bind corresponding objects before comparing attributes

When access-time preservation matters, capture relevant object timestamps before directory listing, symlink-target reads or payload reads, using an existing suitable method. If earlier inspection may already have changed them and no prior evidence exists, leave original access-time preservation unverified.

Enumerate the selected population with coverage limits. Use the supplied path/identity map and retain exact names, object types, source revision and observed destination identity. Do not match files only by equal display names, timestamps or digests: identical contents can belong to separate selected objects.

Inspect links without following them. Separate regular files, directories, symbolic links, reparse-like objects, shortcuts, placeholders and unsupported special objects. A shortcut to an unchanged original is not a transferred copy. A source link converted into a destination regular file is a type change even when its target bytes match.

Use ordinary data-stream size/digest evidence when needed to establish the compared payload, but keep that result independent of metadata. Include selected empty directories and directory attributes when the contract requires them. Report source-only, destination-only, ambiguous and unreadable entries rather than substituting easy examples.

Retain read times and available identity/version checks. If files or relevant attributes change during collection, hold those rows or use existing coherent snapshot evidence. Before/after size and modification-time agreement does not guarantee an atomic snapshot under active writers. Do not erase an unstable result by selecting whichever observation gives a match.

## 2. Build a property and capability matrix

For each required property, record its meaning, source evidence, destination evidence, comparison rule and result. Distinguish `absent` from `not supported`, `not exposed by this reader`, `permission denied`, and `not inspected`. An empty response from an incapable API is not proof an attribute is absent.

Use the relevant rows only:

| Property | Comparison that matters |
| --- | --- |
| Modification, access or creation time | Same semantic clock field, timezone/representation and documented resolution or accepted rounding rule |
| File type and symbolic-link target | Same required object type and literal target, plus separately scoped relative-target meaning if requested |
| Hard-link relationships | Same grouping of selected names that refer to one underlying file, not identical inode numbers across volumes |
| Ownership and mode bits | Expected destination identity mapping and required bits, separate from effective access |
| ACLs, inheritance and security-related attributes | Supported semantic comparison in the actual destination context; unresolved principal or inheritance mapping remains held |
| Extended attributes, resource forks or named streams | Required namespace/name inventory plus authorized value/length/digest evidence; main-stream hashing alone is insufficient |
| Sparse layout or allocation behavior | The expressly required logical-size, hole-map or allocation property, using a supported observer and explicit limits |

Do not treat this table as a universal cross-platform schema. Define how a requested property is represented on both sides before calling it equivalent. If a destination cannot represent it, report an unsupported requirement; a sidecar that records the old value is documentation, not restored behavior.

## 3. Compare property meaning, not familiar labels

**Times.** Keep content modification, last access, metadata change and creation times separate. Record raw precision where available and any display conversion. POSIX-style `ctime` is not creation time; API meanings and resolutions vary by platform. A nanosecond-valued field does not guarantee nanosecond precision. [Python's filesystem field documentation](https://docs.python.org/3.14/library/os.html#os.stat_result) describes these distinctions. Select rounding/tolerance from the evidenced transfer contract before judging differences, never from the observed mismatch.

Directory listing, reading a symbolic-link target and reading payloads can themselves update access times, depending on the platform and mount behavior. Capture relevant timestamp evidence before these reads and disclose observation effects; Linux's [path-lookup documentation](https://cdn.kernel.org/doc/html/latest/filesystems/path-lookup.html) discusses access-time handling for symbolic links. Do not reset times to conceal them, or change mount settings to prevent them. If exact untouched access-time evidence is required and no suitable existing read-only snapshot/method exists, leave that property unverified. A new destination's creation or metadata-change time need not equal the source unless the contract explicitly requires and supports it.

**Links and identity.** On a filesystem with reliable file IDs, compare hard-link equivalence classes within each side. Source names A and B may share an identity while destination A and B have two separate identities: byte equality still leaves link preservation failed. Equal link counts alone cannot establish the group, and links outside the selected scope remain unexamined. Do not create hard links, break them or traverse link targets to improve the result. For symlinks, unchanged literal relative text can resolve differently after relocation; report text preservation and target meaning separately.

**Ownership and access.** Numeric user/group IDs and principal names can mean different accounts on another system. Use the accepted identity map. Equal permission text does not prove equivalent effective access under different parents, inherited ACLs, service shares or security contexts. Preserve the distinction between a raw attribute match and an observed access-policy result. Do not impersonate users or make test writes to infer access; missing supported read-only evidence remains unknown. Changing security-sensitive permissions is a separate action with its own approval requirements.

**Additional content and attributes.** Enumerate only required namespaces or streams using supported read methods. Attribute values can contain private names, source URLs, device identifiers or security data; retain the minimum comparison evidence in a private report, and do not assume hashes make them anonymous. Microsoft's [file-stream documentation](https://learn.microsoft.com/en-us/windows/win32/fileio/file-streams) distinguishes default and named data streams. A matching default stream does not establish that a selected named stream survived. Likewise, copying an AppleDouble or other sidecar file does not alone prove that the destination application reconstructed its intended metadata.

**Storage layout.** Logical bytes, holes, reported allocation and exclusive physical storage are different properties. A sparse file copied densely can preserve all readable bytes yet violate a space/layout requirement. Conversely, different allocation totals across filesystems need not mean content loss. Report only the observer's supported meaning; do not promise identical physical placement, deduplication or reclaimable space from a byte hash or block count.

## 4. Reconcile tool promises with actual readbacks

Treat transfer options and success logs as evidence of intent and reported execution, not final attribute results. Check the actual tool/version and relevant filesystem support. For example, [rsync's archive option](https://download.samba.org/pub/rsync/rsync.1) does not by itself include preservation of ACLs, extended attributes or hard links. [GNU cp's preservation documentation](https://www.gnu.org/s/coreutils/manual/html_node/cp-invocation.html) also distinguishes requested attributes and some failure-reporting behavior. Do not infer a missing attribute from flags alone when destination readback is available, or infer success solely from exit zero.

For each object/property pair, assign one result: preserved under the stated rule, intentionally changed under the accepted contract, different from a required value, or unverified with its reason. Keep optional observations separate from mandatory acceptance. A known failed requirement can reject the transfer even when other rows are unknown; an overall pass requires all mandatory rows covered and satisfied or explicitly permitted to change.

Reconcile selected-object counts separately from property-check counts. One file can fail several attributes, and one lost hard-link group can involve several names. Avoid multiplying one underlying relationship defect into a misleading count of independent transfer failures.

## Deliver the audit and the smallest recovery choice

Return the source/copy mapping, baseline time/version and coverage, required-property matrix, evidence locators and supported verdict. Include observed content-byte agreement separately, intentional losses, privacy/access findings, inspection effects and unavailable checks. Read back the saved report so a summary cannot say “preserved” while a mandatory row remains held.

Leave both sides unchanged. If a discrepancy needs correction, identify the property, affected objects and candidate supported route, with any required authority or missing capability. A retry can overwrite later edits, and restoring old ACLs can expose files; neither is implied by this report. A new copy or corrected attribute set needs a new version-bound audit rather than overwriting the old failure evidence.

If a save or earlier transfer outcome is uncertain, inspect existing evidence before retrying any operation. Stop at the requested audit result or a specific blocked observation. This task does not establish full backup coverage, application usability, safe execution, actual recipient access or permission to delete originals.

## Illustration: fictional and unexecuted

A fictional two-file handoff requires matching data bytes, modification times at one-second resolution and preservation of one hard-link group. Ownership is intentionally assigned to the recipient. Supplied paper observations say both source names share one file ID, while the two destination names have different file IDs; each destination's data digest and accepted modification time matches its source.

The report marks two payload comparisons matched, two time comparisons preserved, ownership intentionally changed, and the one required hard-link relationship failed. It rejects full preservation without calling the bytes corrupt. It does not link the destination files together or repeat the transfer; those actions could affect later edits and require a separate scoped decision.

This is a fictional, unexecuted illustration. No files, accounts, permissions, link relationships or metadata were inspected or changed.
