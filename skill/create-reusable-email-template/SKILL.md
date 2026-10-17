---
name: create-reusable-email-template
description: "Create a reusable full-message email template with matching HTML and plain-text bodies, explicit content variables and checked target-client behavior. Use for a maintainable email layout and authoring handoff, not a signature, one-message EML package, mailing-list management or campaign delivery."
---

# Create a reusable email template

Deliver an editable message template that another author can populate without breaking its meaning, links or layout. Carry the same content contract through the reusable source, populated specimens, optional provider template and the email clients actually checked. A browser preview is useful evidence about that preview; it does not establish what a recipient's inbox will render.

Use [message drafting](../draft-professional-message/SKILL.md) when wording is the main task, [signature creation](../create-email-signature/SKILL.md) for a footer, and [offline email packaging](../prepare-offline-email-draft/SKILL.md) when an approved individual message needs an EML file. This workflow authors conventional HTML/plain-text email bodies, not interactive email applications, subscription policy or a sending system.

## Establish the reusable contract

Identify the message's purpose, audience, approved content and brand assets, intended authoring tool or template engine, and required receiving clients. Distinguish Gmail web from its mobile apps and classic Outlook from other Outlook editions. Ask only for a missing choice that changes a required feature or handoff; with no client list, prepare a conservative draft and leave client compatibility unverified.

Resolve what varies between uses: a title, introduction, repeated items, an optional notice, action text and destination, preview text, or recipient-specific fields. Keep exact dates, amounts, promises and required footer wording grounded in supplied material. Do not invent a mailing address, consent statement, discount, unsubscribe destination or sender identity to make the template look finished.

Determine the requested result:

- A reusable local bundle and editing instructions
- A template saved in a named provider/account, using its supported authoring route
- Particular client checks, including any separately authorized test messages

Template creation does not authorize uploading private copy or assets to a rendering service, publishing images, importing contacts, adding tracking, changing audiences, scheduling campaigns or sending messages. A test send is a real communication; establish its recipient, purpose and allowed content before sending. Inspect current service limits before using paid previews or send credits. Complete already-authorized steps without an extra approval round.

Preserve an existing template and its source assets. For provider edits, identify the exact template, current revision and whether other drafts or active messages depend on it. Prefer a separate candidate when an in-place change would affect those consumers beyond the request. Keep credentials, recipient lists and sensitive examples out of the reusable package; ordinary synthetic values normally suffice for layout checks.

## 1. Define fields, blocks and fallbacks

Make a compact replacement map. For each variable, record its name, meaning, accepted value shape, destination context, required/optional status and missing-value behavior. A small template needs only a small map.

Separate literal text, URLs and deliberately permitted rich content. Escape inserted values for their actual contexts; escaping text is not URL validation. Constrain action URLs to the approved scheme/destination rules, preserve query semantics, and escape the resulting attribute value. Do not treat a contact name, imported description or URL as template code. If rich HTML is genuinely required, use the consumer's supported restricted-content path rather than allowing arbitrary markup.

Define conditional and repeating blocks explicitly:

- Distinguish absent, empty, zero and false values when they mean different things
- Give missing optional fields an approved omission or neutral fallback; missing required facts hold the affected output
- Keep a call-to-action label and its destination together. Do not leave an attractive button pointing to a sample link when the real destination is absent
- Preserve item order and item identity across HTML and text. Establish whether an empty collection removes the section or shows approved empty-state wording
- Prevent an omitted block from leaving orphan headings, separators, empty table cells or contradictory preview text
- Specify date, number, currency and language formatting only where needed; do not infer a reader's locale from their name

Bind placeholders to the selected engine's actual syntax and escaping rules. Check whether the engine handles the subject and preview text separately from the body. If no engine is selected, deliver plainly labeled replacement tokens and a replacement map, not a purportedly import-ready provider template. Keep an unpopulated master separate from every filled specimen.

For subscription or preference controls, retain the approved provider-managed fields and explain their required rendering context. A fabricated static unsubscribe link is not a functioning preference mechanism. Body links alone do not establish required mail headers, recipient consent or legal compliance; leave those transport and policy checks with the sending workflow.

## 2. Build a message that degrades usefully

Use the existing permitted authoring tool or compiler when it fits; a simple message does not need a new framework. Preserve editable source and, where compilation or CSS inlining is involved, identify the actual tool/version and the reproducible authoring step. Inspect supplied build steps before running them so template preparation cannot silently publish assets or send mail.

Choose a modest content width and a narrow-screen arrangement that keeps the message readable without depending on every CSS enhancement. Keep essential words and actions as real text, with useful headings, link labels, image alternatives and a coherent reading order. Layout tables should be marked as presentational when appropriate; genuine data tables retain their header relationships. Avoid duplicating essential content into separate desktop/mobile versions unless the actual consumers can be checked for duplicate reading and inconsistent substitutions.

Use supported email styling, explicit image dimensions and sensible font fallbacks. Do not assume browser layout features work unchanged in mail clients. [Gmail's CSS reference](https://developers.google.com/workspace/gmail/design/css) documents its supported selectors, properties and media queries. [Microsoft's rendering guidance](https://learn.microsoft.com/en-us/troubleshoot/dynamics-365/customer-insights/journeys/email/email-troubleshoot-rendering) explains classic Outlook's different HTML processing and spacing limitations. Apply only relevant workarounds and inspect the resulting client behavior; a large collection of conditional hacks is not evidence of compatibility.

Keep scripts, event handlers, forms, iframes and executable attachments out. An email action should be a clearly described link to the established task destination, not a decorative web control that cannot work in the inbox. Do not introduce remote fonts, tracking pixels or link rewrites merely to make the template look like a marketing campaign.

Handle images as a delivery dependency:

- Preserve the original assets; list the selected filename/revision, intended dimensions, alternative text and final reference strategy
- Use approved hosted URLs or the target's supported embedded-resource mechanism. Local file paths, unbound Content-IDs and data URLs in a preview do not establish recipient-visible images
- Keep the main purpose and action understandable with images blocked. Decorative imagery may disappear; required information cannot exist only inside it
- A provider import can upload bundled assets and replace references. [Mailchimp's import guidance](https://mailchimp.com/help/import-a-custom-html-template/) documents this behavior and its package requirements. Inspect the chosen route's actual effects and obtain missing upload authority before using it

Treat preview text as reader-facing copy even when visually hidden in the body. It can appear in inbox listings or become visible when styling is stripped. Never place private notes or secrets there. Keep it consistent with each populated branch and inspect an empty or unsupported-preview case without filling the template with excessive hidden padding.

Author the plain-text alternative from the same content decisions, with readable headings, spacing and explicit destinations. Preserve the same important facts, item order, actions, qualifications and required footer content. Removing tags mechanically may lose image text, button URLs or conditional structure; inspect the actual text result.

## 3. Populate representative specimens and inspect saved output

Choose a few synthetic cases that expose this template's real boundaries: a normal message, long or non-ASCII text, an omitted optional block, the longest supported item collection, and a missing required value. Exercise each distinct content branch without constructing a combinatorial test project. The missing-required case should remain held, not become a plausible complete message.

Use the actual selected templating route for populated specimens when available. Preserve the clean source. Reopen the saved HTML and text after compilation/inlining; do not inspect only a source preview that differs from the artifact the provider receives.

Check that:

1. Every intended variable resolves or is an explicitly documented provider-managed field; no stale personal/sample values or unintended template tokens remain
2. Each block follows the agreed condition, and HTML/text facts and links agree for the same specimen
3. Parsed destinations match the approved link map after substitution; inspect tokenized or action-bearing URLs without activating password resets, unsubscribe actions, confirmations or other state-changing endpoints
4. Required text survives the rendered layout, including the footer, long content and image-blocked state; no essential content depends on a clipped region
5. Assets and references belong to the candidate revision, with no accidental local paths, private file links or unauthorized tracking

A source-only structural check can help find malformed nesting or duplicate references, but it does not establish client rendering. For an offline preview, prevent automatic remote-resource loading unless that access is permitted. Inspect ordinary and narrow widths, text enlargement where supported, and available light/dark appearances. Record which are browser simulations and which are actual client observations. Do not infer a mail client's color transformations from a browser's dark background.

Keep template expansion, provider preview and received-message checks separate. [Mailchimp's preview documentation](https://mailchimp.com/help/preview-and-test-your-email-campaign/) notes that contact-specific merge tags do not resolve in ordinary test emails and that its link checker does not cover every link or custom-template route. An unresolved test token therefore needs a documented rendering-context check, not an invented success or an unauthorized live campaign. Use supported synthetic preview data when available; otherwise retain that exact verification gap.

## 4. Save to a provider only within scope

If the user requested a provider template, use the documented template-save/import operation in the verified account. Confirm that it is separate from audience selection, campaign activation and sending. Do not follow a tutorial's later send steps simply because they follow import instructions.

Before replacing an existing template, freshly read its ID, revision/activity and relevant dependencies. Reconcile concurrent edits; use conditional updates where supported. If no conflict guard exists, recheck immediately before saving and disclose the remaining concurrency limit. Do not overwrite another author's changes or an active shared template under the assumption that the saved source is still current.

Reopen the saved template by its ID. Compare its actual content, variable syntax, assets and generated body with the candidate, including provider-added footers or changed links. Distinguish an editable-template preview from a rendered message. If a test send was specifically authorized, use only the approved account, recipient and content, inspect available send/received evidence, and stop before any broader distribution.

## Recover and deliver

Fix defects in the reusable source or mapping, then regenerate affected specimens; do not patch only the pretty preview. After a compilation, inlining or provider transformation changes the artifact, repeat the checks affected by that change. A layout correction must not silently remove required wording or a required brand element.

If an image route or client feature is unsupported, offer the smallest compatible candidate and identify any material design tradeoff. Hold required features rather than silently weakening them. If a provider save or test send returns an uncertain result, inspect existing state or delivery evidence before retrying. Retry a send only when evidence establishes that it was not submitted or a supported duplicate-safe mechanism applies; otherwise report its outcome as unverified. Never resend merely because the recipient view is slow. Restore a prior template only when authorized and after checking that rollback would not overwrite newer work.

Deliver the editable template, any compiled HTML, matching text alternative, selected asset/reference list, replacement rules and concise compatibility record. Include filled specimens when they help the next author; keep them unmistakably synthetic and separate from the clean master. For a provider save, include the verified template location and observed state.

Acceptance means the reusable source and actual outputs agree, required content and destinations survive supported substitutions, missing facts are held, and the available checks meet the requested delivery boundary. State unchecked clients or branches precisely. A local bundle can be complete as an authoring handoff while client acceptance remains pending; it must not be called universally compatible, delivered, or ready for an unreviewed campaign.

## Fictional illustration, not executed

A fictional team wants a reusable workshop-update email with a title, two to five agenda items, an optional room-change notice and a registration link. The approved notice appears only when `room_changed` is true. The target clients are Gmail web and classic Outlook; no provider upload or send is requested.

The proposed handoff contains a clean HTML master, a matching text master, replacement rules and two populated specimens: one with a long title and five items, and one with no room-change notice. A third input lacking the required registration URL is held; neither body receives a sample destination. All illustrative links use `https://workshop.example/`.

The intended checks would compare item order and notice conditions in both alternatives, inspect narrow-width and image-blocked layouts, and record actual client checks separately from browser previews. If classic Outlook is unavailable, that client remains unverified. This is an invented preparation and acceptance scenario: no template was compiled, file rendered, provider changed, image hosted or email sent for this illustration.
