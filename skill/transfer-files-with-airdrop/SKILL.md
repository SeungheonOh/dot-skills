---
name: transfer-files-with-airdrop
description: "Send a small selected set of existing files from a Mac to one nearby Apple device through AirDrop, preserve source and recipient identity, and reconcile actual received copies before retrying. Use for bounded one-time file delivery, not folder sharing, synchronization, photo-library migration, credential sharing or an offline-security guarantee."
---

# Deliver selected files to the right nearby device

Finish a one-time transfer from the intended Mac to an identified Mac, iPhone or iPad, with a short source-to-received-item record. Separate peer discovery, transfer submission, the sender's completion indication and actual recipient-side receipt. An avatar appearing nearby is not a verified recipient, and a sent badge is not proof that the recipient can find the required copy.

Use existing ordinary files selected in Finder and the native AirDrop interface. Keep originals unchanged. This guide does not select photos, export native application projects, send passwords, create shared folders, enable synchronization or migrate an entire device. Use [project packaging](../portable-project-handoff/SKILL.md) when dependencies need a reviewed archive first; an already prepared approved archive can then be one file in this transfer. Use [photo-library import](../import-photo-library-batch/SKILL.md) for catalog ingestion and [metadata-transfer review](../audit-file-metadata-transfer/SKILL.md) when non-byte preservation is the actual acceptance question.

## Establish the delivery boundary

Resolve the following from the request and available authorized evidence:

- The sending Mac/session and exact selected file paths or stable identities
- One intended recipient, their actual receiving device, and whether it is the user's own device
- Whether the request is instructions, preparation or an actual send
- The needed result: accessible copies, exact file bytes, or a specific destination/app when that matters
- Any no-cloud, no-mobile-data, metadata, confidentiality or deadline constraint
- Whether receiver-side access is available through an authorized session or only an attributed user/recipient observation

A few harmless files going to the user's identified tablet do not require an elaborate intake form. Ask only for a missing detail that changes selection, destination or delivery effects. A request to prepare files does not authorize transmission. Before sending, establish approval for these files/data and this recipient/device; a generic request to make sharing easier does not identify an audience.

Operate another person's device only with the appropriate authority. Otherwise the recipient controls their acceptance and storage choices, and their report remains attributed evidence. Do not request unrelated contact lists, account inventories or screenshots containing private notifications. Device unlocking, account passwords and other protected credentials stay with their owner through supported handoffs. Credential files, password exports and recovery material are outside this workflow.

If a user-controlled destination automatically syncs received files, inspect that relevant behavior before using it when it affects the approved destination or privacy requirement. A third-party recipient's later storage practices cannot be guaranteed from an AirDrop send. Do not promise local-only retention or change cloud settings to manufacture it.

## 1. Freeze a small, usable selection

Inspect the actual Finder selection before opening its sharing controls. For a simple batch, record names, source locations, count and enough revision/content detail to distinguish the files. Add byte sizes and digests when exact bytes are required and supported ordinary reads are available; do not impose hashing on an ordinary two-document send that only needs readable copies.

Keep these distinctions visible:

- A resident ordinary file versus a cloud placeholder, alias, symbolic link, application package or folder
- Two selected files with the same basename versus two references to the same file
- The saved file versus unsaved application edits
- A file copy versus a collaboration invitation or URL

Do not follow links into unselected material, recursively expand folders or download a whole cloud collection. If an exact requested file is not resident, establish the supported scoped download and its authority before continuing. If the source is changing, save or freeze the intended version within scope, or hold that file. Do not close applications or discard edits to obtain a stable source.

For duplicate names or existing same-name files at the destination, preserve a source-to-received mapping. A timestamp or automatic suffix is supporting context, not content identity. Resolve a noncolliding copy/name plan when the destination can be controlled; obtain approval before renaming deliverables or replacing existing files. Do not overwrite a recipient's current work as an implicit transfer retry.

Native packages and folder trees need their own supported preparation. Do not assume an app bundle or photo library can be safely treated as one ordinary document. If the user needs an unchanged archive, send the approved archive without extracting it for delivery. Receiving a ZIP is distinct from verifying its contents or executing anything inside it.

## 2. Establish the actual peer and permitted route

Match current official instructions to both devices' installed versions. Apple's [AirDrop overview for Mac](https://support.apple.com/guide/mac-help/use-airdrop-to-send-items-to-nearby-devices-mh35868/mac) documents nearby devices with Wi-Fi and Bluetooth enabled, a roughly ten-meter range, and automatic acceptance between devices already using the same Apple Account. Do not sign devices into a different account to obtain that convenience.

Have the user or recipient identify the receiving device through its own visible identity and the trusted conversation, then match the displayed peer before selecting it. If two devices have indistinguishable names, hold the send until the owner resolves which is intended. A matching nickname, silhouette or nearby position alone is inadequate. Apple's [AirDrop security description](https://support.apple.com/en-ca/guide/security/sec2261183f4/web) distinguishes contact-verified identities from device-name presentations; its older protocol account does not describe every current UI or internet-continuation behavior.

Inspect current receive/discovery state and preserve its baseline. Apple's [AirDrop privacy controls](https://support.apple.com/guide/personal-safety/secure-airdrop-ips7d84d2cdc/1.0/web/1.0) describe receiving from contacts, everyone or nobody. Prefer the existing permitted route. Contacts Only depends on the sender's relevant Apple Account contact information being known to the receiver; do not edit contacts or disclose new account identifiers merely to make the peer appear.

If receiving must be enabled or broadened, explain the exact device and exposure and obtain the applicable approval before changing that privacy/security state. Bundle the intended end-state restoration with it. Do not presume that a Mac's Everyone option expires like the iPhone/iPad's Everyone for 10 Minutes. The latter's timed reversion is documented in Apple's [iPhone and iPad procedure](https://support.apple.com/en-us/119857); still read back the actual final state rather than waiting for a timer as proof.

Wi-Fi, Bluetooth or Personal Hotspot changes may interrupt other work. Inspect the needed prerequisite rather than cycling radios. The same Apple procedure says to disconnect Personal Hotspot when it is in use. If another device depends on that connection, pause for the specific interruption decision. Do not disable a VPN, firewall, management restriction or security control, reset network settings or install a transfer utility as a workaround.

### Internet continuation is a separate constraint

Apple's current [iPhone AirDrop guide](https://support.apple.com/guide/iphone/use-airdrop-to-send-items-to-nearby-devices-iphcd8b9f0af/ios) says transfers can continue over the internet after the devices leave local range. Do not describe every AirDrop send as exclusively offline or treat moving away as cancellation. If the user requires a strictly local/no-internet path, establish a supported version-specific way to meet it before submission; when that cannot be established, hold this route and present the constraint. Do not invent a local-only switch, alter network security or choose another transmission service without authority.

### A new AirDrop code can retain a relationship

The current Mac/iPhone guidance describes a code flow for non-contacts on supported 26.2-or-later systems and a known-person relationship lasting 30 days. This is more than an inert file picker. Before completing a flow that creates that retained relationship, disclose the peer and duration and obtain action-time confirmation for the persistent-access change. A one-file send request alone does not supply that confirmation.

Use only the code generated on the intended recipient's device for this current transfer, conveyed through the trusted interaction. Do not guess, reuse a code from another conversation, expose it in a report or save it. Let the owner perform protected steps when required; do not automatically force a handoff for an otherwise supported approved action. If the observed flow differs from the documented one, stop at the discrepancy. A code does not authorize extra files or future sends.

If the user wants that newly created relationship removed afterward, establish the exact approved removal scope. Apple documents the Other Known list and Forget This Person route. Removing that relationship and restoring discoverability are separate actions; neither recalls delivered files. Do not remove unrelated contacts or known people.

## 3. Submit once through the native interface

Use Finder's selected-file sharing route to AirDrop, or the documented Finder AirDrop window. Confirm the selected count and intended peer immediately before the action that starts transmission; dragging onto a peer may itself send. Do not click candidates to discover who they are, select multiple recipients or add an unrequested test file.

For a mixed or unfamiliar batch, an already-selected harmless file may serve as a first transfer when useful. Count it as part of the requested delivery so it is not sent again with the remainder. A simple small batch can be sent together; do not impose a pilot without a real uncertainty to resolve.

On a different person's device, the recipient accepts the intended request through their own session. Same-account devices may accept automatically, so resolve the destination before submission instead of relying on a second prompt. Handle any code/access gate above before completing it. Decline or ignore unrelated incoming requests; a nearby stranger's file is not part of this task.

Record the attempt time, selected identities, peer and visible outcome. Retain relevant warnings, waiting, declined, failed or ambiguous states. Do not translate a spinner disappearing into success, repeatedly select the peer while an attempt is pending, or silently fall back to Messages, email, a shared link or a public upload.

## 4. Locate and reconcile the received copies

Inspect the receiver only through the authorized session or obtain a precise attributed observation. Apple's [receive guidance](https://support.apple.com/guide/mac-help/use-airdrop-to-send-items-to-nearby-devices-mh35868/mac) describes app-dependent placement: Downloads is possible on Mac, Files on iPhone/iPad, and some content opens or saves in an associated app. Do not claim every item lands in one universal folder.

Reconcile the original selection to the newly received items, not merely to a folder's total count. Record actual destination/app, received name or native item locator, observed content/version and final disposition. A pre-existing same-name file cannot prove this attempt arrived. Keep multiple selected occurrences distinct unless the user approved collapsing them.

Use the checks that match the delivery contract:

| Check | Evidence and limit |
| --- | --- |
| Requested peer | Device identity matches the established recipient; visibility alone is insufficient |
| Requested membership | Every selected file maps to a received item or a named unresolved state |
| Readable copies | Safely open the relevant received documents or representative agreed subset; identify what was actually checked |
| Exact bytes, when required | Compare source and received ordinary-file bytes/digests through supported access; thumbnails, names and sizes alone do not prove equality |
| Requested usable location | The recipient can find the actual saved copy at the agreed route, rather than only seeing a transient preview |
| Preserved source | Original files remain present and unchanged to the checked scope; sending does not authorize deletion |

Do not execute scripts, installers, macros or active document content to prove receipt. A safe preview establishes only the inspected content. An app's re-exported rendering is not necessarily the same representation as the received file; leave exact-byte verification unavailable rather than compare a screenshot or derivative to the source. Do not browse private library internals to manufacture a digest.

If a file arrived but the receiving app cannot use its format, record delivered-but-unusable for that requirement. Conversion, new software, additional app imports or a different destination require their own scoped decision. Successful transport cannot substitute for the user's required usable output.

Keep directly observed, user-reported and sender-only evidence separate. With no receiver-side access or report, state that the sender reported completion and receipt remains unverified. Do not impersonate the recipient or contact them through another channel without communication authority.

## 5. Recover only the unresolved part

- **Peer missing:** inspect the intended devices' presence, existing receive mode and documented prerequisite. Hold at a restriction or unavailable peer; do not broaden discovery or change accounts automatically
- **Recipient declined:** retain the refusal and stop that delivery. Clarify through the permitted interaction rather than repeatedly prompting them
- **Waiting or timed out:** inspect the current sender state and recipient's exact destination before another attempt. A timeout does not prove that nothing arrived
- **Some files confirmed:** retain their mappings and retry only files established missing after the prior attempt is terminal. Hold uncertain files rather than resending the whole batch and creating duplicates
- **Wrong representation or name collision:** preserve both the source and existing recipient work; resolve the exact copy/format decision before another write
- **Full storage or denied destination:** report the precise blocker. Do not delete files, buy storage or change permissions as an incidental fix
- **Wrong or uncertain recipient selected:** stop further sends and cancel the pending operation if a supported scoped control is available. Report what is known promptly; cancellation does not guarantee already received data was recalled. Do not claim remote deletion or contact someone independently without authority

If retrying, refresh the selected source version and peer identity first. A changed file is a new version to reconcile, not evidence that the earlier transfer was corrupt. Do not delete partial or duplicate-looking received items unless their exact identities, recovery behavior and cleanup are authorized; irreversible deletion needs its required action-time confirmation.

Restore only the approved temporary discovery/settings changes, after checking for intervening user changes. Read back their final state. Do not turn off a radio used by current work merely because it was off before, or treat expiry of receive visibility as removal of a known-person relationship.

## Deliver and stop

Return the intended recipient/device, selected count, received-copy locations, final per-file exceptions, checks performed and evidence limits. Mention any temporary visibility or known-person state that remains, with the approved ending and exact next step. For a straightforward completed transfer, this can be a short message rather than a separate manifest file. Keep private filenames and paths out of broader-facing reports.

Call delivery verified only to the established recipient-side coverage. Call exact-byte identity verified only when that comparison actually occurred. A complete preparation plan, sender-reported send, receiver-reported receipt and directly checked usable copy are different outcomes. Keep originals; delivery is not backup certification or permission to clear source storage.

Stop when the requested copies and acceptance evidence are established, the recipient declines, a supported prerequisite is unavailable, or a protected action/new authorization is required. Leave uncertain receipt explicitly pending rather than inventing completion or retrying without a changed observation.

## Fictional, unexecuted illustration

A fictional user requests two existing PDFs from their Mac be sent to their own nearby iPad. Both devices already use the same Apple Account, and readable saved copies are the requirement. An older PDF with one matching filename is already on the iPad. No discovery change, new known-person relationship, conversion or original deletion is requested.

The proposed workflow would bind both source versions and the exact iPad before sending, without expecting an acceptance prompt. If the Mac later reported completion but only one new PDF could be located, the record would mark that item received and the other uncertain. The older same-name file would not satisfy receipt. The workflow would locate the actual second destination or establish nonreceipt before retrying just that file. It would report readable-copy evidence separately from an unperformed byte comparison.

This original illustration is fictional and unexecuted. No device, file, account, application, code, contact, permission, network setting or transfer was accessed, changed or tested for it. The instructions describe later authorized work and make no runtime or delivery claim.
