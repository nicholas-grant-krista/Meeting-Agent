# Meeting Agent Run Book

The customer-facing onboarding guide for **Krista Meeting Agent**. This is the
document set a Krista TAM or SE hands a new customer to take them from "what is
this?" to "it's live and my team knows how to use it."

**Covers product release train:** Meeting Agent `2.1` · Meeting Bot `1.0`
**Last full review:** 2026-08-24

---

## Who reads what

Do not hand a customer the whole repo. Hand them the track that matches their role.

| Reader | Their question | Start here |
|---|---|---|
| **Executive / champion** | "What is this and what will it do for us?" | [What is Meeting Agent](docs/01-overview/what-is-meeting-agent.md) → [How it works](docs/01-overview/how-it-works.md) |
| **IT / Workspace Admin** | "What do I have to configure?" | [Prerequisites](docs/02-setup/prerequisites.md) → the platform page for Teams / Meet / Zoom → [Workspace configuration](docs/02-setup/workspace-configuration.md) → [Verify your setup](docs/02-setup/verify-your-setup.md) |
| **New user being onboarded** | "How do I get started?" | [Setting yourself up](docs/02-setup/first-time-registration.md) → [Getting the best from Krista](docs/03-operating/meeting-hygiene.md) |
| **End user** | "Why didn't Krista join my meeting?" | [Questions people ask](docs/04-faq.md) → [Getting the best from Krista](docs/03-operating/meeting-hygiene.md) |
| **Security reviewer** | "Where does our data go?" | Not covered here by design — route to the customer's Krista TAM |
| **Day-2 operator** | "It's live — now what?" | [Admin day 2](docs/03-operating/admin-day-2.md) → [Troubleshooting](docs/05-troubleshooting.md) |

## Contents

**01 — Overview**
- [What is Meeting Agent](docs/01-overview/what-is-meeting-agent.md)
- [How it works](docs/01-overview/how-it-works.md)
- [Capabilities matrix](docs/01-overview/capabilities-matrix.md) — the "does it do X?" table

**02 — Setup**
- [Setting yourself up](docs/02-setup/first-time-registration.md) — the end-user walkthrough; pair this with your rollout email
- [Prerequisites](docs/02-setup/prerequisites.md)
- [Microsoft Teams](docs/02-setup/platform-teams.md)
- [Google Meet](docs/02-setup/platform-google-meet.md)
- [Zoom](docs/02-setup/platform-zoom.md)
- [Workspace configuration](docs/02-setup/workspace-configuration.md)
- [Users and roles](docs/02-setup/users-and-roles.md)
- [Verify your setup](docs/02-setup/verify-your-setup.md)

**03 — Operating**
- [Best practices](docs/03-operating/best-practices.md)
- [Meeting hygiene](docs/03-operating/meeting-hygiene.md) — the end-user one-pager
- [Admin day 2](docs/03-operating/admin-day-2.md)

**04 / 05**
- [FAQ](docs/04-faq.md)
- [Troubleshooting](docs/05-troubleshooting.md)

**99 — Reference**
- [Glossary](docs/99-reference/glossary.md)
- [Limits and quotas](docs/99-reference/limits-and-quotas.md)

> **Data handling is intentionally out of scope for this guide.** Storage,
> retention, sub-processors, and certification questions are answered per
> customer by their Krista TAM, since the answers depend on how their workspace
> is provisioned. Route security-review questions there rather than adding a page
> here.

---

## How this repo works

### Versioning

`main` is always **current GA**. Each Meeting Agent release gets a tag that
mirrors the product version, so a customer onboarding onto 2.1 reads the `v2.1.x`
tag and is not confused by features that ship later.

```
git tag -a v2.1.0 -m "Meeting Agent 2.1 GA"
```

Work in flight goes on a branch named for the release it targets
(`release-2.2`), and merges to `main` when that release is GA.

### Traceability — read this before editing

Every page carries frontmatter naming the engineering documents it was derived
from:

```yaml
---
audience: IT admin
sources:
  - conversation-agent:docs/workspace-platform-routing.md
last-verified: 2026-08-24
---
```

This exists so the runbook can be **re-verified** rather than trusted. When
engineering changes a source document, the pages listing it are the ones that
went stale. A page whose `last-verified` date is older than its sources' last
change is suspect until someone re-reads it.

Do not add a claim you cannot trace to a source, a product owner, or a live test.

### OPEN markers

Where a customer will obviously ask something the source material does not
answer, the page carries a visible marker rather than a guess:

> **OPEN —** What is the maximum meeting length? · _ask: Meeting Agent product owner_

These are deliberate. They are the backlog for the next revision. Resolve them
by asking the named owner and replacing the marker with the answer — never by
deleting the marker.

### What must never go in this repo

This runbook is handed to customers. It is derived from private engineering
documentation, and some of that material must not cross over:

- **Anti-detection and platform-evasion detail.** The engineering docs describe
  in specifics how the bot gets past Teams, Meet, and Zoom automated-join
  detection. That is competitively sensitive, it changes constantly, and no
  customer needs it. State *what works*; never *how detection is circumvented*.
- Internal hostnames, cluster names, namespaces, API keys, or `curl` examples
  carrying dev credentials.
- Incident and RCA narratives naming internal environments or customers.
- Unshipped roadmap presented as though it exists today.

### Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).
