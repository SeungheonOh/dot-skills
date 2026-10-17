---
name: import-photo-library-batch
description: "Import a bounded photo and video batch into an existing native library or catalog, preserving original locations, companion assets and prior imports through source-to-library reconciliation. Use for usable library ingestion, not photo selection, library migration, deduplication, editing or backup setup."
---

# Import a photo batch without losing its originals

Deliver the selected photos and videos in the intended existing library, with usable originals, accounted companion files and a short import record. A thumbnail, an import-complete message and a copied original are three different pieces of evidence. The useful result connects each selected source asset to the correct library item and actual retained media.

Use [photo-selection-caption-review](../photo-selection-caption-review/SKILL.md) for choosing pictures, [correct-photo-capture-times](../correct-photo-capture-times/SKILL.md) for chronology repairs and [configure-versioned-file-backup](../configure-versioned-file-backup/SKILL.md) for a backup job. This workflow imports a selected batch through an existing supported app. It does not merge libraries, recover damaged cards, reorganize an entire collection, identify people, change camera settings or clear source storage.

## Establish the batch and destination

Identify the source device or folder, exact selected population, application/version, existing library or catalog, intended original-storage location and optional album or collection. Distinguish the library from an album within it, and the catalog file from the media files it references. Ask only for a missing choice that changes storage, membership, exposure or preservation.

Establish whether the user wants a preparation plan or an actual import. For an actual import, determine whether originals should be copied into the library, copied to a chosen permanent folder and cataloged, or referenced in their already permanent location. A temporary download folder or removable camera card is not a permanent original store merely because an app can display it.

Inspect effective cloud and sharing behavior before the first import, including any pilot. A private-looking local library may automatically upload new assets, and a selected album or library may have other participants. Obtain required approval for the selected media, service and audience before that transmission. An import request does not authorize enabling synchronization, adding shared-library members, changing permissions, subscribing to storage or moving the whole library. If the chosen route would expose more than authorized, hold the import and ask for the specific destination decision; do not silently disable account-wide sync.

Use the installed app's supported interface. Do not edit its private database, inject files inside its library package or use internal caches as original files. New software, device-trust prompts and expanded photo-library or removable-volume access need their applicable approval. Leave device unlocking and credential entry to the user through supported flows. If physical access is needed, have the user identify and connect the intended device; do not claim that a remembered device name proves its current presence.

## 1. Account for source files and logical assets separately

Before writing, make a bounded inventory outside any automatic import/watch folder. For a small batch, a compact note is enough; mixed formats and interrupted imports need a per-asset map. Record:

- Source device/volume and exact path or native item identity, with the selection boundary
- Original filename, type, byte size and a digest when ordinary file access permits it
- Logical asset grouping and its evidence: single image, RAW/JPEG pair, motion-photo components, video, burst members or separate edited derivative
- Required companions such as XMP sidecars, plus unsupported or unexplained files
- Intended destination representation and any existing-library match

Keep file counts, media-asset counts and visible library-item counts distinct. A sidecar can be required without becoming a picture. Two source files can become one paired item, while a burst or stack can hide multiple items. Do not discard a JPEG because a RAW shares its basename, or treat an edited derivative as redundant merely because it depicts the same scene.

Use known native identifiers and documented importer behavior to establish compound relationships. Equal basenames across different camera folders are not sufficient, particularly after filename numbering wraps. Preserve the full relative path and companion relationships. If a proposed flat destination would collide, choose a supported noncolliding folder layout within scope or hold that group; never let overwrite or automatic suffixing silently decide identity.

Check that selected originals are actually readable. A phone/cloud thumbnail or optimized placeholder may not supply full-resolution bytes through the available route. If the source interface does not expose filenames, complete enumeration or byte reads, record that limit and use its supported item identities; do not invent hashes or claim byte completeness. Do not hydrate an entire cloud library to resolve a few unavailable selected items.

Do not change dates, orientation, ratings, captions, locations or pixels as incidental import cleanup. Preserve source evidence for mismatches. If files appear corrupt or the device disconnects repeatedly, stop repeated acquisition attempts and report the affected items; this is not a disk-recovery workflow.

## 2. Choose the actual import representation

Read current official documentation for the specific app, platform and source route, then inspect the available controls. Similar product names and button labels do not imply the same storage model.

### Copied versus referenced originals

For Apple Photos, inspect the existing library and its import preference. Apple's [storage guidance](https://support.apple.com/guide/photos/change-where-photos-and-videos-are-stored-pht1ed9b966d/mac) explains that disabling copying leaves imported files referenced in their original location; those external files are not included in iCloud Photos or a backup of the library itself. A later rename, move or disconnected source can therefore break access. Do not choose referencing solely to reduce disk use when the user's purpose is to retain the camera batch independently.

For Lightroom Classic, [folder import](https://helpx.adobe.com/au/lightroom-classic/desktop/import-photos/import-photos-video-catalog.html) distinguishes Add, Copy, Move and Copy As DNG. Add retains the current file location; Copy creates files at the selected destination; Move removes the prior location; DNG conversion changes the representation. Use the mode that matches the approved preservation contract. For a source-preserving import, use an appropriate copy or permanent-reference route, never Move as a convenient equivalent. [Camera/card import](https://helpx.adobe.com/lightroom-classic/desktop/import-photos/importing-photos-lightroom-basic-workflow.html) has a narrower choice of copy methods and includes sidecars with Copy.

Do not substitute the cloud-oriented Lightroom app for Lightroom Classic. Adobe's [Lightroom add-photos instructions](https://helpx.adobe.com/lightroom/desktop/add-import-and-capture-photos/add-photos.html) describe copying and uploading full-resolution originals when photos are added. That destination effect needs its own scope check even when the user already has an account.

Choose a real existing destination with sufficient observed free space for originals and expected application working data. Unknown expansion or quota stays a limit. Preserve existing files, folder structure and unrelated import presets. An album name does not establish a physical original-storage location.

### Pairs, companions and import-time changes

Inspect how the app will represent each required asset group. Lightroom Classic's [import preferences](https://helpx.adobe.com/au/lightroom-classic/desktop/import-photos/file-import-formats-settings.html) determine whether a neighboring JPEG becomes a separate photo or a companion to its RAW. Apple Photos' [RAW-original guidance](https://support.apple.com/en-gb/guide/photos/phtbb0eb4eb1/mac) describes selecting which member of a RAW/JPEG capture is used as the original. A visible JPEG rendering does not by itself prove that the RAW was omitted.

Preserve the user's requested representation; do not change a global pair preference or switch the active original merely to make counts agree. If a setting change is needed for this batch, record its old value, scope and restoration plan, with the applicable authorization. For motion photos or another compound format, use a supported import route that retains the relationship. Two separately visible files are not proof of a working compound asset.

Check renaming, automatic culling, metadata/develop presets, keyword injection, conversion and automatic metadata writeback before importing. Existing presets may transform the new items or write to source files/sidecars. Suppress unwanted effects through supported scoped controls when authorized; otherwise hold the affected route. Do not overwrite a shared preset or silently apply ratings and edits from a sidecar whose intended authority is unknown.

If the app cannot retain a required companion or interpretation, preserve it in the authorized unchanged source or separately approved holding folder and mark native ingestion partial. Keeping an XMP file beside a picture does not prove the app consumed its values, and a saved sidecar is not a replacement for unavailable original pixels. Do not transcode or flatten assets just to make the import accept them without agreement to that different deliverable.

## 3. Resolve prior imports before creating new items

Inspect the chosen library's relevant existing items and native import history, where supported. Match using the strongest available combination of exact source identity, original bytes, media properties and native provenance. A common filename, capture time or matching thumbnail alone cannot prove that a selected asset is already represented at the required quality.

Separate these dispositions:

| Source asset | Decision before import |
| --- | --- |
| Confirmed absent within adequate relevant evidence | Selected for new import through the chosen route |
| Confirmed present with the required originals and companions | Reuse the existing item; add album membership only if requested |
| Importer suspects a duplicate, but identity or completeness is unproved | Hold or investigate the specific match; do not call it complete |
| Unsupported or unreadable required representation | Preserve source and report the blocked component |
| Deliberately outside the selected batch | Exclude explicitly; do not use it to fill a missing count |

Adobe documents Lightroom Classic's [suspected-duplicate rule](https://helpx.adobe.com/in/lightroom-classic/desktop/import-photos/photo-video-import-options.html) in terms of original filename, Exif capture date/time and file size. That is an importer heuristic, not a byte comparison. Conversely, identical bytes can legitimately be separate source occurrences. Do not disable duplicate protection for the entire batch or rename originals to evade it without resolving the specific representation the user wants.

An existing library item can satisfy original-media presence while still lacking the requested album membership. A copied item may have prior edits, captions or favorites that must remain intact. Keep reuse, membership changes and new import separate; do not replace an established item merely to obtain a cleaner import history. Absence in a filtered album or a truncated search is not proof of absence from the library.

## 4. Import a representative group, then the remainder

Review the actual source selection, destination, mode, pairing, conversion, preset and deletion controls immediately before submission. Avoid automatic deletion after import. Apple's [camera import instructions](https://support.apple.com/guide/photos/import-photos-from-a-camera-or-phone-pht6c803201/mac) include a source-deletion choice on supported routes; leave that action out of this source-preserving task. Inspect whether an automatic eject would make the planned verification harder before relying on it.

For an unfamiliar or mixed batch, use a small representative group already within the authorized selection. Include the fragile relationship actually present, such as a RAW/JPEG pair with a sidecar or a motion asset, rather than inventing test files. A successful pilot can remain part of the final import; record it so it is excluded from the next submission.

Let the native operation finish, retain its warnings and identify the created items through supported IDs or a reproducible locator combining batch, filename and media information. An import collection can change on the next operation, so preserve enough information to find this batch independently. Reopen the actual items and check original availability and companion behavior before continuing with the rest.

If the pilot unexpectedly changes source files, creates the wrong representation, reaches an unapproved service or audience, or omits a required companion, stop the dependent import. Keep the source and observed result; do not repair the whole library, reset preferences or delete the pilot as an automatic undo.

Continue in coherent groups that preserve related files. Record each attempt's selected source identities and observed imported, reused, rejected or uncertain results. Preserve the distinction between selecting thumbnails and checking them for import when the app uses separate states. Do not infer all selected files were submitted merely from a highlighted region.

## 5. Reconcile the saved library with retained originals

Use the original selection map as the denominator, not the application's latest success count. Assign every selected asset a final disposition: imported and verified, confirmed already present, held, failed or uncertain. Account for each required companion within that asset. Reconcile new library items separately from existing items reused and source files retained.

Check the properties that determine acceptance:

1. **Membership and identity:** every requested asset is represented once under its intended grouping, with no accidental replacements or unexplained omissions; album/collection membership is checked separately
2. **Original location and availability:** copied originals are at the approved destination, or referenced originals point to the agreed permanent location; a cache or a camera-card reference is not called a retained copy
3. **Original preservation:** when supported original-byte access is available, compare the selected source and retained originals by digest; report source-read or export limits rather than assuming byte equality
4. **Native usability:** open actual imported items at useful resolution, inspect representative RAW/pair behavior and play required motion/video content through the intended app; record the inspected subset and any decode failures
5. **Requested metadata and companions:** verify the fields or relationships that matter, without assuming every source tag or sidecar edit was preserved; unexpected interpretation remains visible
6. **Exposure and completion:** state local import and cloud-upload completion separately, and verify any requested remote result only within its authorized destination

For an opaque managed library, prefer supported original export to a new private check folder when that export is authorized and needed; do not browse or modify undocumented package internals to manufacture a byte claim. Apple's [export guidance](https://support.apple.com/guide/photos/export-photos-videos-slideshows-and-memories-pht6e157c5f/mac) distinguishes unmodified originals from rendered exports and notes that a Live Photo exports as still and video files. Preserve the export's component map and compare the actual representations. A JPEG rendered from RAW is not the original RAW, and a screenshot or thumbnail cannot establish full-resolution preservation.

A change from the camera preview to an app's RAW rendering can be a rendering difference rather than corrupt copied bytes. Investigate the exact representation and decoder before promising visual equivalence or altering pixels. Successful sampled viewing is useful consumer evidence, not proof that every byte or metadata field in the entire batch is valid.

When independence from removable media matters, establish original paths and supported full-original readback. A safe eject and reopen check can add evidence only after all writers are finished and the source is not needed by other work; never pull an active drive. Cached previews can still display after removal, so reopening a thumbnail alone does not prove independence. Leave this property unverified if the route cannot expose original availability safely.

## Recover partial imports without multiplying items

After a timeout, app interruption or device disconnect, inspect the existing attempt, current library entries and destination files before retrying. Source files copied without a catalog record, records with missing originals and fully completed imports need different treatment.

- For confirmed completed assets, retain their mapping and omit them from retries
- For copied-but-uncataloged originals, check identity and destination first, then use a supported catalog-add path only if it preserves the approved result; do not create a second copy automatically
- For a catalog record whose required original or companion is missing, retain the evidence and use a supported scoped recovery decision; a fresh import can create a separate item instead of repairing that record
- For uncertain or duplicate-suspected results, hold those assets until actual identity and persistence can be established
- For a full destination or denied access, preserve partial results and request the exact storage/access decision; do not delete photos, buy space or broaden permissions as a retry

Do not rerun the entire batch after an ambiguous response or replace current user edits from a stale pre-import record. Removing an item from an album, removing its catalog record and deleting its stored original are different actions. Any requested rollback needs the exact affected identities, current concurrent edits, actual deletion/sync effects and applicable approval. Never restore an entire catalog over unrelated work to undo one import.

## Deliver the result and its retention boundary

Return the library/catalog and destination references, batch entry point, source-to-item map, original-storage mode, companion treatment, dispositions, checks performed and specific gaps. Keep private source names and metadata out of any report intended for other people. A simple successful batch may need only a few lines plus the relevant item references.

Call the batch imported only to the verified coverage: a partial result remains partial even if all visible thumbnails look correct. A prepared plan or an inaccessible target is not an executed import. State byte verification, native viewing and cloud synchronization independently when their evidence differs.

Leave source originals and card contents intact. Native import is not a backup certification: Adobe's [catalog-backup guidance](https://helpx.adobe.com/lightroom-classic/desktop/manage-catalogs-and-files/back-catalog.html) explicitly separates the catalog from photo files that need their own protection. Any second copy made during import also needs its actual destination and coverage checked before it is described as protective. Do not declare the card safe to erase, remove a staging source used by references, empty Recently Deleted or initiate an unrelated backup job. Stop when the bounded import and its unresolved preservation decisions have been handed back.

## Fictional, unexecuted illustration

A fictional batch contains two established RAW/JPEG pairs, one standalone JPEG already present in the selected catalog, one video and one XMP sidecar belonging to a RAW. That is seven files: six media files plus one companion. The chosen fictional importer is documented to represent each RAW/JPEG pair as one item, so the intended result is four logical assets, including one reused item and three new items. The sidecar has a separate preservation/interpretation check rather than an expected thumbnail.

If an interrupted import later shows both paired items and the reused JPEG, three visible items would not prove that the three new assets arrived: the video would still be missing. The workflow would retain the two confirmed new pair mappings, leave the established JPEG untouched, reconcile the sidecar and retry only the video once its outcome is known. A catalog record still pointing to the card would fail independent-original retention even if its cached preview opened.

These are invented paper facts, not a performed import or tested application behavior. No camera, card, photo, library, account, setting, file transfer, export or native application was accessed or changed for this illustration.
