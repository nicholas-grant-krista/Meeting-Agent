---
audience: IT admin / Workspace Admin
product-version: "2.1"
sources:
  - conversation-agent:docs/user-management.md
  - conversation-agent:docs/workspace-membership-model.md
  - conversation-agent:docs/license-tiers-and-session-auth.md
last-verified: 2026-08-24
---

# Users and roles

## The four user types

Two independent attributes produce four types. Understanding the grid prevents
both over-licensing and the "why isn't my meeting showing up?" question.

| | **Licensed seat** | **No seat** |
|---|---|---|
| **Regular role** | **Regular User** — full member. Calendar is synced. Their meetings are captured. Consumes a paid seat. | **Observer** — can view Meeting Agent content shared with them. Calendar is **not** synced. Consumes no seat. |
| **Admin role** | **Krista Admin** — everything a Regular User has, plus User Management and the Ops Console. Consumes a paid seat. | **Delegate Admin** — administrative authority without a seat. Typically a Krista employee assisting you. Calendar is **not** synced. |

### The consequence that surprises people

**Only licensed users' calendars are synced.** An Observer's presence on a
meeting invitation does **not**, by itself, pull that meeting into your
workspace.

So if a meeting is not being captured, the first question is not "is Meeting Agent
broken?" — it is **"is anyone on that invitation a licensed user?"** A meeting
attended entirely by Observers is invisible to Meeting Agent by design.

### Choosing the right type

- **Regular User** — anyone whose meetings should be captured. This is your
  seat count.
- **Observer** — people who need to read summaries and action items but whose own
  meetings do not need capturing. Executives who consume output, or stakeholders
  in adjacent teams. Free.
- **Krista Admin** — your Meeting Agent administrators. Keep this small.
- **Delegate Admin** — for your Krista TAM or support contact, so they can help
  without consuming one of your paid seats.

## The Meeting Agent Admin role

Separate from the seat model. **Meeting Agent Admin** (also called Workspace
Admin) is what gates the settings in
[workspace configuration](workspace-configuration.md) — platform routing and bot
identity.

Non-admins see those cards read-only, with the controls disabled and an
explanatory tooltip. This is intentional: routing changes affect everyone in the
workspace, including whether customer-facing meetings are recorded at all.

Grant it to people who understand the consent implications of turning external
capture on.

## Licensing

Your workspace is bound to a license that determines your tier.

| Tier | Meaning |
|---|---|
| **Production** | A paying customer. No expiry unless your contract sets one. |
| **Trial** | Try-before-you-buy. Same capability as production, with a **hard expiry date**. |

**A trial expiry is a cliff, not a slope.** When the date passes, users are
blocked in the interface and integrations stop authenticating. There is no grace
period and no read-only mode. Record your expiry date during onboarding and start
the conversion conversation well before it.

Deactivating a license immediately blocks the workspace — both people and
integrations. It is the intended kill switch if you need one.

## Adding and removing users

User Management is available to Krista Admins.

Removing a user's access does not delete the meetings, transcripts, or action
items they were associated with. Historical records keep their references so
past meetings continue to read correctly.

**Bulk provisioning is handled for you.** You don't need to add people one at a
time. Send your Krista TAM a master list from your IT team — the people who need
access, and who among them should be administrators — and they'll load it.

The list is worth getting right before you send it, since it's also the moment to
decide who needs a licensed seat and who is better as an Observer. See the four
user types above.

> **OPEN —** What is the exact self-service path to change a user between
> licensed and Observer, and does it take effect immediately for calendar sync?
> · _ask: Meeting Agent product owner_

---

**Next:** [Verify your setup](verify-your-setup.md)
