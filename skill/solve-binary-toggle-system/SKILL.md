---
name: solve-binary-toggle-system
description: "Solve a supplied finite on/off toggle problem over GF(2), verify the returned presses, and distinguish any solution from a proven minimum."
---

# Solve a binary toggle system

## When to use

A task requires a valid toggle sequence or a reproducible solvable test instance, not a new game interface.

## Required inputs

- Current binary state, target state and exact press influence rule
- Board or graph dimensions and stable element ordering
- Whether minimum press count is required and a practical search bound

## Confirm the fixed-toggle model

Before building a matrix, establish that each allowed press applies one fixed XOR mask to the state, independent of the current lamp values and earlier presses. Under this model a press changes `s` to `s XOR mask`; masks compose by XOR, presses commute, and pressing twice cancels. The [linear-algebra setup in Lights Out on graphs](https://arxiv.org/abs/1903.06942) derives these properties from fixed influence columns. They are premises to check against the supplied rule, not properties implied merely by having binary lamps.

Inspect the rule, not just its effect on the starting board. A changing neighborhood, one-shot switch, conditional availability or required press order needs the corresponding state or constraints. A permanently forbidden press can be excluded from the allowed columns, but other restrictions must not disappear into an unconstrained matrix. A matrix solution may violate those restrictions. If restrictions only remove permitted sequences while the fixed masks remain correct, matrix inconsistency still rules out the target; if the actual press effects differ from the columns, that conclusion does not transfer. Use a suitable bounded state search or report the unsupported part. Double-press and commutativity examples can expose a mismatch, but a few passing examples do not establish fixed masks for every state.

Fictional, unexecuted illustration: one button flips the first lamp if that lamp is off; otherwise it flips the second lamp. Starting at `[0,0]`, two presses give `[1,0]` and then `[1,1]`. A column inferred only from the first press would be `[1,0]` and would incorrectly declare `[1,1]` unreachable from `[0,0]`. The effect is state-dependent, so repeated presses cannot be reduced to parity here. This is a hand-derived counterexample, not an executed solver test.

## Workflow

1. Construct one influence matrix whose columns represent presses. Set the right-hand side to current XOR target. Check boundary neighborhoods against the supplied rule.
2. Gaussian-eliminate the augmented system using XOR. An all-zero coefficient row with right-hand side one proves inconsistency under this model.
3. Extract a particular solution and free-variable basis. Enumerate the free-variable family only within the agreed bound when minimizing Hamming weight; otherwise report a valid solution with minimality unverified.
4. Apply the returned presses through the original influence rule and compare the complete final state with the target. Repeated presses cancel; this does not excuse an incorrect matrix.
5. If generating test instances, start at a known target and apply recorded seeded presses. Keep the seed, ordering and press rule with the instance.

### Bound the minimum-solution claim

Record the element ordering used for both the state vector and influence matrix. If the interface labels cells by coordinates, return presses in those coordinates as well as indices. Rank deficiency does not necessarily mean inconsistency: it may mean several valid solutions. Check the augmented rows before deciding.

For a minimum solution, count free variables before enumeration and state the search bound. If enumeration is stopped, return the best verified solution found with no shortestness claim. A solver’s own matrix multiplication is useful, but an independent application of the original press rule is a stronger check.

## Output

A press sequence, resulting state, consistency verdict and explicit minimum/valid-only status, or a demonstrated inconsistent system.

## Verification and limits

Check double-press cancellation and press commutativity. For small cases, compare with an independent enumeration. JavaScript bitwise operators truncate at 32 bits; use a representation that fits the actual system.

## Stop conditions

Stop minimum enumeration at the declared resource limit. Stop representation use when the matrix exceeds its bit capacity. An unavailable minimum does not prevent returning a verified nonminimal solution.

## Worked example

Two lamps start at [1, 1], with target [0, 0]. Either button flips both lamps. The influence matrix has two identical columns, each [1, 1]. Solving A×x=[1, 1] gives solutions x=[1, 0] and x=[0, 1]. Either single press reaches the target; zero presses does not, so the minimum is 1.

Change only the starting state to [1, 0]. The equations now require the same XOR of the two button choices to equal both 1 and 0. That contradiction proves no solution under the supplied rule.

Return the valid one-press sequence for the first case and an inconsistent-system result for the second. Do not “repair” the second board by changing a lamp or button rule without instruction.

## Evidence status

The worked example illustrates the stated inputs and reasoning. Unless an execution result is explicitly identified, it is not a claim that external services, real devices or user data were tested. Report actual checks and unrun stages on each use.
