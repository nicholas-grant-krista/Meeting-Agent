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

# Questions people ask

Welcome — this page covers what comes up most often once Krista starts joining
your meetings. Nothing here needs reading end to end; it's here for the moment
you have a question.

## The short answers

| | |
|---|---|
| Does Krista join Zoom meetings? | Yes — Zoom, Teams, and Google Meet, including other companies' meetings |
| Why wasn't my meeting recorded? | Usually she was waiting in the lobby and wasn't let in |
| Can I keep something private? | Yes — just ask her in the meeting chat |
| Where's my transcript? | On the meeting itself, in Krista |
| How long can a meeting be? | Up to 3 hours |
| Where can I get help? | The help icon in Krista, then your IT contact |

---

## Finding help

**Where's the best place to start when I have a question?**

There's a help icon on the Krista screen — the small question mark. Searching
there for whatever you're stuck on is usually the quickest route, and the main
screen's help also has some short walkthrough videos.

If that doesn't cover it, your organization's Krista or IT contact looks after
your setup — which meetings Krista joins, who has access, what she's called in
the participant list. They can reach Krista Support directly if anything needs
escalating.

**What does the "automatic" toggle do?**

Searching **`automatic`** in the help icon will explain that setting right where
you're looking at it. It's a useful habit generally — the in-product help covers
the settings screens in more detail than this guide can.

> **OPEN —** Reproduce the "automatic" toggle in the current build and write the
> plain-language definition here, so this page answers it directly rather than
> pointing elsewhere. · _ask: Meeting Agent product owner_

---

## Krista in your meeting

**Can I talk to her during a meeting?**

You can, through the **meeting chat**. She won't speak or interrupt, but she reads
messages addressed to her and acts on them.

Mentioning her with `help` — `@Krista help` — brings up the list in the chat
whenever you need it. She'll use whatever name your organization has given her, so
use the name you see in the participant list.

**What can I ask her to do?**

| Ask her | And she'll |
|---|---|
| `@Krista pause` | Stop transcribing |
| `@Krista resume` | Pick up again |
| `@Krista opt out` | Keep the meeting off the record |
| `@Krista remove last 5 minutes` | Delete what was just said |
| `@Krista help` | List these in the chat |

These are yours to use whenever you'd like. If a conversation turns sensitive,
you don't need to remember to ask someone afterwards to delete anything — you can
pause her in the moment and resume when you're past it, or have her remove the
last few minutes if something's already been said.

**Can she do more than that?**

If your team has built Krista conversations, yes — you can ask her questions,
create tasks, and start workflows right from the meeting chat, along the lines of
`@Krista schedule a follow-up meeting with John`. What's available depends on
what your team has set up, so your Krista contact is the best person to ask.

She responds to people who are active in the meeting.

**She posted a message when she joined — can that be changed?**

That's her introduction, and it lets everyone know how to ask her to pause or opt
out. Most teams like to keep it for that reason, but your administrator can adjust
it if you'd prefer something different.

**Will people see her?**

On Zoom, Google Meet, and Teams meetings she joins as a guest, so she appears in
the participant list. For internal Teams meetings captured natively there's no
extra participant at all.

**What is she called?**

By default `Krista (Your Workspace Name)`, which helps people tell which team's
Krista has joined. Your administrator can give her any name that suits you better.

**Why does Teams show her as "Unverified"?**

That's just how Teams labels any guest who joins without signing in. Nothing is
wrong.

**Why does she arrive before the meeting starts?**

She joins about a minute early so she's ready before the first person speaks — and
she's getting ready quietly for about ten minutes before that.

**What happens if nobody lets her in?**

She waits around **5 minutes** and then leaves, and the meeting is marked as
skipped. This is the most common reason a meeting turns out not to be recorded,
and it's usually nothing deliberate — the host simply hadn't arrived yet.

**What if someone removes her from a meeting?**

She stops, and anything recorded up to that point is discarded rather than kept.
It's a clear way to say you'd like nothing from that conversation retained. If
you'd rather keep most of the meeting and set aside just part of it, pausing or
removing the last few minutes is the gentler option.

**What if everyone leaves but the meeting stays open?**

She'll wait a minute on her own and then leave. If nobody joins at all, she waits
5 minutes before heading off.

---

## After the meeting

**I can't find my transcript — where should I look?**

Everything lives on the meeting itself in Krista: transcript, summary, and action
items together.

If the meeting isn't showing what you expected, a few things are worth a quick
look:

- **Is the meeting there at all?** If not, it may not have reached Krista.
  Meetings come in through the calendars of licensed users, so if nobody on the
  invitation has a licence — or the meeting was ad-hoc and never in a calendar —
  Krista won't have seen it.
- **Is it marked skipped?** Then there's genuinely nothing to show, and the reason
  will say why. Most often she wasn't let in.
- **Did someone remove her, or ask her to opt out?** Then the content was set aside
  on purpose.
- **Was it a WebEx or GoTo meeting?** Those aren't supported, so it was skipped.
- **Has it had a moment to process?** Transcription and summarizing happen after
  the meeting ends, so it's worth giving it a little time.

If none of those explain it, your IT contact can help — see
[finding help](#finding-help).

**How soon will my summary and action items be ready?**

It depends on the meeting — longer, more complex conversations naturally take
longer than a short catch-up. Processing begins as soon as the meeting ends and
works through transcription, summary, and action items in turn.

> **OPEN —** Replace this with a measured, customer-facing expectation. Nick is
> sourcing the real figure. · _ask: Meeting Agent product owner_

**Is there a limit on meeting length?**

She'll capture up to **3 hours**. At that point she leaves and the meeting is
processed as normal, so you keep everything up to that mark. If long workshops
are a regular thing for you, it's worth mentioning to your Krista contact early.

**What happens during a long silence?**

After about 5 minutes of quiet she'll leave, and the meeting is processed as
usual.

**What if a meeting gets cut short?**

It's still processed, with a note that the transcript may be incomplete.

---

## Meeting platforms

**Does Krista join Zoom meetings?**

She does. Zoom is fully supported, including meetings hosted by other
organizations. There's nothing to install in Zoom, and the host doesn't need to be
a Krista customer.

**Which platforms does she support?**

Microsoft Teams, Google Meet, and Zoom. WebEx, GoTo, and others aren't supported,
and those meetings are simply marked as skipped.

**Can she join a meeting hosted by another company?**

Yes, on all three platforms. Someone in the meeting just needs to let her in, the
same as any other guest.

**Is there anything to install?**

Not for meetings she joins as a guest — she uses the meeting link. Native Teams
capture for your own meetings is set up with your Krista contact during
onboarding.

**Can she join a meeting that isn't in a calendar?**

Not at the moment — she works from your connected calendar.

---

## Transcripts and quality

**How does she transcribe?**

She prefers the meeting platform's own live captions. If captions aren't available,
she transcribes the recording herself instead. Either way you'll get a transcript.

**Why do Teams transcripts look more detailed than Zoom or Meet?**

The platforms group their captions differently. Teams gives one segment per
utterance, while Meet and Zoom gather an uninterrupted speaker's sentences into a
single block. All three are complete and correctly attributed — the shape just
differs.

**Does she start Teams' own transcription?**

She doesn't, on purpose — that would notify everyone in the meeting and save a
separate transcript into the organizer's OneDrive. She works from captions
instead.

**Does she pick up Google's post-meeting Drive transcripts?**

No — her transcript comes from the captions she captures live.

**Anything that helps her do a better job?**

A few small things go a long way. Captions being on helps most. Introducing people
on external calls improves how well she attributes who said what. And saying
decisions and actions out loud — "Priya will send the revised quote by Thursday" —
is what turns them into action items. She works from what was said, so a decision
everyone nodded along to won't make it into the summary.

If you host your own Zoom meetings, enabling full transcript viewing on your Zoom
account gives her a cleaner source to work from.

---

## Setup and administration

**How does Krista decide if a meeting is "internal" or "external"?**

Internal means a Microsoft Teams meeting organized by someone on one of your own
domains. Everything else counts as external, and the two can be handled
differently.

**Can we capture internal meetings but not customer calls?**

Yes — internal and external are configured separately, and either can be turned
off entirely.

**Can we pause everything without losing our configuration?**

You can. Setting both to `None` means nothing is captured, while meetings still
appear and are marked as skipped. It's reversible whenever you're ready.

**How quickly do routing changes take effect?**

Within about a minute. Capture is arranged on the day each meeting runs, so a
change saved this morning applies to this afternoon. Meetings that have already
happened are left exactly as they were.

**Why did several Kristas join the same meeting?**

More than one of your workspaces picked up that meeting, and each sent its own.
Your administrator can set the internal option to `Microsoft Teams` or `None` for
the workspaces that don't need to capture it.

**Who can change these settings?**

Anyone with the **Meeting Agent Admin** role. Everyone else can see them, which
often helps when you're trying to understand why something behaved the way it did.

---

## Access and licensing

**What's the difference between a licensed user and an Observer?**

A licensed user has a seat, their calendar is connected, and their meetings are
captured. An Observer can view what's shared with them at no cost, and their
calendar isn't connected.

**A meeting with only Observers wasn't captured — is that right?**

It is. Meetings come in through licensed users' calendars, so at least one person
on the invitation needs a licence.

**Can our Krista contact help without using up a seat?**

Yes — as a Delegate Admin, which carries admin access without a paid seat.

**What happens when a trial ends?**

Access stops on the expiry date, for people and integrations alike, so it's worth
noting the date early and talking to your Krista contact before it arrives.

**Does a trial limit how much we can record?**

No — trials have the same capability and the same limits as a full licence. The
only difference is the expiry date.

**Is there a limit on how many meetings can run at once?**

Not one set by the product. The practical ceiling is the capacity of the
environment Krista runs in, so if you're expecting a big peak — a company-wide
slot where a lot of meetings begin together — it's worth flagging to your Krista
contact so they can size for it.

---

## Privacy

**Where do recordings and transcripts live?**

Your Krista contact can walk you through this for your specific setup, since it
depends on how your workspace is provisioned.

**Are participants told she's there?**

She appears in the participant list, introduces herself in the chat with how to
opt out, and the meeting platform shows its own recording indicator. Whether
that's the right level of notice for your organization and jurisdiction is a
decision your team will want to make — your Krista contact can help you think it
through.

**How do I keep something off the record?**

Whichever suits the moment:

- `@Krista pause` … `@Krista resume` — set aside part of a meeting
- `@Krista remove last 5 minutes` — remove something already said
- `@Krista opt out`, or removing her from the meeting — nothing from that
  conversation is kept

**Can we exclude certain meetings entirely?**

Yes — either by keeping them out of the connected calendar, or by turning off
capture for that category of meeting.

**Is this a compliance recording system?**

It isn't designed for regulatory retention, so if you have obligations of that
kind it's worth raising them early with your Krista contact.

---

## If something doesn't look right

**What's the difference between "skipped" and "failed"?**

Skipped means there was correctly nothing to capture — she wasn't let in, capture
was off, or the platform isn't supported. Failed means something went wrong
technically, and it can be run again. Skipped is usually something on your side;
failed is usually ours.

**A meeting wasn't recorded — where do I start?**

The meeting's status is the quickest clue, and
[troubleshooting](05-troubleshooting.md) walks through what each one means.

**Who should I go to?**

The help icon in Krista first, then your IT contact, who can bring in Krista
Support if it's needed.
