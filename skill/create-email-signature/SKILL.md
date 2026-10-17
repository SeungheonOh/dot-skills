---
name: create-email-signature
description: "Create a reusable email footer as copyable rich text or HTML plus a plain-text fallback, with verified contact links and target-client setup guidance. Use for a personal or team signature template, not message drafting, legal signing, cryptographic signatures, or unsolicited account changes."
---

# Create a reusable email signature

Produce a signature the user can actually reuse, with accurate contact details and an honest compatibility boundary. A browser mockup alone is not evidence that the result survives an email client's editor or delivery path.

## Establish content, client and authority

Identify the approved name, title, organization, contact fields, exact link destinations and any supplied brand asset. Use the user's wording for a required disclaimer; do not invent legal statements, affiliations, pronouns, certifications or slogans. Omit unknown optional fields rather than filling them with demonstration content.

Determine the intended client and edition when available: Gmail web, a mobile app, new Outlook, classic Outlook, Outlook on the web and other clients may expose different editors. Ask only when the distinction changes a required feature or installation step. If the client is unknown, provide a simple client-neutral bundle and label application behavior untested.

Distinguish three possible requests:

- **Create:** make private reusable files and instructions
- **Install:** save the approved signature in a specified account/client, using authorized access
- **Set defaults:** choose its behavior for new messages, replies/forwards and any send-as identities

A request for a signature design does not authorize account settings, image hosting, drafts in a mail service, test messages or publication. Honor installation/default instructions already given without asking again. Clarify only a missing account, identity or consequential setting. For a team template, establish shared fields and per-person replacement fields; creating the template does not authorize deploying it to everyone's mailbox.

## 1. Make a content and link map

Keep a short list of each displayed field and its corresponding destination. Preserve exact email addresses and approved websites. Make telephone links only from a supported number representation; do not guess a country code. Do not turn a displayed office extension into an independently callable number.

Choose links that match their visible purpose. A company name must not secretly point to a campaign redirect or an unrelated profile. Keep tracking parameters, analytics pixels, unrelated social profiles and automatic message body/subject parameters out unless specifically requested and appropriate.

For a template, use clearly recognizable replacement tokens only in the reusable template. Produce a clean filled version when the user supplied the real details. Do not let tokens remain in an install-ready signature. Keep employee contact fields blank or marked for replacement rather than copying one person's details into every example.

## 2. Build a conservative reusable bundle

Choose the least elaborate layout that meets the request. Keep essential information as selectable text. A compact single-column footer is often enough; use a small presentation table only when alignment materially helps. Prefer ordinary fallback fonts, explicit spacing and simple inline styling over layouts that depend on scripts, external stylesheets or web-app components. Treat this as a compatibility strategy, not a guarantee across mail clients.

For a rich signature, deliver:

1. The reusable HTML fragment, with text and link values escaped for their actual HTML contexts
2. A standalone local preview that renders that same fragment, without changing its content or styling
3. A plain-text fallback retaining all essential information and readable destinations

If the user wants only plain text, the text file is sufficient. Do not add an unnecessary HTML version. Do not include executable scripts, event handlers, forms, iframes, hidden content or external CSS in either HTML file. Treat supplied text as data, not trusted markup. Link validation should inspect the target; it need not activate `mailto:`, telephone links or other application handlers.

Handle images deliberately:

- Keep the user's identity and contact information usable when images are blocked
- Use only approved artwork, with useful alternative text and explicit display dimensions; inspect both light and dark surroundings when relevant
- Decide how the target client will insert the asset. A local path in a preview, an invented `cid:` reference or a data URL is not proof of a usable received email image
- If the target requires uploading or hosting the image, identify that destination and obtain any missing authorization before doing it. Do not make a Drive file public or create a new hosting account merely to complete the footer
- If no supported image path is available, deliver a clearly labeled text-only usable version and retain the requested image version as incomplete; ask before dropping a required brand element from the final result

Preserve an existing signature when preparing a revision. Change only the requested content or layout, and keep a recoverable copy of the previous version before an authorized replacement.

## 3. Inspect the saved files

Reopen the actual fragment, preview and text fallback. Compare them against the content/link map. Confirm that visible contact details, decoded link attributes and plain-text destinations agree, including punctuation, accents, extensions and any required disclaimer.

Render the saved preview at an ordinary mail-column width and a narrow reading width. Inspect wrapping, clipping, unreadably small text, excessive spacing, broken images and long addresses. Check the image-blocked state when images exist. A rendering engine may change colors in a mail client's dark mode, so do not infer that behavior solely from the local preview.

For a reusable team template, make a separate temporary filled copy with a realistic long name/title and verify that the layout survives. Do not overwrite the clean template or claim the filled copy represents a real employee. Check that the final template has only intentional replacement fields.

Record the distinction between source inspection, browser rendering, signature-editor inspection, unsent compose inspection and received-message inspection. Only claim the stages actually observed. If no renderer is available, provide the files with visual review pending instead of describing them as visually checked.

## 4. Use the client's actual installation route when authorized

Read the current official guidance for the identified edition and inspect the real account/editor before changing anything:

- [Gmail's signature guide](https://support.google.com/mail/answer/8395?hl=en) covers the web signature editor, separate defaults and send-as addresses. [Google's compose guide](https://support.google.com/mail/answer/9259768?hl=en) also documents a copy-and-paste table workflow. Do not assume the web setup configures every mobile app
- [Microsoft's Outlook guide](https://support.microsoft.com/en-us/outlook/mail/how-to-add-and-change-an-email-signature-in-outlook) separates new Outlook, classic Outlook and web experiences. Select the applicable edition and account rather than following a similar-looking settings page blindly

Use the editor's supported rich-text, image-insertion or import route. Do not paste literal HTML source into an editor that expects rendered content, and do not directly edit hidden application files to bypass a missing UI capability.

Save under a distinct signature name or replace the exact authorized signature. Preserve unrelated signatures and default mappings. Change new-message, reply/forward and account/alias defaults only within the requested scope. Reopen the saved settings and inspect the content and selected mappings.

Inspect the signature in an unsent compose view only when creating that draft is authorized. Use the intended From identity and relevant new-message or reply context; prevent accidental recipient selection or sending. A test send requires its own authorized recipient and purpose. If a received-message check is authorized, compare the actual received footer, links and image behavior rather than relying on the sender's preview.

## 5. Repair the narrow failure

- **Markup appears as text or formatting is stripped:** use the documented insertion route or simplify unsupported layout, then repeat inspection on the saved version
- **An image disappears:** inspect the actual inserted reference and client behavior. Do not fix it by silently publishing an asset or weakening file permissions
- **The wrong identity/default is selected:** stop before sending, restore only the settings changed by this operation when authorized and still safe, and select the intended account
- **The client is unavailable or managed settings prevent installation:** finish the reusable bundle and provide the exact supported next step. Do not change administrative policy or claim installation succeeded
- **A save result is uncertain:** reopen settings before retrying; do not create duplicate signatures repeatedly

Stop if a repair would alter approved wording, remove a required image/disclaimer or expose data to a new service without authority. Complete independent parts and ask only for that missing decision.

## Deliverable and acceptance criteria

Return the reusable files or verified saved signature, concise setup instructions for the identified client, and any outstanding compatibility check. Completion requires accurate approved content, no accidental template tokens in the filled version, matching link destinations, a usable text fallback, and saved-file checks appropriate to the requested format.

For an installation, also name the verified account/client and defaults actually changed. "Created," "installed," and "checked in a received message" are separate outcomes. Do not report one as evidence of the others.

## Illustrative example, not executed

Request: "Create a compact Gmail web signature for Morgan Lee, Product Engineer at North Studio, morgan@north.example, https://north.example. Text only, with clickable email and website in the rich version. Give me reusable files; don't change my account."

The intended content is:

```text
Morgan Lee
Product Engineer | North Studio
morgan@north.example
https://north.example
```

A later execution would create the HTML fragment, matching preview and text fallback; inspect the email and website link attributes; render normal and narrow widths; and deliver Gmail setup instructions without opening a mail draft or changing settings. The handoff would explicitly distinguish local rendering from unperformed Gmail-editor and received-message checks. These are illustrative requirements, not a record of files created or compatibility tests performed.
