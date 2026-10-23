---
name: prepare-editorial-timeline-interchange
description: "Transfer an existing edit into an agreed timeline interchange format, preserving source-to-sequence timing, track structure and media identities while exposing unsupported effects and missing handles. Use for editable conform handoff, not a new cut or a finished movie export."
---

# Prepare an editorial timeline interchange

Deliver an editable timeline candidate, a media identity map and a concise conversion-loss report. The recipient must be able to reconstruct the intended edit, not merely open a file with the correct duration. OpenTimelineIO (OTIO) is a useful intermediate representation when both sides support the required features; it is not a universal replacement for a native editing project.

[Create an edited video](../create-edited-video/SKILL.md) owns editorial choices and the finished viewing file. [Prepare a video proxy handoff](../prepare-video-proxy-handoff/SKILL.md) owns proxy associations. This workflow preserves an existing edit across representations; do not recut it, attach proxies or flatten it merely to make conversion succeed.

## Establish the interchange contract

Identify the source project/export and exact sequence revision, destination application/version, requested interchange format and required editable features. Clarify whether the recipient needs picture only, picture and sound, or selected tracks. Establish whether media is included, already shared through an authorized location, or intentionally offline. Preserve the native source and work on a new candidate.

Inspect the actual source before asking broad questions. A simple straight-cut sequence needs a short mapping, not a studio asset database. Ask only when an unresolved choice affects the result: which sequence is authoritative, whether a speed effect may be baked, or whether a target without nesting is acceptable.

Confirm the installed reader/writer and its supported direction, version and options. The [OTIO adapter documentation](https://opentimelineio.readthedocs.io/en/latest/tutorials/adapters.html) distinguishes native formats from separately maintained adapters. A format being listed does not establish that this environment has the adapter, that it writes the format, or that the receiving editor preserves the features needed here. Do not install plugins automatically to obtain a conversion path.

If the receiver is unknown, return a clearly labeled neutral candidate and feature inventory, not an assertion of import compatibility. If no authorized converter is available, prepare the mapping and exact blocker; a shot list alone is not the requested editable interchange.

## Preserve identity before translating time

Inventory the selected sequence as ordered clip occurrences, gaps, transitions, tracks and nested compositions. Keep a stable relationship to the original occurrence or its source hierarchy path. Two uses of the same take are two edit occurrences, not duplicate records to remove.

For each occurrence, retain the source asset identity, relevant reel/card context, source in/out or start/duration, playback interpretation, parent placement and track role. Record the sequence origin and source timecode convention where supplied. Do not match solely on a basename or a reset timecode. A repeated filename can identify different takes; a renamed file can be the same take.

Map media references separately from editorial structure. Preserve evidence of source revisions and known available coverage. Treat missing media as missing; do not replace it with the nearest filename or convert its clip into an intentional gap. The recipient needs to distinguish an absent take from deliberate empty timeline space.

For portable paths, use the target's documented URL/path convention and an agreed package root. Retain a private old-to-new map when necessary, but exclude credentials, expiring access tokens and unrelated workstation paths from the delivered report. Do not fetch every referenced URL to discover media. Bundling, uploading or sending footage requires the appropriate data and destination authorization.

## Keep coordinate systems and endpoint rules explicit

Maintain both the value and rate for each time quantity. In OTIO, `RationalTime` represents value divided by rate, and `TimeRange` stores start plus duration. Use an explicitly stated end-exclusive comparison convention in the review map; translate an inclusive final-frame label rather than copying it into a duration. Keep exact rate evidence instead of rounding a fractional rate to a nearby integer. See the [OTIO architecture reference](https://opentimelineio.readthedocs.io/en/latest/tutorials/architecture.html).

Separate source-media time, immediate-parent time and final-sequence time. A nonzero source timecode origin is not a leading gap, and a sequence display origin is not an instruction to shift every clip's source range. Preserve the source's interpretation when a timecode label alone cannot establish elapsed time.

In OTIO, a clip's `source_range` is its selected media segment; `available_range` describes known media coverage. `trimmed_range()` selects the source range or falls back to available coverage, while `visible_range()` also accounts for adjacent transitions. Neither is automatically the clip's final-sequence placement. Parent trims can hide all or part of an occurrence. Markers are relative to their owning item. Use the documented coordinate conversions rather than summing raw starts across nesting. See [Time Ranges](https://opentimelineio.readthedocs.io/en/latest/tutorials/time-ranges.html).

For mixed rates, retiming, freeze frames or reverse playback, record the source-to-sequence mapping and target support separately. Rescaling a time quantity is not permission to reinterpret playback speed. If a variable-rate recording lacks an evidenced frame-to-time map, retain that uncertainty rather than deriving precise source frames from a nominal rate.

## Preserve structure and expose representational loss

Retain track ordering, audio roles, nesting and trim boundaries where supported. An upper-track gap can reveal lower content, so it is not necessarily a black picture. OTIO transitions use media on either side of a cut without adding to the track's duration. Their offsets require handle coverage beyond the selected cut ranges; the format can describe requests for media that is not actually available. Effects may have application-specific behavior. These distinctions are described in [Timeline Structure](https://opentimelineio.readthedocs.io/en/latest/tutorials/otio-timeline-structure.html).

For each transition, compare the required source coverage against known available media. Report missing head or tail handles by occurrence and interval. Do not shorten the edit, repeat an edge frame or remove the dissolve silently. Unknown coverage is not proof that the handle is missing, nor evidence that it exists.

Make a compact feature disposition list: preserved, deliberately transformed, unsupported or unverified. Apply it to features actually present, such as retimes, nested/multicam selections, generators, titles, transforms, audio automation, color treatment and markers. Preserve associated metadata where useful, but metadata surviving in a file does not prove that an editor applies the corresponding effect.

When the receiver cannot preserve a required feature, offer a specific choice: a more capable format, the native project, an explicitly approved baked segment with source linkage, or a handoff with that feature unresolved. Baking changes editability and may require rendering and additional media delivery. Do not make that tradeoff without the user's applicable instruction. Keep unsupported content in the original and the loss report rather than deleting it from the evidence.

## Write a candidate and compare what was saved

Use trusted available tooling and an explicitly selected adapter/configuration. Inspect enabled hooks and media-linker behavior before conversion; a parser path can invoke plugins. For a metadata-only conversion, disable unnecessary automatic media linking through the supported mechanism and do not execute scripts shipped beside an input export. OTIO's [architecture documentation](https://opentimelineio.readthedocs.io/en/latest/tutorials/architecture.html#otio-media-linkers) describes automatic linker invocation and the option to disable it.

Save to a separate candidate path and read the saved interchange back. Compare semantic edit decisions with the frozen source map rather than serializer whitespace or record count alone:

- Every selected occurrence has an explained destination, including repeated uses, excluded tracks and held features.
- Source identities, selected intervals, parent placements and final-sequence boundaries agree under the declared rate and endpoint conventions.
- Intentional gaps, layer order, nested trims, transitions and needed handles retain their intended meaning.
- Required audio roles, markers and supported effects survive at the correct owner and time position.
- Media references resolve in the agreed delivery context, or each offline dependency remains explicit.
- Unsupported or transformed features have not disappeared from the loss report.

A same-adapter round trip can reproduce its own mistake. When available and authorized, open the candidate in a separate recipient project and inspect risky boundaries against the source or an existing reference movie. Check first/last frames around cuts, transitions and retimed sections, not only total duration. Use actual listening capability for sound claims; a waveform is not evidence of an audition. Do not alter the recipient's production project merely to validate an export.

Keep separate claims for serialized-file checks, media resolution, receiving-editor interpretation and audiovisual review. A successful parse does not establish any of the latter. If the source or target application is unavailable, provide the candidate and precise unperformed checks without calling the conform verified.

## Recovery and completion

If conversion loses timing or features, retain the failed candidate for diagnosis and correct the narrow mapping or choose an approved alternate format. Repeat affected saved-file comparisons. Do not compensate for drift by nudging downstream clips without finding its cause. If a conversion or import response is uncertain, inspect the actual output/project before retrying; repeated imports can create duplicate sequences.

Deliver the candidate, source/target version and adapter details, media map, feature losses and verification coverage. A small edit can carry these in one readme. State exactly which remaining choices block a faithful conform. Creating the interchange does not authorize uploading media, publishing a movie, replacing the original project or approving editorial changes.

## Fictional, unexecuted illustration

At 24 frames per second, occurrence A selects source frames `[100,148)` and occupies sequence frames `[0,48)`. Occurrence B selects `[200,248)` and occupies `[48,96)`. A dissolve at their cut has six-frame in/out offsets. The sequence remains 96 frames, not 108. A needs tail coverage through frame 153 inclusive, and B needs head coverage beginning at frame 194.

Suppose A's supplied available range ends at exclusive frame 150. Its last four needed tail frames, `[150,154)`, are unavailable according to that evidence. The proposed handoff preserves the edit and reports that missing handle; it does not invent repeated frames or shorten the dissolve. If the recipient accepts a different transition, that becomes an explicit changed edit, not a lossless conversion.

These are illustrative expected relationships, not an observed conversion. No serializer, editor import, media probe, render or playback was executed for this example.
