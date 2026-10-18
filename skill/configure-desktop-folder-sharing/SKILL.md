---
name: configure-desktop-folder-sharing
description: "Create or revise a bounded native SMB folder share on a personal desktop, reconcile published paths, recipient identities and file permissions, and verify the intended access from another computer. Use for host-side LAN sharing, not connecting to an existing share, cloud links, public access, account provisioning or file-server administration."
---

# Share one desktop folder over the local network

Deliver a usable, deliberately scoped SMB share from the intended Mac or Windows PC, plus a short connection and removal handoff. Keep the local folder, published share name, authenticated recipient, effective file rights and observed remote operation connected. A sharing switch, a visible computer or an owner's successful open is not recipient-side acceptance.

Use the operating system's existing supported sharing facility on an already configured personal desktop and an existing trusted local network. This guide does not install a server, configure a NAS, join a domain, provision accounts, expose SMB to the internet, open router ports, set up guest access or redesign network/security policy. Managed devices and unusual enterprise requirements belong with their responsible administrator.

[Connect an existing network share](../connect-network-file-share/SKILL.md) handles the client-side connection after a share exists. [Shared-link access verification](../shared-link-access-verification/SKILL.md) handles a cloud service's item grants. [Upload-only file requests](../configure-file-request-intake/SKILL.md) collect submissions without ordinary folder browsing. This workflow creates or changes the desktop's published resource; it does not migrate files, configure synchronization or establish a backup.

## Establish the sharing contract

Resolve the material choices from the request and authorized settings:

- Host computer, OS/version, owner and available authorized administrative access
- Exact local folder and underlying volume, proposed share name, and any existing share that already publishes it
- Named recipient people and their existing accounts recognized by the host, with required read or edit capability
- Whether the approved content includes later files placed in this folder, and any subfolder exclusions
- Intended client computer/session, existing network, and whether an actual remote check is requested and available
- Existing shares, connected users, open work and local permissions that must survive
- Requested final state: prepared proposal, active reusable share, or a bounded temporary share with an owner-controlled removal plan

Ask only for an unresolved choice that changes access or usefulness. Do not substitute Everyone, an administrator login or an anonymous connection for a missing recipient identity. Similar display names on two computers do not establish the same security principal. A recipient's email address is not automatically a valid local host account.

Choose an ordinary resident folder whose contents and ownership are understood. Do not publish an entire home directory or drive merely because the requested files are inside it. If the proposed folder includes unrelated private files, resolve a smaller existing folder or separately approved copy before sharing. Do not silently move originals.

Inspect relevant nested folders, shortcuts, symlinks, junctions, mounted volumes and cloud placeholders. Record which material the share would actually expose. A selected parent is not a reliable exclusion mechanism, and online-only content may not behave like resident files through another user's SMB session. Hold unresolved out-of-scope targets rather than following them, repairing cloud residency or sharing a larger ancestor. Live databases, application libraries and concurrent editing need application-specific storage support; this workflow does not certify them.

The host must be present, awake enough to serve files and connected when clients use it. A local-network share is not an internet-accessible link or an independent offline copy. Explain that practical dependency without changing sleep, wake, VPN or network settings.

## 1. Inspect the host boundary before activation

Read the relevant current sharing state before making the new folder reachable. Capture only the small baseline needed to preserve it:

- Existing published names and their exact local paths
- Whether the sharing service and SMB are already active
- Relevant account eligibility, guest/public access and broad group grants
- The selected folder's ownership, explicit/inherited permissions and known child exceptions
- Existing network profile/firewall state and whether the intended client already has a supported route
- Known active use that a service or permission change could interrupt

Inspect rather than infer. A Share menu may open cloud sharing or a one-time send flow instead of native network sharing. On Windows, Microsoft documents that the [Remove access menu can appear even for unshared items](https://support.microsoft.com/en-us/windows/experience/connectivity-networking/file-sharing-over-a-network-in-windows). Neither that label nor a folder icon proves the actual published state. A supported share inventory can distinguish name and path; Microsoft's [Get-SmbShare reference](https://learn.microsoft.com/en-us/powershell/module/smbshare/get-smbshare) describes those properties. Use an available authorized read-only view, not a downloaded administration script.

If file sharing is off, inspect what turning it on would expose in addition to the new folder. Apple's [file-sharing guide](https://support.apple.com/guide/mac-help/set-up-file-sharing-on-mac-mh17131/mac) documents automatically shared Public folders and broader access for administrator accounts. Do not promise that enabling the service exposes only the folder just added. Keep any incompatible existing publication inactive until its exact treatment is authorized. Do not remove other people's shares as incidental cleanup.

Preserve security controls. Microsoft's [SMB traffic guidance](https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-secure-traffic) recommends blocking internet-facing SMB. Do not add port forwarding, tunnels or public firewall exposure. Keep password-protected access, SMB signing and encryption requirements intact; do not enable SMB1, insecure guest fallback or disable the firewall to get a successful connection. Microsoft's [guest-logon guidance](https://learn.microsoft.com/en-us/windows-server/storage/file-server/enable-insecure-guest-logons-smb2-and-smb3) explains the missing authentication and signing/encryption protections of guest access.

A missing network route is a prerequisite to resolve, not permission to reclassify an unfamiliar network as trusted. If an OS prompt proposes discovery, firewall or profile changes, inspect the exact affected network and scope and pause for the required security-setting decision. Do not apply a troubleshooting checklist's broad changes to every computer.

## 2. Separate file grants, service access and credentials

Before any share or permission change, establish approval for the exact folder/data, recipients and capabilities, including the ongoing exposure of future contents if applicable. A request to explain or prepare settings does not authorize activation. Ordinary file-sharing changes already specifically approved do not need an extra confirmation merely because they are being verified.

Enabling the host's network-sharing service, enabling an account's SMB authentication capability, creating/materially expanding other persistent access, or changing security-sensitive network/system settings requires its applicable action-time confirmation. State the host, identities, reachable resources and material effects together before acting. Do not treat a folder grant as approval for broader host access.

If activation would make existing Public folders, other shares or additional accounts reachable, disclose that exact scope. If the exposed state cannot be established, hold activation. A safe sequence must not briefly publish broader data and tighten it afterward. Where the interface cannot stage a restricted configuration before enabling the service, resolve that limitation before turning it on.

Use an existing non-administrator recipient account appropriate to the requested scope. If no suitable identity exists, return the account prerequisite. Do not create a local user, reset a password, change group membership or hand out the owner's login as part of folder sharing.

Leave passwords and protected credential submissions to the user through the supported secure handoff. Never read stored passwords, invent a shared password, place credentials in an SMB URL, or include them in the handoff. The client user should authenticate with the approved identity through their own authorized session; do not borrow somebody else's session.

On macOS, enabling an account for Windows file sharing can require its password. Apple's [Mac-to-Windows guidance](https://support.apple.com/guide/mac-help/share-mac-files-with-windows-users-mchlp1657/mac) warns that such passwords may be retained less securely. Disclose that effect before enabling the account and hand credential entry/submission to its owner. A request to share files is not permission to reset an old account's password if the product suggests that as a fix.

## 3. Configure the smallest supported native share

Match current official guidance to the installed version. The references here were inspected on 2026-10-18; use the visible supported controls instead of guessing a missing dialog or running undocumented commands. Apply only the host's branch.

### macOS host

Open System Settings → General → Sharing and inspect File Sharing's details. Add or select the exact folder in Shared Folders, then resolve the named existing users and required per-folder rights. Read Only and Read & Write are different grants; do not use Write Only (Drop Box) for a browsing requirement. Preserve unrelated shared folders and users.

Review the folder's relevant advanced options, especially guest access, encrypted-connection requirements and backup-destination status. Do not enable all-user full-disk access or Time Machine serving for an ordinary folder. If an existing broad grant conflicts with the required audience, identify the exact change and obtain its scope approval before proceeding.

Use the Options pane for the approved SMB state and only the intended eligible account. Apple's [SMB setup guide](https://support.apple.com/en-gb/guide/mac-help/mh14107/27/mac/27) distinguishes the protocol switch from per-account Windows File Sharing eligibility. Those controls and the folder's permission list are not interchangeable. Complete any protected steps through the user handoff, then reopen the settings.

For file-level uncertainty, inspect Finder → Get Info → Sharing & Permissions on the selected items. Apple's [permission guide](https://support.apple.com/guide/mac-help/change-permissions-for-files-folders-or-disks-mchlp1203/mac) describes per-item settings and the separate Apply to enclosed items operation. Do not recursively replace permissions, change ownership or flatten child exceptions merely because one child is denied. Resolve only the actual intended change, including its local-user effects.

### Windows host

Use the selected folder's native network-sharing route, such as File Explorer → Show more options → Give access to → Specific people where the installed version offers it. Choose the already resolved host-recognized account and requested capability. Do not use the ordinary Share button's OneDrive/email destination as a substitute.

Inspect the folder's Properties sharing and security views. Record the resulting network share name, local path and permissions; do not assume the share name equals the folder's display name. If an existing publication already serves the right path, revise it only within scope rather than creating another access route.

Windows has distinct share permissions and filesystem permissions. Microsoft's [access-control overview](https://learn.microsoft.com/en-us/windows/security/identity-protection/access-control/access-control) explains their separate settings, security principals, groups and inheritance. Inspect both for the intended account and selected child items. A read grant in one panel is not a complete effective-access analysis. Where supported, use the native effective-access view as supplementary evidence and preserve its limits.

Do not add Everyone with Full Control to bypass a denial, blanket-deny a broad group, remove inherited entries, take ownership or recursively reset ACLs. Group membership and inherited entries can matter; do not reduce their interaction to one selected person's displayed row. If the available UI cannot establish the intended bounded rights, hold the change for the responsible owner rather than applying an arbitrary permissions recipe.

Do not enable offline caching, administrative shares, Remote Desktop, discovery services or account permissions as convenience additions. Keep the request about the one published folder.

### Read back the publication

After saving, reopen the actual host configuration. Verify the exact name-to-path mapping, intended account identities and capabilities, SMB/service state and any approved exposure-related option. Check that unrelated share records and local permissions were preserved. A successful save response is not this readback.

Derive the connection address from the host's actual published state. Keep the host address, share name and subfolder distinct. Return a verified UNC or SMB route suitable for the client, without credentials. A friendly machine label, guessed IP address or remembered address from another network is insufficient.

After a timeout, inspect the existing share before repeating creation. If the name exists with a different path or the folder is already published under another name, reconcile that state first. Do not create multiple names until one happens to work.

## 4. Verify from the intended client and identity

Use the agreed second computer through its authorized session, or obtain a clearly attributed user observation. Do not claim a second-computer test from opening the folder locally on the host. A host administrator's access cannot establish a restricted recipient's experience.

Before connecting, verify the host address through the established source. Use the linked client-connection workflow when needed. Preserve current mappings and credential sessions; do not clear all saved credentials or disconnect unrelated shares to force a different identity. If the intended account cannot be established without interrupting existing work, stop at that exact prerequisite.

Use a small harmless file already approved for the recipient, preferably plain text through a nonexecuting reader. Check the intended share/subfolder and exact expected contents. A directory listing proves enumeration, not reading every file. Do not execute shared programs, enable macros or follow document links to demonstrate access.

For requested write capability, use only an approved, uniquely named, noncolliding probe in the chosen scratch subfolder:

1. Establish the actual remote identity and the probe's exact destination
2. Create the agreed harmless content without overwriting an existing item
3. Close the file, then reopen it through the client route and confirm its contents
4. Inspect that exact item on the host, binding the remote operation to the intended local folder

Creation does not prove replacement, deletion, atomic application saves or safe concurrent editing. Exercise those only if the task actually requires them and the specific disposable effects are approved. A read-only requirement normally uses permission inspection plus a successful read; an attempted-denial write is not mandatory. If such a negative check is requested, treat possible success as a real write, restrict it to the approved probe, and retain any unexpected result for a scoped correction.

Check a representative required child with different inherited/explicit permissions when such a child exists. Do not invent a recursive read of private contents or test unrelated accounts. If only a subset was examined, report that scope. An unknown group route prevents an exclusive-audience claim even when the intended recipient can read successfully.

Keep configuration, capability and audience evidence separate:

| Evidence | Defensible conclusion |
| --- | --- |
| Host share/path and grant readback | The intended publication and inspected permissions are saved |
| Remote connection under the identified recipient | That identity connected through the observed route |
| Exact harmless file read from the client | That file was readable at the observation time |
| Approved probe saved and read on client and host | The checked creation/read path reached the intended folder |
| Inspected relevant grants with unresolved group membership | The known grants are documented; exclusive access remains unresolved |
| Host-only open or an old cached client copy | No new recipient-side SMB access has been established |

Do not call the share usable when only a cached/offline copy opened. Use the exact live network route and current host evidence. A controlled reconnect can add evidence when requested and safe, after open work is saved; a reboot, network interruption or forced sign-out is not required.

## 5. Recover and remove access without destroying work

Use the failure boundary:

- **Host/path unavailable:** confirm the selected host, current address, service state and expected local network; do not scan other hosts or weaken network controls
- **Authentication rejected:** preserve the intended account and exact error; hand protected correction to the user and avoid repeated guesses, guest fallback or another person's credentials
- **Share opens but a required child is denied:** compare that child's permissions and identity; do not grant the whole volume or erase inheritance to fix one item
- **Unexpected broader access:** stop further sharing/setup actions and report the exact known exposure; apply only an authorized scoped containment change, preserving unrelated users' work
- **Probe outcome uncertain:** inspect its exact client/host path before retrying; a filename alone does not prove complete contents
- **Folder moved, volume missing or a name reused:** hold the stale publication rather than pointing it at a convenient replacement
- **Concurrent settings change:** reconcile each intended delta with the live state; never restore an entire earlier share or ACL list over someone else's new work

Plan unsharing separately from deleting the folder. Removing this published share should preserve its contents and required local access. Check for active use before a change that could sever sessions or writes. Where available, an authorized read-only open-file view can help; Microsoft's [SMB open-file reference](https://learn.microsoft.com/en-us/powershell/module/smbshare/get-smbopenfile) identifies client, user and path evidence. Do not force-close handles or terminate every SMB session.

Within the approved removal plan, remove only this publication or the exact recipient grant and read back the result. Do not stop the whole host's file-sharing service while unrelated shares still depend on it. On Mac, if retiring newly enabled Windows-sharing account eligibility is also authorized, deselect only that account's checkbox through the supported route; merely hiding the folder or switching off sharing is not equivalent to retiring that credential-related state. Keep existing account eligibility needed by other shares.

A removed share name does not prove the same folder is unreachable through another published ancestor/name, existing local rights, or copies already obtained. Record those limits and do not delete downloaded copies or revoke unrelated grants. If actual revocation of an existing session is required, obtain a scoped interruption decision and verify the supported result; a settings screenshot alone does not establish it.

Network-file deletion may bypass ordinary local Trash/Recycle Bin recovery. Keep probe cleanup separate: delete only the exact authorized probe with known recovery semantics, obtain action-time confirmation for irreversible deletion, or leave its location in the handoff. Do not delete the share's real folder as rollback.

## Deliver and accept the result

Return a concise private record:

- Host, local folder/volume, published name and verified client address
- Intended recipient account identities and requested capability
- Saved publication, relevant permission/exposure state and actual changes
- Client-side checks with identity, file scope, time and observed versus user-reported evidence
- Unverified operations or audience routes, retained probe and exact blocker if any
- How to connect, the host-availability dependency, and how to stop this share without deleting its files

Send access instructions to recipients only when that communication is authorized. Keep credentials, unrelated share inventories and private paths out of broader-facing reports. Do not create a recurring monitoring job or promise automatic expiry from a written removal date.

Acceptance requires the right published path, bounded authorized rights, preserved unrelated state and the requested level of remote-use evidence. A preparation-only task can finish with a complete proposed configuration and held activation. A saved share without the required recipient-side check is configured but unverified. No small setup establishes security certification, uninterrupted availability, file backup or reliable multi-user application editing.

Stop when the requested state and evidence are established, a supported prerequisite cannot be met, or a protected user action/new authorization is required. Repeating the same failed connection or broadening access is not progress.

## Fictional, unexecuted illustration

A fictional household wants one existing Mac folder of workshop instructions readable from a Windows laptop through an already established non-administrator host account. The user requests a reusable share and a harmless read check; no writes or new accounts are requested.

The paper inspection finds file sharing off and existing Public-folder entries. The proposed workflow would identify what activation exposes and hold until that scope is resolved, rather than claiming only the new folder will appear. If Windows-sharing account activation is needed, its credential-storage effect would be disclosed for action-time confirmation and private user entry.

After an authorized restricted setup, the proposed readback would bind the published name to the exact local folder and inspect required child permissions. A host-owner preview would not complete the client check. The Windows user would connect with the intended account and read the approved text file; a cached local copy would not count. A denied child would remain unresolved without granting broader access. The removal instructions would distinguish unsharing the folder, retaining its files and retiring separately approved account eligibility.

This original illustration is fictional and unexecuted. No computer, network, account, credential, share, permission, file, connection, application or security setting was accessed, changed or tested for it. The guide describes later authorized work, not observed implementation results.

