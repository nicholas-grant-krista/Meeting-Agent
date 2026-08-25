---
audience: IT admin
product-version: "2.1"
sources:
  - conversation-agent:orchestration/.../config/MeetingBotConfig.java
  - conversation-agent:orchestration/.../model/BotConfig.java
  - conversation-agent:orchestration/.../scheduler/MeetingBotSchedulingJob.java
  - conversation-agent:core/.../config/ApplicationConfig.java
  - meeting-bot:src/config.ts
last-verified: 2026-08-25
---

# Limits and quotas

> **These are the current defaults.** Krista operates the deployment and can tune
> most of these per environment, so confirm the values that matter to you with
> your Krista TAM rather than treating this page as a contract.

## Meeting timing

| Behaviour | Default |
|---|---|
| **Maximum meeting duration** | **3 hours.** The bot leaves and the meeting is processed normally. |
| **Silence timeout** | **5 minutes** of sustained dead air ends the bot's attendance. |
| **Waiting room / lobby wait** | **5 minutes.** If nobody admits the bot in that time, the meeting is marked skipped as never admitted. |
| **Nobody joins the meeting** | The bot leaves after **5 minutes**. |
| **Everyone else leaves** | The bot leaves after **1 minute**. |
| **Bot prepared before start** | **10 minutes** before the scheduled start time. |
| **Bot joins** | **60 seconds** before the scheduled start, to reduce dead air at the top of the recording. |

Two of these are worth planning around:

**The 3-hour cap.** All-day workshops, training sessions, and long incident calls
will be cut at three hours. The meeting is still processed — you get a transcript,
summary, and action items for the first three hours — but the tail is not
captured. If you routinely run longer sessions, raise it with your TAM before you
rely on it.

**The 5-minute lobby wait.** If your meetings habitually start late and the host
admits guests only once they arrive, the bot may have already given up. Admitting
it promptly is the fix; see
[meeting hygiene](../03-operating/meeting-hygiene.md).

## Which meetings get a bot, and when

| | Default |
|---|---|
| Scheduling scope | **The current day.** Bots are scheduled for today's meetings, not for the whole future series. |
| Scheduling cycle | Every **60 seconds** |
| Meetings scheduled per cycle | **100** |
| Deploy retries before giving up | **3** |
| Recovery attempts per meeting | **1** |

The distinction that matters: recurring series are *seeded* into Meeting Agent
well in advance so you can see them coming, but a **bot is only scheduled on the
day**. Changing routing therefore affects tomorrow's instance of a daily series
even though that instance already existed as a calendar entry.

## Field limits

| Field | Limit |
|---|---|
| Bot display name | 255 characters |
| Bot avatar image URL | 1000 characters; must be `http`/`https` and point directly at an image |
| Transcript size | 1,000,000 characters — roughly 22 hours of speech, so the 3-hour duration cap binds first |

## Quotas

**There are no per-tier volume quotas.** Trial and production licenses have the
same capability and the same limits. A trial differs in exactly two ways: it has
a hard expiry date, and some environments admit only certain tiers.

**There is no meeting, minute, or recording quota** at any tier.

**Seats are tracked commercially, not enforced technically.** Each user carries a
licensed-seat flag that governs whether their calendar is synced, but there is no
numeric seat cap in the product. Agree your seat count contractually and audit it
yourself — see [users and roles](../02-setup/users-and-roles.md).

## Concurrency

**There is no configured limit on how many meetings Meeting Agent captures
simultaneously.** Each captured meeting gets its own isolated capture job, and
the product does not cap, queue, or throttle them.

The practical ceiling is the capacity of the environment Krista runs for you, not
a product setting. If you expect large simultaneous peaks — a company-wide
meeting slot where a hundred meetings start at once — raise it with your TAM as a
capacity question during onboarding. Do not assume a limit exists that will
protect you, and do not assume there is none that will affect you.

> **OPEN —** What simultaneous-capture volume is a given deployment sized for,
> and what does a customer see if that capacity is exceeded? This is the one
> genuine gap on this page. · _ask: Meeting Agent product owner + ops_

## Processing time after a meeting

**No target is published**, and none is configured in the product. Processing is
event-driven: capture finishes, then transcription, summary, action items, and
follow-up actions run in sequence.

The only bounds that exist are protective ceilings, not expectations — a
knowledge-ingest step that gives up after 90 minutes, and AI calls that time out
after 60 seconds and retry up to three times. None of those tell you what a
normal meeting takes.

> **OPEN —** State a customer-facing expectation for meeting-end to
> transcript / summary / action items — measured, not derived from timeouts. This
> is the second question every customer asks after "does it join Zoom." · _ask:
> Meeting Agent product owner_

## Platform limits outside Krista's control

These come from the meeting platforms, not from Meeting Agent:

- **Lobby and waiting-room policies** — set by the host or their organization. If
  the bot is not admitted within the wait window, it cannot record.
- **Host recording restrictions** — a host who has disabled recording by policy
  prevents capture.
- **Caption availability** — where a platform or host prevents captions, Meeting
  Agent falls back to transcribing recorded audio.
- **Zoom full transcript viewing** — controlled by the host's Zoom account
  settings, which affects transcript fidelity on Zoom.
