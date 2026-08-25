---
audience: everyone — this is the page SEs paste into customer emails
product-version: "2.1"
sources:
  - conversation-agent:docs/workspace-platform-routing.md
  - conversation-agent:docs/meeting-bot-end-state-policy.md
  - meeting-bot:README.md
  - meeting-bot:docs/transcription.md
last-verified: 2026-08-24
---

# Capabilities matrix

The short answer to "does it do X?"

## Meeting platforms

| Platform | Supported | How |
|---|---|---|
| **Microsoft Teams** | ✅ Yes | Native Teams capture (your own meetings) or the Krista Bot (any meeting) |
| **Google Meet** | ✅ Yes | Krista Bot |
| **Zoom** | ✅ Yes | Krista Bot |
| **WebEx** | ❌ No | Meetings are skipped as an unsupported platform |
| **GoTo Meeting** | ❌ No | Meetings are skipped as an unsupported platform |
| Anything else | ❌ No | Skipped |

**Yes, it joins Zoom meetings.** This comes up constantly, so to be unambiguous:
Zoom is fully supported through the Krista Bot, including Zoom meetings hosted by
organizations other than yours. You do not need to install anything in Zoom, and
the meeting host does not need to be a Krista customer.

An unsupported platform is not an error — the meeting is simply marked skipped
and no one is paged about it.

## Capability by platform

| Capability | Teams (native) | Teams (bot) | Google Meet | Zoom |
|---|---|---|---|---|
| Record the meeting | ✅ | ✅ | ✅ | ✅ |
| Transcribe | ✅ | ✅ | ✅ | ✅ |
| Speaker attribution | ✅ | ✅ | ✅ | ✅ |
| Capture participants | ✅ | ✅ | ✅ | ✅ |
| Capture in-meeting chat | ✅ | ✅ | ✅ | ✅ |
| Join meetings hosted by other orgs | ❌ | ✅ | ✅ | ✅ |
| Visible as a participant | No | Yes | Yes | Yes |
| Subject to lobby / waiting room | No | Yes | Yes | Yes |
| Custom bot display name | n/a | ✅ | ✅ | ✅ |
| Custom bot avatar | n/a | ✅ | ✅ | ✅ |
| Transcript granularity | Per utterance | Per utterance | Per speaker turn | Per speaker turn |

## What Meeting Agent does

| | |
|---|---|
| Attend scheduled meetings automatically | ✅ |
| Record audio and video | ✅ |
| Produce a speaker-attributed transcript | ✅ |
| Fall back to its own transcription when platform captions fail | ✅ |
| Generate meeting summaries | ✅ |
| Extract action items | ✅ |
| Run configured follow-up actions after the meeting | ✅ |
| Route different meeting types differently (internal vs external) | ✅ |
| Let a workspace opt out of recording entirely | ✅ |
| Per-workspace bot name and avatar | ✅ |

## What Meeting Agent does not do

| | |
|---|---|
| Join ad-hoc meetings that are not on a connected calendar | ❌ |
| Participate in the conversation or answer questions live | ❌ |
| Join a meeting nobody admits from the lobby | ❌ — by design |
| Record when a host has disabled recording by policy | ❌ |
| Support WebEx, GoTo, or other platforms | ❌ |
| Guarantee capture for regulatory / compliance retention | ❌ — not designed for this |
| Start Microsoft Teams' own transcription on your behalf | ❌ — deliberately, as it notifies all participants and writes a file to the organizer's OneDrive |
| Retrieve Google Workspace post-meeting transcripts from Drive | ❌ |

## Things worth knowing before you commit

**The bot is visible.** On Teams-via-bot, Meet, and Zoom, attendees see a
participant in the roster. If you need capture that no one can see, the only
route that provides it is native Teams on your own meetings.

**The bot must be admitted.** Waiting rooms and lobbies apply to it exactly as
they do to any guest. Meetings where nobody admits it are not recorded. This is
the single most common reason a customer says "it didn't work."

**One bot per workspace, per meeting.** If several workspaces in your
organization all capture the same meeting, each sends its own bot. For a
frequently shared internal meeting, set the internal bucket to **off** for the
workspaces that do not need it. See
[workspace configuration](../02-setup/workspace-configuration.md).

**Captions quality drives transcript quality.** Meeting Agent prefers the
platform's own captions. Meetings where captions cannot be enabled still work,
but take a slower and more expensive path.

> **OPEN —** Are there platform-specific limits on meeting length or concurrent
> bots that a customer should plan around? · _ask: Meeting Agent product owner_

---

**Next:** [Prerequisites](../02-setup/prerequisites.md)
