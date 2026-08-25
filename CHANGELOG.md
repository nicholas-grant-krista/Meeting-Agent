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
