---
name: prepare-video-proxy-handoff
description: "Create or repair an editing project's proxy-media associations, preserve the route back to the correct full-resolution sources, and deliver the project with a bounded proxy package and explicit finishing limits."
---

# Prepare a video proxy handoff

Deliver an editable project whose lightweight media represents the intended source clips, together with the requested proxy files and a usable reconnect record. A folder of smaller movies is not an attached proxy workflow, and a project that plays is not necessarily using the right takes.

Use this for preparing an existing project for lightweight or offline editing, attaching supplied camera/editor proxies, or repairing wrong proxy associations. This is not editorial assembly, a generic playable-file conversion, recovery of missing original footage, or an assertion that proxies replace an archive. [Create an edited video](../create-edited-video/SKILL.md) owns the cut and final viewing deliverable; [media export compatibility](../media-export-compatibility/SKILL.md) owns a target-format conversion. Do not rebuild the edit just to attach proxies.

## 1. Identify the project and the intended handoff

Establish the application/version, exact project/library revision, selected clips or sequences, original-media locations, existing proxies, destination and recipient's available editor. Determine whether the user wants local preparation, a proxy-only editing handoff, or a package including full-resolution media. Ask only for choices that affect the result. A short local project can use a small readme rather than a production database.

Work in a separately saved project copy and a distinct output location. Preserve original media, its directory/card structure and the previous project. Do not move originals, rename camera files in place, delete generated files, change shared storage, install codecs or upload footage just because those actions might simplify preparation. Verify whether an output location is synced or already shared. Actual sending needs authorization for the particular files and recipient/destination; reduced resolution does not make private footage non-sensitive.

Inspect the available editor's supported proxy operations before choosing a method. Creation, attachment, relinking an offline source, and reconnecting a full-resolution representation are different operations. For example, Adobe documents separate [Attach Proxies](https://helpx.adobe.com/premiere/desktop/organize-media/ingest-proxy-workflow/attach-proxies-to-full-resolution-media.html) and [Reconnect Full Resolution Media](https://helpx.adobe.com/premiere/desktop/organize-media/ingest-proxy-workflow/reconnect-full-resolution-media-to-proxies.html) paths. Do not replace the project item's source with a small movie and assume it now has a reversible proxy association.

If the editor is unavailable, prepare a source/proxy map and specific attachment instructions, but label the project attachment and reopen checks unperformed. If originals are missing, distinguish evidence supplied by the user from media actually inspected. A proxy can support continued editing without establishing that the correct original can later be recovered.

## 2. Map identities before batch matching

Build a compact record for the selected clips. Include only fields useful to the particular project:

- Project item/bin identity and full-resolution source path or stable media identity, retaining card/reel context
- Proxy path and provenance: supplied camera proxy, editor-generated file, or derivative of a named source revision
- Duration, source start timecode and timecode convention where present; frame-rate interpretation and relevant frame-count evidence
- Image dimensions, pixel aspect, orientation/field order, and audio channel count/roles where relevant
- Current association, proposed association, and any unresolved conflict

Use checksums to distinguish copies of the same representation where useful, not to require compressed proxy bytes to equal the original. File size and extension do not prove which take a proxy depicts. Metadata is corroborating evidence, not a unique identifier: two cards can contain identically named clips, reset timecode and similar durations. Inspect corresponding picture landmarks and audio content when capabilities permit. Do not infer content agreement from a filename match or thumbnail alone.

Distinguish multiple project items referring to one source from distinct recordings that happen to share a name. Preserve existing source interpretation, audio mapping and sequence placement. If relinking proposes an unexpected many-to-one association, resolve it before acceptance rather than assuming duplicate footage.

Record how each ambiguous pair becomes resolved. If source footage is absent and there is no reliable production map, leave identity uncertain. Avoid a global search across unrelated folders to make all missing-media warnings disappear.

## 3. Choose a compatible proxy representation

Prefer the editor's supported creation mechanism when the originals are present and the intended format is supported. Read current product guidance for the actual media type and version. Adobe's [creation guidance](https://helpx.adobe.com/premiere/desktop/organize-media/ingest-proxy-workflow/create-proxies.html) limits which items can be proxied and describes editor-to-encoder jobs, destination choice and optional proxy watermarks. Apple's [optimized/proxy guidance](https://support.apple.com/guide/final-cut-pro/verb8e5f6fd/mac) distinguishes optimized media from proxy representations. Do not use the names interchangeably.

Choose the representation for responsive editing, storage constraints and the recipient's supported workflow, not merely the smallest output. Record the preset/version and deliberate changes. Estimate room for the proxy set and working outputs before starting, and retain the selected source list as the denominator for completion.

Maintain the clip's temporal correspondence and editorial geometry. Do not trim handles, concatenate takes, change playback speed, normalize all clips to a guessed frame rate, crop the picture or downmix channels as incidental proxy creation. Inspect variable-rate, interpreted slow-motion, anamorphic, rotated, multichannel and unusual-duration material separately rather than applying a universal preset. If the editor cannot support the source as an attached proxy, identify the limitation and a separately scoped conform workflow instead of silently changing the original-media contract.

Adobe's [reference manual](https://helpx.adobe.com/pdf/premiere_pro_reference.pdf) describes matching frame rate, duration, fielding and audio channels for its proxy workflow. Check the applicable installed version; successful attachment alone is not proof of compatibility. A codec/preset that discards required audio channels is not repaired by renaming the output.

Keep color interpretation explicit. Record any baked viewing transform, watermark or burn-in so it is not mistaken for source pixels or applied again unintentionally. Proxy review is not approval of final color, fine detail, noise reduction or compositing quality. Do not claim visual equivalence when a transform or reduced detail is intentional.

Create a small representative pilot before processing the selected set, including the source types that could fail differently. Inspect actual job state and existing outputs before retrying an uncertain job. A queued or partly written file is not a completed proxy. Use a new candidate for corrected settings; do not overwrite an uncertain existing proxy or discard previous results without authority.

## 4. Attach deliberately, then inspect the associations

Use the supported proxy attachment operation in the project copy. Select matching criteria appropriate to the source map. Adobe's attachment dialog can automatically link other matching clips; leave such expansion off when the criteria are ambiguous, then verify every proposed association within the selected scope. A valid pairing for one card does not establish a matching rule for all cards.

After attachment, inspect the editor's resolved paths and representation status. Reconcile each selected item as attached, intentionally unsupported, failed or unresolved. Reopen problem items individually. Correct a wrong association through the application's supported detach/re-attach path in the working copy; do not delete the wrong file merely to force an offline warning.

Check the pilot and risk-sensitive clips in the actual project:

1. Switch between original/full-resolution and proxy representations at corresponding early, middle and late source positions. Confirm the same take and action, complete endpoints and stable alignment, not just similar duration.
2. Inspect framing, aspect, orientation and any crop/transform-sensitive edit. Reduced detail may be expected; shifted subject placement or a different frame is not explained by lower resolution.
3. Check required audio channels and synchronization using actual listening capability where available. A waveform or playback command is not evidence of listening. Attribute operator observations rather than claiming them as direct review.
4. Inspect sequence in/out points, transitions, speed-altered sections and multicamera uses affected by the selected sources. Attachment must not quietly change edit decisions or media interpretation.
5. Save, close and reopen the candidate project when available, then recheck representation paths and representative playback. Report the actual coverage; sampling does not prove every frame of every clip correct.

If a mismatch appears late in a clip, investigate source identity, timing and conversion settings. Do not conceal it by slipping the timeline or retiming the proxy while calling the association repaired. Keep the last known project copy and the failed candidate distinguishable.

## 5. Package for the intended availability of originals

Use the application's supported copy/consolidation route when needed. Include the saved project, selected proxies and required non-proxy dependencies within the agreed scope, such as sound, graphics and captions. A proxy association does not package those other dependencies. List intentionally external items and missing originals separately.

Preserve the original-to-proxy map and a concise full-resolution reconnect procedure. For a proxy-only package, state plainly that finishing requires the identified originals and any other excluded dependencies. Do not call it a complete master archive. Avoid exposing unnecessary private source paths in the recipient readme; retain sufficient authorized reel/card identity to disambiguate reconnects.

Open the delivered copy from its intended location and verify its resolved references. A project that finds proxies through the authoring machine's old path has not demonstrated package portability. Where a proxy-only check is needed, use an isolated copy or supported scoped relink workflow; do not disconnect shared drives or move originals merely to simulate absence. If isolation cannot be demonstrated, report that limitation.

Treat playback selection and export selection separately. Adobe's [export guidance](https://helpx.adobe.com/premiere/desktop/organize-media/ingest-proxy-workflow/export-proxies.html) says its default export uses full-resolution media despite the editing proxy toggle, while explicit proxy/preview export settings can change the source used. Apple advises returning to optimized/original media before sharing in its proxy guidance above. Follow the actual editor, not a cross-application assumption.

This handoff need not export a final movie. Give the recipient the concrete finishing gate: reconnect and verify correct full-resolution sources, resolve remaining dependencies, and inspect the actual export settings before claiming a full-quality result. If export was separately requested, use the final-video workflow and inspect that exact output.

## Deliver and stop

Lead with the project and proxy package. Include the selected/attached/unresolved counts, source map, editor/version, storage layout, important representation choices, reconnect instructions, and checks actually performed. Separate file creation, project attachment, isolated reopening, playback/listening and recipient use. State whether the result is ready for proxy editing, ready for verified full-resolution finishing, or blocked on named sources.

Stop when the requested package works to the stated inspection level, or the remaining source/capability/decision is explicit. Do not publish, share, delete originals or start a new editorial cut as a follow-on.

## Fictional, unexecuted illustration

A fictional travel-film project contains `CardA/C001.mov` and `CardB/C001.mov`. Both have the same duration and start timecode; one depicts a bridge and the other a station. A folder contains a single `C001_Proxy.mov` showing the station. Filename and duration matching must not attach it to both project items. The expected result is a verified association for CardB and an unresolved or newly generated proxy for CardA, preserving their separate identities.

If CardB's supplied proxy drops an isolated microphone channel, the expected repair is a compatible derivative or a clearly held item, not an unexplained downmix. A proxy-only handoff would identify both full-resolution sources needed later. No editor, source footage, encoder, attachment, file package, playback, listening or export was exercised for this illustration; it describes decisions only.
