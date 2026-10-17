---
name: prepare-gpx-route-handoff
description: "Prepare existing route, track and waypoint data for a named mapping app as a GPX handoff, preserving travel order, segment breaks and supported point metadata. Use for moving an established path between tools; not choosing a route, calculating directions, live navigation or certifying current access or safety."
---

# Prepare an existing path for a mapping app

Deliver a GPX file and a compact transfer note that tell the recipient what the path represents and what the receiving app has actually been shown to preserve. The meaningful result is a usable route/track transfer, not merely coordinates that draw a plausible line.

Use [export-geojson-features](../export-geojson-features/SKILL.md) for a general feature-layer export. This workflow instead preserves ordered journey semantics: a standalone place, a route's planned sequence, a track's continuous spans and the distinction between recorded and planned times. Use [analyze-geospatial-data](../analyze-geospatial-data/SKILL.md) for measurements or derived spatial answers.

## Establish the source and receiving behavior

Obtain the exact supplied file/export or authorized coordinate records, the selected routes/tracks/waypoints, and the target app/device/version when known. Determine:

- Whether the source represents an established planned route, a recorded track, or independent saved places
- Evidence for point order, route/track grouping, segment breaks, coordinates and their reference system
- Which names, elevations, timestamps, notes and extensions must survive, and which fields the user explicitly wants excluded
- Target limits and documented handling of routes versus tracks, point counts, segments, recalculation and supported extensions
- The private output destination and whether account upload/device import is requested or preparation only

A screenshot, place names or an unordered table does not establish a complete path. Request an actual export or the missing order/grouping rather than tracing or geocoding it as an incidental step. Inspect a supplied file before deciding from its extension what it contains. An existing GPX file can contain several object types at once.

Read the receiving product's current official documentation when making compatibility claims. If the consumer is unspecified, prepare a GPX 1.1 candidate and state that target behavior is untested. Do not assume that every GPX importer retains tracks, routes, waypoints and metadata equally.

## 1. Preserve the original and the journey structure

Keep source bytes unchanged. Record source identity/revision and the selected objects. Assign private source locators to each object, segment and point occurrence; do not use a displayed place name as a unique key. Repeated visits to the same coordinates can be essential to an out-and-back path and must not be deduplicated.

Build a small mapping of source objects to output objects, with their ordered point counts, segment counts and field dispositions. Keep independent waypoints independent unless the source explicitly makes them route points. A saved café near a track is not automatically a required stop on it.

Preserve source direction and segment boundaries. Do not sort points by name, latitude or timestamp, join separate recordings, reverse a path or connect the end of one span to the start of another merely to make one line. A gap may mean missing observations, separate activity or an intentional break; retain the evidenced break without inventing its cause.

Where source data is inconsistent, hold the affected object or deliver a clearly labeled partial transfer only if that meets the user's intent. Dropping one invalid point from the middle may create a misleading shortcut. Do not silently continue the line across a removed point or segment.

## 2. Map meaning before writing XML

The [GPX 1.1 schema documentation](https://www.topografix.com/GPX/1/1/) defines WGS 84 coordinates, metric measurements, standalone `wpt` points, ordered `rte`/`rtept` routes and `trk` tracks containing `trkseg` spans of `trkpt` points. Keep these roles explicit. A route may be recalculated by a receiving app; a track's shape does not itself supply turn instructions. Do not substitute one role for another solely to satisfy an importer.

GPX requires latitude/longitude attributes. Establish their meanings from source metadata; do not copy a longitude-first pair into latitude-first fields. Confirm that latitude lies from -90 through 90 and longitude from -180 inclusive to 180 exclusive for the 1.1 schema. A source's positive 180-degree longitude needs an explicit equivalent-boundary mapping, not an unexplained rejection or arbitrary clamp. Coordinates outside the required reference system need a supported, documented transformation; relabeling the values does not transform them.

Preserve supported coordinate precision. Extra decimal digits do not increase source accuracy. Any rounding or point reduction needs a declared tolerance and acceptance of its effect on the intended path. Do not simplify a path merely to fit a consumer's point limit without approval of the resulting loss.

Treat elevation as optional measured data with its actual units and vertical-reference evidence. Do not supply zero when unknown, invent heights from an online lookup, or assume a source's third coordinate has the required meaning. If faithful conversion is unresolved, preserve the source field separately in the private mapping and hold or explicitly omit it according to the agreed contract.

Distinguish recorded point time, planned arrival time, file-generation time and metadata time. Do not fabricate a plausible pace, distribute timestamps evenly along the path or replace a recording date with today's date. Preserve an evidenced time-zone interpretation and any missing times. Ambiguous local times cannot be silently labeled UTC. Preserve sequence even when timestamps repeat or move backward; flag the source anomaly rather than sorting the path.

Handle application extensions deliberately. They may contain navigation cues, activity measurements, identifiers or personal data. Keep a required supported extension with its namespace and exact meaning, map it through a documented target feature, or disclose the loss/hold. Do not turn unknown extension content into core GPX fields or claim that retaining XML proves the receiving app uses it.

## 3. Minimize location exposure without changing the story silently

Precise path endpoints, times, names and embedded links can reveal homes, routines or private visits. Use only authorized sources and fields. Do not upload coordinates to an online converter, map preview, elevation service or routing engine as an incidental check. A requested export does not authorize a public activity post or account synchronization.

If the user requests a less revealing share copy, agree on which endpoints, time fields or notes to remove and preserve the private original. Reducing names alone does not anonymize a track. Remove a sensitive span as an explicit omission and preserve the remaining spans separately; do not join them with a new apparent route or claim a complete journey. Review descriptions, extensions, links and output filenames as well as visible point names.

Do not strip attribution or required rights information as ordinary cleanup. Keep the audience-facing transfer note minimal while retaining enough private lineage to explain an omission or correction.

## 4. Write a separate, target-scoped GPX candidate

Use a supported GPX writer or safe XML serializer. For GPX 1.1, use the documented namespace, version and creator attributes, required coordinate attributes and schema element order. The creator should identify the actual exporter/workflow truthfully, not impersonate the source recording device. Escape names and descriptions as text; do not interpret them as markup or commands.

Write only the selected objects and approved metadata to a new file. Keep metadata bounds absent unless they are useful and correctly recomputed from the final selected coordinates. Do not copy stale bounds from an untrimmed source. Avoid adding remote image references, credentials or internal filesystem paths.

Parse source XML without external-entity or network resolution. If schema validation is available, use a trusted local copy of the applicable schema rather than following arbitrary schema locations supplied by the file. Static syntax review, XML parsing, schema validation and target import are separate levels of evidence.

For a consumer requiring multiple files, split only along a documented object/segment mapping and preserve the intended order in the handoff note. For a route that exceeds limits, stop for an accepted simplification/splitting decision rather than silently discarding points. Keep the unchanged source and any previously checked candidate.

## 5. Check the saved path and receiving interpretation

Reopen the actual output and reconcile:

1. Selected route, track, waypoint and segment counts, with one disposition for every selected source object
2. Point order, repeated visits, first/last points and all segment boundaries
3. Coordinate fields against source controls with unequal latitude/longitude, including relevant negative values or dateline cases
4. Preserved names, elevations, time semantics and supported extensions; no unknown value has become zero or an invented timestamp
5. Approved omissions and transformations, including whether a privacy trim changed continuity

Inspect the shape in an authorized local, non-network viewer when available, checking direction, disconnected spans and unintended straight joins. A visual line alone does not prove point-for-point preservation, correct metadata or a usable route. State whether the entire sequence or only representative points were compared.

If target import is authorized, confirm the destination/account and likely sync audience, preserve existing routes and use a distinct candidate name. After import, inspect actual object type, counts where exposed, direction, segment treatment, names and any automatic recalculation. A success banner does not prove that the track shape survived. Do not start navigation, record an activity, change a device's routing defaults or publish the path merely to check import.

Report preparation, structural checks and target interpretation separately. GPX data is not an offline basemap; the receiving device may still need its own map data and supported offline capability. File acceptance does not verify present-day path access, closures, terrain, permissions or safety.

## Recovery and final handoff

- **Wrong axes or reference system:** return to the source mapping, correct the actual transformation and compare known controls before delivering
- **Consumer merges segments or recalculates a different path:** retain the original candidate, document the observed change and seek a supported preservation route or the user's accepted tradeoff
- **Required metadata disappears:** identify the unsupported field and hold equivalence claims; do not treat the source archive as proof the target retained it
- **Import response is uncertain:** inspect the target for the exact candidate before retrying; avoid duplicates and never remove unrelated saved paths
- **Source revision changes:** regenerate from one agreed revision or clearly bind the delivered file to the earlier snapshot

Return the `.gpx` file, source/version, object and segment summary, target/profile, intentional losses, actual verification and any remaining import step. Stop at the requested preparation or verified handoff stage. Do not claim navigation readiness when the evidence only supports artifact transfer.

## Fictional example, not executed

An invented source has one recorded track with two ordered spans of three and two points, plus two independent named waypoints. The spans are separated because the source explicitly marks an observation break. The request is a private GPX candidate preserving the track and places; no app import is authorized.

The expected output has one track, two track segments, five track-point occurrences and two standalone waypoints. The break remains a break, and the waypoints are not inserted into the track. One point without elevation stays without elevation. The handoff notes that offline maps and consumer treatment of the break remain unchecked.

This is an authored illustration only. No GPX was generated, coordinates transformed, mapping app opened, file imported or physical route assessed for the example.
