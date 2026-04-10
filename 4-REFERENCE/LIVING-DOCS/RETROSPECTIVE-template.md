# Retrospective Template
**Use this:** After every promoted branch. Takes 10 minutes. Compounds into massive long-term gains.

---

## Retrospective: [BRANCH NAME]
**Date:** [DATE]
**Branch:** [branch-name]
**Session duration:** [How long this work took in total]

---

### 1. What was the goal?

[One sentence: what were you trying to accomplish?]

### 2. Did you achieve it?

```
[ ] Fully achieved
[ ] Partially achieved -- [what's left]
[ ] Not achieved -- [what happened instead]
```

---

### 3. What broke unexpectedly?

[List anything that failed that you didn't expect. These are knowledge gaps worth documenting.]

| What broke | Why it broke | Could it have been predicted? |
|------------|-------------|-------------------------------|
| | | Yes / No / Maybe |

---

### 4. What did the agent get wrong that it shouldn't have?

[If an agent violated a rule, made a wrong assumption, or produced code that needed significant correction:]

| Agent mistake | Root cause | Rule to add/improve |
|--------------|------------|---------------------|
| | | |

---

### 5. What prompt worked especially well?

[If you wrote a prompt that got great results, capture it here:]

**Prompt:**
```
[paste the prompt]
```

**Why it worked:**
[What made this prompt effective]

**Action:** Add to /PROMPTS as [filename]-v[N].md

---

### 6. Did scope creep happen?

```
[ ] No -- scope stayed frozen throughout
[ ] Yes -- [describe what crept in]
```

If yes:
- Where did it creep? [Exact moment or decision]
- Why did it happen? [Honest reflection]
- Guardrail to add: [What to add to the relevant prompt to prevent recurrence]

---

### 7. What would you do differently?

[Honest reflection. No judgment -- just useful signal for the next branch.]

1. [Thing you'd change]
2. [Thing you'd change]

---

### 8. RULES.md updates

[Every retro should produce at least one rule update. If you have none, look harder.]

**Rules to add:**
```
[DATE] - [Rule description]
What happened: [brief context]
Root cause: [what caused the problem]
Rule: [the actual rule to add]
```

**Rules to improve (existing rules that weren't clear enough):**
```
Current rule: [quote the existing rule]
Problem with it: [why it wasn't clear]
Improved rule: [better version]
```

---

### 9. Living docs updates needed

```
[ ] Architecture docs -- [what changed]
[ ] Database docs -- [what changed]
[ ] API docs -- [what changed]
[ ] Component docs -- [what changed]
[ ] Feature docs -- [what changed]
[ ] No updates needed
```

---

### 10. The one-line summary

[Complete this sentence:]

"This branch taught me: _______________"

---

*Part of the Agentic Engineering methodology. This is where the system gets smarter.*
