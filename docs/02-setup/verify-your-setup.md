---
audience: IT admin / Workspace Admin
product-version: "2.1"
sources:
  - conversation-agent:docs/workspace-platform-routing.md
  - conversation-agent:docs/meeting-bot-end-state-policy.md
  - conversation-agent:docs/user-management.md
last-verified: 2026-08-24
---

# Verify your setup

Do not declare go-live from a settings screen. Run a real meeting through the
whole path first.

Budget about 30 minutes and two people.

## Test 1 — Internal meeting

**Setup:** Schedule a short Teams meeting between two licensed users on your
internal domains. Talk for two or three minutes — enough for a real transcript.
Say something distinctive and quotable so you can confirm attribution later.

**Expect:**

- [ ] The meeting appears in Meeting Agent before it starts
- [ ] It is routed the way you configured the internal bucket
- [ ] If routed to `Krista Bot`, a participant appears in the roster with your
      configured display name
- [ ] After the meeting: a transcript exists
- [ ] Speakers are attributed correctly
- [ ] A summary is generated
- [ ] Action items are extracted
- [ ] Your configured follow-up actions ran

**If routed to `None`:** the meeting should appear and be marked **skipped**.
That is a pass, not a failure — it confirms your opt-out works.

## Test 2 — External meeting

This is the one that finds real problems. Do not skip it because test 1 passed;
they exercise different routes entirely.

**Setup:** Have someone outside your organization host a meeting on the platform
you actually use with customers — Zoom, Meet, or Teams — and invite a licensed
user. A colleague on a personal account is fine.

**Expect:**

- [ ] The meeting appears in Meeting Agent
- [ ] It is routed to `Krista Bot`
- [ ] The bot requests admission — **the host must admit it**
- [ ] The bot appears in the roster with your display name and avatar
- [ ] After the meeting: transcript, summary, action items, follow-up actions

**Deliberately fail it once.** Run a second external meeting and do not admit the
bot. Confirm the meeting is marked **skipped** with a "never admitted" reason and
nobody is paged. Your support team should recognize this state on sight — it will
be your most common real-world question.

## Test 3 — Observer visibility

**Setup:** Have an Observer (unlicensed user) view a meeting summary shared with
them.

**Expect:**

- [ ] They can see content shared with them
- [ ] A meeting attended **only** by Observers does **not** appear in the
      workspace — this confirms the seat model is behaving

## Test 4 — Routing change

**Setup:** Change one bucket's routing and save. Schedule a meeting in that
bucket.

**Expect:**

- [ ] The new meeting follows the new routing on the next scheduling cycle, with
      no restart
- [ ] A meeting that already completed still shows its original routing —
      history is not rewritten

## Sign-off checklist

Go-live means all of these, not just the happy path:

- [ ] Internal capture verified end to end
- [ ] External capture verified end to end
- [ ] Non-admission produces a clean skip that your support team recognizes
- [ ] Bot display name is what you want external guests to see
- [ ] Transcript quality reviewed by someone who was in the meeting
- [ ] Summary and action-item quality reviewed and judged useful
- [ ] Follow-up actions land in the right place, with the right people
- [ ] Workspace Admins identified and trained on routing
- [ ] End users have received the [meeting hygiene](../03-operating/meeting-hygiene.md) one-pager
- [ ] Consent posture communicated
- [ ] Trial expiry date diarized, if applicable

## If something fails

Go to [troubleshooting](../05-troubleshooting.md). Start with the meeting's
status — Meeting Agent distinguishes "correctly nothing to do" (skipped) from
"something broke" (failed), and that distinction tells you whether the problem is
yours or ours.

---

**Next:** [Best practices](../03-operating/best-practices.md)
