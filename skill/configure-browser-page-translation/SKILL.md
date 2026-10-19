---
name: configure-browser-page-translation
description: "Set up built-in desktop browser page translation for a bounded reading task, reconcile language and site rules, verify actual text coverage, and preserve a route back to the original. Use for everyday translated browsing, not authored translations, audio captions, OCR or changing the browser's interface language."
---

# Make translated browsing usable and reversible

Deliver the requested page-reading setup, its exact translation scope and a short original/translated-view reference. Distinguish a saved preference from an observed translated page and from verified meaning. A translation icon or fluent paragraph does not prove that the entire page was translated correctly.

This guide provides a desktop Firefox route and a public-page Chrome route using existing native features. Other browsers need their own current official controls and data-processing evidence. Use [translation-release-review](../translation-release-review/SKILL.md) for a durable reviewed translation artifact, [configure-native-live-captions](../configure-native-live-captions/SKILL.md) for incoming speech, and [configure-separate-browser-profile](../configure-separate-browser-profile/SKILL.md) for a new retained browsing context. None is an automatic part of this setup.

## Establish the reading scope

Resolve only what affects the next step:

- Actual computer, browser/version, active profile and any management restrictions
- Intended page or site, source language and desired reading language; distinguish a regional variant when it matters
- One page on demand, selected passages, automatic translation for a language, or an exclusion from unwanted translation
- A harmless public sample, plus the actual page type that must work: ordinary article, dynamic page, mixed-language text or authenticated content
- Existing language/site rules, browser interface language and relevant translation extensions
- Whether the request is a plan or an authorized configuration and check; the desired ending state

Do not infer the user's fluency or change their system language. A webpage's own language selector, the browser's interface language, website-language preferences and machine-translation target are separate controls. Identify which layer currently produces the displayed text. A website serving its own English edition is not evidence that browser translation works.

Without target-browser access, deliver a source-matched plan and name the checks left to the user. Another browser session cannot establish the requested profile's settings. Preserve unsaved forms and ongoing work; do not reload a live application merely because a help page suggests refreshing after translation fails.

## 1. Resolve processing and first-use effects

Use current official documentation and the actual version's visible controls. The sources below were inspected on 2026-10-19; language availability and settings labels can change.

Mozilla's [translation feature explanation](https://www.firefox.com/en-CA/features/translate/) describes downloaded language models and local translation. That processing claim does not make the website itself offline or private. Existing extensions, browser services, screen sharing and the source site's own requests remain separate. Check whether the needed language resources are already present before promising a no-download session.

For any service-backed route, establish the translation provider, content sent and applicable authority before processing private content. The Chrome route below is limited to non-sensitive public sample pages; its configuration instructions are not a verified privacy assessment for private accounts. A request to make pages readable does not authorize sending private messages, personal records or confidential work to a new service. If processing behavior is unknown, hold that page rather than experiment on it. Do not paste private text into a public translation website as a workaround.

A request for scoped translation preferences covers those ordinary settings. New software, language-component installation, unexpected permissions, browser sign-in, sync changes and external feedback submissions retain their own approval requirements. Explain a required first-use download before triggering it. Do not replace a disabled native feature with an extension or change management policy to evade a restriction.

Automatic translation is broader than a one-page action. For a service-backed implementation, future processing also requires appropriate standing data-sharing authority; a setting labeled “always” is not that authority. If the requested scope is only one site but the product offers a language-wide rule, use manual translation or ask about the wider scope. Do not silently translate every future page in that language.

## 2. Identify the applicable controls

Record only affected before values: active profile, translation availability, target language, language-level automatic/never rules, relevant site exception and installed resources. Preserve unrelated language preferences and exclusions.

### Firefox

Mozilla's [Firefox translation guide](https://support.mozilla.org/en-US/kb/website-translation) documents the toolbar or menu translation panel, source/target selection and Show original. It also describes language-wide automatic translation, language/site exclusions and installed-language management. First use can install language data automatically. Check the installed version's settings layout rather than assuming every release exposes the same panels. Mixed-language pages and non-text content have limits; consult current supported translation directions before promising a pair.

Use those controls to inspect the relevant exception before removing it. A missing toolbar icon does not alone prove that translation is unavailable; inspect the native menu route. If the actual version exposes an AI Controls gate, inspect that state without broadening other AI settings. Respect a managed or deliberately blocked feature.

Mozilla's [technical overview](https://firefox-source-docs.mozilla.org/toolkit/components/translations/resources/01_overview.html) distinguishes source-language detection from translation and explains directional models and possible pivot translation. A language appearing somewhere in a list does not establish every requested direction. Do not infer identical quality across pairs or use a developer test page as a substitute for the everyday page-reading path.

### Chrome: public pages

Google's [desktop translation guide](https://support.google.com/chrome/answer/173424?hl=en&co=GENIE.Platform%3DDesktop) documents the address-bar/context-menu action, selected-text translation, and Settings > Languages > Google Translate controls. These include the translation target, automatically translated languages and languages never offered for translation. Preferred website languages and Chrome's interface language are separate choices. Use the current panel to inspect the original-language return route before the sample.

Keep this route to public non-sensitive pages unless a separate provider/data review and authorization establish the private-content path. Do not enable account saving, install the Google Translate extension, or reorder website-language preferences merely to change the translation target. If the browser lacks the exact requested site-specific behavior, report that limit rather than invent a rule or modify the site.

## 3. Translate one page before making a persistent rule

Start with an approved public article containing ordinary selectable text and a clearly identifiable passage. Keep the original URL and a small source locator, such as a heading. Avoid retaining a whole article or private browsing history as setup evidence.

1. Confirm the original view and whether the displayed source language is correctly identified. Where supported, correct a mistaken source selection rather than changing the browser's global language.
2. Select the desired target and invoke only the bounded page or passage action. Observe completion or the specific error. Do not interpret a successful button click as completed translation.
3. Inspect the intended heading and paragraph in the rendered page. Check that the target is the requested language and the content is genuinely new translated text, not an old overlay or the website's alternate edition.
4. Compare a few meaning-bearing details with the original: a quantity, a negation or exception, and a named item where present. Record a material discrepancy rather than smoothing it over. If competent comparison is unavailable, report that text appeared while meaning remains unverified.
5. Inspect the parts the user actually needs. Identify text in images, video, embedded documents, frames, collapsed panels or subsequently loaded regions separately. Do not assume the main article's success proves those regions work. Reveal or navigate only harmless, authorized content.
6. Return through the native original-view control and confirm the source passage is restored. Re-enter translation if it is the desired ending view. Returning to original is not proof that a stored automatic rule was removed.

Do not submit a form, accept terms, place an order or act on a consequential translated instruction as part of the check. Browser translation is a reading aid, not a certified interpretation. Resolve important medical, legal, financial or safety wording against an authoritative original or suitable reviewer before relying on it.

For dynamic content, check one representative harmless update only if it is part of the task. Distinguish already translated content from new untranslated text. Do not inject text into the page or replace its DOM to manufacture a successful result. If images contain the required text, report the OCR/translation need separately rather than claiming page translation covered it.

## 4. Apply the narrow rule and check its effect

After the one-page path works, apply only the requested persistent preference. Record its exact scope: this site, this source language, target language, or offering behavior. An option that stops suggestions may differ from a prohibition on manual translation; describe the actual product behavior rather than calling every exclusion a block.

Read back the saved value, then revisit a harmless page within the rule's scope without risking unsaved work. For an automatic rule, check whether translation actually occurs without another manual action. For an exclusion, check the intended absence of automatic translation or prompts. Where safe and relevant, use one public page outside the scope to detect an accidentally broad rule. Do not visit a private account to prove an exclusion.

If rules conflict, compare the relevant site and language entries before changing either. Do not remove all exclusions or reset the browser. Keep a user's deliberate exception unless the requested change includes it. If behavior remains inconsistent, record the exact page, source/target, saved rules and observation; stop guessing at precedence.

| Observation | Bounded response |
| --- | --- |
| Translation control is missing | Check native menu, actual version, feature availability and supported direction |
| Wrong language is detected | Inspect the source selection and mixed-language content before retrying |
| Manual translation works but automatic behavior does not | Check the active profile and relevant language/site rules |
| Only part of the page changes | Identify content type, loading boundary and required untranslated region |
| Rule saves but reverts | Inspect management or profile state; do not bypass policy or enable sync |
| Resource download fails | Retain the error and supported deployment requirement; avoid unofficial models |
| Translated controls become ambiguous | Return to original before any action; do not guess from changed labels |

Restore a failed temporary change to its recorded prior value only after checking for intervening user edits. Do not clear cookies, delete language resources, remove extensions or create a fresh profile as generic recovery. Preserve the useful manual path when a requested persistent rule remains blocked.

## Handoff and acceptance

Return a compact record:

- Browser/profile and intended source-to-target reading task
- Exact old-to-new rules, their scope and any first-use component decision
- Observed page/passage coverage, meaningful errors and user-reported readability
- How to translate on demand and return to the original; final current view and stored-rule state
- Prepared, saved/read-back, page-observed and meaning-reviewed evidence kept separate
- Missing regions, privacy review, language support or persistence checks

Finish when the requested reading path and rule behavior are checked, a usable plan is ready, or a specific missing capability or authorization blocks progress. A successful article does not certify all sites, future visits or translation accuracy. Do not export, publish or send a translated copy unless separately requested.

## Fictional illustration, unexecuted

A fictional user wants English reading of one public Spanish reference site in their existing Firefox profile, with no new downloads and no language-wide automatic rule. Supplied fictional settings show the required resources already installed and an existing site exclusion.

The proposed workflow first clarifies that changing the selected site's exception is in scope, then uses a manual page translation. It checks a paragraph containing “not before 15:00,” distinguishes a diagram's unchanged labels from translated article text, and returns to the original. If the browser only offers automatic translation for all Spanish pages, that option does not meet the one-site request. The result would retain an on-demand route and identify the diagram's separate need rather than broadening the rule.

If supplied hypothetical output instead reads “before 15:00,” the rendering path may work but the meaning check fails. The guide would preserve that discrepancy and prevent reliance on the translated timing instruction. No browser, page, preference, resource download, translation engine or live check was operated for this authored illustration.
