---
name: digitize-analog-audio
description: "Capture a bounded existing tape, record or other analog audio source into a preserved digital master through an available supported recording setup, reconciling channel identity, input level, source playback and take continuity. Use for analog-to-file transfer, not recording new speech, screen capture, sound restoration, transcription or converting an existing media file."
---

# Capture an analog source into a usable digital master

Deliver the requested audio files and enough source-to-take information to identify what was captured, what remains missing and how an affected interval could be recaptured. The original carrier remains unchanged. A responding meter, audible hardware monitor or completed recording timer does not establish that the saved file contains the intended source without gaps.

Use [media-export-compatibility](../media-export-compatibility/SKILL.md) when an existing digital file needs conversion, [create-audio-narration](../create-audio-narration/SKILL.md) for a new spoken rendition, and [transcribe-recorded-audio](../transcribe-recorded-audio/SKILL.md) for a transcript. This workflow acquires existing audio; it does not restore damaged media, repair playback equipment, master a release or certify archival fidelity.

## Establish the source and available capture path

Reuse the user's stated choices. Identify only what changes the transfer:

- The selected carrier, side/program and requested start/end or full-side coverage; use neutral source IDs when titles are private
- The playback device and its available documented output, any existing interface/preamp, and the actual computer and recording application/version
- Who can safely identify, load, play, pause and stop the physical source; remote app access does not establish physical access
- The source's supported playback speed, recorded channel arrangement and any evidenced playback-decoding requirement
- Intended use, requested master and listening-copy formats, destination and any duration or file-size constraint
- Authority to capture this material, permitted device/app changes and what must remain undisturbed

If the source is already an ordinary accessible digital file, preserve and use that file rather than taking an unnecessary analog generation. Do not bypass protected-content restrictions or extract material outside the authorized scope. A request to digitize a selected source does not authorize room-microphone capture, recording a call, streaming, transcription or sharing with a new service.

Use an already-available supported recorder. Installation, driver changes, account linking and new recording-device permissions require the applicable authority. Inspect the app's actual save route: a cloud-project button is an upload, even when it resembles local Save. Keep private recordings out of new synchronization or sharing destinations unless authorized. Check the requested computer is available before promising to operate it; provide a source-matched setup plan if physical assistance or capture access is missing.

Have the operator check the carrier and playback path using the equipment's own instructions. Stop for tangling, sticking, visible damage or uncertain safe handling. Do not prescribe tape baking, head alignment, chemical cleaning, electrical repair or repeated playback of a deteriorating original. A difficult or unique carrier may need specialist handling rather than a software workaround.

## 1. Bind the electrical source to the recorded channels

Map the path explicitly: selected carrier and playback output → any required preamp/interface input → OS input endpoint → recorder input/channels → saved file. Separate that path from the output used to listen. Record model-specific facts as observed or operator-reported, not inferred from a device name.

Check manufacturer documentation for the actual connectors and input modes before connecting equipment. Connector shape alone does not establish compatible signal level or channel wiring. A stereo line output needs a supported line-level input; do not substitute a built-in microphone or assume a headset socket accepts stereo line audio. Do not connect amplified speaker outputs or change phantom-power/input modes as an experiment. Physical connection changes belong with a capable operator following the equipment's instructions.

[Audacity's equipment guide](https://manual.audacityteam.org/man/how_to_connect_your_equipment.html) distinguishes tape line output, computer line input, interfaces and turntable preamplification. A turntable's raw phono output and a documented line-level output are different paths. Establish whether the particular device already applies phono gain/equalization; avoid adding a second correction merely because the source is a record. USB playback devices may supply their own conversion, but still require the correct input endpoint and channels. Use actual model guidance for exceptions instead of treating the tutorial's equipment examples as purchasing recommendations.

In the recorder, choose the identified endpoint rather than an unresolved “Default,” loopback, virtual cable or webcam microphone. Preserve other apps' working selections. Select the required channel count and input pair using the recorder and interface's supported mapping. A two-channel file can contain duplicated mono, one empty side or an unintended channel pair; two moving meters do not prove left/right identity.

Use a known source passage or an available documented channel-identification route to check mapping. Do not invent a left/right cue in unfamiliar material or disconnect live cables merely to provoke a signal. If the recording has two nonempty channels but their intended order is unverified, retain that limitation. Do not downmix, duplicate a missing channel or apply gain to one side to conceal an unresolved capture fault. An intentionally mono source can remain mono when that matches its evidenced content and the user's output need.

## 2. Prepare an unprocessed, recoverable take

Create a fresh local project/take at an authorized location with a unique source/side/attempt name. Check that Record will start a new intended take, rather than append to an earlier one, overwrite a selected region or mix existing tracks. Do not import an old pilot into the capture project merely because it has the right filename.

Choose a supported sample rate and sample representation suited to the agreed output. Record the recorder settings and the device/OS settings that can actually be established, including any conversion layer; do not claim direct hardware sampling from an export dialog alone. Preserve a supported higher-precision working project where useful, then state any export conversion. [Audacity's sample-format documentation](https://manual.audacityteam.org/man/sample_format_bit_depth.html) distinguishes floating-point working precision from integer delivery formats. A floating-point project cannot restore information already lost in an overloaded analog input or converter.

Estimate storage from the planned duration, channel count and working representation, allowing additional room for the project, saved master, retries and app overhead. Inspect the actual available destination space and any recorder/container size limits. Do not reduce channels or quality silently to fit a full disk. Choose a documented working location with reliable sustained writes; for Audacity, its [saving and exporting guidance](https://support.audacityteam.org/basics/saving-and-exporting-projects) warns against active projects on external or network storage and distinguishes project saves from exported audio. A verified closed copy can be delivered elsewhere later within scope.

Keep the master free of optional denoising, automatic silence removal, normalization, tempo changes, fades and other editorial processing. Inspect enabled effects and recording modes rather than assuming a new track is unaffected. Automatic start/stop thresholds can omit quiet passages or alter continuity. Disable only the implicated task settings within authorization, record their prior values, and retain required playback decoding when it is evidenced for this source. A missing tape-speed or noise-reduction setting is an unresolved source interpretation, not permission to make the recording sound more pleasing.

Select a monitoring route that cannot feed its output back into the recording. Prefer the interface's supported direct headphone monitoring when suitable; otherwise use a documented software route. Avoid duplicate monitoring paths and keep playback volume comfortable. Monitoring volume and capture gain serve different purposes. Turning down headphones does not reduce recorded overload, and hearing a direct monitor does not establish that the app wrote audio.

## 3. Establish level and verify a saved pilot

With the operator ready, monitor a representative loud passage and the quieter content the user needs preserved. Adjust the supported gain control that affects the actual capture path. If the app's input slider is unavailable or ineffective, inspect the interface's documented control rather than compensating with an unrelated playback slider.

Leave useful peak headroom and inspect both channels. [Audacity's meter guidance](https://manual.audacityteam.org/man/meter_toolbar.html) gives a peak near −6 dB as a practical recording target; it is guidance, not a universal acceptance threshold or a measure of perceived loudness. A sampled loud passage may not be the source's loudest moment. Red overload indications, flattened peaks or audible distortion need investigation of the earliest affected stage; lowering an already clipped digital track cannot recover its lost waveform.

Record a short pilot that includes the chosen source passage, both intended channels and a useful quiet boundary. Stop and finalize it, then export/reopen that exact saved pilot. Check:

- The expected source content, channel arrangement and plausible playback speed, with operator comparison when needed
- No unintended room, desktop or monitor-return audio
- No unexplained missing side, overload, hum, repeated echo, dropout or clipped beginning/ending
- The actual file format, rate, channel count and duration, plus successful playback of the saved content

Listen through an available audio-perception capability, or attribute the listening result to the operator. A waveform, playback command or file probe is not a listening observation. If listening is unavailable, preserve that limit and do not call sound quality verified. If a critical source or capture problem remains unresolved, hold the full pass rather than spend the original's playback life on a known-bad setup.

Correct one supported implicated setting and make a new pilot when that would resolve the fault. Keep pilots separate from accepted takes so they cannot accidentally become duplicate opening material. Reconfirm endpoint, gain and channels after reconnecting equipment or restarting the app.

## 4. Capture with source-relative continuity

Assign a separate take to each side/program or other agreed unit. Have the operator return to the known starting point. Start the recorder before the wanted source audio, establish that recording is active, then begin source playback. Allow the wanted ending and decay to pass before stopping the capture. Preserve these raw boundaries; any later trimming belongs in a separately identified derivative.

Maintain a small take record: source/side, attempt, source start/end anchors, selected settings, saved location and interruptions. Use recognizable content anchors or the operator's observations when a source has no dependable clock. A cassette counter is not automatically elapsed seconds. Keep physical source time, recorder timeline and wall-clock time distinct; never invent a precise mapping from a guessed side duration.

The player and recorder are separate transports. Pausing the recorder while the source continues loses content; pausing the source while capture continues records a gap. Keep both states explicit. When a source must be turned, cued or interrupted, finish or clearly separate the take rather than presenting a discontinuity as an uninterrupted transfer. Do not silently resume into the middle of a previous waveform.

Observe the capture through the requested interval. If a device disconnects, storage fails, the app reports dropped audio or the source stops unexpectedly, preserve what exists and stop the affected pass through supported controls. Do not repeatedly press Record/Stop or force-close an app whose write status is uncertain. Establish the current transport and save state before retrying.

[Audacity's recording documentation](https://manual.audacityteam.org/man/recording.html) explains that detected dropouts may be replaced with zero samples to preserve later timing, with labels marking affected regions; detection can be incomplete. Therefore a plausible duration, a continuous waveform timeline or the absence of a warning cannot by itself establish complete captured sound. Retain reported intervals and inspect the corresponding saved audio.

For recovery, identify the missing or compromised source interval. With a safe replayable source and corrected cause, make a new complete take or a separately named overlap capture covering identifiable material on both sides. Do not discard a useful partial before the replacement is verified. If assembly is requested, preserve the untouched takes, establish the actual overlap, and document every join; a seamless-sounding edit alone does not prove that material was neither skipped nor repeated. If source correspondence cannot be established, keep the gap explicit rather than guessing a splice.

## 5. Preserve and check the actual master

Save the native project if requested or useful for recovery, then export a separate lossless master in a supported format that meets the agreed contract. Inspect whether export uses the full intended range, correct tracks and channel mapping, with no accidental selection-only export, muted channel or effect-rendered change. Preserve capture settings, dropout labels and take notes outside the audio when the chosen format does not carry them.

Reopen the exact exported master, not just the project preview. Confirm identity, format, channel count, sample rate, usable duration and a complete readable/decodable stream with available tools. Compare the beginning and end, source anchors, every interruption and any recaptured area. Inspect each channel and reported fault interval. Listen to the full selected capture when complete audible review is required; otherwise name the reviewed and unreviewed intervals. A sample review supports only that sample, and even full listening is not a bit-perfect comparison with an analog original.

Acceptance means:

- Requested source units are represented in order, with no unresolved omitted interval presented as complete
- Saved channels correspond to the established source mapping, with any unknown orientation stated
- The capture and final export have no unresolved observed clipping/dropout problem concealed by processing
- The master is preserved separately from any edited, compressed or normalized listening copy
- Actual file checks, operator observations and listening coverage are distinguished, and the approved destination is verified

If a boundary or interval remains uncertain, deliver a useful labeled partial and identify the specific recapture or review needed. Do not replace silence with guessed audio, manufacture a missing channel, or claim that cleanup recovered absent information. Requested restoration, track splitting, captions and listening-copy conversion can follow from the preserved master under their own scope.

Return the accessible files, source/side-to-filename map, duration and format, material settings, known source/capture defects, take continuity and checks performed. A single short side may need only a few lines; a multi-side or interrupted transfer needs a compact register. Confirm capture and monitoring have stopped, restore temporary settings where appropriate without overwriting concurrent changes, and have the operator safely stop/remove the original. Cleanup of failed takes, disposal of carriers and publication are separate actions.

## Fictional, unexecuted illustration

A fictional user requests an unprocessed stereo master of side A of a cassette of their own instrumental composition. The first hypothetical pilot contains the right program on the left but no right-channel audio. Its two-channel WAV header would not satisfy the channel requirement; the operator would check the documented output/input mapping and make a fresh pilot before a full pass.

In a later hypothetical pass, the recorder labels a dropout near 07:12 while preserving the file's elapsed length. The take would remain incomplete at that interval despite its plausible total duration. After the cause is established and corrected, a safely replayable source could be captured again with recognizable overlap around the fault, keeping both attempts. Until the overlap and replacement are verified, the deliverable would retain the fault and no seamless-completion claim would be made.

This original illustration describes expected decisions only. No cassette, interface, recorder, settings, audio file, playback, listening check, recovery or export was operated or executed for it.
