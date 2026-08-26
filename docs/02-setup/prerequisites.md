---
audience: IT admin
product-version: "2.1"
sources:
  - conversation-agent:docs/license-tiers-and-session-auth.md
  - conversation-agent:docs/workspace-membership-model.md
  - conversation-agent:docs/user-management.md
  - conversation-agent:docs/workspace-platform-routing.md
last-verified: 2026-08-24
---

# Prerequisites

What must be true before setup begins. Work through this with your Krista TAM —
several items are provisioned by Krista, not by you.

## Provided by Krista

| Item | Notes |
|---|---|
| A **Meeting Agent workspace** | Your tenant. Created by Krista during onboarding. |
| A **license** bound to that workspace | Determines your tier (trial or production) and, for a trial, the expiry date. |
| The **Meeting Agent URL** | Where your team signs in. |

A trial license carries a hard expiry. When it passes, both your users and your
integrations stop working — not gradually, immediately. Know your date and start
the conversion conversation before it.

## Provided by you

### Calendar connection

Meeting Agent works from your calendar. Nothing is captured until a calendar is
connected, because unscheduled meetings are invisible to it.

> **OPEN —** Which calendar providers are supported for connection (Microsoft 365
> only, or Google Workspace as well), and what admin consent is required for
> each? · _ask: Meeting Agent product owner_

### Your internal domains

The list of email domains belonging to your organization — `acme.com`,
`acme.co.uk`, and so on.

This drives the internal/external split. A Teams meeting organized by someone on
one of these domains is **internal**; everything else is **external**, and the
two are routed and configured independently. Getting this list wrong is the most
common cause of meetings being captured the wrong way, so include every domain
your people actually send mail from — acquisitions and regional domains
included.

### Decisions to make before you configure anything

Have answers ready. Each maps directly to a setting.

1. **Which meetings do you want captured?** Internal only, external only, or
   both? Either bucket can be off.
2. **Is a visible bot acceptable in customer-facing meetings?** If not, external
   capture is not for you — Krista is always visible on Meet, Zoom, and
   Teams-as-guest.
3. **What should Krista be called?** It defaults to `Krista (<Your Workspace
   Name>)`. Many customers rename it to something their meeting guests will
   recognize.
4. **Who are your Workspace Admins?** They can change routing, bot identity, and
   settings for everyone in the workspace.
5. **What is your consent posture?** See below — decide this before your first
   external meeting, not after.

### Consent and notification

Krista appears in the participant roster, and meeting platforms notify
participants when recording starts. That is your notification mechanism, and for
many organizations it is not sufficient on its own.

Decide, in writing, before you go live:

- Do you announce Meeting Agent to external participants in advance?
- Is there meeting content — HR, legal, medical, privileged — that must never be
  captured? Those meetings need to be kept off the connected calendar or run
  outside the captured buckets.
- Which jurisdictions do your participants join from? Some require all-party
  consent to record.

Krista cannot make these determinations for you. Route them through your legal
and compliance function during onboarding rather than after an incident.

## Technical prerequisites

| Requirement | Detail |
|---|---|
| Supported meeting platforms | Microsoft Teams, Google Meet, Zoom. See [capabilities matrix](../01-overview/capabilities-matrix.md). |
| Browser access for your users | Meeting Agent's interface is web-based. |
| Bot avatar image (optional) | A publicly reachable `http(s)` URL pointing directly at an image. If not set, Krista joins with her camera off. |

> **OPEN —** Are there network requirements on the customer side — allowlisted
> domains, IP ranges, or firewall rules — for either the interface or Krista?
> · _ask: Meeting Agent product owner_

## Readiness checklist

- [ ] Workspace created and reachable
- [ ] License issued; if trial, expiry date recorded and diarized
- [ ] Calendar connected
- [ ] Internal domains listed and confirmed complete
- [ ] Internal / external capture decisions made
- [ ] Bot display name agreed
- [ ] Workspace Admins identified
- [ ] Consent posture agreed with legal / compliance
- [ ] Exclusions identified — meetings that must never be captured

---

**Next:** [Microsoft Teams](platform-teams.md) · [Google Meet](platform-google-meet.md) · [Zoom](platform-zoom.md)
