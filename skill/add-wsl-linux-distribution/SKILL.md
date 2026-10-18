---
name: add-wsl-linux-distribution
description: "Add one official Linux distribution to an already working Windows Subsystem for Linux installation, establish its user and filesystem identity, and verify a bounded Linux activity without replacing existing distributions or changing host-wide WSL settings."
---

# Add a usable Linux distribution to WSL

Deliver one newly registered distribution, an explicit way to launch that distribution, a deliberate location for its working files and evidence that an ordinary Linux activity retains its result. A terminal tab labelled Linux does not establish which distribution, user, executable or filesystem is in use.

Use this workflow only when Windows Subsystem for Linux (WSL) is already installed and working on the selected Windows computer. Keep it to a new official distribution through the supported installation route. Host enablement, firmware changes, WSL 1/2 conversion, imported root filesystems, physical disk mounting, service exposure and migration of an existing distribution are separate work.

This differs from a [desktop virtual machine](../create-local-virtual-machine/SKILL.md): there is no guest installer disk-selection workflow here, and Windows/Linux integration is central. A [Dev Container](../configure-development-container/SKILL.md) defines a project's image, mounts and hooks. A [Python environment](../create-python-virtual-environment/SKILL.md) separates packages inside an existing operating system. Neither registers this Linux distribution or settles its Windows filesystem boundary.

## Resolve the installation contract

Use the request, installed state and current official documentation to establish:

- The selected Windows computer and Windows account, available operator access, Windows architecture and current WSL support
- Existing registered distributions, their running states and WSL generation, and which existing work must remain uninterrupted
- The official distribution/release needed for the intended activity, its actual available installation name and acceptable acquisition source
- Storage location and free-space budget, including expected growth; an explicit approved location if the default is unsuitable
- Whether authority covers installation, first-run account setup, a small file write and the intended Linux activity
- Required Windows-file access, network use and any editor integration; do not assume these are all needed
- One simple acceptance activity and the agreed final state, with a stopping point if a prerequisite is missing

Do not ask the user to provide information that a narrow installed-state check can establish. If only a plan is requested, deliver the exact proposed route and leave installation unrun. Do not silently substitute an available distribution for a project-required release.

Use a verified Windows WSL executable, not an arbitrary wrapper found in the current folder. From the Windows side, inspect its help/version/status and registered-distribution list. The [Microsoft command reference](https://learn.microsoft.com/en-us/windows/wsl/basic-commands) documents `wsl --version`, `wsl --status`, `wsl --list --verbose` and `wsl --list --online`. Online listing contacts the distribution source; it does not install a distribution. If a command is unsupported, establish the installed version rather than treating an error as proof of no existing distributions.

Record the current default distribution and version policy without changing them. An existing distribution with the requested name is a collision, not permission to reinstall it. Stop and resolve whether the user meant to use that existing instance or choose a genuinely new supported target. Do not unregister it to free the name.

## 1. Confirm source, effects and access before installation

Start from the current official WSL distribution list and publisher documentation. Confirm the release actually provided rather than inferring it from a friendly name. Match architecture and project requirements. Use the selected supported installation mechanism; do not replace it with an arbitrary rootfs archive, a downloaded shell bootstrap or a command copied from a forum.

Obtain missing authority for the named software and its source. Read any new agreement before accepting it through the permitted route. If installation introduces an unexpected account, permission request or protected administrator step, stop at that boundary. An installation request is not permission to disable endpoint protection, change execution policy or bypass managed-device restrictions.

WSL platform setup can enable Windows components and require a restart; see [Microsoft's setup guidance](https://learn.microsoft.com/en-us/windows/wsl/setup/environment). That platform setup is outside this add-distribution workflow. If the selected computer lacks a working supported WSL platform, report the prerequisite and its likely interruption instead of running a general installation command as a repair. Do not update or convert other distributions incidentally.

Inspect the intended storage destination for existing data, links and automatic sharing or sync. Do not point installation at a folder containing another distribution or manually reuse its virtual disk. Keep a private working location with a plausible growth budget. A small initial installation is not a bound on future disk usage. Record actual placement through supported product information rather than guessing a backing-file path from an application name.

WSL deliberately integrates Linux with Windows. It is not a place to execute suspicious software safely. Microsoft's [WSL security model](https://wsl.dev/technical-documentation/security/) explains that the owning Windows user controls their distributions and that Linux-to-Windows integration must be considered in the threat model. Inspect only the relevant mounted paths and integration settings, without reading private host files merely because they are reachable. Keep credentials, browser profiles, SSH agents and private account exports out of setup examples and logs.

If the user requires a host-isolated environment, stop and select a suitable separately authorized design. Do not promise isolation by changing one WSL setting. Network, host-access or security-sensitive configuration changes need their applicable specific approval; they are not routine installation cleanup.

## 2. Install exactly the new distribution

Use current help to confirm the selected command's supported options. The command reference describes selecting a distribution with `--distribution`, suppressing automatic first launch with `--no-launch` and choosing storage with `--location`. Do not assume an older WSL accepts newer flags. Use the documented alternative only after checking that it preserves the same source, target and agreed storage contract.

The later-use PowerShell template below deliberately postpones first-run account setup. Replace the placeholder with the verified official name and invoke the verified WSL executable in the selected Windows account:

```powershell
wsl --install --distribution <VerifiedDistributionName> --no-launch
```

This template has not been executed. Add a verified supported location option only when needed by the approved storage decision. Do not use bare `wsl --install`, silently change the global default, or import an existing disk to bypass a name collision.

Observe the installer result and inspect both the installed package and registered-distribution state through their supported controls. These can be separate stages: Microsoft's [distribution-launcher reference](https://github.com/microsoft/WSL-DistroLauncher#installing--testing) describes an installed Appx whose launcher registers the distribution on first run. If the package is installed but no registration exists yet, continue through its verified publisher-supported first-launch route; do not call the absent list entry an installation failure or reinstall it. If already registered, record the exact registration name and WSL generation. If an operation times out, inspect the existing package, registration and installer before retrying; do not launch competing installers or delete a partial result.

## 3. Complete first run and bind the user explicitly

For an installed but unregistered package, use its verified publisher launcher to complete registration and first run. For an already registered target, launch it by its exact name through the supported command or verified launcher. After registration, read back the actual name and WSL generation before using named commands or recording acceptance. Do not guess a registration name from a store title. Keep the old default untouched. Distinguish Windows account identity from the Linux account created inside this distribution; they are separate identities in the setup process. Follow the selected distribution's current first-run instructions rather than imposing another distribution's account commands.

Any password creation, entry, confirmation or submission belongs to the user through the supported secure handoff. Do not choose a reusable password, paste one into a command or store it in the handoff. Record only whether account setup completed. Unexpected prompts for additional persistent access require their own approval.

After setup, check the Linux user, home directory, release information and architecture within the explicitly named distribution. Do not accept root as a convenient substitute for the intended ordinary development user. If the distribution's supported first-run route does not establish that user, report the missing setup step instead of improvising account administration.

Verify both explicit-user and ordinary named-distribution launch behavior when the requested handoff relies on a default Linux user. A successful explicit-user launch does not prove the default was saved. Keep any correction limited to that distribution and use its documented mechanism. The [WSL settings reference](https://learn.microsoft.com/en-us/windows/wsl/wsl-config) distinguishes per-distribution `/etc/wsl.conf` from Windows-user-wide `.wslconfig`; never overwrite either with a generic template. Preserve existing settings and obtain authority before changing access-related options.

## 4. Choose the working filesystem and actual toolchain

Agree whether work will live in the Linux filesystem or on a mounted Windows drive. Microsoft's [filesystem guidance](https://learn.microsoft.com/en-us/windows/wsl/filesystems) recommends Linux-side storage for Linux-command-line work and documents Windows access through `\\wsl$`. The same guidance explains that Windows executables can run from Linux. A command's apparent availability therefore does not prove it is the intended Linux tool.

For a new Linux-only activity, choose a new ordinary directory under the intended Linux user's home. Do not relocate an existing project, copy a home directory or expose additional host folders to make a demonstration convenient. If an existing project must remain on Windows storage, record that decision and inspect relevant case, permission and executable-selection behavior before using it. Do not change directory case-sensitivity or apply broad recursive permissions as a shortcut.

Resolve the executable that will perform the acceptance activity and its actual operating-system context. A Windows runtime found through inherited PATH may run successfully while using the wrong dependencies or file semantics. Prefer an explicit verified Linux executable for the check. If project tooling or package acquisition is missing, report it separately; distribution creation does not authorize installing an entire language stack or running repository hooks.

Use only supported filesystem access paths. Do not edit or move a distribution's backing storage directly from Windows. Keep source and data separate from any disposable test folder. If editor integration is requested, inspect the actual connection target and opened path; a Windows editor window with a Linux-looking terminal is not evidence that its tools execute inside this distribution. Missing integration can remain an explicit incomplete stage rather than triggering unrequested extension installation.

## 5. Verify identity, retained work and interruption scope

Use the agreed small activity, with inspected commands and no external service effects. For example, creating and reopening an original tiny text file can demonstrate basic filesystem persistence without downloading packages. Confirm the destination is absent before writing; record its expected content and actual path. Do not reuse a filename that could overwrite existing work.

Collect separate evidence for:

1. The intended new registration and release, WSL generation and ordinary Linux user
2. A named launch selecting that registration rather than the pre-existing default
3. The intended working filesystem and executable identity
4. Successful execution of the agreed activity and observed result
5. Reopening a new named session and reading the retained result
6. Existing registrations, host-wide defaults and unrelated files remaining unchanged

A new terminal session establishes session reuse, not a full distribution restart. If a restart is part of the request, first save work, close or gracefully stop known processes in the new distribution, and explain the exact interruption before the authorized stop. The command reference distinguishes `wsl --terminate <name>`, which stops one distribution, from `wsl --shutdown`, which terminates all running distributions. Never use the all-distribution operation as a casual check. Termination can lose unsaved process state; it is not graceful application shutdown.

After an authorized target-only stop, confirm the target's stopped state, relaunch the same registration and repeat the retained-file check. If another process immediately starts it, investigate that ownership rather than repeatedly terminating it. Do not interrupt existing background work merely to improve the evidence. Report a restart check as unrun when its interruption is not approved.

## Recover without destroying a distribution

- **Name already present:** preserve it and resolve intended reuse versus a genuinely new installation. Never infer disposability from a familiar name
- **Download or installation fails:** retain the exact sanitized failure and partial registration state; retry only the evidenced supported step, within the same approved source and target
- **Platform, virtualization or managed-policy prerequisite fails:** stop this workflow and identify the separate host change needed; do not change firmware, boot configuration or security controls
- **First run is incomplete:** return to the existing instance's supported setup after checking current state; do not reinstall to avoid a credential handoff
- **Wrong user or executable:** correct only the verified launch selection within scope. Preserve the existing default and avoid global PATH edits
- **Files appear missing:** confirm registration, user, working directory and filesystem before restoring or copying anything. Do not search unrelated private Windows folders indiscriminately
- **Space becomes insufficient:** pause new acquisition/writes where safe and report the storage decision. Do not shrink virtual disks, move backing files or remove another distribution

The command reference warns that unregistering a distribution permanently loses its associated data, settings and software. Do not include unregister as an automatic rollback or retry step. Any permanent removal needs exact-target action-time confirmation and a separately understood recovery position. A fresh install is not a restoration of the former instance.

If a correction is made, repeat only the affected acceptance checks against the final state. Stop at a missing prerequisite, new permission boundary or repeated failure without new evidence. Leave a usable handoff for the partial state rather than manufacturing success from installation output.

## Deliver the launch and preservation handoff

Return the registration name, distribution/release, WSL generation, ordinary user, supported launch command, work-directory location and the actual checks performed. Include the final running/stopped state and any incomplete package, editor or restart stage. Do not expose credentials or unnecessary account paths.

State separately whether the result is a prepared plan, installed distribution, completed first run, verified activity, session-reuse check or observed restart. Acceptance requires the requested supported distribution and user, correct launch/file/tool identities, the agreed activity and persistence evidence at the permitted level, and preservation of other instances and defaults.

Do not promise a backup merely because files survive a restart. Distribution export, migration, ongoing backup, automatic service startup and exposure to other computers are separate tasks. End at the bounded Linux workspace the user requested.

## Fictional, unexecuted illustration

A fictional user has a working WSL platform and an existing distribution used for a local service. They want a different official Linux distribution for learning shell commands, with a tiny practice file that survives reopening. The existing service must stay available, and no new editor or language package is needed.

The proposed plan records the existing registration and default, confirms that the selected new distribution is available and absent locally, then installs only that target without automatic launch. The user completes its first-run password setup. A named launch establishes the new ordinary Linux user; the practice folder stays under that user's Linux home rather than a mounted Windows project folder.

Expected acceptance is the correct release and registration, a verified Linux tool, the expected practice-file content and the same content in a newly opened named session. A full distribution restart is withheld unless its interruption is separately acceptable; global shutdown would also disrupt the original service. If the selected name is already registered, the plan stops before installation and never unregisters it.

This is a fictional decision walkthrough, not execution evidence. No distribution was installed, account created, file written, process stopped or application launched for this illustration.
