---
name: prepare-batch-rename-handoff
description: "Prepare a collision-checked, recoverable handoff for renaming a bounded set of local files, with exact old-to-new mappings, cycle and case-only ordering, stale-plan guards and per-step recovery. Use for a local bulk-rename plan, not document classification, folder synchronization or content conversion."
---

# Prepare a batch-rename handoff

Turn a naming rule or supplied mapping into an inspectable plan that a permitted local executor can apply without overwriting a different file. The deliverable is a version-bound mapping and operation order, not a shell one-liner assembled from filenames. Preparation does not execute the renames.

Use this for ordinary files whose names must change within a selected local filesystem. Keep directory-tree moves, cross-volume transfers, package internals, application-managed libraries and synchronized remote objects outside the ordinary plan unless their additional semantics are explicitly established. A cloud service's stable file IDs and move API need its own filing workflow.

## Inputs and outputs

Establish the selected root, exact file set or bounded selection rule, recursion and exclusions, requested target names, intended filesystem/platform, and where the private handoff should be saved. Preserve an explicit preview-only instruction. If the target environment is unavailable, work from a supplied inventory and identify every assumption that must be checked there.

Return a compact packet, using the user's preferred document or machine-readable format:

- A scope record with root identity, capture time, selection, filename-comparison assumptions and permitted effects
- A mapping with an entry ID, original relative path, source identity evidence, requested relative path, disposition and reason
- An ordered list of exact moves, including temporary names, preconditions and expected after-state
- A recovery ledger template and acceptance checklist, with checks performed distinguished from checks awaiting an executor

Store paths losslessly. Use a structured format with escaping when names contain newlines, tabs or other delimiters. A display table is not a machine-safe instruction format. Keep private path names out of public examples and logs; do not read file contents merely to infer better names when a supplied naming rule suffices.

## Capture the selected files and occupied namespace

Inspect directory entries without following links by default. Record object type, exact filename spelling, parent identity, size, modification information and available filesystem identity. A device/inode or platform file ID helps identify an object during this run; it is not a permanent identity across copies, restores or later reuse. A content digest can support preservation when reading the bytes is permitted, but equal digests do not make two directory entries interchangeable.

Inventory occupied target names as well as selected sources. Excluded entries can still block a target. Mark unreadable directories, missing mounts and incomplete listings as unknown, not empty. Hold links, junctions, hard-linked entries, cloud placeholders or unsupported file types until the mechanism's treatment is known. Never rename a link target by resolving it silently.

Freeze the selected population before numbering files. For sequential names, specify an explicit stable ordering and preserve leading zeroes and the chosen width. Directory enumeration order and modification time are not implicit sequence policies. Resolve whether extensions, multi-part suffixes and hidden-file names participate before applying a stem rule. A renamed extension does not convert the file format.

Keep naming policy separate from filesystem comparison. Check separators, parent traversal, empty components, reserved names and length limits for the target. Check case and Unicode-equivalent collisions according to the actual volume or documented target contract; lowercasing every name is not a universal filesystem model. Preserve the user's spelling when valid. If comparison behavior is unknown, hold affected names rather than claiming portability.

## Build and inspect the rename graph

Each selected original path must have exactly one disposition: rename, unchanged, held or excluded. Each rename must identify one target. Two files requesting the same effective target are a conflict, even when their bytes match. Do not silently add counters, overwrite one, merge entries or delete a presumed duplicate.

Classify each target against the complete occupied namespace:

1. Unoccupied target: potentially direct move
2. Target occupied by an unchanged, excluded, held or unselected entry: conflict
3. Target occupied by another selected entry that will move: ordering dependency
4. Same object and same spelling: no-op
5. Same object with a requested case or normalization spelling change: explicit spelling-only operation, not an automatic no-op

For an acyclic chain, vacate destinations before moving into them. For a cycle, choose a unique temporary name on the same filesystem, move one member aside, rotate the remaining moves, then move the temporary entry to its final name. A supported two-phase approach that stages every moving member can also work, but record its extra intermediate states. Treat a case-only rename using a temporary name when the target's supported operation requires that route.

Temporary names must be outside both requested targets and occupied names under the same comparison rule. They are part of the plan and collision checks, not secret implementation details. Do not create an empty placeholder and later overwrite it as an improvised reservation. Give each dependent group a boundary: if any required member is held, the group cannot partially proceed as though the blocked destination will become free.

Check application references separately. Renaming a media sidecar, source asset or linked document can break a caller even when bytes survive. Preserve explicit pairs and groups, identify known path-based references, and hold unresolved reference-sensitive changes. This skill does not silently rewrite contents or promise that unknown references are intact.

## State the executor contract

The handoff must require the executor to re-establish the root, complete affected namespace and source identities immediately before applying the plan. A changed file, newly occupied destination, altered selection or changed mapping invalidates the affected group. Use current observations to revise the plan within the user's authority; do not replay stale paths over newer work.

Require an available rename mechanism whose destination-collision behavior is known. For example, Python's ordinary rename can replace an existing file on Unix; a prior existence check does not make that operation no-clobber. See the [documented rename semantics](https://docs.python.org/3/library/os.html#os.rename). Use a supported non-replacing operation for this preservation contract. If it is unavailable, deliver the plan and hold execution rather than substitute copy-and-delete or an overwriting primitive.

A collision-safe destination operation alone does not protect a source from concurrent edits or replacement. Record the actual coordination available and require other writers to be quiescent for affected files during the bounded operation. A lock file respected only by the rename tool cannot enforce that promise on editors or sync agents. If source identity and coordination cannot be established, the executor must stop that group.

Before each move, the executor records intent durably enough for the agreed recovery boundary; after it, it reads back source/target identity and appends the observed result. Keep planned, attempted, verified, failed and uncertain distinct. A lost response can follow a successful move. Preserve the original ledger and inspect reality before any retry.

No single-file rename establishes all-or-nothing completion of a multi-file batch or power-loss durability. State those limits. Authorization to prepare the packet does not authorize applying it, stopping applications, changing permissions, moving outside the selected root or publishing its path inventory.

## Acceptance and recovery

Review the saved packet against the inventory, not just the naming expression:

- Every source entry has one disposition, and every executable target is unique under the established comparison rule
- Simulating the ordered path/identity moves on the inventory never consumes an occupied destination or loses an entry; final paths match the mapping
- Every temporary path is accounted for, and held members block their dependent group
- A supplied interruption point has an unambiguous next inspection and cannot trigger blind replay
- Required content, metadata and reference preservation is stated honestly, including unverified properties

Where a later permitted execution occurs, acceptance additionally requires re-listing the selected entries, verifying final identities and required bytes/metadata, reconciling every journal row and confirming no temporary entry remains unexplained. Do not claim those checks from a plan simulation.

For recovery, inspect every original, temporary and target location implicated by the last uncertain step. Match identities, not names alone. Resume only operations whose preconditions now hold. If reversal is requested and authorized, invert verified moves in reverse dependency order after checking that current entries still match their recorded post-state and old names are free. A later edit or a newly occupied old name is a recovery hold; never overwrite it to make the journal look clean. Retain partial results and report exact remaining locations.

## Fictional, unexecuted example

A supplied inventory on one volume contains `front.png` with identity F and `back.png` with identity B. The approved mapping swaps the two names. A third file `notes.txt` is excluded. A proposed temporary name `.rename-swap-01` is shown unoccupied in the supplied inventory.

The planned sequence is F: `front.png` to `.rename-swap-01`; B: `back.png` to `front.png`; F: `.rename-swap-01` to `back.png`. After the second move, the expected intermediate state is F at the temporary name and B at `front.png`. A timeout on the third move requires inspecting both the temporary name and `back.png`; repeating the original three moves would be wrong.

If an unselected file appears at `.rename-swap-01` before application, the group is held and replanned. This walkthrough establishes only the mapping logic on fictional facts. No filesystem, rename command, interruption or recovery was executed.
