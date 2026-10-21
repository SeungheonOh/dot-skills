---
name: prepare-security-contact-file
description: "Prepare or update a website's security.txt vulnerability-reporting contact file, with approved destinations, expiry, host coverage and publication/signing handoff. Not a vulnerability scan, disclosure-policy authoring or authorization to test systems."
---

# Prepare a security contact file

Deliver the actual `security.txt` candidate and a concise deployment and renewal handoff. The outcome is a maintained route for reporting vulnerabilities, not a decorative security badge or a generic contact-page template.

[Website creation](../build-usable-website/SKILL.md) builds a site; [crawl-policy preparation](../prepare-robots-crawl-policy/SKILL.md) controls voluntary crawler behavior; [link-sharing metadata](../prepare-link-share-metadata/SKILL.md) describes pages to preview consumers. This workflow owns security-report contact discovery for an existing site. It does not scan the site, submit a vulnerability, create a mailbox, promise a bounty or write a new legal disclosure policy.

## Establish who can receive reports

Identify the requested host or hosts, existing file and owning source, approved reporting destination, responsible team, intended publication date and output location. Distinguish preparation from authorized publication. For an update, retain the current bytes and revision, including any signature, before proposing changes.

Do not infer a monitored mailbox from the conventional name `security@`. Obtain an explicit owner-provided destination or current approved policy evidence. A reachable contact page does not establish that someone triages its submissions. Record separately what is known about the destination's ownership, availability and actual response process. Ask only for missing facts that block a truthful candidate.

Prefer an approved team endpoint over an employee's personal address when that is the organization's choice. Publishing contact information makes it public: do not expose internal incident channels, ticket links, private staff details or credentials. Keep ownership evidence and internal renewal notes outside the candidate.

## Apply the format without inventing policy

The [project's field reference](https://securitytxt.org/) identifies required `Contact` and single `Expires` fields. Use URI-valued contacts: `mailto:`, `tel:` or HTTPS. Optional `Encryption` points to a public key; `Policy` points to an existing disclosure policy. `Preferred-Languages` is one comma-separated language-tag list. `Canonical` identifies file locations. OpenPGP cleartext signing is supported. Do not fill optional fields merely because a generator displays them.

The normative [RFC 9116](https://www.rfc-editor.org/rfc/rfc9116.html) adds important boundaries:

- Serve UTF-8 plain text with `Content-Type: text/plain; charset=utf-8` through HTTPS at `/.well-known/security.txt`; that location takes precedence over a legacy root copy. End each line with LF or CRLF.
- Order repeated contacts by preference. Use one RFC 3339 expiry timestamp; less than a year ahead is recommended.
- Host scope does not automatically include parent domains or subdomains.
- If `Canonical` is present, a retrieval URI absent from that list should not be trusted; listing several canonical URIs alone does not authenticate them all.
- `Encryption` contains a key URI, not key material; its key is not necessarily the signing key.
- The file's presence or absence does not grant or deny permission for security testing.

Keep an existing approved policy link, but do not silently change its terms, eligible targets, safe-harbor language, response deadlines or payment commitments. If those conflict with the requested contact change, flag the conflict and hold the dependent publication. A contact-file task is not authority to establish an organization-wide disclosure program.

## Prepare the source and host map

For each requested host, map the candidate to its exact intended HTTPS endpoint and the source/template responsible for serving it. A file in a repository root is not evidence that the host serves the well-known path. Inspect the project's deployment conventions without changing routing, access controls or unrelated configuration incidentally.

Keep apex, `www`, service subdomains and vendor-hosted reporting portals distinct. Do not claim coverage for every company hostname from one prepared file. When an approved redirect or shared contact service is involved, record the initiating and final destinations and reconcile the canonical values instead of copying a corporate template unchanged.

Compare all known copies. Retain a single maintainable owner rather than leaving independently edited legacy and well-known files to drift. If a root-path redirect is proposed, identify it as a separate integration change, not an effect of adding the text file.

Choose expiry from the intended publication window and the owner's ability to review it. Put the renewal owner and proposed review date in the handoff, not in speculative public promises. Do not extend an expired file merely to make a checker happy: first reconfirm its contacts, policy and key references. Recommend a reminder when useful, but do not claim one was scheduled without an authorized, confirmed setup.

## Preserve the signing boundary

For an already signed file, separate the proposed unsigned content from the retained original. Do not edit contact text inside an old signature wrapper and hand it back as signed. Explain that the changed candidate needs the organization's approved signing route before it can replace the signed version.

Do not request private signing keys in chat, create a new organizational key or strip the existing signing requirement to finish faster. Supply the finalized content and intended canonical locations to the authorized signer. After a signed artifact is returned, compare its represented content with the approved candidate and record only verification actually performed. A syntactically plausible signature block is not evidence of signing or signer trust.

## Inspect the saved artifact and deliver

Reopen the saved candidate. Check contacts against their approval evidence, expiry against the intended release date, field multiplicity, URI schemes, line endings and the mapped host locations. Confirm there are no placeholder destinations or private notes. Inspect any changed values against the before-state so unrelated supported fields are not discarded.

Use a compatible local parser only when available and authorized; report source inspection separately from parser results. File syntax cannot establish that a mailbox receives reports. Do not send test mail or submit a form merely to validate preparation. A separately requested delivery test needs an approved recipient, harmless payload and observed result.

For authorized publication, first compare the latest source revision, then use the established narrow publishing route. Inspect the actual endpoint's status, content type, body and redirect destination. An HTML fallback with status 200 is not the file. Record the time and final bytes inspected; if publication is uncertain, read back before retrying and preserve newer edits.

Return:

- The candidate and any exact integration change, identifying unsigned or signing-pending state
- The host-to-endpoint/source map, with uncovered requested hosts held explicitly
- Confirmed destination ownership, expiry and renewal handoff without claiming an untested response process
- Checks performed, remaining signing/delivery dependencies and the next responsible action

Finish at the requested preparation or publication stage. Do not begin security testing, contact third parties or introduce ongoing monitoring as an incidental extension.

## Fictional illustration, not executed

A studio asks for a candidate for `studio.example`. It supplies an approved reporting portal and confirms a review owner. Its old root-path file names a departed employee; `shop.studio.example` is operated separately.

The proposed candidate points to the approved portal and has one future expiry chosen for the planned release. Its deployment map targets the apex well-known endpoint. The shop host remains outside the coverage claim pending an owner decision. The handoff identifies the obsolete root copy and any proposed redirect rather than pretending the new source file removes it. If the old artifact was signed, the replacement stays signing-pending until that step is actually completed.

This is an authored scenario only. No parser, signature operation, endpoint check, message, deployment or live workflow was executed for this guide.
