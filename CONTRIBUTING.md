# Contributing to the Meeting Agent Run Book

This is customer-facing material. The bar is different from an internal doc: a
wrong sentence here becomes a wrong sentence in a customer's onboarding call.

## Before you edit

1. **Know which release you are documenting.** `main` is current GA. If the
   behaviour you are writing about has not shipped, it goes on a `release-X.Y`
   branch, not `main`.
2. **Read the source.** Every page lists its `sources:` in frontmatter. Read them
   before changing a claim they support.
3. **Check the redaction rules** in [README.md](README.md#what-must-never-go-in-this-repo).
   Anti-detection detail, internal infrastructure, and credentials never cross over
   from the engineering repos.

## Making a change

- One logical change per commit. A page plus its FAQ entry plus its glossary term
  is one commit; six unrelated pages is six.
- Update `last-verified` in the frontmatter when you re-read the sources and
  confirm the page is still accurate. Leave it alone if you only fixed a typo.
- Add a `CHANGELOG.md` entry for anything a customer would notice.
- If you resolve an OPEN marker, replace it with the answer and note who
  confirmed it. Do not silently delete it.

## Voice

Write for the reader named in the page's `audience:` field.

- **Plain language over product vocabulary.** "The bot joins your meeting and
  records it," not "the KRISTA_BOT handler is deployed as an ephemeral job."
- **Say what is not supported, plainly.** A customer who finds a gap themselves
  in week three trusts the document less than one who read about it in week one.
- **No hedging on facts we know.** If it works, say it works. Reserve
  qualification for things that are genuinely conditional.
- **Second person for instructions.** "Set the internal bucket to…", not "The
  admin should set…".

## Review

At least one reviewer, and for anything touching setup steps or data handling
that reviewer should be someone who has run the setup or owns the feature.

Security-review material needs product-owner **and legal** sign-off before it is
published at all — customers forward that content verbatim to their own security
teams. It is deliberately absent from this repo until then.
