---
name: prepare-web-app-manifest
description: "Prepare or revise an existing website's web app manifest, preserving installed-app identity and reconciling launch URLs, navigation scope and icon assets. Deliver the manifest and integration map; do not equate valid JSON with installation, offline support or a complete PWA."
---

# Prepare a web app manifest

Deliver the actual manifest candidate, its document-link integration and a short resolved-URL/asset map. The useful outcome is an application identity and launch contract that survives the intended deployment location, not merely a JSON file containing a name and logo.

[Website creation](../build-usable-website/SKILL.md) builds the application. [Link-sharing metadata](../prepare-link-share-metadata/SKILL.md) describes pages to sharing consumers. [SVG icon packaging](../package-svg-icon-library/SKILL.md) handles reusable artwork. This workflow owns installation metadata for an existing web application; it does not implement offline behavior, service workers, push delivery or app-store submission.

## Establish the application and deployment boundary

Identify the existing manifest and its owning source/template, linking documents, final deployment origin and base path, intended launch page, application name and approved icon assets. For an update, capture the current manifest URL, effective identity and source revision before editing. Ask whether this is the same installed application or an intentionally separate application only when the answer is unresolved and affects identity.

Select the target browsers/platforms when installation or presentation verification is requested. Otherwise prepare a base candidate and leave consumer behavior unverified. The [W3C manifest specification](https://www.w3.org/TR/appmanifest/) is a working draft, not a promise of identical support across browsers. Consult current target documentation for required members and supported extensions instead of imposing one browser's checklist on all consumers.

Keep staging and production destinations explicit. If the final host/base path is unknown, prepare the independent content and a provisional map; do not declare unresolved relative URLs deployable. Preserve existing supported members that are outside the requested change. Do not replace a generated endpoint with a second hand-maintained manifest.

Manifest names, paths and assets can be publicly fetched or retained in an installed application. Exclude private labels, personal identifiers and authentication tokens. Do not upload private artwork to online icon checkers, publish the candidate, install an app or clear a browser profile merely to verify a file-preparation request. Use approved local copies and keep internal source locators out of public JSON.

## 1. Resolve identity, launch and scope separately

Record each raw member beside its intended absolute result and resolution base. Do not apply one generic base URL to every field.

- **Identity:** The [id member](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Manifest/Reference/id) identifies the application rather than a resource to fetch. Relative IDs resolve against the start URL's origin, not the manifest directory. Keep the ID same-origin with the start URL; fragments are ignored while queries can affect identity. A missing or invalid ID falls back to the start URL. Preserve an existing effective identity when introducing an explicit ID; do not choose a prettier identifier that creates a second app.
- **Launch:** A relative [start_url](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Manifest/Reference/start_url) resolves against the manifest URL. It must be same-origin with the document linking the manifest; otherwise processing falls back to that document's URL. Choose a durable approved entry point, not the current editor route, a signed link or a user-specific session URL. A browser may treat this member as a hint, so file inspection does not prove the actual launch destination.
- **Navigation:** Relative [scope](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Manifest/Reference/scope) resolves against the manifest URL. The start URL must be within the effective same-origin scope; invalid or missing scope falls back to the start URL's directory. Scope is a path-prefix boundary, not a filesystem directory check: prefer a slash-terminated directory when that is the intended boundary. `/studio/` excludes `/studio-old/`, while `/studio` can capture it. Scope neither prevents out-of-scope navigation nor provides access control.

For an existing app, compare the before/after effective ID independently from changes to manifest location, launch path or display name. Keep an identity change held unless a separate app or migration is actually intended. If the previous identity cannot be established, report that uncertainty rather than asserting update continuity.

Build a small boundary list from the actual site: launch page, nested app page, bare directory path, similar-prefix sibling, unrelated same-origin page and any required login/return route. Classify intended navigation scope without broadening it to the whole origin just to silence a warning. Manifest scope is not service-worker registration scope; changing one does not repair the other.

## 2. Attach truthful names, presentation and icon assets

Use approved application wording, not the title of whichever page supplied the manifest link. Keep a shorter name recognizable if needed. Choose requested display and color values as presentation preferences, without promising that every platform uses them. Avoid adding orientation locks, shortcut actions, file/protocol handlers or experimental members when they are not needed for the requested package.

Associate each icon entry with actual delivered or retained bytes. The [icons reference](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Manifest/Reference/icons) defines relative `src` resolution against the manifest URL. Record real raster dimensions and media type; a filename containing `512` is not dimension evidence. `sizes: "any"` describes scalable artwork, not an arbitrary bitmap. Distinguish ordinary, maskable and monochrome uses rather than assigning every purpose to the same image by default.

For a maskable asset, inspect a crop preview of the final derivative. Google's [maskable-icon guidance](https://web.dev/articles/maskable-icon) places essential content inside a centered circle with radius 40% of the square icon width and recommends an opaque padded image. The corners of a centered 80%-wide square are not all inside that circle. Merely adding `purpose: "maskable"` does not move a logo into the safe region. Keep approved ordinary artwork separately when the needed padding would make it unsuitable for ordinary use.

Do not redraw a protected mark or change its colors without scope to do so. Preserve originals and record any approved crop, padding or format conversion. If required artwork is missing, deliver the dependent entry as held rather than inventing an asset URL or declaring a placeholder installation-ready. Check target requirements for icon sizes/formats at execution time; no universal size list proves platform compatibility.

## 3. Prepare the manifest and owning integration

Write a JSON object with the chosen members and no comments, trailing commas or competing duplicate keys. Use the existing project's serialization/template route when it owns the output. Provide the exact document link or source change at its owning layer, preserving unrelated head tags. Avoid adding a second manifest link beside an existing definition and assuming the later one wins.

The [manifest specification's linking guidance](https://www.w3.org/TR/appmanifest/#using-a-link-element-to-link-to-a-manifest) uses `rel="manifest"` and recommends `application/manifest+json` delivery. Resolve the link from each relevant document, including any effective HTML base. Resolve member URLs from the resulting manifest location. Moving the JSON file can therefore change launches and assets without changing its contents.

Keep the handoff concrete: local file, intended served URL, owning source, link insertion/replacement, resolved member values and retained/new asset paths. Authentication, cross-origin fetching and content-security policies can affect delivery. If such a dependency is encountered, record the actual target-specific requirement; do not weaken policies, expose restricted assets or grant new access incidentally.

## 4. Check the saved candidate at the requested level

Reopen the delivered JSON, integration fragment and asset map. With available authorized local tools, check syntax and member types, then compare resolved values against the intended contract. A JSON parser cannot establish browser processing or installation eligibility. Inspect the exact final artwork for clipping and wrong variants rather than checking only file existence.

Check these acceptance points:

1. The linking documents resolve to the intended manifest, with no competing owner left unresolved
2. The effective identity remains the same for an update, or a deliberate separate identity is documented
3. Launch and scope agree with the final deployment path; boundary pages have the intended classifications
4. Icon references resolve to the mapped assets, with truthful dimensions, type and purpose
5. The package contains no private values, unresolved public placeholders or unintended unrelated member removals

For an authorized browser check, inspect the actual served manifest and asset responses, not just status codes: an HTML fallback is not valid manifest delivery. [Chrome's Application-panel documentation](https://developer.chrome.com/docs/devtools/progressive-web-apps) describes its Manifest view for parsed properties, icons and errors. Use the chosen browser's equivalent supported inspection route and record its version, origin and observed result. Do not claim another platform passed from that observation.

Actual installation and launch checks are separate from source inspection. If requested and authorized, use an appropriate disposable test context and observe launch destination, displayed identity/icon and a relevant scope boundary. Do not uninstall the user's existing app, erase its data or unregister its service worker as a troubleshooting shortcut. A successful fresh install also does not establish that existing installations have adopted an update.

## Recovery and handoff

- Wrong resolved URL: repair the responsible base/member or link, then recheck all dependent references
- Uncertain prior identity: preserve the working manifest and hold the migration claim, not unrelated content preparation
- Missing icon or unsupported presentation: report the exact asset/consumer gap and retain a truthful supported subset
- Stale installed metadata: distinguish served bytes from installed state; do not churn IDs or promise immediate refresh
- Uncertain publication: inspect the current source and served candidate before retrying; do not overwrite newer work

Return the manifest, integration change, asset/resolution map and concise evidence note. Separate `prepared`, `source checked`, `served metadata inspected` and `installation/launch observed`. Keep offline operation, app-store acceptance and existing-installation update behavior outside the claim unless those were separately requested and actually checked. Finish at the requested stage or the specific unresolved dependency.

## Fictional illustration, not executed

A studio's manifest will be served at `https://clay.example/assets/app.webmanifest`, while its app lives under `/studio/`. The approved candidate uses `id: "/studio-app"`, `start_url: "/studio/"` and `scope: "/studio/"`. The identity is not required to be a fetched page under the navigation scope. An icon source `icons/launch.png` resolves beneath `/assets/`, not beneath `/studio/`.

The handoff must therefore map that icon to `/assets/icons/launch.png` or use the approved correct address. `/studio/workbench` belongs inside the intended scope; `/studio-old/` does not. Replacing scope with `/studio` would widen that boundary. For an already installed app, the proposed ID remains provisional until compared with its previous effective identity.

This is an authored example only. No manifest parser, renderer, browser, installation or deployment was run for it.
