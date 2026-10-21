---
name: prepare-audio-stem-handoff
description: "Export an existing authorized DAW arrangement as aligned audio parts or grouped stems for another mix session, preserving source coverage, timing and intended processing while preventing doubled buses or returns. Use for reconstructable multitrack audio delivery, not source separation, new composition, mastering or single-file conversion."
---

# Prepare aligned audio parts for another mix session

Deliver a coherent set of audio files, a reference mix and concise import instructions. The recipient should know which files to play together, where they begin and what processing is already printed. A folder of individually playable WAVs is not enough if their timing, routing or roles are ambiguous.

Use [media-export-compatibility](../media-export-compatibility/SKILL.md) for a rejected existing media file, [digitize-analog-audio](../digitize-analog-audio/SKILL.md) for acquiring an analog source, and [portable-project-handoff](../portable-project-handoff/SKILL.md) for ordinary archive packaging. This workflow renders an existing arrangement into mix components; it does not separate instruments from a finished stereo recording or replace a requested editable native session with flattened audio.

## Define what the recipient needs to reconstruct

Reuse the brief and inspect the project before asking questions. Resolve only consequential missing choices:

- Exact source project/revision, selected song or arrangement, intended start/end and excluded material
- Individual track files for remixing, grouped stems for reduced control, or both as clearly separated alternatives
- Processing to preserve, such as an instrument sound or creative delay, versus processing the recipient should be able to change
- Required file format, sample rate, sample representation, channel arrangement and destination application/version if known
- Common placement origin, tempo/time-signature information where needed, and whether the recipient needs a reference-only mix or an exact reconstruction target
- Local preparation destination and any separately authorized recipient or upload destination

“Stems” is used for both groups and individual parts in practice. Settle the actual file membership instead of relying on the word. A mixing engineer needing separate kick and snare does not receive that control from a single drums file. If the request is ambiguous and the source is large, show a short proposed grouping before doing expensive renders.

Use the available authorized DAW and its current version-matched documentation. Do not install plug-ins, activate licenses, connect accounts or record external inputs just to satisfy an export request. Opening a session may load third-party plug-ins, devices or external dependencies; keep that within the allowed environment and do not bypass security warnings. If source access or rendering is unavailable, deliver a clearly labeled preparation plan, not a claim that stems exist.

Preserve the original project. Use a distinct working copy or supported project alternative for export-specific changes. Keep private media out of new shared/synced folders, online converters and collaboration services unless authorized. Preparation does not by itself authorize sending the package.

## 1. Account for source sound and processing

Identify the active arrangement, selected takes, audible tracks, groups, returns and main-output processing. Check missing-media and missing-plug-in indications before rendering. Do not let a silent substitute or offline instrument become an apparently valid part.

For each deliverable, record its source track/group, role, included processing and whether it is intended to play with the main set or only as an alternative. A small session needs only a short list. Classify reference mixes, click guides, dry alternatives and safety versions outside the simultaneous-playback set.

Choose one treatment for shared effects: include their contribution in the intended parts, or provide separately identified return files with the corresponding dry/direct parts. Do not include a shared return twice. Likewise, a printed group and its constituent tracks are normally alternative levels of control, not simultaneous additions. Explain exceptions when a deliberately parallel bus is part of the mix.

[Ableton's stem guidance](https://help.ableton.com/hc/en-us/articles/360000843404-Importing-and-exporting-stems) distinguishes group exports with group processing from individual group members without that processing. Use the actual routing to decide which are required; an export command's list is not a ready-made mix recipe.

Treat sidechain/control dependencies separately from audible membership. A muted or solo-excluded trigger can change a compressor or gate even when the trigger should not be heard in that stem. Preserve the intended control path using the application's supported render behavior and verify a representative passage; do not improvise a new routing scheme merely to make a meter move.

State whether volume/pan automation, inserts, bus processing and master processing are printed. “Dry” needs a concrete definition: removing a creative instrument effect may change the intended sound, while bypassing a software instrument can remove the sound entirely. Preserve an approved sound as audio when the recipient lacks its instrument, and provide editable MIDI only if requested. MIDI alone is not the rendered timbre.

Do not promise that independently rendered, master-processed parts will sum identically to a full mix. As a signal-processing consequence, a nonlinear processor acting on a combined signal need not equal the sum of its separate responses. Decide whether the recipient needs remix flexibility or an evidenced reconstruction of a particular mix. Keep an appropriate full reference mix from the same source revision either way.

## 2. Establish a shared time origin and complete ending

Specify one exact render start for the simultaneous-playback set, including any pickup, leading silence or needed pre-roll. Keep every component referenced to that origin. Do not trim each file to its first audible sample. A late entrance must remain late after import, not move to the beginning because its leading silence vanished.

Specify an end that includes wanted release and effect tails. A common start is essential for simple alignment; identical lengths are a useful delivery convention, not evidence by themselves that content is complete. If tail handling produces different lengths, either retain and document that supported arrangement or use an authorized common range long enough for all tails. Do not truncate a longer file merely to make counts agree.

Record the placement origin in a form the recipient can use: project position and, when needed, elapsed time or sample-frame offset. Bars/beats alone need the corresponding tempo map and meter. A single BPM label cannot describe a changing-tempo song. Rendered audio can retain its musical timing without a tempo map, but editing on the correct bar grid may require a separate supported tempo export or a clear map.

Avoid loop-specific rendering for a linear song unless explicitly intended. Ensure a leftover cycle range, selection, alternate scene or solo state cannot select the wrong content.

[Ableton Live's export manual](https://www.ableton.com/en/manual/managing-files-and-sets/#exporting-audio-and-video) documents explicit render start/length, post-fader track exports, optional return/main effects, and real-time rendering for relevant external-device paths. Confirm the actual mode and active material; do not assume a generic “export all” choice means only the requested arrangement. If the render needs unavailable external hardware, hold the affected part rather than substitute silence.

## 3. Render one coherent candidate set

Use a new uniquely identified export folder with source revision and short, unambiguous filenames. Select the agreed format and rate across the set. Preserve mono/stereo roles deliberately; a stereo effect on a mono source may need a stereo result. Do not collapse channels just to make file sizes consistent.

Keep independent normalization off when preserving relative levels is part of the handoff. If a format cannot represent a rendered level safely, resolve gain or format at the intended signal stage rather than quietly clipping or changing every file's gain independently. Record any accepted conversion or gain adjustment. Do not describe a floating-point file as repairing clipping already present earlier in the signal path.

[Logic Pro's track-export documentation](https://support.apple.com/guide/logicpro/export-tracks-as-audio-files-lgcpb27f70f9/mac) describes separate controls for effect bypass, audio tails, volume/pan automation, tempo information, normalization and multi-output instruments. Check the chosen export mode rather than transferring a preset from another DAW. Its tail option can extend files, and normalization includes an overload-only mode distinct from Off. A multi-output instrument also needs an explicit choice between combined track output and separate channel-strip files.

Use a short, relevant pilot when it will expose routing or timing mistakes before a long render. Include the late entrance, sidechain-dependent section or reverb tail that matters, not only an easy opening. A pilot checks those choices; it does not verify the final whole-song exports.

Inspect render status and actual output before retrying an uncertain operation. Keep incomplete or superseded candidates separate. If a change affects routing, automation or the range, rerender the affected components and reference as needed, then reconcile the set again. Do not silently combine files from different source revisions.

## 4. Re-import the delivered files, not the original tracks

When application access permits, create a fresh verification session using only the candidate files. Place the simultaneous-playback set at the documented common origin. Keep the reference and alternatives on separate muted/audition paths. Follow the handoff's level and pan instructions; printed balance must not receive the source mix's fader/pan moves a second time.

Prevent unintended automatic time-stretching, tempo adaptation, transposition or per-file alignment. Check the import application's actual settings rather than assuming matching filenames or displayed BPM preserve timing. If timestamps are used for placement, verify the reader honors them; retain a manual common-origin route when supported.

Check distinct properties:

- **Membership:** Every requested part is present once, each omission is explained, and no reference/group/return alternative is accidentally added to the main set.
- **File content:** The actual files open/decode, have the agreed format/rate/channel roles, and contain the expected source rather than silence, the wrong take or an unrelated bus.
- **Timing:** Compare early, middle and late source landmarks, pickups, late entrances and endings. Identical durations cannot prove alignment; one correct onset cannot rule out later drift.
- **Processing and tails:** Inspect the routing-sensitive pilot passages again in the final files, including sidechain behavior, automated changes and effects decay.
- **Reconstruction:** Compare the combined candidate set with the appropriate same-revision reference. A remix-ready dry set may intentionally differ from the processed reference; document that rather than “fixing” it by adding effects twice.

A numerical difference/null comparison can be useful only under established alignment, level, channel and processing conditions. Do not equate a nonzero difference with failure when stochastic instruments, modulation, different processing stages or intentional dry exports are involved. Conversely, a plausible waveform is not evidence of correct sound or complete listening review.

Listen with an available audio-perception capability or attribute the listening result to the operator. A playback command, meter or decode check is not listening. Name the review coverage and any unavailable target-application check. If exact reconstruction was required but remains unexplained, retain that as a blocker rather than relabeling the package remix-ready.

## 5. Hand off without hidden mixing decisions

Return the actual files and a compact readme naming:

- Source revision, render range/origin and required import placement
- Files to play together, alternatives not to combine, reference-only files and omissions
- Format/rate/channel roles, tempo/meter information where needed, and printed processing/level choices
- Actual file, re-import, timing and listening checks, with remaining uncertainties

Keep the native original and useful intermediate renders intact. Package or send only the agreed candidate set to the authorized destination; verify the transmitted identity if delivery is included. A completed upload is not evidence that the recipient imported the mix. Stop when the requested handoff is usable to the stated verification level or the remaining decision/access blocker is explicit.

## Fictional, unexecuted illustration

A fictional instrumental session contains Kick, Snare, a processed Drums group, Bass and a shared Reverb return. The recipient requests grouped stems retaining the mix's creative effects. A candidate folder containing Drums, Kick, Snare and a full Mix is not four additive components: it would count drums more than once and add the reference mix again.

The expected handoff would identify the chosen simultaneous set, keep the reference separate, and resolve whether the Reverb is already printed or supplied once as a return. Bass enters later than the drums, so its export would retain leading silence from the shared origin. A full-length file with Bass moved to the beginning would still fail alignment. If soloing Bass removes the kick-triggered compression, that render would require a supported control-path correction and renewed checking, not an unsupported exact-reconstruction claim.

This original illustration states expected decisions only. No DAW, project, instrument, render, file decoder, re-import, comparison, playback or listening workflow was executed for it.
