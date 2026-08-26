---
audience: end user — hand this out as a one-pager
product-version: "2.1"
sources:
  - conversation-agent:docs/meeting-bot-end-state-policy.md
  - meeting-bot:docs/transcription.md
last-verified: 2026-08-24
---

# Meeting hygiene — for everyone

Meeting Agent joins your meetings and turns them into notes, summaries, and
action items. Five habits make the difference between output you trust and output
you ignore.

## 1. Let the bot in

If your meeting has a lobby or waiting room, **someone has to admit Meeting
Agent** — it waits like any other guest.

**It waits about 5 minutes, then gives up.** That is the number to remember. It
arrives just before the scheduled start, so if your meeting habitually begins ten
minutes late and nobody admits guests until the host arrives, the bot is already
gone. Admit it when you see it, not when you're ready to start.

It appears in the participant list with your organization's chosen name (often
something like `Krista (Acme)`). On Teams it may be tagged **"Unverified"** —
that just means it joined as a guest, not that anything is wrong.

**If nobody admits it, the meeting is not recorded.** This is the single most
common reason someone says "it didn't work." On a recurring meeting, it fails
every time until someone changes the habit.

## 2. Turn on captions

Meeting Agent works best from the meeting platform's own live captions. Any
participant can turn them on:

- **Teams** — More actions → Language and speech → Turn on live captions
- **Google Meet** — the **CC** button, or More options → Turn on captions
- **Zoom** — Show Captions

It usually turns captions on itself. Doing it yourself is a reliable fallback
when a meeting matters.

## 3. Say who you are, and say what you decided

The transcript records who spoke. It cannot record what you meant.

- Introduce people at the start of external meetings — attribution improves.
- State decisions explicitly. "So we're going with option B" produces a decision
  in the summary. Everyone nodding does not.
- Say action items out loud with an owner: "Priya will send the revised quote by
  Thursday." That is what turns into a tracked action item.

## 4. Don't kick the bot out — unless you mean it

If you remove Meeting Agent from a meeting, **the recording up to that point is
discarded**, not saved. It is treated as a clear instruction that you do not want
the content kept.

That is the right behaviour when a meeting turns sensitive mid-way — removing the
bot is the correct move. Just know it is all-or-nothing: you cannot remove it and
keep the first half.

If you know in advance a meeting should not be captured, keep it off the
connected calendar or ask your admin about exclusions.

## 5. Know what it does not do

- It **does not join ad-hoc meetings** — only ones on a connected calendar.
- It **does not participate**. It will not answer questions or take instructions
  during the call.
- It **does not support WebEx or GoTo**. Those meetings are skipped.
- It **is visible**. On Zoom, Meet, and external Teams meetings, everyone can see
  it is there. Assume your guests will notice and ask.

## Quick reference

| Situation | What happens |
|---|---|
| Nobody admits the bot within ~5 minutes | Not recorded. Marked skipped. |
| You remove the bot mid-meeting | Recording discarded. Nothing processed. |
| Meeting ends normally | Transcript, summary, action items. |
| Your meeting runs past 3 hours | Captured up to 3 hours, then the bot leaves. Everything up to that point is processed. |
| Everyone leaves but the meeting stays open | Bot leaves after a minute. |
| The call drops or is cut short | Processed, with a note that the transcript may be incomplete. |
| Captions were unavailable | Still transcribed, just by a different route. |
| The link is WebEx or GoTo | Skipped — not supported. |

## Who to ask

Your Meeting Agent administrator handles bot naming, which meetings are captured,
and whether recording is on for your team.

---

*Longer version: [FAQ](../04-faq.md)*
