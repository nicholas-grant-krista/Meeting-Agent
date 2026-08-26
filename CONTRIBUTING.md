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

Write for the reader named in the page's `audience:` field. This is customer-facing
writing, so the tone matters as much as the facts.

**Krista is "she."** She joins your meeting, she listens, she'll pause when you ask
her to. Not "it," and not "the bot" where "Krista" reads naturally. Reserve *the
Krista Bot* for the moments you genuinely mean the capture route rather than
Krista herself.

**Be welcoming.** The reader is often new, sometimes a little wary of a recorder
in the room. Write like a helpful colleague showing them round, not like a manual.
Warmth costs nothing and changes how the whole guide lands.

**Offer, don't instruct.** "You can ask her to pause at any time" rather than "Type
this command." "Many teams find it helps to…" rather than "You must…". The reader
decides; we're here to make the choice easy. Avoid stacked imperatives, "please",
and anything that reads as telling a customer off.

**Plain language over product vocabulary.** "Krista joins your meeting and records
it," not "the KRISTA_BOT handler is deployed as an ephemeral job."

**Be straight about limits, kindly.** A customer who discovers a gap themselves in
week three trusts the guide less than one who read about it in week one. Frame it
as what to expect rather than what she can't do — and never hedge a fact we
actually know. Exact numbers stay exact; only the framing softens.

## Review

At least one reviewer, and for anything touching setup steps or data handling
that reviewer should be someone who has run the setup or owns the feature.

Security-review material needs product-owner **and legal** sign-off before it is
published at all — customers forward that content verbatim to their own security
teams. It is deliberately absent from this repo until then.
