---
name: subscribe-calendar-feed
description: "Add or repair a native subscription to an existing published calendar feed, preserving source identity, account placement and update behavior while checking the displayed events. Use for an automatically updated reference calendar, not a one-time ICS import, shared-calendar permissions, event editing or two-way synchronization."
---

# Keep an external calendar connected to its source

Deliver the selected feed as a separate usable subscription in the intended calendar client/account, or a precise setup proposal when access or permission prevents saving. Keep source publication, subscription configuration, displayed content and observed update propagation separate. An imported event or a successful Add dialog does not establish a working subscription.

This workflow follows an existing publisher-controlled calendar. It does not publish the user's calendar, grant another person access, create events, accept invitations, change availability rules or set up an account-wide calendar integration. Use [configure-shared-calendar](../configure-shared-calendar/SKILL.md) for collaboration permissions, [calendar-file-reconciliation](../calendar-file-reconciliation/SKILL.md) for repairing an offline file, and [diagnose-calendar-time-displays](../diagnose-calendar-time-displays/SKILL.md) when an established event is displayed at the wrong time.

## Establish the subscription contract

Resolve from the request, source and current client:

- The intended publisher, exact feed and schedule scope; distinguish a team, venue or category-specific feed from an organization-wide one
- Destination service/account, calendar client and devices on which it must appear
- New subscription, repair of an existing one, or replacement of an obsolete feed
- Whether automatic source updates are essential, and how much delay the intended use can tolerate
- Requested name, display treatment, alerts and attachments; preserve established choices for an existing subscription
- Whether the feed is public, requires a signed-in account, or carries a private access token
- Existing subscriptions or imported copies to preserve, and the user's actual authority to subscribe, change or remove them

Ask only for a missing choice that changes the result. A public event timetable can be an appropriate delayed reference; a requirement to catch last-minute changes immediately may not fit a polling feed. State that mismatch before promising a solution.

A subscription is an ongoing connection to the selected publisher. An explicit request to add that feed to a named calendar account covers the ordinary setup and supported retrieval. It does not authorize publishing either calendar, changing the publisher's permissions, adding unrelated accounts, enabling new reminder channels or sharing private feed contents with an unapproved service.

For a private feed, establish what information the destination provider will receive and whether that transfer and ongoing access are authorized. Keep credential-bearing feed URLs out of chat, reports, screenshots, search queries and ordinary logs. Use the applicable secure handoff for credential entry or transmission; do not copy a secret URL into another service merely because the browser can already open it. Never rotate or generate a token, add OAuth access, weaken organizational policy or bypass a security warning as incidental setup.

## 1. Identify the feed and the existing calendar objects

Get the link from the publisher's official subscription controls or another authorized, verified source. Inspect its meaning before activating an "Add to calendar" link: it may download a single event, start a one-time import, request calendar access or open an entirely different account flow.

Keep these objects distinct:

| Object | What it establishes |
| --- | --- |
| Publisher's ordinary webpage | A human-readable schedule; not necessarily the feed's current contents |
| Published calendar endpoint | A source the calendar consumer can retrieve, subject to its access and format support |
| Downloaded ICS file | A dated snapshot; it does not keep itself synchronized |
| Native subscription | A retained relationship to the endpoint, with consumer-specific refresh behavior |
| Imported or manually copied event | A separate destination record whose future updates are not established by the feed |

Do not guess an ICS URL from a webpage path, convert a sharing invitation into a public URL or strip query parameters from a feed to make it look cleaner. Such parameters may select the intended schedule or control access. A URL that works in a signed-in browser is not evidence that a server-side calendar subscriber can retrieve it. Stop on a login page, expired link or unsupported authentication requirement rather than substituting cookies or exposing the calendar.

Use the exact endpoint only in its authorized setup surface. In the handoff, retain a safe publisher/source label, destination subscription identity and a non-secret source-page link where available. Compare existing endpoints privately when needed; matching calendar names or event titles alone cannot prove a duplicate.

Inspect existing subscribed calendars, their account/local location, refresh settings, visible state and any imported copies relevant to the report. A hidden subscription is still an existing object. Do not create a second copy simply because it is unchecked or has a custom name. Do not delete a similarly named calendar without establishing whether it contains independent user edits.

For an existing subscription, capture only the before-state needed to recover the selected settings. Keep personal calendars and unrelated event details out of the record.

## 2. Choose the supported subscription route

Check current official guidance and the actual interface for the client/version and account type. Prefer a supported connector when it exposes subscription settings; event-creation or calendar-list tools alone do not prove that capability. A subscription cannot be implemented faithfully by copying every feed event through an event API.

Use the user's intended account and device scope. Do not substitute a cloud account for a local-only request or use a personal account to evade a work-account restriction. If the selected client cannot consume this feed, deliver the supported alternatives and the exact limitation; do not silently replace automatic updates with a static import.

### Apple Calendar on Mac

Apple's [calendar subscription instructions](https://support.apple.com/en-ca/guide/calendar/icl32362/mac) use File > New Calendar Subscription. Enter the approved endpoint, subscribe, then set the name, Location and requested options. Location distinguishes a local On My Mac subscription from an iCloud subscription available to devices using that account. Check the actual account before saving.

Inspect the separate attachment, alert and Ignore alerts controls rather than treating them as one notification switch. Set only the requested behavior. Source-controlled subscription events are not editable through this route. Reopen Get Info after saving to verify the source and settings.

[Apple's refresh guidance](https://support.apple.com/en-gb/guide/calendar/icl1024/mac) distinguishes a subscription's Auto-refresh control from an account-wide refresh setting. Change the selected subscription's interval when requested, without changing all calendars. A chosen interval is configuration evidence, not a guarantee that a publisher changes promptly or that every device has received a revision.

### Outlook.com or Outlook on the web

Use Calendar > Add calendar > Subscribe from web with the approved endpoint and available name/list options. The final action may be labeled Import or Import and Save even though the selected route is a subscription. Confirm the selected route; the button word alone is insufficient.

[Microsoft's import/subscription guide](https://support.microsoft.com/en-us/outlook/import-or-subscribe-to-a-calendar-in-outlook-com-or-outlook-on-the-web) distinguishes this from Upload from file, which creates a snapshot. It also warns that subscription updates can take more than 24 hours. Do not promise instant updates or treat that period as a guaranteed maximum.

A web-created subscription may be managed by the server rather than the desktop client. [Microsoft's Internet-calendar troubleshooting guidance](https://learn.microsoft.com/en-us/troubleshoot/outlook/calendaring/cannot-add-an-internet-calendar) describes this distinction. Inspect the account's actual calendar entry before adding another desktop subscription or changing desktop send/receive options. Do not assume a desktop refresh forces the server to fetch the source again.

### Google Calendar on the web

[Google's documented URL route](https://support.google.com/calendar/answer/37100?hl=en) is Other calendars > Add other calendars > From URL, followed by the published calendar URL and Add calendar. Its guidance describes this for public calendars and requires a computer browser to add a new subscription. The separate Subscribe to calendar route can request another person's Google calendar access; it is not an interchangeable URL field.

Do not make a source public to satisfy the documented route or send an access-request email as a workaround. For a private or authenticated feed, establish current supported behavior and the authorization boundary before entry. Do not promise support from the file extension alone.

### Before committing

Confirm source, account/location, new-versus-existing identity and requested alert/attachment behavior. For an existing subscription, apply only the supported changed fields. If changing its endpoint requires removal and recreation, explain the identity and local-setting consequences and obtain any missing removal authority first. Do not automatically remove the old object before establishing what would be lost.

## 3. Check the saved subscription and initial contents

After saving, navigate away and reopen the exact calendar's information/settings. Record whether the subscription exists under the intended account/local location, retains the correct source relationship and exposes the requested refresh behavior. If no stable ID is available, use the account, source relationship and native entry together; disclose that identity limit.

Check content over a bounded useful date range against the publisher's feed or other authorized source evidence. Use a few discriminating records rather than only a total count:

1. A recognizable upcoming event with its full date, start/end, source zone where available and intended display zone
2. An all-day or multi-day event when present, checked as dates rather than midnight UTC conversions
3. A recurrence exception, cancellation or recently changed record if that is the reason for the task
4. An edge of the requested schedule scope, such as the intended category or first relevant week

Do not require fixtures the real feed lacks or create source events to obtain them. Preserve event identity where the consumer exposes it; titles and times are weaker comparison evidence. The publisher may offer only a rolling horizon, so absence outside that range is not automatically a missing subscription event.

Open the actual event details or relevant view. A calendar listed in a sidebar with no checked content is not initial-load verification. Conversely, a temporarily empty feed is not necessarily a failed setup; report the observed source coverage and unresolved display check.

Check only the requested devices using already-authorized access. One Mac's successful load does not verify an iPhone, another account or a coworker's view. A subscription being displayed does not establish that it blocks free/busy, prevents bookings, creates an attendee relationship or produces reminders. Keep those consumer-specific claims unverified unless separately required and evidenced.

If there is a time discrepancy, compare the source revision and time meaning before changing a display preference. Never move or duplicate a subscribed event to compensate for a stale or misunderstood view.

## 4. Separate refresh configuration from update evidence

Use three distinct result levels:

- **Saved:** the intended subscription and settings were read back
- **Initially loaded:** selected current source records appeared in the consumer
- **Update observed:** a known later source revision propagated to that same subscription

The third level needs a before/after source change and the corresponding destination observation. A spinner, HTTP success, changed retrieval time or a second identical calendar view does not prove it. Do not create, reschedule or cancel an event in the publisher's calendar just to manufacture a test.

For an ordinary setup request, saved configuration plus a checked initial load can complete the work, with future propagation explicitly untested. If the user specifically requires observing an update, agree on an existing or expected source revision, observation window and acceptable delay. Continue only that bounded check; an unchanged destination remains pending until the condition or agreed window is resolved. Do not claim a failed propagation merely because no source event changed.

Use a supported refresh where available. Separate publisher state, subscriber-service cache and device display: reloading a page may update only the last layer. Preserve timestamps for the source revision, source observation and consumer observation rather than labeling everything "last synced."

A time-critical decision should use the authoritative publisher's current notice when available; do not present a delayed subscription as a guaranteed cancellation alert.

## Recovery, removal and delivery

After an uncertain Add/save response, inspect the destination list and exact source relationship before retrying. A duplicate subscription can double displayed events and alerts. Do not repair it by deleting every repeated event.

Use the narrowest supported next step:

- **Calendar exists but is not visible:** inspect its selected/hidden state and the viewed dates before adding it again
- **No initial events:** verify source scope, current source contents and consumer retrieval support; distinguish an empty feed from a failed fetch
- **Source revised, destination old:** identify the refresh owner and documented delay; preserve the stale revision and observation time
- **Wrong category or source:** establish the correct endpoint and whether the native client permits changing it; retain the existing object's identity/settings before any approved replacement
- **Login/expiry/access failure:** obtain the supported owner/user action; do not scrape through a session, publish the source or weaken authentication
- **Malformed or incompatible feed:** preserve the precise error and publisher-facing diagnosis; do not import a locally repaired snapshot while claiming automatic updates
- **Duplicate views:** separate a second subscription, imported copies and attendee events before proposing removal

Unsubscribing, hiding the calendar, removing imported copies and deleting the publisher's calendar are different actions. Use the selected provider's supported unsubscribe/remove-subscription control only with the appropriate authority, after checking its exact effect and device/account scope. Do not report the calendar as disconnected merely because it is hidden. Do not report the publisher as having deleted events because a local subscription disappeared. An exposed private URL requires its own authorized access-revocation decision; local removal is not proof that earlier copies or other subscribers lost access.

Return a compact handoff: publisher/source label; destination account/client and local/cloud scope; subscription identity or safe entry route; saved refresh and notification choices; initial-content checks; update evidence or its explicit limit; preserved old/imported copies; and any precise blocker or next check. Keep secret endpoints out of the deliverable.

Stop when the requested setup and bounded verification are complete, when an explicitly requested observation reaches its outcome/window, or when a necessary capability, permission or decision is missing. Do not add ongoing monitoring, publish feeds, clean up old copies or message the publisher unless separately requested.

## Fictional, unexecuted illustration

A fictional user asks to follow a community workshop's public timetable in their work calendar, with future updates and no new alerts. Their calendar already contains last month's one-time import. The intended route is a new source-linked subscription in the named account, preserving those imported records until a separate cleanup decision.

The publisher's fictional source now shows an afternoon session moved from 14:00 to 15:00. If the saved subscription still shows 14:00, setup and initial retrieval may be observable, but the required revision is not yet established. The plan checks the subscription's source and refresh owner, retains the observed stale time, and does not repeatedly import the file or delete the user's old records. A later 15:00 observation would support propagation of that identified change, not a promise of immediate future updates.

These are invented inputs and proposed observations. No feed was subscribed to, calendar read or changed, event imported, alert sent, application used or update propagation tested for this illustration.
