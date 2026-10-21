---
name: prepare-web-font-package
description: "Prepare authorized font files, a bounded character/feature repertoire and matching CSS as a reusable self-hosted web-font package, with separate asset, rendering and fallback evidence. Use for font delivery or subsetting, not desktop installation, typeface design, general site creation or automatic publication."
---

# Prepare a self-hosted web-font package

Deliver the intended font faces, integration CSS, required notices and a small specimen that makes missing characters, wrong face selection and fallback visible. Preserve the source fonts and explain what future content would invalidate a subset. A smaller font file is not useful if the site silently renders important text in another font.

Use [character-coverage auditing](../audit-font-character-coverage/SKILL.md) for mapping evidence alone, [desktop installation](../install-desktop-font-family/SKILL.md) for local application availability, and [website creation](../build-usable-website/SKILL.md) for a complete site. This workflow produces a portable font delivery unit; it does not redesign typography, purchase rights, install fonts system-wide, invent a font converter or deploy to production.

## Establish the delivery boundary

Resolve only choices that change the package:

- Exact supplier/source files and version, included permissions, required family/weights/styles and any variable-font axes
- Intended website or recipient, supported browsers, asset base path and same-origin or approved cross-origin hosting
- Content that must work: fixed published copy, translated UI, generated values, user-entered text or future editorial content
- Features that matter, such as joining, marks, ligatures, tabular figures or stylistic alternates
- Whether the request permits conversion/subsetting or only packaging existing webfonts
- Allowed local tools, specimen/rendering checks, output location and whether integration into an existing site is requested

Prefer supplied official webfont assets when they meet the requirement. Do not convert a desktop file merely because it exists. A package-only request does not authorize changing a live site's font provider or sending its text to an online optimizer. If rights, assets or browser access are unavailable, distinguish a decision-ready plan from built or rendered assets.

## 1. Establish which bytes may be delivered

Record each selected source's identity, face metadata and permission source. Keep actual notices with the package; a filename or a font's appearance cannot establish its provenance. Do not extract restricted fonts from another site's requests or a PDF to obtain a missing source.

Check the supplied license for the actual hosting, modification and redistribution use. Desktop availability is not evidence of web-use rights. For OFL fonts, the [official FAQ, section 2](https://openfontlicense.org/ofl-faq/), distinguishes unchanged WOFF/WOFF2 compression from modification and treats subsetting as modification. Reserved Font Name conditions can therefore matter. Check the particular font's notices and any explicit naming permission; do not assume every OFL font has reserved names or that all conversion tools preserve an unmodified font. Unresolved rights or naming requirements block the affected derivative, not independent inventory work.

Preserve original files unchanged. Keep candidate outputs in a new directory, with source-to-output correspondence. Do not strip notices, rename internal records to conceal origin, or claim the surrounding project's license relicenses a bundled font. Required lawful renaming must be deliberate and checked in both font metadata and integration references.

Keep private content out of distributable samples and command logs. Use approved public copy or a synthetic specimen. Installation of conversion dependencies, uploads to third-party tools, new hosting services and publication remain separate actions with their applicable authorization.

## 2. Choose a repertoire that survives ordinary use

Separate the exact current sample from the promised future population. A title containing twelve unique letters may justify a fixed-title subset; it does not justify the font used for search results, customer names or a CMS editor. For open-ended text, retain an appropriately broad authorized distribution or agree on a fallback contract instead of pretending today's crawl is complete.

Build the selected repertoire from the actual content sources within scope. Include relevant punctuation, spaces, accented letters, combining sequences, currency signs, numbers, translated states and generated messages. Keep original sequences and normalization differences visible. Do not transliterate names, normalize application data or discard unsupported characters to reduce the set.

For each required text class, decide whether it must use the packaged font, may use a named fallback, or remains unsupported. Separate missing source coverage from characters removed by subsetting. If the original lacks a required character, optimization cannot create its design; obtain an approved face or explicitly accepted fallback instead.

Partition only when the delivery benefit justifies additional CSS and checks. Start with fewer files. Do not split an indivisible shaping requirement across arbitrary chunks merely to balance sizes. A scalar mapping audit cannot establish complete clusters, joining or stylistic features. Preserve a specimen for those requirements and use the original authorized face as a comparison reference, not as an assumed infallible result.

Keep a compact repertoire record: source of the selected text/ranges, intentionally broader coverage, feature requirements, exclusions and the change trigger. New locales, newly editable fields, changed copy or changed typography can require regeneration and review.

## 3. Produce one candidate without sacrificing behavior

Use an existing trusted tool with documented support for the selected font type. Inspect its version and effective options before transformation. Record the actual invocation when run, input identity, requested character/feature selection and output destination. Do not run supplier scripts or an unfamiliar build system merely to package a font.

[FontTools' subset reference](https://fonttools.readthedocs.io/en/latest/subset/index.html) documents WOFF2 output and its Brotli dependency. Its missing-Unicode default can ignore requested absent characters; use an explicit strict policy or independent missing-character accounting. Keep layout closure enabled unless a justified alternative is established: preserved features can require additional glyphs beyond directly requested characters. The default feature selection is not every optional feature; specify required alternates deliberately. Review metadata preservation rather than trusting size reduction alone. Do not use blanket table removal or disabled layout closure as routine optimization.

For this workflow, leave variable axes and their ranges intact unless axis reduction was explicitly part of the agreed transformation. Prefer an official supported static face when the consumer needs one. Treat axis instancing, color-font conversion and unsupported collections as distinct unresolved transformations rather than guessing settings.

After transformation, inspect the candidate's real container, names, faces, required coverage, notices and relevant features using supported tools. Reconcile all intended faces against outputs. Keep failed and partial outputs out of the deliverable directory. Compare file sizes only after functional checks; report input and output units and bytes without inventing page-speed gains.

If a command fails or its outcome is uncertain, inspect the exact candidate before retrying. Do not overwrite a prior accepted package or repeatedly process a broken source. Preserve the source, observed failure and unresolved capability.

## 4. Bind CSS to the actual delivered files

Give the package a small explicit asset map: output filename, intended face/style/weight or supported variable range, character selection and CSS rule. Use paths relative to the delivered stylesheet or the agreed site asset base, and keep case consistent. Avoid placeholder URLs and undeclared remote providers.

The [CSS Fonts Level 4 working draft](https://www.w3.org/TR/css-fonts-4/) defines face descriptors separately from element styling; verify required features in the target browsers rather than assuming draft coverage implies implementation. Match each rule to the supplied face rather than declaring one Regular file as every weight. A unicode-range declaration limits use; it does not add glyphs. Effective coverage intersects that declaration with the font's character map. Overlapping rules with matching face descriptors have ordering consequences. Keep intended overlaps explicit and inspect which resource actually serves them. For exact-file checks, omit a local-source shortcut from the specimen so an installed copy cannot satisfy the request instead.

Choose the loading/fallback policy for the reading task, not solely for a performance score. The same specification's font-display behavior controls loading-time presentation; it does not guarantee identical line breaks or eliminate fallback. Identify which text must remain readable before or without the download. Keep a suitable fallback stack and check it in the actual layout. Do not replace useful text with outlines or an image to hide a font failure.

[CSS Fonts 3's fetching requirements](https://www.w3.org/TR/css-fonts-3/#font-fetching-requirements) explain why cross-origin font delivery needs appropriate server permission. Record the intended document and asset origins. Do not loosen an entire site's CORS or security policy as a packaging shortcut. If the authorized hosting configuration cannot serve the fonts, provide the exact integration requirement and keep delivery unverified.

Do not add preloads for every subset by default. Establish which assets the initial page actually needs before making optional loading changes. Preserve existing application CSS and deployment settings unless their modification is within scope.

## 5. Verify assets, selected rendering and fallback separately

Build a small specimen from the agreed text classes, not only an alphabet. Show each required face and meaningful feature with labels outside the font-dependent content. Include a representative combining sequence, a long value or heading, and any script/locale essential to the request. A sample is not a complete language certification.

Use the authorized browser/preview route and record its browser, origin and asset base. Do not bypass a denied preview with another port, tunnel or public host. Where rendering is unavailable, deliver only the asset-level evidence and leave these checks unrun:

1. **Resource identity:** Inspect the exact resolved font URL, successful resource response and absence of parser/load errors. Distinguish fresh fetches from cached responses and check the intended version. A 200 response containing an HTML fallback page is not a font success.
2. **Face actually used:** Inspect rendered-font information where available for the selected specimen runs, including weight and style. Computed family text alone is not proof of glyph use. Keep local-font substitution and browser-synthesized styles distinct from the supplied face.
3. **Required text and shaping:** Compare the same content and settings against the preserved reference. Inspect marks, joining, alternates, spacing, clipping and line breaks where relevant. Keep unsupported script review explicit if no qualified comparison is available.
4. **Absent or delayed resource:** Through a supported bounded preview check, withhold only the specimen's font resource and inspect readable fallback, navigation/control labels and layout. Do not disconnect the user's computer or alter production assets to force failure.
5. **Real integration boundary:** If integration was requested, inspect a representative nested page and the intended styles at that actual asset base. A standalone specimen does not prove the site's cascade, paths or server behavior.

[MDN's FontFaceSet.check reference](https://developer.mozilla.org/en-US/docs/Web/API/FontFaceSet/check) explicitly warns that a true result can occur for a nonexistent font, and its text argument does not check individual glyph coverage. Do not use that single boolean as acceptance. Combine file, resource and rendered-run evidence; mark exact-face identity unverified when the available browser cannot expose it.

Keep failures actionable: absent glyphs require repertoire/source review; wrong style requires face/CSS mapping review; failed requests require asset-path/server review; correct files with broken shaping require feature/transform review. Change the responsible layer and repeat only the affected checks plus the final representative specimen. Do not keep shrinking the file after reaching the agreed delivery budget and behavior.

## Handoff and stopping point

Return the font assets, matching CSS, required notices, specimen and concise provenance/regeneration notes. State what is fixed-copy-only, what future content is covered, intentional fallbacks and the checked browsers/paths. Retain source identities and exact transformation settings without embedding confidential sample text. Preserve prior site assets for a separately authorized integration reversal.

Accept the package only at its observed level: prepared plan, built assets with rendering pending, specimen-verified package, or integrated package verified at the named site. Publication is separate and requires the intended destination and authority. Never claim universal language coverage, licensing certification or a performance improvement from a successful conversion.

## Fictional, unexecuted illustration

A fictional museum supplies a permitted Regular and Italic family for a fixed exhibition title and a visitor-name form. The title's letters are known, but visitor names are open-ended. The permitted source covers an accented letter used in the title, while an initial ASCII-only subset would remove it.

The workflow would reject that subset for the title, preserve a separate broad-font or accepted-fallback decision for names, and keep Italic mapped to its own asset. A specimen that looks correct because the original family is installed would not prove the downloaded subset works. A true FontFaceSet.check result would not settle that uncertainty either. The next useful evidence would be the actual resource and rendered-face identity, followed by the title and name-field fallback checks.

This is an authored decision example, not a completed conversion or browser test. No font files, license terms, site assets, hosting settings or live user data were changed for it.
