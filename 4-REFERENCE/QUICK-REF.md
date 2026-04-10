# Agentic Engineering — Quick Reference

> Print this. Pin it. Read it before every session.

---

## The 10 Commandments

1. One prompt, one task. Never two.
2. Always tell it what NOT to touch.
3. Read before you write. Always.
4. Plan → Approve → Implement. Never skip approval.
5. Commit small, commit often. Branches are cheap.
6. Freeze scope when you enter a branch.
7. Screenshot + error + console log = the debug holy trinity.
8. The agent is a brilliant but careless junior dev.
9. When in doubt, audit first.
10. Hard-won lessons go into rules files, not your memory.

---

## Session Pre-Flight (30 seconds)

- [ ] Phase declared? (PLAN / BUILD / CODE / QA / UAT / AUDIT)
- [ ] Docs current?
- [ ] ONE session goal written?
- [ ] "Do not touch" list written?
- [ ] Staging green?

---

## Roles at a Glance

| Mode | Agent does | Agent does NOT |
|------|-----------|----------------|
| MENTOR | Explain, advise, recommend | Write code |
| PLAN | Task breakdowns, estimates | Write code |
| ARCHITECT | Schema, API, component design | Write code |
| CODE | Implement approved plan | Add unrequested features |
| QA | Find bugs, write test cases | Fix bugs |
| AUDIT | Find problems, write report | Fix problems |
| UAT | That's you | Trust the agent |

---

## Every Branch Starts With

**Prompt 1:** "Read RULES.md + [relevant docs]. Summarize your understanding before doing anything."

**Prompt 2:** "Flag any gaps or stale info in the living docs. Don't update yet."

**Prompt 3:** "List the 5 rules from RULES.md most relevant to this branch."

---

## Bug Report Template

```
EXPECTED: [what should have happened]
ACTUAL: [what actually happened]
EVIDENCE:
  - Screenshot: [attached]
  - Console error: [pasted text]
  - Server log: [pasted text]
STEPS TO REPRODUCE:
  1. [step]
  2. [step]
  3. [where it breaks]
```

---

## Kill Switch Criteria

Abandon the branch when:
- 5+ fix attempts on the same bug
- Fixes in one area break two others
- Agent can't explain what it changed or why
- You've been on this branch 3+ days

**Before abandoning:** Write 3 sentences on what failed. Add lessons to RULES.md. Start fresh.

---

## Retro Checklist (after every promote)

- [ ] What broke unexpectedly?
- [ ] What did the agent get wrong it shouldn't have?
- [ ] What prompt worked especially well?
- [ ] Did scope creep? Where?
- [ ] Update RULES.md with at least one new/improved rule
- [ ] Update living docs

---

## The 3-Minute Rule

Always wait **3 minutes** after pushing to staging before testing.
Deployments need time. Testing too early = testing the old version.

---

*Agentic Engineering -- developed with the vibe coding community*
*github.com/[your-handle]/agentic-engineering-starter-kit*

---

## The Golden Phases (Before Any Code)

```
VISION & GOALS → PRODUCT BLUEPRINT → ARCHITECTURE → BOOTSTRAP → CODE
```

- [ ] VISION.md complete and approved? (Prompt 09)
- [ ] BLUEPRINT.md complete and approved? (Prompt 10)
- [ ] Walking skeleton defined before Phase 1 starts?
- [ ] Red team pass run on the plan?
- [ ] Explicit out-of-scope list written?

**Walking skeleton rule:** Build the thinnest end-to-end slice first.
One user. One core action. Every layer of the stack. Nothing else.

---

## Advanced Techniques

**Explain it back** -- after any complex prompt, ask the agent to restate the goal before coding. Catches misinterpretations before they become 200 lines of wrong code.

**Negative space prompt** -- describe what the feature does NOT do. Often more useful than describing what it does.

**Red team pass** -- ask an agent to argue against your own plan before committing to it.

**Prompt chaining** -- pass the OUTPUT of one phase as the INPUT of the next. Vision feeds blueprint. Blueprint feeds architecture. Architecture feeds code prompt.

**Checkpoint tags** -- `git tag v0.1-skeleton-working`. 10 seconds. Gives you clean rollback points and demo milestones.

**One breaking change per branch** -- branches with multiple coordinated breaking changes are exponentially harder to debug.
