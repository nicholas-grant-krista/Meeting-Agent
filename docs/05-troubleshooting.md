---
audience: Workspace Admin / support desk
product-version: "2.1"
sources:
  - conversation-agent:docs/meeting-bot-end-state-policy.md
  - conversation-agent:docs/workspace-platform-routing.md
  - conversation-agent:docs/user-management.md
  - conversation-agent:docs/license-tiers-and-session-auth.md
last-verified: 2026-08-24
---

# Troubleshooting

## Start here

**Find the meeting and read its status.** Meeting Agent deliberately distinguishes
*"there was correctly nothing to process"* from *"something broke,"* and that
tells you immediately whether the problem is yours or Krista's.

If the user is newly onboarded and *nothing* is working, start with
[Section E](#section-e--access-problems) instead — first-sign-in problems look
like capture problems but aren't.

```
Meeting missing or wrong?
        │
        ├── Is the meeting in Meeting Agent at all?
        │      NO ──► Section A: the meeting never arrived
        │      YES
        │       │
        │       ├── Status: Skipped ──► Section B: read the skip reason
        │       ├── Status: Failed  ──► Section C: technical fault
        │       └── Status: Completed but wrong ──► Section D: content quality
```

---

## Section A — The meeting never appeared

Meeting Agent never saw it. Work these in order.

| Check | Why | Fix |
|---|---|---|
| Was anyone on the invite a **licensed** user? | Only licensed users' calendars are synced. Observers don't pull meetings in. | License a participant, or accept it is out of scope |
| Is the calendar connected? | No calendar, no meetings | Reconnect; escalate if it will not |
| Was the meeting on the calendar at all? | Ad-hoc meetings are invisible | Schedule it |
| Is the workspace's extension still registered? | A deregistered workspace schedules nothing | Re-register with your TAM |

**The most common cause by far is the first one.** A team that was set up as
Observers to save on seats has no meetings captured, and it looks exactly like a
broken integration.

---

## Section B — Skipped

Skipped is usually correct behaviour. Read the reason.

### "Never admitted"

Krista reached the meeting and waited **about 5 minutes**, but nobody let her in.

That window is the thing to check first. Krista arrives just before the
scheduled start, so a meeting that habitually begins ten minutes late will lose
Krista before anyone thinks to admit her — the host isn't refusing, they're just
late.

- **One-off:** expected. Nothing to fix.
- **Recurring, every time:** either the host habitually doesn't admit guests, or
  the meeting reliably starts more than five minutes late. Both are habit fixes,
  and neither self-corrects.
- **Every external meeting:** your users don't know they need to admit it. Send
  out [meeting hygiene](03-operating/meeting-hygiene.md).

This is the #1 real-world cause of "it didn't work."

### "Removed by a participant"

Someone kicked Krista out. The partial recording was discarded by design.

If intentional, nothing to fix. If not, the person who removed it probably didn't
know what it was — which is a naming and communication problem. Give Krista a
self-explanatory name.

### Content is missing, and nobody removed Krista

Check whether a participant used the in-meeting chat controls. Anyone can type
`@<bot> pause`, `@<bot> opt out`, or `@<bot> remove last X minutes`, and each does
exactly what it says. A meeting with an unexplained gap in the middle is often a
`pause` that was never resumed.

This is working as intended — but it does mean "missing content" is not always a
fault. Ask the attendees before escalating.

### "Turned off for this meeting" / "Not scheduled to join"

Capture was off for that meeting. Check your bucket routing — a bucket set to
`None` produces exactly this.

### "Couldn't be matched to a supported meeting platform"

The link was WebEx, GoTo, or something else unsupported. Nothing to fix; nothing
is broken.

---

## Section C — Failed

A technical fault. These are replayable and Krista should see them.

| What it means | What to do |
|---|---|
| Krista could not navigate the meeting platform's interface — a sign-in page, a consent screen, or a platform UI change | Raise with Krista Support. If it affects one platform across many meetings, say so — that pattern matters. |
| Krista hit a fault before reaching the call | Raise with Krista Support, with date and platform |
| Krista was lost mid-call | Raise with Krista Support — content may be recoverable |
| An unrecognized state | Always raise. This is a defect. |

**One failure on one meeting** — note it and watch. **Repeated failures, or a
cluster on one platform** — raise immediately; meeting platforms change their
interfaces and that is exactly what it looks like from your side.

Include: the meeting, date, platform, status and reason, and what you expected.

---

## Section D — Recorded, but the content is wrong

### The transcript is coarse — long blocks instead of separate lines

Not a fault. Google Meet and Zoom group an uninterrupted speaker's sentences into
one block; Teams splits per utterance. Attribution and content are complete.

### Speakers are wrong or missing

- **On Zoom, occasionally, on very short utterances** — a known limitation when
  the meeting falls back to the rolling caption banner. Enabling full transcript
  viewing on your Zoom account moves capture to the higher-fidelity path.
- **Systematically wrong across a whole meeting** — not expected. Raise it.

### Large sections of the meeting are missing

Check whether the meeting was flagged as possibly incomplete — that indicates the
bot was interrupted mid-call, and the gap is explained. If there is no such flag
and content is genuinely missing, raise it.

### The summary is unhelpful

Usually the meeting, not the model. Summaries reflect what was said explicitly.

- Were decisions stated out loud, or only implied?
- Were action items named with an owner?
- Was it a rambling discussion without conclusions?

Try the hygiene practices for a week. If quality does not improve on meetings
that *did* state decisions clearly, raise it with your TAM.

---

## Section E — Access problems

### Registration and first sign-in

Most of what a new user hits is in this table, and almost all of it is
self-service.

| Symptom | Cause | Fix |
|---|---|---|
| "Authentication Failed" during setup | Known browser timing quirk, not a real failure | Click **Refresh Events** on the dashboard |
| Meetings don't appear after connecting the calendar | The agent tab was refreshed rather than closed and reopened | Close the tab fully, reopen from the agent list, click **Home**, then **Refresh Events** |
| Meetings still missing after a reopen | Calendar sync takes a few minutes | Wait, then **Refresh Events**. Still nothing → **Conversation Agent → Initiate → Connect My Calendar** and re-authenticate |
| "Email address does not belong to the registered domains list" | The Krista account was created with an address outside your domains | Correct the account's email — an admin task |
| Sign-in error at the very first step | The user's Microsoft account may be blocked | Unblock in your identity system |
| 403, missing agent, permission message | Account or entitlement issue | Admin task; not fixable by the user |
| Never received a welcome email | Account not provisioned, or mail delivery | Resend from user management |
| Can't find "Meeting Agent" in the agent list | It may be labelled **New Conversation Agent** | Point the user at the right agent |

A cluster of these arriving at once usually means the rollout email went out
before accounts were fully provisioned. Sending
[setting yourself up](02-setup/first-time-registration.md) alongside the welcome
email heads off most of them.

### Access and licensing

| Symptom | Likely cause | Fix |
|---|---|---|
| Users suddenly cannot sign in | License expired or was deactivated | Check expiry; contact Krista Support |
| Integrations stopped authenticating at the same moment | Same — a license cut blocks both channels at once | Contact Krista |
| One user cannot see settings | Not a Meeting Agent Admin | Grant the role if appropriate |
| A user can sign in but their meetings aren't captured | They are an Observer, not licensed | Convert to a licensed seat |

A trial expiry cuts users and integrations simultaneously with no grace period.
If everything stopped at once and nothing changed, check the date first.

---

## Escalating to Krista

Include:

1. Meeting name, date, and time
2. Platform — Teams, Meet, or Zoom
3. Whether the organizer was internal or external
4. The meeting's status and reason as shown
5. What you expected instead
6. Whether it is one meeting or a pattern — and if a pattern, its shape

Items 4 and 6 narrow the problem faster than anything else.
