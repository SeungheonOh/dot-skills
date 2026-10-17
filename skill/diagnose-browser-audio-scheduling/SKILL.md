---
name: diagnose-browser-audio-scheduling
description: "Inspect browser audio timing and lifecycle behavior, identify duplicated or late scheduling, and verify start/stop recovery without changing the composition."
---

# Diagnose browser audio scheduling

## When to use

An authorized browser-audio implementation stutters, drifts, restarts after Stop, or fails during rapid interaction.

## Required inputs

- The relevant scheduling/playback code and a bounded reproduction
- Tempo/event semantics and expected start, stop and edit behavior
- Allowed test runtime and whether audible playback is authorized

## Workflow

1. Trace event generation separately from sound scheduling and visual animation. Establish the expected absolute event times; do not infer them from frame rate.
2. Inspect whether sound uses AudioContext.currentTime and a bounded lookahead horizon. Identify timer-relative accumulation, duplicate loops and bursts of overdue notes after a stall.
3. Check ownership of active sources, timers and pending resume promises. Stop must cancel scheduled voices and invalidate older asynchronous starts. A late failure from an older start must not cancel a newer session.
4. Reproduce rapid Play/Stop, parameter changes, hidden-tab transitions and failed resume. Make authorized fixes at the owning lifecycle boundary rather than increasing gain or hiding errors.
5. Run timing/lifecycle tests separately from a comfortable-level listening check. Explain device latency and browser behavior that a mock cannot establish.

### Capture the smallest lifecycle trace

Record actions and promise resolutions with session/generation identifiers, audio-clock times and source ownership. Do not rely solely on console logs that say “playing.” Check which sources were actually scheduled and cancelled. Keep the reproduction synthetic when possible; microphone capture and private recordings are not necessary for a start/stop race.

If a code change is authorized, first freeze the failing sequence as a test. Ensure cleanup belongs to the session being cleaned up. A global error handler that stops whichever session is current can reproduce the same race in another form.

### Distinguish a stalled scheduler from a suspended audio clock

For a timing failure, pair each relevant callback with `performance.now()` in milliseconds, `AudioContext.currentTime` in seconds, context identity/state, visibility and the event's intended audio time. Compare elapsed values within each clock; do not subtract their absolute readings or carry an origin across a replaced context. Record scheduling-call time separately from intended onset. These are scheduling observations, not measurements of when sound reached the listener.

An explicitly suspended context pauses progression of its audio clock; a delayed JavaScript callback while that clock advances is a different condition. Do not infer suspension merely from a hidden tab or a quiet speaker. Preserve the state transitions and both clock samples before changing timing parameters. The [Web Audio specification](https://www.w3.org/TR/2021/REC-webaudio-20210617/#dom-audiocontext-suspend) defines suspension; its [scheduled-source start rules](https://www.w3.org/TR/2021/REC-webaudio-20210617/#dom-audioscheduledsourcenode-start) also explain why submitting already-past start times can play overdue events immediately.

Recover according to the existing playback contract: skip missed events while preserving phase, pause musical position, or restart from a defined origin only when that behavior is intended. If the contract is silent, make that decision explicit before an authorized fix. Account separately for events already handed to the audio graph and those still queued in JavaScript, so recovery cannot reschedule the same event twice. Stop still invalidates stale work. Check the chosen policy with the same delayed-callback sequence; larger lookahead alone does not establish recovery correctness.

**Fictional, unexecuted illustration:** one context advances from audio time 4.0 to 5.2 seconds while callback samples advance from 1000 to 2200 milliseconds. Events due at 4.5 and 5.0 were not scheduled before the gap. Under a supplied skip-missed contract, both are recorded as missed and the next event keeps its original phase; submitting both past starts is not a faithful recovery. A separate explicitly suspended case requires different expectations. No browser, audible playback or timing test was run for this illustration.

## Output

A short diagnosis with the reproducible sequence, responsible code path, authorized fix if requested, passed checks and remaining audible/device limits.

## Verification and limits

Check that only one scheduler owns playback, Stop silences already-scheduled sources, and stale promises cannot restart or stop a newer session.

## References

[MDN Web Audio sequencing](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API/Advanced_techniques)

## Handoff checklist

Name the action sequence, expected ownership, observed divergence and exact test result. If audible playback is unavailable, deliver the diagnosis and lifecycle evidence without claiming to have listened.

## Worked example

The supplied trace is: Play starts session A; AudioContext.resume remains pending; Stop invalidates A; Play starts session B and schedules its first notes; then A’s resume promise rejects. The observed bug is that A’s catch handler calls a global Stop and silences B.

The diagnosis is stale-session cleanup, not an incorrect tempo. The proposed authorized fix checks A’s generation before changing current playback and cleans up only A-owned sources. The regression reproduces this exact resolution order and requires B to remain active. A separate test resolves A successfully after Stop and requires no restarted sources.

Mocked promise/source tests establish lifecycle behavior for this sequence. The report still leaves real-device latency and audible quality unverified until those checks are performed.

## Evidence status

The worked example illustrates the stated inputs and reasoning. Unless an execution result is explicitly identified, it is not a claim that external services, real devices or user data were tested. Report actual checks and unrun stages on each use.

## Executed synthetic checks

A bounded two-tone scheduler was exercised with mocked AudioContext methods on Node 24.19. One test held resume pending, called Stop, then resolved resume; no oscillator was created. Another let a newer session schedule its tones, then rejected the older resume; the current status and newer sources remained unchanged. Stop disconnected all owned sources.

A clock check placed two tones 0.85 seconds apart using the same audio-clock origin and verified oscillator frequencies of 440 Hz and 880 Hz. Simulated-interface checks required an explicit Play before answering, counted only the first answer, and preserved usable practice when browser storage failed. No microphone, real device, audible output or real-browser layout was verified by these tests.

For short bounded phrases, scheduling the complete phrase against one audio-clock origin can be appropriate; a repeating or unbounded sequencer needs a bounded lookahead strategy. Do not add a timer loop merely to satisfy the form of the workflow.
