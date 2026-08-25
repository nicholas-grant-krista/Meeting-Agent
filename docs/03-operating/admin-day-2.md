---
audience: Workspace Admin / day-2 operator
product-version: "2.1"
sources:
  - conversation-agent:docs/meeting-bot-end-state-policy.md
  - conversation-agent:docs/workspace-platform-routing.md
  - conversation-agent:docs/user-management.md
  - conversation-agent:docs/license-tiers-and-session-auth.md
last-verified: 2026-08-24
---

# Admin day 2

Running Meeting Agent after go-live.

## The weekly check

Five minutes, once a week. You are looking for patterns, not individual
meetings.

1. **Any meetings marked failed?** Failed means a technical fault, and it is
   replayable. A steady trickle is worth raising with Krista; a spike is worth
   raising immediately.
2. **Any recurring meeting skipped every time?** Almost always non-admission on a
   series where nobody admits the bot. Fix the habit or change the routing —
   the system will not fix itself.
3. **Any unexpected skips?** A meeting you thought was in scope but was not
   captured usually means no licensed user was on the invite, or the platform is
   unsupported.
4. **Seat count still right?** People who only read summaries should be
   Observers.

## Reading meeting outcomes

Meeting Agent separates *"correctly nothing to do"* from *"something broke."*
This distinction is the core of day-2 triage.

| Outcome | Meaning | Your action |
|---|---|---|
| **Completed** | Processed normally | None |
| **Completed, with a notice** | Processed, but the transcript may be incomplete — the bot was interrupted mid-call | Spot-check the transcript if the meeting mattered |
| **Skipped** | There was correctly nothing to process | Check the reason. Usually yours to fix, not Krista's. |
| **Failed** | A technical fault | Replayable. Raise with Krista if it repeats. |

### Skip reasons and who owns them

| Reason | Owner | Fix |
|---|---|---|
| Bot was never admitted | You | Admit the bot, or change routing |
| Bot was removed by a participant | You | Expected if intentional |
| Meeting Agent was turned off for this meeting | You | Expected |
| Not scheduled to join | You | Check calendar connection and licensed attendees |
| Unsupported platform | Neither | WebEx, GoTo, etc. Nothing to fix. |

## Routine changes

**Changing routing** — Settings → Meeting Bots & Assistants → Meeting Platform
Routing. Takes effect on the next scheduling cycle. Completed and in-progress
meetings are never re-routed.

**Renaming the bot** — same screen, Krista Bot Identity card. Only affects bots
scheduled after the change.

**Adding a user** — decide licensed vs Observer first. Licensed means their
calendar is synced and their meetings are captured, and it consumes a seat.

**Removing a user** — historical meetings, transcripts, and action items keep
their references and continue to read correctly.

## Pausing capture

Set both buckets to `None`. Meetings still appear and are marked skipped; nothing
is recorded. Reverse it by restoring the routing — no support ticket either way.

This is the right lever for a company-wide sensitive period, a compliance review,
or a pause during an incident.

## When to call Krista

Handle yourself:

- Non-admission, on any platform
- Routing and bot-identity changes
- Seat and role changes
- Meetings skipped for unsupported platforms
- "Why wasn't this recorded?" — work the
  [troubleshooting](../05-troubleshooting.md) list first

Raise with Krista:

- Repeated **failed** meetings
- Transcripts that are wrong rather than merely coarse — wrong speakers, missing
  large sections of a meeting the bot definitely attended
- Summary or action-item quality that does not improve after the meetings
  themselves improved
- Anything involving your license: expiry, tier change, suspension
- A meeting captured that should not have been

When you raise something, include the meeting, its date and platform, its status
and reason, and what you expected instead. The status and reason narrow it
faster than anything else.

## Before your trial expires

A trial license stops working on its expiry date — for users **and** for
integrations, at once, with no grace period.

Two weeks before:

- [ ] Confirm the expiry date
- [ ] Decide whether you are converting
- [ ] If converting, start with your Krista TAM now
- [ ] If not, export anything you need to keep

> **OPEN —** What is the self-service path for exporting transcripts, summaries,
> and action items before a trial ends? · _ask: Meeting Agent product owner_

---

**Next:** [Troubleshooting](../05-troubleshooting.md)
