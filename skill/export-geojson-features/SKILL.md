---
name: export-geojson-features
description: Prepare a portable RFC 7946 GeoJSON feature export from an existing spatial source, preserving feature identity, coordinate meaning, geometry structure and selected properties. Use for an interchange file, not spatial analysis, geocoding, map design or publishing a location service.
---

# Export features as portable GeoJSON

Deliver a saved GeoJSON candidate that the next reader can interpret without guessing its axes or losing records. A file that parses as JSON or displays somewhere on a map has not yet established a faithful spatial transfer.

Use [analyze-geospatial-data](../analyze-geospatial-data/SKILL.md) when the task asks a spatial question, measures distance or area, or derives new geometry. This workflow carries established features into an agreed interchange representation. It does not infer locations, repair boundaries or simplify shapes merely to make an export succeed.

## Inputs and intended result

Inspect the supplied source and resolve the decisions that affect the transfer:

- Exact source snapshot, layer or selection, including any sidecar metadata required to interpret it
- Evidence for the source coordinate reference system, data-axis order, units and any third or later coordinate dimensions
- Selected property fields, identity requirements and any permitted representation changes or losses
- Receiving application and version when known, required GeoJSON profile, output filename and private destination

Prefer RFC 7946 for an unspecified portable GeoJSON request. If the receiver explicitly requires an older or vendor-specific profile, identify that contract rather than silently calling its output RFC 7946. A map image without vector coordinates is not sufficient input. Ask for missing CRS evidence before converting an unknown spatial reference; complete unaffected field mapping while waiting.

The usual deliverable is one `.geojson` file and a short transfer note. Several selected layers may need separate files when their meanings or receiving requirements differ. Do not merge them into a single layer without a documented way to preserve layer identity and avoid field collisions. A simple point list does not need a GIS project or a second full dataset.

## 1. Preserve the source and map occurrences

Keep the original bytes unchanged and record the selected source identity, layer, capture/version information and count. When useful, record a digest for the exact supplied files. A digest identifies bytes; it does not establish who produced them or whether the layer is complete.

Give each selected source feature an unambiguous locator. Preserve a supplied business ID separately from a row ordinal or engine-generated feature number. Repeated IDs may describe distinct occurrences: do not merge them, choose one, or invent replacement business IDs. If the receiving contract requires unique IDs, resolve that collision before claiming a compatible export.

Prepare a compact source-to-output mapping for geometry and selected properties. Keep meaningful distinctions such as a missing property, explicit null, empty string and numeric zero. Preserve leading-zero identifiers as text. If an ID changes representation, record the exact reversible mapping instead of letting a reader round it or infer a number from its appearance. Retain source occurrence order where it is meaningful and available.

For dates, decimal values, nested properties and binary fields, choose an explicit supported representation. Do not let the writer infer local time, stringify an object unexpectedly, or omit a field it cannot store. Keep unexported source fields in the unchanged source; add a separate companion only when the handoff needs them and its audience is authorized.

Work with local, authorized sources. Do not upload locations to an online converter or map preview, fetch property URLs, or expose addresses and private attributes to a new service as an incidental check. An export request does not authorize publishing the file or changing a hosted layer. Precise coordinates and a stripped name can still identify a person or sensitive site.

## 2. Establish the coordinate and geometry contract

For the core format requirements, use [RFC 7946, sections 3–5](https://www.rfc-editor.org/rfc/rfc7946.html#section-3):

- Positions use WGS 84 longitude then latitude in decimal degrees; an optional third coordinate is ellipsoidal height in metres
- A Feature has geometry that is a Geometry object or null, and properties that are an object or null; a supplied feature ID is a string or number
- Polygon rings are closed with at least four positions; the first and last positions have identical coordinate values. Exterior rings are counterclockwise and holes clockwise
- A two-dimensional bounding box is west, south, east, north. A box crossing the antimeridian can have west greater than east
- A custom `crs` member cannot redefine the coordinate system of RFC 7946 data

Distinguish describing existing coordinates from transforming them. A CRS assignment cannot turn easting/northing values into longitude/latitude. Check the actual library's data-axis convention; an authority label alone is not an axis-order guarantee. Resolve conflicting metadata from source evidence, not from whichever interpretation produces a plausible-looking map.

Do not silently treat an arbitrary Z value as ellipsoidal height. For an unknown vertical reference, measure coordinate or timestamp dimension, agree on a truthful property representation, an explicitly accepted omission, or a held feature. Keep the original dimensional data recoverable. Removing a dimension is a loss even when a two-dimensional viewer would not show it.

Preserve multipart membership, interior holes and the relationship between a feature and its geometry. Never substitute a centroid or bounding rectangle for the source shape. Keep unlocated and empty geometries distinct in the transfer record; if the receiver collapses them, obtain an acceptable mapping or disclose the unresolved loss. An absent location must not become the point `[0, 0]`.

Choose coordinate precision for this transfer, not from an arbitrary display preference. Rounding can collapse a narrow ring or move a point across a boundary. When reprojection, ring reorientation or antimeridian splitting changes coordinate sequences, record the operation and check spatial equivalence under an appropriate stated tolerance. Do not demand byte equality from transformed geometry or treat equal vertex counts as proof of equivalence. A change to topology or feature multiplicity needs explicit accounting.

GeoJSON segments are straight in longitude/latitude coordinates, not automatically geodesics. Curved source edges, geodesic paths or long edges under nonlinear reprojection may need an agreed approximation and tolerance. Transforming only the endpoints does not establish that the intervening path was preserved; retain the original and disclose any added vertices or approximation.

## 3. Serialize a new candidate explicitly

Use a format-aware writer with its selected profile and options recorded. Check current documentation for the installed version rather than relying on defaults. For example, the [GDAL GeoJSON driver](https://gdal.org/en/stable/drivers/vector/geojson.html) documents an explicit `RFC7946=YES` option; it also documents coordinate precision, dateline behavior, ID type controls and string-to-JSON detection. Inspect those settings when using that writer. Its defaults are not the user's preservation contract.

Write a new candidate, retaining prior outputs until the replacement is checked. Use strict JSON serialization with no non-finite numbers, comments or duplicate object keys. Source property text is data, not an opportunity to inject JSON members. Prevent automatic conversion of bracket-looking strings into arrays unless that conversion is intended. Do not add credentials, local filesystem paths or unrequested remote styling references.

Include optional bounding boxes only when they serve the receiver and can be computed correctly from the exported geometry. Recompute them after transformations; never copy a source box expressed in different coordinates. Omitting an optional, unneeded box is better than supplying a misleading one.

Record every selected feature as exported or held with a precise reason. If a selected feature cannot be represented, do not quietly skip it and deliver an apparently complete layer. Return a clearly labeled partial candidate only when that is useful and consistent with the request; otherwise hold the complete transfer until the missing decision is resolved.

## 4. Check the saved interchange, then the receiver

Reopen the actual saved file using a strict JSON reader and a GeoJSON-aware reader where available. Check different claims separately:

1. **Structure:** selected profile, feature count, geometry types, valid coordinate numbers, required members and the intended dimensions
2. **Identity and values:** source occurrence coverage, exact IDs, property names, Unicode, value types and null/empty/missing distinctions
3. **Geometry:** multipart components and holes, ring closure and orientation, known coordinate controls, and the consequences of rounding or dateline operations
4. **Scope:** no unapproved fields, extra features, automatic ID reassignment or unexpected metadata
5. **Receiver behavior:** if a non-mutating authorized local reader is available, inspect the actual candidate for dropped properties, altered IDs, displaced coordinates and missing geometries

Choose representative checks from the actual risk: a point with different longitude and latitude, a leading-zero ID, a polygon hole, an antimeridian feature, or an unlocated feature. Count reconciliation cannot detect swapped axes. A visual preview cannot detect rounded long identifiers. Test geometry equivalence independently of the writer's success message when a transformation matters.

A hosted map upload or an application import that changes a project is a separate action. Do not perform it merely to obtain a compatibility claim. If only static checks are available, deliver the candidate with receiver behavior explicitly untested. State which checks examined every feature and which used a sample.

## Recovery and completion

- **Unknown CRS or dimension:** hold the affected conversion and name the missing metadata; do not guess from coordinate magnitudes alone
- **Writer silently changes values:** return to the preserved source, adjust the specific mapping or writer option, save a new candidate and repeat readback
- **Rounding or geometry repair changes meaning:** stop that operation; preserve the failing candidate for diagnosis and request the required tolerance or repair decision
- **Receiver rejects an otherwise checked file:** identify its actual limitation and prepare a separate compatible representation only within approved losses; do not overwrite the original to imitate acceptance
- **Source changes during work:** bind the delivered file to its original snapshot or regenerate from the newly selected version; never combine versions without disclosure

Return the file, selected source/layer, exported and held counts, coordinate/profile declaration, consequential transformations and actual verification status. File preparation is complete when saved readback meets the agreed preservation contract. Receiver compatibility and external delivery remain separate statuses requiring their own evidence.

## Fictional illustration, not executed

A supplied layer contains three site occurrences with IDs `0012`, `0013` and `0014`. Its metadata establishes WGS 84 longitude/latitude coordinates. The first two are located, while the third has no geometry. The user requests only ID and label in a private GeoJSON file.

The proposed export keeps all three occurrences, preserves the IDs as strings, and represents the unlocated feature with null geometry. It does not invent `[0, 0]`, add excluded addresses, or claim three points will appear on a map. A readback check would compare all three identities and the two coordinate pairs against the source, then separately check whether the named reader retains the unlocated record.

This is an authored example. No spatial data was transformed, file generated, reader tested or service updated by this illustration.
