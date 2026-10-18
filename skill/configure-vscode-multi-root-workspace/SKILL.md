---
name: configure-vscode-multi-root-workspace
description: "Save several existing project folders as one reopenable VS Code workspace, with deliberate root identities, portable paths and setting scope. Use for a multi-root editing handoff, not creating checkouts, running project tasks, configuring a debugger or provisioning a development environment."
---

# Configure a reopenable multi-root workspace

Help someone move between related folders without losing track of which project owns a file or setting. Deliver a small `.code-workspace` file and a checked root map. The workspace groups existing locations; it does not combine repositories, move source, install tools or establish cross-project build dependencies.

Use [linked Git worktrees](../create-linked-git-worktree/SKILL.md) to create another checkout, [repository onboarding](../repository-onboarding-map/SKILL.md) to explain source, [manual editor tasks](../configure-vscode-manual-tasks/SKILL.md) to wrap commands, and [development containers](../configure-development-container/SKILL.md) to provision an environment. This workflow owns the saved editor composition and its effect on navigation and settings.

## Establish the folders and intended use

Resolve the following from the request and available files rather than asking a long setup questionnaire:

- The exact existing folders to include and one reason they belong together
- The machine and filesystem where VS Code will open them, plus the target editor version
- Whether the workspace is personal or intended for a team with a known directory layout
- The destination for the workspace file and any existing workspace to preserve
- Whether the request authorizes a candidate only, writing the workspace file, or opening it in the editor
- A representative file from each root and the navigation or editing behavior the user needs

Use only an available, authorized environment. A path visible to the authoring tool does not prove it exists in the user's editor environment. Keep local and remote locations explicit; if the proposed collection crosses execution contexts the selected client cannot combine, provide separate workspace candidates with that limitation rather than inventing a shared mount or connection.

A missing folder is a blocker for that root, not permission to clone, download, mount, or create an empty substitute. Ask for the correct location if it cannot be resolved. Do not add a parent directory containing unrelated projects merely because it makes selection easier.

## Inspect before opening

Read existing workspace files and relevant `.vscode` configuration as data. Identify startup tasks, executable-path settings, extension recommendations and other activation hooks that could matter when opening a folder. Do not execute project code to determine its name. Preserve unsaved editor buffers and record the currently open workspace before replacing a window; prefer a separate window where supported and useful.

Opening a workspace can activate installed extensions. Inspect the existing trust state and proposed activation surface before opening unfamiliar content. [Workspace Trust](https://code.visualstudio.com/docs/editing/workspaces/workspace-trust) restricts certain capabilities in Restricted Mode; it is not a general isolation guarantee. Do not trust a new folder, broaden a trusted parent, disable protections, enable automatic tasks or install recommended extensions just to complete this arrangement. Security changes need their own applicable approval. If safe opening is blocked, return the file and mark native verification pending.

Keep account identifiers, private absolute paths, credentials and confidential folder labels out of shareable examples. A personal workspace can disclose machine layout even when it contains no source. Saving in a shared or synchronized location and sending the file to others require the appropriate destination and sharing authorization. Do not enable settings synchronization as part of this task.

## Choose root identities and a path base

Resolve each root to its actual directory and check for duplicate aliases, symlinks, case-equivalent paths and parent/child overlap. Prefer the smallest nonoverlapping set that serves the user's goal. If overlapping roots are intentional, explain their navigation implications and verify the target editor's behavior; do not silently drop one.

Assign stable, distinct display names when directory basenames collide or are unclear. Record the association between each label and its actual directory. Labels describe roots, not Git branches, and renaming a label must not silently retarget a directory. Inspect existing named-folder references before changing labels.

Choose the workspace file's final location before calculating paths. Relative folder paths are resolved from that file's directory; absolute paths bind the file to a particular layout. A shared candidate should state its required sibling-directory arrangement. If that arrangement is unavailable, supply a clearly personal candidate or leave the unresolved path explicit rather than claiming portability. See the [multi-root workspace format](https://code.visualstudio.com/docs/editing/workspaces/multi-root-workspaces).

Do not move the original source folders to make paths fit. Resolve paths with their exact spelling and case, preserve spaces, and use the native file format's escaping. A relative path that resolves today can still point to a different project after someone rearranges folders; acceptance must check identity as well as existence.

## Write only the needed composition

For a new workspace, begin with the `folders` array and optional root names. Add settings only when needed for the requested behavior. For an existing workspace, edit its selected entries without replacing comments, unrelated settings, launch definitions, tasks or recommendations. The file supports JSON with comments; use compatible validation rather than treating every plain-JSON parser rejection as an editor failure.

Keep source-folder configuration in place. Multi-root folder settings apply only where that setting supports folder scope; editor-wide settings belong at a supported broader scope. Do not flatten every folder's settings into the workspace. Converting an existing single-folder window can carry editor-wide settings into the saved workspace, so inspect the resulting file rather than assuming only roots changed. The multi-root reference describes these distinctions.

For a setting that matters, inspect its effective value on a representative file in each root. Account for profile/user, remote, workspace, folder and language-specific overrides, plus administrator policy. Object-valued settings can merge while arrays replace; a language-specific value can beat a narrower non-language value. Consult [settings precedence](https://code.visualstudio.com/docs/configure/settings#_settings-precedence) for the installed version. Do not solve an override by resetting global settings or removing a project convention.

Avoid adding format-on-save, auto-save, code actions or tooling changes as cosmetic defaults. They can change files beyond this task. Preserve existing task and debugger references; if root naming exposes an ambiguous reference, describe the affected consumer and route any functional change through its existing workflow. Workspace arrangement does not authorize running that consumer.

## Verify the saved workspace at the allowed level

First read back the final bytes and check syntax, root names, path resolution from the final location and absence of unintended settings or executable sections. Compare the scoped change with the previous file. Check local links and required folder identities without dumping private directory contents.

When opening is authorized and its activation effects are understood, use the actual saved file in the intended editor context:

1. Confirm the opened workspace file and expected roots, including a distinct known file from each root
2. Open same-named files from different roots where relevant and verify that their ownership is distinguishable
3. Search for a known harmless term across the intended roots, then limit a search to one root; inspect exclusions and ignore handling before interpreting missing results
4. Inspect effective values of any setting intentionally changed, in each affected root and relevant language
5. Close and reopen the saved workspace only after preserving unsaved work, then confirm that the same root identities and intended settings return
6. Check that source files and unrelated configuration were not changed by the arrangement or activation

Do not run builds, tasks, terminals or debugging sessions solely to prove that folders are present. A visible repository list does not authorize staging, committing, fetching or switching branches. If an extension is needed for a requested feature, check its multi-root support and actual availability; do not promise cross-root language intelligence merely because both folders appear.

Separate static validity, successful editor opening, navigation checks and persistence after reopening. A parsed candidate is useful but does not establish native behavior. If access or trust boundaries prevent a check, name that exact unrun stage and deliver the safe work already completed. Test only the requested environment; one local check does not prove portability to another machine.

## Recover and hand over

If a root is missing, re-resolve the path against the saved workspace's location and check whether the volume or remote context is unavailable. Do not create a blank directory, grant broader filesystem access or replace it with a similarly named project. If saving was interrupted, inspect which file exists and its contents before retrying.

If a setting changes unexpectedly, inspect the winning scope and any migration from the original window. Revert only the owned setting or root edit after comparing current bytes; preserve concurrent changes. Return to the prior workspace when needed without discarding buffers. Removing a root from the workspace is different from deleting its source directory; never use filesystem deletion as workspace cleanup.

Deliver the workspace file or scoped patch, its intended save location, root-to-folder map, layout prerequisites, any deliberate setting changes, and checks actually performed. State whether it is a candidate, applied file or verified reopened workspace. Stop when the requested composition is usable or one precise missing path, permission or client capability blocks the next check. Publication and source cleanup remain separate actions.

## Fictional, unexecuted example

A fictional Cedar project keeps `web-client` and `service-api` beside a `workspaces` directory. Both roots contain `README.md`. The user wants a personal saved workspace without changing either repository's settings.

A candidate saved as `workspaces/cedar.code-workspace` is:

```json
{
  "folders": [
    { "name": "Cedar client", "path": "../web-client" },
    { "name": "Cedar service", "path": "../service-api" }
  ]
}
```

The review resolves both paths from `workspaces`, checks that they identify the intended existing projects and leaves folder-specific conventions intact. If the file were copied into `web-client`, those relative paths would need a fresh resolution check; the original portability claim cannot follow it automatically. If opening the service root requires a new trust decision, the candidate is delivered with editor verification pending.

A later authorized check would distinguish the two README files, find a known term within each intended search scope and reopen the saved composition without source changes. Those are expected checks only. No workspace was installed, editor opened, trust changed, command executed or live workflow tested for this illustration.
