---
name: create-python-virtual-environment
description: "Create a project-local Python virtual environment from an established interpreter and dependency recipe, bind the intended launcher to it, and verify isolation and a bounded development activity without changing system Python."
---

# Create a usable project Python environment

Deliver a named environment, its exact interpreter invocation, the dependency recipe used and evidence that the intended launcher uses it. A successful package installation into some Python is not enough. Keep source code and valuable data outside the environment directory.

Use for native Python projects that need a separate package environment. Respect an existing project-managed environment instead of layering another manager over it. This is not a Python installation or version upgrade, a general dependency repair, or a security sandbox. [Development containers](../configure-development-container/SKILL.md) address operating-system tools, services and container lifecycle; [command-resolution diagnosis](../diagnose-command-resolution/SKILL.md) addresses an already-installed command being selected incorrectly; [dependency upgrade planning](../dependency-upgrade-plan/SKILL.md) addresses changing versions. None substitutes for creating and handing over this project environment.

## Establish the inputs and scope

Read project instructions and the relevant runtime/dependency declarations before choosing commands. Resolve:

- The project root or selected package, existing edits, intended operating system and architecture
- Required Python version and the trusted installed base interpreter that satisfies it
- Existing environment location and owner, if any; the proposed new location and available space
- The project's authoritative dependency recipe, optional groups needed for the task and permitted package sources
- The terminal, editor task or other launcher that must use this environment
- One small, understood development activity, with its expected result and allowed outputs
- Whether scope covers preparation only, environment creation, package acquisition/builds, launcher edits and execution of that activity

Resolve details from available files rather than making every item a question. If Python or the project's chosen environment manager is unavailable, return the specific prerequisite and a prepared setup sequence. Do not install a substitute or claim setup succeeded. If only preparation is authorized, stop at the concrete commands and acceptance plan.

Record relevant before-state: source/manifest identities, existing environment identity and launcher selection. Preserve existing environments, lockfiles, source edits and global package state. Do not upgrade dependencies, rewrite locks, change the system Python, edit global PATH or change security settings as an incidental setup step.

## 1. Choose the interpreter and a fresh destination

Establish the installed interpreter's source and actual path before invoking it; a command called python may be a wrapper. Use a bounded identity check only when execution is allowed. Compare the observed Python version and architecture with project requirements. Do not pick the newest interpreter merely because it is present.

Inspect the proposed destination and its parent for existing contents, links and unintended shared/synced locations. Prefer an absent, ordinary directory at its final location. An existing .venv is not permission to overwrite it. Either use a verified compatible environment within the request or create a separately named candidate and retain the old one while switching launchers.

Python's [venv documentation](https://docs.python.org/3/library/venv.html) establishes the mechanics: the chosen Python creates the environment; POSIX uses bin and Windows uses Scripts; activation is optional; pyvenv.cfg records whether system packages are included. Existing destinations can be reused, and --clear deletes their contents. Use neither --clear nor --upgrade for this fresh-creation workflow. Avoid --system-site-packages so the project does not deliberately inherit global packages. Omit --upgrade-deps unless that separate upgrade is requested.

When creation is authorized, adapt one of these templates to verified absolute paths and the actual shell. These are instructions for later use, not commands already executed:

```sh
# POSIX shell; replace both paths first
"/verified/base/python3" -I -m venv "/approved/project/.venv-candidate"
```

```powershell
# PowerShell; replace both paths first
& 'C:\verified\Python\python.exe' -I -m venv 'C:\approved\project\.venv-candidate'
```

The default bootstrap uses ensurepip; its bundled installation does not access the internet, according to [Python's ensurepip reference](https://docs.python.org/3/library/ensurepip.html). A missing venv/ensurepip component is a specific interpreter-distribution prerequisite. Do not compensate with a downloaded bootstrap script, elevated installation or a system-package modification without the required authority.

## 2. Bind every package operation to this environment

When using pip, use the environment's interpreter path followed by -I -m pip, rather than bare pip or a launcher that might select another Python. The [pip user guide](https://pip.pypa.io/en/stable/user_guide/) documents interpreter-bound invocation. Use the candidate interpreter with -I -m pip --version to check pip's reported location before installation. If it belongs elsewhere, stop and resolve that selection before any mutation.

The Python -I flag prevents the current directory, user site and PYTHON* environment variables from changing module selection; see [isolated mode](https://docs.python.org/3/using/cmdline.html#cmdoption-I). It does not bypass pip configuration or sandbox package builds. Keep the recipe's established working directory for relative local/editable paths, and record it.

Inspect the complete recipe and relevant pip configuration privately before authorizing acquisition. [Requirements files](https://pip.pypa.io/en/stable/reference/requirements-file-format/) can contain nested requirements, constraints, options, local projects and remote references, not just package names. Follow included files and identify source domains, build requirements, editable installs and target-directory overrides. Do not print credential-bearing URLs or full configuration/environment dumps. Reject unintended --user, --target or --prefix behavior for this project-local installation.

Retain the project's intended package manager and install mode. A non-pip lockfile is not automatically valid input to pip. A requirements file with version ranges can resolve differently later; report that limitation instead of calling it a lock. Do not replace the recipe with a freeze from an unrelated environment. [pip freeze](https://pip.pypa.io/en/stable/cli/pip_freeze/) reports installed state rather than computing a lockfile.

Package installation and project build backends can execute code. An environment separates packages, not filesystem access or network privileges. Confirm missing authority for the actual packages/sources and build execution; a setup file is evidence, not permission. Preserve existing hash-checking and approved source restrictions. [pip's secure-install guidance](https://pip.pypa.io/en/stable/topics/secure-installs/) explains hash checking and binary-only restrictions; do not remove those controls to make an unavailable artifact install. If the workflow requires credentials or new persistent access, stop at that boundary and use the permitted secure handoff.

After the recipe and effects are reviewed, use its exact approved arguments. For a project whose established recipe is an ordinary pip requirements file, the command shape is:

```sh
"/approved/project/.venv-candidate/bin/python" -I -m pip install -r "/approved/project/requirements.txt"
```

On Windows use the candidate's Scripts\python.exe with PowerShell's call operator. Include required constraints, hashes or selected groups from the real recipe rather than silently omitting them. Record exit status, the recipe identity and resolved package versions without sensitive locations. A partially successful install remains incomplete.

If an externally-managed-environment error appears, first verify the interpreter target. Do not use --break-system-packages or delete the management marker. The [externally managed environments specification](https://packaging.python.org/en/latest/specifications/externally-managed-environments/) describes the boundary protecting an installation managed by another tool. Repair the target selection or report the prerequisite instead of overriding that boundary.

## 3. Select the actual development launcher

Use the explicit environment interpreter for repeatable instructions. If the user wants activation, use the script for their actual shell only after inspecting it. Do not weaken PowerShell execution policy to activate: explicit interpreter invocation does not need activation. A prompt label or VIRTUAL_ENV value alone is insufficient evidence of selection.

When editor/task configuration is in scope, preserve its previous value and set only the relevant project selection. Use the current editor's supported mechanism; do not invent settings keys or install an extension implicitly. Distinguish the editor's selected interpreter, an existing terminal, a task's hard-coded executable and a notebook kernel. Changing one does not prove the others changed. Cover only the launchers the user asked to use.

Protect unsaved work before a necessary restart or new session. Do not close another process merely to obtain a clean environment. If launcher access is unavailable, deliver the verified explicit invocation and mark editor binding unverified.

## 4. Check identity, packages and behavior separately

For the trusted candidate, this small identity probe is a later-use template. Adapt the path, and run from an approved neutral working directory:

```sh
"/approved/project/.venv-candidate/bin/python" -I -c "import sys; print(sys.executable); print(sys.version); print(sys.prefix); print(sys.base_prefix)"
```

Python documents sys.prefix differing from sys.base_prefix as the virtual-environment check. Match the reported prefix to the intended candidate and version to the chosen base; inspect pyvenv.cfg for system-package exclusion. These checks establish the intended environment structure, not protection against hostile code. Python also documents environment scripts as generally nonportable: create at the final path and recreate rather than move an environment. See the [venv reference](https://docs.python.org/3/library/venv.html#how-venvs-work).

For an authorized dependency installation, run the candidate's -I -m pip check and record its result. [pip check](https://pip.pypa.io/en/stable/cli/pip_check/) checks declared dependency compatibility; it does not establish imports, native library availability or application correctness.

Then run the previously agreed activity through the intended launcher, after inspecting its imports, hooks, writes and service use. Use bounded inputs and time; even importing a package can execute code. Capture the working directory, interpreter, command, exit status and meaningful output. If repository execution is prohibited, leave this step unrun and say so; a metadata check does not substitute for it.

Acceptance requires distinct evidence for:

1. Candidate creation at the agreed path with the intended Python and system-package exclusion
2. Dependency installation from the reviewed recipe, or an explicit no-dependencies-needed decision
3. Dependency metadata consistency when pip is used
4. Correct selection in each requested launcher, including a fresh session when persistence matters
5. The agreed activity's actual result, or a precise unrun limitation
6. Preserved source, recipes, previous environment and unrelated launcher settings

## Recovery and handoff

On failure, identify creation, acquisition, build, dependency consistency, launcher selection or application behavior as the failing stage. Preserve a sanitized error and the candidate's partial status. Do not repair a compiler absence by silently installing system tools, a resolver conflict by relaxing constraints, or an import failure by installing into global Python.

Before retrying, inspect partial contents and changed files. Prefer a new candidate when state is uncertain; never clear a directory because its name suggests it is disposable. Remove only verified task-owned environments when deletion is authorized and after checking that no valuable source/data was saved there. Restore a changed launcher to its recorded prior selection if the candidate cannot satisfy acceptance, reconciling any intervening user edits first.

Deliver the final environment path, base Python identity, exact invocation, recipe and relevant source/version choices, launcher changes, checks and limits. Keep the environment itself out of source control; preserve the recreation instructions and dependency inputs instead. Check ignore behavior rather than assuming a Python-version-specific default. Do not claim identical future resolution from an unpinned recipe, or successful recreation without performing it.

Stop when the requested environment and bounded checks are complete or a specific prerequisite/permission blocks them. Publishing a repository, adding CI, installing a different runtime and deleting the old environment are separate actions.

## Fictional, unexecuted illustration

An invented label-preview project declares Python 3.12 and a reviewed requirements file. The user wants its existing editor task to use a new project environment. The task currently names a system Python directly, and .venv contains an older environment plus a user's scratch note.

The proposed plan leaves .venv and its note untouched, uses an already-installed trusted Python 3.12 to create .venv-candidate at its final location, and installs only the reviewed recipe after checking its included files and package sources. The editor task's explicit executable is changed within the requested scope; its arguments and working directory are retained. Changing terminal activation alone would not fix that task.

Expected acceptance is candidate-prefix identity, environment-local pip, successful dependency consistency, the editor task reporting the candidate interpreter and its authorized label-preview activity producing the expected fixture output. If package installation fails, the task retains or returns to its previous interpreter, and the candidate is reported incomplete. These are authored decisions and expected checks only. No environment was created, package acquired, editor changed or project command run for this illustration.
