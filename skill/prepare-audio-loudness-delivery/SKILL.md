---
name: prepare-audio-loudness-delivery
description: "Prepare an existing finished audio program to a stated loudness and true-peak delivery contract, preserving content and channel balance while exposing gain-only limits and verifying the final encoded file. Use for measured audio-level delivery, not composition, source repair, stem export or automatic publication."
---

# Prepare a measured audio loudness delivery

Deliver a separate audio copy and a concise measurement report tied to its exact bytes. The result should distinguish meeting a numerical delivery contract from sounding good, being accepted by a service, or being safe at a listener's playback volume. A peak-normalized waveform, an export preset and a meter screenshot of the source are not equivalent to a checked deliverable.

Use [media-export-compatibility](../media-export-compatibility/SKILL.md) when the main problem is an unsupported container or codec, [create-audio-narration](../create-audio-narration/SKILL.md) to create speech, and [prepare-audio-stem-handoff](../prepare-audio-stem-handoff/SKILL.md) to deliver additive mix components. This workflow starts with a finished program. It does not promise to repair clipped sources, rebalance dialogue against music, or independently normalize stems that must retain their mix balance.

## Establish the actual delivery contract

Inspect the supplied brief and source before asking for missing information. Identify the selected program/version, intended full duration, output format and channel layout. Resolve the level requirements that affect the work:

- Integrated loudness target and permitted tolerance, with units and measurement method
- Maximum true-peak ceiling, and any separately specified momentary, short-term or loudness-range requirement
- Whether measurement covers the entire program, specified segments or a documented dialogue-based method
- Whether each file is an independent program or part of a sequence whose relative levels must remain intact
- Whether the user wants gain only or also permits limiting/compression when needed
- The delivery destination's documented requirements, or an explicitly agreed local target if no destination is specified

Do not borrow a popular streaming number and call it a universal requirement. [EBU R 128](https://tech.ebu.ch/publications/r128) recommends a particular broadcast framework, including a -23 LUFS program level; it is not evidence that an unrelated podcast host or client requires that target. Retain the actual specification's source, revision/access date and tolerance. A playback service's normalization policy is not automatically an upload acceptance rule.

Use an available authorized editor or processor and its version-matched documentation. If a meter cannot implement the contract's method or channel layout, report that limitation rather than substituting RMS, sample peak or a different gating mode. A value labeled simply “dB” is not enough to identify the metric. [ITU-R BS.1770](https://www.itu.int/rec/R-REC-BS.1770-5-202311-I/) specifies algorithms for program loudness and true-peak measurement; the recipient's contract still determines the required target.

Preserve the original. Work in a new local candidate file/project and avoid new cloud uploads, plug-in installations or account connections without the applicable authority. For referenced media or playlists, resolve the authorized dependency scope before a decoder follows references; use the containment guidance in the linked compatibility workflow. Preparation does not authorize publishing or sending the recording.

## 1. Measure the intended program, not a convenient excerpt

Record source identity/checksum, selected stream, full program interval, channel roles and meter/tool version. Complete the intended editorial assembly before measurement. Joining an introduction, trimming a section, changing a downmix or inserting an advertisement creates a different measurement input.

Reset accumulated meter history, select the correct measurement mode, and analyze the full specified interval. Retain the measured integrated loudness, maximum true peak and any other required descriptors with units. Record errors and incomplete analysis; do not label a partial pass as a full-program result. Do not average the LUFS numbers of individual chunks to claim the integrated loudness of their concatenation.

Keep the following choices explicit:

- **Channel mapping:** Measure the actual delivery layout. A pair of channels might be stereo, dual mono or two separate languages. Do not mix alternate languages together to obtain one loudness result.
- **Mono convention:** Check whether a meter applies dual-mono compensation. Use the same agreed convention for input and output; do not switch it to make a candidate pass.
- **Stereo balance:** Apply linked gain to a finished stereo program unless a balance change is explicitly intended. Independent left/right normalization is a mix change.
- **Program boundaries:** Do not discard quiet passages or remove pauses just to improve the meter result. Preserve required leaders and tails while applying the contract's documented measurement scope.

[Audacity's loudness-normalization manual](https://manual.audacityteam.org/man/loudness_normalization.html) documents both independent stereo-channel processing and a mono-as-dual-mono option. Those settings can change the interpretation of a result; matching the displayed target alone does not establish comparable measurements across tools.

Silence, very short material or audio below the meter's usable measurement conditions may yield no meaningful integrated value. Keep undefined or non-finite results explicit. Do not replace them with zero, inject noise, or apply an extreme gain automatically. Establish whether the input is the right program and whether the requested method is applicable.

## 2. Decide whether gain alone can meet both constraints

For a first planning estimate, subtract measured integrated loudness from target loudness to obtain the proposed gain in dB. Add that gain to the measured true-peak level to estimate the peak after uniform scaling. This is a feasibility estimate, not final evidence: gating, format conversion and later processing require remeasurement.

Compare the estimate with the actual ceiling and tolerances:

- If linked gain can meet the loudness target without exceeding the peak ceiling, prefer that minimal change.
- If the required increase would exceed the ceiling, a peak-safe gain may leave the program below its target. State the conflict; do not report a peak-safe but too-quiet file as fully conforming.
- If controlled dynamics processing is already authorized, choose a supported limiter/compressor approach and disclose the change. Otherwise ask whether to allow it, accept a lower loudness where the recipient permits it, or return to the mix.
- If there is no acceptable route within the authorized sound changes, return the measured source and exact blocker rather than repeatedly driving a limiter harder.

A maximum true-peak value is a ceiling, not a level every file must reach. A quiet peak does not need boosting when integrated loudness already meets the contract. Likewise, loudness-range reduction is not an incidental consequence to hide inside “normalization.” Do not introduce an arbitrary range target when the brief does not require one.

## 3. Render with the measured input bound to the settings

Keep the selected source, stream, range, channel mapping and pre-processing identical between analysis and application. If any changes, obtain fresh measurements. Never reuse another episode's statistics or a stale analysis from before an edit. Save the applied gain, processing order, output format and material settings alongside the candidate identity.

For an FFmpeg route, consult the installed version and [the official loudnorm documentation](https://ffmpeg.org/ffmpeg-filters.html#loudnorm). Its linear mode requires measured integrated loudness, range, true peak and threshold; it can revert to dynamic processing when the conditions for linear operation are not met. Check the reported actual mode rather than treating a requested linear setting as proof of gain-only processing. Explicitly choose the output sample rate, because dynamic processing uses an internal higher rate. Keep analysis and render mono conventions consistent. These are adapter-specific constraints, not a requirement to use FFmpeg.

Do not let an export dialog silently add a second normalization or master effect. Check the actual range, selected channels and muted/soloed state. Preserve timing and content; a level-delivery task does not authorize trimming, speed changes, new fades or denoising. Keep the editable or lossless source available, and derive new candidates from it rather than repeatedly processing a lossy candidate.

If rendering fails or times out, establish which output is complete before retrying. Keep incomplete candidates out of the final folder and do not overwrite the only original. A stopped meter or a file appearing on disk is not proof that the entire render finished.

## 4. Reopen and measure the exact deliverable

Analyze the final encoded file after export, using the agreed measurement scope and method. Do not substitute measurements from a pre-encoder bus or working WAV when the deliverable is another format. This check catches differences introduced after the normalization stage instead of assuming that its settings controlled every later stage.

Verify separately:

1. The exact candidate opens/decodes through the intended program, with correct duration, stream, channels, sample rate and format.
2. Full-program integrated loudness is within the agreed tolerance and maximum true peak is within its ceiling; any additional required metrics also pass.
3. Beginning, ending, quiet sections, loud transients and processing-sensitive passages retain the intended content and timing. No independent-channel gain, accidental downmix, missing channel or truncated tail is concealed by the numerical result.
4. Listening review covers audible distortion, pumping, altered transitions and noise changes where audio perception is available. A meter or playback command without hearing the output is not a listening check.

If measurements disagree between tools, compare file identity, interval, channel mapping, meter reset, algorithm/version and mono/gating settings before changing the sound. Do not select whichever meter produces a pass. If the recipient requires a particular meter or process, identify whether that check was actually available.

If a candidate misses its target, revise the implicated setting from the preserved source, create a new candidate and repeat the relevant final checks. Stop once it meets the agreed contract with the required review, or when the next step needs unavailable capability or a sound-changing decision. Do not silently relax a failed tolerance or claim that normalization restored pre-existing clipping.

## Hand off the file and honest evidence

Return the actual final file with source/output identity, target/source specification, before/after measurements, units, analysis scope and tool/version. State whether the transformation was linked gain only or included dynamics processing, and identify any accepted deviation. Report content/listening coverage and unreviewed portions separately from numerical checks.

Keep local conformance, listening review and destination acceptance distinct. Upload only when authorized, and identify the submitted candidate. A completed upload does not establish that the destination's processing or quality control accepted the file. No file-level loudness result guarantees hearing safety, which also depends on playback equipment and listening level.

## Fictional decision example, not executed

A fictional finished stereo program is stipulated to measure -22 LUFS integrated and -4 dBTP maximum true peak. Its client-supplied contract asks for -18 LUFS, a tolerance of 0.5 LU, and no peak above -2 dBTP. The user permits gain changes only.

The nominal +4 dB gain would predict a 0 dBTP peak, exceeding the ceiling. A +2 dB gain would predict -20 LUFS and -2 dBTP, still outside the loudness tolerance. The correct outcome is a disclosed constraint conflict and a choice about permitted dynamics processing or an accepted lower target, not a claimed conforming render. The arithmetic is a planning illustration; it does not establish how a real gated meter or encoded file would measure.

No audio file, meter, processor, encoder, playback, listening check or upload was executed for this original example. It describes expected decisions only.
