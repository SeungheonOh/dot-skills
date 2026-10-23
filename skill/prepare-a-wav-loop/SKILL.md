---
name: prepare-a-wav-loop
description: "Trim an authorized PCM/float WAV at exact frame boundaries, optionally crossfade the loop seam, and export a validated new audio file."
---

# Prepare a WAV loop without replacing its source

## When to use

The user needs a bounded loop asset from a supplied recording, with a clear record of timing, overlap and format changes.

## Required inputs

- Authorized WAV, supported encoding/channel/sample-rate limits
- Selected frame or time interval and desired seam overlap, including any fixed cycle-length or start/downbeat requirement
- Output encoding and whether peak scaling is allowed

## Workflow

1. Validate RIFF/WAVE chunk bounds and actual PCM/float format. Convert requested times to frame indices with a declared rounding rule and preserve the original bytes. Reject unsupported encodings rather than guessing.
2. Check a nonempty interval and overlap shorter than the available segment under the chosen construction. State the output length formula; overlap crossfades shorten a loop and are not merely a fade applied in place.
3. Apply the documented seam construction identically across channels. Keep operations frame-aligned, reject nonfinite samples and do not silently resample or normalize.
4. If requested, calculate peak scaling explicitly and record the gain. A seam crossfade does not guarantee perceptual smoothness; comfortable-level listening is a separate authorized check.
5. Serialize a new WAV with valid sizes, channel layout and sample encoding. Reopen using an independent parser and verify sample rate, frames, channels and duration. Do not claim an output was heard if only numeric checks ran.

### Specify the seam before modifying samples

Record the exact selected half-open frame interval and channel count. Convert seconds using the file’s own sample rate, not a requested export rate. If a new sample rate is requested, treat resampling as a separate operation with its own quality and length checks.

Choose an explicit sample construction, not just a fade preset name. A fade-out followed by a fade-in is not an overlap, and retaining both complete edge regions after blending would not yield the claimed shorter cycle. [Audacity's crossfade guide](https://manual.audacityteam.org/man/creating_a_crossfade.html) describes overlapping sections and the effect of different fade shapes; an editor's chosen curve and endpoint convention still need to be established.

One explicit choice is the following **linear tail-to-head profile**, expressed in complete multichannel frames. It is an authored construction, not a promise that every editor implements the same operation. Let `x[0:N)` be the selected segment and `M` the integer overlap:

- For `M = 0`, copy the segment unchanged; there is no seam blend and the output has `N` frames.
- For a blend, require `2 <= M <= floor(N / 2)`. Hold a one-frame blend because this profile's endpoint-inclusive ramp has denominator `M - 1`; do not divide by zero or silently choose an unrelated midpoint mix. Larger overlaps need a separately specified construction, not a clamped input.
- Retain the middle `x[M:N-M)`. It is empty, not invalid, when `2M = N`.
- For each `k` from `0` through `M - 1`, form one seam frame with weight `w = k / (M - 1)`: `s[k] = (1 - w) * x[N-M+k] + w * x[k]`. Apply the same weights to corresponding channels.
- Write the retained middle followed by `s[0:M)`, exactly once each. The resulting cycle has `(N - 2M) + M = N - M` frames. Do not append either original edge region afterward.

For a nonzero blend this ordering starts at selected frame `M`, not at selected frame zero. Record that start-point shift as well as the shorter duration. If a fixed bar length, attack or downbeat position is required, resolve that conflict before processing; do not silently rotate, pad, stretch or remove another region to restore it. Another arrangement is acceptable only with its own declared frame map, length and endpoint rules.

Check both joins. When the middle exists, its last frame is followed by the seam's first frame, preserving the original adjacent pair `x[N-M-1], x[N-M]`. At repeated playback, the seam's last frame is followed by the output's first frame, preserving `x[M-1], x[M]`, including when the middle is empty. This avoids introducing a new jump at those two joins but does not prove smooth behavior inside the blend or an inaudible cycle. Compare expected frame order and seam values with the decoded output under the declared gain and quantization, not just its duration.

**Fictional, unexecuted frame-order illustration:** for `N = 8` and `M = 3`, this profile yields `[x3, x4, x5, (x6 + x1) / 2, x2]`, five frames per channel. Its repeated-playback join is `x2` to `x3`; a five-frame result with the fade direction reversed would not establish this contract. These symbols describe an expected ordering, not generated or measured audio.

Check peaks before quantization; do not let out-of-range float values become clipped PCM silently. Complementary linear weights preserve a constant-valued input, but do not guarantee unchanged perceived loudness or prevent cancellation between different edge signals. Changing to another curve changes the processing contract. Preserve the source and save to a new destination with no-overwrite handling where available.

### Reconcile source-relative metadata

Inspect non-audio chunks before deciding what the new loop retains. Cue positions, playlists and associated labels can refer to the old sample layout. The [original IBM/Microsoft WAVE specification](https://www.mmsp.ece.mcgill.ca/Documents/AudioFormats/WAVE/Docs/riffmci.pdf#page=61) defines cue offsets, playlist segments and label-to-cue references; valid RIFF sizes alone do not establish that these still describe trimmed audio.

For retained metadata, derive positions and lengths from the actual output construction and keep references consistent. A plain trim can subtract its starting frame from retained positions, but a crossfade may blend or relocate source regions, so that subtraction is not a universal mapping. Do not clamp an excluded marker into the new audio. If meaningful metadata cannot be represented, disclose that limit and resolve its omission or keep export pending; do not blindly copy unknown chunks or silently discard required markers. Reopen the saved result and inspect retained positions and references separately from sample-rate/frame-count checks.

**Fictional, unexecuted illustration:** With a plain trim of frames [1000, 3000), a retained cue at source frame 1500 would move to output frame 500; one at 3500 is outside the selection. No WAV was generated or played for this illustration.

## Output

The new loop file, source interval, overlap, gain/encoding changes and numeric/listening verification status.

## Verification and limits

When execution is authorized, check mono/stereo, zero overlap, the supported minimum blend, an empty middle at `2M = N`, held one-frame/oversized overlaps, exact ramp endpoints, both joins, out-of-range float samples and quantization. Check actual frame order as well as length. No source overwrite or external upload is implied.

## Hold conditions

Hold export if samples are nonfinite, the overlap is outside the chosen construction's supported range, or the requested encoding cannot represent the samples without an unapproved change. Ask whether clipping, scaling or another encoding is acceptable rather than choosing silently.

## Worked example

A supplied synthetic stereo WAV has sample rate 48, 000 Hz. The chosen interval is frames 24, 000 through 120, 000 exclusive, giving 96, 000 frames or 2 seconds. The requested linear seam overlap is 12, 000 frames, using the tail-to-head profile above. Its 72, 000 middle frames followed by 12, 000 blended frames shorten the cycle by the overlap.

The output therefore has 84, 000 frames, two channels and duration 1.75 seconds. Its first frame comes from original source frame 36, 000 (0.75 seconds), not the selected start at frame 24, 000; that changed start point must be compatible with the requested use. If serialized as 16-bitPCM without extra chunks, the audio payload has 84, 000×2×2 =336, 000 bytes; the total RIFF file also includes headers. This arithmetic is not a claim about audible smoothness.

The handoff records the 0.5–2.5 second source interval, 0.25 second overlap, encoding and any allowed gain change. Independent parsing checks frames/rate/channels; listening remains explicitly unperformed if no playback check occurred.

## Evidence status

The worked example illustrates the stated inputs and reasoning. Unless an execution result is explicitly identified, it is not a claim that external services, real devices or user data were tested. Report actual checks and unrun stages on each use.
