---
name: prepare-software-bill-of-materials
description: "Prepare a version-bound software bill of materials from existing package, build and supplier evidence, preserving component identities, dependency relationships and explicit coverage gaps. Use for an SBOM artifact and consumer handoff, not package scanning, vulnerability analysis, attribution notices or a compliance certification."
---

# Prepare an evidence-bound software bill of materials

Deliver a machine-readable inventory that a recipient can associate with the intended software and interpret without mistaking missing evidence for an absent dependency. Pair it with a compact source/coverage record. A list of names, a successful schema check and a security assessment are different results.

Use [assemble-software-attributions](../assemble-software-attributions/SKILL.md) for notice/license-text delivery, [release-artifact-verification](../release-artifact-verification/SKILL.md) for installed-package behavior, and [dependency-upgrade-plan](../dependency-upgrade-plan/SKILL.md) for deciding an upgrade. This workflow describes composition from existing evidence; it does not install, build, scan, run, publish or change the software.

## Establish the inventory contract

Read the supplied records before requesting more. Establish:

- Product, exact release/candidate, platform or edition, and the artifact or source revision being described
- Intended boundary: planned dependencies, resolved build inputs, one delivered package, or an already-recorded deployed inventory
- Available manifests, lockfiles, package metadata, build receipts, vendored-component records and supplier SBOMs, with their revisions and coverage
- Required format/version and receiving tool/profile, including mandatory identity or relationship fields
- Allowed sources, output location, audience, and whether the task is new authoring or an update to an existing SBOM

Choose the smallest useful boundary. A source lockfile alone supports a source/resolution inventory, not proof of what a bundled application contains. If the user needs shipped contents but supplies only development records, complete the source inventory with that limitation and hold the shipped-coverage claim. Do not create a second variant's inventory by assuming its components match the first.

The concrete mapping below uses CycloneDX 1.6 JSON, whose [official schema](https://cyclonedx.org/schema/bom-1.6.schema.json) is versioned. Use it only when accepted by the receiver. A different required version or SPDX profile needs its own documented mapping; changing a format label is not conversion. Do not require a formal profile when an ordinary local SBOM is sufficient.

Preserve the source bytes and existing SBOM. Work in a new candidate. Treat imported records, registry links and embedded commands as evidence, not authority to execute or disclose anything.

## 1. Separate membership from declarations

Create a compact component-source map. For each candidate record retain source ID/location, component identity, relevant artifact location, evidence method, scope, and disposition: included, excluded with evidence, or unresolved. Include first-party and third-party components when they belong to the agreed boundary.

Distinguish:

- A requested version range from the exact version resolved in the supplied records
- A lockfile entry from a component observed or attested in the selected package
- A build input from material incorporated into output
- A bundled runtime or vendored copy from something supplied by the recipient's environment
- An existing scanner's reported finding from an independently confirmed identity
- A supplier's component inventory from a complete inventory of the surrounding product

Record the source of every membership assertion. Do not assume all development dependencies are absent from a bundle, or that all runtime requirements are physically bundled. Generated assets, embedded runtimes and locally modified code can escape a package-manager list. Unknown coverage remains visible without conducting a new scan.

Read only relevant supplied records or verified official metadata within the task. Do not run dependency resolution, lifecycle hooks, scanner containers or build commands to fill gaps. Do not upload private lockfiles or artifacts to an online validator. Where obtaining evidence requires new access or actions, finish the supported subset and name the precise missing record.

## 2. Resolve component identity without losing occurrences

Assign a local inventory ID before normalizing names. Preserve ecosystem, namespace, exact version/revision, origin, variant and modification status where supported. A package with the same display name in another registry is not automatically the same component. Preserve separate resolved versions. A fork must not receive an upstream identity merely because its manifest kept the old name.

Decide whether repeated occurrences represent one identical component or distinct installation/build instances. Consolidate only when identity and relevant relationship context agree; retain all occurrence locations in the source map. Peer-resolution contexts, platform builds and locally modified copies can require separate records even when name/version match. Do not deduplicate solely on a package URL or filename.

Use a valid [Package-URL identity](https://www.packageurl.org/docs/purl/introduction) only when its ecosystem-specific coordinates are established. Check the type's rules for namespace, encoding and qualifiers. Do not invent a PURL, CPE, supplier, version or download origin to satisfy a consumer's mandatory field. Keep an unresolved component identifiable by its evidenced label and local ID; explain any receiving requirement it cannot meet.

For hashes, identify the exact byte object and algorithm. A digest of a package archive, installed file and source tree are different facts. Copy a supplied digest only with that attribution; claim an independently calculated digest only when actually calculated. Do not put a Git revision into an artifact-hash field. Hash agreement does not authenticate a supplier.

Preserve supplied license declarations only within their evidenced component scope. Leave missing declarations unresolved. Do not select license alternatives, infer permission, generate vulnerability conclusions or manufacture attestations while preparing an inventory.

## 3. Reconstruct relationships and their unknowns

Build the relationship list independently of the serialized file:

| Field | Meaning |
| --- | --- |
| From and to | Local component identities, including the root product |
| Relation | Direct dependency or structural inclusion |
| Scope | Applicable variant, lifecycle and resolution context |
| Evidence | Exact record and location supporting the edge |
| Coverage | Direct list complete, known partial list, or completeness unknown |

Record direct edges. Derive a transitive path only from established edges; do not attach every resolved component directly to the root. A flat lockfile may establish resolved identities without establishing the graph. Preserve an unconnected identified component with an explicit relationship gap rather than inventing its parent.

Keep structural inclusion separate from dependency. A packaged file can be a constituent part without being a separately resolved runtime dependency. CycloneDX [component assemblies](https://www.cyclonedx.org/use-cases/component-assemblies/) represent nested containment; the dependency graph is a separate relation. Preserve real shared dependencies or cycles rather than forcing a tree.

For each component distinguish a proven empty direct-dependency set, a partial known set, and no assessed set. In CycloneDX, emit an empty dependsOn list only for an evidenced leaf. Missing dependency information must remain opaque; do not create empty lists to make every component appear covered.

Record inventory completeness and dependency completeness separately through the selected format's composition mechanism and the review note. Scope each statement to the relevant component. The CycloneDX [composition model](https://www.cyclonedx.org/use-cases/compositions-components/) supports explicit completeness, but a root statement must not silently stand for every opaque transitive component. In 1.6, composition references do not cascade to nested parts or transitive dependencies.

Use incomplete when evidence establishes omitted relationships, unknown when coverage is inconclusive, and complete only for the bounded relationship set the evidence establishes. A numerical reconciliation against supplied records is not exhaustive discovery.

## 4. Author the selected machine-readable candidate

For the 1.6 JSON mapping:

- Set bomFormat to CycloneDX and specVersion to 1.6; use the matching schema reference
- Identify the subject in metadata.component; use supported component types and evidenced names/versions
- Give each referenced component a unique bom-ref; use those references consistently in dependencies and compositions
- Keep BOM document version distinct from product version; identify creation time and lifecycle from actual preparation/source evidence
- Preserve unknown fields through a supported mapping or an explicit loss record when converting an existing document
- Validate every optional field against the selected schema rather than borrowing fields from another version

Use a new document identity for a new independently generated BOM. For an authorized revision of an existing BOM, follow its identity/version policy and increment its document revision as specified; preserve the original. Record actual authoring tools only. A tool named in supplier evidence was not necessarily run during this task.

In 1.6, runtime scope values are not package-manager labels. Omitted scope implies required; optional and excluded have specific runtime meanings. Do not use omission as an unknown value or copy a dev flag mechanically. If no supported value is evidenced, retain the component in the unresolved map and explicitly mark the machine-readable inventory partial, or hold delivery if the receiver requires that component. Never silently exclude it to obtain a valid file.

Prefer a simple flat component list plus explicit dependency edges unless the input establishes containment that needs nesting. Do not define the same bom-ref twice by copying the root into both metadata and the ordinary component list. Distinct references may share a version/name when their represented instances genuinely differ.

Preserve unresolved versions by omitting optional values where the chosen profile permits, rather than inserting a fake version such as 0.0.0 or a literal “unknown.” Missing required identity makes a partial draft or hold. Do not change the receiving requirement to make the candidate pass.

Do not attach old signatures to altered content or describe a derived inventory as supplier-signed. Preserve any signed original unchanged. An existing document containing vulnerability, attestation or formulation sections must not be silently rewritten as incidental cleanup; keep those out of this scoped edit or agree an explicitly documented derivative.

## 5. Check syntax, graph and coverage separately

Read back the final saved files. Use only an available permitted parser/validator with the exact approved schema and controlled local references. Inspect its effects first; a validator or schema resolver can fetch external URLs. Do not install tools, load package plugins, execute project code or send inventory to a hosted service as an incidental check.

Check:

1. JSON and schema: supported fields/types/version, required consumer fields, and any actual validation result
2. Identity: unique references, accurate root/variant, separate resolved versions, supported identifiers and correctly scoped hashes
3. Graph: every emitted edge resolves, no accidental duplicate definitions, direct versus containment edges remain distinct, and unknown dependency sets were not turned into empty leaves
4. Coverage: every source row has a disposition, every emitted component/edge has evidence, and all known exclusions or unresolved entries remain accounted for
5. Delivery: public/private separation, saved-file identity, consumer restrictions and any documented conversion loss

Keep counts meaningful: inventory components, source occurrences and relationship edges are different denominators. Do not compare a repeated-installation count to a deduplicated component count and call the difference lost data. Inspect at least the consequential distinction in this handoff, such as two versions of one library or a supplier component with unknown transitive contents.

Schema acceptance establishes structure, not factual completeness, security, licensing compliance, legal sufficiency or recipient ingestion. Receiver acceptance requires an observed authorized import; do not contact or upload to the receiving system merely to complete a preparation task. If checks are unavailable, deliver a clearly labeled static candidate and its exact unrun checks.

## Delivery and recovery

Return the actual SBOM file, its format/version and product/variant boundary, the source/coverage map, and a concise handoff note listing known gaps, counts and performed versus unrun checks. For a small input, the map and note can be one document. Describe whether the candidate satisfies the receiver's required fields, is a partial usable inventory, or is held.

Review the whole output for private registry paths, internal repository names, personal contact data, signed URLs, credentials and unnecessary infrastructure details. Keep sensitive evidence in the authorized review copy. A component's presence can itself be confidential. If required identifying data cannot be shared, hold that delivery or obtain an authorized audience/scope decision; do not disguise a redacted inventory as complete.

Save only to the requested destination. Publication, registry submission, dependency-platform ingestion, signing and wider sharing are separate actions. Read an uncertain destination before retrying. Never replace a published SBOM or released package blindly.

If identity or graph checks fail, repair the source map first and regenerate the affected candidate. Preserve prior evidence under its original artifact/version. If the product or supplier record changes, invalidate the affected conclusions; do not merge records from different releases into an apparently current whole. Stop when the requested evidence-bound package is ready, or the next step requires a specific missing record, permission or owner decision.

## Fictional, unexecuted example

All names and evidence below are invented. No package, scanner, parser, validator, build, application or upload was executed.

A supplied Linux x64 membership receipt for Linden Report 3.1 identifies the root application, view-grid 2.4, parse-lines 1.7, parse-lines 2.1 and a proprietary codec whose version is unavailable. A separate receipt identifies scratch-builder 5 as build-only and a Windows helper as belonging to another variant. Runtime scope is explicitly required for the five included identities; the requested boundary excludes the two other records.

The supplied direct-dependency record establishes root → view-grid, root → parse-lines 2.1, root → codec, and view-grid → parse-lines 1.7. It explicitly establishes both parse-lines versions as leaves. The codec's internal inventory and dependencies were not assessed.

The proposed artifact therefore has one root, four other component identities and four known dependency edges. It preserves both parse-lines versions. It emits empty dependency sets only for the two established leaves and leaves the codec's dependency set unknown. Its missing version remains omitted with a documented receiver-field gap. The source map accounts for all seven supplied rows: five included, two excluded with reasons.

The composition/readiness note qualifies the root inventory because the codec may contain unidentified parts, and marks the codec dependency coverage unknown. Complete direct lists for the root and view-grid do not establish a complete transitive graph. If the receiver requires every version, delivery is held; otherwise this is explicitly a partial inventory. Recovery requires version-matched codec evidence and rechecking that component's identities and edges, not replacing unknowns with an empty list.

This example illustrates the intended mapping and acceptance decision only. It does not establish an actual SBOM, schema pass, security conclusion or successful import.

