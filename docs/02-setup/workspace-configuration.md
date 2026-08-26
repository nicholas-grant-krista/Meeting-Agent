---
audience: IT admin / Workspace Admin
product-version: "2.1"
sources:
  - conversation-agent:docs/workspace-platform-routing.md
  - conversation-agent:docs/workspace-bot-identity.md
  - conversation-agent:docs/workspace-aiqa-config.md
last-verified: 2026-08-24
---

# Workspace configuration

Everything here lives under **Settings → Meeting Bots & Assistants**, and every
change requires the **Meeting Agent Admin** (Workspace Admin) role. Non-admins
see the same cards read-only.

Changes take effect on the **next scheduling cycle**. No restart, no support
ticket, no waiting period.

## Meeting platform routing

The most consequential setting in the product. Two dropdowns, one per bucket.

### The buckets

- **Internal** — a Microsoft Teams meeting whose organizer is on one of your
  internal domains.
- **External** — everything else: Google Meet, Zoom, or a Teams meeting organized
  outside your organization.

Bucket membership is determined by the product and is not configurable. What you
configure is **what happens to each bucket**.

### Allowed values

| Bucket | You can choose | You cannot choose |
|---|---|---|
| **Internal** | `Microsoft Teams`, `Krista Bot`, `None` | — |
| **External** | `Krista Bot`, `None` | `Microsoft Teams` |

External cannot be Microsoft Teams because the native Teams route requires an
internal organizer, which an external meeting never has. The interface rejects
the combination rather than silently ignoring it.

### `None` — the opt-out

Setting a bucket to `None` means this workspace does not capture that class of
meeting at all. No bot is scheduled, no transcript exists, and the post-meeting
stages are marked skipped rather than failed.

Use it when:

- A workspace should not capture customer-facing meetings → external = `None`.
- Several workspaces share an internal domain and only one of them needs to
  capture internal meetings → the others set internal = `None`.

That second case is the important one. **Every workspace that picks up a meeting
sends its own bot.** A single internal meeting shared across fifteen workspaces
routed to `Krista Bot` produces fifteen bots in one lobby. `None` is the lever
that prevents it.

### Common configurations

| Your situation | Internal | External |
|---|---|---|
| Microsoft shop, capture everything | `Microsoft Teams` | `Krista Bot` |
| Capture internal meetings only | `Microsoft Teams` | `None` |
| Capture customer calls only | `None` | `Krista Bot` |
| Google or Zoom shop | `None` | `Krista Bot` |
| Paused / evaluating | `None` | `None` |

### What changing routing does and does not affect

- **Future meetings** — re-routed on the next scheduling cycle, which runs about
  once a minute. An override becomes authoritative the moment you save it.
- **Recurring series** — every future instance follows the new routing, including
  instances that already appeared in your calendar weeks ago. Capture is arranged
  on the day each meeting runs, so there is no backlog of already-committed
  instances to wait out.
- **Meetings already completed or in progress** — never re-routed. History is
  frozen and always reflects what actually happened.

In practice this means you can change routing in the morning and it governs that
afternoon's meetings.

### Reading the dropdowns

The option matching your deployment's default is labelled `… (Default)`. If a
bucket shows that option selected, you are inheriting rather than overriding.
Re-selecting the `(Default)` option clears your override. **Reset to default**
clears both buckets.

## Krista Bot identity

Under the **Krista Bot Identity** card.

| Field | Behaviour |
|---|---|
| **Bot display name** | Free text, up to 255 characters. Blank → `Krista (<Your Workspace Name>)`. |
| **Bot avatar image URL** | A public `http(s)` URL pointing directly at an image, up to 1000 characters. Blank → Krista joins with her camera off. A live preview shows whether the URL resolves. |

The two fields are independent — override the name and inherit the avatar, or
the reverse.

**An explicit name is used verbatim.** Set `Acme Notetaker` and attendees see
exactly `Acme Notetaker`, with no workspace name appended. The
`Krista (<Workspace>)` form only applies when you have *not* set a name, and
exists so attendees can tell which team's bot joined.

**Renaming only affects bots scheduled after the change.** A bot already in a
call is never relabelled.

Choose a name a meeting guest will recognize. `Krista (Acme)` tells an external
participant nothing if your company is not called Acme; something like
`Acme Meeting Notes` explains itself.

## A workspace with no active extension captures nothing

If a workspace's Meeting Agent extension is deregistered, that workspace stops
scheduling bots — even for meetings it is still nominally a member of. This is
deliberate, and it is worth knowing because the symptom ("we suddenly stopped
getting recordings") looks like a bug.

Deregistering an extension does **not** cancel your license. Ending a Meeting
Agent relationship is two separate acts: deregister the extension, and deactivate
the license.

## Other workspace settings

The AI configuration behind summaries and action items is **managed centrally by
Krista**. You don't need to supply or maintain your own model credentials, and
there's nothing to configure on your side. If you have a specific requirement
here, your Krista TAM is the person to raise it with.

---

**Next:** [Users and roles](users-and-roles.md) · [Verify your setup](verify-your-setup.md)
