---
name: configure-development-container
description: "Create or repair a reusable Dev Container environment for an existing project, preserving workspace data, lifecycle effects and host boundaries through creation, reuse and rebuild. Use for development-environment configuration and verified handoff, not production deployment, toolchain upgrades, a repository tour or a one-command editor task."
---

# Configure a development container that can be recreated

Deliver the native environment definition and a usable route back into the project's development work. The important result is that a fresh environment and a reused one provide the intended tools and workspace without depending on unexplained manual installs or damaging retained work. An editor attaching successfully is only one checkpoint.

Use an established Dev Containers implementation supported by the requested environment. Keep this task bounded to the development environment. [Repository onboarding](../repository-onboarding-map/SKILL.md) explains existing code and commands; [integration configuration handoff](../prepare-integration-config-handoff/SKILL.md) documents application settings; [manual editor tasks](../configure-vscode-manual-tasks/SKILL.md) wraps established commands. None of those alone defines the environment's creation, retained storage and rebuild contract.

## Establish one useful development activity

Read project instructions, existing container definitions, toolchain declarations, dependency locks and the commands needed for the user's selected activity. Identify relevant pre-existing edits before changing files. Do not replace a working environment merely because a preferred template exists.

Resolve these inputs from available evidence:

- Project snapshot, selected workspace or monorepo package, configuration location and intended development activity
- Requested client and version, container runtime and actual daemon/build-host location, host and container architecture, and supported target platforms
- Required runtime/compiler, system packages, language dependencies and any local companion services
- Source location, writable outputs, valuable retained data, disposable caches and existing container/volume identities
- Permitted scope: prepare files, apply a scoped edit, download/install named dependencies, create or rebuild an environment, and run the selected check

Record the command, inputs and expected result for one representative development activity before designing the environment. Derive it from the project rather than assuming a conventional command exists. Inspect hooks and subprocesses sufficiently to understand writes, network calls and service use. If a tool or execution permission is unavailable, complete a configuration candidate and precise verification plan; do not claim the environment was built.

## 1. Select the smallest supported definition

Choose an existing image when it already supplies the required stack, a Dockerfile when the environment needs a maintained image recipe, or Compose when the activity needs independently managed companion services. Do not introduce Compose solely to wrap one otherwise sufficient container. Preserve a project's established mode unless changing it is necessary and within scope.

Return the actual selected devcontainer.json and only the companion files it requires. Use the target implementation's supported JSON-with-comments format and schema. Preserve unrelated settings, comments, service definitions and other environment variants. Name the exact configuration to select when several exist. The [Dev Container specification](https://github.com/devcontainers/spec/blob/main/docs/specs/devcontainer-reference.md) defines supported file locations, image metadata and orchestration modes; product-specific customizations need that client's own documentation.

Map each path to its real base: configuration file, build context, Compose project, host source root or container workspace. A workspaceFolder value names where the client opens; it is not evidence that the intended files were mounted there. For Compose, distinguish the service to attach to from the services that may be started and stopped. Inspect dependencies, file merge order, existing resource names and lifecycle ownership before operating a shared stack. Use the [metadata reference](https://github.com/devcontainers/spec/blob/main/docs/specs/devcontainerjson-reference.md) for those fields instead of copying an unrelated template.

## 2. Make the build inputs and acquisition explicit

Identify each image, Feature, package source and extension by its actual publisher and requested version or pin. Prefer existing project constraints; do not silently upgrade a runtime, rewrite a dependency lock or switch package managers to make setup easier. Record the platform and resolved image identity when available. Separate an immutable artifact identity from a mutable tag or version range, and leave an unavailable digest unknown rather than inventing one.

Determine what the builder can receive before any build. Keep the context as small as the recipe needs, inspect the applicable .dockerignore rules, and ensure required dependency manifests remain included. The context and exclusions define which local files are available to the builder; a Dockerfile's location is not automatically its context. See [Docker build contexts](https://docs.docker.com/build/concepts/context/). Do not send unrelated source, private exports, local secret files or a whole home directory to a local or remote builder as a convenience.

Read proposed Dockerfile instructions, Feature installation behavior, lifecycle commands and relevant project install hooks as executable operations. A trusted-looking environment file can still run repository scripts. A package lock does not authorize installation, and a container does not make arbitrary code harmless. Obtain missing authorization for acquisition or execution rather than treating configuration parsing as permission to build.

Keep credentials out of Dockerfiles, build arguments, environment examples, layers, logs and shared configuration. [Docker's build-secret guidance](https://docs.docker.com/build/building/secrets/) distinguishes temporary build-secret facilities from ordinary build arguments and environment variables. Document only the required binding and owner; arranging ongoing credential access or transmitting credentials requires its own permitted secure route. A development-environment request does not authorize copying credential stores or enabling agent forwarding.

## 3. Define what survives each lifecycle

Create a compact storage map covering only meaningful paths: host source or container-volume source, container writable layer, dependency/cache volume and any local service data. For each, state the writer, retention expectation, whether it is reconstructible, and what a rebuild or cleanup may affect. Do not label a directory disposable just because it is named cache.

Check mount targets against image content. A bind mount can hide files previously installed at the same target; a successful image build therefore does not prove those files are available in the opened workspace. Docker also resolves bind mounts on the daemon host, which may differ from the client machine. See [bind-mount behavior](https://docs.docker.com/engine/storage/bind-mounts/). Resolve the actual source path and its owner rather than silently substituting a local directory on another machine.

Choose a workspace/dependency arrangement that avoids mixing incompatible host and container artifacts. If a volume hides a dependency directory, explain how it is populated and refreshed when its defining lock or platform changes. An old populated volume must not be the only reason a rebuilt environment passes. Do not delete it to demonstrate freshness; use a separately named, authorized scratch resource when fresh-state evidence is needed.

Establish the initial contents as well as the volume's identity. Docker can copy existing image-directory content into an empty volume by default, so a new volume is not proof that a setup hook populated it. Record deliberate image seeding or establish the intended empty starting state before attributing the result to a hook. See [volume population behavior](https://docs.docker.com/engine/storage/volumes/#mounting-a-volume-over-existing-data).

Preserve the user's ability to edit and recover their files. Establish the effective container user and client user, expected file ownership, and host-specific UID/GID behavior. remoteUser affects the client and its subprocesses rather than every container process; container-wide identity is a different setting. Consult the target implementation's [non-root user guidance](https://code.visualstudio.com/remote/advancedcontainers/add-nonroot-user). Do not fix a mismatch with a recursive ownership change over the host checkout, broad permissions or an unrequested switch to root.

## 4. Assign setup to the correct lifecycle

For each required setup operation, record where it runs, when it repeats, what it reads or changes, what establishes success and how an interrupted attempt resumes. Keep stable environment tools in the maintained image recipe where appropriate; keep source-dependent setup tied to the actual mounted project. Avoid hidden manual installation steps that vanish with the old container.

The metadata reference distinguishes host-side initializeCommand from container-side creation commands, postStartCommand on starts, and postAttachCommand on client attachment. Commands can repeat; attaching a second window must not unknowingly reseed data or start another service. A lifecycle object's members run in parallel, so dependent operations need explicit ordering rather than reliance on key order. See [lifecycle scripts and command forms](https://github.com/devcontainers/spec/blob/main/docs/specs/devcontainerjson-reference.md#lifecycle-scripts).

Put each operation in a hook only when automatic execution at that point is requested and appropriate. Leave ordinary development commands manual unless the desired environment requires their startup. Keep setup finite; a long-running server placed in a completion-gating hook can prevent readiness. Define an observable prerequisite for dependent work and use the implementation's supported waiting behavior. Do not confuse attachment with completion of every asynchronous setup step. The [VS Code creation guide](https://code.visualstudio.com/docs/devcontainers/create-dev-container) explains setup hooks and the rebuild loop.

Inspect effective metadata inherited from images and Features, not only the checked-in file. Added hooks, mounts or capabilities can survive a superficially restrictive local setting because properties have different merge rules. Verify the final resolved behavior without exposing secrets; do not infer that one false value cancels inherited privileges. See the specification's [metadata merge rules](https://github.com/devcontainers/spec/blob/main/docs/specs/devcontainer-reference.md#merge-logic).

Keep environment scope explicit: a value intended for a client terminal may not reach a companion service. Resolve only necessary ordinary values and describe secret requirements without retrieving them. Keep shell versus argument-array behavior faithful to the actual command; changing quoting can alter what a setup operation receives.

## 5. Review host reach and side effects before activation

Make required access visible: bind-mounted paths and write modes, published or forwarded endpoints, devices, privilege/capability requests, daemon sockets, automatic credential sharing and additional services. Never add a Docker socket mount, privileged mode, relaxed security profile, host networking or a public port as a routine troubleshooting shortcut. Such changes can reach beyond the intended development environment and require the applicable specific approval.

Use only already authorized resources and destinations. Confirm the actual runtime context immediately before creation, rebuild, stop or removal so a familiar resource name cannot target another daemon. A request to prepare files does not authorize running hooks; an authorized ordinary rebuild does not authorize discarding valuable data, changing security settings or installing unknown software.

Agree which resources this task owns and what closing the editor should stop. Do not attach to or stop an unrelated existing service simply because its name matches. A local forwarding declaration and a published host port have different exposure; check the actual route and target-client visibility before claiming it is private or usable. Keep production connections out of a routine development smoke check.

## 6. Verify fresh, reused and rebuilt states at the allowed level

First read back the saved files. Check the chosen schema, referenced paths, image/Feature identities, effective hooks, mount relationships and required configuration. Use a compatible passive parser or client validation when available. Inspect the effects of any command called validate, resolve or dry-run before using it; do not let a static check invoke installers, hooks or infrastructure unintentionally.

When environment execution is authorized, verify the exact delivered definition through the intended implementation. Keep original work protected and use approved sample data and isolated resources where possible. Record configuration identity, host/client/runtime context and outcomes separately:

1. Creation or build: the selected recipe completed, or its exact failed stage and partial resources are recorded
2. Workspace: the opened path contains the intended source snapshot, required files are visible, and a permitted scratch write has the expected ownership and retention
3. Development activity: the selected command resolves the intended toolchain and produces its independently expected result inside this environment
4. Reuse: detach/reattach or stop/start as relevant, then check repeated-hook effects, service ownership and retained work
5. Recreation: rebuild or create a separate fresh instance within scope, then repeat the distinguishing activity without relying on unexplained old container state

Choose the lifecycle transitions that define the requested acceptance, not every possible platform or restart pattern. Keep build-cache use, dependency-volume reuse and genuinely fresh state distinguishable. A successful cached rebuild is useful evidence but does not establish an empty-cache or offline rebuild. No need to purge global caches to make a stronger claim.

Inspect setup failure and recovery when it matters, using an approved bounded case. A failed hook must remain visible; do not append a success-forcing shell expression or move the same failure into an ignored phase. Check changed files and partial data before rerunning. Re-run relevant checks after configuration changes; results from earlier bytes do not establish the final candidate.

Report static review, creation, client attachment, actual development work and recreation as separate statuses. Missing runtime, denied access or unavailable installation authority yields an explicit unrun stage, not a replacement claim based on a JSON parser. A working Linux container does not prove native Windows behavior or every supported host architecture.

## Delivery, recovery and stopping

Return the actual configuration files or scoped patch, the selected entry point, prerequisites, version/acquisition choices, important storage and hook behavior, and the shortest useful start/reopen/rebuild instructions. Include checks actually performed and the unresolved stage that changes usability. Do not deliver only a checklist when usable configuration files were requested.

On failure, preserve relevant logs without secrets and identify whether the cause is acquisition, image build, mount resolution, setup, permissions, client connection or the development activity. Fix only the authorized cause. Do not solve dependency failure by silently changing the project lock, mount failure by exposing a broader path, or startup failure by disabling security controls.

Reconcile current files before restoring the previous configuration so later edits survive. Configuration rollback and data rollback are separate: rebuilding from older files does not reverse writes to a source mount or database volume. Stop or remove only freshly verified resources within the approved cleanup scope, preserve anything holding valuable work, and avoid system-wide prune commands. If safe recovery needs a new decision, return the prepared correction and precise blocker.

Stop when the requested environment definition and justified checks are complete, or when a concrete prerequisite blocks the remaining stage. Publishing configuration, pushing an image, changing shared CI, upgrading unrelated tooling or deploying the application are separate actions.

## Fictional, unexecuted illustration

A fictional map-preview project uses an established Node toolchain and a checked-in dependency lock. Its Linux image recipe installs dependencies under /work/project/node_modules, while the proposed workspace bind mount covers /work/project. The editor can attach, but the mount would hide the image's dependency directory. Moving installation into postAttachCommand would also repeat it for every attachment and make an ordinary second window an installation trigger.

The proposed correction uses an approved toolchain-only image without project dependencies at the volume target, mounts source at the explicit workspace, and uses an isolated dependency volume with a documented source-dependent creation step and lock-change refresh procedure. The step's installation effects require the existing setup authorization. No daemon socket, extra privileges or production credentials are added. An existing populated volume remains untouched; a separately approved fresh volume, with its empty starting state established, would let a later check attribute dependency population to the creation step.

Expected checks are a visible workspace, correct user ownership, the project's established preview build using the intended dependencies, no repeated install on a second attachment, and the same result after an authorized fresh recreation. These are authored expectations only. No configuration was installed, package downloaded, container built, application run or lifecycle check executed for this illustration.
