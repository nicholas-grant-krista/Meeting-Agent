---
audience: IT admin
product-version: "2.1"
sources:
  - conversation-agent:docs/workspace-platform-routing.md
  - meeting-bot:docs/transcription.md
  - meeting-bot:README.md
last-verified: 2026-08-24
---

# Setup — Google Meet

Google Meet is captured by the **Krista Bot** only. There is no native route.

Because every Meet meeting is captured by the bot, and the bot only handles the
external bucket unless you route internal to it as well, Meet meetings fall into
the **external** bucket regardless of who organized them — the internal bucket is
defined as *Teams meetings with an internal organizer*.

## What to configure

Set the **external** bucket to `Krista Bot` in
[workspace configuration](workspace-configuration.md). That is the whole
Meet-specific configuration on the Krista side.

There is nothing to install in Google Workspace, and the meeting host does not
need to be a Krista customer.

## What your users will see

The bot joins as a guest. On Meet that means it **knocks** and someone in the
meeting must admit it — the same prompt any external guest produces.

If nobody admits it, the meeting is not recorded and is marked skipped. On a
recurring external meeting where the host habitually ignores the knock, this
happens every single time; see [meeting hygiene](../03-operating/meeting-hygiene.md)
for how to get ahead of it.

## Transcription on Meet

Meeting Agent turns on Meet's **live captions** and captures them. Any
participant can enable captions, so no special rights are needed.

**Transcript granularity is per speaker turn.** Meet groups an uninterrupted
speaker's sentences into a single block — a ten-minute monologue produces one
long segment rather than many short ones. The content is complete and correctly
attributed; it is simply chunked differently from Teams. Set expectations
accordingly if your users are comparing transcripts across platforms.

## What is not supported on Meet

**Google Workspace's own post-meeting transcripts are not ingested.** If your
Workspace tier generates a `.docx` transcript into the organizer's Drive after a
meeting, Meeting Agent does not read it. It has no Drive access, and that file
only exists after the call has ended. Meeting Agent's transcript comes from the
captions it captured live.

This means you may end up with two transcripts of the same meeting from two
systems. If that is undesirable, turn one of them off.

## Bot identity

Same as everywhere: display name defaults to `Krista (<Your Workspace Name>)`,
overridable per workspace, with an optional avatar image URL. See
[workspace configuration](workspace-configuration.md).

> **OPEN —** Does connecting a Google Workspace calendar require admin consent,
> and is Google Calendar supported as a calendar source at all? · _ask: Meeting
> Agent product owner_

---

**Next:** [Workspace configuration](workspace-configuration.md)
