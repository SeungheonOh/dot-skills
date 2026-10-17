---
name: create-contact-card
description: "Create a portable .vcf contact card from approved contact details, preserving field meanings and verifying the saved serialization. Use for a digital business card or a small named contact bundle, not address-book cleanup, bulk migration, or automatic importing."
---

# Create a portable contact card

Deliver the actual vCard file and a readable summary of what it contains. The important result is a contact that a recipient can interpret correctly, not a screenshot of a business card or a renamed text file.

## Establish the card's scope

Use the request and supplied facts to identify:

- The person or organization represented, approved display name and fields to include
- Whether this is one card or an explicitly named bundle, and the intended receiving application when known
- Required format/version, filename and private delivery location
- Whether the task ends with creating the file or includes a specifically authorized import or sharing action

Do not mine a whole address book to enrich a small card. An existing export is evidence, not permission to copy every note, birthday, home address, photograph or internal identifier. Select only the requested fields. Keep credentials and authentication links out of the card. Ask only when an unresolved identity, required value or target requirement changes the result.

Prefer the receiving application's documented format when one is specified. Otherwise, create an explicitly identified vCard 4.0 candidate and state that application compatibility still needs checking. Do not claim universal compatibility or produce several competing versions without a reason. A `.vcf` extension alone does not identify the version.

## 1. Map facts before serializing

Make a small field map, in working notes or the handoff: source value, intended contact property, label, and any representation change. Separate the display name from structured name components. Do not infer a family name from the last word of an unfamiliar name; preserve the supplied display name and resolve a structured name only when needed.

Keep these distinctions visible:

- A person's role and their organization are different fields
- Two supplied emails or phone numbers remain separate, correctly labeled values; do not choose a preferred one without evidence
- An extension is not part of a country's calling code. Do not add a guessed country code or discard leading zeros to make a number look international
- An office address is not a home address. Preserve supplied address components without inventing a region or postal code
- A missing optional field is omitted, not filled with a plausible value or the word "unknown"

Retain exact spelling, accents, email addresses and approved URL destinations. Flag inconsistent source values rather than silently selecting one. For a bundle, maintain a one-to-one mapping between the approved identities and card records; shared names or phone numbers are not sufficient grounds to merge people.

## 2. Write a version-correct file

Use an available version-aware serializer when practical, inspecting its supported vCard version and field mappings. A library that accepts a value may still serialize it into a field the receiver ignores. Do not install software or use an online generator without the authorization that action requires.

For vCard 4.0, use UTF-8, CRLF line endings, `BEGIN:VCARD`, an immediately following `VERSION:4.0`, the required `FN`, and a final `END:VCARD`. Fold long content lines at no more than 75 octets without splitting a multibyte character. Keep structured property separators distinct from literal text, and apply the escaping rules for the actual property type. See [RFC 6350, sections 3 and 6](https://www.rfc-editor.org/rfc/rfc6350.html#section-3).

Treat source strings as values, never as raw content lines. An embedded newline must not inject an additional property or card. Parameter values have different encoding rules from property text; use [RFC 6868](https://www.rfc-editor.org/rfc/rfc6868.html#section-3) when parameter quoting or special characters are relevant. For telephone URIs, follow [RFC 3966](https://www.rfc-editor.org/rfc/rfc3966.html#section-3), including its handling of local-number context and extensions. If that representation cannot be established, resolve the ambiguity or use an explicitly supported text representation instead of fabricating a callable number.

If the target requires vCard 3.0, generate a separate candidate under [RFC 2426](https://www.rfc-editor.org/rfc/rfc2426.html); do not just replace the version line. Its required properties and value/parameter rules differ. Preserve the user's facts through any conversion and report fields that cannot be represented or supported.

Avoid unrequested remote-photo references, embedded attachments, custom vendor properties and source-account identifiers. Preserve a supplied stable UID when this is an authorized revision of the same card; do not copy a different person's UID or assume an import will update rather than duplicate an existing contact.

Save to a new `.vcf` candidate, keeping any original card intact unless replacement was requested. Supply a UTF-8 readable summary containing the same approved fields when useful for review; that summary does not replace the machine-readable file.

## 3. Reopen and compare the saved bytes

Read the actual saved file with a version-aware parser, preferably a different implementation from the writer when available. Compare decoded properties with the approved field map, not just the serialized lines or the parser's success result.

Check:

1. The intended number of cards, version, boundaries, required properties and absence of unintended extra properties
2. Exact decoded names, accents, emails, URLs and all repeated values with their labels
3. Structured-field associations, phone extensions and any explicitly chosen preferred value
4. Correct line endings, valid UTF-8, folding/unfolding and escaping, including any long or punctuation-bearing value actually present
5. No private fields carried over from an export, unresolved placeholders, local file references or unapproved remote dependencies

A parser-only check proves neither address-book presentation nor import behavior. If the target has a genuinely non-mutating preview, inspect it without activating links or accepting an import. Otherwise, report target application behavior as untested unless the user authorized that import into a named account or isolated destination.

Do not double-click a card and assume the result is read-only. [Apple's Contacts instructions](https://support.apple.com/en-gb/guide/contacts/adrbk1457/mac) describe opening a vCard as an import route, and [iCloud's import instructions](https://support.apple.com/guide/icloud/import-export-and-print-contacts-mmfba748b2/icloud) state that imported cards become contacts. Do not change account sync settings or import live contacts just to validate a file.

## 4. Recover without losing fields

- **Serialization fails:** preserve the original and fix the specific encoding, property or required-field error in a new candidate; repeat saved-file comparison
- **A reader drops or relabels a field:** determine whether it is a version or target limitation. Offer a supported representation or disclose the loss; do not hide information in an unrelated field to force acceptance
- **No compatible parser or preview is available:** deliver the candidate and readable summary with the exact unperformed checks; do not call it import-verified
- **An authorized import times out or reports duplicates:** inspect the destination's actual records and receipt before retrying. Do not reimport the whole bundle or merge/delete existing people automatically

## Deliverable and completion

Return the `.vcf`, the included-field summary, chosen version, checks actually completed and any target-specific limitation. For a bundle, account for each requested identity and each withheld card. File creation is complete when the saved content matches the approved fields; importer compatibility remains a separate claim requiring its own evidence.

Share, upload or import only when that destination, data and action are authorized. A request to make a downloadable card does not authorize publishing it, adding it to a shared address book or sending it to colleagues.

## Illustrative example, not executed

Request: "Make a vCard 4.0 file for Léa Park using these work details. Given name Léa, family name Park, organization River, Lab, email lea@river.example, website https://river.example/lea. Leave out phone numbers and personal details. Give me the file, without importing it."

An illustrative serialization is:

```text
BEGIN:VCARD
VERSION:4.0
FN:Léa Park
N:Park;Léa;;;
ORG:River\, Lab
EMAIL;TYPE=work:lea@river.example
URL:https://river.example/lea
END:VCARD
```

The actual file would need CRLF endings, including after the final line. A later execution must reopen the saved file and establish that the decoded organization is `River, Lab`, the name components are correct, there is exactly one card, and no phone or personal fields appeared. This example is an unexecuted specification; it is not evidence that a file was produced, imported or accepted by a particular application.
