---
name: verify-merkle-consistency
description: "Verify that two supplied Merkle tree snapshots have an append-only prefix relationship under a declared tree scheme, keeping both root anchors and the scope of the history claim explicit."
---

# Verify consistency between two Merkle snapshots

Use for an older/newer tree-head pair and its consistency proof. Membership of one leaf is a different question. A valid relationship between two roots does not authenticate either publisher, rule out split views shown to other clients, or certify an entire log's operating history.

## Required evidence

Obtain both expected roots and sizes, their provenance, the proof's hash list, and the hash/tree-shape conventions. Establish the ordering from the sizes rather than a timestamp alone. If the expected roots came only from the proof packet, label the check internal consistency; do not silently treat them as independent trusted anchors. Signature verification, key trust and an authorized retrieval of published heads remain separate tasks when needed.

Keep the old and new roles explicit throughout parsing, output and comparison. Bound sizes, proof length and input bytes to the implementation's supported range before converting large numeric fields or allocating memory. Reject unknown schemes and malformed digests instead of trying alternate padding or concatenation conventions until something passes.

### Preserve exact sizes before choosing a verifier branch

Parse both sizes without rounding before testing zero, equality, ordering or powers of two. [RFC 9162 §4.11](https://www.rfc-editor.org/rfc/rfc9162.html#section-4.11) carries both sizes as unsigned 64-bit integers. Preserve those values in the report as well as the calculation. A smaller implementation range is acceptable when declared; an unsupported size is not a failed cryptographic proof.

For JavaScript, use an exact integer representation throughout, such as BigInt parsed from lossless input, or reject sizes outside an explicitly supported exact range. Converting an already rounded Number to BigInt does not recover the original size. The [safe-integer boundary](https://tc39.es/ecma262/multipage/numbers-and-dates.html#sec-number.max_safe_integer) matters even before hashing: distinct transported sizes can otherwise compare equal and wrongly select the equal-size shortcut. Apply the same exactness to the power-of-two test that selects the verifier's initial hash and to both traversal counters. Number [bitwise operations](https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#sec-numberbitwiseop) narrow operands to 32 bits; replacing a signed shift with an unsigned Number shift does not preserve a 64-bit counter.

Fictional, unexecuted illustration: an older size of 4,294,967,297 is not a power of two. A JavaScript Number implementation using `(size & (size - 1)) === 0` reduces the operands to 1 and 0 and incorrectly reports that it is. In the RFC verifier that selects the wrong initialization route by prepending the older root. Keep the size exact and use a compatible exact-integer test instead. This illustrates a branch-selection defect, not a computed proof or an observed failure in a particular implementation.

## Apply the scheme's verifier

For the history-tree scheme, use [RFC 9162 §2.1.4](https://www.rfc-editor.org/rfc/rfc9162.html#section-2.1.4) with its separate old/new hash accumulators and uneven-tree handling. A single root reconstructed from a membership path is insufficient. Both reconstructed roots and the traversal's completion condition must match.

Handle boundary cases explicitly. The older size cannot exceed the newer size. Equal sizes require equal roots; define whether the accepted representation also requires an empty proof. A zero-size older tree imposes no constraints on earlier records, so do not present that vacuous case as meaningful evidence of preserved contents. Supporting or rejecting it should be explicit. A growing nonempty pair requires a complete proof; reject missing and excess nodes.

Do not replace a failed consistency proof by rebuilding an unrelated tree whose root happens to match one anchor. Reconstructing from a complete authorized record set is useful independent evidence only when it is tied to both intended snapshots and the same encoding rules.

### Validate empty-tree snapshots before fast paths

When zero-size snapshots are supported, check each zero-size root against the scheme's empty-tree hash before accepting an equal-size or empty-prefix case. For [RFC 9162 §2.1.1](https://www.rfc-editor.org/rfc/rfc9162.html#section-2.1.1), that is HASH of zero bytes. It is not an all-zero digest, a missing root, or the root of one empty record, which hashes the leaf prefix byte. Equal supplied roots alone do not validate two zero-size snapshots.

Keep the empty-case handling outside the [growing nonempty verifier](https://www.rfc-editor.org/rfc/rfc9162.html#section-2.1.4.2), whose precondition is 0 < old size < new size. Declare the accepted empty-proof representation. An accepted empty-to-nonempty pair establishes only the vacuous prefix relationship; it does not reconstruct or independently verify the newer root's contents.

Fictional, unexecuted illustration: two size-zero snapshots supply the same well-formed digest that differs from HASH of zero bytes. An equality-only shortcut would pass, but both snapshots fail the declared tree scheme. Check this case, a valid empty pair, an empty-to-nonempty pair and one empty record separately when implementing the verifier; these are proposed checks, not execution evidence.

## Report the bounded conclusion

Include scheme, both sizes and roots, provenance, pass/fail or unsupported status, and which checks failed. A path trace can show the old and new accumulators at each step. Label incomplete accumulations as intermediate hashes, not verified roots. Retain the distinction between a well-formed nonmatch and malformed input.

For an interactive checker, bind results and exports to the submitted pair of anchors and proof. Changing an input invalidates the verdict; a late calculation must not overwrite a newer one. Proof hashes can reveal predictable underlying values through guessing, even when the raw records are absent. Keep private evidence local unless sharing is authorized.

## Verification exercise

Generate synthetic sequences and compute their complete prefix roots using an independently structured hash calculation. Verify every supported old/new size pair, especially around powers of two and uneven right edges. Mutate each anchor and path component; remove and append nodes. A rewritten old-prefix record should fail against the preserved old anchor, while a changed newly appended tail with its corresponding new proof can legitimately pass.

For an implementation that supports large snapshots, add bounded metadata/path cases around 2^31, 2^32 and its exact-integer limit. Check power-of-two classification, both traversal counters, unequal adjacent sizes, and round-trip preservation through the input and report formats. Include an explicitly rejected value outside the supported range. Use an independent exact-integer reference rather than materializing enormous trees; keep these checks separate from the small full-record exercise below.

A local October 2026 exercise checked all 8,256 positive size pairs through 128 records against independent full-prefix roots, with altered anchors, truncated/excess/changed paths, equal-size pairs, a rewritten prefix and a legitimate new tail. UI tests checked separate anchor entry and stale/cancelled results. These results cover the bounded synthetic implementation, not a deployed log, signed head, publisher identity or global split-view detection.

