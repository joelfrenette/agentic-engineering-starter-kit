# Prompt 07 — Session Pre-Flight Checklist
**Use this:** At the start of EVERY session, before any code is written. Takes 3 minutes. Saves hours.

---

## FILL THIS IN YOURSELF (it's a checklist for you, not the agent):

---

### Pre-Flight Checklist

**Date:** _______________
**Branch:** _______________
**Session goal:** _______________

---

**[ ] 1. Phase declared**

What phase is this session in?

```
[ ] PLAN    -- planning a feature or approach
[ ] BUILD   -- architecting a solution
[ ] CODE    -- implementing an approved plan
[ ] QA      -- testing or diagnosing bugs
[ ] UAT     -- browser testing as a real user
[ ] AUDIT   -- reviewing the codebase systematically
[ ] MENTOR  -- learning or getting advice
```

**Active phase:** _______________

---

**[ ] 2. Docs are current**

When were the living docs last updated? _______________

If more than [your threshold -- recommend: 1 week for active projects], regenerate before this session.

```
[ ] Living docs are current (updated within threshold)
[ ] Docs need regeneration -- do this BEFORE starting session
```

---

**[ ] 3. Single session goal defined**

Write the goal of this session in ONE sentence:

> _______________

If you needed more than one sentence, the session is too big. Break it into two sessions.

---

**[ ] 4. "Do not touch" list written**

What must not be changed in this session?

```
Files:
- _______________
- _______________

Systems/features:
- _______________
- _______________

Patterns:
- _______________
```

This list goes into every prompt you send this session.

---

**[ ] 5. Staging is green**

Before building anything new, confirm staging is passing.

```
[ ] Staging is passing -- clear to build
[ ] Staging has a known failing issue -- fix this first before adding new work
[ ] Staging has an unknown issue -- investigate before proceeding
```

---

### Session kick-off prompt (paste into agent after checklist is complete)

---

You are starting a new session on **[PROJECT NAME]**.

**Mode:** [YOUR DECLARED PHASE]
**Branch:** [BRANCH NAME]
**Session goal:** [YOUR ONE-SENTENCE GOAL]

Before doing anything:
1. Read RULES.md: [paste or reference]
2. Read the relevant living docs: [paste relevant sections]
3. Confirm you understand the goal and the mode.
4. Confirm you will NOT modify: [paste your "do not touch" list]

Do not write any code until I give you the working prompt for this session.

---

### At the end of the session

Before closing:

**[ ] Committed?** All working code is committed with a descriptive message.

**[ ] Staging passing?** If not, flag for next session -- don't leave it broken.

**[ ] Docs updated?** If any schema, routes, or features changed, update living docs.

**[ ] Lessons learned?** Anything that should go into RULES.md? Add it now, not "later."

**[ ] Scope stayed frozen?** If scope crept, note what happened and add a guardrail to the relevant prompt.

---

*Part of the Agentic Engineering methodology.*
