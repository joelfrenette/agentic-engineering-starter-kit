# VISION.md — Project Vision & Goals
**Project:** [PROJECT NAME]
**Date:** [DATE]
**Version:** 1.0
**Status:** Draft / Approved

> This document is completed BEFORE any code is written. It is the foundation everything else builds on. Every agent reads this file as part of onboarding.

---

## The Problem

[2-3 sentences. What specific problem are you solving, for whom, and why existing solutions are inadequate.]

**Who has this problem:** [Specific user type -- not "everyone"]

**How they solve it today:** [Current workaround or alternative]

**Why that's inadequate:** [Specific pain point with current solution]

**Evidence this is a real problem:** [How do you know? User research, your own experience, market signals?]

---

## The User

[One paragraph. Specific enough that an agent can make design decisions based on it.]

**Primary user:** [Name the type of person. One type, not a list.]

**What they know:** [Relevant skills and context they bring]

**What they don't know:** [Technical limitations or knowledge gaps to design around]

**Their goal when they open this app:** [One sentence -- what are they trying to accomplish?]

**What would make them leave and never return:** [The failure mode to avoid above all others]

---

## The Solution

**In one sentence:** [What does this product do?]

### Core Features (minimum valuable product)

1. [Feature 1] -- [one-sentence description]
2. [Feature 2] -- [one-sentence description]
3. [Feature 3] -- [one-sentence description]
4. [Feature 4 if needed]
5. [Feature 5 if needed]

### Explicitly Out of Scope

These things will NOT be built, no matter how good the idea sounds:

- [Out of scope item 1] -- [reason / when it might be reconsidered]
- [Out of scope item 2]
- [Out of scope item 3]

**The first 5-minute win:** [What should a user be able to accomplish within 5 minutes of signing up?]

---

## The Walking Skeleton

> The walking skeleton is the thinnest possible end-to-end slice that proves the core loop works.

**The skeleton is:** [One sentence describing the minimum that proves the product concept]

**It includes:** [List the exact screens/features/data flows in the skeleton]

**It proves:** [What architectural and product assumptions does completing this validate?]

**Phase 1 is complete when a user can:** [Specific, demonstrable user action]

---

## Success Metrics

Success at **30 days:**
- [ ] [Specific measurable outcome]
- [ ] [Specific measurable outcome]

Success at **90 days:**
- [ ] [Specific measurable outcome]
- [ ] [Specific measurable outcome]

**The one metric that tells us it's working:** [Single KPI]

**We would consider this project a failure if:** [Honest failure definition]

**What we will cut first if we run out of time:** [What's lowest priority if forced to choose?]

---

## Phased Roadmap

### Phase 0: Foundation
**Complete when:** Staging and production environments deployed, auth working, database connected, core UI shell renders, team can push and test changes.
**In scope:** [List]
**Not in scope:** [List -- deferred to Phase 1+]

---

### Phase 1: Walking Skeleton
**Complete when:** [Specific user action that proves the core loop -- see Walking Skeleton above]
**In scope:** [List]
**Not in scope:** [List]

---

### Phase 2: [Name]
**Complete when:** [Specific, testable acceptance criteria]
**In scope:** [List]
**Not in scope:** [List]

---

### Phase 3: [Name]
**Complete when:** [Specific, testable acceptance criteria]
**In scope:** [List]
**Not in scope:** [List]

---

### Phase N: Polish & Scale Readiness
**Complete when:** Performance benchmarks met, security audit passed, error handling complete, onboarding flow tested with real users.

---

## Technical Constraints

**Stack:** [Framework, database, hosting, auth -- with brief rationale for each choice]

**Required integrations (Phase 1):**
- [Integration]: [why it's needed on day one]

**Required integrations (later phases):**
- [Integration]: [phase when needed]

**Non-negotiable technical requirements:**
- [Security requirement, compliance, performance target, etc.]

**Biggest technical uncertainty:** [The decision you're least confident about]

---

## Known Risks

From the red team exercise:

1. **[Risk 1]** -- [Description] -- Mitigation: [How we reduce this risk]
2. **[Risk 2]** -- [Description] -- Mitigation: [How we reduce this risk]
3. **[Risk 3]** -- [Description] -- Mitigation: [How we reduce this risk]

**The assumption most likely to be wrong:** [The thing we're betting on that we haven't proven]

---

## What We Are NOT Building

The scope boundary. If something isn't in the phased roadmap above, it isn't being built. Good ideas go to the backlog in BLUEPRINT.md.

- [Not building X because Y]
- [Not building X because Y]
- [Not building X because Y]

---

## Approval

| Reviewer | Status | Date | Notes |
|----------|--------|------|-------|
| [Your name] | Approved / Draft | | |

**Next step after approval:** Run Prompt 10 (Product Blueprint) to map every screen and user journey before architecture begins.

---

*Part of the Agentic Engineering methodology. No code is written before this document is approved.*
