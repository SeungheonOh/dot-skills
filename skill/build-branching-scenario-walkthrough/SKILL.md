---
name: build-branching-scenario-walkthrough
description: "Build a bounded interactive rehearsal in which a learner chooses actions, observes authored consequences and revisits a decision to compare paths. Use for scenario-based learning and decision explanation, not a scored quiz, a predictive simulator, professional eligibility assessment or live operational workflow."
---

# Build a branching scenario walkthrough

Deliver a playable learning scenario with concrete choices, coherent consequences and a useful debrief. Let the learner revisit a decision and inspect what changes along an alternative path. The artifact should make a tradeoff or decision process understandable, without pretending that its authored outcomes predict what will happen in real life.

Use this when the learning depends on a sequence of decisions and their context. [Learning materials](../create-learning-materials/SKILL.md) handles a broader lesson; [deliberate practice](../deliberate-practice-workbook/SKILL.md) handles repeated scored exercises; [finite workflow verification](../find-finite-workflow-counterexamples/SKILL.md) investigates model properties. This workflow creates a bounded rehearsal, not any of those results by implication.

## Define what the rehearsal can teach

Establish from the request and supplied sources:

- The learner's role, starting situation and observable decision skill
- What the learner knows initially, what new information a choice reveals and what remains uncertain
- Governing facts or approved policies, with source/version, versus fictional scenario assumptions
- Consequences worth comparing, meaningful endings and the intended session length or scope
- Whether the scenario is for self-study, facilitation or a private prototype; requested host/format, storage and audience

Choose a small situation that reveals the intended tradeoff. Use a few consequential branches rather than a large tree of cosmetic choices. If the task is merely “which answer is correct?”, a straightforward question and explanation may suffice; do not disguise a quiz as a narrative.

Use original fictional or authorized sanitized content. Do not copy identifiable disputes, learner evaluations, personnel cases or sensitive records into a shareable scenario by default. Keep factual instruction tied to evidence and display fictional status prominently. A policy unknown must stay unknown; an attractive ending cannot establish the organization's rule.

Keep rehearsal controls separate from real actions. A simulated “send update,” “approve” or “cancel” changes only the scenario state and must be labeled accordingly. Do not wire those choices to messaging, accounts, payments, equipment or other services. Creating the artifact does not authorize publication, enrollment, analytics or sharing learners' choices. Do not use it to make high-impact eligibility decisions about people or infer personality, competence or health from their paths.

## Author the decision graph and state contract

Create an editable graph/content representation with stable node and choice IDs. Each decision node needs:

| Element | Required meaning |
| --- | --- |
| Situation and available evidence | What the learner can reasonably know before deciding |
| Choices | Concrete actions, including a plausible alternative where the tradeoff needs one |
| Conditions | Any prerequisites for displaying/enabling a choice |
| State effects | Explicit changes to named scenario facts or resources |
| Destination | The next node or a named terminal state |
| Feedback | Why the choice changes the situation; distinguish rule from fictional consequence |

Define the initial state and the finite domains or bounds that matter. Track only variables that change a future choice, explanation or ending. Separate scenario state from presentation state such as open hints or selected panels. Avoid a hidden universal “goodness” score; name the actual considerations, such as clarity, elapsed fictional time or unresolved work.

Make choices fair with the information available at that point. A consequence can reveal a new fact, but do not fault the learner for failing to know it. Represent uncertainty honestly: an authored branch is a possible outcome under stated assumptions, not a measured probability. Use random outcomes only if the learning objective genuinely requires them and their assumptions and replay behavior are explicit.

Specify how conditions and effects compose. Evaluate eligibility on the pre-choice state, then apply the declared update once and select the next node. Reject unknown variables, duplicate IDs, missing destinations and contradictory branch conditions. Do not evaluate arbitrary expressions imported from scenario files; use bounded supported conditions or trusted authoring facilities.

## Preserve consequences across branches and revisits

When two paths reconverge, do not erase their earlier effects unless the narrative explicitly resolves them. The same node ID reached with different scenario states may need different text or choices. Check the reachable node-and-state combinations that affect the lesson; counting visited node IDs alone can miss an inconsistent path.

Prefer an acyclic graph for a short rehearsal unless repetition is part of the lesson. For a loop, define what changes, how the learner can leave and any visit limit. A loop limit should produce an honest stopping message, not imply that the learner failed. Every reachable nonterminal state should have a meaningful continuation or a clearly explained unresolved state.

Keep a path history with choices and state snapshots or reproducible updates. Define Back as restoring an earlier scenario position, not merely displaying its old text over the latest state. Taking a new choice from there should replace the old future path for the active attempt. Do not silently combine consequences from mutually exclusive branches.

If comparing alternatives, preserve the common ancestor state and branch from that exact point. Label the two paths and their stated assumptions. Compare relevant consequences and remaining uncertainty rather than declaring a universal winner. Do not persist the learner's attempt across sessions unless requested; if persistence is requested, disclose where it lives and provide a clear reset/export behavior appropriate to that storage.

## Build the reader-facing artifact

Use an available authorized authoring surface that supports the required navigation. Follow an existing project or host's conventions. A bounded local HTML artifact can work without accounts or a server; a linear linked document may be the supported fallback. Do not assume a particular game engine, LMS, hosting service or framework is available.

Show one situation at a time with its evidence and clearly named choices. Present the consequence after selection, then the next decision or ending. Keep the chosen path inspectable. Distinguish “Review this earlier choice” from “Start again,” and make it clear when a new choice will replace the active future path. Prevent repeated activation from applying a resource decrement or other effect twice.

Offer optional hints or evidence detail where useful. Do not make hints count as failure or silently change an assessment. Keep hints attached to the current scenario version. For simple show/hide content, WAI's [disclosure pattern](https://www.w3.org/WAI/ARIA/apg/patterns/disclosure/) describes the button and expanded-state relationship; native controls are preferable to a custom widget without keyboard behavior.

At an ending, provide a compact debrief:

- Which choices were made and which facts were available at those points
- Which consequences followed from the stated rules and which were authored possibilities
- What tradeoff the path illustrates and what remains unresolved
- A useful earlier decision to revisit, without claiming the learner has mastered the skill

Keep hypothetical clocks and resources clearly labeled. A fictional ten-minute delay is not time spent by the learner. Avoid real countdowns, response-speed scoring and forced motion unless they are specifically part of the requested learning task.

## Include a navigable text alternative

Use native controls, readable focus and a logical reading order. After a scene replacement, move or retain focus predictably so the reader can discover the new situation; do not leave focus in a removed choice. Follow the relevant [WAI keyboard-interface guidance](https://www.w3.org/WAI/ARIA/apg/practices/keyboard-interface/). Color, sound and animation must not be the only carriers of a consequence.

Provide a text version with a starting section, numbered/named decision sections, choice destinations and endings. Include initial values and per-choice updates needed to track scenario state manually, as well as state-dependent text and choice conditions. A flat list of all prose without branch links and relevant state updates is not an equivalent walkthrough. Keep the text representation derived from the same graph/content to reduce drift, and make it available without requiring scripting.

## Acceptance criteria and recovery

Review content and graph separately from actual interaction. Exercise the delivered artifact when the environment and authorization permit:

1. Each choice has a supported destination; all intended endings are reachable, and unfinished branches are labeled
2. Ordinary and consequential alternative paths produce the intended state, including a reconvergence or loop if present
3. Back, changed choice and Reset restore the correct state; abandoned future effects do not survive and repeated activation does not duplicate effects
4. Facts revealed later are not presented as prior knowledge, and debrief claims agree with the chosen path and source/version
5. Keyboard navigation, narrow layouts, hints and text fallback preserve the same choices and explanations
6. The artifact makes no unapproved network submissions, telemetry or durable recording; any approved storage behaves as described

For a small finite graph, inspect all meaningful reachable state combinations. For a larger one, state the reviewed coverage and unresolved combinations instead of claiming exhaustive verification. A successful author walkthrough proves only those paths and interactions, not learner improvement or real-world validity.

If a path reaches no enabled choice, show a content-error or unresolved-state message and retain the history; do not invent a success ending. Fix the source graph and recheck affected incoming paths. If a changed choice leaks old consequences, repair restoration/history semantics rather than patching the debrief wording. If policies conflict, hold the dependent content and preserve the source conflict. If rendering or execution is unavailable, deliver the graph and linked text version with the interactive checks marked unrun. Respect denied actions instead of changing tools to bypass them.

Return the playable artifact, editable scenario content, text alternative and concise notes on assumptions, source versions, storage and actual checks. Stop at the agreed rehearsal and verification boundary. Running a class, assessing participants, collecting results or taking a rehearsed action in the real world needs its own scope.

## Fictional example, not executed

A fictional team must prepare an internal demo. A sample chart has no unit label. The learner can “Ask the owner for the unit” or “Keep the chart with a visible caveat.” The authored scenario assumes that asking supplies the unit after five fictional minutes; keeping the caveat preserves that time but leaves the chart unresolved. Neither outcome is claimed to predict a real colleague's response.

Both branches next reach “Prepare the handoff.” The asking branch carries unit_known=true and time_used=5; the caveat branch carries unit_known=false and time_used=0. The handoff text must respect that distinction. Returning to the first decision and choosing the other branch must restore the original state before applying its effects. The debrief compares remaining uncertainty and fictional time, rather than awarding a personality or competence score.

This is an authored example of a graph and planned checks. No interactive artifact, learner session, state transition implementation or learning outcome has been executed or observed by this example.
