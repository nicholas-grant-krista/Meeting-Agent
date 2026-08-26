---
audience: IT admin / Workspace Admin / champion
product-version: "2.1"
sources:
  - conversation-agent:docs/workspace-platform-routing.md
  - conversation-agent:docs/workspace-bot-identity.md
  - conversation-agent:docs/user-management.md
  - conversation-agent:docs/meeting-bot-end-state-policy.md
  - meeting-bot:docs/transcription.md
last-verified: 2026-08-24
---

# Best practices

What separates a deployment people rely on from one that quietly gets ignored.

## Rollout

**Start with internal meetings.** Internal capture has no lobby to clear, no
external participants to notify, and no consent conversation with third parties.
Get summary quality right where the stakes are low, then extend outward.

**Pick one team, not one person.** Meeting Agent's value is in shared follow-up.
A single user with summaries nobody else sees proves nothing. A team whose action
items land in a shared place proves everything.

**Review output with people who were in the room.** The only meaningful quality
check is whether an attendee agrees the summary is right. Do this in week one,
before habits form around ignoring it.

**Expand deliberately, not by default.** Adding external capture is a policy
decision, not a settings change. Treat it as its own mini-project with its own
consent review.

## Routing

**Set both buckets explicitly.** Inheriting the deployment default works, but
nobody remembers what it was six months later. Explicit configuration is
self-documenting.

**Audit for duplicate bots before go-live.** If your organization runs more than
one Meeting Agent workspace on the same internal domain, every one of them picks
up the same internal meetings. All routed to `Krista Bot` means one bot per
workspace in the same lobby. Decide which single workspace captures internal
meetings and set the rest to `Microsoft Teams` or `None`.

**Use `None` rather than turning things off elsewhere.** It is the supported
opt-out: no bot, and the post-meeting stages are cleanly skipped rather than
appearing as failures.

**Routing changes land fast — use that.** Capture is arranged on the day a
meeting runs, so a change you save this morning governs this afternoon. You do
not need to wait out a backlog of already-committed recurring instances.

**Raise your peak capture volume during onboarding.** Meeting Agent does not cap
simultaneous captures, so nothing in the product will warn you before your busiest
slot becomes an environment-capacity problem. If your organization has a
company-wide meeting hour where dozens of meetings start together, tell your TAM
the number before your first one.

## Bot identity

**Rename the bot for external meetings.** The default tells your guests which
workspace joined, which is useful internally and meaningless to a customer. Give
it a name that explains itself: `Acme Meeting Notes`, not `Krista (ACME-PROD-2)`.

**Set an avatar.** A blank avatar means the bot joins with its camera off — a
silent black tile. A small logo makes it obviously a tool rather than an
unexplained participant.

**Do not rename frequently.** Only newly scheduled bots pick up the change, so
during a rename different meetings show different names for a while.

## Licensing

**Audit seats quarterly.** People who only consume summaries should be
**Observers** — free, and their calendars are not synced.

**Remember Observers don't pull meetings in.** If a whole team is Observers, none
of their meetings are captured. This is correct behaviour that looks exactly like
a bug, so document it in your internal FAQ.

**Give your Krista TAM a Delegate Admin account.** They can help without
consuming a paid seat.

**Diarize your trial expiry.** It is a hard cutoff for both users and
integrations. Set a reminder a month out.

## Transcript quality

**Encourage captions.** Platform-native captions are the preferred path — faster
and cleaner than the fallback.

**On Zoom you host, enable full transcript viewing.** It moves capture onto the
higher-fidelity path with stable speaker attribution and timestamps.

**Set granularity expectations across platforms.** Teams gives per-utterance
segments; Meet and Zoom group each speaker's turn into one block. Users comparing
platforms will notice and assume something is broken. It is not.

## Governance

**Write down your consent posture before go-live.** Who is told, when, and how.
Decide it once, in writing, rather than per-meeting under pressure.

**Name the meetings that must never be captured.** HR, legal, medical,
privileged. Keep them off the connected calendar or in a bucket routed to `None`.

**Teach "remove the bot" as the escalation.** When a meeting turns sensitive
unexpectedly, removing Meeting Agent discards the partial recording. Everyone
should know this is available and what it does.

**Own the "why wasn't this recorded?" question internally.** Nearly always the
answer is one of: nobody admitted the bot, no licensed user was on the invite,
the meeting was not on a connected calendar, or the platform is not supported.
Your admins should be able to answer without opening a ticket — see
[troubleshooting](../05-troubleshooting.md).

## Anti-patterns

| Don't | Because |
|---|---|
| Turn on external capture the same week you go live | You will be debugging consent and admission at the same time as summary quality |
| Leave every workspace routed to `Krista Bot` on a shared domain | Multiple bots pile into the same lobby and none get admitted |
| License everyone by default | Observers are free, and seats are your cost |
| Treat "skipped" as a failure | It usually means the system correctly decided there was nothing to process |
| Judge summary quality from meetings you did not attend | You cannot evaluate accuracy without ground truth |

---

**Next:** [Admin day 2](admin-day-2.md) · [FAQ](../04-faq.md)
