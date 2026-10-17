---
name: correct-photo-capture-times
description: "Correct the capture chronology of a bounded photo collection using supported clock evidence, preserved originals and asset relationships, and verified metadata or library readback. Use for camera-clock and capture-date repairs, not changing file modification times, identifying people or editing image content."
---

# Correct photo dates without losing the original chronology

Deliver a corrected photo collection or an explicitly scoped native-library update, with an exact old-to-new time map and remaining ambiguities. Preserve the image content, original evidence and paired assets. A gallery that sorts differently is not by itself proof that the intended capture timestamps were corrected.

Use [photo-selection-caption-review](../photo-selection-caption-review/SKILL.md) for choosing pictures and grounding captions, and [audit-file-metadata-transfer](../audit-file-metadata-transfer/SKILL.md) for checking attributes after a transfer. This skill changes supported capture-time metadata. It does not geotag photos, infer an itinerary from private images, retouch pixels, deduplicate a library or make evidence-authenticity claims.

## Establish the collection and desired result

Identify the exact files or native asset IDs, source application/library, camera or clock groups when known, observed problem, trusted time references and requested destination. Determine whether the user wants corrected copies, metadata changes inside an existing library, or both. A library-only adjustment and an embedded-file edit have different downstream effects.

Useful evidence includes a documented camera-clock error, a photograph of a clock whose time and timezone are independently known, a reliably matched reference-camera capture, or the user's specific correction. A filename, upload time, filesystem creation date or nearby photo is only a clue unless its relationship to capture time is established. Ask the smallest question that determines the change; do not ask for a full travel history when a verified offset suffices.

Confirm the selected population before a batch edit. A folder may contain multiple cameras, screenshots, scans, downloaded pictures, edited versions and clocks reset halfway through a trip. Use source identity and actual observations to partition it; do not apply one apparent error to everything with a similar filename.

A request to correct the selected library can authorize its scoped metadata edit. Check whether that library is synchronized or shared and whether the requested change covers those effects. Do not silently import copies into a shared album, overwrite source files, enable cloud synchronization or change global metadata-writing defaults. Keep reports private because timestamps and source names can reveal personal routines.

## Preserve assets and read time fields with their meaning

For local work, preserve an unchanged original set and write to a separate destination. Record each file's source identity, byte digest, type and selected output path. For a native library, use stable asset IDs and a supported original/metadata record before editing; do not manipulate the application's private database. A catalog backup may preserve editing records without containing the original photo bytes, so establish which recovery material actually exists.

Inspect effective automatic writeback before a native edit or pilot: an existing setting can write source files or sidecars even when this task does not change the setting. A copied catalog, virtual copy or duplicate library record may still point to the same underlying originals. It is not an isolated file copy. If the available route cannot preserve the required originals, hold that route and propose a genuinely separate working copy or the exact setting change needing approval.

Inventory related assets without merging them: RAW plus JPEG, burst members, sidecars, an edited derivative and its original, or the still and motion parts of a compound asset. Do not assume equal basenames prove a relationship. Retain known pair identifiers and necessary companion files. Use the native supported edit for a compound asset where available; separately altering just its still image may break chronology or pairing in the consumer.

Read the relevant timestamp fields with their namespace, raw value, precision and offset evidence. Distinguish:

- The capture/original time, including any associated fractional-second and UTC-offset field
- Digitization or scan time, which can legitimately differ from the photographed scene's date
- File or metadata modification time and filesystem creation time
- Native-library display time, which may be an adjustment over the stored original
- Motion/container or track timestamps when a paired asset requires them

A missing offset means the instant may be unknown; it does not mean UTC. A timezone is a rule set for dates and clock changes, while a numeric offset describes one relationship to UTC. Do not apply today's offset to an earlier date. Preserve precision instead of turning whole-second evidence into invented milliseconds.

Read all relevant namespaces rather than trusting a flattened “Date” field. Different readers can select different tags or convert a stored instant to the computer's display timezone. ExifTool's [QuickTime tag reference](https://exiftool.org/TagNames/QuickTime.html) warns that cameras can store local clock values in integer fields whose specification expects UTC. Its UTC option changes interpretation; it is not a repair switch to apply indiscriminately. Treat container timestamps as a separate supported profile, and hold them when their semantics are unknown.

Do not copy every date field into every other field. In particular, a scan's digitization date and a later edit's modification date should not automatically become the scene's historic date. Keep GPS coordinates, camera identifiers and other unrelated metadata unchanged, and avoid sending them to an online timezone or geocoding service.

## Derive the correction before writing

Create a small transformation map per supported clock group:

`asset IDs; old field/value/offset; evidence; correction type; exact proposed value/offset; fields allowed to change; consumer; unresolved limits`

Choose the correction type explicitly:

1. **Fixed clock error:** add the evidenced signed duration to each selected old capture value. Preserve intervals between photos unless there is evidence that the error changes.
2. **Wrong or missing timezone interpretation:** establish whether the local clock text is correct and its offset is wrong/missing, or the represented instant is correct and only its local display is wrong. Reinterpretation and conversion are different operations; applying both can introduce a second shift.
3. **Known per-asset date/time:** set that value from a specific source rather than deriving a batch shift.
4. **Incomplete historic date:** retain the known year/month/day precision in the report or a suitable supported field. Do not fabricate midnight, a day of the month or a timezone merely because a timestamp field requires it. A user-approved sorting convention must remain labeled approximate and separate from a claimed exact capture instant.

For a fixed correction, check the sign against a trusted anchor and calculate expected values on both sides of any day, month or year boundary. Check another independent anchor when available. If the error changes after a camera reset, split the group at supported boundaries. A drifting clock or two contradictory anchors is not a constant-offset problem; return the conflicting evidence and hold that group unless a justified per-asset mapping is supplied.

For local times near a daylight-saving transition, establish which occurrence of a repeated time is meant, or flag a nonexistent local time. Do not choose a convenient interpretation merely to make the sequence monotonic. Burst photos and multiple cameras may legitimately share timestamps; do not introduce artificial offsets to force a unique ordering.

Construct proposed values from the preserved baseline, not from whatever the latest partially edited file currently displays. This makes a retry detectable and prevents the same two-hour correction from being applied twice. Keep already-correct assets in the accounting with an explicit no-change disposition.

## Select a supported editing route and pilot it

Choose the smallest route that satisfies the user's target:

- Native-library edit when the intended result is correct chronology in that library
- Supported metadata edits on separate file copies when another consumer needs embedded values
- A supported sidecar when the target consumer actually reads that sidecar's capture-time fields
- A correction manifest when the required write format, source identity or consumer interpretation is unsupported

Do not call a sidecar-only result an embedded-file repair. Do not transcode a photo merely to gain a writable date field without the user's agreement to that changed deliverable. Use the installed tool's current documented tag and format support; a readable tag need not be writable.

In Apple Photos, the [documented date/time adjustment](https://support.apple.com/guide/photos/add-titles-captions-and-more-phta4e5a733f/mac) includes both an adjusted time and a timezone choice. Inspect the resulting value and batch behavior rather than assuming that selecting a city only changes the label. A Photos display edit does not prove what a later unmodified-original export will contain.

In Lightroom Classic, [capture-time editing](https://helpx.adobe.com/lightroom-classic/desktop/organize-photos-in-lightroom-classic/metadata-basics-actions.html) depends on selection mode: Grid can apply a common adjustment to selected photos, while other views can affect only the active photo. It can also update the digitized-time field. The documented reversal is Revert Capture Time To Original rather than ordinary Undo. Check these effects against the desired field map before proceeding. [Catalog settings](https://helpx.adobe.com/lightroom-classic/desktop/manage-catalogs-and-files/create-catalogs.html) separately control writing date/time changes into proprietary RAW files; do not enable that globally to complete a catalog-only request.

Use a representative small pilot before the full batch when formats or batch semantics vary. Include an anchor, a boundary-crossing image and a paired/RAW asset if present. Check the saved pilot in the intended consumer. If it sets every image to the same time, drops precision, changes an unexpected field or breaks a pairing, stop before the remaining collection. Preserve the failed candidate for diagnosis without presenting it as corrected.

For direct file edits, restrict writes to the exact supported timestamp fields and required representation companions. Avoid broad “all dates” or copy-all-metadata operations that rewrite scan times, location, ownership or edit history. Retain tool-generated backup files if applicable; do not disable backups merely to avoid clutter. Capture any documented metadata normalization or unsupported preservation rather than hiding it.

## Verify the saved result and actual consumer

Reopen the saved files or exact library assets. For each changed asset compare the actual new time with the proposed map, retaining the original value and evidence. Verify all rows programmatically when suitable supported readers are available; do not infer a whole batch from the first image's dialog.

Check separately:

- Selected assets account for changed, unchanged, held, failed and uncertain outcomes without duplicate application
- Every constant-offset group preserves its pairwise time differences and uses the intended signed correction
- Offsets, fractions and date boundaries follow the approved interpretation, and unknowns remain unknown
- Required original bytes remain unchanged; edited copies have separately recorded identities
- Paired assets, filenames, native edit relationships and necessary sidecars remain usable
- Relevant non-time metadata, dimensions, orientation, color interpretation and image content are preserved to the supported inspection boundary
- The target application reads and sorts by the corrected field, rather than filename, import date or a stale cached value

A metadata edit normally changes the whole-file digest, so a differing digest is expected for the candidate; it does not prove the pixel content changed. Use supported image-data comparisons or the format's preservation evidence, plus visual inspection of representative saved outputs. State whether image payloads were compared or only decoded appearance was inspected. A thumbnail-only view cannot establish full-resolution integrity, and an unchanged rendering does not establish every metadata field survived.

If corrected exported files are part of the request, inspect those actual saved files and reopen them in the named receiver. Library display, sidecar state and embedded metadata must have separate verdicts. Do not claim portability when only the source library was checked. Do not flush the entire photo cache or rebuild a library to force an apparent result.

## Recover partial work and deliver

On an interrupted or uncertain write, reread the exact affected asset before retrying. Classify it by baseline and expected result; do not repeat a relative shift on already corrected files. Hold unexpected intermediate values and preserve both copies. Continue unaffected groups only when the batch boundary is clear.

For file-copy work, leave originals in place and deliver only checked candidates. For a library rollback, restore recorded values through the supported interface within the existing authority, after checking for later user edits. A “revert to original” action may discard an older intentional adjustment that preceded this task; do not use it as a substitute for restoring the actual pre-task state. Never restore an entire catalog over concurrent unrelated work to undo a few timestamp changes.

Return the corrected copies or library/asset references, the supported clock explanation, the old-to-new map, held assets and exact verification limits. State which representation changed and which did not. This is an organizational correction, not proof of when a scene truly occurred. Do not alter timestamps to misrepresent evidence or remove the correction history from a record intended to document provenance.

## Fictional, unexecuted illustration

A fictional camera group has an independently documented clock that ran two hours fast. Two originals read December 31 at 23:40 and January 1 at 00:10, with no reliable timezone information. The intended correction subtracts two hours, producing December 31 at 21:40 and 22:10, preserving the 30-minute interval and leaving the offset unknown.

A scanned print in the same folder has only “summer 1982” as its scene-date evidence. It remains outside the camera shift; its scan timestamp is preserved and its approximate scene date stays in the review record. A paired motion asset with unresolved container-time semantics is held rather than rewritten with the still-photo rule.

These are invented paper values, not executed transformations. No photos, libraries, metadata, location services or cloud accounts were accessed or changed for this illustration.
