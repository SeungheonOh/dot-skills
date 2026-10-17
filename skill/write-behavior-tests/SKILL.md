---
name: write-behavior-tests
description: Create or improve automated tests for a specific behavior contract using the project's existing test approach. Use when the user needs meaningful coverage of observable results and failure paths, rather than diagnosis of a failing run or a coverage-number increase alone.
---

# Write Behavior Tests

Deliver tests that distinguish the required behavior from plausible mistakes. Test the contract at the right boundary, run the actual tests, and explain what they protect. A larger test count or a green run is not enough if the assertions would also accept the wrong result.

## Establish what should be true

Read the requirement, relevant interface or specification, current implementation, and existing tests. Identify the input or starting state, the operation, the observable result, and the important conditions under which that result changes.

Do not treat current behavior as automatically correct. A requirement may intentionally change an old default, and an existing bug should not become the expected answer merely because the implementation returns it. If sources conflict on a consequential case, show the concrete difference and resolve that contract before encoding an assertion. Continue writing tests for settled behavior.

Determine the requested scope: new tests, stronger assertions, a regression test, or tests accompanying an authorized implementation. Test creation alone does not require changing product behavior. If a well-grounded test exposes a defect, preserve the useful failing case and report it; implement a fix when the request also covers that work.

## Choose the boundary that proves the behavior

Use the project's existing framework, fixtures, and conventions where suitable. Find the entry point or consumer whose behavior matters. A unit test may be enough for a pure calculation; a changed serializer, command, or persisted default may need a check through its real consumer.

Separate concerns without replacing the whole system with mocks. Mock a boundary when it makes an external dependency controllable, but keep enough real code to exercise the contract under test. A mock returning the expected answer does not prove the product can produce it. State what an isolated test leaves to integration or application-level checks.

Select cases that cover different decisions or likely mistakes:

- An ordinary valid input with a concrete expected result
- A meaningful boundary or alternative branch
- A relevant failure or incomplete result, including the resulting state
- A compatibility case when existing callers or saved data must continue to work

These are prompts for judgment, not a mandatory checklist for every function. Use parameterized cases when they clarify a shared rule; use distinct tests when setup or expected behavior differs substantially.

## Build reliable inputs and assertions

Use original or approved test data with only the detail needed to express the case. Preserve the distinctions the contract depends on, such as order, duplicate occurrences, types, omitted versus explicit values, or empty versus unknown results.

Compute expected values independently of the implementation being tested. Calling the same helper to build both the expected and actual result can reproduce the same defect twice. For generated or property-based inputs, state the invariant and any valid-input assumptions; random generation is useful only when failures can be reproduced and the oracle is meaningful.

Assert the output that matters, including consequential side effects or their absence. Checking only that a function returns, a file exists, or a status is successful may miss the wrong content. Conversely, avoid asserting incidental formatting, private call order, or internal helper names unless they are part of the actual contract.

Make time, randomness, environment, and external dependencies controllable where they affect the test. Use an explicit clock or synchronization condition rather than a sleep that merely makes failure less likely. Keep temporary resources isolated, restore changed state, and clean up only resources the test owns. Do not make tests depend on personal accounts, private files, or live services unless that integration is explicitly within the requested environment and authority.

For errors, assert the relevant type, status, or documented message and verify the remaining state. Do not catch every exception and call the test successful. A timeout, skipped test, or failed setup is not a passing assertion.

### Make asynchronous completion part of the assertion

When the operation or assertion is asynchronous, bind its completion to the runner's supported test lifetime. Await or return the full assertion chain, or use the framework's callback-completion mechanism and propagate its errors. Starting work, registering a callback, or awaiting only setup does not show that the behavioral assertion ran. In Jest, [promise assertions must be returned or awaited](https://jestjs.io/docs/asynchronous); use the project's equivalent mechanism rather than mixing incompatible completion styles.

Make the wrong outcome fail explicitly. An expected-rejection case that asserts only inside a catch branch may pass if no rejection occurs. Use a rejection assertion that rejects success, or a supported assertion-count/explicit-failure guard as appropriate. For callbacks, ensure the expected callback and assertion occurred before completion. Do not replace behavioral checks with an assertion count alone.

Keep setup and cleanup in that same ownership model. Wait for asynchronous fixture setup before the action and for owned cleanup before declaring the case finished; Jest's [setup and teardown hooks](https://jestjs.io/docs/setup-teardown) support asynchronous completion. After a timeout or canceled case, do not assume spawned work has stopped. Use the fixture's supported stop-and-join path where available, retain cleanup errors, and report unresolved background activity instead of reusing a possibly contaminated fixture. Restore replaced clocks or mocks only after work that relies on them has settled.

For a negative side-effect claim, observe the state at a defined completion barrier. An empty write log immediately after starting an operation cannot prove it will never write later. If an authorized isolated wrong variant is used to check detection, make it return the opposite completion outcome or perform the forbidden effect, and confirm the runner reports failure before removing that variant.

**Fictional, unexecuted illustration:** A test for a rejected save starts the request and checks the error only in a rejection callback, without returning its promise. The intended repair would make the runner await a rejection assertion, verify the stored record after the operation and its owned background work settle, and await fixture cleanup. A deliberately fulfilled response must fail the rejection expectation; a late write must fail the state check. No save or test run is claimed here.

## Check that the tests can detect a mistake

Run the focused tests using the actual project command and prerequisites. Inspect the result rather than assuming discovery included the new file. Confirm the intended cases executed and that assertions reached the real behavior.

Where useful, demonstrate that a new regression test fails before the corresponding fix, or check a small deliberately wrong variant in an isolated copy. Choose a benign, relevant mistake, such as dropping a duplicate, reversing a comparison, or changing a default. Do not mutate the user's working implementation merely to manufacture a failure, and do not require a mutation exercise for every trivial test.

If a test fails, distinguish an implementation defect, incorrect expectation, unsuitable fixture, and environment problem. Fix the part the evidence supports. Do not weaken the assertion or skip the case solely to make the suite green.

Run nearby or required project checks when the new tests affect shared fixtures, setup, or discovery. After later edits, rerun the affected cases. Avoid repeated full-suite runs when no relevant files or unresolved concern changed.

## Deliver the useful coverage

Leave the tests in the requested project location and preserve unrelated changes. Explain which behavior the tests now protect, what actually ran, and any defect or unavailable integration check still open. A failing regression test can be the correct deliverable when the task was to expose a known problem; label its expected failure clearly rather than claiming the suite passes.

Keep coverage claims tied to the tested boundary. Do not infer production reliability, complete compatibility, or the absence of all bugs from a local suite. Follow the established scope for commits, remote runs, and publication; test authoring does not itself authorize changing shared services or disabling existing checks.
