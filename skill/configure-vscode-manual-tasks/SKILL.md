---
name: configure-vscode-manual-tasks
description: "Turn existing project commands into explicit, manually invoked VS Code tasks with preserved arguments, workspace context, dependency order and observable completion. Use for a tasks.json handoff, not implementing a CLI, fixing command discovery, enabling background automation or changing global editor settings."
---

# Configure manually invoked VS Code tasks

Give the user a dependable named task they can select from their project, using commands that already exist. The task configuration is a launcher contract: it must preserve what the command receives, where it runs and what counts as completion. A valid configuration file alone does not prove that a command or its output works.

## Establish the intended launcher

Read the actual project instructions, existing `.vscode/tasks.json` or workspace task settings, and the requested command's documented interface. Inspect relevant script bodies and package-manager hooks as data before proposing invocation. A target called `check` or `preview` may write files, install dependencies or contact a service.

Capture these inputs:

- Selected workspace folder, task file location and supported VS Code version/environment
- Command/runtime already available, exact arguments, current working directory and relevant non-secret environment requirements
- Input files or parameters, expected outputs and existing-output policy
- Required dependency order, termination behavior and failure meaning
- Allowed changes: candidate file only, scoped configuration edit, and separately whether a representative task run is authorized

Identify whether VS Code is operating on the local machine, a remote workspace, container or WSL context. A path available to the authoring environment is not proof that it exists where the task executes. Resolve a multi-root workspace explicitly. If the intended runtime is absent, deliver a candidate and precise prerequisite; do not install it or silently substitute another interpreter.

If the problem is an unexplained runtime mismatch, establish its selection chain before authoring a new task. If the requested command does not exist, explain that implementation is separate work rather than hiding a new application inside the launcher.

## Preserve the existing task file

Use a narrowly scoped edit or provide a separate candidate when editing is not authorized. Preserve unrelated task definitions, comments, input IDs, platform overrides and workspace settings. Inspect top-level defaults inherited by the new task; the visible task object may not describe the whole effective configuration.

Choose a unique, descriptive task label. Check `dependsOn` and any existing consumers before changing a label; a debugging configuration may refer to it. Do not make the new task the default build/test action, alter keybindings, add a pre-launch task or move it into user-level settings unless requested. Keep the previous file or exact before-change text for a scoped reversal that will not erase subsequent edits.

## Translate the invocation faithfully

Use the native `process` task form for an executable and an argument vector when no shell behavior is needed. Keep each argument as its own string; do not embed shell quotes into ordinary argument values. Use a `shell` task only when the command genuinely requires the selected shell's pipelines, redirection, builtins or expansion, and state that shell and quoting contract. Process launch avoids shell parsing but does not make the launched program harmless. VS Code documents both forms in its [task schema](https://code.visualstudio.com/docs/reference/tasks-appendix).

Set a deliberate working directory. Prefer established workspace-relative paths when portability is needed, including a named workspace-folder variable for multi-root use. Do not substitute the currently active file's directory when the command operates on the project. Keep input and output paths anchored to the tool's documented base.

Review variable expansion as part of the invocation. A task using `${file}` may affect a different file on the next run. For a fixed-input handoff, use the intended workspace path or a narrowly constrained ordinary input instead. Treat `${command:...}` and command-backed input variables as executable extension operations requiring inspection and authority, not passive interpolation. Check the supported [variable reference](https://code.visualstudio.com/docs/reference/variables-reference) rather than inventing substitutions or assuming nested expansion.

Keep secrets out of task files, command arguments, input defaults and copied terminal output. Reuse an existing approved credential mechanism only if the underlying command needs it; do not grant persistent access through a launcher edit. Inspect only relevant environment keys. Avoid copying the full environment or assuming a task inherits an interactive terminal's activated environment. A shell startup profile is code, not an inert source of variables.

Use platform overrides only for platforms actually requested and supported by the command. A Windows executable name, path escaping and shell choice may differ from Unix. State unverified platforms instead of manufacturing a cross-platform claim.

## Preserve order, failure and manual activation

Keep the dependency graph small and explicit. Detect missing labels, duplicate identities and cycles. When a later step consumes an earlier step's files, encode ordering rather than relying on the written order of task definitions. VS Code runs multiple `dependsOn` entries in parallel by default; `dependsOrder: "sequence"` specifies sequential dependencies. Confirm failure stops the dependent action in the actual target version and task shape. See [compound tasks](https://code.visualstudio.com/docs/debugtest/tasks#_compound-tasks).

For this manual workflow, set or retain `runOptions.runOn` as `default` and do not enable folder-open execution. Do not alter Workspace Trust or automatic-task permissions to get a result. Leave watches, long-running servers and background readiness protocols to a task that explicitly asks for them. A problem matcher can describe diagnostics or readiness; it is not independent proof that a saved artifact is correct.

Use a finite task and an appropriate instance limit, normally one when it writes a fixed destination. The editor's task limit does not coordinate another editor window, terminal invocation or external writer; use the command's supported coordination or document that concurrent access must be excluded. Do not claim a global lock.

Make the terminal result observable. Keep failure output available; use an existing appropriate problem matcher or no matcher rather than a broad expression that hides failures. Do not add `|| true`, suppress exit statuses or change tool options to make the task appear successful. Document what the user should see and where the result goes. The [run behavior guidance](https://code.visualstudio.com/docs/debugtest/tasks#_run-behavior) distinguishes manual and folder-open invocation and describes instance limits.

## Verify the actual handoff at the allowed level

Static verification must establish the saved configuration's syntax/schema for the target version, effective task fields, labels and dependencies, argument boundaries, path bases and absence of unrequested activation. JSON with comments needs a compatible parser or editor check; a plain JSON parser rejecting a comment does not by itself show that VS Code rejects the file. Do not run a repository command merely to validate its launcher text.

When a representative run is authorized, use the actual task in the selected VS Code workspace, with approved input and a separate safe output location. Compare resolved command context and saved output with the command contract. A successful run in an unrelated terminal is supporting evidence, not verification of the editor launcher. Inspect both exit/failure indication and output contents.

Choose a small discriminating check: a path containing spaces for argument handling; a missing required input for failure visibility; an out-of-date or changed dependency input for ordering. Run only checks that fit the permitted effects. Verify an ordinary second invocation does not append duplicates or overwrite unrelated data when repeatability matters. If cancellation is tested, inspect partial files and child-process state before calling it clean; terminating an editor task does not imply its file effects were reversed.

If app access, execution permission or a required runtime is unavailable, finish the config candidate, invocation mapping and check plan. Mark editor launch, output correctness and cancellation checks not run with their exact blockers. Do not present source inspection as a successful task run.

## Delivery and recovery

Deliver the exact task file or scoped patch, the task label and manual invocation path, required environment/input values, output destination and completion/failure meaning. Include the before-change scope and checks actually performed. State whether the file was only prepared or applied, and whether the task was observed running.

On a failed run, preserve diagnostics and inspect the real output before another attempt. Do not enable automatic retries in the task file. Re-running a command with a partial output is safe only under that command's established behavior. A configuration fix must preserve unrelated tasks and needs the affected static and launcher checks again. To revert, restore only the changed task configuration after comparing current text; hold concurrent edits for reconciliation. Rollback of produced files is a separate, scoped action.

## Fictional, unexecuted example

A project already supplies a trusted finite converter `tools/render.py`. Its documented command takes `--input` and `--output` as separate values and refuses an occupied output. The requested task prepares `drafts/June notes.md` as `out/June preview.pdf` from the workspace root.

The proposed process task uses the already-established Python executable, the script path as one argument, and the two paths as separate argument values. Spaces stay inside their values; literal shell quote characters are not added. Its label is `Render June preview`, its working directory is the selected workspace root, it is manual and it has no dependency that publishes the PDF.

Static review can check that mapping. A later approved task run must establish the actual interpreter, arguments and saved PDF. A second run should encounter the converter's existing-output refusal unless the user supplies a new output name; the launcher must not delete the first PDF to force success. No configuration was installed and no editor, converter or test was run for this example.
