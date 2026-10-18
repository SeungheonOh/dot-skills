---
name: create-local-virtual-machine
description: "Create one new desktop virtual machine from a supported operating-system installer in an existing hypervisor, bind installation to a fresh virtual disk, and verify independent startup and retained guest work. Use for a usable local guest system, not Dev Containers, physical OS installation, imported appliances, cloud instances or host virtualization changes."
---

# Create a local guest system that starts again

Deliver one identifiable virtual machine (VM), its installed guest operating system and a concise start/shutdown handoff. Carry the selected host, installation source, virtual hardware, storage and permitted host access through creation and a real stop/start check. Reaching an installer desktop or resuming a saved session does not establish that the installed system boots from its own disk.

Keep this workflow to a new VM with a fresh ordinary file-backed virtual disk in an already installed, supported desktop hypervisor. It does not import an appliance, clone or repair an existing VM, operate a production server, enable nested virtualization, expose raw physical disks, or build an environment for executing suspicious software. A VM is not a safety guarantee for untrusted programs.

[Dev Container configuration](../configure-development-container/SKILL.md) produces a project development environment with its own build and mount lifecycle. [Bootable installation media](../create-bootable-installation-media/SKILL.md) produces a removable installer for a physical target. Neither result is this independently bootable guest system. If the user only wants instructions extracted from a supplied manual, use [manual-to-task preparation](../manual-to-task-checklist/SKILL.md) instead of claiming a configured VM.

## Establish the guest contract

Resolve these facts from the request, existing settings and official sources before allocating resources:

- The purpose and one ordinary activity that will demonstrate usability, such as creating and reopening a small guest-local document
- Whether the request covers a plan or actual VM creation and OS installation; the selected host and current operator access
- Host architecture and OS, installed hypervisor/version, available memory and CPU capacity, free space on the intended VM storage volume, and other work that must remain usable
- Selected guest OS release, architecture and edition; exact installation image and its official provenance; any applicable license or activation requirement
- New VM name and approved storage folder, with no reuse of existing machine files or disks
- Guest network needs, permitted update/download destinations and budget, and any specifically requested host-folder or peripheral access
- User-controlled guest-account setup, required credential handoff, and the agreed final state: running or normally shut down

Ask only for a missing choice that changes the route. A host's marketing name does not settle its processor architecture. A disk-size recommendation is not evidence that the host has that much free storage. If the installed hypervisor cannot support the selected host/guest combination, return that precise compatibility gap; do not substitute CPU emulation, change firmware settings or install another hypervisor as an incidental fix.

Use current official documentation for the actual versions. The product-specific references below describe Oracle VirtualBox 7.2, not a universal interface. Its [host/guest combinations](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/Introduction.html) distinguish x86 and Arm platforms and support levels. For another hypervisor, establish its equivalent storage, boot and host-access contract before operating it. A dropdown entry or a bootable image alone does not establish full guest support.

## 1. Establish the installation source and authority

Start from the OS publisher's official image and installation guidance for the selected release and architecture. Record the supplied or downloaded image's source and identity. Where the publisher provides an authenticated checksum or signature for that exact image, use the supported verification route; a hash calculated only from the local file does not authenticate its publisher. Keep the source separate from the new writable guest disk.

Confirm that the image is an OS installer, not a preconfigured appliance with unknown accounts, startup services or attached-disk expectations. Do not boot a downloaded VM or an arbitrary image merely because the hypervisor can open it. Hold an unverified or unsupported source rather than modifying it to bypass its requirements.

Permission to prepare a plan is not permission to execute an installer. For actual setup, obtain the applicable installation approval and disclose any new agreement before its acceptance. The VM software does not supply a guest OS license. Purchases, activation purchases, account subscriptions and organization enrollment are separate decisions.

Use an attended installation route unless the user separately requests and authorizes automation. In the [VirtualBox 7.2 creation flow](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/create-vm.html), an eligible ISO can select unattended installation by default; deselect “Install OS Using Unattended Installation” for this route. Do not leave a generated answer file containing passwords or product keys, accept a default credential, or copy secrets into a command to avoid a handoff.

When setup requires creating or entering a password, product key, recovery material or another protected credential, pause for the supported secure owner-controlled step before entry. Record only completion or the remaining prerequisite. Do not invent a reusable login, save a secret in the handoff, capture it in screenshots, or enable automatic login for convenience. Apply separate approval requirements to persistent account access and unexpected permissions.

## 2. Allocate a new machine and identify its disk

Choose a unique machine name and a private, approved folder on storage with enough available space for the guest installation, expected work and operational headroom. Keep it out of an automatically shared or uploaded folder unless that destination and its data exposure are explicitly authorized. Check the proposed path for existing contents before creation; do not overwrite a same-named machine or reuse a familiar disk.

Choose memory and processor allocations that meet the guest's documented needs while leaving capacity for the host's existing work. Treat a wizard's suggestions as starting values, not measured performance guarantees. Defer creation if there is no feasible resource budget. Do not stop other people's workloads, change host boot options or disable security features to make room.

Create a fresh file-backed disk with an explicit virtual capacity, backing-file location and allocation mode. In VirtualBox, fixed-size and dynamically allocated images have different host-space behavior: dynamic images grow as previously unused sectors are written. A large virtual capacity is not reserved host space. Budget current files, future growth and any separately requested snapshots; do not equate the size shown inside the guest with free host space. See [virtual storage](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/storage.html).

Record enough identity to distinguish the VM and its disk from similarly named resources: native VM identifier where available, settings location, disk path/identifier, capacity and controller attachment. Inspect the newly saved configuration before the first boot. The permitted storage set is the new disk plus the intended installer as virtual optical media. Exclude raw disks, existing guest disks, host storage devices and network storage targets.

For VirtualBox, the [VM folder reference](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/Troubleshooting.html) distinguishes machine settings, disk images, logs and optional snapshot files. Record actual locations rather than assuming everything is next to the visible settings file. Do not rename or move backing files outside the hypervisor while it owns them.

## 3. Review guest access before its first start

Inspect all adapters and integration settings on this VM. Do not assume that a clean machine name means a disconnected or private environment. Apply the narrow agreed access; obtain the required action-time approval for security-sensitive network or host-access changes. Keep host-wide settings and other VMs untouched.

Make the network choice explicit:

| Intended use | Bounded configuration decision |
| --- | --- |
| Offline installation and local work | Use the hypervisor's supported disconnected-adapter state; inspect every adapter |
| Ordinary approved internet access | Select the supported outbound route and record its scope; inspect forwarding rules |
| Host/LAN services, inter-VM labs or remote access | Treat as a separate network design and authorization boundary; do not improvise it during setup |

VirtualBox [networking documentation](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/networkingdetails.html) distinguishes disconnected, NAT, NAT Network, bridged, internal and host-only modes. NAT permits guest-initiated traffic, including access toward the host/LAN; it is not offline isolation. Host-only includes the host. A disconnected network adapter does not disable other host integrations. Do not add port forwarding, bridging or a remote-console listener just to make an installation check easier.

Keep shared clipboard, drag-and-drop, host-folder shares, automatic USB capture, webcam/microphone passthrough and remote access off unless the requested activity requires an approved subset. Inspect existing defaults and effective settings rather than relying on their names. For a required share, resolve its exact host path, recipient guest, read/write scope and duration; never expose the home directory or credential stores as a shortcut.

Guest integration packages are additional software with their own supported installation path. Install only the needed, authorized package for the selected host/hypervisor/guest combination. Its presence does not authorize every integration feature. VirtualBox [Guest Additions](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/guestadditions.html) can provide shared folders independently of guest networking; those folders default to read/write when created. Confirm the actual share mode before exposing data. If integration is optional and unavailable, finish a usable basic guest with the limitation recorded.

## 4. Install only inside the identified guest

Open the chosen VM console and verify its identity before sending input. Establish the supported method to release keyboard/mouse capture back to the host. Keep installation in a window until the operator can reliably tell host controls from guest controls. Avoid global key combinations whose recipient is unclear; use the hypervisor's documented guest-input controls when needed.

Boot the verified installer and follow the OS publisher's version-specific instructions. Confirm the actual release/edition, language and ordinary installation choices. Do not turn a local guest setup into directory enrollment, account migration, paid services or an unattended deployment. Pause at protected credential or new agreement steps rather than selecting convenient defaults.

Before any partitioning, formatting or “erase disk” confirmation, reconcile the disk displayed by the guest installer with the new virtual disk's capacity and attachment. Verify the full attached storage set on the host side. A guest's “Disk 0” or “erase disk” label does not identify the backing resource by itself. Obtain the required exact-target confirmation, explaining that the action concerns the newly created virtual disk. If the installer sees unexpected disks or pre-existing partitions, stop and resolve identity before proceeding.

Observe installation completion through the existing console. A remote tool timeout is not evidence that installation stopped. Reconnect and inspect the current VM state and installer before retrying. Do not start a duplicate machine, rerun formatting or discard the first disk because a progress response is missing.

At the documented end of installation, remove the installer from the guest's virtual optical drive using the supported control; preserve the source image on the host. Do not eject a physical host device or detach the installed virtual disk. If the first restart returns to an installer or live session, inspect optical-media attachment, boot selection and installed-disk evidence before repeating installation.

## 5. Prove startup and persistence at the requested level

Define a harmless, local acceptance activity before using the guest. It should exercise the user's intended basic use without importing private work, signing into unrelated services or installing an arbitrary application solely for a demonstration.

Perform these checks when authorized and observable:

1. Confirm the installed guest's reported OS release and architecture, the selected VM identity, and its actual boot from the new virtual disk with installer media detached
2. Complete the agreed basic activity and save a small, clearly named guest-local result in an ordinary persistent user folder; record what is expected on reopening
3. Save work, request normal shutdown from the guest, and observe that the VM reaches the native powered-off state
4. Start that same VM again, let the user complete any protected sign-in, and reopen the saved result; verify its content and the agreed basic activity
5. Read back the final virtual hardware, storage attachments, network and host-integration settings; resolve unexpected changes before calling setup complete

Keep startup, guest usability, persistence and network evidence separate. A visible login screen does not prove usable access. A successful web request does not establish general connectivity or absence of unintended exposure. For an offline request, configuration inspection can establish the selected controls; it does not constitute a penetration test or proof of a security boundary.

VirtualBox's [VM lifecycle guidance](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/working-with-vms.html) distinguishes saving execution state, asking the guest to shut down and forcibly powering off. Resuming a saved state is not the cold-start check above. A shutdown request may need time or fail; wait for the observed state rather than immediately forcing power off. Treat reset, forced power-off and discarding saved state as potentially lossy recovery actions requiring the applicable authority.

Do not take or restore a snapshot solely to add a green check. If the user separately asks for a baseline snapshot, use the product's supported procedure and record its included disks and state. Restoring it can lose later guest changes; it does not undo writes to host shares or external services. A same-storage snapshot is not an independent backup. Keep any [backup-coverage plan](../plan-file-backup-coverage/SKILL.md) separate from demonstrated installation success.

## Recover without discarding the first result

- **Architecture, firmware mode or guest support mismatch:** hold the install or boot check and compare the selected image and virtual hardware with current support documentation. Do not bypass guest requirements or alter host security/firmware
- **Insufficient memory or storage:** stop new writes through the supported safe control when possible, preserve existing guest files and identify the bounded resource decision. Do not erase unrelated host data or prune snapshot chains
- **No bootable disk after installation:** inspect the intended disk attachment, installation result and boot configuration. Preserve the disk; an empty-looking guest screen is not permission to recreate it
- **Installer or guest appears stuck:** establish whether it is still working, awaiting input or reporting an error. Retain the specific error and resource state; use a supported, authorized correction instead of repeated resets
- **Guest cannot use network or integration:** distinguish the declared access policy from missing drivers/software and guest configuration. Do not broaden network exposure, share a larger folder or disable host protections as a diagnostic shortcut
- **Current state is uncertain after a disconnect:** inspect the existing VM and disk identities before issuing another state-changing action. Report unknown completion honestly if observation cannot be restored
- **Disk identity conflicts or unexpected existing data:** stop before formatting or overwriting. A fresh name does not make an existing backing file disposable

Change one evidenced cause and repeat only the affected acceptance checks. Stop on a new permission boundary, unsupported prerequisite, repeated failure without new evidence or an exhausted agreed resource/time budget. Retain the incomplete VM with its exact status and next action. Removing its registration, deleting its files and restoring a snapshot are different operations; none is an automatic “undo.” Never manually delete differencing files to recover space or repair a machine.

## Deliver a usable start/shutdown handoff

Return the VM's actual saved identity and location, guest release/architecture, installation source, resource allocation, storage arrangement, approved access settings and concise instructions for opening the console and shutting down normally. Include only necessary private locators, no credentials. State which checks were observed, user-reported, unrun or blocked, and the final running/powered-off state.

Acceptance requires the intended supported guest on the newly identified disk, completion of the requested installation and basic use, independent startup and persistence evidence, and final configuration consistent with the permitted host access. If any requested check is unavailable, describe that gap rather than claiming a working installed system from a settings file or installer screen.

Stop at this bounded local guest. Exporting or uploading the VM, copying its disks to another person, enabling automatic startup, provisioning remote access, importing personal accounts and removing the installation source are separate actions. The guest can accumulate sensitive data during use; a VM image is not automatically a shareable template.

## Fictional, unexecuted illustration

A fictional user wants a new offline Linux guest in an already installed, compatible desktop hypervisor. The supplied installer has an established publisher source. The agreed result is a guest-local text file that survives a normal shutdown and start. A fresh virtual disk is selected, but the wizard also offers unattended account setup and an existing host-folder share.

The proposed route disables unattended installation, leaves the share unexposed and verifies the disconnected state of every virtual adapter. Account credentials remain an owner-controlled step. Before the installer formats anything, the operator matches its sole disk to the fresh backing file and obtains the required target confirmation.

If a paper observation says “desktop visible” while the installer ISO is still attached, the result remains ambiguous: it may be a live session. The proposed acceptance removes only that virtual optical attachment at the supported point, starts the installed guest, saves the agreed local file, shuts down normally and starts again to reopen it. A saved-state resume would not satisfy that check. If the second boot cannot be observed, the handoff retains that specific untested stage.

This illustration is original, fictional and unexecuted. No VM, guest account, installation image, disk, hypervisor, application or network was created, accessed, installed, booted or tested for it. The checks above are instructions for later authorized work, not a report of performed validation.
