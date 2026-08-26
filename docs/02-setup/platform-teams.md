---
audience: IT admin
product-version: "2.1"
sources:
  - conversation-agent:docs/workspace-platform-routing.md
  - conversation-agent:docs/workspace-bot-identity.md
  - meeting-bot:docs/transcription.md
last-verified: 2026-08-24
---

# Setup — Microsoft Teams

Teams is the one platform with two capture routes. Choose deliberately.

## The two routes

| | **Native Teams** | **Krista Bot** |
|---|---|---|
| Which meetings | Teams meetings organized by **your** domains | Any Teams meeting, including other organizations' |
| Visible participant | No | Yes |
| Lobby / admission | Not applicable | Must be admitted like any guest |
| Configured as | Internal bucket → `Microsoft Teams` | Either bucket → `Krista Bot` |

Native Teams capture is only available on the **internal** bucket. This is not a
configuration limitation you can work around — the route depends on the organizer
being on one of your domains, which by definition an external meeting's organizer
is not. The external bucket will reject an attempt to set it to Microsoft Teams.

## Recommended configuration

For most customers:

- **Internal → `Microsoft Teams`.** Your own meetings are captured without an
  extra participant in the roster and without anyone needing to admit anything.
- **External → `Krista Bot`**, or **off** if you have decided not to capture
  customer-facing meetings.

Set these on the workspace — see
[workspace configuration](workspace-configuration.md).

## If you use the Krista Bot on Teams

Krista joins as an anonymous guest. Two consequences your users should expect:

**It appears in the roster tagged "Unverified."** This is Teams' standard label
for a guest who joined without signing in. It is not a warning about Krista.
Tell your users this in advance so it does not generate help-desk tickets.

**It must be admitted from the lobby.** If your meeting policy puts guests in the
lobby, someone has to let Krista in, every time. If nobody does, the meeting is
not recorded and is marked skipped.

> If you want Krista admitted automatically, that is a Teams meeting-policy
> decision on your side about how guests are handled. Weigh it against the
> security posture you want for actual guests, since the setting is not specific
> to Krista.

## Transcription on Teams

Meeting Agent turns on **live captions** and captures them. Any participant can
turn captions on, so Krista does not need elevated rights.

Teams also has a separate **transcription** feature (More → Record and transcribe
→ Start transcription). **Meeting Agent deliberately does not start it**, for two
reasons worth explaining to stakeholders:

1. It notifies every participant with a "this meeting is being transcribed"
   banner they must acknowledge.
2. It writes a transcript file into the organizer's OneDrive / Teams Files —
   creating a second copy of the content in a location Meeting Agent does not
   manage.

Starting Teams transcription is your organization's decision to make
meeting-by-meeting, not something a bot should do on your behalf. If you do start
it, Meeting Agent still captures via captions as normal.

Teams produces the finest-grained transcripts of the three platforms — one
segment per utterance.

## Bot identity

Krista's display name defaults to `Krista (<Your Workspace Name>)` so attendees
can tell which team's bot joined. Override it per workspace under
Settings → **Meeting Bots & Assistants** → **Krista Bot Identity**. An explicit
override is used verbatim with no workspace suffix.

An avatar image URL can be set as Krista's camera tile. Leave it blank and the
bot joins with its camera off.

## Watch out for: multiple bots in one meeting

If several Meeting Agent workspaces in your organization share the same internal
domain, an internal meeting is picked up by **each** of them — and if they all
route internal to `Krista Bot`, each sends its own bot to the same lobby.

The fix is routing, not a support ticket: set the internal bucket to
`Microsoft Teams` or **off** for every workspace that does not need to capture
that meeting. See [workspace configuration](workspace-configuration.md).

> **OPEN —** What Microsoft 365 admin consent or app registration does the native
> Teams route require, and who performs it? · _ask: Meeting Agent product owner_

---

**Next:** [Workspace configuration](workspace-configuration.md)
