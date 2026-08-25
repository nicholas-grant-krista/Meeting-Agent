---
audience: executive / champion
product-version: "2.1"
sources:
  - conversation-agent:README.md
  - conversation-agent:release.info
  - meeting-bot:README.md
last-verified: 2026-08-24
---

# What is Meeting Agent?

Meeting Agent captures your meetings and turns them into work that actually gets
done.

It attends the meetings you tell it to, records and transcribes them, and then —
this is the part that distinguishes it from a notetaker — runs **post-meeting
actions**: summaries, action items, and follow-up work routed into the systems
your team already uses.

## The problem it solves

Most meeting tools stop at the transcript. Someone still has to read it, decide
what mattered, and go do something about it. In practice that step is skipped,
and the recording becomes an archive nobody opens.

Meeting Agent is built around the assumption that the transcript is an
*intermediate artifact*, not the deliverable. The deliverable is the follow-up.

## What it does

**Before the meeting** — watches your connected calendar, decides which meetings
are in scope, and prepares to capture them.

**During the meeting** — captures the conversation, either by joining as a
participant or by attaching to Microsoft Teams natively. It captures who spoke,
what was said, participants, and chat.

**After the meeting** — produces a transcript, then runs the post-meeting
workflow: summarize, extract action items, and execute the follow-up actions
configured for your workspace.

## The two capture routes

This is the single most important thing to understand, because it determines
what your attendees see and what you need to configure.

| | **Native Teams** | **Krista Bot** |
|---|---|---|
| How it captures | Attaches through Microsoft Teams itself | Joins the call as a participant |
| Do attendees see it? | No extra participant | **Yes** — a named participant in the roster |
| Works with | Teams meetings hosted by *your* organization | Teams, Google Meet, and Zoom — including meetings hosted by *other* organizations |
| Needs to be admitted? | No | Yes, if there is a lobby or waiting room |

You are not forced to pick one. Meeting Agent routes each meeting to one of these
based on two **buckets** you configure independently — internal meetings and
external meetings. A common setup is native Teams for your own meetings and the
Krista Bot for everything else. See
[Workspace configuration](../02-setup/workspace-configuration.md).

Either bucket can also be set to **off**, meaning that workspace does not capture
that class of meeting at all.

## What it is not

Being direct about this up front saves a difficult conversation in week three.

- **It is not a compliance recording system.** It is not designed to guarantee
  capture of every meeting for regulatory retention.
- **It is not a live assistant.** It does not participate in the conversation,
  answer questions in the room, or take instructions mid-meeting.
- **It does not work on every platform.** Teams, Google Meet, and Zoom are
  supported. WebEx, GoTo, and others are not — see the
  [capabilities matrix](capabilities-matrix.md).
- **It does not bypass a host who refuses it.** If nobody admits the bot from the
  lobby, the meeting is not recorded. This is by design.

## Where it fits

Meeting Agent runs on the Krista platform, so its output can feed anything Krista
can reach — your knowledge base, ticketing, CRM, or a custom workflow. For most
customers the starting point is much simpler: accurate summaries and action items
delivered reliably, to the right people, without anyone having to ask.

---

**Next:** [How it works](how-it-works.md) · [Capabilities matrix](capabilities-matrix.md)
