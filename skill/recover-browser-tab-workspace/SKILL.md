---
name: recover-browser-tab-workspace
description: "Recover a selected lost browser window or tab workspace through supported session and history interfaces, preserving current tabs, repeated occurrences and reload boundaries. Use for returning to interrupted browsing work, not bookmark migration, whole-profile restoration or recovering a submitted transaction."
---

# Recover the browser workspace the user was using

Return the user to the recoverable pages and organization of a selected interrupted browsing session. Preserve work that is open now, distinguish restored session state from reconstructed links, and leave sensitive or consequential reloads held. A list of visited URLs is not necessarily the lost window, and reopening a page does not prove its unsaved work survived.

Use [bookmark-migration-rehearsal](../bookmark-migration-rehearsal/SKILL.md) for a persistent bookmark collection and [recover-unsaved-editor-work](../recover-unsaved-editor-work/SKILL.md) for a document editor's buffer. This workflow does not read credentials, decode raw session databases, change sync, install recovery extensions or repair a corrupt browser profile.

## Identify the missing workspace and protect the current one

Establish the authorized device, browser/version, exact profile, ordinary versus private window, and what happened: one tab closed, a window closed, a crash, or an apparently empty restart. Use the user's remembered page titles, approximate closure time, window/group names and purpose as search clues. Ask only for a distinction that changes the recovery, such as which of two work profiles was used.

Check whether the workspace is merely hidden, minimized, on another desktop, collapsed into a group or open in another existing window. Reading an already connected device is different from enabling cross-device sync or signing into a new account. Do not transfer a private workspace to another profile to make it accessible.

Before restoring anything, identify current windows, important unsaved forms, active downloads and newly opened work that must remain. Do not close them, restart the browser, clear history/cache, reset settings or repeatedly relaunch the app. Those actions can destroy useful recovery choices or current work. Record a minimal private baseline when needed; avoid screenshots containing unrelated page contents.

If important unsaved text is still visible, preserve it using the site's supported draft/copy route within existing authority before navigating away. Do not click Submit, Save to a shared account, or repeat a prior transaction merely to preserve the text. A private copy needs an appropriate approved destination, and its existence must not be described as recovery of the site's complete state.

## Choose the strongest supported source

Inspect current official instructions for the actual product and version, then prefer the narrowest source that identifies the missing workspace:

1. An existing window or collapsed group: reveal it without navigating its pages unnecessarily
2. A recently closed window, group or individual tab: prefer its identified entry over reopening unrelated closures
3. The browser's previous-session recovery interface: inspect available selections before restoring the whole session
4. Bounded browsing history or an already available tab list from the relevant period: reconstruct selected links when native restoration is unavailable
5. A supplied export/list: prepare a recovery map, explicitly limited to what that list records

History contains visits, not an authoritative list of tabs that were open simultaneously. Bookmarks can nominate a page but do not establish its place in the lost session. A tab on another device is evidence about that device, not a complete copy of this workspace. Retain those source distinctions.

[Chrome's documented shortcuts](https://support.google.com/chrome/answer/157179?hl=en) reopen previously closed tabs. Use one supported action and inspect the result rather than blindly repeating a shortcut through unrelated history. [Firefox's session guidance](https://support.mozilla.org/en-US/kb/restore-previous-session) distinguishes recent tabs/windows and previous-session restoration; private windows are excluded from its restoration model. Check the actual available entries instead of assuming a control exists or changing future startup settings to recover past work.

Do not follow troubleshooting advice that resets, reinstalls or clears the profile as part of this recovery. If the supported interfaces cannot expose the needed state, preserve the situation and report that limit. Raw session files can contain form and authentication state; copying or uploading a whole profile is not a harmless fallback.

## Keep page identity separate from a safe reload

For each meaningful candidate, retain enough to match it after recovery: source entry, window/group position when evidenced, title, safe URL identity, expected page purpose, recovery method and current outcome. Preserve repeated occurrences; the same URL can have belonged to two workflows or held different navigation/form state. Do not deduplicate on title or URL alone.

Keep credential-bearing, password-reset, one-time sign-in and action-bearing URLs out of derived files and chat. Use a neutral source locator and hold reason rather than copying their secret values. Do not strip an ordinary query or fragment silently: it may identify the needed record or view. When safe identity cannot be represented, use the native entry without reproducing its private value, subject to the action boundary below.

Restoration can load pages and contact their services. A request to recover ordinary browsing pages can authorize their normal reopening, but it does not authorize resubmitting a form, purchasing again, sending a message, confirming a payment or accepting a security warning. Inspect known risky candidates before bulk restoration. Hold a whole-window restore when it would necessarily activate a known unsafe entry and the browser cannot exclude it; recover an available safe subset instead.

If the browser asks to resend form data, stop that page and establish what the original operation did. Preserve an unknown outcome as unknown. For an expired login, missing permission, download restart or security prompt, use the appropriate separately authorized route or leave the page pending. Do not weaken protection or invent that the previous operation failed.

## Restore in observable increments

Use the actual browser's supported operation in the correct profile. Preserve existing windows and groups; do not replace current work with an older snapshot. A native window restore may preserve more context than opening its URLs individually, but only observed properties can be claimed.

After the first action, read back the resulting window/tab identities before continuing. Establish whether the operation added one tab, a group or a whole window and whether it restored the intended source. If the result is uncertain or the interface timed out, inspect current windows before repeating it. Avoid creating duplicate restored windows through blind retries.

For history-based reconstruction, open selected ordinary pages in a separate recoverable workspace when supported. Keep the evidenced order; mark any proposed grouping or order as reconstructed. A reconstruction should not silently rearrange or close the user's current tabs. Do not call a fresh page load a recovered navigation stack, scroll position or draft.

Verify the properties the user actually needs: expected page/record identity, occurrence count, window/group membership, pinned state, and any specifically required in-page context. Inspect unsaved content only as far as needed. A familiar title can appear on a login screen or error page, so distinguish a restored tab container from a usable destination. Do not read unrelated content merely to increase confidence.

If one page crashes or causes a repeat failure, stop restoring that candidate. Preserve usable recovered work and report the trigger. Do not repeatedly restore the whole session to reproduce the crash. Broader browser diagnosis belongs in [isolate-browser-profile-failures](../isolate-browser-profile-failures/SKILL.md) when requested.

## Deliver the recovered state and remaining limits

Return a concise recovery map or summary identifying:

- The actual profile and recovered windows/groups, using safe labels
- Pages restored through native session state versus reconstructed from history
- Properties checked, required context missing and entries still held
- What current work was preserved and any unexpected changes observed
- The smallest next decision for a blocked entry

Account for every selected candidate as restored, reconstructed, already open, held or unavailable. Do not claim complete recovery when the original population is unknown. “Eight candidate pages reopened” is defensible; “all tabs recovered” needs evidence of the original workspace and a match.

If a private recovery list was requested, save it separately and reopen the actual file to verify its safe links, ordering and status labels. Do not export raw browsing history or active credentials. Creating bookmarks, enabling startup restoration, changing sync and deleting duplicate tabs are separate changes, not automatic cleanup.

Stop when the requested workspace is usable to its evidenced extent, supported sources are exhausted, or a specific access/authorization boundary prevents the next step. Do not undo recovery by closing newly restored tabs that now contain user edits. State remaining browser state the user should preserve.

## Fictional, unexecuted illustration

A fictional user lost a research window but has a new unsaved form open elsewhere. A supported recent-window entry contains six tabs, including two occurrences of the same comparison page and a payment-result page known to request form resubmission.

If the recovery interface permits choosing entries, the plan would restore the five ordinary occurrences while leaving the payment page held. The two comparison tabs would remain distinct. If no selective restore is available, the plan would use supported individual entries or reconstruct the safe URLs, labeling the lost window organization as unverified. It would preserve the current form and would not resubmit the payment.

No browser, account, tab, form or recovery store was accessed for this illustration. The candidate counts and outcomes are invented, not observed recovery evidence.
