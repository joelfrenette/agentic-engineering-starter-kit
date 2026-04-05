# Agentic Engineering Starter Kit

> *The evolved methodology for building real software with AI agents -- developed across multiple production projects and refined with the vibe coding community.*

---

## What Is Agentic Engineering?

Vibe coding got us excited. Agentic Engineering gets things shipped.

Vibe coding is the spark -- the idea that you can describe intent and let AI handle implementation. Agentic Engineering is the system that makes it repeatable, scalable, and production-grade.

After building multiple projects on GitHub using AI agents end-to-end, I kept running into the same failure modes: regressions from agents touching things they shouldn't, scope creep that turned 2-hour fixes into 2-day disasters, living docs that went stale and poisoned every subsequent prompt, and painful debugging loops with no clear exit criteria.

This starter kit is the methodology I developed to solve all of that. It works whether you're a solo founder, a non-technical builder, or a developer who wants to move faster with AI. It is tool-agnostic -- the principles apply whether you're using V0.dev, Cursor, Windsurf, Claude, GPT-4, or whatever ships next month.

**The core insight:** You are not the coder. You are the engineering manager. The moment you internalize that, everything changes.

---

## The 10 Commandments of Agentic Engineering

1. **One prompt, one task. Never two.** Every time you ask an AI agent to do two things in one prompt, it does both wrong.
2. **Always tell it what NOT to touch.** Most AI regressions happen because you forgot to define the boundary.
3. **Read before you write. Always.** Agent reads relevant docs before writing a single line. No exceptions.
4. **Plan → Approve → Implement. Never skip approval.** Written plan first. Your sign-off. Then code.
5. **Commit small, commit often.** Every working state is a checkpoint. Branches are cheap. Lost work is not.
6. **Freeze scope when you enter a branch.** "While we're in here..." is how 2-hour fixes become 2-day disasters.
7. **Screenshot + error + console log = the debug holy trinity.** Never describe a bug in prose if you can show it.
8. **The agent is a brilliant but careless junior dev.** Review everything before promoting. You are the senior engineer.
9. **When in doubt, audit first.** Debt compounds. Clean before you build on top.
10. **Hard-won lessons go into rules files, not your memory.** Document every painful lesson immediately.

---

## The Agent Team

Agentic Engineering works by giving each AI agent a clear role, mode, and scope. Never let an agent "just figure it out" -- declare the role at the start of every prompt.

| Role | Mode | What They Do |
|------|------|--------------|
| **Mentor** | `MENTOR` | Onboarding, best practices, explains "why" not just "what" |
| **Project Manager** | `PLAN` | Breaks features into tasks, estimates complexity, flags dependencies |
| **Architect** | `BUILD` | System design, schema decisions, ADRs, integration patterns |
| **Engineer** | `CODE` | Implementation only -- reads plan, follows rules, outputs modified files |
| **QA** | `TEST` | Test plans, edge cases, regression checks, log triage |
| **Auditor** | `AUDIT` | Dead code, security, SQL, standards, simplification |
| **You** | `UAT` | Browser testing, business judgment, final approve/reject |

**Role activation:** Always start your prompt with the role. Example: *"You are in ARCHITECT mode. Before writing any code, read RULES.md and produce a schema design for approval."*

---

## The Workflow at a Glance

```
NEW BRANCH
    │
    ▼
Prompt 1: Mentor / orientation (read docs, confirm understanding)
Prompt 2: Living docs read + flag gaps
Prompt 3: Rules confirmation
    │
    ▼
[PLAN] PM produces task breakdown → you approve
    │
    ▼
[BUILD] Architect designs → you approve schema/API/components
    │
    ▼
[CODE] Engineer implements approved plan → commit immediately
    │
    ▼
[QA] Push to staging → wait 3 min → test → collect evidence
    │
    ├── Bug found → [fix loop] → commit each fix → retest
    │
    ▼
[UAT] You test in browser as a real user
    │
    ├── Fail → back to fix loop
    │
    ▼
[PROMOTE] Merge to production → update living docs → run retro
```

---

## What's In This Kit

```
agentic-engineering-starter-kit/
│
├── README.md                          ← You are here
├── RULES.md                           ← Non-negotiable architecture rules (fill in your own)
├── METHODOLOGY.md                     ← Full methodology reference
│
├── PROMPTS/
│   ├── 00-agent-onboarding.md         ← First prompt every agent reads on any project
│   ├── 01-mentor.md                   ← MENTOR mode prompt
│   ├── 02-plan.md                     ← PLAN mode prompt
│   ├── 03-architect.md                ← BUILD/ARCHITECT mode prompt
│   ├── 04-code.md                     ← CODE mode prompt
│   ├── 05-qa.md                       ← QA/TEST mode prompt
│   ├── 06-audit.md                    ← AUDIT mode prompt (all audit types)
│   └── 07-session-preflight.md        ← Pre-flight checklist prompt
│
├── LIVING-DOCS/
│   ├── 01-architecture-template.md
│   ├── 02-database-template.md
│   ├── 03-api-template.md
│   ├── 04-components-template.md
│   ├── 05-features-template.md
│   ├── ADR-template.md                ← Architecture Decision Record template
│   └── CHANGE-LOG-template.md
│
└── AUDIT-TEMPLATES/
    ├── radical-simplification.md
    ├── security-audit.md
    ├── sql-audit.md
    └── standards-audit.md
```

---

## How to Use This Kit

### Starting a new project

1. Copy this entire folder into your project root (or fork the repo)
2. Fill in `RULES.md` with your project's non-negotiables
3. Fill in `PROMPTS/00-agent-onboarding.md` with your stack and project context
4. Set up your staging and production environments (see METHODOLOGY.md)
5. Start every session with the pre-flight checklist in `PROMPTS/07-session-preflight.md`

### Using the prompts

Each prompt file in `/PROMPTS` is designed to be pasted directly into your AI agent (Claude, ChatGPT, V0.dev, Cursor, etc.) at the start of the relevant phase. They are intentionally structured so you fill in the `[BRACKETED]` sections with project-specific context.

### Maintaining living docs

The `/LIVING-DOCS` templates are meant to be filled in as your project grows and regenerated (or updated) at key milestones. Update them at minimum:
- After every schema migration
- After every new API route
- After every promoted branch
- Before starting any major new feature

---

## Recommended Stack (what this was built on)

This methodology was developed and refined using:

- **AI Agents:** Claude (orchestration + prompts), V0.dev (implementation), Grok (team simulation)
- **Frontend:** Next.js App Router, TypeScript, Tailwind, shadcn/ui
- **Backend:** Supabase (DB + auth), Vercel (deployment + functions)
- **Storage:** Vercel Blob
- **Local dev:** Dyad.sh

The methodology works with any stack. The prompts are tool-agnostic.

---

## Contributing

This is a living methodology. If you use it on your own projects and discover improvements, open a PR. Every lesson learned in production is worth sharing.

**Found a better prompt? Submit it.** Found a gap in the audit templates? Fill it. Built something with this kit? Tag it `#AgenticEngineering` and share it.

---

## Credits

Developed across multiple production projects with heavy inspiration from:
- **Andrej Karpathy** for coining "vibe coding" and the intent-first philosophy
- **Pieter Levels** for the constraints-breed-creativity mindset
- **Theo (t3.gg)** for the ship-fast, staging-as-safety-net approach
- **Harper Reed** for the brilliant-but-careless-junior mental model
- The broader vibe coding community for sharing war stories publicly

---

*Agentic Engineering is not a product. It is a methodology. Use it, improve it, share it.*
