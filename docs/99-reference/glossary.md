---
audience: everyone
product-version: "2.1"
sources:
  - conversation-agent:docs/workspace-platform-routing.md
  - conversation-agent:docs/workspace-bot-identity.md
  - conversation-agent:docs/user-management.md
  - conversation-agent:docs/meeting-bot-end-state-policy.md
  - conversation-agent:docs/license-tiers-and-session-auth.md
last-verified: 2026-08-24
---

# Glossary

**Action item** — a task extracted from a meeting, with an owner where one was
stated. Produced by the post-meeting workflow.

**Bucket** — one of the two classes every meeting falls into: **internal** or
**external**. Each is routed independently. Bucket membership is determined by
the product; what happens to each bucket is what you configure.

**Delegate Admin** — administrative authority over a workspace without consuming
a paid seat. Typically a Krista employee assisting a customer. Calendar not
synced.

**External (bucket)** — every meeting that is not internal: Google Meet, Zoom, or
a Teams meeting organized outside your domains. Can be routed to the Krista Bot
or off.

**Failed** — a meeting outcome meaning a technical fault occurred. Replayable,
and Krista's to investigate. Contrast with *skipped*.

**Internal (bucket)** — a Microsoft Teams meeting whose organizer is on one of
your configured internal domains. The only case where native Teams capture can be
used.

**Internal domains** — the email domains belonging to your organization. Drives
the internal/external split.

**Krista Admin** — a licensed user with administrative access including User
Management.

**Krista Bot** — the capture route where a bot joins the meeting as a visible
participant. Works on Teams, Google Meet, and Zoom, including meetings hosted by
other organizations.

**Licensed seat / licensed user** — a paid workspace member whose calendar is
synced and whose meetings are captured. Contrast with *Observer*.

**Meeting Agent Admin** — the role permitting changes to workspace settings:
platform routing and bot identity. Also called **Workspace Admin**.

**Native Teams** — the capture route that attaches through Microsoft Teams
directly, with no extra participant in the meeting. Available only for internal
Teams meetings.

**None** — a routing value meaning this workspace does not capture that bucket at
all. No bot is scheduled and post-meeting stages are cleanly skipped.

**Observer** — an unlicensed user who can view content shared with them. Consumes
no seat, calendar not synced, and their presence on an invitation does **not**
pull a meeting into the workspace.

**Platform captions** — the meeting platform's own live captions. Meeting Agent's
preferred transcription source.

**Post-meeting workflow** — the sequence that runs after capture: transcript,
knowledge ingest, summary, action items, and configured follow-up actions.

**Production (tier)** — a paying customer's license tier.

**Routing** — the decision assigning each meeting to a capture route, made per
bucket per workspace.

**Skipped** — a meeting outcome meaning there was correctly nothing to process:
nobody admitted the bot, capture was off, or the platform is unsupported.
Contrast with *failed*.

**Trial (tier)** — a time-limited license with a hard expiry date that cuts both
user and integration access when it passes.

**Unverified** — Microsoft Teams' standard label for a guest who joined without
signing in. Applied to the Krista Bot; not a warning.

**Workspace** — your Meeting Agent tenant. Settings, users, meetings, and
licensing are all scoped to it. One organization may run several.
