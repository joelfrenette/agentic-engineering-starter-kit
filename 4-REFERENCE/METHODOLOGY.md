# Agentic Engineering: Full Methodology Reference

> Complete methodology reference. For quick-start, see README.md. For prompts, see /PROMPTS.

---

## Part 1: Philosophy & Mindset

### The Manager Mindset

The single biggest shift in Agentic Engineering is accepting that you are not the coder. You are the engineering manager. Your job is to:

- Define what needs to be built and why
- Set the rules the team operates by
- Review plans before approving implementation
- Test the output as a real user would
- Document lessons and improve the system

The AI agents are your team. A fast, tireless, occasionally overconfident team that will do exactly what you ask and sometimes exactly what you didn't mean to ask. Your job is to direct them clearly, review their work critically, and not let them run unsupervised on anything important.

### Why "Agentic Engineering" and Not "Vibe Coding"

Vibe coding is the spark. You describe intent, AI writes code, magic happens. It works. It's genuinely transformative.

The problem is that vibe coding has no system. No rules. No guard rails. And at some point every vibe coder hits the same wall: the codebase becomes a tangle of AI-generated code that nobody fully understands, bugs get fixed in ways that create three new bugs, and the AI starts hallucinating plausible-sounding solutions to problems it doesn't actually understand.

Agentic Engineering is vibe coding with a system. The creativity and speed stay. The chaos gets managed.

---

## Part 1B: The Philosophical Shift (The Most Important Update)

### The Old Way (Error-Prone)

```
You → Claude (external AI) → manual doc export → manual upload → V0 → code
→ bug found → describe bug to Claude → Claude advises → paste to V0 → fix
→ update docs manually → repeat
```

This worked. But every handoff across tool boundaries was a failure point. Docs went stale. Context got lost between sessions. The feedback loop depended on you remembering to export, upload, and re-explain. Human error was baked in.

### The New Way (Self-Contained)

```
V0 reads AI_RULES.md + CONTEXT.md → codes → end of chat → V0 updates files
→ next chat reads improved files → codes better → updates files → compounds
```

The loop never leaves V0 + GitHub. There is no export. There is no upload. There is no external AI needed for day-to-day development. The files ARE the agent's memory. The files improve themselves. Every session the system gets smarter automatically.

### What Changed

The agent's memory and improvement now live in three files in your repo -- not in your head, not in an external AI, not in a manual process:

- **AI_RULES.md** -- the rules engine. Every painful bug becomes a rule. Grows and improves with every session.
- **CONTEXT.md** -- the living project state. V0 reads it at the start of every chat. Knows exactly where you left off. Updated at the end of every chat automatically.
- **PROMPT-LOG.md** -- the prompt performance log. Captures what worked and what failed. Every session your prompts get sharper.

### The Self-Improving Loop

```
Chat starts → V0 reads AI_RULES.md + CONTEXT.md → knows the rules + current state
Chat runs  → V0 implements, tests, fixes
Chat ends  → V0 updates all three files with what changed, what worked, what failed
Commit     → Files are saved to GitHub
Next chat  → V0 reads improved files → starts smarter than last time
```

After 10 chats: the files know your project better than any template.
After 50 chats: the agent rarely makes the same class of mistake twice.
After 100 chats: your AI_RULES.md is a precisely calibrated instruction set built from real production experience with your specific codebase. No generic guide could replicate it.

This is the compounding effect applied to the AI agent itself -- not just the codebase.

### The Bonus Features (Not Required -- Just Powerful)

The three core files give you permanent memory and self-improvement. These additional capabilities compound on top of that foundation:

- **Live project tracking** -- CONTEXT.md is always current. Any agent reading it knows exactly where the project stands.
- **Self-updating documentation** -- living docs update as part of the chat close protocol. No manual doc maintenance.
- **Self-improving prompt library** -- PROMPT-LOG.md captures what works. Prompts get sharper automatically.
- **Built-in UAT tracking** -- CONTEXT.md tracks what has been UAT-approved. Nothing ships without it.

These are bonuses. The three core files alone give you the fundamental shift. Start simple. The rest follows naturally.

---

## Part 1C: The Matrix Crew -- Agent Personas

Every chat gets a named persona. Every persona has a specific mode and a specific set of behaviors it will and will not exhibit. This is not decoration -- it is a constraint system that prevents the most common V0 failure mode: mode drift.

Mode drift is when a coding agent starts planning, or a planning agent starts coding, or a QA agent starts refactoring. Personas prevent this by giving the agent a clear identity that resists out-of-mode behavior.

**The rule:** One branch. One phase. One persona. One name.

| Phase | Persona | Mode | Does | Does NOT |
|-------|---------|------|------|----------|
| MENTOR | **Morpheus the Mentor** | Advice | Explain, advise, recommend | Write code |
| PLAN | **Oracle the Organizer** | Planning | Task breakdown, estimates | Write code |
| BUILD | **The Architect** | Design | Schema, API, component design | Write code |
| CODE | **Cypher the Coder** | Implementation | Implement approved plan only | Improvise or add features |
| QA | **Trinity the Tester** | Testing | Find bugs, diagnose, document | Fix without approval |
| AUDIT | **Smith the Scrutinizer** | Audit | Find problems, report findings | Fix without approval |
| PROMOTE | **Tank the Transporter** | Deploy | Final checks, merge, tag | Skip any checklist item |
| UAT | **You (The One)** | Acceptance | Test as real user, approve/reject | Trust the agent to do this |

See PROMPTS/15-agent-personas.md for the complete persona prompts to paste at the start of each chat.

---

---

## Part 2: The Golden Phases (Before Any Code)

This is the most skipped section of any build. It is also the most valuable. The root cause of most failed or stalled projects is not bad code -- it is building the wrong thing, or building the right thing in the wrong order, because the vision was never written down.

### The correct sequence before bootstrap:

```
VISION & GOALS  →  PRODUCT BLUEPRINT  →  TECHNICAL ARCHITECTURE  →  BOOTSTRAP  →  CODE
```

Skipping any of these phases does not save time. It borrows time from later, at interest.

### Phase -2: Vision & Goals (Prompt 09)

Before a single line of code, before the repo is created, before any technical decisions:

**The Problem** -- what specific problem are you solving, for exactly whom, and why existing solutions are inadequate. Vague answers produce vague products.

**The User** -- one specific user type. Not "everyone." Specific enough that an agent can make design decisions based on it.

**The Solution** -- what the product does in one sentence; the 3-5 core features; the explicit out-of-scope list. The out-of-scope list is as important as the feature list.

**Success Metrics** -- specific and measurable at 30 and 90 days. Not "users like it."

**The Phased Roadmap** -- phases defined BEFORE features are discussed, each with a specific testable "this phase is complete when..." acceptance criteria.

**The Red Team** -- before finalizing, ask an agent to argue against your own plan. Catching a bad assumption here costs nothing. Catching it after 3 months of code costs everything.

Output: `VISION.md` in the project root. Every agent reads it. See template in `/LIVING-DOCS/00-vision-template.md`.

### Phase -1: Product Blueprint (Prompt 10)

After Vision & Goals is approved. Still no code.

**Screen & Route Map** -- every screen in the product, its route, who accesses it, what happens there. If a screen isn't in this map, it doesn't get built.

**User Journeys** -- the 3-5 most important flows, step by step. These become your UAT test cases.

**Feature Map by Phase** -- every feature assigned to a specific phase. The authoritative source of "what gets built and when."

**The Walking Skeleton** -- the thinnest possible end-to-end slice that proves the core loop works. Touches every layer of the stack. Demonstrable to a real user. Deployable to production. This is what Phase 1 must deliver.

**The Explicit Backlog** -- good ideas that are NOT in scope. They live here so they don't get lost and don't cause scope creep.

Output: `BLUEPRINT.md` in the project root. See template in `/LIVING-DOCS/00b-blueprint-template.md`.

### Why the Walking Skeleton Matters Most

Build the thinnest possible slice end-to-end first. A logged-in user performs the core action and sees the result. That's it. Nothing else.

Why: it validates your architecture before you've invested in it. It proves the core loop works before you've built 20 features on top of it. It prevents the failure mode of "everything is 80% done and nothing works end-to-end."

The walking skeleton is ugly. It has one feature. It has no polish. It is the right thing to build first.

---

## Part 3: Project Bootstrap (Do This Once)

### Step 1: Environments

Create separate staging and production environments before writing a single line of feature code.

- **Production:** your live environment, deployed from `main`
- **Staging:** your test environment, deployed from feature branches

Never share a database between staging and production. Never test directly on production. The 10 minutes it takes to set this up will save you from catastrophic mistakes.

### Step 2: RULES.md

Your `RULES.md` is the most important file in your project. Every agent reads it before doing anything. It contains:

- Non-negotiable architecture rules
- Banned patterns and why they're banned
- Required wrappers/patterns for specific operations
- File structure conventions
- Naming conventions
- Any lessons learned from past painful bugs

See the template in this repo. Fill it in for your project. Add to it constantly.

### Step 3: Living Docs Structure

Create the documentation structure at the start. Empty templates are fine -- they grow as the project grows. Structure:

```
/docs (or inline in root)
├── 01-architecture/
├── 02-database/
├── 03-api/
├── 04-components/
├── 05-features/
├── RULES.md
└── CHANGE-LOG.md
```

### Step 4: Super Prompt Library

Store your agent prompts in `/PROMPTS` in the repo. Treat them like code:
- Version them (`mentor-v1.md`, `mentor-v2.md`)
- Update them when they fail or when you learn something new
- Keep deprecated versions with a note on why they were retired

### Step 5: Commit Conventions

Establish before the first commit:

```
feat/     -- new feature
fix/      -- bug fix
refactor/ -- code change with no behavior change
audit/    -- audit pass results
docs/     -- documentation only
```

Commit message format: `feat(auth): add Google OAuth callback handler`

Small, atomic, reversible commits. Not "fixed stuff."

### Step 6: Agent Onboarding Prompt

Write `PROMPTS/00-agent-onboarding.md` with:
- What the project is and who it's for
- The tech stack
- The current phase of development
- What's working, what's broken, what's in progress
- A pointer to RULES.md

Every new session with any agent starts here.

---

## Part 3: The Session Loop

### Pre-Flight Checklist (Every Session)

Run this before touching any code. It takes 3 minutes and prevents hours of wasted work.

1. **What phase is this branch in?** PLAN / BUILD / CODE / QA / UAT / AUDIT. Declare it explicitly.
2. **Are docs current?** Stale docs = wrong context = wrong code. Regenerate if needed.
3. **What is the ONE goal of this session?** If you can't state it in one sentence, break it into smaller sessions.
4. **What is out of scope?** Write the "do not touch" list before starting. Paste it into every prompt.
5. **Is staging passing?** Never build on a broken base. Fix red before adding green.

### The Core Loop

```
Context load → Written plan → Approve → Implement → QA → Fix loop → UAT → Promote → Update docs
```

**Context load:** Agent reads RULES.md + relevant doc slice + current branch state.

**Written plan:** Agent produces a plain-English change plan: what files will be modified, what will change, what will NOT be touched. You read and approve before any code is written.

**Implement:** Engineer implements the approved plan. Modified files only. Commit on first working state.

**QA:** Push to staging. Wait 3 minutes (deployments need time). Collect: screenshot + browser console errors + server logs. Feed all three to the agent for fixes.

**Fix loop:** Fix one thing at a time. Commit each fix. Retest. Repeat until staging passes.

**UAT:** You test as a real user. No code reading. If it feels wrong, it is wrong.

**Promote + update docs:** Merge to production. Update living docs. Run the retrospective.

### The 3-Minute Rule

Always wait at least 3 minutes after pushing to staging before testing. Deployments, migrations, and CDN propagation need time. Testing too early means testing the previous version and filing false bug reports.

---

## Part 4: Branch Phase Prompts

### The Three Branch-Start Prompts

Every new branch starts with these three prompts in order. Every time.

**Prompt 1 -- Orientation:**
> "You are in [PHASE] mode for branch [name]. The goal is [one sentence]. Read RULES.md, then read [relevant doc section]. Before doing anything else, summarize your understanding of the current state."

**Prompt 2 -- Living docs check:**
> "Read the living documentation for [feature area]. Identify gaps or outdated information. Do not update anything yet -- just flag what's stale."

**Prompt 3 -- Rules confirmation:**
> "Before we write any code, confirm you have read and will enforce RULES.md. List the 5 rules most relevant to this branch's work."

### Phase Reference

| Phase | Key behavior |
|-------|-------------|
| PLAN | Break into tasks, estimate complexity (S/M/L), flag dependencies. Produce task list for approval first. |
| BUILD | Design before code. Produce schema, API contract, component tree. Architecture approval before implementation. |
| CODE | Implement approved plan only. Output modified files only. No adjacent refactoring. No unrequested features. |
| QA | Happy path + 3 edge cases + 2 failure modes. Check logs. Check auth. Check data integrity. |
| UAT | That's you. Test as a real user. If it feels wrong, it is wrong. |
| AUDIT | Specify type. Radical simplification, security, SQL, standards. Produce fix report before implementing anything. |

---

## Part 5: Prompt Engineering Discipline

### The Anatomy of a Great Coding Prompt

```
[ROLE DECLARATION]
You are in [MODE] mode.

[CONTEXT BLOCK]
Relevant doc section: [paste or reference]
Current state: [describe briefly]

[GOAL -- ONE SENTENCE]
The goal of this prompt is to [specific task].

[CONSTRAINTS -- WHAT NOT TO TOUCH]
Do not modify: [list files or systems]
Do not use: [banned patterns]
Rules to enforce: [reference RULES.md sections]

[OUTPUT FORMAT]
Produce a written change plan first. Wait for my approval. Then output only the modified files.
```

### Prompt Anti-Patterns

**"Can you also..."** -- That's a second prompt. Send it separately after the first is done.

**"Fix the bug and clean it up while you're in there."** -- Cleanup is a separate audit branch.

**Describing the solution instead of the problem.** -- Describe what's broken and what success looks like. Let the agent design the solution.

**Trusting a prompt forever.** -- Prompts age. As the codebase grows, prompts need updating. Review your prompt library monthly.

### Context Window Discipline

- Slice documentation surgically. Paste the 2-3 relevant sections, not the full bundle.
- Put rules and constraints at the TOP of long prompts. Context windows compress from the middle.
- When an agent starts "forgetting" rules mid-session, start a fresh session with clean context. Don't try to correct a degraded context window.
- Prefer markdown over PDF for documentation. Cleaner token parsing, no layout overhead.

### Prompt Version Control

Store prompts in `/PROMPTS/[role]-v[N].md`. When a prompt fails or gets improved, bump the version number. Keep old versions with a deprecation note explaining what changed and why. Your prompts are assets.

---

## Part 6: Error Taxonomy & Debug Playbook

### Error Types

| Error | Where to look | What to send the agent |
|-------|--------------|----------------------|
| Build error | CI/CD build logs | Full log text -- never screenshot a build log, paste it |
| Runtime error | Browser console + server function logs | Screenshot of UI + pasted console error + pasted server log |
| Logic error | Your own eyes during UAT | Screenshot of wrong state + expected vs actual behavior |
| Auth error | Server logs + browser network tab (401/403) | Network tab screenshot + relevant auth policy |
| Data/state bug | Database query results | SQL output showing actual vs expected state |
| AI/API error | Provider logs + server function logs | Full error response JSON |

### The Debug Trinity

Every bug report to an agent must include all three:
1. What you expected
2. What actually happened
3. Evidence (screenshot + error text + logs)

Missing any one of the three roughly doubles resolution time.

### When Fixes Make Things Worse

- **Before attempting a fix:** commit your current broken state. This gives you a revert point.
- **After 3 failed fix attempts:** switch to AUDIT mode. Ask the agent to explain the root cause before suggesting more fixes.
- **After 5 failed attempts:** invoke the Kill Switch (see Part 8).

### The Rubber Duck Pre-Step

Before pasting any error to an agent, try to explain in plain English: what is the bug, and why might it be happening? If you can explain it clearly, you often solve it yourself. If you can't, that explanation becomes the best possible opening for your debug prompt.

---

## Part 7: Living Docs System

### Why Living Docs

Your documentation is the shared brain between every AI agent you work with. When docs are current, agents make fewer mistakes, regressions decrease, and onboarding new agents to a project takes minutes instead of hours.

When docs go stale, you pay for it in wrong assumptions, phantom bugs, and agents that confidently break things they think are working differently.

### Update Triggers

| Document | Update when |
|----------|------------|
| Architecture docs | Any infrastructure or design decision changes |
| Database docs | Any schema migration |
| API docs | New or changed route |
| Component docs | New component, hook, or utility |
| Feature docs | Feature shipped, changed, or deprecated |
| RULES.md | Any new lesson learned or pattern established |
| CHANGE-LOG.md | Every promote to production |

### Automation Targets

These are the high-value automation wins for living docs:

**CI/CD doc regeneration:** A post-merge action that regenerates the doc bundle and commits it back to the repo. Eliminates stale docs entirely.

**Schema snapshot on migration:** Auto-generate database docs from database introspection on each migration. Never manually update table docs again.

**Route index from build:** Parse the framework build output to auto-update API docs on deploy.

---

## Part 8: The Kill Switch

Knowing when to abandon a branch is as important as knowing how to fix bugs. Sunk cost thinking is the enemy.

### Abandon the Branch When

- **5+ fix attempts on the same bug.** You're in a hallucination spiral. Start fresh with a clean audit on a new branch.
- **Fixes in one area consistently break two others.** Too much entangled change. Promote what works, restart what doesn't.
- **The agent can no longer explain what it changed or why.** Context has degraded to guessing. Fresh session required.
- **You've been on the same branch for 3+ days.** Scope is wrong. Break it smaller.

### Before You Abandon: Save the Lessons

1. Write 3 sentences: what you tried, what failed, why you think it failed.
2. Add any newly discovered rules to RULES.md before deleting the branch.
3. Screenshot the error state for the next attempt's reference.

### The Restart Protocol

New branch from main. Fresh session with no baggage. Paste the lessons-learned summary as Prompt 1. You now have all the knowledge from the failed branch without any of the corrupted code.

---

## Part 9: The Retrospective Loop

This is the compounding multiplier. Most builders skip it. Don't.

### After Every Promoted Branch

1. **What broke unexpectedly?** These are knowledge gaps. Document them.
2. **What did the agent get wrong that it shouldn't have?** The rule wasn't clear enough. Fix the doc.
3. **What prompt worked especially well?** Capture it. Version it. Make it a template.
4. **Did scope creep happen? Where exactly?** Add a guardrail to prevent recurrence.
5. **Update RULES.md.** Every retro should produce at least one improved rule.

### The Compounding Effect

At 90 days with no retro loop: you're doing the same work faster.
At 90 days with a retro loop: your agents make fewer mistakes every month because the rules file gets smarter every week.

The retro loop is where Agentic Engineering compounds. It is the difference between a methodology and just a faster way to work.

### Monthly Methodology Audit

Once a month: ask your AI orchestrator to review your RULES.md and prompt library. Ask it: "What gaps do you see? What rules are contradicting each other? What's missing?" Treat it like a performance review for the system, not the people.

---

## Part 10: The Built-In QA System (Admin UAT Runner)

This is one of the most powerful extensions of Agentic Engineering: baking the testing loop directly into the product itself.

### The Concept

Instead of maintaining an external test checklist or relying on memory during UAT, you build a **UAT Test Runner** into your app's own admin dashboard. The app tests itself from the inside -- hitting its own API routes, reading its own database, and presenting a pass/fail dashboard you can check with a single click.

This closes the loop between shipping and validating. No external tools. No separate test suite to maintain. No mental checklist to forget.

### Why This Is Different

Traditional testing workflows treat QA as something that happens outside the product -- in a terminal, a spreadsheet, or an external tool. The Admin UAT Runner treats testing as a **feature of the product itself**.

The result:
- Any admin (technical or not) can run QA
- Tests are always current because they run against the live app
- Old phases accumulate as regression tests automatically
- The testing discipline compounds with the product, not alongside it

### The Hybrid Model

The UAT Runner uses two types of checks, because not everything can or should be automated:

**Automated checks** validate data and API state. These are objective:
- Does this API route return HTTP 200?
- Does this database row exist?
- Is this token populated?
- Does this config value resolve correctly?

**Manual steps** validate UI and UX. These require human judgment:
- Does this element render correctly?
- Does this redirect feel right?
- Does this flow make sense to a real user?

Never try to automate UI judgment -- it produces fragile tests and false confidence. Keep manual steps short, with plain-English instructions a non-technical person can follow.

### Phase-Based Structure

Test suites are organized by development phase -- one phase per major feature branch. Each phase contains its automated checks and manual steps. Old phases never get deleted; they become your regression test suite.

When you click "Run All Phases," every automated check from every shipped phase runs. If Phase 1's chat tests fail after you shipped Phase 5, you find out immediately.

### When to Add a New Phase

After every major branch promotes to production:

1. Add a new `UATPhase` object to the config file
2. Write automated checks for every new API route or DB state change
3. Write manual steps for every new UI element that needs verification
4. Write manual step instructions in plain English for a non-technical tester
5. Commit as part of the promotion process

**Rule:** Every promoted branch should produce at least 2 automated checks and 1 manual step. If you can't write any checks, you haven't thought clearly about what you just shipped.

### Implementation

See `PROMPTS/08-admin-uat-runner.md` for the complete super prompt to build this into any project (Part A: build it once; Part B: add a new phase after each branch).

See `LIVING-DOCS/06-uat-runner.md` for the documentation template.

### Future: Closing the Loop Fully

Once the manual UAT pass is consistent, the automation targets are:
- **CI/CD trigger:** Run automated checks on every staging deploy, flag as passing/failing before UAT begins
- **Regression alerts:** Notify when a previously passing phase starts failing
- **Scheduled runs:** Nightly regression sweeps to catch environment drift

---

*Last updated: See CHANGE-LOG.md*

---

## Part 11: Advanced Best Practices (What Most Vibe Coders Miss)

### Prompt Chaining

The output of one agent prompt becomes the structured input of the next. Rather than treating each session as independent, you explicitly pass context forward:

- Vision & Goals → feeds the agent onboarding prompt
- Approved architecture → feeds the CODE mode prompt verbatim
- QA bug report → feeds the fix prompt with exact error context
- Retro lessons → feeds the next branch's Prompt 1

Chaining prevents the context loss that causes agents to repeat mistakes or contradict earlier decisions.

### The "Explain It Back" Verification

After any complex prompt, before the agent writes a single line of code:

> "Before you start, explain in 3-5 sentences what you understood the goal to be, what you will NOT touch, and what you plan to produce."

If the explanation is wrong, you catch the misinterpretation before it becomes 200 lines of wrong code. This single habit eliminates a significant category of wasted sessions.

### The "Negative Space" Prompt

When describing a feature, explicitly describe what the finished version does NOT do. This is often more useful than describing what it does:

> "This component does NOT fetch its own data -- it receives data as props. It does NOT handle errors -- the parent handles errors. It does NOT navigate -- it calls a callback."

Agents that know the boundary of a feature build it more accurately than agents who must infer the boundary from what's described.

### The Red Team Prompt

Before committing to any significant architectural decision, run a dedicated red team pass:

> "You are a skeptical senior engineer reviewing this plan. What are the 3 most likely ways this fails? What assumptions are we making that might be wrong? What would you build differently and why?"

Run this before major phases, not during them.

### Checkpoint Tags

Beyond regular commits, tag working milestones:

```
git tag -a v0.1-skeleton-working -m "Walking skeleton: auth + core loop end to end"
git tag -a v0.2-phase1-complete -m "Phase 1 all UAT checks passing"
```

Tags give you clean demo points, rollback targets, and a visible progress timeline. They cost 10 seconds each.

### Token Budget Planning

Before a session, decide which slices of your living docs to feed which agents. Pasting everything to everyone wastes tokens and dilutes attention. A simple planning step:

- CODE mode for a database feature: feed DB schema + API doc + RULES.md only
- AUDIT mode for security: feed API routes + auth architecture + RULES.md only
- QA mode: feed feature doc + recent change log + RULES.md only

The right context fed precisely outperforms comprehensive context fed randomly.

### The "One Breaking Change Per Branch" Rule

Every branch should introduce exactly one breaking change (if any). A breaking change is any change that requires coordinated updates across multiple layers -- schema migration + API change + frontend update at the same time.

Branches with multiple breaking changes are exponentially harder to debug and impossible to roll back cleanly. If you find yourself needing two breaking changes, that's two branches.

### Prompt Versioning as a Feedback Loop

When a prompt produces surprisingly good results, capture exactly why it worked and version it up. When a prompt fails, note what was missing and version it up. Over time, your prompt library becomes a compounding asset -- each version slightly better than the last.

The builders who improve fastest with AI are not the ones with the best AI. They are the ones with the best prompt libraries, because their prompts encode everything they've learned.


---

## Part 12: Agile / Scrum Aliases

Every Agile99 phase mapped to its Agile/Scrum equivalent. Use Agile99 as the primary language -- the aliases help when collaborating with teams or stakeholders who speak standard Agile.

| Agile99 Phase | Agile / Scrum Equivalent |
|--------------|--------------------------|
| VISION & GOALS | Product Vision; Epic Definition |
| PRODUCT BLUEPRINT | Story Mapping; PRD; Backlog Creation |
| SPRINT ZERO | Sprint Zero; Foundation Sprint |
| PLAN mode | Sprint Planning; Backlog Refinement |
| ARCHITECT mode | Architecture Spike; Technical Design |
| CODE mode | Sprint Execution; Development |
| QA mode | Sprint QA; Test Pass |
| UAT mode | User Acceptance Testing; Stakeholder Review |
| PROMOTE | Sprint Release; Ship It |
| AUDIT mode | Technical Debt Sprint; Hardening Sprint |
| RETRO | Sprint Retrospective |
| OPERATE | Kanban / Operations; Maintenance |
| CHECKPOINT | Milestone Tag; Release Baseline |
| 8S AUDIT | Definition of Done; Quality Gate |

---

## Part 13: The 99x Equation

The "99" in Agile99 is not arbitrary. Here is the math, shown honestly.

### The inputs

**Traditional Agile sprint (lean 3-developer startup team):**
- Duration: 2 weeks = 10 business days
- 3 developers × 10 days × 8 hours = 240 person-hours per sprint
- At $75/hr blended rate = $18,000 per sprint

**Agile99 branch (one founder + AI agents):**
- Duration: 1 focused business day
- 1 person × 8 hours = 8 person-hours
- Your time + ~$5 in AI API costs = ~$605 at same rate

### The ratios

- **Time:** 10 days → 1 day = **10x faster per iteration**
- **Cost:** $18,000 → $605 = **~30x cheaper per sprint**
- **Person-hours:** 240 → 8 = **30x fewer hours**

### The compound claim

10x faster iteration × ~10x cheaper team cost = **~99x more efficient**

The "10x cheaper team" is the conservative figure. A traditional 3-dev startup team costs ~$450k/year in salaries. A solo Agile99 founder spends ~$1,200/year in AI tools. That's 375x cheaper on headcount -- which more than supports the compound math.

### The honest caveat

The 99x is a **compound efficiency** claim (speed × cost), not a pure calendar time claim. A solo founder with AI agents cannot out-code a 10-person team on raw parallel execution. The advantage is **iteration velocity and cost-to-ship** -- the number of tested, deployed features per dollar and per day. That is where Agile99 genuinely dominates.

### Agile99 sprint length

At 10x faster per iteration vs. a traditional 2-week sprint:
- **Small feature branch:** half a business day (2-4 hours)
- **Medium feature branch:** 1 business day (4-8 hours)  
- **Large feature branch:** 2-3 business days

You can run 2-3 sprints per day on focused features. A traditional team runs 1 sprint per 2 weeks. That is the velocity gap.



---

## Part 14: The Simple Rules (Catchy Edition)

These rules exist because the best rules are the ones you actually remember.

**A Feature in Five** -- 5 chats, 5 branches, 1 shipped feature. Every feature. Every time.

**Prompt 21 is Done** -- Maximum 20 prompts per chat. Hit 21? Close the chat. Open a new one. Paste the opener. The files carry the context -- not the chat.

**New Branch. New Name.** -- One branch = one phase = one persona. When the phase changes, the chat closes, the persona changes, a new branch begins.

**Read Before You Write** -- Agent reads AI_RULES.md + CONTEXT.md before writing a single line. No confirmation line output = stop and demand it.

**Plan Before You Build** -- No code without an approved plan. The Architect does not build what Oracle has not approved.

**One Thing. One Prompt.** -- Never ask for two things in one prompt. "And also..." is a second prompt. Send it separately.

**Show Don't Describe** -- Screenshot + console error + Vercel log. Never describe a bug in prose when you can show it.

**Main is Sacred** -- Never push directly to main. PRs only. Branch protection is on. Non-negotiable.

**Close the Chat, Not the Tab** -- Run the End of Chat Protocol before closing any chat. Five minutes now saves hours next session.

**When in Doubt, Audit** -- Messy code gets Smith before Cypher. Audit before features.

**Wake Up, Neo** -- UAT is yours. No agent can test it for you. Open the staging URL. Use it as a real user. If it feels wrong -- it is wrong.

See SIMPLE-RULES.md in the project root for the printable one-page version.


---

## Part 15: Guided Intake Prompting (Morpheus Mode)

### The Concept

Standard AI tools wait to be told what to do. Guided Intake Prompting flips that dynamic entirely.

Instead of: **User → AI → action**
It becomes: **AI → User → AI → action**

At the start of every session, Morpheus (the AI) leads Neo (you) through a structured intake process before anything is built, designed, or coded. The AI asks the questions. You answer. The right crew member is summoned based on your answers.

This is not a gimmick. It is the methodology's answer to one of the most common failure modes in vibe coding: starting to build before understanding what you are actually trying to accomplish.

### Why It Works

Most sessions fail not because of bad code but because of bad intake. The developer (or vibe coder) opens the AI tool, describes something half-formed, and the agent starts building based on an incomplete picture. This produces work that needs to be redone.

Morpheus Mode solves this by making intake the mandatory first step of every session. You cannot skip it. The AI will not let you. You get routed to the right crew member only after Morpheus understands what you need.

### What It Captures

Before any work begins, Morpheus captures:

1. **The current phase** -- read from CONTEXT.md, confirmed with Neo
2. **The session goal** -- one sentence, in Neo's own words
3. **User stories** -- structured as "As a [user], I want [action], so that [outcome]" with a use case number
4. **Scope boundary** -- what this session will NOT do
5. **Evidence** (for QA sessions) -- screenshot, console error, Vercel log

These are logged in the session before any crew member is activated.

### The Seven Routes

Morpheus opens every session with a numbered menu and routes based on the answer:

1. **PLAN** → Oracle the Organizer (task breakdown, use case to feature)
2. **DESIGN** → The Architect (schema, API contract, component design)
3. **CODE** → Cypher the Coder (implement approved plan)
4. **TEST/FIX** → Trinity the Tester (bug diagnosis and fix)
5. **SHIP** → Tank the Transporter (promote to production)
6. **AUDIT** → Smith the Scrutinizer (security, simplification, standards, SQL)
7. **MENTOR** → Morpheus stays (explain, advise, guide)

### Where to Paste It

**V0.app:** Project → Settings → Instructions (system prompt field)
**Dyad.sh:** Project settings → System prompt

See `PROMPTS/16-morpheus-system-prompt.md` for the complete paste-ready prompt.

### The Use Case Log Format

Every user story captured by Morpheus is logged in this format:

```
═══════════════════════════════════════════
USE CASE #[N] — [Date]
═══════════════════════════════════════════
As a:     [specific user type]
I want:   [what they want to do]
So that:  [outcome or benefit]
Priority: High / Medium / Low
Phase:    [which development phase]
═══════════════════════════════════════════
```

These use cases feed directly into Oracle's task breakdown, which feeds into The Architect's design, which feeds into Cypher's implementation. The chain is unbroken.

### The Rule

**Morpheus never writes code.** Even if Neo begs. Even if the task seems obvious. Morpheus routes. The crew builds.

