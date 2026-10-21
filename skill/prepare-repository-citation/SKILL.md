---
name: prepare-repository-citation
description: "Prepare or repair maintainer-owned CITATION.cff metadata for a software or dataset repository, preserving release identity, author credit and preferred-citation behavior. Use for a repository citation handoff, not a bibliography export, manuscript citation repair or archive deposit."
---

# Prepare repository citation metadata

Deliver a usable `CITATION.cff` candidate and a short explanation of which work readers will be asked to cite. The important outcome is correct credit and version identity, not merely a visible citation button.

[Bibliographic export](../export-bibliographic-records/SKILL.md) converts reviewed references for a citation manager. [Source-linked citations](../maintain-source-linked-citations/SKILL.md) maintains manuscript occurrences. [RO-Crate packaging](../package-ro-crate-research-objects/SKILL.md) describes research-object relationships. This guide instead establishes the repository maintainer's citation instructions; it does not register a DOI, publish a release or decide authorship disputes.

## Establish the cited work before writing fields

Read the existing citation file, README citation instructions, selected release record and any supplied archive or publication metadata. Identify the repository and source revision, whether the subject is software or a dataset, the intended release or project-wide scope, and the requested output location. Preserve the original file when updating it.

Distinguish the work itself, a particular released version, and a paper describing it. Record the supplied evidence for each identifier. A paper DOI must not become the software DOI merely because both titles resemble the repository name. An identifier for a collection of versions does not establish which version a user ran. A default-branch commit after a release must not silently inherit that release's archive identity.

Use the maintainer's approved author list and order. A Git contributor count, repository owner, committer email or paper author list does not settle software authorship. Keep supported names and collective credit without inventing personal name components, affiliations or ORCIDs. Ask about a material credit conflict rather than selecting whichever source is easiest to parse. Exclude private contact details and unpublished collaborators unless their publication is authorized.

## Select the citation behavior deliberately

Confirm whether the user wants readers to cite the software/dataset, a related paper instead, or both. Do not add a preferred paper just because one exists.

The [CFF 1.2.0 schema guide](https://github.com/citation-file-format/citation-file-format/blob/main/schema-guide.md) defines root metadata for the software or dataset. `preferred-citation` describes a different work to cite instead; `references` describes work it builds on. Keep those roles separate. Preserve the root's own identity even when a preferred citation is supplied.

GitHub uses `preferred-citation` for the generated citation rather than presenting it as a second citation. If the maintainer asks for both works, make that request clear in the human-readable message and any authorized accompanying instructions, and explain the consumer limitation. Do not claim that one generated snippet credits both. Consult [GitHub's citation-file behavior](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-citation-files).

## Author a small, evidence-bound candidate

Use the receiver-supported CFF version. For 1.2.0, required keys are `cff-version`, `message`, `title` and `authors`. The file is YAML 1.2 named exactly `CITATION.cff`. Quote string values that might be interpreted as numbers or special YAML syntax. Use supported person or entity objects, not an undifferentiated author string.

Keep optional metadata useful rather than exhaustive:

- `version` and `date-released` describe the selected work, not the CFF format or today's editing session. The release date requires a full calendar date; omit an unsupported optional date rather than inventing a day.
- `doi` can carry one work identifier; `identifiers` supports multiple described identifiers. Label concept-wide and version-specific identifiers accurately rather than presenting them as interchangeable.
- Root `type: dataset` identifies a dataset. Do not borrow a preferred-reference type for the root.

Check the chosen schema when adding other fields. Preserve existing supported metadata outside the requested correction. Do not turn package dependencies into an automatic citation list, infer a license from public availability, or relabel an author-approved citation policy as a legal requirement. A missing required fact leaves a draft incomplete; a plausible placeholder is not a resolved value.

Reconcile release metadata as a unit. Updating the version while retaining the preceding release's date or DOI produces a plausible but misleading citation. If the new archive record does not exist yet, omit its optional identifier and identify the pending step. Do not create an archive deposit, retag history or modify a released artifact to make the fields agree.

## Inspect content and consumer behavior separately

Reopen the exact saved candidate. Compare every changed value against the source evidence, including author order, work level and release identity. Inspect the preferred citation independently of the root. Check for stale duplicate instructions elsewhere and propose only the related edits the request needs.

When an available validator is authorized, use the selected CFF schema and report its actual result. Plain YAML parsing is not CFF validation; neither establishes authorship or identifier accuracy. Do not upload private metadata to an online generator or install/run repository code merely to check a citation file. If validation is unavailable, deliver a static candidate with that limit.

For GitHub integration, the root file on the default branch drives the repository citation link. A file on a working branch is not evidence that this UI has changed. If publication is authorized, compare the current revision first, make the narrow change, then inspect the saved file and actual citation output. Check which work, authors, date, version and identifier the consumer exposes. Other citation formats may be linked without being parsed, so a visible link alone is not a successful CFF rendering.

If the generated citation differs, distinguish source metadata error from consumer mapping or display limitations. Preserve correct source metadata rather than corrupting it to force one display. Keep a local candidate when publication needs a decision; read back an uncertain write before retrying.

## Deliver and stop at the requested stage

Return the candidate or verified changed file, its source revision and intended release, the selected credit behavior, and any missing evidence. State separately what was inspected, schema-validated and observed in the target consumer. A citation file does not prove the software executes, that an archive deposit exists or that scholarly claims are sound.

For the next release, identify the fields that must be reviewed together and the owner responsible for approving credit changes. Do not introduce recurring automation or release publication as an incidental extension.

## Fictional illustration, not executed

A maintainer supplies approved authors for “Harbor Mesh” version 2.4, its release date and a version-specific archive record. The repository's old citation still describes 2.3. A related methods paper has a different author list, and the maintainer requests citation of both works.

The candidate updates the software release fields together and preserves its own approved authors. The paper remains a separate work with its own metadata. The handoff explains that adding it as `preferred-citation` changes GitHub's generated snippet to the paper; it does not produce a two-work citation. The maintainer can choose that behavior with explicit instructions to cite both, or keep the software snippet and describe the paper separately. Neither choice silently assigns the paper's authors or DOI to the software.

This is an authored illustration only. No citation parser, schema validator, repository publication, consumer rendering, archive deposit or live workflow was executed for this guide.
