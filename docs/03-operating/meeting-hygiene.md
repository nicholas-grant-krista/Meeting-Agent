---
audience: end user — hand this out as a one-pager
product-version: "2.1"
sources:
  - conversation-agent:docs/meeting-bot-end-state-policy.md
  - meeting-bot:src/observers/chat.ts
  - meeting-bot:docs/transcription.md
last-verified: 2026-08-25
---

# Getting the best from Krista

Krista joins your meetings and turns them into notes, summaries, and action
items. There's nothing you have to do differently — but a few small habits make
her noticeably more useful.

## Let her in

If your meeting has a lobby or waiting room, Krista waits there like any other
guest until someone lets her in.

She waits about **5 minutes**. She arrives just before the scheduled start, so if
a meeting tends to begin ten minutes late and guests are admitted once everyone's
gathered, she may already have left. Letting her in when you spot her is the one
habit that matters most.

You'll see her in the participant list under whatever name your organization has
given her — often something like `Krista (Acme)`. Teams may label her
"Unverified", which simply means she joined as a guest.

If nobody lets her in, the meeting isn't recorded. It's the most common reason
someone finds a meeting missing later.

## Ask her for what you need

You can talk to Krista in the **meeting chat**. She won't speak or interrupt, but
she reads anything addressed to her.

| Ask her | And she'll |
|---|---|
| `@Krista pause` | Stop transcribing |
| `@Krista resume` | Pick up again |
| `@Krista opt out` | Keep the meeting off the record |
| `@Krista remove last 5 minutes` | Delete what was just said |
| `@Krista help` | List these in the chat |

Use the name you see in the participant list, and `help` any time you'd like the
list again.

**These are yours whenever you want them.** If a conversation moves somewhere
sensitive, you don't need to remember to ask anyone afterwards — pause her, and
resume when you're past it.

If your team has built Krista conversations, you can also ask her things directly:
`@Krista schedule a follow-up meeting with John`. Your Krista contact can tell you
what's set up for you.

## Turn captions on

Krista works best from the meeting platform's own live captions. She usually turns
them on herself, and doing it yourself is a reliable backup when a meeting really
matters:

- **Teams** — More actions → Language and speech → Turn on live captions
- **Google Meet** — the **CC** button, or More options → Turn on captions
- **Zoom** — Show Captions

## Say the things you want captured

She records who spoke and what was said — she can't record what was meant.

- Introducing people at the start of external meetings helps her attribute
  correctly.
- Saying decisions out loud gets them into the summary. "So we're going with
  option B" lands; everyone nodding doesn't.
- Naming action items with an owner is what turns them into tracked actions:
  "Priya will send the revised quote by Thursday."

## A note on removing her

If you remove Krista from a meeting, everything recorded up to that point is
discarded rather than kept — a clear way to say you'd like nothing from that
conversation retained.

If you'd rather keep most of the meeting and set aside only part of it, pausing
or removing the last few minutes is the gentler option.

For meetings that shouldn't be captured at all, your administrator can arrange
that in advance.

## Worth knowing

- She joins meetings from your calendar, so ad-hoc meetings won't include her.
- She doesn't speak or join the conversation — chat only.
- She supports Teams, Google Meet, and Zoom. WebEx and GoTo meetings are skipped.
- She's visible on Zoom, Meet, and external Teams meetings, so guests will see
  her and may ask.

## What happens when

| | |
|---|---|
| Nobody lets her in within ~5 minutes | Not recorded, marked skipped |
| You pause her | Transcribing stops until you resume |
| You ask her to opt out | The meeting is kept off the record |
| You remove her | Recording discarded, nothing processed |
| The meeting ends normally | Transcript, summary, action items |
| The meeting runs past 3 hours | Everything up to 3 hours is captured and processed |
| Everyone leaves, meeting stays open | She leaves after a minute |
| The call drops early | Processed, with a note that the transcript may be incomplete |
| Captions weren't available | Still transcribed, just a different route |
| It's a WebEx or GoTo link | Skipped — not supported |

## Where to get help

The **?** icon in the top-right corner opens the built-in User Guide, with short
video tutorials covering the dashboard, meeting templates, and how Krista takes
part in your meetings. Searching it for whatever you're stuck on is usually the
quickest route.

Not set up yet, or your meetings aren't showing? [Setting yourself
up](../02-setup/first-time-registration.md) covers it.

Your organization's Krista or IT contact looks after naming, which meetings are
captured, and access. They can bring in Krista Support if anything needs going
further.

---

*More questions: [the FAQ](../04-faq.md)*
