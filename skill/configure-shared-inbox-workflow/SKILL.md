---
name: configure-shared-inbox-workflow
description: "Prepare or configure an existing shared team inbox so incoming work, reply ownership, sender identity and team-visible response history stay connected. Use for native inbox operating setup and a usable handling handoff, not mailbox provisioning, personal-mailbox delegation, automatic replies, message triage or a new support system."
---

# Configure a shared inbox people can operate together

Deliver the smallest native setup and handling guide that lets the intended team find an incoming request, establish who is responding, use the correct sending identity and see what happened. Keep saved configuration, a person's access, observed message behavior and team adoption separate. A common email address alone does not create a shared work queue.

Use [email filing rules](../configure-email-filing-rules/SKILL.md) for automatic arrival predicates, [support-case handoff](../prepare-support-case-handoff/SKILL.md) for the history of one ongoing problem, and [team working agreements](../draft-team-working-agreement/SKILL.md) when responsibility or service expectations themselves need deciding. This workflow maps established handling needs onto an existing inbox. It does not provision a mailbox or group, convert a personal account, migrate historical mail, set customer promises or build a ticketing application.

## Establish the inbox and the requested result

Read the request and relevant existing setup. Recover only the inputs that affect the result:

- Provider, organization, exact mailbox/group identity and address, chosen client and supported access route
- Existing team audience and verified operating roles; who needs to read, claim, reply, resolve or manage the inbox
- Where incoming messages and outbound replies currently live, including any known forwarding, distribution or linked help-desk route
- Established handling states, ownership/coverage rule, escalation route and definition of completion
- Expected public sender identity and recipient behavior, including whether personal operator names may appear
- Proposal-only versus authorized configuration changes, requested handoff destination and any separately authorized message test

Ask about a consequential gap rather than inventing a response policy. “Everyone monitors it” does not identify who owns a particular reply. “Use the team address” does not establish Send As rather than Send on Behalf, nor authorize disclosure to all group members. Continue the configuration proposal while such a choice is pending.

Inspect the actual resource type. An alias can deliver into another mailbox; a distribution address can create separate member copies; a shared mailbox can retain common messages; a collaborative inbox can add conversation assignment and resolution. Do not infer which model exists from the address or its display name. Preserve the chosen service instead of replacing it with a new account or product.

The output is a concise before/after configuration map, a practical handling card and the evidence/limits for the saved result. If only preparation is possible, supply the exact target settings, current prerequisites and blocked operation. A useful handoff does not require granting anyone new access.

## Separate operating setup from access and communication

Use existing authorized account access. Never share credentials, enable direct shared-account sign-in, obtain token values, grant an app new permissions or install an add-in as a hidden setup step. Microsoft's [shared-mailbox guidance](https://learn.microsoft.com/en-us/microsoft-365/admin/email/about-shared-mailboxes?view=o365-worldwide) specifies access through delegates' own accounts and keeping the shared account blocked from direct sign-in. Report an incompatible access model rather than working around it.

Treat mailbox delegation, Send As/Send on Behalf grants, group membership and permission changes as separate consequential operations. Before changing account-security settings or creating/materially expanding persistent access, obtain the required action-time confirmation for the exact resource, people, capabilities and historical/future information exposed. A general setup request, this guide, an administrator role or a proposed role map is not that confirmation. Ordinary operating configuration may proceed within its specific existing authorization; do not make every read or harmless display choice an access change.

Membership is not the only exposure boundary. Group archive visibility, copying replies into a common folder, subscription delivery and forwarding can expose different information to different audiences. Confirm any missing data-sharing scope before enabling it, including whether sensitive content can reach that audience. Do not make a group public, broaden posting privileges or forward mail elsewhere to solve an access problem. Missing administration capability can remain a precise prerequisite in the handoff.

Configuration does not authorize responding to customers, assigning real conversations, marking them complete, creating mailbox drafts, sending tests, changing subscriptions or notifying teammates. A separately requested ordinary action can proceed within its actual authority. Keep message content, membership evidence and private account details out of a broadly shared setup note unless needed and authorized. Prefer metadata and minimal representative evidence; preserve unread state through a supported read-only route, or resolve the side effect before opening a message that would mark it read.

## Identify the authoritative work record

Inspect the current inbox, relevant folders/labels, assignment and resolution controls, sent-message locations and applicable settings. Record stable IDs where available, capture time and the actual scope inspected. A partial view of one client is not a complete configuration inventory.

Determine which record operators should use before answering. A forwarded copy, personal subscription email and group conversation may represent the same exchange but have different state. Do not treat a personal read flag, star, snooze or archive action as a team claim or completion marker unless the actual service makes that meaning shared and the team has adopted it.

Keep these questions independent:

1. Where does the original request arrive, and can the intended operators see it?
2. Where is ownership represented, and is the change visible to other operators?
3. Where is the reply sent from, and what identity does the recipient see?
4. Where can the next operator find that exact outbound reply?
5. What marks work finished, waiting or reopened, and what new event changes that state?

A conversation can contain several requests or unrelated same-subject messages. Bind observations to actual message/conversation identity and inspect relevant threading behavior. Do not merge cases, delete apparent duplicates or bulk-classify old mail to make the new workflow look clean. Preserve existing message states and unresolved ownership.

Inspect competing routes only to the depth needed: existing filing rules, forwarding, automatic responders or a linked support system may already control the same incoming mail. Document that dependency without disabling it. If the help-desk record is authoritative, do not introduce a second independent completion state in the mailbox. If no common history or ownership mechanism exists, state the limitation and propose the minimum supported choice; a shared address is not proof of collision prevention.

## Map handling needs to the native capabilities

Prepare a short map of each needed capability, current setting, proposed delta and verification method. Keep access to messages, permission to send and permission to manage workflow metadata distinct. Reuse existing labels/folders by identity rather than creating similarly named duplicates.

### Microsoft 365 shared mailbox

Check the exact account and Outlook version. [Exchange Online's permissions reference](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-permissions-for-recipients) separates Full Access from sending rights. Full Access includes modifying/removing mailbox contents but does not grant sending; Send As and Send on Behalf produce different sender presentation and do not themselves grant reading. Record the actual rights, not a generic “member” checkmark. Adding both sending modes is not a neutral fix: Microsoft documents that Send As takes precedence when both exist.

Use the existing delegate's supported opening route. In Outlook on the web, the profile menu's Open another mailbox route opens the selected mailbox separately; adding a shared folder instead changes personal navigation. Follow [the matching Outlook product instructions](https://support.microsoft.com/en-us/outlook/sharing/open-and-use-a-shared-mailbox-in-outlook), and verify the full address. A shortcut appearing does not prove permission or sending success. Do not restart a client with unsaved work merely to refresh the view.

Inspect the saved sent-item behavior for the sending mode actually used. Microsoft's [shared-mailbox settings reference](https://learn.microsoft.com/en-us/microsoft-365/admin/email/configure-a-shared-mailbox?view=o365-worldwide) describes the default personal Sent Items location and the mailbox-level options for retaining shared copies. If shared reply history is requested and authorized, use Teams & groups → Shared mailboxes → the exact mailbox → Sent items, changing only the applicable approved option. Keep the distinct Send As and on-behalf paths explicit. Do not change forwarding, automatic replies, email apps or unrelated settings in the same panel.

Do not infer that enabling a future-copy option backfills old replies. Preserve historical gaps. A mailbox without native assignment can use an already-approved shared folder/category convention only after its actual shared visibility and client behavior are established. A label is not an atomic lock: the handling card must retain the team's claim/recheck practice and disclose the remaining concurrency limit. If that limit conflicts with the stated need, hold that part rather than silently installing a ticketing add-in.

### Google Groups Collaborative Inbox

Verify the exact group and whether Collaborative Inbox is already enabled. Google's [group settings reference](https://support.google.com/groups/answer/2464926?hl=en) distinguishes viewing, posting, posting as the group, default sender and reply-destination settings. Its Collaborative Inbox feature requires conversation history. Do not enable history without checking the changed storage/exposure and approval boundary. [History behavior](https://support.google.com/a/users/answer/6103429?hl=en) differs from email subscription: turning history off stops new posts appearing in the web archive while older archived posts remain. A member's personal email copy is not proof that the common queue is complete.

Use native assignment and resolution if their required permissions already exist. [Google's assignment guidance](https://support.google.com/groups/answer/2467048?hl=en) identifies Who can moderate metadata as the relevant capability for taking and assigning conversations. Do not promote someone to owner or manager merely to enable ordinary handling. Missing capabilities remain an exact access request until separately confirmed.

Map the team's meanings to the actual operations, not just the icons. [Google's Collaborative Inbox guidance](https://support.google.com/a/users/answer/167430?hl=en) requires metadata-moderation permission to mark complete, but content-moderation permission for no-action-needed or duplicate actions. Assigning a conversation sends the assignee an email, including any assignment note. A resolved conversation can remain assigned. Marking a duplicate locks that conversation. Keep those effects in the handoff and do not exercise them on live requests as setup tests. Prefer an unresolved-view filter to deleting completed conversations.

For approved configuration, select the existing group, inspect Group settings and apply only the named deltas. Resolve prerequisites before enabling a dependent feature. Preserve membership, history, moderation, spam handling, delivery subscriptions and reply settings unless the request and applicable confirmation cover their change. Do not add the group as a new Gmail sending identity to bypass a missing posting capability.

## Write the handling card around actual decisions

Make the operator's first steps concrete without inventing team policy:

- Open the verified common inbox/queue and check the current conversation, ownership and latest team-visible response
- Claim or follow the established assignment route before composing; state where a claim appears and how a conflict is handled
- Check the actual From identity and To/Cc recipients for each reply, including the difference between replying to the original author and posting to the group
- Keep internal notes in a verified internal-only location; an assignment-email note, group post, quoted thread or shared draft is not automatically private
- Record the response through the established common history, then apply the supported waiting/completion state only when its real condition is met
- On a later reply, unavailable owner or handover, use the existing reopening/escalation rule; label any unresolved rule as a decision, not a configured behavior

Document the native status mechanism and its limits. Establish whether a later reply changes resolution/assignment or merely adds a message; do not assume automatic reopening. Do not use unread as a promise that no one is handling the item, Sent as proof the recipient received it, or “complete” as proof the underlying problem is solved. For uncertain delivery, use [email-delivery tracing](../trace-email-delivery/SKILL.md) instead of resending. For missing coverage, surface the gap rather than assigning a colleague or adding a response deadline.

Include only the useful routes and state definitions. A small inbox should get a short card, not a new management process. Keep proposed conventions visibly proposed; saving labels or a guide does not establish that the team adopted them.

## Apply, verify and stop at the evidenced result

Capture the current values of changed settings, then recheck the exact resource and affected fields immediately before writing. Reconcile concurrent changes rather than replacing the whole configuration. Apply only approved deltas; a multi-panel setup is not transactional. Reopen the provider settings and compare saved values with the requested map.

Check the requested outcome at separate levels:

1. **Prepared:** the exact settings and handling card exist, with prerequisites and missing decisions
2. **Saved and read back:** the native fields/objects match, with unrelated settings preserved
3. **Access supported:** evidence supports the named operator's required capability; invitation, grant metadata and successful use remain distinct
4. **Behavior observed:** an authorized specific message or recipient-side record demonstrates the reply identity, common history or workflow state being claimed

Use existing authorized evidence when it answers the question. The setup account opening the inbox does not prove every operator can do so. Do not borrow a teammate's session, export personal Sent Items, grant access or send a sample message to manufacture a pass.

If a live test is expressly requested, establish the exact authorized sender/recipient accounts, benign content, mailbox, operations and expected side effects. Keep it separate from real work. Verify the observed recipient-facing sender and recipients, the correct common conversation/reply copy, and any actually exercised ownership/state transition. An internal exchange does not prove external sender acceptance or another client's behavior. A dry-run walkthrough or configuration readback is sufficient for its stated level, but must not be labeled an end-to-end test.

Return the verified inbox route, actual configured changes, concise handling card, remaining authority/capability gaps and the level of evidence obtained. Stop when the requested setup/proposal and bounded checks are delivered. Do not start monitoring arrivals, replying for the team or auditing membership on a schedule without a separate instruction.

## Recover partial or uncertain changes

After a timeout, read the exact setting or object before retrying. Avoid duplicate folders, labels, invitations or replies. Record each proposed delta as saved, absent, blocked or unknown; finish only still-needed authorized steps with current preconditions.

If sent history or ownership visibility is missing, keep that gap explicit. Do not bulk-copy old personal messages, rerun a send, move all mail back to Inbox or reset everyone to unassigned. Those actions can expose unrelated content, duplicate responses or erase live work. Correct only the evidenced affected field or item within its actual authority.

Rollback has its own effects. Disabling future sent-item copies does not remove existing copies; changing a reply default does not retract delivered mail; removing a personal mailbox shortcut does not revoke access. Permission restoration, revocation, history changes and message deletion need the applicable current confirmation. Preserve concurrent legitimate changes rather than restoring an entire stale snapshot.

For an unintended recipient, audience expansion or sensitive exposure, stop further dependent changes and report the verified discrepancy promptly. Carry out only authorized containment; do not claim deletion retracts notifications, downloads or existing copies. If the new handling convention cannot be made reliable with available native controls, deliver the usable partial handoff and exact decision instead of claiming duplicate replies are prevented.

## Fictional, unexecuted illustration

An invented studio already has a Microsoft 365 shared mailbox, studio@example.invalid, and two existing operators. Its accepted process is to claim a request in a shared ownership category, check for a newer reply before sending, and leave waiting requests open. The user asks for a setup proposal that makes replies visible to both operators; access changes, historical copying and test mail are excluded.

The fictional settings record shows Send As access but reply copies only in each sender's personal Sent Items. The proposal identifies the mailbox's Send As copy option and the required confirmation of the shared reply audience. It preserves the separate on-behalf setting and does not claim old replies would appear. The handling card names the common inbox, current claim convention, From/recipient checks and reopen rule. It labels the claim convention as coordination rather than an enforced lock.

The deliverable would be “prepared; no settings saved and no sending behavior observed.” No mailbox, message, category, permission or account was accessed, changed or tested for this illustration. All identities, settings and events are fictional.
