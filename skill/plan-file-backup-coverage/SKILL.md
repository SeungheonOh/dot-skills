---
name: plan-file-backup-coverage
description: "Turn a bounded file collection and recovery needs into a practical backup coverage plan, mapping source classes to supported capture routes, retained versions, independent destinations and recovery checks. Use before configuring or replacing backups, not executing a backup, restoring files or certifying disaster recovery."
---

# Plan file backup coverage

Deliver an actionable plan for preserving the files the user actually needs, including what existing arrangements cover, what they omit and what must be established before changing them. The useful result is a source-to-recovery coverage map and a staged setup checklist, not a list of recommended products or a promise that several copies make data safe.

Use [backup restore spot checking](../backup-restore-spot-check/SKILL.md) to retrieve and inspect selected historical files. Use [recovery evidence review](../prepare-recovery-evidence-packet/SKILL.md) to assess an existing recovery exercise. This workflow plans ordinary personal or team file protection. Live databases, distributed services, incident containment, regulated retention and system-wide disaster recovery need their own applicable procedures and owners.

## Establish what must be recoverable

Identify the selected devices/accounts, file collections, existing backup arrangements, intended reader and private plan destination. Use current inventories, settings summaries, backup catalogs or supplied records within authorized access. Begin with metadata and relevant examples; do not scan every account or read all file contents merely to make the inventory complete.

Ask only about decisions that change the plan:

- Which work is irreplaceable, replaceable with effort, or explicitly excluded?
- Which failures matter: accidental overwrite/deletion, lost device, failed drive, account loss, or loss of a location?
- How much recent work could be recreated, and how far back might an unnoticed mistake need to be recovered?
- Which files must become usable first, and what waiting time or manual effort is acceptable?
- Which destinations, recurring costs, network limits and handling routines are already chosen or permitted?

Keep these as user requirements or proposed choices, not measured recovery guarantees. If they are missing, provide a provisional plan with the affected decisions visible. Do not silently choose a retention period or paid service. Preserve supplied organizational rules; ask the responsible owner about legal holds or regulated records rather than inventing retention advice.

Do not collect passwords, recovery keys, private keys, tokens or credential-store contents. The plan may identify a credential-dependent recovery prerequisite without recording the credential or its exact secret location. Backup creation, uploads, purchases, installation, account grants, encryption changes and retention deletion are outside this planning task.

## Inventory the real source classes

Give each selected collection a stable row or ID. Record its actual device/account and source location, authority/owner, approximate size and observation date, change pattern, required history, native format and dependencies. Separate current file count, logical bytes and stored backup size; they answer different questions. Avoid double-counting nested folders or counting the same shared library as several independent collections.

Distinguish cases that change capture behavior:

- Ordinary local files versus cloud placeholders or files available only through a service
- Native app libraries, packages or open files requiring a documented export, snapshot or application-consistent procedure
- Linked assets, fonts or sidecars required to make a project usable
- Shared material the user can read but may not own or have authority to copy elsewhere
- Local changes, uncommitted/unpushed project work and files omitted by existing exclude rules
- Replaceable downloads/build outputs versus user-created source material, using evidence rather than folder names alone

A synchronized folder or source-control remote can contribute protection for a stated subset; do not assume either captures every local file, historical state or dependency. A folder shown in a file browser does not establish that its payload is resident or readable to a backup tool. Keep inaccessible locations and incomplete inventories as coverage gaps.

For each class, record included, intentionally excluded with a reason, or unresolved. Do not use the backup's current item list as the only denominator: material omitted from it still matters to the user's desired coverage. A useful small plan can use collection-level rows with a few representative exceptions instead of a file-by-file manifest.

## Map each source to a supported recovery path

Inspect current official documentation for the actual tool, plan and platform when its behavior affects the proposal. Record the source and date. Distinguish documented capability, configured selection, an observed successful capture and an observed restore; none automatically proves the next.

For each source class and destination, state:

1. The supported capture route and any availability or consistency prerequisites
2. Included/excluded scope and the properties retained: bytes, versions, metadata, native editability or linked resources
3. Capture trigger/cadence, conditions that can delay it, and what evidence would reveal a missed capture
4. Version and deletion retention, including expiry or capacity-driven pruning where documented
5. Destination identity, access boundary and the recovery route if the original device or account is unavailable
6. Required recovery software, format support and user-controlled authentication prerequisites
7. Current evidence level and the exact unresolved question or proposed setup action

Keep a file's last-edit time, backup-job time and latest captured version separate. A frequent schedule does not establish the maximum amount of work that can be lost while the laptop is asleep, a drive is unplugged or a service is offline. Describe the proposed exposure and its assumptions, not an achieved objective.

Assess independence against the user's failure cases. Two partitions on one drive do not protect against that drive's loss; two devices in one bag do not protect against loss of the bag. Distinct folders or branded services do not establish separate storage, deletion authority or account recovery. Keep unknown dependencies explicit instead of claiming independence from names alone.

The [CISA ransomware guide](https://www.cisa.gov/stopransomware/ransomware-guide) recommends keeping protected offline backups and checking recovery. Use that principle to examine whether a copy remains reachable by the same failure or unwanted deletion, not to certify that this plan prevents ransomware. Encryption, offline handling and historical retention address different risks; merely naming one does not establish the others. Record proposed safeguards and required user/administrator actions without changing security settings.

## Make the plan feasible and change-preserving

Estimate initial transfer/storage needs from the observed selected scope, with units and a date. Treat growth, changed-file volume, compression, deduplication and retention behavior as separate assumptions. Do not multiply current data by a version count and present it as exact capacity demand when the tool stores incremental or deduplicated data. If throughput is known, distinguish an approximate active transfer duration from elapsed time that includes sleep, outages and throttling. Unmeasured quantities stay uncertain.

Prefer a small set of steps tied to clear gates:

- Resolve unsupported source classes, destination authority, capacity and retention decisions
- Preserve existing protection while preparing the separately authorized arrangement
- Establish the initial selected capture and reconcile it against the source coverage map
- Inspect representative recovery in an isolated destination, including one important historical/deleted case when required
- Record remaining exclusions and owner acceptance before proposing retirement of an old arrangement

This is a setup handoff, not permission to run those steps. Never recommend erasing the old backup merely because a new job is green. Specify what evidence would support any future retirement decision, while keeping deletion and retention changes separately authorized. If existing storage must be repurposed before replacement coverage exists, expose the unprotected interval and ask for a different destination or an explicit decision.

Write a modest upkeep checklist: what success/failure evidence to inspect, what source changes require a coverage review, and how the user would discover expired or inaccessible versions. A described review cadence is not a configured reminder, monitoring service or guarantee that someone will respond. If the plan relies on manual drive rotation, name the required behavior and its unconfirmed owner rather than treating it as automatic.

## Deliver, check and revise the plan

Return the coverage map, current gaps, proposed arrangement, setup gates and recovery-check specification in one editable artifact when practical. Include the highest-consequence unresolved decision first. Minimize private path details in any audience-facing summary; the full source map belongs only in the authorized private destination.

Read back the saved plan and check that every selected source class has a disposition, every required failure case has a supported or explicitly missing recovery path, and every proposed change preserves existing copies until its gate is met. Walk through accidental overwrite, unavailable original device and an interrupted initial capture where relevant. This is a paper review, not an actual restore or adversarial test.

Use separate labels for proposed coverage, configured coverage, captured evidence and restore evidence. Do not say the files are backed up, protected or recoverable based on this plan alone. If a source or tool contract changes, preserve the prior plan and update the affected mappings. If a save is uncertain, inspect before retrying; if information is unavailable, deliver the independent rows and the exact blocked decision.

Stop when the requested planning packet is usable. It does not start jobs, copy files, unlock encrypted stores, grant persistent access, buy storage, delete old copies or schedule future checks.

## Fictional, unexecuted illustration

A fictional designer wants to recover current project work after losing a laptop and retrieve last month's version after an unnoticed overwrite. Their inventory has local working files, an external photo library and cloud-only reference documents. An existing laptop backup excludes external volumes; the cloud client displays references without storing all payloads locally.

The coverage map does not mark all three collections covered because the laptop's job succeeded. It retains the existing backup, proposes a documented capture route for the external library, and holds the cloud-reference row until export or provider-history coverage is established. The recovery-check plan includes a project with linked assets and a selected older revision. Destination capacity and recovery access remain decisions, not completed setup.

No files were scanned or copied, settings changed, accounts accessed, backups started or recoveries attempted for this invented paper illustration.
