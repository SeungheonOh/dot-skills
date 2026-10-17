---
name: diagnose-command-resolution
description: "Explain why a terminal, editor task or local script selects the wrong command or runtime, trace shell precedence and launcher context, and verify a scoped correction when authorized."
---

# Find Which Command Actually Runs

Use when an installed tool is reported missing, the wrong version launches, or the same command behaves differently in a terminal and an editor task. Deliver a resolution chain for the affected invocation and a justified next action. A list of installed versions does not show which one this launcher selects.

This workflow investigates command selection before application logic. Use ordinary build debugging after the intended executable and runtime are established. It does not install a toolchain, repair a package manager, rewrite global shell setup or bypass execution restrictions.

## Required inputs

- The literal command name and relevant arguments, with secrets removed; preserve quoting and whether the launcher uses an argument array or a shell command string
- The failing context: computer or container, working directory, terminal/editor/task runner, actual shell and version if applicable, and whether that shell is interactive or a login shell
- The expected tool/runtime and its authoritative project requirement, such as a version file, manifest or explicit user choice
- The observed error/version and time, plus a known-working context if one exists
- The permitted machine, files and diagnostic commands; whether the request is diagnosis only or includes a scoped local correction

Read available evidence before asking questions. A missing expected version prevents deciding which version is correct, but does not prevent identifying the selected command. If the only evidence is a screenshot from another machine, report that boundary and request the smallest useful diagnostic from that context.

## 1. Capture the original launcher before changing it

Keep one record per context rather than combining outputs from different sessions:

```text
context_id; capture_time; machine/container; launcher; working_directory
shell_and_mode_or_no_shell; command_spelling; relevant_argument_shape
expected_tool_and_source; observed_error_or_result; evidence_locator
```

Do not assume an editor task uses its integrated terminal's shell. It may invoke an executable directly, set its own environment or run inside a container. Confirm the task configuration or process details that establish the launch route. A configured default shell is not proof of the shell already running.

Inspect only relevant environment values and configuration lines. Usually these are the ordered executable search path, active environment indicator, project version selector and launcher override. Do not dump the entire environment, shell history, profile or process command line into the report; these can contain tokens and personal paths. Use consistent path labels in shared output while retaining enough private evidence to distinguish candidates.

Do not start a new login shell, source a profile or activate an environment merely to inspect it. Those operations execute setup code and alter the state being explained. Read the relevant text first; record conditional branches and includes that cannot be resolved safely.

## 2. Resolve names in the affected context without launching candidates

Use the active shell's own lookup facility, not a different shell's idea of the search path. Establish whether the supplied name is a shell alias, function, builtin, script, shim or executable. An explicit path is a different invocation from an unqualified command name.

For a confirmed Bash session, these are inspection examples for a fictional command named `atlas`:

```sh
type -t -- atlas
type -aP -- atlas
hash -t atlas
```

The first classifies the name, the second searches executable paths, and the last reports an existing remembered location or a lookup failure. The path search alone does not account for alias/function selection. Inspect a relevant alias/function privately when indicated; avoid pasting its full body if it embeds secrets. Do not clear the hash table before recording it. Bash searches functions, builtins and then executable paths, with remembered executable locations relevant to that last stage; aliases are expanded earlier during parsing. See the [Bash command search rules](https://www.gnu.org/software/bash/manual/html_node/Command-Search-and-Execution.html), [builtin lookup options](https://www.gnu.org/software/bash/manual/html_node/Bash-Builtins.html) and [alias rules](https://www.gnu.org/software/bash/manual/html_node/Aliases.html).

For PowerShell, use the applicable version's command metadata facilities and preserve command type, source/module and path. `Get-Command -Name 'atlas' -All -ListImported` limits discovery to the current session; absence there does not inventory every installed module. An unrestricted exact-name `Get-Command` lookup can auto-import a module and run its setup, so do not use it as a supposedly inert inspection of an untrusted module. Refer to [Get-Command](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/get-command) and [command precedence](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_command_precedence). For other shells, use their documented equivalent rather than translating these flags by guesswork.

Preserve search-path order and duplicate entries while diagnosing. Note an empty or relative entry rather than silently replacing it. Inspect filesystem metadata for the selected candidate: existence, file kind, symlink target where available, and readable relevant launcher text. Do not change permissions or follow an inaccessible link through another access route.

Build the shortest supported chain:

```text
typed name -> shell-selected alias/function/builtin or executable
           -> resolved file / version-manager shim / wrapper
           -> selected project tool and interpreter, where established
```

A shim pathname is not the final runtime. Read the relevant version-manager selection and wrapper configuration without executing arbitrary hooks. A script's interpreter directive can introduce another lookup; trace that only as far as the evidence supports. If runtime selection happens dynamically and cannot be inspected safely, mark that edge unresolved rather than claiming the chain is complete.

## 3. Compare contexts and choose a discriminating explanation

Compare the failing and working contexts along the chain, not just their displayed version numbers:

| Evidence | Bounded interpretation and next check |
| --- | --- |
| An alias or function shadows an installed executable | Determine where it is introduced and whether the intended launcher uses that shell expansion; changing the search path alone may not help |
| Different executable path order | Trace the differing entry to the launcher, environment activation or documented startup layer; do not assume either order is correct |
| Same shim, different project directory | Inspect project-local version selection and parent-directory configuration; the shim can choose different tools |
| A remembered path differs from current path search | Preserve both observations; a scoped session refresh is a possible correction only after establishing the expected target |
| Terminal and editor agree on executable, but errors differ | Inspect interpreter, arguments, working directory and relevant environment; command selection alone may be ruled out |
| Lookup finds a file but launch fails | Preserve the exact error; permissions, interpreter availability or binary compatibility are separate possibilities, not proof that installation is missing |
| No candidate appears in the inspected context | Report not found in this scope; do not infer that the tool is absent from the whole computer |

Rank hypotheses by the observations they explain and name the smallest check that would distinguish the top two. Do not reinstall a tool because a wrapper failed, or edit a lockfile to make an unexpected runtime acceptable.

## 4. Apply only the authorized, narrow correction

For diagnosis-only work, return the proposed change and verification procedure. If a local fix is already authorized, choose the smallest supported change, such as correcting an editor task's explicit executable path or using the project's already-installed intended environment. Preserve the before value and unrelated edits.

- Prefer a bounded launcher or project-level correction when that matches the intended behavior; do not convert it into a system-wide default change
- A temporary override needs a restoration plan and an explicit record that it is temporary; a fresh shell is a separate verification context, not an automatic fix
- Changing persistent shell profiles, global search paths, aliases, package installations or defaults requires authority for that scope
- Do not add the current directory or an untrusted directory to the executable search path, weaken execution policy, remove quarantine, use elevated privileges or bypass a security warning to make lookup succeed
- Never invoke an unknown candidate just because it is named like the expected tool. Even `--version` executes it. First establish source/trust and permission for the bounded invocation

Read back the actual changed configuration. If writing failed or its outcome is uncertain, inspect the destination before retrying; do not stack duplicate path entries or repeat a partial edit blindly.

## 5. Verify resolution and task behavior separately

Repeat the relevant lookup in the actual affected launcher. A correct lookup in a new terminal does not verify an already-running editor task. Record the final selected path and runtime evidence, including any remaining unresolved wrapper edge.

When execution is permitted and the selected program is trusted, run its documented non-mutating identity check and the smallest safe operation that demonstrates the original problem is resolved. Inspect the command's real side effects first; a wrapper named `check` may install packages, write outputs or contact services. Do not run repository hooks, builds or tests when execution is restricted. In that case report static resolution established and behavior untested.

For a persistent correction, verify in a fresh authorized instance of the intended launcher after protecting unsaved work. For a temporary correction, verify the bounded result and then restore the original state unless the user asked to keep it. Capture restoration separately from successful diagnosis. Do not interrupt other tasks or restart an application without the needed permission.

Acceptance requires:

- The selected command matches the user's intended tool and project requirement, with evidence for the relevant selection layers
- The originally failing launcher is checked, not replaced by an easier unrelated context
- The identity check and original safe behavior check have separate actual results or explicit unrun reasons
- A permanent fix survives the relevant fresh-launch check, or remains labelled provisional
- Temporary changes are restored or explicitly retained within authorization

## Deliverable and failure handling

Return the cause if established, the resolution chain for each inspected context, the narrow change made or proposed, and exact checks with passed/failed/blocked/not-run status. Include relevant configuration locations, preserved before values and any restoration result. Keep machine-identifying paths private when sharing beyond the user.

Stop the dependent operation if the candidate is untrusted, access is denied, the required interpreter cannot be established, or the next step requires installation, security changes or broader file edits. Continue the read-only explanation. Give the exact unresolved edge and smallest needed decision. A successful lookup is not a successful build; a new error after selecting the intended command is a new finding, not a completed repair.

## Fictional worked example

These facts are authored to illustrate reasoning; no command or application was run for this example.

A project requires the already-installed `atlas` 4. The user's terminal resolves `atlas` to `/opt/atlas-4/bin/atlas`. An editor task reports version 3. Its inspected task configuration invokes `/opt/atlas-3/bin/atlas` directly, without a shell. Both contexts have the same search path, with version 4 first.

The direct path explains why changing `PATH` would not change this task. The proposed correction is the task's executable field, from the version-3 path to the verified existing version-4 path, preserving its arguments and working directory. The required checks are a readback of that field, an authorized task-launched identity check, and the original safe operation. Until those happen, the status is **diagnosis supported by supplied configuration; correction proposed; execution unrun**. A terminal-only version check cannot close the issue.

Example request:

```text
Explain why this editor task uses a different atlas version from my terminal.
Inspect the supplied task configuration and sanitized shell lookup output.
Identify the selection chain and propose the narrowest fix. Do not execute
the project, install tools or edit global shell settings.
```
