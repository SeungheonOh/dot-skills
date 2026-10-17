---
name: review-signed-pdf-revisions
description: "Map an existing PDF's certificate-based signatures to the revisions they cover, reconcile later changes with native validation and certification evidence, and return a bounded content-coverage report. Use for signed-document revision review, not signing, editing, changing certificate trust or deciding legal validity."
---

# Review signed PDF revisions

Explain which saved document state each signature covers and what happened afterward. Deliver a signature-to-revision map and a concise account of later changes, bound to the exact received file and the validator actually used. A signature that validates for an earlier revision does not, by itself, establish that its signer signed every value displayed in the current revision.

Use this for questions such as “What changed after the first signature?” or “Both signatures look valid; did they cover the same answers?” Keep the original signed file unchanged. This is a technical evidence review, not a decision that an agreement is enforceable, a person consented, or a document's statements are true.

For assembling an unsigned packet, use [signing preparation](../prepare-document-signing-packet/SKILL.md). For merging competing wording, use [document revision reconciliation](../document-revision-reconciliation/SKILL.md). For an ordinary software-package signature check without a signed-document revision question, use [release artifact verification](../release-artifact-verification/SKILL.md).

## Establish the review boundary

Resolve from the request and available evidence:

- The exact PDF or bounded file set, its source, and the current version the user wants reviewed
- The question to settle: later edits, a warning, a particular signer's content coverage, or reconciliation of several signatures
- Any important fields, pages or attachments the user specifically needs traced; do not invent an obligation to audit every factual claim
- The available native validator, its version and operating environment, and any existing organization-specified validation policy
- Whether current certificate-status lookups are permitted, or the review must remain offline with supplied or embedded evidence
- A private destination for the report and any authorized comparison exports; the original must remain recoverable and unchanged

A request to inspect a named file permits the ordinary read-only checks it entails. It does not authorize uploading the PDF to a new validation website, contacting signers, changing trust settings, adding signatures or repairing the document. Ask only for a missing decision that blocks the requested conclusion. If no supported validator or original signed file is available, prepare the evidence inventory and identify the missing capability; do not call a visual inspection cryptographic validation.

## Preserve the evidence and the validation environment

Retain the received bytes and record their file identity, size and digest when available. When the viewer can save changes, inspect a separately named byte-identical working copy and keep the received original untouched. A screenshot, printed copy, flattened export or a new PDF produced from the same pages is a different object. Preserve any supplied provider receipt separately; it may describe a transaction but does not substitute for inspecting the actual signed file.

Use the existing authorized desktop application or supported local verifier. Preserve its security protections. Do not enable document scripts, launch attachments, follow embedded links or accept new permissions merely to inspect signatures. An opening or password restriction is a blocker to resolve through the user's authorized access route, not a reason to remove protection. Never request a signing private key or digital-ID password for verification.

Before opening, check whether the chosen route automatically validates on open or retrieves certificate information. Respect an offline constraint before that action, using an already permitted offline route rather than silently contacting services or altering global security settings. A native certificate-status request and uploading the whole document to a hosted validator are different disclosures. If a new network permission or unapproved destination is required, name that step and continue with available local evidence.

Record the validation time and relevant existing settings, including the time basis, trust-store source and revocation-check behavior where observable. [Acrobat's validation preferences](https://helpx.adobe.com/acrobat/desktop/e-sign-documents/manage-digital-signatures/set-preferences.html) expose controls for these behaviors and automatic validation. Inspect settings without changing them. A missing setting value remains unknown; a screenshot of a green badge does not establish the policy behind it.

Do not select Add Verification Information, save an optimized copy, clear a signature, flatten fields or use Print to PDF. [Adding verification information](https://helpx.adobe.com/acrobat/desktop/e-sign-documents/fill-sign-documents/add-verification.html) is a separate workflow that can retrieve data and save it into the PDF. That modification is outside this unchanged-file review. If the viewer offers to save on close, decline an unrequested rewrite and keep the report outside the PDF.

## 1. Inventory signatures and the revisions they identify

Open the signature inventory in the supported validator rather than counting handwritten-looking marks on pages. A visible signature graphic, a typed name, an empty signing field and a certificate-based signature are different evidence. Invisible signatures can matter too. Report a signature as absent only when the supported inventory has actually been inspected; an ordinary viewer that shows no panel may simply lack the feature.

Assign a local row ID to each actual signature or document timestamp. Record only the identifiers necessary to distinguish them:

```text
row ID | signature/field locator | kind reported by validator
certificate subject and issuer | certificate fingerprint or equivalent stable ID
covered revision identifier | current revision relationship
native status and detailed evidence locator | later-change review state
```

Do not collapse different certificates with the same displayed name, or several signature occurrences by the same certificate. Distinguish approval signatures, certification signatures and document timestamps according to the validator. A service's certificate may identify the service that applied a seal; do not automatically relabel it as each human participant named in the document or transaction receipt.

Capture revision identifiers and ordering from the native evidence. A displayed signing time is not a reliable way to order document revisions. [RFC 9321's PDF profile](https://www.rfc-editor.org/rfc/rfc9321.html#appendix-B) describes the incremental relationship between successive PDF signatures. Use that relationship to ask which version is covered, while relying on the actual validator to identify this file's supported revision structure. Do not reconstruct a history from filenames or infer that the last visible signature covers every later byte.

If the file is a portfolio or contains embedded PDFs, keep the container and its component documents distinct. Inventory only the requested scope. A result for the outer file does not automatically establish each embedded document's own signature status or history. Do not open or extract components beyond the authorized review merely to produce a larger count.

## 2. Validate the actual signature entries without changing trust

Run the native validation operation for the in-scope signatures and inspect each detailed result, including entries that the summary marks unknown or invalid. In current Acrobat, [the documented route](https://helpx.adobe.com/acrobat/desktop/e-sign-documents/manage-digital-signatures/validate-digital-sign.html) uses the Signatures panel and its validation command; Signature Properties exposes certificate details. Confirm the controls in the installed version rather than treating the documentation's labels as execution evidence.

Keep at least these findings separate for each signature:

- Whether the validator accepts the signature's cryptographic integrity for the identified signed revision
- Whether later changes are present, and the validator's result for those changes
- Whether its certificate path is accepted under the recorded trust context
- What time and revocation evidence the result relies on, and what remains unavailable

Preserve the application's meaningful status text with its locator and observation time. Do not turn an unavailable algorithm, unsupported signature type, interrupted check or missing certificate into a mathematical signature failure. Conversely, do not relabel a reported integrity failure as a harmless trust warning without evidence from the detailed result.

Never import an embedded certificate as a trusted root just to obtain a successful result. The received document is not independent authority for its own trusted identity. [Acrobat's trust controls](https://helpx.adobe.com/acrobat/desktop/e-sign-documents/manage-digital-signatures/set-certificate-trust.html) can also allow privileged document behavior, so changing them is not a cosmetic repair. If an expected organizational trust anchor is unavailable, report the exact gap for the appropriate administrator instead of changing the acceptance policy.

## 3. Relate signed content to the current displayed document

For each in-scope signature, open its supported signed-version view and compare that revision with the current document. [Acrobat provides a signed-version comparison](https://helpx.adobe.com/acrobat/desktop/e-sign-documents/manage-digital-signatures/compare-versions.html) from the signature's options. Use the native signed representation, not an independently re-exported approximation. If the feature is unavailable, retain the known revision identifiers and mark content comparison unperformed.

Start with the user's consequential locations, then inspect the native change report's remaining entries so the explanation accounts for its reported scope. Record the comparison coverage: full native change list, selected page/field inspection, or an explicitly incomplete report. A page count, text-only diff or screenshot comparison cannot establish the absence of every PDF-object change.

For each relevant difference, retain:

```text
change ID | compared signature/revision and current file identity
native change description | page/field/object locator when exposed
earlier value or state | current value or state
reported permitted/rejected/unknown treatment | evidence and interpretation limit
```

Separate a later signature or validation-data addition from a changed answer, annotation, attachment, page or visible content. Keep exact values and meaningful qualifiers at material locations; do not summarize “minor form changes” when a requested amount or date changed. If the UI groups changes too coarsely to locate them, preserve that limitation instead of claiming an exhaustive content map.

Where available, compare adjacent signed revisions as well as each relevant signed revision with the current document. This can localize when a value first appears. A difference between revision 1 and revision 3 alone does not establish whether revision 2 introduced it. Do not assign the edit to a person merely because their signature follows the change: the signature's coverage and the identity of the editor are separate questions.

Reconcile the map in both directions. Every in-scope signature must point to a reviewed or explicitly unavailable revision, and every reported later change must have a disposition or an unresolved entry. Include changes after the latest signature. Do not infer “nothing changed after signing” from the fact that all listed signatures remain cryptographically valid for their own revisions.

### Interpret certification and field restrictions narrowly

Inspect any native certification permissions, locked-field information and modification assessment relevant to the changed locations. [Adobe's certification documentation](https://helpx.adobe.com/acrobat/desktop/e-sign-documents/manage-digital-signatures/certify-pdfs.html) distinguishes a certification signature and its permitted later actions from ordinary approval signing. Record the actual restrictions and the validator's decision for this file; do not assume all certified files have identical permissions.

Apply these distinctions:

- A permitted later form fill can coexist with a valid earlier certification. It does not mean the earlier signer signed the later field value
- A later approval signature may cover a more complete revision. It does not retroactively put that revision inside an earlier signature's covered content
- An unchanged visible page is not proof that no later objects, field values or attachments changed
- A restriction or lock defines a technical constraint. It does not establish the business authority of the person making an allowed change
- Unsupported or conflicting modification analysis stays unresolved. Do not manually override it because the pages look reasonable

Use supported detail to determine whether a relevant field was locked at the earlier revision and how the validator treats its later state. If that information is unavailable, state it explicitly. Do not edit a field to test the lock, alter signature dictionaries, repair byte ranges or remove a later revision to make the original appear valid. Specialized format forensics or a standards-conformance assessment is separate work.

## 4. Qualify trust, time and revocation evidence

Keep this context attached to the revision findings rather than replacing them with one green/red verdict. Match the certificate identity to any independently supplied expected signer or organization, and distinguish an application's trusted path from evidence that a particular human personally reviewed the content. If the user supplied no identity expectation, report the certificate identity and trust result without inventing a verified relationship.

Separate the signer-declared clock time, a verified timestamp and the time this review occurred. [Adobe's deployment guidance](https://www.adobe.com/devnet-docs/acrobatetk/tools/DigSigDC/planning.html#timestamp-servers) explains that a trusted timestamp concerns the prior existence of the document/signature, while a signer's local clock can be changed. It is not proof that the named person performed an action at exactly that timestamp. Preserve native timezone information and do not silently reinterpret a displayed local time as UTC.

For certificate-status results, record whether the validator used embedded, cached or newly retrieved evidence when exposed, the relevant validation time, and any reported gaps. The same [official guide's revocation section](https://www.adobe.com/devnet-docs/acrobatetk/tools/DigSigDC/planning.html#certificate-revocation-checks) describes OCSP/CRL checks and their configurable behavior. An unavailable status check is neither proof of revocation nor proof of current good standing. Do not claim a fresh online result from an offline or cached check.

An expired certificate today does not alone settle the validator's historical result; record its treatment of trusted time and available status evidence. Do not weaken revocation requirements, accept an expired timestamp, change the system clock or switch trust policy to force success. If two validators disagree, retain their exact versions, settings, file identity and per-signature results; explain only evidenced differences and hold the unresolved conclusion.

## Acceptance, recovery and delivery

Return the unchanged original's identity and a private report containing:

- The signature inventory, covered revisions and requested scope actually inspected
- The later-change map, with precise earlier/current values at the user's important locations
- Native integrity and modification results for each signature, with trust/time/status qualifications kept separate
- Which parts of the current content are demonstrably in each reviewed signed revision, and which appeared later or remain unverified
- The validator/version, observation time, relevant settings, evidence locators and any material missing capability

Read back the report and reconcile its rows to the native observations. Check the original's final digest against its preserved input identity where possible; report an unavailable byte-identity check honestly. If opening or inspection unexpectedly writes a new file, preserve the received original and the changed copy separately, identify which bytes each observation concerns, and restart the affected review from the original. Do not overwrite either with a reconstructed “clean” version.

Call the review complete when every in-scope signature and reported relevant change has an evidenced disposition or explicit limitation. A completed report may conclude that a requested content-coverage claim is unsupported. Avoid “the document is authentic,” “everyone signed the final version” or “legally valid” when the evidence supports only narrower technical findings.

On an unavailable signed-version view, failed validation request or inaccessible certificate service, retain completed independent rows and name the exact unresolved check. A retry must use the same preserved file and a documented reason, such as the authorized service becoming available. Do not run repeated network checks, seek a more permissive viewer or change security settings until the badge turns green. A changed file or validation policy creates a new review context; earlier results cannot be silently carried over.

If a different source version is needed, ask for the existing original or the specified evidence without sending an unrequested message to its owner. Sharing the report or signed file, requesting a replacement signature, editing the document and accepting an agreement require their own authorization. Stop after the bounded report and precise next decision.

## Fictional, unexecuted illustration

A fictional equipment checklist has three stored revisions. The user asks which quantity was covered by each signature and supplies an expected organization certificate identity. In the invented evidence, revision 1 contains a certification signature and a blank, unlocked quantity field; its reported permissions allow form filling, later signatures and comments. Revision 2 fills the quantity with `12` and adds an approval signature. Revision 3 adds a comment, with no further approval signature.

The authored report maps the certifier to revision 1 and the approver to revision 2. Assuming the fictional native validator reports both signatures valid for their revisions and the later changes permitted, that result still does not show that the certifier signed quantity `12` or that the approver signed the revision-3 comment. The final content map distinguishes the quantity present at revision 2 from the later comment. It does not identify who typed either change without separate evidence.

If the approval signature's certificate-status check is unavailable, retain its reported integrity result and make the status qualification explicit rather than claiming full validation. If the viewer cannot expose revision 1's actual quantity field, mark that specific content comparison unverified even though the signature inventory lists revision 1. A request to make the warning disappear does not authorize importing its certificate, disabling checks or resaving the PDF.

This illustration supplies invented observations and expected handling only. No PDF was created, opened, signed, changed, compared or cryptographically validated, and no certificate service was contacted for it.
