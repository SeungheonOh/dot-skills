---
name: prepare-integration-config-handoff
description: "Prepare secret-free, loader-specific configuration templates and a field-binding handoff for an existing integration, preserving required values, profile composition and consumer semantics. Use for setup artifacts, not configuration-drift comparisons, secret provisioning, infrastructure deployment or changing runtime behavior."
---

# Prepare an integration configuration handoff

Turn an integration's established configuration requirements into templates another operator can complete without guessing units, defaults, environment identity or where credentials belong. Deliver the requested files and a concise field map tied to the actual consumer revision. A copied environment dump is neither a safe template nor a documented setup contract.

Use [configuration-drift-inventory](../configuration-drift-inventory/SKILL.md) to compare existing snapshots and [automate-repeatable-task](../automate-repeatable-task/SKILL.md) to implement a repeatable operation. This workflow authors configuration artifacts for an existing integration; it does not redesign or activate that integration.

## Establish the consumer and target

Identify the integration/component revision, relevant configuration declarations or bounded source references, exact loader and version, launch/deployment context, selected profiles, output format/location and intended operator. Read applicable setup documentation and supplied sanitized templates. Do not infer supported variables simply because similarly named variables exist in another service.

Determine whether the requested output is a .env example, JSON/YAML template, platform-specific values file or another native format. Name the loader, not only the file extension. [Node.js documents its own .env grammar](https://nodejs.org/api/environment_variables.html#dotenv); quoting, interpolation and precedence must be checked for the actual consumer. A shell assignment file, a dotenv file and a container environment file are not automatically equivalent.

If the loader or authoritative key set is unavailable, prepare the supported field map and hold the runnable-template claim. Ask only for the missing input that changes the output. Do not launch the integration to discover settings or inspect an entire process environment, credential store or unrelated deployment.

## 1. Derive a field map from the real consumer

For each in-scope field, record its exact key/path, consuming component, source location/revision, purpose, required/conditional status, accepted representation, unit/range, missing and empty behavior, established default, and ordinary-versus-secret classification. Keep the original spelling and case; a friendly label is not a replacement key.

Separate raw text from parsed meaning. If the runtime reads a string and the application converts it, document both. A text value "false" is not evidence that every caller treats it as a false boolean. A timeout named TIMEOUT has no established unit until its consumer or contract says so. A default printed in documentation is not proof that the application applies it.

Record relationships that determine whether a profile is coherent: paired endpoint/region/account identifiers, conditional feature requirements, mutually exclusive auth mechanisms, callback URLs, and accepted version selectors. Include a cross-field rule only when it is supported by the consumer or accepted setup contract. Do not invent an environment-matching check that the software does not implement.

Mark deprecated, ignored, unknown and externally injected fields separately. Every template key should map to a consumer or a documented launcher setting. Preserve unknown existing keys in the original, and hold their inclusion rather than silently declaring them valid or deleting them. Ordinary template authoring does not authorize code changes to accept a preferred variable name.

## 2. Resolve profile composition without using live secrets

Describe how the selected launcher obtains configuration: file order, process environment, command options, application defaults and supported secret injection. Record precedence from current official docs and relevant consumer code, including whether an empty value overrides, falls back or is rejected. Avoid claiming one universal order for every platform.

Keep loader substitution and runtime injection separate. For example, [Docker Compose interpolation](https://docs.docker.com/compose/how-tos/environment-variables/variable-interpolation/) explains how values substitute into the Compose model; [container environment precedence](https://docs.docker.com/compose/how-tos/environment-variables/envvars-precedence/) addresses the resulting container environment. A value available to interpolation is not by itself proof it reaches the application.

Make each delivered profile's dependencies visible. Use a small table or manifest showing supplied ordinary values, inherited established values, required operator values and secret bindings. Name the files and order needed to compose a profile. Do not silently mix a staging host with a production account identifier or reuse a default tenant merely because both fields parse.

Describe secrets by safe binding names, required purpose and provisioning owner, without retrieving or including their values. Do not include hashes, suffixes or partial credentials as a convenience. A secret-store reference can itself identify private infrastructure; include only the recipient-appropriate reference already authorized for the handoff. Creating credentials, granting roles or configuring persistent access is separate work.

## 3. Author the templates in the requested syntax

Create separate candidate files and preserve originals, comments and unrelated settings. Keep file names clearly marked as templates or examples. Use synthetic values only when their fictional nature and replacement requirement are unambiguous. Prefer inert example hosts for invented systems; for a real integration, use an approved non-production destination or leave the required endpoint unset as the target format supports. Never silently fall back to production to make a template look complete.

Represent required-but-unprovided values deliberately. An empty assignment can override a useful value or satisfy a weak presence check; a fake token can be sent as a literal credential. Where appropriate, omit/comment the assignment and put the requirement in the field map instead. Describe a placeholder as a placeholder, not as a guaranteed startup guard. Do not claim fail-closed behavior unless the consumer actually enforces it.

Preserve the distinctions the loader implements: quoted versus unquoted strings, literal dollar signs, hashes, backslashes, embedded newlines, leading/trailing spaces, null versus absence and string versus numeric values. Use format-supported comments only. For dotenv-like files, do not provide a shell `source` command unless the file is actually intended and verified as shell input; sourcing is execution, not parsing.

Avoid embedding multi-line credentials, certificates or binary data in example files. Describe the established file/secret binding when supported without copying the underlying material. Do not add TLS bypasses, permissive permissions, broad network access or debug logging that exposes request headers as setup shortcuts.

When editing existing templates, preserve established key names and non-secret defaults unless the requested correction requires a change. Keep obsolete keys visibly deprecated or remove them only within the authorized edit scope, with a source-backed explanation. Do not rewrite deployment manifests or change .gitignore as an unannounced side effect of preparing a template.

## 4. Check effective meaning with synthetic values

Read back the saved files and reconcile fields in both directions: required consumer settings must have a supplied value, established default, injection binding or explicit hold; every emitted key must have an identified consumer. Recheck that no real credentials, production captures or private environment dumps entered the package.

Make a compact resolution worksheet using fictional values. Trace at least the actual ambiguity that could break this handoff: missing versus empty, a process override of a file value, a literal special character, a conditional missing setting or a cross-profile mismatch. Derive expected values from source-established rules, independently of the authored template.

Use an available permitted parser or a documented side-effect-free configuration-rendering path only after inspecting its effects. Some commands print resolved secrets, invoke plugins, load application modules or contact infrastructure. Do not execute those paths merely to validate syntax. Use only a bounded synthetic environment and prevent unrelated inherited values from contaminating a permitted check. Never print real resolved secrets as evidence.

Report static review, parser acceptance, effective-value resolution and application startup separately. A parseable template does not prove that credentials are valid, remote endpoints are reachable, a feature is enabled or the integration is ready to run. If no safe parser is available, finish the static worksheet and state that parsing and runtime behavior remain unverified.

## Acceptance, recovery and delivery

Accept the handoff when the operator can identify the intended profile, supply each required value through the documented route, understand its interpretation, and distinguish established defaults from missing decisions. Check that templates, field map and profile composition agree; unsupported keys or unresolved units are visible holds rather than invented defaults.

If sources disagree, preserve the conflicting evidence and hold the affected assignment. If a consumer revision changes mid-task, refresh its field map before overwriting a candidate. On an uncertain save, inspect first; do not replace a working operator file or an existing .env. Recover from a bad candidate by issuing a corrected template and change note, not by changing live settings or rotating secrets.

Deliver actual template files, the consumer/loader revision, field and secret-binding map, profile composition, operator prerequisites and check results. Keep the documentation proportional to the number of consequential fields. State that preparation is complete while unresolved provisioning or runtime checks remain. Uploading, importing, deploying, granting access and activating the integration require their own authorized scope.

## Fictional, unexecuted illustration

A fictional reader's supplied configuration contract recognizes CATALOG_URL, RETRY_DELAY_MS and CLIENT_TOKEN. RETRY_DELAY_MS is decimal text interpreted as milliseconds; missing means 1500, empty is invalid. CLIENT_TOKEN is required from an existing secure injection channel. The supplied launcher rule says process values override file values. The target dotenv grammar permits a hash inside quotes.

The candidate .env.example includes CATALOG_URL=https://catalog.example.invalid and RETRY_DELAY_MS=1500. CLIENT_TOKEN has no assignment; its comment and field-map entry identify the required user-side injection step. The file is explicitly fictional and not startup-ready. It does not contain an actual secret reference or a production fallback.

The expected resolution worksheet shows a synthetic process RETRY_DELAY_MS=2500 overriding the file's 1500 and an explicitly empty process value remaining invalid. A separate worksheet-only grammar probe, GRAMMAR_PROBE="alpha#beta", has expected text alpha#beta under the supplied grammar; it is never emitted as an integration key. No configuration file, parser, launcher or integration was executed for this illustration. The worksheet establishes the intended handoff reasoning, not observed application behavior.
