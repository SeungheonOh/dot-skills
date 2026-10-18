---
name: orbital-game-lab
description: "Evaluate a supplied fixed-step trajectory model against conservation, convergence and terminal-event checks; return measured errors and model limits."
---

# Check a numerical trajectory for drift

## When to use

A simulation produces plausible-looking paths, but the user needs evidence that its numerical integration is behaving consistently.

## Required inputs

- The equations, units, initial conditions and integrator implementation or recorded trajectory
- The supported domain, stop conditions and requested simulation duration
- An error tolerance or permission to report measured error without declaring a pass

## Workflow

1. Freeze the model revision and initial conditions. Separate fictional parameters from measured quantities; do not infer real-world calibration from a visually convincing plot.
2. Identify conservation laws that apply to this model. For an ideal inverse-square two-body model, evaluate specific energy v²/2−mu/r and angular momentum. Do not demand conservation across impulses or terminal collisions.
3. Run identical inputs twice to check determinism. Repeat the same physical interval with step h and h/2, using the same event rules. Compare positions and invariants at aligned physical times rather than array indices.
4. Measure maximum absolute and relative error. Use an explicit scale when the initial invariant is near zero; a division by nearly zero is not a useful relative-drift result.
5. Check impact/escape/time-limit boundaries separately. Report whether events are detected only at sampled endpoints and whether reducing the step changes their classification. Stop before applying a fictional model to real navigation.

### Choose a comparison that can answer the question

Pin the units and integration interval before running any case. If the supplied output has irregular times, compare interpolated samples only when the interpolation method is justified; otherwise rerun at shared checkpoints. Record h, h/2, sample count and terminal time separately. Reducing the step can change an impact classification because a coarse step jumped through a surface. Treat that as event-resolution evidence rather than a conservation-law failure.

Keep a case-level result: expected model property, measured quantity, tolerance, observation and conclusion. If no tolerance was supplied, report measured drift and convergence without inventing a pass criterion. Preserve the original implementation while an authorized candidate fix is compared against it.

### Separate invariant drift from trajectory error

Report invariant drift, agreement between step sizes and error against a reference trajectory as different quantities. The same implementation can repeat a defect at both step sizes, and conserved energy or angular momentum does not establish the correct orbital phase. [Hairer's analysis of symplectic integration](https://www.unige.ch/~hairer/preprints/varsymp.html) distinguishes energy-error behavior from growth of angle error; a good conservation result is not a position-accuracy guarantee.

When trajectory accuracy is the requested claim, use an analytic solution for the same equations and initial conditions where available, or an independently justified numerical reference. Compare position and, when relevant, velocity at fixed physical times, including an intermediate checkpoint rather than only a whole-period endpoint. Name the norm, units and reference basis. Do not rotate a trajectory or match nearest points along its curve to erase a timing error. For a numerical reference, retain its method, settings and accuracy limits; disagreement is not an exact error estimate unless the reference uncertainty supports that claim. If only invariant or step-agreement evidence is available, return those findings with trajectory accuracy unresolved.

**Fictional, unexecuted illustration:** In the unit circular model below, the analytic position is `(cos t, sin t)` and velocity is `(-sin t, cos t)`. A faulty recorder that repeats the initial position `(1, 0)` and velocity `(0, 1)` at every timestamp would show zero energy and angular-momentum drift, identical repeated runs and identical coarse/fine states. It would even match the true position after one full period. At `t = π/2`, however, the true position is `(0, 1)`, so its Euclidean position error is `√2` distance units. This is an algebraic counterexample, not an executed trajectory test.

## Output

A table of cases, step sizes, duration, error measures, terminal outcome and tolerance result, plus reproducible initial conditions and untested model assumptions.

## Verification and limits

Confirm unit consistency, aligned sample times and unchanged initial conditions. A smaller error at one step size is evidence for that case, not proof of stability for every trajectory.

## Failure triage

If drift spikes at an impulse, first verify whether conservation was expected across it. If h/2 worsens error, inspect final-time alignment, force singularities and event handling before concluding the integrator is unstable. Keep visualization fixes separate from numerical fixes.

## Worked example

This is a synthetic unit-system example, not a spacecraft calculation. The supplied model has mu=1, initial position (1, 0), velocity (0, 1), no impulses and no collision surface inside the orbit. The user asks whether a fixed-step integrator preserves an ideal circular trajectory for one period.

The initial specific energy is 1/2−1 = −0.5 and angular momentum is 1. The analytic period is 2π. A suitable check runs to that same physical time at two step sizes, handling the final fractional step consistently, then compares radius, energy and final position against the analytic circle.

A local Python velocity-Verlet calculation was executed for this synthetic case: update position with the old acceleration, calculate the new acceleration, then update velocity with their mean. The final step was shortened to end exactly at 2π. With h=0.02, maximum relative energy drift was approximately 3.998×10⁻⁸ and final-position error 8.378×10⁻⁴ distance units. With h=0.01, the corresponding values were 2.500×10⁻⁹ and 2.095×10⁻⁴. The smaller-step final-position error is about one quarter of the larger-step error for this case.

These observations support convergence for the supplied synthetic circle, without establishing a global tolerance or real navigation accuracy. If only one saved trajectory is available on a later task, report its invariant drift and mark step-size convergence untested.

## Evidence status

The worked example illustrates the stated inputs and reasoning. Unless an execution result is explicitly identified, it is not a claim that external services, real devices or user data were tested. Report actual checks and unrun stages on each use.
