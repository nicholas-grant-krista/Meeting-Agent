---
audience: executive / champion, IT admin
product-version: "2.1"
sources:
  - conversation-agent:README.md
  - conversation-agent:docs/workspace-platform-routing.md
  - conversation-agent:docs/meeting-bot-end-state-policy.md
  - conversation-agent:orchestration/.../config/MeetingBotConfig.java
  - meeting-bot:README.md
  - meeting-bot:docs/transcription.md
last-verified: 2026-08-25
---

# How it works

The life of a single meeting, from calendar to follow-up.

```
  Calendar                Capture                  Afterwards
  ────────                ───────                  ──────────
  Meeting                 Krista joins             Transcript
  appears        ──►      and listens       ──►    Summary
  Routed to a             Speakers, chat,          Action items
  capture route           captions                 Follow-up actions
```

## 1. The meeting is picked up

Krista watches your connected calendar. When a meeting appears, it's sorted into
one of two groups:

- **Internal** — a Microsoft Teams meeting organized by someone on one of your own
  domains.
- **External** — everything else. A Google Meet or Zoom link, or a Teams meeting
  organized outside your organization.

Each group is handled independently: captured through Teams directly, captured by
Krista joining as a participant, or not captured at all. Recurring series appear
well in advance so you can see what's coming, and capture itself is arranged on
the day each meeting runs.

> Changing how a group is handled applies to future meetings, not past ones.
> Anything that hasn't started yet picks up the change within about a minute —
> no restart, no waiting period. Meetings that have already happened are left
> exactly as they were, so your history always reflects what really took place.

## 2. The meeting is captured

### When Krista joins as a participant

She gets ready about **10 minutes** before the scheduled start and joins around
**60 seconds** beforehand, so she's already listening when the first person
speaks. Your attendees see her in the participant list under a name you choose —
by default `Krista (Your Workspace Name)`, which helps people tell which team's
Krista has joined.

If there's a lobby, she waits **up to 5 minutes** to be let in. After that she
leaves, and the meeting is marked as skipped.

Once she's in, she records and picks up participants, chat, and live captions,
reporting as she goes so you can see the meeting's status while it's still
running.

She'll leave when:

| | |
|---|---|
| The host ends the meeting | Straight away |
| Everyone else leaves | After **1 minute** on her own |
| Nobody ever joins | After **5 minutes** |
| The room goes quiet | After **5 minutes** of silence |
| The meeting runs long | At **3 hours** |

All five wrap up normally — you'll get a transcript, summary, and action items
for what was captured.

### When capture runs through Teams

For internal Teams meetings, capture happens through Microsoft Teams itself. No
extra participant appears, and there's no lobby to clear. This route is available
for meetings your own organization hosts.

## 3. Speech becomes a transcript

Krista prefers the meeting platform's **own live captions**. They're produced by
the platform's speech recognition, already attributed to speakers, and cost
nothing extra.

If captions aren't available, she transcribes the recorded audio herself instead.
You get the same kind of transcript; she simply takes a different route to it.

What this means in practice: **meetings where captions are on give you better
results, sooner.** See
[getting the best from Krista](../03-operating/meeting-hygiene.md).

Each platform structures captions differently, which shows up in how the
transcript is grouped:

| Platform | How the transcript is grouped |
|---|---|
| Microsoft Teams | One segment per utterance — the finest of the three |
| Google Meet | One block per speaker turn |
| Zoom | One block per speaker turn |

All three are accurate. Meet and Zoom simply gather more sentences into each
block.

## 4. The follow-up runs

With a transcript in hand, the rest follows: the transcript is stored, knowledge
is taken in, a summary is generated, action items are pulled out, and whatever
follow-up your team has set up is carried through.

## Along the way — people stay in control

Anyone in the meeting can talk to Krista in the chat. `@Krista pause` and
`@Krista resume` bracket anything that shouldn't be captured, `@Krista remove last
5 minutes` deals with something already said, and `@Krista opt out` keeps the
whole meeting off the record. She explains these when she joins.

## When things don't go to plan

Krista distinguishes between *"there was correctly nothing to capture"* and
*"something went wrong"* — and you'll see the difference in the meeting's status.

| What happened | Outcome |
|---|---|
| The meeting ended normally | Processed in full |
| She was interrupted part-way | Processed, with a note that the transcript may be incomplete |
| Someone removed her | **Skipped** — anything partial is discarded rather than kept |
| Nobody let her in | **Skipped** — nothing was recorded |
| Capture was off for this meeting | **Skipped** |
| The link wasn't a supported platform | **Skipped** |
| Something failed technically | **Failed** — flagged for attention, and can be run again |

Skipped means there was genuinely nothing to process. Failed means something Krista
should look into. [Troubleshooting](../05-troubleshooting.md) covers what to do
with each.

> One deliberate choice worth knowing: if someone removes Krista from a meeting,
> anything recorded up to that point is discarded rather than processed. Removing
> her is treated as a clear signal that the content shouldn't be kept.

---

**Next:** [Capabilities matrix](capabilities-matrix.md) · [Prerequisites](../02-setup/prerequisites.md)
