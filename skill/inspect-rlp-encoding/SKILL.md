---
name: inspect-rlp-encoding
description: "Decode or validate a supplied RLP byte tree with exact prefix and container boundaries, canonicality checks and explicit separation from higher-level Ethereum semantics."
---

# Inspect RLP encoding

Use for a concrete RLP item, a codec check or a byte-range explanation. This is separate from ABI argument decoding, bytecode disassembly and transaction execution.

## Required inputs

- Exact hexadecimal bytes and whether they represent one RLP item or an explicitly identified envelope
- The requested result: structural validation, a byte-offset explanation, or extraction of a subtree
- Resource limits and, if protocol meaning is requested, the applicable schema

## Workflow

### Establish framing and meaning

Obtain the exact bytes and whether the caller expects one item or a separately specified envelope/stream. Do not strip a leading byte because the remainder looks plausible. A typed transaction or other wrapper needs its own framing evidence before extracting the RLP body.

Choose explicit byte, node and nesting limits. Clarify whether the result is structural RLP validation or validation against an additional protocol schema. A byte leaf is not automatically an integer, text string, address or account. Empty bytes and an empty list are distinct values. Leading-zero rules for protocol integers must not be imposed on arbitrary byte strings without that schema.

### Decode bounded containers

Follow the [Ethereum RLP definition](https://ethereum.org/developers/docs/data-structures-and-encoding/rlp/) for direct single bytes, short byte/list payloads and long length-prefixed payloads. Treat lengths as exact unsigned values and check them against available bytes and resource limits before converting indices or allocating memory.

Check every child against its containing list's end, not merely the end of the complete input. Record each item's encoded start, payload start and end with a clear inclusive/exclusive convention. Advance by the complete encoded child length; require children to fill their parent exactly. If one item was requested, retain a trailing-byte error instead of silently ignoring the rest.

For strict canonical validation, reject redundant single-byte prefixes, leading-zero length fields and long forms used for short payloads. Re-encode the decoded byte tree and compare the complete original bytes as a further consistency check. State whether a rejection is a format violation or only an implementation resource limit.

### Preserve inspectable evidence

Return a typed byte/list tree, exact byte ranges and the chosen limits. Keep node IDs and paths scoped to that input; edits must invalidate old selections and exports. A paged view should not discard nodes from the full report. A subtree export must include its own original prefix and payload, and should be checked as a standalone item.

Keep optional text previews separate from the byte value. Decode previews strictly, preserve a BOM when present, and escape invisible controls for display. Invalid text encoding does not make an otherwise valid byte leaf invalid. Do not normalize the underlying bytes to improve the preview.

A structurally valid item can still be invalid for its purported transaction or trie schema. Do not infer signatures, ownership, authorization, a chain state or execution success. Exports can expose private bytes; share them only within the user's authorized destination and scope.

### Locate a byte without losing its container

When explaining an offset, use zero-based byte offsets into the complete encoded item, not hex-character positions or payload-relative indices. Select the deepest node whose half-open encoded interval contains the offset. A byte in a list prefix belongs to the list itself, while a byte in a nested child belongs to that child. A direct single-byte leaf has no separate prefix. Reject negative, fractional, unsafe and end-exclusive offsets; do not silently clamp them. Keep the prior selection on invalid input and invalidate offset results when source bytes change.

For a paged inspector, move to the selected node's page and restore keyboard focus to it. Report whether the selected byte is in the node's prefix or payload; this does not add protocol meaning.

## Verify a codec or repair

Use an independent implementation for canonical positive vectors. Include all one-byte values, empty bytes/lists, short/long boundary lengths, nested lists and supported capacity limits. Separately exercise truncated lengths, huge declared lengths, leading-zero lengths, redundant prefixes, parent-boundary crossings, trailing data, depth limits and node limits. Do not let a permissive reference decoder define the strict rejection policy by accident.

For a byte locator, compare every offset in a bounded fixture corpus against an independent exhaustive search of the recorded intervals and depths. Separately check invalid offsets, prefix boundaries, page changes, focus restoration and source-edit invalidation. Model and DOM tests do not establish rendered layout or live browser behavior; report those checks separately.

## Worked example

Given the synthetic item `0xc583636174c0`, explain byte offset 2 and extract its containing leaf:

1. `c5` introduces a list with five payload bytes. Its encoded interval is `[0, 6)` and its payload interval is `[1, 6)`.
2. The first child starts at offset 1. `83` introduces three bytes, `636174`. Its encoded interval is `[1, 5)` and its payload interval is `[2, 5)`.
3. The second child is `c0` at offset 5: an empty list with encoded interval `[5, 6)` and empty payload interval `[6, 6)`.
4. Offset 2 selects the first child and lies in its payload. An optional strict UTF-8 preview reads `cat`; the authoritative value remains the bytes `0x636174`.
5. Extract `0x83636174`, including the child's prefix. Decoding and re-encoding that extracted item must reproduce it exactly. Returning only `0x636174` would lose the leaf's framing and produce trailing data if interpreted as one RLP item.

Boundary checks: offset 0 selects the outer list's prefix; offset 1 selects the first child's prefix; offset 5 selects the empty list's prefix; offset 6 is out of range. Replacing the final `c0` with `80` produces empty bytes instead of an empty list, even though the item length stays the same.

## Deliverable

Provide the structural verdict, byte/list tree, exact encoded and payload ranges, and any requested offset or subtree result. Include the resource limits and verification performed. Keep optional previews and schema-dependent interpretations clearly separate from the decoded bytes.
