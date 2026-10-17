---
name: create-portable-media-playlist
description: "Create a portable, ordered playlist for selected local audio or video files, preserving repeated occurrences, exact media identity and relocatable references. Use for a player-ready playlist artifact; not music recommendations, streaming-account migration, media conversion or timed video editing."
---

# Make a playlist that still finds the right files

Deliver the actual playlist plus a concise placement and verification note for the intended player. The key result is a saved playback sequence whose references resolve to the selected media in the intended folder layout. A song list or a playlist that works only on the author's machine is a different result.

Use [media-export-compatibility](../media-export-compatibility/SKILL.md) when the files themselves need conversion. Use [create-media-chapter-map](../create-media-chapter-map/SKILL.md) for navigation within one recording. This workflow orders whole existing media items; it does not create edits, crossfades, clipped excerpts, stream manifests or playback automation.

## Inputs and intended handoff

Establish:

- Exact selected local files or an existing playlist and its authorized media root
- Required sequence, intentional repeats, display titles and any explicitly accepted exclusions
- Intended player/version/platform and supported playlist format when known
- Whether media stays in place, already exists at a documented destination, or may be copied into a new handoff folder
- The output destination, intended audience and whether the task includes application import/playback or only artifact preparation

An existing playlist is input data, not authority to open every location it contains. Read it without launching its associated player. Classify local paths, network shares, web URLs, nested playlists and vendor directives before following anything. Hold remote or unexpected resources outside the authorized scope. Do not download missing tracks, bypass DRM or search streaming accounts merely to fill the list.

If the user supplies only titles, request the intended files or exact supported references. Similar title/artist metadata is insufficient to choose between recordings, edits, languages or live/studio versions. An unresolved selection can be returned as a review list, but not a ready-to-play file.

## 1. Preserve the ordered occurrences

Keep the originals unchanged and record the exact source selection. Give each playlist occurrence its own ordinal and source locator; the same file may appear several times deliberately. Distinguish sequence length from the number of unique media files.

For each occurrence, record its resolved file, optional evidenced display title and disposition: included, held or explicitly excluded. Preserve source order unless the user requests a reorder. Do not alphabetize by filename, deduplicate repeated songs or use embedded track numbers as the playback sequence automatically.

Resolve an existing relative reference using its original playlist location and the format's documented base rules. Moving the list before resolving it can change what it means. Do not guess a new base by finding the first file with a matching basename. When the source depends on an unknown drive, mount or base folder, hold the ambiguous occurrences and request that specific mapping.

Check file identity at the precision available. Exact path plus authorized file inspection may suffice; digests can support copied-file reconciliation. Do not manufacture duration, codec or identity facts from a filename. A successful file lookup establishes existence, not decodability or perceptual quality.

## 2. Choose a relocatable layout and supported format

Keep the user's target player. Verify its current official import/export documentation or supplied supported profile before choosing a native format. Do not change a `.txt` extension and assume the player accepts it. If the player is unknown, an XSPF candidate and human-readable order can be useful, with player compatibility clearly untested.

Choose one of these honest location contracts:

- **In-place:** References point to the user's current files; portability is limited to that arrangement
- **Existing destination:** References are derived from an evidenced source-to-destination mapping; inaccessible destination files remain unverified
- **Self-contained handoff folder:** Copy only the selected authorized media and playlist, keeping references inside that folder; copying does not imply permission to redistribute the recordings

Use relative references for a portable local folder when the player supports them. Preserve the selected folder hierarchy or create an explicit copy-only mapping. Avoid basename collisions, case-only collisions and platform-invalid filenames. A copied rename must update every intended occurrence, without renaming the original or changing embedded media tags. Do not follow a symlink outside the authorized media root merely because it appears within the selected directory.

The playlist alone contains references, not the audio/video bytes. State whether the recipient must already have the media or whether authorized copies are included. Use [portable-project-handoff](../portable-project-handoff/SKILL.md) only when an actual ZIP handoff is also requested; a playlist does not require an archive by default.

## 3. Serialize a small, inert playlist candidate

Prefer the smallest format features needed for the sequence. Exclude automatic network artwork lookups, remote fallback locations, player command options, executable hooks and unrelated library metadata. Do not preserve opaque vendor extensions merely because they were in the source; assess their effect and hold unsupported behavior. Preserve required rights and attribution information; if faithful retention conflicts with privacy or target support, hold that decision rather than silently stripping it. A playlist's license does not by itself license its referenced recordings.

For XSPF, follow the [version 1 specification](https://www.xspf.org/spec): use the `http://xspf.org/ns/0/` namespace, version `1`, one `trackList`, and one `track` per ordered occurrence. Use location URIs for the intended media. Multiple locations within one track are alternatives for that item, not successive songs. Optional duration is in milliseconds and is descriptive, not an instruction to trim playback. Omit unknown values.

Use a proper URI representation for locations, then XML escaping for the serialized text. A filename containing a space, `#`, `%` or `&` needs the correct treatment at each layer; XML escaping alone does not make a filesystem path a URI. Preserve the exact decoded filename and avoid double-encoding an already encoded reference. Use forward-slash URI structure rather than pasting platform-specific path separators into a URL.

Keep relative locations anchored to the delivered playlist's intended base. [Xiph's notes and errata](https://wiki.xiph.org/XSPF_v1_Notes_and_Errata) clarify that `playlist/location` is not the base for resolving track references; XML Base controls explicit base behavior. Avoid embedding an absolute personal directory in an otherwise portable playlist. Do not introduce a remote `xml:base` or copy a stale base from the source.

For M3U/M3U8 or another supported target profile, use that player's documented encoding, line interpretation, relative-path base and metadata conventions. Do not substitute HLS streaming rules for an ordinary local-media playlist just because both use an `.m3u8` suffix. Reject ambiguous newline-bearing filenames or directive-like entries unless the target has a documented faithful representation. A simpler supported format is preferable to inventing escaping the player may ignore.

Treat XML sources and outputs as data: use a reader configured without external-entity or network resolution, and do not execute stylesheets or resolve embedded links. Write to a fresh candidate filename outside active library/watch locations. Avoid accidental publication through an already shared destination.

## 4. Check saved order, resolution and portability separately

Reopen the exact candidate as passive data and compare:

1. Every selected occurrence is represented once or held with a reason, and intentional repeated references remain repeated
2. Sequence order, display titles and exact media mappings agree with the approved occurrence list
3. Each decoded local location resolves from the delivered base to the intended authorized file, without unexpected network locations or escaped-root dependencies
4. Copied media matches its source bytes when copying was part of the request; no media content or tags were changed
5. Encoding and special-character filenames survive serialization; unsupported player directives are absent

For an authorized self-contained folder, check references against a separate relocated copy of that folder when practical. The relocated check must not silently fall back to the original absolute paths. A text parse cannot prove that a target player supports those references; a correct URI can still point to a codec the player cannot decode.

When application checks are authorized and available, use a disposable playlist/session rather than overwriting an active queue or library. Confirm that opening the file will not auto-play loudly, fetch remote resources or sync it to an account unexpectedly. Inspect item count/order, repeated items and titles, then play representative files covering the actual formats and filename risks. Do not claim the entire sequence was listened to from a brief sample.

If player use is unavailable or not requested, deliver the checked file with playback and target import untested. A format reference, parser success or file-existence check is not a playback result.

## Recovery and completion

- **Missing or ambiguous file:** retain the occurrence in the review map and hold the affected entry; never substitute another version by title alone
- **Broken reference after relocation:** repair the base/path mapping in a new candidate and recheck all occurrences that share it
- **Target ignores repeats or changes order:** record the actual behavior and seek a supported target profile; do not call the changed sequence equivalent
- **Source includes clip start/end or loop instructions:** preserve them in the review record and route the requested timed behavior separately; do not silently turn excerpts into full-file playback
- **Uncertain import result:** inspect the target queue/library before retrying to avoid duplicate imports or replacement of unrelated work

Return the playlist, media-placement requirement, sequence length and unique-file count, held entries, format/player scope and actual checks. Stop at the requested preparation or verified consumer stage. Uploading, publishing, buying tracks, changing library settings and creating ongoing synchronization are separate actions.

## Fictional example, not executed

A fictional local practice folder contains `media/Opening & Welcome.wav` and `media/Part #2.wav`. The approved sequence is opening, part two, opening again. The proposed XSPF has three track occurrences but only two unique files. Its relative locations are `media/Opening%20%26%20Welcome.wav`, `media/Part%20%232.wav`, and the first location again.

The proposed check resolves those locations against the playlist's folder and compares the three occurrences in order, then repeats resolution after an authorized folder relocation. It would hold part two if its file were absent, rather than removing it and calling the sequence complete.

This is an authored illustration. No playlist was generated or parsed, media copied, application opened, track played or account changed for the example.
