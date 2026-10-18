---
name: verify-discrete-conservation
description: "Validate a discrete state-transition model with an explicit input/storage/output ledger, including boundary loss, resumable computation and independent conservation checks."
---

# Verify a Discrete Conservation Ledger

## When to use

Use this when a user or agent is implementing or checking a finite count-based simulation, inventory flow or resource transfer and needs evidence that updates do not silently create or lose units. This is numerical/model verification, not proof that the model represents physical reality or that a real-world financial ledger is correct.

## Required inputs

- State variables, units and initial counts
- Permitted additions, transfers, removals and boundary behavior
- The intended balance equation and any explicitly modeled sources or sinks
- Numeric range, step budget and checkpoint/resume semantics
- A small fixture that can be checked by hand or with a separate implementation

Resolve unit mismatches and undefined sinks before proceeding. A model with deliberate creation, decay or fractional quantities needs those terms represented explicitly; do not force it into an integer conservation claim.

## Workflow

1. **Define the accounting boundary.** State which quantities remain inside the system and which have left it. For a simple dissipative lattice, cumulative added units must equal units on the grid plus cumulative boundary loss. Keep units and sign conventions consistent across counters and displays.
2. **Validate the starting state.** Check dimensions, nonnegative integer counts, supported numeric range and the balance equation. Do not repair a mismatched imported ledger by silently changing a counter. Either reject it with the exact discrepancy or use an explicitly authorized reconciliation rule.
3. **Audit each transition locally.** Calculate the amount removed from the source and added to destinations. Record any out-of-bound portion in an explicit sink counter. Ensure the transition itself balances before relying on a final aggregate check; two compensating bugs can hide in a final total.
4. **Bound arithmetic and work separately.** Keep counts within exactly representable integer limits and enforce a total-volume cap where needed. Separately cap transitions or topplings per computation chunk. Reaching the work limit means unfinished, not stable. Report pending unstable or eligible states explicitly.
5. **Make resume semantics exact.** Persist the resulting state and cumulative ledger together. Resume from that pair without reapplying the original addition or counting already completed losses again. A canceled in-flight computation should leave the last committed complete chunk intact. Reject obsolete worker results after reset, import or a new operation.
6. **Check conservation after every committed chunk.** Recompute the stored total from the actual state, not from a second incrementally maintained total that could share the same bug. Compare it with additions and sinks. If the check fails, preserve evidence and stop rather than continuing from corrupted state.
7. **Cross-check with an independent small oracle.** Use a slow direct implementation that differs from the optimized queue or batching logic. Compare final cells and sink counts on bounded fixtures. Changing update order can be a useful check only when order independence is part of the model; do not assume it for arbitrary dynamics.
8. **Verify export and restore.** Export the exact displayed state and ledger, then validate them after restoration. Separate the physical/model state from UI counters such as “steps this session.” If exporting art or a preview, derive it from the same state and disclose whether the computation was stable or still in progress.

## Preserve the opening balance and counter origin

The zero-start lattice equation above needs an explicit opening term when the chosen accounting interval begins with stored units. Record the starting state and its independently summed quantity `opening`. For counters that begin at that same boundary, check `opening + added_since_start = stored_now + removed_since_start`, including every modeled sink in removals. Internal transfers cancel in this total; they are not external additions. [MIT's stock-and-flow lecture](https://ocw.mit.edu/courses/esd-36-system-project-management-fall-2012/800ceb204ef03177b61e1288533446c1_MITESD_36F12_Lec06.pdf), slides 30 and 35, gives the initial-stock term and the discrete stock-update equation.

Distinguish a checkpoint from a newly declared starting state. If restoring lifetime addition/removal counters, retain their original baseline and validate the full ledger before continuing. For an interval check from that checkpoint, subtract each counter's saved value to obtain only the subsequent additions and removals. Do not add the checkpoint's stored units to lifetime additions again, mix lifetime losses with interval additions, or reset counters to conceal a failed restore check. Store the accounting origin with the state and counters so resume and export use the same convention.

A state-only snapshot can be an explicitly declared new baseline for future transition checks, but it cannot establish conservation before that snapshot. Label the historical ledger unavailable instead of inventing prior additions or losses. Independently check a nonempty start, a checkpoint with nonzero historical losses, and an unchanged resumed state with zero new flows; these expose origin mismatches that an empty-start fixture cannot.

**Fictional, unexecuted illustration:** An empty-start model has lifetime additions 12, stored units 7 and lifetime losses 5 at a checkpoint. Later it adds 3 and loses 2, leaving 8 stored. The lifetime check is `15 = 8 + 7`; the checkpoint-interval check is `7 + 3 = 8 + 2`. Adding the opening 7 to lifetime additions would count those units twice. If only the 7-unit state had been supplied, it could support the second equation for subsequent observed transitions, but not a claim about the earlier 12 additions or 5 losses. No simulation or restore procedure was executed for this illustration.

## Worked example

An open-boundary grid starts empty. Add4 grains to its upper-left corner. A toppling removes4 grains from that cell and sends1 to each orthogonal neighbor.

- The right neighbor receives1
- The lower neighbor receives1
- The two off-grid destinations add2 to the loss counter
- The original corner returns to0

The ledger is added4 = on-grid2 + lost2. Counting only visible neighbors without recording the two outgoing grains would falsely look like a conservation failure; subtracting all4 but adding4 to both existing neighbors would create units.

For a paused run, save the whole lattice and cumulative loss after a completed chunk. Resuming must not add the original4 again. An imported state with on-grid2, lost2 and added5 is invalid under this model and should be rejected, not normalized to make the totals agree.

## Verification cases

Cover an interior transfer, an edge, a corner, an already stable state, multiple eligible cells, a tiny work budget, repeated resume, cancellation and export/restore. Compare independent implementations on small fixtures and verify both location-specific state and aggregate totals. A passing aggregate alone cannot detect units moved to the wrong destination.

## Deliverable and limits

Return the balance equation, transition accounting, input validation rules, exact fixtures and observed checks. Report numerical-range limits, unfinished work and any unsupported restore format. Conservation establishes bookkeeping consistency within the model; it does not validate every rule, prove realism or authorize an external transfer.
