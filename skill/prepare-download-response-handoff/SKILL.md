---
name: prepare-download-response-handoff
description: "Prepare a route-scoped HTTP file-download response contract and implementation handoff, preserving media type, safe internationalized filenames and actual client behavior. Use for response metadata and download naming, not file generation, interrupted-transfer recovery or production activation."
---

# Prepare a file-download response handoff

Deliver a response contract, concrete header candidate or narrow configuration patch, and a client-aware verification worksheet. The result should explain what file a recipient receives and how its suggested name is derived, not merely add an attachment header to every response.

[Interrupted download recovery](../interrupted-download-recovery/SKILL.md) preserves transfer identity and reconstructs bytes. [HTTP cache policy](../prepare-http-cache-policy/SKILL.md) controls response reuse. [Browser CORS policy](../prepare-browser-cors-policy/SKILL.md) controls script-readable cross-origin responses. This workflow owns the download response's presentation and filename contract across an existing server and client.

## Establish the file and consumer

Read the selected route, file producer, response middleware and client call site at an identified revision. Resolve the expected file format, filename source, intended inline-versus-download experience, selected routes and statuses, and actual owning server or storage service.

Separate direct navigation from a JavaScript fetch followed by a client-created download. Identify whether a proxy, object store or browser script replaces metadata or selects a different filename. An HTTP header candidate cannot establish the behavior of an unseen client.

Use supplied files, source or sanitized captures. Keep signed URLs, account records and private filenames out of the shareable handoff. Preparation does not authorize endpoint requests, export generation, storage settings, access expansion or deployment. If the producer or consumer is unavailable, complete the known response contract and identify the missing layer.

Ask only for decisions that change the output: whether the file should open inline, the approved naming convention, or which supported clients matter. Do not require a platform interview when the requested deliverable is only a header-level proposal.

## 1. Bind metadata to the actual response

Record one row for each materially different branch:

```text
route and response class | producer/file format | media type
disposition | filename source and fallback | emitting layer
client consumption path | unresolved decision
```

Treat an authentication page, JSON error and successful document as different responses even if they share a URL. A global attachment rule can turn a login or error page into a misleading file. Keep failure behavior visible rather than treating any saved body as the requested export.

Choose Content-Type from the established representation, not solely from the requested extension. [RFC 9110 section 8.3](https://www.rfc-editor.org/rfc/rfc9110.html#section-8.3) defines this field as representation metadata. Do not relabel known PDF or CSV bytes as an arbitrary type merely to influence browser behavior. Keep content coding separate from the underlying format.

Check whether the producer actually returns the promised file. A title ending in `.pdf` and a proposed application/pdf header do not establish PDF content. If bytes are unavailable, record the producer contract as source evidence and leave content verification pending.

## 2. Derive a safe suggested filename

Define a short naming transformation from approved source fields to a basename. Keep the transformation independent of the raw header serializer. Do not concatenate an untrusted title, query value or stored upload name into a response header.

Reject line breaks and control characters before serialization. Resolve separators, path-like components, reserved names, misleading extensions, empty results and excessive lengths under the supported client/filesystem requirements. Use a predictable safe fallback when the approved naming policy allows it; otherwise hold the input. Do not hide a rejected value inside comments or logs included in the deliverable.

Keep useful human distinctions without exposing unnecessary personal information. If transliteration or normalization changes a name, show the intended display name and the fallback separately. Two distinct names can collapse to one fallback; explain that collision rather than promising unique local files.

Under [RFC 6266 sections 4.1–4.3](https://www.rfc-editor.org/rfc/rfc6266.html#section-4.1), attachment requests saving rather than normal media-type processing, while inline retains normal processing. Filenames remain advisory. Duplicate instances of the same parameter are invalid; filename and filename* are distinct parameters, with the extended form preferred when understood.

A suggested name is not a destination path, overwrite instruction or assurance that the file is safe to open. Keep output-location and collision handling with the actual recipient.

## 3. Serialize the response header deliberately

Use the target framework's established header serializer when available, after checking its documented behavior and version. If returning raw candidate text, make clear that the implementation still needs safe dynamic-value handling.

For internationalized names, use filename* with UTF-8 extended-value encoding and an appropriate ASCII filename fallback. [RFC 8187 section 3.2](https://www.rfc-editor.org/rfc/rfc8187.html#section-3.2) defines the charset, optional language and encoded-value structure. Encode UTF-8 bytes, not Unicode code-point numbers. Spaces use percent encoding rather than form-style plus substitution; the extended value is not a quoted string. Do not encode the whole header as a URL or apply encoding twice.

Keep the ordinary filename fallback simple and correctly quoted when necessary. Do not put percent escapes there and assume every client decodes them. Do not copy email attachment continuations or multipart form-upload syntax into a download response.

Name one layer responsible for the final Content-Disposition value. Inspect append-versus-replace behavior at the application, proxy and storage boundary. A correct application value can become ambiguous when another layer adds its own value. Retain unrelated security, caching and access-control configuration.

If the platform is known, provide the scoped configuration fragment and exact insertion point. If it is unknown, deliver the header contract without inventing deployable syntax.

## 4. Reconcile server and client naming

Inspect any download attribute, filename parser, Blob creation and save action in the selected client. Do not assume a fetched attachment automatically starts a browser download or that a filename from the original HTTP response automatically transfers to a client-created object.

The [HTML download model](https://html.spec.whatwg.org/multipage/links.html#downloading-resources) includes origin and safety decisions and produces a suggested filename. A candidate should not promise an exact save dialog, path or final disk spelling across all browsers and user preferences.

For a cross-origin script that reads Content-Disposition, include that exact response-header requirement in the CORS handoff. It is not among Fetch's default [CORS-safelisted response headers](https://fetch.spec.whatwg.org/#cors-safelisted-response-header-name). Server headers being visible in a network inspector does not prove application code can read them. Preserve the approved audience and credential mode; do not broaden origins to make naming work.

Keep direct-download and script-driven results separate. If one works and the other remains unresolved, report that boundary instead of claiming the endpoint is universally fixed.

## 5. Review the candidate and hand it off

Read back the complete candidate against the naming policy and response-class map. Use a compact set of authored cases that exposes the actual decisions:

- An ordinary successful file
- A name containing a space and non-ASCII text
- A rejected line break or path-like name
- An empty or colliding fallback
- An error or authentication response
- The actual script-reading branch, if present

For each, record expected metadata, filename disposition and held dependency before reviewing the candidate. These are static decision cases unless an authorized client actually exercises them.

A later verification worksheet should name environment, browser/client, harmless file, expected status/media type, served header, script-visible header where applicable, and actual saved name. Keep download receipt, filename observation and content identity as separate evidence. Do not open executable downloads, bypass browser warnings, overwrite existing files or run live exports as incidental validation.

Return the response-class map, header/configuration candidate, naming transformation and fallback, owning layers, client dependencies and precise verification status. Preserve the before-state for any proposed configuration replacement. After an uncertain change, inspect current state before retrying; do not stack additional headers onto an unknown result.

Finish at the requested preparation boundary. A source-reviewed package is not proof of deployed headers, browser behavior, content correctness or download completion.

## Fictional illustration, not executed

A fictional archive supplies an existing PDF producer and asks for the suggested name `Café notes.pdf`. Its approved ASCII fallback is `Cafe notes.pdf`. The prepared successful-response candidate is:

```http
Content-Type: application/pdf
Content-Disposition: attachment; filename="Cafe notes.pdf"; filename*=UTF-8''Caf%C3%A9%20notes.pdf
```

The error branch remains application/json without the successful file's attachment header. A title containing a line break is rejected before header construction rather than escaped into another header line.

The direct-navigation client and a cross-origin script client are listed separately. The latter's header-reading requirement remains with the existing CORS owner; no new origin is silently admitted. Expected review outcomes are a coherent PDF contract, one safely serialized filename pair, and an explicit client dependency.

This is an authored, unexecuted illustration. No file was generated, header parser run, endpoint called, browser download performed or configuration deployed.
