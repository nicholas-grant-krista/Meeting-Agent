# Changelog

Changes to the run book itself. For changes to the Meeting Agent product, see the
product release notes.

The format is loosely [Keep a Changelog](https://keepachangelog.com/). Tags mirror
the Meeting Agent release they document.

## [Unreleased]

### Added
- Initial run book covering Meeting Agent `2.1` / Meeting Bot `1.0`:
  overview, setup (Teams / Google Meet / Zoom), workspace configuration, users
  and roles, verification, best practices, meeting hygiene, day-2 admin, FAQ,
  troubleshooting, glossary, and limits.
- Traceability frontmatter on every page naming its engineering sources.
- OPEN-marker convention for questions the source material does not answer.

### Not included
- **Data handling / security-review page.** Held back until its open questions
  are answered and signed off by product and legal. Customers forward that
  content verbatim into vendor security reviews, so it publishes when it is
  exact. Route security questions to the customer's Krista TAM until then.

### Notes
- This first pass is derived from internal engineering documentation as of
  2026-08-24. Every OPEN marker in the set is a question that needs a
  product-owner answer before this is handed to a customer unaccompanied.

### Changed
- `limits-and-quotas.md` rewritten from source: meeting duration cap (3 h),
  silence timeout (5 min), lobby wait (5 min), no-one-joined and everyone-left
  windows, bot prepare/join offsets, scheduling scope and cycle, and field
  limits are now stated rather than marked open.
- Established that there are **no per-tier volume quotas** and **no configured
  concurrency limit**, and said so plainly rather than leaving both ambiguous.
- Two OPEN items remain on that page and are the real gaps: deployment capacity
  for simultaneous captures, and a measured post-meeting processing expectation.
- `capabilities-matrix.md` now states the 3-hour cap instead of asking about it.
- Propagated the confirmed timings out of the reference table into the pages
  where a customer actually meets them: the lifecycle in `how-it-works.md`, the
  five-minute admission window in `meeting-hygiene.md`, `05-troubleshooting.md`
  and `verify-your-setup.md`, same-day routing in `workspace-configuration.md`
  and `best-practices.md`, and new FAQ entries for the duration cap, silence and
  empty-meeting behaviour, trial limits, and simultaneous capture.

### Fixed
- **The run book said Meeting Agent does not participate in meetings. It does.**
  The bot reads meeting chat and acts on commands addressed to it — `pause`,
  `resume`, `opt out`, `remove last X minutes`, `help` — and posts a welcome
  message explaining them. Corrected in `what-is-meeting-agent.md`,
  `capabilities-matrix.md`, and `meeting-hygiene.md`, all of which stated the
  opposite.

### Changed
- **`04-faq.md` rebuilt as the primary page.** Reordered around the user's
  journey through a meeting rather than by system taxonomy, opened with a
  quick-answers table, and added the in-meeting commands, the help escalation
  path, and "I'm not seeing my transcript — where do I look?" with a
  self-service checklist.
- Chat commands added to `meeting-hygiene.md` as the end-user privacy controls,
  to the glossary, and to `05-troubleshooting.md` as a cause of missing content
  that is not a fault.

### Changed — voice
- **Krista is now "she" throughout.** She joins, she listens, she'll pause when
  asked. Applied across all 20 pages; the voice rule is recorded in
  CONTRIBUTING.md so it holds.
- **Warmer, less prescriptive tone**, with the deepest rework on the pages
  customers actually read: the FAQ (retitled "Questions people ask"),
  `meeting-hygiene.md`, `what-is-meeting-agent.md` ("Meet Krista"), and
  `how-it-works.md`. Instructions became offers — "you can ask her to pause"
  rather than "type this command".
- Disambiguated **Krista the company** from **Krista herself** where the two
  collided: "raise with Krista" is now "raise with Krista Support".

### Added
- **`first-time-registration.md` — the end-user setup walkthrough.** The guide had
  nothing for the person actually being onboarded; setup was entirely
  admin-facing. Covers sign-in, connecting the calendar via Microsoft, the
  close-and-reopen step that catches people out, and where the User Guide lives.
  Derived from the internal Registration Quick Start and generalised — no
  customer name, domain, or tenant detail.

### Changed
- `prerequisites.md` now states that **each user connects their own calendar** with
  their organizational Microsoft account, and flags the two things to line up
  first: accounts must be on your registered domains, and Microsoft sign-in must
  not be blocked.
- FAQ gains a **Getting started** section — how to set up, why Microsoft sign-in is
  needed, the "New Conversation Agent" naming, the "Authentication Failed"
  non-failure, and meetings not appearing.
- Help is now precise: the **?** icon top-right, opening the User Guide with video
  tutorials — replacing the vaguer "help icon" wording.
- `05-troubleshooting.md` gains a registration table covering the first-sign-in
  symptoms, most of which are self-service.

### Answered
- **Krista manages the AI configuration centrally** — customers don't supply or
  maintain model credentials. (`workspace-configuration.md`)
- **No customer-side network requirements** — no allowlists, IP ranges, or
  firewall changes; the TAM handles anything environment-specific.
  (`prerequisites.md`)
- **Bulk user provisioning is handled by the TAM** from a master list supplied by
  customer IT — no one-at-a-time console work. (`users-and-roles.md`)

### Changed
- Reworded the concurrency open item, which conflated two questions: environment
  capacity (an ops sizing figure) and what a customer actually sees at the
  ceiling (a product behaviour). Only the second belongs on a customer page, and
  it is now stated as unverified inference rather than implied fact.
- Data handling is now recorded as **intentionally out of scope** rather than
  pending sign-off. Security-review questions are answered per customer by their
  TAM.
