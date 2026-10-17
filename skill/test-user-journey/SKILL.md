---
name: test-user-journey
description: Perform bounded functional QA of a real website or application by checking whether a user can complete requested tasks and obtain the right result. Use before or beyond a known defect, rather than for a security assessment, accessibility certification, or source-only review.
---

# Test a User Journey

Check the product that the user will actually use. Start with a meaningful task and an independently defined success condition, perform it through the available interface, and inspect the result. A source review, mocked interaction, or passing helper test supports a different claim from an executed user journey.

## Define the tested surface and boundary

Identify the application, environment or build, entry point, relevant account or role, and requested devices or viewports. Verify the actual available browser or application controls. Honor the user's chosen environment and preserve existing work and sessions.

Establish which actions and test data are in scope. Prefer suitable disposable data and a known starting state. Do not infer that a system is harmless merely because its name contains “test” or “staging.” Submissions, messages, purchases, permission changes, and deletion can still have real effects. Stop before a consequential action not covered by the request, while continuing independent permitted checks.

Record the tested version or observable build identity when available. If the application changes during the pass, reassess affected results rather than combining checks from different versions into a single clean verdict.

## Choose journeys that answer the user's question

Turn the request into observable outcomes. Examples include finding the correct event details and reaching its registration page, selecting records and receiving a matching export, or editing an item and seeing the saved value after reopening it.

Define the expected result from the requirement, supplied content, or accepted contract. Do not derive it solely from whatever the implementation happens to display. If the intended behavior is unclear, ask the smallest consequential question and test settled parts in the meantime.

Select representative journeys by importance and likely failure points. Include an ordinary successful path and the relevant interruption, empty result, invalid input, cancellation, or repeated action. Do not mechanically click every control or add unrelated edge cases.

Identify the start and reset points. Keep setup, product behavior, and cleanup distinguishable so a failure can be reproduced without relying on hidden prior actions. Use the same role and data scope when comparing before and after a fix.

## Execute and inspect the actual result

Use the supported interface or functional automation available for the task. Observe the current state before acting, then check what changed. Wait for a relevant completion signal rather than assuming a fixed delay proves that work finished.

Check both the visible path and the deliverable it promises:

- A confirmation message should correspond to the intended saved item or completed action
- An exported file should open and contain the requested records, fields, and formatting where those are part of the contract
- A filter or reset should update the actual result, not only the control's selected state
- Cancel, Back, Close, or a repeated action should leave the state expected by the product contract
- An empty or error state should remain distinguishable from loading or a successful result

Read the actual content and result, including important labels, dates, prices, units, links, and qualifications supplied for the test. A visually attractive screen can still lead the user to the wrong destination or describe the wrong behavior.

For layout, inspect the requested sizes through supported controls. Record the widths or devices actually used. A narrow desktop viewport can establish responsive layout at that width; it does not automatically establish touch behavior or compatibility with a physical phone. Check important controls, overflow, long content, and the path back from an error or overlay.

For keyboard or other accessibility-related observations, state exactly what was exercised. A small functional pass cannot establish conformance or assistive-technology coverage that was not tested.

Respect unavailable capabilities and denied routes. Do not change security settings, bypass browser warnings, or recreate a blocked operation through another route merely to obtain a result. Continue useful permitted checks and label the specific untested journey; do not count source inspection as a UI pass.

### Check the result after the user changes direction

For an asynchronous journey, choose a relevant superseding action: change the selection, start a newer search, edit an input, dismiss an overlay, or navigate away. Record which input or record now owns the visible result and any dependent action such as Download. Where the authorized interface or existing test controls permit it, observe the older operation completing after that transition. Check late success, failure and loading-state cleanup where relevant; a stale error or spinner can break the current journey even when the displayed data remains correct.

After Close or Back, inspect the destination and whether an old result reopens the dismissed view or steals focus. Follow the product's contract for retained drafts; dismissal need not erase every draft. Keep UI dismissal separate from cancellation of an external action. For an uncertain save or submission, inspect its identified record through an authorized read before repeating it; a closed dialog or canceled browser request is not evidence that the effect was undone.

Capture the action order and completion evidence. If the available controls cannot establish that the older result completed last, report that race order as untested rather than counting fast repeated clicks as proof. A controlled mock can support a separately labeled check; it does not replace the real-interface result. Use [reconcile-obsolete-ui-requests](../reconcile-obsolete-ui-requests/SKILL.md) for an authorized implementation investigation.

**Fictional, unexecuted illustration:** In an event finder, search A requests Harbor events and search B requests Orchard events. The intended check would let B finish before A, then verify that the Orchard selection, event IDs and downloaded result still agree. An old A failure must not replace B's success. If the completion order cannot be observed, the ordinary search can pass while this race case remains untested. No browser journey is claimed here.

## Investigate a failure proportionally

Separate a reproducible product defect from a setup, access, environment, or unclear-requirement problem. Capture the smallest sequence that demonstrates the observed difference from the expected behavior. Include the relevant starting state, input, version, expected outcome, and actual outcome.

Use screenshots, console output, logs, or exported artifacts when they help explain the issue and are within the authorized data scope. Keep sensitive or unrelated information out of the shared evidence. Do not infer a root cause from one error message or claim an action reached a backend when only the interface was observed.

Recheck a suspected defect enough to establish its conditions without repeating consequential side effects. Inspect an uncertain outcome before retrying. If the user requested fixes, make or delegate a scoped correction and repeat the affected journey against the actual final result. Otherwise return the finding without silently changing the application.

## Deliver a useful QA result

Lead with whether the requested tasks worked and the most consequential issue. Report tested journeys and their observed outcomes, actionable defects with locations and reproduction steps, and specific blocked or unrun coverage. Distinguish passed, failed, and untested; an unavailable environment is not itself a product failure.

Keep the report proportional. A small site may need a short result and a few screenshots; a multistep application may need a compact journey matrix. Do not manufacture a quality score or claim the whole application is verified from a narrow pass.

Clean up only the temporary data and sessions the test owns, using the authorized recovery path. Preserve user work and report any remaining test state that matters. Finish with evidence tied to the tested build and concrete next steps for unresolved issues, not a blanket assurance that everything works.
