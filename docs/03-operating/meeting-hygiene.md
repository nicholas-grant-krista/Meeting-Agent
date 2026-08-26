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
action items. A few habits make the difference between output you trust and
output you ignore.

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

## 4. Learn the chat commands — they're your privacy controls

You can direct Meeting Agent from the **meeting chat** by mentioning it by name.
It never speaks, but it reads messages addressed to it.

| Type this in the chat | What happens |
|---|---|
| `@Krista pause` | Stops transcribing |
| `@Krista resume` | Starts transcribing again |
| `@Krista opt out` | Keeps the whole meeting off the record |
| `@Krista remove last 5 minutes` | Deletes what was just said |
| `@Krista help` | Lists the commands in the chat |

Use your organization's name for the bot — whatever appears in the participant
list.

**This is the part worth remembering.** If a meeting turns sensitive, you do not
have to remember afterwards to ask someone to delete it. Pause in the moment,
resume when you're past it, or remove the last few minutes if it's already been
said.

If your team has built Krista conversations, you can also ask it things —
`@Krista schedule a follow-up meeting with John`. Ask your Krista contact what's
available to you.

## 5. Don't kick the bot out — unless you mean it

If you remove Meeting Agent from a meeting, **the recording up to that point is
discarded**, not saved. It is treated as a clear instruction that you do not want
the content kept.

That is the right move when you want nothing kept at all. If you only want part
of the meeting off the record, `pause` or `remove last X minutes` is the better
tool — removing the bot is all-or-nothing.

If you know in advance a meeting should not be captured, keep it off the
connected calendar or ask your admin about exclusions.

## 6. Know what it does not do

- It **does not join ad-hoc meetings** — only ones on a connected calendar.
- It **does not speak** or join the spoken conversation. Chat only.
- It **does not support WebEx or GoTo**. Those meetings are skipped.
- It **is visible**. On Zoom, Meet, and external Teams meetings, everyone can see
  it is there. Assume your guests will notice and ask.

## Quick reference

| Situation | What happens |
|---|---|
| Nobody admits the bot within ~5 minutes | Not recorded. Marked skipped. |
| You remove the bot mid-meeting | Recording discarded. Nothing processed. |
| You type `@Krista pause` | Transcription stops until you `resume`. |
| You type `@Krista opt out` | The meeting is kept off the record. |
| Meeting ends normally | Transcript, summary, action items. |
| Your meeting runs past 3 hours | Captured up to 3 hours, then the bot leaves. Everything up to that point is processed. |
| Everyone leaves but the meeting stays open | Bot leaves after a minute. |
| The call drops or is cut short | Processed, with a note that the transcript may be incomplete. |
| Captions were unavailable | Still transcribed, just by a different route. |
| The link is WebEx or GoTo | Skipped — not supported. |

## Where to get help

In this order:

1. **The in-product help.** There's a question-mark icon on the Meeting Agent
   screen — open it and search for the word you're stuck on. The main screen's
   help also has walkthrough videos. Try this first; most questions are answered
   here in seconds.
2. **Your organization's Meeting Agent / IT contact.** They handle bot naming,
   which meetings are captured, and whether recording is on for your team.
3. **Krista Support**, through that contact.

---

*Longer version: [FAQ](../04-faq.md)*
