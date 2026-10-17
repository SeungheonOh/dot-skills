---
name: configure-shared-calendar
description: "Create or configure a separate native calendar for a defined group, with verified ownership, audience roles and usable access instructions. Use for a shared planning calendar, not scheduling meetings, mailbox delegation, room booking, public-feed publication or calendar migration."
---

# Set up a shared calendar with the right audience

Deliver a usable shared calendar or a complete proposed configuration with the exact blocked step. Keep its durable identity, calendar-wide access, each person's display/subscription and future event behavior separate. Seeing the calendar in the setup account does not establish that collaborators can use it.

Use [meeting-window-coordination](../meeting-window-coordination/SKILL.md) for an invitation, [change-recurring-calendar-series](../change-recurring-calendar-series/SKILL.md) for recurring-event edits, and [configure-meeting-booking-page](../configure-meeting-booking-page/SKILL.md) for self-service appointments. This workflow configures a separate ordinary calendar from established needs. It does not provision a shared mailbox, organization group, resource calendar, booking engine or account-wide delegation.

## Resolve the calendar and approved effects

Establish from the request and current context:

- Service, account/organization and intended owning account; new calendar or exact existing secondary-calendar ID
- Purpose, name, concise description and authoritative regional timezone where the calendar exposes one
- Verified people or bounded group, the ordinary information to be placed here, and who may see availability, read details, edit events or manage sharing
- Whether the user wants a proposal, creation, named sharing grants, or changes to existing settings
- Expected use: shared reference dates, collaborative planning or a calendar that must affect a particular availability consumer
- Existing events, grants, names, settings and other calendars that must remain untouched

Ask only for consequential missing choices. Do not assume “team calendar” means everyone in the organization, choose a similarly named email account, or infer permission to share a person's primary calendar. For a group grant, establish the intended group and membership boundary; a hidden roster remains an uncertainty, not proof that only the listed people have access.

Sharing a calendar grants ongoing access to the covered event information. The request must cover the calendar, audience, access level and information scope, including future contents. An empty calendar is not a reason to ignore this future exposure. Obtain any required action-time approval when the grant materially expands persistent access to sensitive information. Do not repeat ordinary confirmation already supplied by a specific request.

Inspect actual tools. Event read/write access may not include calendar creation or permission changes. Use an available supported connector or authorized native interface; do not create OAuth grants, enable domain-wide delegation, switch accounts or weaken organization policy to finish setup. When the intended owner cannot create or share the calendar through existing access, prepare the settings and identify that exact dependency.

## Inspect the current boundary

Check for an equivalent calendar and name collisions in the intended account. An incomplete calendar list does not prove absence. Do not adopt, rename or unhide an unrelated calendar simply because its name resembles the request.

For an existing calendar, record its stable ID, owning account, relevant settings and current access routes, including direct, group, organization and public access where visible. Inspect enough content or source context to determine the sharing consequence without copying private event details into a setup report. Preserve unrelated grants and settings. If current broad access conflicts with a requested restricted audience, expose the mismatch; adding named viewers alone does not remove that access.

Distinguish the calendar itself from a personal view. [Google's CalendarList reference](https://developers.google.com/workspace/calendar/api/v3/reference/calendarList) describes per-user colors, selected/hidden state, title overrides, reminders and notification settings. Changing the acting user's display or reminders is not configuring those values for the group. Removing a calendar from that list is also different from deleting the calendar. Do not promise shared styling or alerts from personal settings.

Verify the owning identity before creation. [Google's calendar resource](https://developers.google.com/workspace/calendar/api/v3/reference/calendars) makes the authenticated creator the data owner of a new secondary calendar. Use the intended already-authorized account; do not create under a convenient service account and assume it can be transferred later. Ownership transfer and organizational lifecycle planning are separate actions.

## Map needs to real roles and behavior

Prepare a compact role map containing recipient/group identity, needed capability, proposed native role, relevant restrictions and current status. For a small setup, a short list is enough. Select the least capability that satisfies the request; editing events, managing sharing and acting on someone's behalf are distinct powers.

Consult current official documentation and the actual account controls. Do not assume a label has the same meaning across providers or that an event marked private defeats every editor role. Existing administrator access and retention processes also remain outside ordinary sharing controls.

For Google, [the sharing model](https://developers.google.com/workspace/calendar/api/concepts/sharing) distinguishes availability-only, reader, writer without private access, writer and manager-level owner roles. The manager role does not transfer the calendar's single data ownership. Its private-event behavior also differs between writer roles. Match the actual available role to the user's requirements; if a tool cannot express the needed boundary, hold that grant rather than silently upgrading it. Sharing does not by itself insert the calendar into another person's CalendarList, so entitlement and addition to their view need separate evidence.

For Outlook, [Microsoft distinguishes editing from delegation](https://support.microsoft.com/en-us/outlook/sharing/share-and-access-a-calendar-with-edit-or-delegate-permissions-in-outlook). Delegation can include scheduling and responding on the user's behalf and is limited to the primary calendar in the documented Microsoft 365 workflow. A secondary-calendar editor does not need that authority. Account types and organization boundaries affect available roles; do not offer an external work-account recipient an editor capability the service does not support, or change mailbox permissions to imitate it.

Check whether the calendar can serve the requested planning purpose. [Microsoft's additional-calendar guidance](https://support.microsoft.com/en-us/outlook/calendar/create-additional-calendars) warns that classic Outlook secondary-calendar events do not contribute to Scheduling Assistant availability, and describes response-tallying limitations for meetings on a new Exchange calendar. A calendar visible beside the primary calendar is not automatically a conflict-check source or room reservation system. If availability blocking or meeting-response handling is essential, establish the actual consumer's supported behavior before calling this setup suitable. Do not duplicate events or reconfigure a booking service as an incidental fix.

Use named access for a named group. A public HTML/ICS publication route is a different audience, and a secret/private subscription URL can expose calendar data to its holder. Do not copy credential-bearing links into messages or substitute publication for a failed invitation. Keep current public/domain settings unchanged unless the requested audience change explicitly covers them. Refer sensitive access tokens to the supported secure handoff rather than chat.

## Create and share through the selected service

For proposal-only work, return the name, owner, purpose, timezone, role map and exact recipient instructions without creating provider state. For authorized setup, prepare the smallest ordered set of changes and note any unavoidable invitation notifications before the action. A request to share with named people ordinarily includes the provider's sharing invitation; it does not authorize a separate announcement or repeated reminder.

Supported starting routes, checked on 2026-10-17:

- **Google Calendar:** In the browser, use Other calendars → Add other calendars → Create new calendar, enter the approved name/description and check the available timezone setting, then create. Reopen the exact new calendar's settings and sharing controls. Under Shared with, add the verified people/groups, select each approved role and Send. Creation and sharing are separate effects. See [creation](https://support.google.com/calendar/answer/37095?hl=en) and [sharing](https://support.google.com/calendar/answer/37082?hl=en).
- **New Outlook:** Use Calendar → Add calendar → Create blank calendar, name it, choose its list category and save. Select that exact secondary calendar in Share calendar, add each verified recipient, select the appropriate available permission and Share. The list category is a navigation choice, not a recipient group. Follow the matching product tab rather than applying these controls to classic Outlook or another client. See [creation](https://support.microsoft.com/en-us/outlook/calendar/create-additional-calendars) and [view-only sharing](https://support.microsoft.com/en-us/outlook/sharing/share-an-outlook-calendar-as-view-only-with-others); use the editing reference above only for requested editor roles.

Before each mutation, recheck account, calendar ID and affected settings. Preserve the provider-returned identity immediately after creation and read it back before adding people. Apply only the authorized metadata and role deltas; a multi-step setup is not automatically transactional. Keep the existing primary calendar, events, reminders, conferencing defaults and unrelated permissions intact.

Do not move/import events merely to populate the calendar, invent a test meeting, invite attendees or send an availability poll. Calendar membership does not make someone an attendee of every event, and calendar sharing does not reserve anyone's time. When the user separately requests real entries, use the appropriate event workflow and confirm the destination calendar for each one.

## Verify setup and provide usable entry instructions

Reopen the calendar through its supported native navigation and verify:

1. Stable identity, owning account, shared name/description and applicable timezone match the request
2. Each changed role applies to the exact intended recipient/group; relevant public/domain and other access routes still match the approved boundary
3. The saved calendar exists independently of a personal title override or selected-view state
4. Existing events, unrelated grants and other calendars were not changed
5. Invitation evidence supports the reported state, with recipient addition/opening separately observed, reported or untested

The owner's success is owner-only evidence. Do not borrow a recipient session, create a test account, send an unrequested “can you open this?” message or grant extra access to manufacture a successful test. Use available authorized recipient evidence or state that the permissions were saved but recipient use remains untested.

Give the appropriate entry route: Google recipients can follow the sharing email's link; Outlook recipients can accept the sharing invitation and show/select the shared calendar. Use only a verified, non-secret native link when one is available. Explain where future entries belong and whether the calendar's availability behavior was established. Do not claim every member receives reminders or that invitation delivery proves acceptance.

Return the calendar identity/link, purpose and timezone, concise saved role map, invitation status, recipient-use limits and any exact blocker. Acceptance means the requested calendar and authorized grants are saved/read back, the audience boundary is supported, and the user has a workable handoff. Unknown group membership, unsupported roles or a failed audience readback prevent claiming a fully verified restricted setup.

## Recover partial or uncertain setup

After a timeout, inspect the intended account for the returned calendar/grant identity and current state before retrying. A matching name alone is insufficient. If creation succeeded but one grant failed, keep the created calendar and finish only the missing authorized delta once its preconditions are current. Do not create a duplicate calendar or resend all invitations.

When another person changes a setting during setup, reconcile the affected field rather than replacing the entire saved configuration. Reverting a grant can change access and requires its own applicable authority. Do not delete a calendar, remove another person's access, reset a subscription token or cancel events as automatic cleanup. Deletion may be irreversible and is not equivalent to hiding a calendar.

If unintended exposure is found, stop further sharing and report the exact verified audience discrepancy. Apply only an already-authorized containment action or request the specific decision. Removing access cannot retract earlier notification text, exports or copies. Stop when the authorized setup/proposal and bounded checks are delivered; recurring audience audits or future event creation require their own scope.

## Fictional illustration, unexecuted

An invented workshop team requests a separate “Workshop Dates” calendar owned by its coordinator. Two verified coworkers should edit ordinary planning events; one verified contractor should read details. The request excludes access to the coordinator's primary calendar, managing sharing, event creation and a launch announcement.

The proposed map uses the selected service's supported editor and reader capabilities on the new calendar only. If the contractor's account is restricted by organization policy, that grant remains blocked rather than making the calendar public. If creation and two grants are confirmed but the third result is unknown, the next step is a targeted permission readback. The handoff distinguishes saved access from recipients adding the calendar to their views and leaves reminders and attendance unclaimed. No calendar, permission, invitation, event or recipient session was created, changed or exercised for this illustration.
