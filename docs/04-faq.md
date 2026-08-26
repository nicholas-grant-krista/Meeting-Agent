---
audience: everyone — the single most-used page in this run book
product-version: "2.1"
sources:
  - meeting-bot:src/observers/chat.ts
  - meeting-bot:src/config.ts
  - meeting-bot:docs/transcription.md
  - meeting-bot:README.md
  - conversation-agent:orchestration/.../config/MeetingBotConfig.java
  - conversation-agent:orchestration/.../model/BotConfig.java
  - conversation-agent:docs/workspace-platform-routing.md
  - conversation-agent:docs/workspace-bot-identity.md
  - conversation-agent:docs/meeting-bot-end-state-policy.md
  - conversation-agent:docs/user-management.md
  - conversation-agent:docs/license-tiers-and-session-auth.md
last-verified: 2026-08-25
---

# FAQ

## Quick answers

| Question | Short answer |
|---|---|
| Does it join Zoom meetings? | **Yes** — Zoom, Teams, and Google Meet, including other companies' meetings |
| Why didn't it record my meeting? | Almost always: nobody admitted it within ~5 minutes |
| Can I stop it recording something sensitive? | Yes — type **`@Krista pause`** in the meeting chat, or remove it from the meeting |
| Where is my transcript? | In Meeting Agent, on the meeting itself |
| How long is the recording limit? | 3 hours |
| Where do I get help? | In-product help first, then your IT contact, then Krista Support |

---

## Getting help

**Where should I go when I have a question?**

There is a defined escalation path. Use it in order:

1. **In-product help.** There is a help icon on the Meeting Agent screen — a small
   question-mark icon. Open it and search. The main screen's help also carries
   walkthrough videos. Most "what does this setting do?" questions are answered
   here in seconds.
2. **Your organization's Meeting Agent / IT contact.** They own your
   configuration — which meetings are captured, who has a seat, what the bot is
   called.
3. **Krista Support**, reached through your IT contact.

Please try step 1 before step 2. A large share of questions are answered by
searching the in-product help for the word you are stuck on.

**What does the "automatic" toggle mean?**

Search **`automatic`** in the in-product help — it explains that setting exactly
where you are looking at it. This is the pattern worth learning: the help search
covers the settings screens in detail, and it is faster than asking.

> **OPEN —** Reproduce the "automatic" toggle in the current build and write the
> plain-language definition here, so this page answers it directly rather than
> redirecting. · _ask: Meeting Agent product owner_

---

## In the meeting

**Can I talk to it during the meeting?**

Yes — through the **meeting chat**, by mentioning the bot by name. It does not
speak, and it does not interrupt, but it reads chat messages addressed to it and
acts on them.

Type `@Krista help` in the chat to see the commands. (Substitute whatever your
organization named the bot — the help text uses its actual name.)

**What commands can I use?**

| Command | What it does |
|---|---|
| `@Krista pause` | Stop transcribing |
| `@Krista resume` | Start transcribing again |
| `@Krista opt out` | Keep the meeting off the record |
| `@Krista remove last X minutes` | Delete the last X minutes of content |
| `@Krista help` | Show this list in the chat |

These are your live privacy controls. If a meeting turns sensitive, you do not
have to remember afterwards to ask an administrator to delete something —
`pause` it in the moment, `resume` when you are past it, or use
`remove last 5 minutes` if something has already been said.

**Can it do more than that?**

If your organization has built Krista conversations, yes — you can ask questions,
create tasks, and trigger workflows from the meeting chat, for example
`@Krista schedule a follow-up meeting with John`. What is available depends
entirely on what your team has built. Ask your Krista contact what is wired up
for you.

It only responds to active participants in the meeting.

**It posted a message when it joined. Can we turn that off?**

The welcome message introduces the bot and tells participants how to use the
commands above — particularly the opt-out. Most organizations keep it for exactly
that reason. Ask your administrator if you want it changed.

**Will people see it?**

On Zoom, Google Meet, and Teams meetings it joins as a guest, so yes — it appears
in the participant list. The native Teams route for your own internal meetings
adds no participant at all.

**What is it called?**

By default `Krista (<Your Workspace Name>)`, so attendees can tell which team's
bot joined. Your administrator can rename it to anything.

**Why does Teams say "Unverified"?**

That is Teams' standard label for a guest who joined without signing in. It is
not a warning about the bot.

**Why does it turn up before the meeting starts?**

It joins about a minute before the scheduled start so recording is running before
the first person speaks. It is prepared behind the scenes about ten minutes
ahead of that.

**What if nobody lets it in?**

It waits about **5 minutes**, then leaves, and the meeting is marked skipped.
This is the most common reason a meeting is missing — and often the host was not
refusing, just running late.

**What if I remove it mid-meeting?**

Recording stops and the partial capture is **discarded**, not processed. That is
the right move when a meeting turns sensitive and you want nothing kept. If you
only want part of it off the record, `pause` or `remove last X minutes` is the
finer tool.

**What if everyone leaves but the meeting stays open?**

The bot leaves after a minute alone. If nobody joins at all, it waits 5 minutes
and leaves.

---

## After the meeting

**I'm not seeing my transcript. Where do I look?**

Open Meeting Agent and find the meeting — the transcript, summary, and action
items live on the meeting itself.

If it is not there, work down this list before raising a ticket:

1. **Is the meeting listed at all?** If not, it never reached Meeting Agent. The
   usual cause is that nobody on the invitation is a licensed user — an
   Observer's presence does not pull a meeting in. Ad-hoc meetings that were
   never on the calendar are also invisible.
2. **Is it marked skipped?** Then there is correctly nothing to show. Read the
   reason — most often the bot was never admitted.
3. **Did someone remove the bot, or use `opt out`?** Then the content was
   discarded on purpose.
4. **Was it a WebEx or GoTo meeting?** Not supported, so it was skipped.
5. **Has it finished processing?** Transcription and summarization run after the
   meeting ends, so give it a little time before concluding it failed.

If none of those apply, ask your IT contact — see [getting help](#getting-help).

**How long until my summary and action items appear?**

Processing starts once the meeting ends and runs through transcription, summary,
and action items in sequence.

> **OPEN —** Publish a measured, customer-facing expectation here. This is one of
> the two most-asked questions and it currently has no stated answer. · _ask:
> Meeting Agent product owner_

**Is there a maximum meeting length?**

Yes — **3 hours**. The bot leaves at that point and the meeting is processed
normally, so you get everything up to the cap rather than nothing. If you
routinely run all-day sessions, raise it with your Krista TAM before relying on
it.

**What happens in a long silence?**

After about 5 minutes of sustained dead air the bot leaves, and the meeting is
processed as normal.

**What if the meeting was cut short?**

It is still processed, with a notice that the transcript may be incomplete.

---

## Platforms

**Does Meeting Agent join Zoom meetings?**

Yes. Zoom is fully supported, including meetings hosted by other organizations.
Nothing is installed in Zoom, no Marketplace app is needed, and the host does not
have to be a Krista customer.

**Which platforms are supported?**

Microsoft Teams, Google Meet, and Zoom. WebEx, GoTo, and everything else are not
supported — those meetings are marked skipped.

**Can it join a meeting hosted by another company?**

Yes, on all three supported platforms. Someone in the meeting has to admit it,
exactly as with any guest.

**Do we need to install anything?**

Not for the Krista Bot — it joins as a guest via the meeting link. The native
Teams route for your own meetings is set up with your Krista TAM during
onboarding.

**Can it join a meeting that isn't on the calendar?**

No. Meeting Agent works from your connected calendar.

---

## Transcripts and quality

**How does it transcribe?**

It prefers the meeting platform's own live captions. If captions could not be
enabled or produced nothing, it transcribes the recorded audio instead. Either
way you get a transcript.

**Why do Teams transcripts look more detailed than Zoom or Meet?**

Different platforms group captions differently. Teams produces one segment per
utterance; Meet and Zoom group an uninterrupted speaker's sentences into a single
block. Content and attribution are complete in all three — only the chunking
differs.

**Does it start Teams transcription?**

No, deliberately. That would notify every participant and write a transcript file
to the organizer's OneDrive. Meeting Agent captures via captions instead.

**Does it read Google's post-meeting Drive transcripts?**

No. Its transcript comes from captions captured live.

**How do I get better transcripts and summaries?**

Make sure captions are on, introduce speakers on external calls, and state
decisions and action items out loud with an owner. Summaries reflect what was
said explicitly — a decision everyone nodded at does not become a decision in the
summary. On Zoom meetings you host, enable full transcript viewing on your Zoom
account.

---

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

They apply on the next scheduling cycle, about a minute. Capture is arranged on
the day a meeting runs, so a change saved this morning governs this afternoon.
Meetings that already ran are never re-routed.

**Why did several bots join the same meeting?**

More than one of your workspaces picked up that meeting and each sent its own
bot. Set the internal bucket to `Microsoft Teams` or `None` on the workspaces
that do not need to capture it.

**Who can change these settings?**

Users with the **Meeting Agent Admin** (Workspace Admin) role. Everyone else sees
them read-only.

---

## Users and licensing

**What is the difference between a licensed user and an Observer?**

A licensed user consumes a paid seat, their calendar is synced, and their
meetings are captured. An Observer is free, can view content shared with them,
and their calendar is **not** synced.

**A meeting with only Observers wasn't captured. Why?**

By design. An Observer's presence on an invitation does not pull a meeting into
the workspace. At least one licensed user must be on it.

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
for you. If you expect large peaks, raise it with your TAM as a capacity question
rather than assuming either that a limit protects you or that none affects you.

---

## Data and privacy

**Where do recordings and transcripts go?**

Ask your Krista TAM. Storage location, retention, and sub-processor detail are
answered directly for your deployment, because they depend on how your workspace
is provisioned.

**Are participants notified?**

The bot is visible in the participant list, it posts a welcome message explaining
how to opt out, and platforms show their own recording indicators. Whether that
is sufficient notification for your jurisdiction and policy is a decision your
organization must make.

**How do I keep something off the record?**

Three options, from finest to bluntest:

- `@Krista pause` … `@Krista resume` — exclude part of a meeting
- `@Krista remove last X minutes` — delete something already said
- `@Krista opt out`, or remove the bot from the meeting — nothing from that
  meeting is kept

**Can we exclude specific meetings entirely?**

Keep them off the connected calendar, or route their bucket to `None`.

**Is this a compliance recording system?**

No. It is not designed to guarantee capture of every meeting for regulatory
retention.

---

## When something goes wrong

**What is the difference between "skipped" and "failed"?**

Skipped means there was correctly nothing to process — nobody admitted the bot,
capture was off, the platform is unsupported. Failed means a technical fault, and
it is replayable. Skipped is usually yours to fix; failed is usually ours.

**A meeting wasn't recorded. Where do I start?**

[Troubleshooting](05-troubleshooting.md). Start with the meeting's status — it
tells you whether the cause is yours or ours.

**Who do I escalate to?**

In-product help, then your IT contact, then Krista Support through them. See
[getting help](#getting-help).
