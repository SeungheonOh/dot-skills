---
name: repair-notebook-execution-order
description: "Repair a computational notebook that depends on hidden session state, out-of-order cells or stale results, preserving its narrative and native structure while establishing an explicit execution path. Use for a corrected notebook and bounded fresh-kernel evidence, not a general build failure, new analysis or a reproducibility certification."
---

# Make the notebook's saved story match its execution

Deliver a corrected notebook that can produce its required results through the declared execution path, plus a concise record of inputs, environment, changed cells and actual verification. A notebook that looks complete can contain outputs from different source versions or an earlier kernel state. Consecutive execution numbers and a successful file open do not prove that its current cells produced its current results.

Use [failing-build-repair](../failing-build-repair/SKILL.md) for an ordinary project build/test failure, [analyze-data-question](../analyze-data-question/SKILL.md) for a new analysis, and [recover-unsaved-editor-work](../recover-unsaved-editor-work/SKILL.md) when preserving missing edits is the immediate task. This guide repairs the connection between notebook cells, persistent kernel state, input artifacts and saved outputs without redesigning the analysis.

## Establish the intended notebook run

Identify the exact notebook/revision, intended kernel and language, execution environment, input files or existing approved data sources, expected outputs, and the failure or mismatch. Determine whether the user wants explanation, a repair candidate, or a repaired and executed notebook. The intended route may be top-to-bottom or an explicitly documented selection; do not assume every exploratory branch belongs in one run.

Record the desired parameters, working directory and output destination. Distinguish fixed input snapshots from live data, deterministic results from permitted variation, and saved figures/tables from external actions. A previous displayed number can be evidence to investigate, but it cannot define correctness without its input and calculation meaning.

Preserve the current saved notebook and unsaved source edits before restarting, clearing outputs or closing anything. An active kernel may contain the only copy of an intermediate result, and multiple clients can share it. Do not restart a user's shared kernel as a diagnostic shortcut. Prefer a separate authorized candidate and fresh kernel; resolve any irreplaceable live-state preservation first.

## 1. Inspect cells as data before running them

Read source, cell order, cell types, available IDs, attachments, metadata, execution counts and output records through a nonexecuting reader. Preserve notebook-native structure. The [Jupyter file-format reference](https://nbformat.readthedocs.io/en/latest/format_description.html) describes code cells, rich outputs, attachments and cell IDs; converting the notebook to a script and back can lose material the user needs.

Create a compact cell map using stable IDs when present and source-revision-bound ordinals otherwise. Note definitions, reads, mutations, file/working-directory effects, external calls and output-producing cells. Keep narrative headings and explanations attached to the computation they describe. Execution counts are incomplete clues, not an authoritative historical trace: source can change after execution, outputs can be copied, and other clients may have changed the kernel.

Inspect the actual code and relevant invoked helpers before execution. Include shell commands, notebook magics, imports with initialization effects, package installers, database calls, file writes, subprocesses and output-rendering behavior. A cell titled “setup” or “test” is not necessarily harmless. Do not run unfamiliar code, install dependencies, contact live services or publish artifacts without the authority required for that source and effect.

Opening or trusting a notebook is separate from establishing safe execution and truthful results. [Jupyter's trust model](https://jupyter-server.readthedocs.io/en/latest/operators/security.html#our-security-model) governs active output rendering; a trusted badge is neither a code audit nor proof of current output provenance. Do not enable trust or weaken rendering protections just to display an old chart. Minimize private data in tracebacks, tables, widget state and embedded outputs; do not upload a notebook to an external viewer without authorization.

## 2. Find the missing dependency or stale claim

Trace the first affected result back through its cell dependencies and input versions. Look for the specific hidden state that would explain it:

- A variable or function defined only in a later, deleted or unexecuted cell
- A name rebound after an earlier result, or an object mutated through another reference
- A cell that appends, accumulates, consumes an iterator or mutates a dataframe when rerun
- A changed parameter whose downstream outputs were not regenerated
- A different working directory, environment variable, local file, imported module version or cached artifact
- A result displayed by an earlier version of the current cell
- An intentional alternative branch mistaken for a mandatory step

Distinguish static findings from observed execution. A missing earlier definition suggests a dependency problem; an actual fresh-kernel failure at that cell establishes the observed boundary when the run is authorized. Do not infer every dependency from a simple variable-name scan: functions, closures, shared objects, dynamic execution and file effects may hide relationships.

Treat source errors, missing environment prerequisites, unavailable inputs and hidden-session dependencies separately. A missing package is not fixed by changing analysis results. A fresh-kernel failure after a data source changes does not by itself prove that cell order caused the old/new difference.

Map affected downstream cells and narrative claims, not just the first exception. A repaired table with an old attached chart and unchanged prose conclusion remains inconsistent. Keep unrelated preserved outputs clearly historical until their relationship to the current source is established.

## 3. Repair the declared execution path

Make the smallest coherent source/order change that removes the evidenced dependency while preserving the intended computation. Common repairs include moving a definition before its first use, introducing an explicit parameter cell, loading a required authorized input in the declared path, or making state initialization visible before a repeated operation.

Do not simply sort cells by old execution counts. Moving cells can change mutations, randomness, file writes and narrative meaning. Preserve the order of meaningful side effects and the relationship between explanations and their results. When two exploratory alternatives cannot both belong to one run, retain them and make the intended choice explicit rather than deleting an inconvenient branch.

Do not hard-code the old answer, suppress an exception, replace missing inputs with invented data or add a seed solely to make results look familiar. A fixed seed or changed initialization is a computational choice that must match the intended analysis. For expected stochastic variation, define the actual acceptance relationship and uncertainty rather than promising byte-identical output.

Preserve cell identity, Markdown/raw content, attachments, tags and required metadata unless a specific repair needs a change. Record a source-cell change map. When a tool cannot preserve a required extension or widget structure, hold that conversion or use the supported native route; do not silently flatten the notebook.

Keep authoritative inputs read-only. Redirect generated artifacts to a new authorized scratch/output location only when that preserves the computation's meaning. A fresh kernel does not reset files, external services, environment state or existing caches. Identify and isolate these separately; do not delete a cache or reuse an existing output as an unexplained substitute for computation.

## 4. Establish fresh-kernel evidence safely

Execute only when the source, environment and cell effects are within existing authority. Obtain any required confirmation for unfamiliar code or additional external effects. If some required cell remains unapproved, do not skip it and claim the full notebook ran; complete static repair and identify the exact blocked dependency.

Use an isolated candidate with the intended kernel, actual recorded runtime/dependencies, approved input snapshots, declared working directory and bounded resources. Metadata naming a kernel does not prove that this installed kernel or package set was used. Do not install, upgrade or switch runtimes merely to make the run pass without resolving the relevant scope.

A browser reload or closing/reopening the tab is not a fresh-kernel reset. [Jupyter documents that a kernel can remain active after the browser closes and can have other clients](https://jupyter-notebook.readthedocs.io/en/stable/notebook.html#opening-notebooks). Establish a genuinely new, task-owned kernel/session and execute the declared cells in their intended order using the supported consumer. Do not attach to a convenient existing session containing hidden variables.

Preserve baseline outputs separately, then remove stale outputs and execution markers from the candidate's intended execution path through the supported route. Run that path without manual rescue cells, concealed warm-up commands or accidental continuation after a required error. Record the first failure and which cells actually completed. Stop dependent execution when its prerequisites are invalid.

Check consequential outputs independently of the old notebook display: a known small calculation, reconciled record count, required schema, expected dimensions, or source-supported result relationship. Inspect actual generated files and meaningful plots, not just the absence of exceptions. A cell that returns a filename does not prove a complete file was written.

If the repair concerns rerun accumulation, exercise the relevant repeat behavior only in the isolated safe state and within the permitted effects. For a top-to-bottom requirement, the decisive observation is the complete intended path from fresh state; running the failed cell after arbitrary interactive preparation is insufficient. Another full run is useful only when it resolves a real repeatability question.

## 5. Save a self-consistent candidate

After the successful bounded run, save and read back the exact delivered notebook and generated artifacts. Verify that source cells, parameters, input identities and saved outputs belong to that run. Inspect required Markdown attachments, tables, images and output formats in a safe compatible reader when available. Rich-output presence is not proof that an interactive widget works after reopening.

Do not retain old successful outputs below a newly failed cell without an unmistakable historical/unverified label. If execution is blocked or partial, deliver the edited candidate with affected stale outputs removed or clearly separated, while preserving the original's evidence. Never manually renumber cells or attach fabricated results to imply a run occurred.

Provide the notebook or verified destination and a concise execution note: original/candidate identities, changed cells and reason, kernel/runtime, input versions, parameters, declared cell path, generated files, observed checks and remaining limits. Keep logs private and redact secrets from the report without erasing necessary evidence in the protected source.

## Recovery and completion

On a timeout, interrupt only the task-owned execution through the supported route when safe. An interrupted cell may already have written part of a file or contacted a service; inspect effects before any retry. Do not treat interrupt as transaction rollback. If a save is uncertain, inspect the destination before writing again, and preserve concurrent edits to a shared notebook.

If a repair fails, retain the useful diagnostic, revise the evidenced cause and rerun only from an appropriate clean state. Do not keep rerunning an unchanged side-effecting cell. If the required environment, input or permission is unavailable, return the useful static candidate and the precise blocker with execution marked unverified.

Finish when the requested notebook path and saved candidate meet the bounded acceptance checks, or when a concrete missing prerequisite blocks further authorized work. A successful fresh-kernel run establishes that run under its recorded inputs and environment, not universal reproducibility, scientific validity or permission to publish.

## Fictional, unexecuted illustration

A fictional notebook loads 20 observations, calculates a subtotal, and then applies an exclusion rule. A chart cell displays a filtered subtotal from an earlier interactive run even though the saved cell order calculates the subtotal before filtering. All cells have output, so opening the notebook looks reassuring.

The proposed repair moves the supported exclusion step before the subtotal, retains the explanation next to that step, and regenerates the affected subtotal and chart from the declared input in a fresh task-owned kernel. Acceptance would independently count the retained observations and check that both displayed results use that same population. Changing the old chart label or renumbering execution counts would not repair the computation.

This scenario is invented and was not executed. No notebook, kernel, dataset, code cell, package installer, chart renderer or external service was run for the illustration.
