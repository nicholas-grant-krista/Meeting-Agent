---
audience: IT admin
product-version: "2.1"
sources:
  - conversation-agent:docs/workspace-bot-identity.md
  - conversation-agent:docs/workspace-platform-routing.md
  - conversation-agent:docs/meeting-bot-end-state-policy.md
last-verified: 2026-08-24
---

# Limits and quotas

> Several figures on this page are unconfirmed and marked OPEN. Do not quote an
> OPEN item to a customer — get the answer first. See
> [README](../../README.md#open-markers).

## Confirmed limits

| Limit | Value |
|---|---|
| Bot display name | 255 characters |
| Bot avatar image URL | 1000 characters; must be `http` or `https` and point directly at an image |
| Supported meeting platforms | Microsoft Teams, Google Meet, Zoom |
| Bots per meeting, per workspace | One |
| Routing granularity | Per workspace, per bucket — not per meeting or per series |

## Behavioural caps

Meeting Agent ends a bot's attendance on any of these, all of which produce a
normally-processed meeting:

- The host ends the meeting
- Everyone else leaves
- Nobody joins at all
- A **silence timeout** is reached — sustained dead air
- A **maximum duration** cap is reached

> **OPEN —** What are the actual values of the silence timeout and the maximum
> duration cap? These are the two most likely to affect a customer with long
> workshops or all-day sessions. · _ask: Meeting Agent product owner_

> **OPEN —** How long does the bot wait in a lobby before giving up as "never
> admitted"? · _ask: Meeting Agent product owner_

## Not established

Everything in this section needs an answer before this page is customer-ready.

> **OPEN —** Is there a limit on concurrent bots per workspace, or per
> deployment? What happens when a customer has more simultaneous meetings than
> that limit? · _ask: Meeting Agent product owner_

> **OPEN —** How far in advance are recurring series seeded? The engineering
> material indicates roughly a month for a daily series, but the customer-facing
> guarantee is not established. · _ask: Meeting Agent product owner_

> **OPEN —** Is there a maximum meeting length beyond the duration cap — a point
> at which recording or transcription degrades? · _ask: Meeting Agent product
> owner_

> **OPEN —** Are there per-tier quotas? Does a trial license cap meetings,
> minutes, or seats compared with production? · _ask: Meeting Agent product
> owner_

> **OPEN —** What is the retention period for recordings and transcripts, and is
> it configurable per customer? · _ask: Meeting Agent product owner_

> **OPEN —** How long after a meeting ends should a customer expect the
> transcript, summary, and action items to be available? A stated target is worth
> having — it is the second question every customer asks. · _ask: Meeting Agent
> product owner_

## Platform limits outside Krista's control

These come from the meeting platforms, not from Meeting Agent:

- **Lobby and waiting-room policies** — set by the meeting host or their
  organization. If the bot is not admitted, it cannot record.
- **Host recording restrictions** — a host who has disabled recording by policy
  prevents capture.
- **Caption availability** — where a platform or host prevents captions, Meeting
  Agent falls back to transcribing recorded audio.
- **Zoom full transcript viewing** — controlled by the host's Zoom account
  settings, which affects transcript fidelity on Zoom.
