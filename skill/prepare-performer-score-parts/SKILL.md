---
name: prepare-performer-score-parts
description: "Prepare a revision-matched set of readable performer parts from an approved notation score, reconciling player assignments, written pitch, navigation and page turns. Use for rehearsal or performance PDFs and their editable source; not composition, arranging, audio transcription or MIDI-event verification."
---

# Prepare performer score parts

Turn an approved score into the parts the named players actually need. Deliver the requested part PDFs, an updated native notation copy when supported, and a short part list identifying the source revision and unresolved musical decisions. A full-score PDF, a MIDI export and a player part are different deliverables.

Use [verify-generated-midi](../verify-generated-midi/SKILL.md) for timed-event checking and [document-export-check](../document-export-check/SKILL.md) for ordinary document conversion. [prepare-print-production-package](../prepare-print-production-package/SKILL.md) covers a commercial printer's requirements. None of those checks establishes that a musician has the right notes, pitch convention or usable page turns.

## Establish the musical source and players

Identify the approved native score and revision, movements or excerpts required, available notation application/version, and any reference PDF representing the intended music. Obtain the player/instrument roster, including doubling, shared desks and separate players occupying different voices on one staff. Ask only about ambiguities that change the result.

Confirm whether each requested part uses written or concert pitch, the intended paper size or tablet view, single-sided or duplex handling, and individual files versus a combined packet. Do not impose a conductor's concert-pitch preference on the players. Preserve required attribution and rights notices; permission to prepare parts does not automatically permit public distribution.

If only a scanned score, audio or MIDI is supplied, identify the missing notation source and separate transcription/reconstruction work. Do not call an automated import an approved engraving. Existing part PDFs can support a packaging and discrepancy review, but not linked-source correction.

Work on a new local candidate, retaining the original and its revision identity. Do not enable account publishing, automatic uploads, plugins or online conversion to complete a local parts request. Check shared-folder exposure before saving private scores.

## 1. Stabilize the working score

Open the copy in the supported notation application and compare movement order, measure numbering, pickup, endings and instrumental roster with the approved source. Preserve deliberate numbering offsets and nonstandard measures. Report missing fonts, unsupported symbols and import warnings before treating the copy as equivalent.

For MusicXML, inspect layout and content after import rather than assuming lossless exchange. MuseScore's [MusicXML guidance](https://handbook.musescore.org/file-management/working-with-musicxml-files) describes imported layout/break settings, font fallback and cleanup needs. Record consequential import choices. Compare representative dense passages, text instructions, tuplets, cross-staff material and instrument changes, plus every flagged region. State when coverage is only sampled.

Do not reset all spacing, stems or text styles merely because a cleanup command exists. An apparently odd detail may be intentional notation. Hold an uncertain musical change for the designated reviewer; continue unaffected parts.

## 2. Map score material to each player

Make a compact roster: output part name, player/instrument, included staves and voices, doubling and expected movements. A keyboard part may need two staves; one staff containing two players may need separate outputs. Do not infer allocation from stem direction alone, or assume a player remains in the same encoded voice throughout.

Use the application's supported linked-parts mechanism. In MuseScore, default parts can expose additional instruments, and custom parts can select visible voices. Its [parts documentation](https://handbook.musescore.org/basics/parts) distinguishes content changes shared with the score from part-specific properties; text synchronization needs particular care. Inspect the current version's controls before editing.

Reconcile every movement and shared-staff passage against the roster. Check unisons, divisi, voice swaps, cross-staff notation and instrument changes. Hiding another voice is insufficient if the desired notes were entered there elsewhere. For ambiguous allocation, identify exact measures and request a musical decision instead of copying the whole staff to both players.

Do not delete unwanted notes from a linked part to hide another player's material: content deletion can affect the score. Use supported visibility/extraction controls, or a clearly identified independent derivative with an explicit maintenance plan if necessary. Do not describe that derivative as still linked.

## 3. Reconcile written and sounding pitch

Inspect the actual instrument definition, transposition interval and clef, not just the printed label. Distinguish concert/written-pitch display from transposing the underlying music. MuseScore's [transposition reference](https://handbook.musescore.org/notation/pitch/transposition) explains those separate operations and the staff transposition setting.

For each transposing instrument, compare identifiable notes and key signatures with the approved sounding-pitch reference, including the octave. Repeat around instrument changes and ottava indications. Record the expected convention for octave-transposing instruments rather than assuming a familiar key signature proves correct octave placement.

Correct an evidenced configuration or conversion error only within scope. Do not manually shift notes to compensate for a wrong display setting and then apply instrument transposition again. A new key, replacement instrument or range adaptation is an arranging decision, not an invisible formatting adjustment. Preserve uncertain spelling or instrument-specific notation for review.

Authorized playback may help find discrepancies but cannot prove that the printed written pitch or accidental spelling is right. Do not launch audio or download sound libraries as an automatic requirement for a visual handoff.

## 4. Preserve the player's route

Compare each part with the source for tempo changes, rehearsal marks, measure references, repeats, numbered endings, jumps, return targets, fermatas and final endings. A player must be able to locate the same rehearsal point as everyone else, even while silent. Include needed instructions without inventing cues or changing repeat interpretation.

Review long rests against the underlying measures. A multimeasure-rest number counts measures, not beats or elapsed seconds. Confirm compression does not conceal a required entry, change or navigation instruction. MuseScore supports independent rest compression in score and parts and documented break controls in its [multimeasure-rest guide](https://handbook.musescore.org/notation/rhythm-meter-and-measures/measure-and-multimeasure-rests). Inspect the result rather than relying on automatic breaks.

Keep cues distinguishable from the player's notes and preserve their source/instrument label when present. Adding a cue can require musical judgment and authorization; do not fabricate one from an assumed melody. For percussion, retain approved instrument labels and legends rather than inferring sounds from notehead position or playback alone.

## 5. Lay out each part for its use

Inspect every part independently at its intended reading size. Avoid collisions involving accidentals, dynamics, lyrics, articulations, ties, slurs and ledger lines. Retain clear titles, instrument names, movement starts and page identifiers. Do not force parts to share the score's system breaks or page counts.

Place page turns with the particular player's activity in mind, including repeated visits and backward jumps. A large rest is not automatically a usable turn if it belongs to another voice, occurs only on a later pass, or is too brief at the intended tempo. Distinguish loose-sheet transitions, duplex turns and tablet changes; note unresolved physical setup rather than promising effortless turns.

Prefer layout adjustments over deleting markings or shrinking notation to meet an arbitrary page target. Use supported breaks and spacing, checking whether the change is part-local. MuseScore's [page-layout guidance](https://handbook.musescore.org/formatting/pages-and-vertical-spacing) describes page breaks and vertical spacing. If no workable turn fits, offer a specific alternative such as a foldout, larger sheet or different break for the user's decision. Do not silently change the music.

## 6. Export and reconcile the exact set

Save the final native candidate, then export only the intended score/parts from that revision. Use filenames distinguishing similar instruments, movements and revisions. MuseScore's [export guide](https://handbook.musescore.org/file-management/file-export) distinguishes readable PDF output from MIDI, which does not preserve visual formatting. Verify separate-file versus combined-file selection; the active editor tab alone does not establish what was exported.

Open the saved PDFs and inspect every page, not just the editor view. Compare:

- Roster against filenames and internal part titles, with no missing, duplicate or unintended parts
- Movement/page order, first and last musical content, pickup and final endings
- Written-pitch convention and identified transposition checkpoints
- Navigation landmarks, rest counts, entries and approved voice allocation
- Glyphs, collisions, clipping, page size and proposed page turns

For a combined packet, check part boundaries and deliberate blank pages. Do not accidentally carry page-number or duplex assumptions from one separate part into another. Tablet import and physical print checks are separate observed results, not established by opening a PDF on the author's screen.

If correction is needed, return to the native candidate and regenerate affected outputs. Recheck linked parts and later pagination that may have changed. Do not patch only a PDF and leave the editable source claiming a different final revision.

## Completion and recovery

Return the PDFs and requested native source, source revision, delivered part list and concise exceptions. Separate musical reconciliation, saved-PDF inspection and performer/physical acceptance. Do not call a sampled score fully proofread or a proposed page turn performer-tested.

If the application is unavailable, return a concrete roster and discrepancy plan with exports not produced. If a split or transposition is uncertain, hold that part with exact measures and the needed decision; do not pass it off as ready because the PDF opens. Sending parts to performers or publishing them requires the applicable audience authorization and rights. Stop at preparation when delivery was not requested.

## Fictional, unexecuted example

An invented rehearsal score has two flute players sharing a staff and one B-flat clarinet. The requested output is three written-pitch part PDFs from revision R7. The flute voices exchange roles in measures 25–28; the clarinet rests in measures 17–24, with rehearsal B at measure 21.

The proposed roster cannot simply assign flute 1 to encoded voice 1 throughout: the exchanged passage needs the approved player mapping. The clarinet rest should preserve the landmark at 21, representing 17–20 and 21–24 as separate four-measure spans if compressed there. A source sounding C4 should correspond to written D4 for this B-flat clarinet; concert-pitch display is not the requested final convention.

The candidate would remain held if the flute assignment were unresolved. After an authorized resolution, review would check all three titles, the split passage, clarinet pitch/rest landmarks and each page transition against R7. These are proposed decisions and checks only: no score was created, application opened, part exported, PDF rendered, music played, print made or performer approval obtained for this example.
