---
name: export-design-token-package
description: "Prepare an interchange package from an established design-token source, preserving typed values, aliases, identities and theme composition while mapping the result to a named consumer. Use for token handoff or migration, not inventing a visual identity, designing screens or implementing a token compiler."
---

# Export a design-token package

Deliver machine-readable tokens that retain the design system's meaning across a named handoff, together with a compact mapping and unresolved-loss record. A palette screenshot, list of CSS colors or renamed JSON file is not a token interchange package.

Keep new artwork with [create-visual-asset](../create-visual-asset/SKILL.md) and interaction decisions with [design-user-interface](../design-user-interface/SKILL.md). This workflow translates established design decisions; it does not redesign a product or change its live component library.

## Input and output contract

Establish from the request and supplied material:

- Exact source export/revision, selected collections and token identities, including descriptions and vendor metadata that must survive
- Source dialect and target consumer/version; distinguish a requested DTCG file from a particular tool's partially compatible format
- Required themes, brands, densities or other contexts, their defaults, and the source's actual precedence rules
- Deliverables: alias-preserving interchange files, any requested resolved snapshots or platform outputs, and a mapping of source identity to destination path/name
- Permitted name/value changes, known deprecations, protected extensions, and an authorized private destination

Return the actual requested files, the context/composition instructions needed to interpret them, and a coverage ledger for included, excluded and blocked tokens. For a small export, the mapping and notes can be one document. Do not require a compiler, preview site or full design-system migration when a few files suffice.

If only screenshots or ambiguous labels exist, prepare the recoverable inventory and request the actual source values or owner decision. Sampled pixels do not establish color-space intent, aliases, units or theme membership. Do not manufacture missing tokens to make the package appear complete.

## Preserve the source meaning

Work in a new output copy and retain the original export. Record its revision or digest when available. Separate a token's source ID, human label, hierarchical path and eventual consumer identifier; they are not interchangeable. Two roles with equal values may need distinct identities, while two equal labels may identify different tokens.

For each selected token, record its type, literal value or reference, description, context membership, deprecated status and required metadata. Include the dependency closure of selected aliases only within the authorized selection. A referenced token outside that scope is a held dependency, not permission to copy an entire private library.

Resolve the file dialect before changing syntax. The [DTCG Format Module 2025.10](https://www.designtokens.org/tr/2025.10/format/) defines typed JSON tokens, references and extensions; it is a Community Group report, not a W3C Recommendation. Use that dated contract when requested, and check the consumer's documented support separately. Preserve unknown extension data in the interchange source; do not flatten it away because a downstream output cannot use it.

Do not infer a type from a group name or guess whether a number means pixels, seconds or a ratio. Preserve units, precision, color-space labels and alpha. Keep composite values such as typography and shadows together unless the requested consumer requires an explicit, recorded decomposition. Font-family values do not provide the font files or permission to redistribute them.

## Settle names, references and contexts

Build a deterministic name map before producing outputs. Check full paths for collisions after the consumer's escaping, case treatment or separator conversion. For example, `control.primary` and `control-primary` may both become `--control-primary`. Hold that collision for a stable disambiguation; do not choose whichever token is processed last. Preserve existing public names unless the requested migration authorizes changes.

Trace every alias through the selected graph. Identify missing targets, cycles and incompatible types with the affected paths. Preserve aliases in the editable interchange package when requested; a resolved snapshot is a derivative and should not replace the maintainable source. Never substitute zero, black or an empty string for an unresolved reference.

Write the composition contract for each requested context: inputs, source files, ordering, overrides and default behavior. A folder named `dark` is not evidence of override semantics. Resolve aliases against the final composed token set so a changed base token can affect its semantic aliases. The separate [DTCG Resolver Module 2025.10](https://www.designtokens.org/tr/2025.10/resolver/) describes ordered context composition followed by alias resolution. Use its structure only if the consumer supports it; otherwise document the existing tool-specific ordering or deliver explicit per-context files with that limitation.

Keep supported combinations bounded to the request. Do not invent a default theme, assume all dimensions combine freely, or generate every possible combination without a need. When a source has no defined winner for conflicting values, retain the conflict rather than using filesystem order as policy.

## Produce the requested representations

Write the alias-preserving files and any explicitly requested resolved/platform outputs from the same source revision and mapping. Keep generated snapshots distinguishable from editable sources. Record each output's context and the transformations applied.

Use the consumer's actual serialization rules. A value that is valid JSON can still be invalid for the selected token dialect. Do not coerce a dimension into a bare number, reorder font fallbacks, turn alpha into an opaque hex value, or discard a shadow layer just to satisfy an importer. For a required conversion, identify the approximation and its scope. Converting relative units to fixed units needs an established reference size; converting wide-gamut colors needs a stated gamut policy. Hold material appearance changes that the user has not approved.

Treat extensions, descriptions and source links as potentially private. Preserve them in the private working source while reviewing the intended delivery copy for internal URLs, unpublished product names or unnecessary personal data. If required metadata conflicts with the allowed audience, ask for a scoped resolution instead of silently deleting it or sharing it. Token export does not authorize uploading to a converter, publishing a registry package, connecting a design account or modifying a shared library.

## Acceptance and failure handling

Check the exact saved artifacts against the source and requested consumer:

1. Every selected token has one mapped destination or a visible reason it is held/excluded; no duplicate input keys or mapped-name collisions are silently overwritten
2. Types and value structures satisfy the declared dialect; units, precision, aliases and retained extensions survive the intended representation
3. References resolve without cycles in every requested composition, and the resolved values agree with the stated precedence
4. Generated outputs use the same source revision and context, with every lossy transformation identified
5. A consumer import, if available and authorized, uses a disposable copy and records imported counts, names, values and unsupported features; a schema or text check alone is not import evidence

Check representative boundaries deliberately: an alias affected by a context override, a same-value/different-role pair, and a complex value if present. Do not claim visual consistency or accessibility conformance from token validation. If a preview was requested, inspect the rendered result separately and name untested contexts.

If import fails, retain the original package and exact unsupported feature. Correct only the implicated mapping or use an agreed alternate representation, then recheck affected tokens and references. Do not repeatedly flatten more information until an importer accepts the file. If the source changes, refresh the affected graph and regenerate dependent outputs rather than mixing revisions.

Stop when the requested files and mapping are prepared with their actual verification status, or when a missing source, semantic decision or consumer capability blocks the next step. Report file identities, included/held counts, transformations and whether the named consumer was exercised. Do not call an untried import successful.

## Fictional, unexecuted illustration

These invented inputs and expected results illustrate the workflow. No exporter, validator or design tool was run.

**Request:** Export Cedar UI's spacing tokens as DTCG 2025.10 JSON for a consumer that accepts separate resolved context files. Preserve an editable alias source. The supplied ordering is base, then the selected density override.

**Source:** Base token `space.step` has type `dimension` and value `{ "value": 8, "unit": "px" }`. Token `control.gap` aliases `{space.step}`. The compact context overrides `space.step` with `{ "value": 4, "unit": "px" }`. The comfortable context uses the base unchanged.

**Expected package:** Keep the alias in the interchange source and record the base/override ordering. Produce separate comfortable and compact resolved snapshots, with `control.gap` resolving to 8 px and 4 px respectively. Do not resolve the alias once before applying the compact override. Keep the source identities distinct even if another role also resolves to 8 px.

**Expected handoff:** “Two token identities and one context override mapped; alias source and two context snapshots prepared. Consumer import is untested.” If the consumer requires a single combined file but has no documented context mechanism, hold that output choice instead of claiming the two snapshots are a working import.
