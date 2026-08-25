---
audience: IT admin
product-version: "2.1"
sources:
  - conversation-agent:docs/workspace-platform-routing.md
  - meeting-bot:docs/transcription.md
  - meeting-bot:README.md
last-verified: 2026-08-24
---

# Setup — Zoom

Zoom is captured by the **Krista Bot** only, and falls into the **external**
bucket (the internal bucket is defined as Teams meetings with an internal
organizer, so no Zoom meeting is ever internal).

**Zoom is fully supported, including meetings hosted by other organizations.**
Nothing is installed in Zoom, no Marketplace app is required, and the host does
not need to be a Krista customer.

## What to configure

Set the **external** bucket to `Krista Bot` in
[workspace configuration](workspace-configuration.md). That is the whole
Zoom-specific configuration on the Krista side.

## What your users will see

The bot joins as a participant. If the meeting has a waiting room, it waits there
until admitted. If nobody admits it, the meeting is not recorded and is marked
skipped.

## Transcription on Zoom — one setting worth knowing

Meeting Agent captures Zoom captions two ways, and which one it gets depends on
a setting on **the host's Zoom account**:

| Host account setting | What Meeting Agent uses | Result |
|---|---|---|
| Full transcript viewing **enabled** | Zoom's full transcript panel | Cleanest transcripts — stable speaker attribution and timestamps per utterance |
| Full transcript viewing **disabled**, or a free-tier meeting | Zoom's rolling caption banner | Works, but text is reconstructed as it scrolls; very short fragments at boundaries can occasionally attach to the wrong segment |

If you host your own Zoom meetings, enabling full transcript viewing on your Zoom
account measurably improves transcript quality. For meetings hosted by other
organizations you have no control over this, and the fallback handles it.

**Transcript granularity is per speaker turn**, like Google Meet — an
uninterrupted speaker produces one block rather than many.

## Known constraint

On the fallback (rolling banner) path, reconstruction requires a minimum overlap
to stitch text correctly. Very short utterances at a boundary — a one-word "yes"
between two long turns — can occasionally be attributed to the adjacent speaker.
This does not occur on the full-transcript-panel path, which is another reason to
enable that setting where you can.

## Bot identity

Same as everywhere: display name defaults to `Krista (<Your Workspace Name>)`,
overridable per workspace, with an optional avatar image URL. See
[workspace configuration](workspace-configuration.md).

> **OPEN —** Are there Zoom account types or meeting configurations (webinars,
> end-to-end encrypted meetings, meetings requiring registration or
> authentication) where the bot cannot join at all? · _ask: Meeting Agent product
> owner_

---

**Next:** [Workspace configuration](workspace-configuration.md)
