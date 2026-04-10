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
A FEATURE IN FIVE
─────────────────────────────────────────────────────────────
Chat 1  │ 🔮 Oracle the Organizer  │ PLAN    │ max 20 prompts
Chat 2  │ 🏗️ The Architect         │ BUILD   │ max 30 prompts
Chat 3  │ 💻 Cypher the Coder      │ CODE    │ max 40 prompts
Chat 4  │ ⚡ Trinity the Tester    │ QA+FIX  │ max 40 prompts
Chat 5  │ 🚚 Tank the Transporter  │ PROMOTE │ max 20 prompts
UAT     │ ⭐ You (The One)         │ UAT     │ approve/reject
─────────────────────────────────────────────────────────────

Each chat opens with:
  1. AIRULES.md + CONTEXT.md confirmation
  2. Character persona activation
  3. Phase-specific prompt

Each chat closes with:
  1. End of Chat Protocol
  2. V0 updates AIRULES.md + CONTEXT.md + PROMPT-LOG.md
  3. Commit all three files to GitHub
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
│   ├── 00-onboarding.md               ← First prompt every agent reads on any project
│   ├── 01-morpheus.md                 ← Morpheus the Mentor (MENTOR mode)
│   ├── 02-oracle.md                   ← Oracle the Organizer (PLAN mode)
│   ├── 03-architect.md                ← The Architect (BUILD mode)
│   ├── 04-cypher.md                   ← Cypher the Coder (CODE mode)
│   ├── 05-trinity.md                  ← Trinity the Tester (QA/TEST mode)
│   ├── 06-smith.md                    ← Smith the Scrutinizer (AUDIT mode)
│   ├── 07-preflight.md                ← Pre-flight checklist (start of every chat)
│   ├── 08-uat-runner.md               ← Admin UAT Runner build prompt
│   ├── 09-vision.md                   ← Vision & Goals (before any code)
│   ├── 10-blueprint.md                ← Product Blueprint (before any code)
│   ├── 11-checkpoints.md              ← Checkpoints & GitHub best practices
│   ├── 12-audit-cycles.md             ← Audit cycle calendar & 8S standard
│   └── 15-personas.md                 ← All Matrix crew persona prompts
│
├── LIVING-DOCS/
│   ├── 00-vision-template.md          ← Vision & Goals doc (fill before coding)
│   ├── 00b-blueprint-template.md      ← Product Blueprint doc (fill before coding)
│   ├── 01-architecture-template.md
│   ├── 02-database-template.md
│   ├── 03-api-template.md
│   ├── 04-components-template.md
│   ├── 05-features-template.md
│   ├── 06-uat-runner.md               ← UAT Runner documentation
│   ├── ADR-template.md                ← Architecture Decision Record template
│   ├── AUDIT-LOG.md                   ← 8S scores and audit history
│   ├── CHANGE-LOG-template.md
│   └── RETROSPECTIVE-template.md      ← Post-branch retro guide
│
└── AUDIT-TEMPLATES/
    ├── radical-simplification.md
    ├── security-audit.md
    ├── sql-audit.md
    └── standards-audit.md
```

---

## The Simple Rules

**A Feature in Five** -- 5 chats. 5 branches. 1 shipped feature. Every time.

**Prompt 21 is Done** -- Max 20 prompts per chat. Hit 21? Close, open fresh, paste opener.

**New Branch. New Name.** -- One branch = one phase = one character. Always.

**Read Before You Write** -- AIRULES.md + CONTEXT.md confirmed before any code.

**Plan Before You Build** -- The Architect does not build what Oracle has not approved.

**One Thing. One Prompt.** -- "And also..." is a second prompt. Send it separately.

**Show Don't Describe** -- Screenshot + console error + Vercel log. Never just describe a bug.

**Main is Sacred** -- PRs only. Branch protection is on. Non-negotiable.

**Close the Chat, Not the Tab** -- End of Chat Protocol before closing anything.

**Wake Up, Neo** -- UAT is yours. No agent replaces it. Test as a real user.

See `THE-RULES.md` for the full printable one-pager.

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
---

## Legal Notice

The character names used in this methodology (Morpheus, Oracle, The Architect, Cypher, Trinity, Agent Smith, Tank, Neo / "The One") are references to *The Matrix* film franchise, which is the intellectual property of Warner Bros. Entertainment Inc. and the Wachowskis.

**Agile99 and this starter kit are not affiliated with, endorsed by, or connected to Warner Bros. Entertainment Inc. in any way.** The Matrix character names are used here purely as memorable, educational labels for software development roles -- in the same spirit that developers reference fictional characters to name concepts, patterns, or tools.

No commercial claim is made over any Matrix intellectual property. All trademarks and copyrights related to *The Matrix* remain the exclusive property of their respective owners.

If you prefer to avoid any IP adjacency in a commercial or enterprise context, the character names can be replaced with the generic role names (MENTOR, PLAN, BUILD, CODE, QA, AUDIT, PROMOTE, UAT) at any time -- the methodology works identically either way.

---

