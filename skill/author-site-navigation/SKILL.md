---
name: author-site-navigation
description: Turn an existing website's approved page inventory into a maintainable navigation map and usable menu, breadcrumb and human-sitemap artifacts. Resolve page placement, route bases, current-page states and audience boundaries; use for navigation authoring rather than full-site design or QA alone.
---

# Author a coherent site navigation set

Deliver the actual navigation artifacts for the selected website: the requested menus, section navigation, breadcrumb trails or human-readable sitemap, backed by a small page map that future editors can maintain. A tree drawn in a planning document is insufficient when the user needs usable links or source fragments.

This workflow arranges routes through an existing set of pages. [Classification design](../design-classification-scheme/SKILL.md) defines topic categories and assignment rules. [Subject indexing](../create-subject-index/SKILL.md) selects discussions and passage locators within a work. [Document search](../build-document-search/SKILL.md) implements queries. Use those workflows when their outcomes are requested; a navigation task does not automatically need a new taxonomy, search service or whole-site redesign.

## Establish the navigation contract

Identify the selected site/revision, authorized page inventory, intended audience and visitor tasks, existing terminology, site root/base path, languages/versions and requested outputs. Read enough page content to establish what the pages actually do; route names and headings alone can mislead. Record inaccessible or unfinished pages rather than silently declaring the inventory complete.

Determine which navigation surfaces are in scope: global menu, section menu, breadcrumbs, previous/next links for a real sequence, footer links or a human sitemap. Do not add all of them by default. Keep a search-engine XML sitemap, structured-data markup and redirects separate unless requested; a human sitemap is a readable linked directory, not proof of indexing.

Inspect the existing content system's source conventions and available output path. Choose between editing the supplied source, producing exact compatible fragments/configuration, or a plain HTML candidate when the integration is unknown. Preserve the requested stack and do not introduce a runtime or navigation library merely to emit ordinary links.

### Audience and publication boundary

Page names, paths and categories can reveal unpublished projects even without exposing their body text. Build each reader-facing artifact from the content approved for that audience. Do not put all private routes in a downloaded manifest and rely on CSS, collapsed menus or client-side filtering to hide them. Hiding a link does not restrict direct page access.

Keep the complete editorial inventory private when it contains held or restricted pages. Return a separate publication-safe navigation set rather than leaking exclusions in comments or HTML data attributes. Do not change page permissions, publish drafts, expand site access, upload sources to a navigation service or contact readers without authority. If authorization-dependent navigation is required, establish the actual server/access integration before claiming a static artifact implements it.

## 1. Build a page map with stable identities

Create a compact map containing:

```text
page ID; source revision/locator; destination route; approved audience/state;
page title; navigation label; primary parent ID; sibling order;
navigation surfaces; optional sequence position and alternate-language/version IDs
```

Keep page identity separate from its title, label and route. Two pages can have the same title without being duplicates; a route can change while the page remains the same. Distinguish a real page, non-link grouping label, external destination and section anchor. A grouping label must not become a fabricated empty page or `href="#"` control.

Account for every in-scope page: included in named surfaces, deliberately reachable through contextual links only, held, or excluded from this audience. The global menu need not list every page. A deliberately unlisted campaign or utility page is not necessarily an accidental orphan; record its intended entry route privately. Do not conceal missing destinations by dropping them from the denominator.

Preserve final URLs as supplied until an authorized route change is decided. Navigation editing does not by itself authorize renaming files or installing redirects. If a label changes, retain the route unless the user requested that separate change.

## 2. Choose useful hierarchy and labels

Organize around the reader's actual tasks and the content, not automatically around the owner's organizational chart or source folders. Use clear, distinctive labels at each level. Retain established terms when they help returning visitors; explain consequential terminology changes. Do not invent a fixed maximum number of menu items or a mandatory depth as a universal usability rule.

Assign a primary parent when the deliverable needs a consistent location trail. A page useful in two sections can have one primary location plus contextual links from the other, or another explicitly agreed multi-placement design. Do not duplicate the content or infer a different identity solely because two menus link to it. Keep cross-links separate from parent edges so the hierarchy can remain acyclic.

Resolve these boundary cases before emitting artifacts:

- A section has a real landing page: link its label to that actual page
- A section is only a group: use a non-link label or an explicitly implemented disclosure control, not a fake destination
- A leaf has no approved parent: decide its entry path rather than guessing from the longest URL prefix
- A page belongs to a sequence: previous/next follows the evidenced sequence, not alphabetic file order
- Several languages or versions exist: switch to the corresponding page when mapped; a missing counterpart is visible rather than silently returning an unrelated homepage

Choose the hierarchy needed for navigation, not a new conceptual ontology. If content ownership or intended placement is materially ambiguous, hold that placement while completing clear branches. A proposed structure is editorial judgment; do not call it user-tested unless readers actually used it.

## 3. Resolve links in the delivered location

Decide how routes are resolved under the actual base path and deployment layout. A root-relative link that works at a domain root may leave a site hosted under `/handbook/`; a file-relative link that works from one folder may fail from a deeper page. Use the platform's established URL helper or compute each artifact's actual relative target. Do not add an HTML base element as an incidental shortcut because it can change unrelated links and forms.

Check case, trailing-slash and extension conventions, percent-encoding and fragment IDs against the supplied target system. Distinguish a URL's query from its fragment and preserve meaningful values. Treat untrusted labels and destinations as data: escape text and attributes correctly, allow only intended link schemes, and exclude executable URLs. External links should be explicit where otherwise confusing and should not silently open a new context unless the design requires it.

For section anchors, identify the intended heading or stable target, not merely any matching ID. Generated heading slugs can change when titles change; retain durable IDs where the source supports them. A valid route with a nonexistent fragment is still an incomplete deep link.

Keep old-URL continuity separate. If reorganization includes approved route changes, hand their old-to-new mapping to the redirect work; changing menu links alone does not preserve previously shared addresses.

## 4. Author semantic artifacts from one map

Generate the requested surfaces from the same accepted identities, labels and ordering. Record any intentional surface-specific label differences. Repeated menus should not drift because separate copies were edited independently.

For ordinary site navigation, prefer native links in an appropriately labeled navigation region and list structure. Use unordered lists for ordinary groups and ordered lists when sequence matters. Distinguish multiple navigation regions with useful labels and preserve logical order across layouts. The [W3C menu-structure guidance](https://www.w3.org/WAI/tutorials/menus/structure/) provides these structural patterns; the [HTML nav definition](https://html.spec.whatwg.org/multipage/sections.html#the-nav-element) distinguishes major navigation blocks from incidental links. Ordinary site links do not require application-menu behavior.

Generate current-page state for the actual output page rather than hardcoding one shared active item. Use `aria-current="page"` when a link denotes that page; a parent section is not also the current page. A menu without the current page can legitimately have no current-page marker. Preserve a visible non-color-only indication in the site's styling contract.

Breadcrumbs express the selected hierarchy, not the visitor's browser history or every segment of a URL. Derive the ancestor chain from page IDs, then use the real ancestor labels/routes. The [W3C breadcrumb pattern](https://www.w3.org/WAI/ARIA/apg/patterns/breadcrumb/) uses a labeled navigation landmark and current-page semantics when the current item is linked. Omit invented ancestors and make decorative separators nonessential to the spoken labels.

A human sitemap should be a complete readable list for its approved scope, with meaningful grouping and links. Avoid requiring a search box, hover or scripts to reveal the only route to required content. If the requested design collapses a menu, implement or integrate the actual disclosure behavior and its keyboard/focus states through the site's existing pattern. A collapsed-looking icon without behavior is unfinished; a source-only fragment cannot establish runtime usability.

Do not redesign unrelated colors, typography or page content to finish navigation. Include only the styling or integration changes necessary for the requested navigation to remain legible and operable in the existing site.

## 5. Verify coverage, meaning and real integration separately

Reopen the exact saved map and artifacts. Check:

1. **Coverage:** Every selected page has a recorded inclusion/disposition; expected published pages are reachable by their intended entry path
2. **Hierarchy:** Parent IDs exist, no ancestor cycle occurs, breadcrumb chains terminate, sequence endpoints are correct, and cross-links do not become unintended parents
3. **Destinations:** Every emitted href resolves from its actual placement to the intended page/fragment, including nested routes, external destinations and language/version alternatives
4. **Consistency:** Labels/order agree with the map, per-page current states are accurate, and repeated surfaces do not disagree accidentally
5. **Privacy:** Public markup, manifests, comments and labels exclude held/private items and credential-bearing, reset-token-bearing or session-specific links; approved generic Sign in or password-reset entry destinations can remain
6. **Reader behavior, when available:** A few actual tasks can be completed through the delivered navigation, with keyboard operation, focus visibility and narrow-layout behavior inspected where applicable

Inspect all structural records when practical; describe any sampling of content meaning or runtime use. A graph-reachability check does not prove that a reader understands labels, and a valid anchor is not proof of the correct content. A static markup pass is useful but cannot establish rendering, focus handling or full accessibility conformance.

Use a supported preview only within the available authorization. If runtime checks are unavailable, deliver source-checked artifacts and list the precise untested interaction. Do not open a denied target through another port, tunnel or account. If actual publication is requested, verify the published route set and navigation revision separately from the local candidate.

## Recovery and exact handoff

- Missing page or anchor: correct the target from source evidence or hold it; do not substitute a generic destination
- Ambiguous placement: retain the existing safe path and request the one editorial decision that changes the hierarchy
- Cyclic hierarchy or several current pages within one navigation set: fix the map/generation source and regenerate affected surfaces, rather than patching only one rendered copy
- Wrong base path: correct resolution at the source and recheck shallow and deeply nested pages
- Private route exposed: stop publication, prepare a corrected candidate and follow the authorized removal path if already published; do not claim cached copies disappeared
- Source changed during work: reconcile the changed page identities/routes before applying the old navigation artifact

Return the accepted page map, the requested HTML/configuration/source artifacts, a placement map explaining which files or routes receive them, and a short note naming included/held scope and checks. Keep the restricted editorial map separate from publishable files. A preparation request finishes with these concrete artifacts; installation/publication is complete only when requested and read back. Do not claim improved search rankings or measured findability from an authored hierarchy.

## Fictional illustration, not executed

A fictional community workshop has Home, Classes, Safety, Equipment, and a Kiln Guide. The kiln guide is useful from both Classes and Equipment. The accepted hierarchy places it under Equipment, while Classes keeps a contextual link. Its breadcrumb is Home → Equipment → Kiln Guide regardless of which link the visitor followed.

The site is intended for `/workshop/`, so a root-relative `/equipment/kiln/` would leave that base and fail the proposed contract. The map resolves the actual `/workshop/equipment/kiln/` target and marks Kiln Guide as current only on that page. A private instructor rota is excluded from the public map, including hidden fields and comments.

This is a fictional design illustration. No site was built or published, links followed, accessibility test run or reader study performed.
