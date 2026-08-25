---
audience: executive / champion, IT admin
product-version: "2.1"
sources:
  - conversation-agent:README.md
  - conversation-agent:docs/workspace-platform-routing.md
  - conversation-agent:docs/meeting-bot-end-state-policy.md
  - meeting-bot:README.md
  - meeting-bot:docs/transcription.md
last-verified: 2026-08-24
---

# How it works

The lifecycle of a single meeting, start to finish.

```
  Calendar                Capture                  Post-meeting
  ────────                ───────                  ────────────
  Meeting                 Join / attach            Transcript
  appears        ──►      Record            ──►    Summary
  Routed to a             Capture speakers,        Action items
  capture route           chat, captions           Follow-up actions
```

## 1. The meeting is picked up

Meeting Agent reads your connected calendar. When a meeting appears, it is
**routed** — assigned to a capture route based on which bucket it falls into:

- **Internal** — a Microsoft Teams meeting whose organizer is on one of your
  organization's domains.
- **External** — everything else. A Google Meet or Zoom link, or a Teams meeting
  organized by someone outside your organization.

Each bucket resolves independently to native Teams capture, the Krista Bot, or
off. Recurring series are picked up in advance, sometimes weeks ahead.

> **Changing routing takes effect on future meetings, not past ones.** If you
> change a bucket's route, every meeting that has not yet started is re-routed on
> the next scheduling cycle — no restart or waiting period. Meetings that have
> already run are frozen and are never re-routed, so your history always reflects
> what actually happened.

## 2. The meeting is captured

### If routed to the Krista Bot

The bot is prepared shortly before the scheduled start, joins the meeting URL,
and requests admission. From your attendees' point of view it is a participant in
the roster with a display name you control — by default `Krista (<Your Workspace
Name>)`, which is how attendees can tell which team's bot joined.

Once admitted, it records and captures participants, chat, and live captions. It
reports progress continuously, so the meeting's status is visible while it is
still running.

The bot leaves when the meeting ends, everyone else leaves, a silence timeout is
reached, or a maximum duration cap is hit.

### If routed to native Teams

Capture happens through Microsoft Teams directly. No extra participant appears in
the meeting and there is no lobby to clear. This route only works for Teams
meetings your own organization hosts.

## 3. Speech becomes a transcript

Meeting Agent prefers the **meeting platform's own captions**. They are produced
by the platform's speech recognition, already attributed to speakers, and cost
nothing extra.

If captions could not be turned on, or produced nothing, Meeting Agent falls back
to transcribing the recorded audio itself. The result is the same kind of
transcript; it simply takes a different path to get there.

The practical consequence for you: **meetings where captions work produce better
and faster results.** See [meeting hygiene](../03-operating/meeting-hygiene.md).

How captions are structured differs by platform, which affects how granular the
transcript looks:

| Platform | Transcript granularity |
|---|---|
| Microsoft Teams | Per utterance — the finest of the three |
| Google Meet | Per speaker turn — one long block per uninterrupted speaker |
| Zoom | Per speaker turn |

All three are accurate. Meet and Zoom simply group more sentences into each
block.

## 4. Post-meeting actions run

With a transcript in hand, the post-meeting workflow runs: transcript stored,
knowledge ingested, summary generated, action items extracted, and the follow-up
actions configured for your workspace executed.

## What happens when something goes wrong

Meeting Agent distinguishes deliberately between *"this could never have worked"*
and *"this broke."* You will see the difference in the meeting's status.

| What happened | Outcome |
|---|---|
| Meeting ended normally | Full processing |
| Bot was interrupted mid-call | Processed, with a notice that the transcript may be incomplete |
| Bot was removed by a participant | **Skipped** — partial capture is discarded, not processed |
| Bot was never admitted from the lobby | **Skipped** — nothing was recorded |
| Meeting Agent was turned off for this meeting | **Skipped** |
| Meeting link was not a supported platform | **Skipped** |
| The bot hit a technical fault | **Failed** — flagged for attention, and replayable |

"Skipped" means there was correctly nothing to process. "Failed" means something
went wrong that Krista should look at. See
[troubleshooting](../05-troubleshooting.md) for what to do about each.

> Note the deliberate choice on **removal**: if someone kicks the bot out of a
> meeting, any partial recording is discarded rather than processed. Removing the
> bot is treated as a clear instruction not to keep the content.

---

**Next:** [Capabilities matrix](capabilities-matrix.md) · [Prerequisites](../02-setup/prerequisites.md)
