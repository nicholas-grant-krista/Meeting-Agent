---
audience: everyone
product-version: "2.1"
sources:
  - conversation-agent:docs/workspace-platform-routing.md
  - conversation-agent:docs/workspace-bot-identity.md
  - conversation-agent:docs/meeting-bot-end-state-policy.md
  - conversation-agent:docs/user-management.md
  - conversation-agent:docs/license-tiers-and-session-auth.md
  - meeting-bot:docs/transcription.md
  - meeting-bot:README.md
last-verified: 2026-08-24
---

# FAQ

## Platforms

**Does Meeting Agent join Zoom meetings?**
Yes. Zoom is fully supported, including meetings hosted by other organizations.
Nothing is installed in Zoom, no Marketplace app is needed, and the host does not
have to be a Krista customer.

**Which platforms are supported?**
Microsoft Teams, Google Meet, and Zoom. WebEx, GoTo, and everything else are not
supported — those meetings are marked skipped.

**Can it join a meeting hosted by another company?**
Yes, on all three supported platforms, using the Krista Bot. Someone in the
meeting has to admit it, exactly as with any guest.

**Do we need to install anything in Teams, Meet, or Zoom?**
Not for the Krista Bot — it joins as a guest via the meeting link. The native
Teams route is set up with your Krista TAM during onboarding.

**Can it join a meeting that isn't on the calendar?**
No. Meeting Agent works from your connected calendar. Ad-hoc meetings are
invisible to it.

## The bot in the meeting

**Will people see it?**
On Zoom, Google Meet, and Teams meetings it joins as a guest — yes, it appears in
the participant list. The native Teams route for your own meetings adds no
participant.

**What is it called?**
By default `Krista (<Your Workspace Name>)`, so attendees can tell which team's
bot joined. Your admin can rename it to anything, and a custom name is used
exactly as entered.

**Why does Teams say "Unverified"?**
That is Teams' standard label for a guest who joined without signing in. It is
not a warning about the bot.

**Why does it have no camera?**
No avatar image is configured. Your admin can set one and it appears as the bot's
video tile.

**Does it talk, or answer questions?**
No. It does not participate in the conversation.

**What if nobody lets it in?**
It waits about 5 minutes, then leaves. The meeting is not recorded and is marked
skipped. This is the most common reason a meeting is missing — and often the
host wasn't refusing, just running late.

**Why does it turn up before the meeting starts?**
It joins about a minute before the scheduled start so recording is already
running when the first person speaks. It's prepared behind the scenes about ten
minutes ahead of that.

**What if everyone leaves but the meeting stays open?**
The bot leaves after a minute alone and the meeting is processed normally. If
nobody joins at all, it waits 5 minutes and then leaves.

**What if I remove it mid-meeting?**
Recording stops and the partial capture is **discarded**, not processed. Removing
the bot is treated as an instruction not to keep the content. Use it when a
meeting turns sensitive.

## Recording and transcripts

**How does it transcribe?**
It prefers the meeting platform's own live captions. If captions could not be
enabled or produced nothing, it transcribes the recorded audio itself. Either way
you get a transcript.

**Why do Teams transcripts look more detailed than Zoom or Meet?**
Different platforms group captions differently. Teams produces one segment per
utterance; Meet and Zoom group an uninterrupted speaker's sentences into a single
block. Content and attribution are complete in all three — only the chunking
differs.

**Does it start Teams transcription?**
No, deliberately. Starting Teams transcription notifies every participant and
writes a transcript file to the organizer's OneDrive. That is your organization's
decision, not something a bot should do on your behalf. Meeting Agent captures
via captions instead.

**Does it read Google's post-meeting Drive transcripts?**
No. It has no Drive access. Its transcript comes from captions captured live.

**Can I improve transcript quality?**
Yes — make sure captions are on, introduce speakers on external calls, and state
decisions and action items out loud. On Zoom meetings you host, enable full
transcript viewing on your Zoom account.

**What if the meeting is cut short?**
It is still processed, with a notice that the transcript may be incomplete.

**Is there a maximum meeting length?**
Yes — **3 hours**. The bot leaves at that point and the meeting is processed
normally, so you get everything up to the cap rather than nothing. If you
routinely run all-day sessions, raise it with your Krista TAM before relying on
it.

**What happens in a long silence?**
After about 5 minutes of sustained dead air the bot leaves and the meeting is
processed as normal.

## Setup and administration

**What decides whether a meeting is "internal" or "external"?**
Internal means a Microsoft Teams meeting whose organizer is on one of your
configured internal domains. Everything else is external. The two are routed
independently.

**Can we record internal meetings but not customer calls?**
Yes. Set the internal bucket to your preferred route and the external bucket to
`None`.

**Can we turn it off entirely without losing our configuration?**
Yes. Set both buckets to `None`. Meetings still appear, marked skipped, and
nothing is recorded. Reverse it any time.

**How long do routing changes take?**
They apply on the next scheduling cycle — no restart, no waiting period.
Meetings that have already run are never re-routed.

**Why did several bots join the same meeting?**
More than one of your workspaces picked up that meeting and each sent its own
bot. Set the internal bucket to `Microsoft Teams` or `None` on the workspaces
that do not need to capture it.

**Who can change these settings?**
Users with the **Meeting Agent Admin** (Workspace Admin) role. Everyone else sees
the settings read-only.

## Users and licensing

**What is the difference between a licensed user and an Observer?**
A licensed user consumes a paid seat, their calendar is synced, and their
meetings are captured. An Observer is free, can view content shared with them,
and their calendar is **not** synced.

**A meeting with only Observers wasn't captured. Why?**
That is by design. An Observer's presence on an invitation does not pull a
meeting into the workspace. At least one licensed user must be on it.

**Can our Krista contact help without using a seat?**
Yes — as a Delegate Admin: admin authority, no paid seat.

**What happens when a trial expires?**
Access stops for users and integrations at once. There is no grace period and no
read-only mode. Note your date and convert before it.

**Does a trial limit how many meetings or minutes we can record?**
No. Trial and production have the same capability and the same limits. A trial
differs only in that it has a hard expiry date.

**Is there a limit on how many meetings can be captured at the same time?**
Not one set by the product — Meeting Agent does not cap or queue simultaneous
captures. The practical ceiling is the capacity of the environment Krista runs
for you. If you expect large peaks, such as a company-wide slot where many
meetings start at once, raise it with your TAM as a capacity question rather than
assuming either that a limit protects you or that none affects you.

## Data and privacy

**Where do recordings and transcripts go?**
Ask your Krista TAM. Storage location, retention, and sub-processor detail are
answered directly for your deployment rather than in this guide, because they
depend on how your workspace is provisioned.

**Are participants notified?**
The bot is visible in the participant list, and platforms show their own
recording indicators. Whether that is sufficient notification for your
jurisdiction and policy is a decision your organization must make — see
[prerequisites](02-setup/prerequisites.md).

**Can we exclude specific meetings?**
Keep them off the connected calendar, or route their bucket to `None`. For a
meeting already in progress that turns sensitive, remove the bot — the partial
recording is discarded.

**Is this a compliance recording system?**
No. It is not designed to guarantee capture of every meeting for regulatory
retention.

## Troubleshooting

**A meeting wasn't recorded. Where do I start?**
[Troubleshooting](05-troubleshooting.md). Start with the meeting's status — it
tells you whether the cause is yours or ours.

**What is the difference between "skipped" and "failed"?**
Skipped means there was correctly nothing to process — nobody admitted the bot,
capture was off, the platform is unsupported. Failed means a technical fault, and
it is replayable. Skipped is usually yours to fix; failed is usually ours.
