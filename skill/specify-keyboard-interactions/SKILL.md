---
name: specify-keyboard-interactions
description: "Prepare a component-level keyboard and focus contract for an established web interface, reconciling key ownership, composite navigation, activation and recovery destinations. Use for an implementation handoff or interaction reference, not screen design, code changes or executing keyboard QA."
---

# Specify keyboard behavior at component boundaries

Produce a keyboard interaction specification that lets an implementer and reviewer determine what each relevant key does, which component owns it, and where focus and selection end up. The deliverable is an editable component/key matrix and focus-transition map with concrete acceptance cases. A shortcut list alone does not establish ordinary keyboard access or explain nested interactions.

Use [design-user-interface](../design-user-interface/SKILL.md) when the task flow or controls still need designing, [keyboard-form-completion-check](../keyboard-form-completion-check/SKILL.md) for an actual bounded form journey, and [implement-scoped-change](../implement-scoped-change/SKILL.md) for implementation. This workflow fills a detailed interaction handoff for an established design; it does not introduce a mandatory specification phase for every small control.

## Inputs, evidence and scope

Identify the selected components and revision, their existing design-system patterns, visible controls and accepted state rules, target web platforms, and requested document destination. Include component instances that nest or share shortcuts. A screenshot can establish visible layout but cannot establish keyboard handlers, DOM order, hidden controls or actual focus behavior.

Distinguish accepted behavior, source-derived behavior, an observed result supplied with its environment, and a new proposal. For an as-built reference, unresolved behavior stays unknown; do not fill gaps with an APG pattern and present them as observed implementation. For a proposed handoff, use the selected pattern to resolve ordinary reversible details and mark material departures or product decisions explicitly.

Read supplied code only as passive text when needed. Do not run handlers, install a library, change OS/browser keyboard settings, operate the application or submit a live action under a documentation request. Keep screenshots and source excerpts within the approved audience, remove unnecessary personal data, and use fictional values in scenarios. Preserve the prior contract and original design files; writing this document does not authorize publishing it or changing the product.

## 1. Inventory actions and interaction owners

Give each selected component a stable ID, purpose, source locator and semantic pattern. List the actions people must reach, including pointer-only controls that need a proposed keyboard route. Distinguish an action from navigation to an action: focusing Delete must not delete anything.

Choose native controls where they express the accepted behavior. A visual row of links is not automatically a tablist, and ordinary navigation is not automatically an application menu. The [APG introduction](https://www.w3.org/WAI/ARIA/apg/practices/read-me-first/) explains why assigning an ARIA role creates behavioral expectations; semantic labels do not supply the keyboard implementation.

Record the component boundary and its children before assigning keys. A page, dialog, tablist and editable field can all contain the same key event, but they must not all perform unrelated actions. For each handled key identify its owner, applicable state, descendant exclusions and whether the browser's normal action remains available. Do not prescribe document-wide interception just because it is easy to describe.

Separate ordinary access from optional shortcuts. Every required task needs a discoverable route through the supported controls. A proposed shortcut is an additional path with its own scope, label and conflict review, not a replacement for reaching the action normally.

## 2. Write the key and focus contract

Use rows containing only the fields the component needs:

- Component/state and starting focus or active item
- Key or input action, including relevant modifiers and orientation
- Preconditions and the component that handles it
- Resulting focus/active item, selection, expanded state or value
- Activation effect, if any, separately from movement
- Boundary behavior, event ownership and reference/proposal status

For a composite widget, specify entry from both directions, navigation within it, exit, and re-entry after leaving. [WAI keyboard-interface guidance](https://www.w3.org/WAI/ARIA/apg/practices/keyboard-interface/) distinguishes the page tab sequence from internal composite navigation, and DOM focus from selection. Record the chosen focus strategy: actual focus moving among children or a supported active-descendant relationship. Do not combine their names as if they were interchangeable behavior. Where active descendants are used, hand off the required role/relationship, valid item identity and scroll/visual-focus obligations for the implementer to verify.

Define the first/last boundary, whether navigation wraps, disabled-item treatment, and empty or single-item behavior from the selected pattern. Optional pattern keys should be explicitly included or omitted. Do not generalize one widget's arrow-key, Space or Escape behavior to every control. Preserve text editing, caret movement and composition inside inputs; an outer component must not steal those keys merely because they appear in its navigation matrix.

Record focus and selection separately in all selection widgets. Decide whether movement changes selection, whether selection activates content, and whether that work can wait. The [APG tabs pattern](https://www.w3.org/WAI/ARIA/apg/patterns/tabs/) distinguishes manual and automatic activation and recommends avoiding automatic activation when loading delays impede navigation. For manual tabs, arrow movement and panel activation therefore require separate rows. Include panel entry/exit rather than stopping the specification at the tab labels.

For toggles, disclosure controls and mutually exclusive choices, tie the visible state to the corresponding programmatic state and stable name. Record expected meaning rather than an exact synthesized sentence: assistive technologies may announce equivalent information differently. A control's source label is not proof of its computed accessible name.

For an action where repeated activation matters, define the effect of one complete key gesture and whether holding the key repeats it. Preserve native activation rather than proposing an extra key handler that also triggers the same action. If event phase is material to the selected component, record it explicitly; do not leave an implementer to guess whether keydown, keyup and a synthesized click are three separate operations.

## 3. Resolve focus after transitions

Create a focused transition map for changes that can invalidate the current target. Each entry identifies the initiating component/item, immediate destination, later destination if different, fallback if the intended target disappears, and preserved data/selection. Keep item identity separate from its current row or visual position.

Cover only relevant transitions, such as opening/closing a popup, deleting an item, filtering away the focused result, changing pages, entering an error state or completing asynchronous work. A routine background refresh should not take focus merely to announce completion. A late callback must not pull focus back into a dismissed view; state which current interaction still owns a proposed delayed move. This is a contract requirement, not evidence that race handling is implemented.

For a modal dialog, document initial focus, contained Tab traversal, closing routes and focus restoration. The [APG modal dialog pattern](https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/) permits context-dependent initial focus and a logical alternative when the invoker no longer exists. Specify the actual alternative instead of “return focus somewhere sensible.” Do not label a visual overlay modal unless the proposed interaction also makes background content unavailable. Treat a nonmodal panel separately.

Resolve nested dismissal deliberately. Identify whether Escape closes an inner popup, cancels an edit or closes a dialog in each state; do not let one press silently perform all three. Retain unsaved-work and confirmation rules already supplied. Closing a view is not proof that a server operation was canceled or that changes were undone.

Describe where the focus indicator must remain discernible and which sticky regions or scrolling containers could cover it. Keep visibility requirements tied to the target layout; the written map does not demonstrate that the final CSS satisfies them.

## 4. Specify shortcuts without taking over the user's environment

For each requested shortcut record the action, scope, discoverability, ordinary-control equivalent, editable-content exclusions, and target keyboard-layout/platform assumptions. List known browser, OS and assistive-technology conflicts; unresolved compatibility is a review question rather than a promise that the shortcut is unused everywhere.

For character-only shortcuts, including character sequences, document the selected off switch, remapping mechanism or focus-only scope. [WCAG's character-key guidance](https://www.w3.org/WAI/WCAG22/Understanding/character-key-shortcuts.html) explains these alternatives and why a printable character requiring Shift on one keyboard is still a character shortcut. Do not prescribe global system remapping or infer support from an access-key label. Help text and shortcut metadata describe a binding; neither creates it.

## 5. Check and deliver the specification

Read the saved matrix and transition map against the selected design/revision. Confirm that every in-scope action has a route or an explicit gap; every handled key has one applicable owner; and every destination exists in the relevant state or has a defined fallback. Reconcile repeated component instances and avoid contradictory rules between the shared pattern and local exceptions.

Perform a paper walkthrough of an ordinary path and the important boundary: reverse traversal, last-item removal, nested Escape, disabled item, editable child or delayed completion. Track focus, selection, visible panel and effect separately at each step. A contradiction in the written contract needs correction or a specific owner decision. Do not call this walkthrough a browser or screen-reader test.

Include implementation acceptance cases with initial state, action sequence, expected meaningful result, focus/selection checks and reset requirements. Leave observed-result fields unrun until an actual authorized environment is exercised. These cases are a handoff, not permission to trigger purchases, sends or destructive actions as tests.

If source rules conflict, retain both locators and hold only the affected rows. If a component changes, reconcile by stable component/action identity and refresh its inbound/outbound focus transitions. If a save is failed or uncertain, inspect the destination before retrying and preserve concurrent edits. Do not replace an existing working convention merely to match a generic example.

Return the editable contract, covered components/revision, proposals or unresolved decisions, and the exact review performed. Completion means a coherent, implementation-ready specification for the covered scope; runtime behavior, user-study findings and accessibility conformance remain unverified until separately established.

## Fictional, unexecuted illustration

A fictional workspace has three manually activated tabs and an editable note in each panel. The proposed contract has Tab enter the selected tab, arrow keys move focus among tab labels, and Enter or Space select the focused tab. Typing in the note remains text editing. Leaving and re-entering the tablist returns to the selected tab, not necessarily the last arrow-focused tab.

A Rename dialog opens from a row action. Escape closes a name-suggestion popup first while leaving the dialog open; another Escape closes the dialog under its existing discard rule. If the row still exists, focus returns to its Rename button. If a permitted concurrent update removed that row, the proposal returns focus to the named list heading. That fallback is a design decision to review, not an observed result.

This illustration is authored and unexecuted. No application, keyboard handler, browser setting, assistive technology or live action was exercised.
