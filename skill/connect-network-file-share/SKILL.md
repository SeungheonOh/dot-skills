---
name: connect-network-file-share
description: "Connect an existing authorized SMB file share to a desktop through its native client, preserving server identity, account context and existing mappings, then verify the requested folder access and saved reconnection behavior. Use for a working client-side share connection, not creating shares, changing permissions, copying collections, configuring backups or weakening network security."
---

# Connect an existing network file share

Deliver a usable connection to the intended shared folder, with an exact remote-to-local path mapping, observed access result and clear reconnection instructions. Keep the server's existing access rules intact. A visible drive letter, remembered server or successful sign-in alone does not establish that the requested folder is usable.

Use an already configured SMB server or network-attached storage device and the operating system's existing supported client. This workflow does not provision a server, enable sharing on another computer, expose storage to the internet, configure a VPN, join a domain or administer credentials. It does not implement a custom mount service or login script.

A mapped share is a route to remote files. It does not establish an independent copy, retained versions or offline availability. Use [backup setup](../configure-versioned-file-backup/SKILL.md) for a separately authorized capture job and [cloud-file conflict resolution](../resolve-cloud-file-conflicts/SKILL.md) for an existing synchronization conflict. [Shared-link access verification](../shared-link-access-verification/SKILL.md) concerns a service's item-sharing relationship rather than a desktop network mount.

## Establish the endpoint and intended use

Resolve these from the request and available authorized records:

- The user's actual computer, OS and normal desktop account/session
- The server address and exact share name from the user, administrator or other trusted existing record
- Any required subfolder, intended account identity and known organization/domain context
- Whether the user needs a one-session connection, a convenient saved location, or reconnection at sign-in
- Whether acceptance requires listing a folder, reading a selected file, or a narrowly scoped write check
- Existing connections that must remain available, open documents and any required drive letter

Do not require an exhaustive network inventory. A verified endpoint, intended session and simple read requirement are enough to begin. If the share address or identity is missing, prepare the next steps and ask for that specific information; do not scan the local network or guess server names.

Keep the remote endpoint separate from its local presentation. A Windows UNC path such as `\\server.example.test\TeamFiles\Reference` contains a server, share and optional subfolder. A macOS SMB address such as `smb://server.example.test/TeamFiles` selects a server/share; record the required subfolder separately when navigating after connection. These are fictional path shapes, not destinations to contact. Preserve the actual spelling and supported escaping rather than constructing an address from a display label.

Confirm the destination before attempting connection, not just before typing a password. [Microsoft's SMB security guidance](https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-secure-traffic) describes credential-harvesting risks from malicious servers. Do not open an unsolicited SMB link, substitute a lookalike hostname, or send an internal hostname to a public diagnostic service. A connection attempt can involve authentication; it is not merely passive inspection of text.

## Set the action and authentication boundary

Use the user's explicit connection request for the named server and current account. A request for instructions ends with instructions; it does not authorize operating the computer. A request to connect does not authorize reading unrelated shared content, uploading files or altering the server's access rules.

Use an existing authorized authenticated session where supported. Never read saved passwords, extract authentication material, place secrets in paths or commands, or include credentials in a report. Let the user complete new credential entry and submission through the supported secure handoff. If the prompted server or account differs from the established target, stop before entry. Do not ask the user to paste a password into chat.

Distinguish four choices:

1. **Connect now:** establish the named session using the authorized identity
2. **Remember the location:** retain an ordinary path/favorite or drive mapping when requested
3. **Reconnect automatically:** configure only the requested supported client behavior; if this configures existing credentials for ongoing access or otherwise creates or materially expands persistent access, obtain action-time confirmation before enabling it
4. **Remember or provision authentication:** obtain the required specific approval and user-controlled credential handoff; obtain action-time confirmation for newly created or materially expanded persistent access

Do not silently select “remember password,” change an existing credential entry, enroll a new account or enable a login task because it would make reconnection convenient. A drive label or favorite is not permission to save authentication information.

Inspect existing network context without changing it. If a managed network or already configured VPN is required but unavailable, report that prerequisite. Do not switch networks, change a network profile, turn on discovery, add firewall exceptions, modify DNS/proxy settings, enable guest fallback, downgrade SMB, disable signing/encryption or bypass a security warning as an incidental connection fix. [Microsoft's guest-logon guidance](https://learn.microsoft.com/en-us/windows-server/storage/file-server/enable-insecure-guest-logons-smb2-and-smb3) explains that guest access lacks normal SMB signing/encryption protections. A server requiring weaker settings needs its responsible owner; successful access is not a reason to weaken the client.

## 1. Inspect existing connections and preserve their use

Work in the desktop session that will use the share. A connection established by another account, an elevated tool, remote session or background service is not evidence that the user's ordinary application can see it. Microsoft documents [mapped-drive visibility differences between logon contexts](https://learn.microsoft.com/en-us/troubleshoot/windows-client/networking/mapped-drives-not-available-from-elevated-command); verify the actual consumer rather than changing UAC or registry settings. Do not elevate merely because a normal connection fails.

Record relevant current mappings or mounts, their remote targets and requested persistence settings where visible. Include disconnected remembered mappings: a drive letter that looks unused may still be reserved. On macOS, do not infer a server's identity from a mounted volume's short display name or assume its local mount path before inspecting it.

Choose the smallest change:

- If the intended share is already connected under the intended identity, reuse and verify it rather than creating a duplicate
- If a requested drive letter already maps to that exact target, inspect its current usability and saved behavior
- If it points elsewhere, preserve it; use another genuinely available letter if acceptable or ask about the specific replacement
- If the server is already connected under a different identity, preserve the existing connection and determine whether switching would interrupt work
- If only a stale shortcut or favorite exists, treat it as a remembered address, not a live connection

Do not disconnect all network drives, clear the credential store, remove old mappings wholesale or terminate applications to make one connection succeed. If a credential/session conflict is reported, keep the exact message and relevant connection identities. A different hostname or IP address is not an approved workaround for an identity or policy conflict.

Before an authorized replacement or disconnect, identify open work using that connection and preserve unsaved changes through the application's supported workflow. If usage is unknown or the operating system warns that files are open, stop rather than forcing disconnection. Keep any necessary replacement plan scoped to the one verified mapping.

## 2. Connect through the native interface

Consult current official instructions for the actual platform and visible controls. Keep the live procedure small; do not run every platform's branch.

### macOS

Use Finder's Go > Connect to Server with the verified SMB address. [Apple's connection instructions](https://support.apple.com/en-sg/guide/mac-help/mchlp1140/mac) describe this route and selecting a server volume or shared folder; [its Windows-server guide](https://support.apple.com/guide/mac-help/connect-to-a-windows-computer-from-a-mac-mchlp1660/mac) documents the SMB server/share address form.

Use the agreed identity and only the selected share. Do not accept Guest merely because it avoids a prompt, select every offered volume, or change another computer's sharing settings. If authentication needs user input, pause at the secure handoff and resume after its outcome is known.

After connection, inspect the actual mounted target and navigate to the requested subfolder. If a requested favorite or sidebar entry is appropriate, save that location and read it back. A recent-server entry, favorite and automatically mounted login item are different states; adding one does not prove another. Do not introduce a login item or script under a request for a favorite.

### Windows

For a drive-letter mapping, use File Explorer's This PC > Map network drive through the menu available in that Windows version. Choose the verified available letter and enter the exact UNC target. [Microsoft's mapping instructions](https://support.microsoft.com/en-us/windows/experience/connectivity-networking/file-sharing-over-a-network-in-windows) distinguish selecting a drive letter from the optional Reconnect at sign-in setting.

Set reconnection only as requested and inspect any credential-choice controls before finishing. A direct UNC location can be sufficient when the user wants access without a drive letter; do not add a mapping unnecessarily. Use the normal desktop session and the authorized identity.

If the interface reports a remembered mapping or a conflicting existing connection, inspect that target before retrying. [Microsoft's network-connection reference](https://learn.microsoft.com/en-us/windows/win32/api/winnetwk/nf-winnetwk-wnetaddconnection2w) distinguishes occupied local devices, remembered connections, unavailable paths and denied access. Preserve the actual error instead of treating every failure as an incorrect password. The reference is background for interpreting these states, not an instruction to build or run an API client.

For either platform, after a timeout or ambiguous response inspect current mounts/mappings and the intended target before another attempt. The connection may already exist. Do not create alternate mappings until one happens to open.

## 3. Verify the actual requested access

Keep a compact observation record: time, computer/session, server/share, local entry, requested subfolder, action, outcome and evidence source. Redact internal paths in any wider-facing summary. Do not collect a recursive directory listing to prove a single folder is usable.

Verify each required boundary separately:

| Observation | Supported conclusion | What remains unproved |
| --- | --- | --- |
| Mapping/favorite is saved with the right target | The address/configuration was retained | A live connection or file access |
| Share is connected and requested folder lists | That folder can be enumerated in this session | Reading every file, writing, or other folders |
| An authorized existing file opens through a safe reader | That file is readable through the checked route | Application editing, write rights or future availability |
| An approved scratch-file write closes and independently reads back | The checked write/read path worked at that time | Replacing existing files, deletion rights or reliable concurrent editing |
| A requested normal reconnect later succeeds | Reconnection worked under those observed conditions | All later sessions, networks or unattended operation |

Start with a selected existing harmless file when read access is the goal. Use a nonexecuting viewer or safe content read; do not run scripts, installers, macros, external links or executable content from the share. Opening an editable file can create lock files or auto-save changes, so use a read-only route when no write is authorized.

Only perform a write check if its exact location, harmless content and effects are authorized. Create one uniquely named noncolliding probe in the approved scratch folder using a supported no-overwrite operation. Close it, read it back through the mapped route and compare the expected content. Do not use a real document as the probe or infer replacement/delete rights from creating a new file. If an outcome is uncertain, inspect the exact probe before retrying.

Do not assume deleting a network file uses the local Recycle Bin or Trash. Inspect actual recovery semantics; irreversible cleanup requires action-time confirmation even for a test file. If cleanup is not authorized, retain the named probe and report it. Never delete a similarly named pre-existing item.

When the real requirement includes a particular application, verify the approved operation in that same ordinary application/session if available and authorized. A file-browser read is not an application write check, and connection success does not certify that a database, photo library or project supports direct editing on SMB. Leave unsupported application storage needs for that application's documented workflow.

## 4. Check saved behavior without disrupting the user

Reopen the saved mapping or favorite and inspect its target and requested reconnection setting. Keep “saved,” “connected now” and “reconnected after a session change” distinct.

If a safe disconnect/reconnect is requested and no open work depends on the connection, use the supported control for that exact connection and repeat the scoped access check. Preserve its intended remembered state. Do not force an unmount, restart the computer, sign the user out, interrupt a call or unplug the network merely to demonstrate persistence.

For automatic sign-in reconnection, report the configured setting and whether a real later sign-in has been observed. If that observation is required, arrange the user-approved observation opportunity; leave it pending until evidence arrives. Do not turn a manual reopen into proof of automatic startup. A disconnected remembered drive can reflect current server/network availability; it is not by itself proof that the saved target is wrong.

Do not enable offline caching, sync or copying as a substitute for an unavailable server. If the user needs offline work, that is a separate data-selection and storage decision.

## 5. Recover at the evidenced boundary

- **Wrong or uncertain endpoint:** stop further access and authentication; verify the address through the established trusted source before reconnecting
- **Server or path unavailable:** record the exact target and error, check only the relevant existing network/server evidence, and identify the owner-side prerequisite; do not scan hosts or open ports
- **Authentication rejected:** preserve the intended identity and visible error, allow the appropriate user-controlled correction, and avoid repeated password attempts or lockout-provoking retries
- **Share connects but a child folder is denied:** keep the successful connection separate from the folder-specific failure; do not grant broader access or copy around the restriction
- **Remembered letter or session conflict:** preserve the working mappings, identify the actual collision, and ask only about the specific interruption or replacement that remains necessary
- **Connection lost during a write:** preserve any local unsaved buffer and inspect the exact remote file before retrying; neither an error nor a visible filename proves which bytes were committed
- **Unexpected data or audience:** stop browsing or writing and verify the target; do not delete evidence or alter sharing as an improvised cleanup

When abandoning the new connection, disconnect or remove only the scoped client entry within the authorized recovery plan, after preserving open work. Read back the final mapping state. Disconnecting does not revoke server permissions, erase retained credentials, undo prior uploads or delete remote files. Do not alter those separate resources under the name of rollback.

## Deliver and accept the result

Return a concise private handoff with the verified server/share, local access route, intended session/account context, observed folder/file capability, saved reconnection choice, any retained probe and remaining blocker. Include how to reconnect and safely disconnect using the existing interface. Save a separate connection record only if useful or requested; do not create configuration files containing credentials.

Acceptance requires the exact intended target and requested client state, an observed access check appropriate to the task, preservation of unrelated mappings, and honest distinction between configured and observed repetition. If credentials, server availability or a policy decision is still missing, deliver the prepared setup and precise held step. Do not call an untested mapping working, a readable folder writable, or a mapped share backed up.

## Fictional, unexecuted illustration

A fictional user wants read access to a team's reference folder from their Windows desktop and asks for reconnection at sign-in. The trusted share address is already supplied. Their preferred drive letter is a disconnected remembered mapping to a different server, and the user permits another available letter. No write check or credential saving is requested.

The proposed workflow would preserve the old mapping, connect the exact new target under the intended account using the permitted alternative letter, and read back the requested reconnection setting. It would list the reference folder and safely read one approved plain-text document. A successful current connection would support present read access; automatic reconnection would remain unobserved until a real later sign-in. A password prompt would be handed to the user without copying or retaining its contents.

This invented illustration was not executed. No server was contacted, credential entered, drive mapped, file opened, setting changed, test file created, session interrupted or network reconfigured.

