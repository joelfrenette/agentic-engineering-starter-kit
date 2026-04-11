```
╔═══════════════════════════════════════════════════════════════════════════════════╗
║                                                                                   ║
║          █████╗  ██████╗ ██╗██╗     ███████╗     ██████╗  ██████╗               ║
║         ██╔══██╗██╔════╝ ██║██║     ██╔════╝    ██╔═══██╗██╔═══██╗              ║
║         ███████║██║  ███╗██║██║     █████╗      ╚████████║╚████████║             ║
║         ██╔══██║██║   ██║██║██║     ██╔══╝       ╚═══╝███║ ╚═══╝███║            ║
║         ██║  ██║╚██████╔╝██║███████╗███████╗     ██████╔╝ ██████╔╝              ║
║         ╚═╝  ╚═╝ ╚═════╝ ╚═╝╚══════╝╚══════╝     ╚═════╝  ╚═════╝              ║
║                                                                                   ║
║              AGENTIC ENGINEERING METHODOLOGY  //  agile99.com                    ║
║              github.com/joelfrenette/agile99-starter-kit                         ║
╚═══════════════════════════════════════════════════════════════════════════════════╝
```

> *"Wake up, Neo... The Matrix has you."*
> — Morpheus, every session start

---

## What is Agile99?

**Vibe coding got us excited. Agile99 gets things shipped.**

Agile99 is a lightweight agentic engineering methodology that brings just enough structure to vibe coding to make it production-worthy — without killing the speed or creativity that makes it fun.

Three files in your repo. One paste to activate. Morpheus leads every session. The system improves itself automatically. Works with V0, Dyad, Windsurf, Cursor, Claude Code, Antigravity, and more.

---

## The Philosophical Shift (Why This Is Different)

### The old way — error prone

```
You → external AI → export docs → upload → coding tool → code
  → bug → describe bug → get advice → paste → fix
  → update docs manually → repeat
```

Every handoff across tool boundaries was a failure point. Docs went stale. Context got lost between sessions.

### The new way — self-contained

```
Tool reads AI_RULES.md + CONTEXT.md → codes
  → end of chat → tool updates all three files
  → next chat reads improved files → codes better
  → compounds forever. Automatically.
```

**The loop never leaves your tool + GitHub.** No export. No upload. No external AI for day-to-day work. The files ARE the agent's memory. The files improve themselves.

---

## The Three Files That Power Everything

```
┌─────────────────────────────────────────────────────────────────┐
│  AI_RULES.md        ←  The rules engine                        │
│                         Every painful bug becomes a rule.        │
│                         Grows and improves every session.        │
│                         After 50 chats: your project's law.     │
│                                                                  │
│  CONTEXT.md         ←  The living project brain                 │
│                         AI reads it first every chat.            │
│                         Updated automatically at session end.    │
│                         Zero manual doc maintenance.             │
│                                                                  │
│  PROMPT-LOG.md      ←  The self-improving prompt library        │
│                         Captures what worked and what failed.    │
│                         Prompts get sharper automatically.       │
│                         After 10 sessions: better than any       │
│                         generic guide.                           │
└─────────────────────────────────────────────────────────────────┘
```

The compounding effect:

```
Session 1   → Generic rules. Some mistakes.
Session 10  → Project-specific. Mistakes drop significantly.
Session 30  → Finely tuned. System knows your patterns.
Session 50  → Agent knows your codebase better than you do.
Session 100 → Errors that used to take hours rarely happen.
```

---

## Morpheus Mode — The Novel Piece

**Standard AI:** You tell it what to do. It does it. Sometimes the wrong thing.

**Morpheus Mode (Guided Intake Prompting):** The AI leads every session. You answer. The right crew member activates.

```
┌─────────────────────────────────────────────────────────────────┐
│  AI_RULES.md OK | CONTEXT.md OK                                 │
│                                                                  │
│  Wake up, Neo...                                                 │
│                                                                  │
│  What brings you here today?                                     │
│                                                                  │
│  1. 🔮 PLAN something new                                       │
│  2. 🏗️  DESIGN a feature                                        │
│  3. 💻 CODE something                                           │
│  4. ⚡ TEST & fix bugs                                          │
│  5. 🚚 SHIP to production                                       │
│  6. 🕴️  AUDIT the codebase                                      │
│  7. 🕶️  MENTOR me                                               │
│                                                                  │
│  Type a number, or describe what's on your mind.                │
└─────────────────────────────────────────────────────────────────┘
```

Every idea is captured as a structured use case before work begins:

```
USE CASE #[N]
════════════════════════════════════
As a:     [specific user type]
I want:   [action they want to take]
So that:  [outcome or benefit]
Priority: High / Medium / Low
════════════════════════════════════
```

This is **Socratic AI** — the agent asks, you answer, context is captured, work begins. No more half-baked prompts. No more building the wrong thing.

---

## The Matrix Crew — Agent Personas

One branch = one phase = one character. Personas prevent mode drift — the most common AI coding failure mode.

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  Character              Mode      Does                    Does NOT           │
│  ─────────────────────────────────────────────────────────────────────────  │
│  🕶️  Morpheus the Mentor  MENTOR   Explain, advise, guide  Write code         │
│  🔮  Oracle the Organizer PLAN     Task breakdowns, plans  Write code         │
│  🏗️   The Architect        BUILD    Schema, API, design     Write code         │
│  💻  Cypher the Coder     CODE     Implement approved plan  Improvise         │
│  ⚡  Trinity the Tester   TEST     Find bugs, diagnose      Fix w/o approval  │
│  🕴️   Smith the Scrutinizer AUDIT   Find violations, report Implement fixes   │
│  🚚  Tank the Transporter PROMOTE  Merge, deploy, tag       Skip steps        │
│  ⭐  You (The One)        UAT      Test as real user        Trust blindly     │
└──────────────────────────────────────────────────────────────────────────────┘
```

> *Legal notice: Character names reference The Matrix franchise, IP of Warner Bros. and the Wachowskis. Agile99 is not affiliated with Warner Bros. Used as educational role labels only.*

---

## A Feature in Five — The Core Workflow

```
┌────────────────────────────────────────────────────────────────────┐
│  Every feature = 5 chats = 5 GitHub branches = 1 shipped feature  │
│                                                                    │
│  Chat 1  │ 🔮 Oracle the Organizer  │ PLAN    │ max 20 prompts   │
│  Chat 2  │ 🏗️  The Architect         │ BUILD   │ max 30 prompts   │
│  Chat 3  │ 💻 Cypher the Coder      │ CODE    │ max 40 prompts   │
│  Chat 4  │ ⚡ Trinity the Tester    │ QA+FIX  │ max 40 prompts   │
│  Chat 5  │ 🚚 Tank the Transporter  │ PROMOTE │ max 20 prompts   │
│  UAT     │ ⭐ You (The One)         │ UAT     │ approve/reject   │
└────────────────────────────────────────────────────────────────────┘
```

Branch naming:
```
feat/[name]-plan     feat/[name]-build    feat/[name]-code
fix/[name]-qa        merge to main → ships to production
```

---

## The 10 Commandments

```
01  A Feature in Five      5 chats. 5 branches. 1 shipped feature. Always.
02  Prompt 21 is Done      Max 20 prompts. Hit 21? Close. Open new chat.
03  New Branch. New Name.  One branch = one phase = one character.
04  Read Before You Write  AI_RULES.md + CONTEXT.md confirmed first.
05  Plan Before You Build  No code without an approved plan.
06  One Thing. One Prompt. "And also..." is a second prompt.
07  Show Don't Describe    Screenshot + console + log. Not prose.
08  Main is Sacred         PRs only. Branch protection. Non-negotiable.
09  Close the Chat         End of Chat Protocol before closing anything.
10  Wake Up, Neo           UAT is yours. No agent replaces it.
```

---

## Supported Tools

```
┌──────────────────────────────────────────────────────────────────┐
│  Tool           Rules File                    Auto-loads?        │
│  ────────────────────────────────────────────────────────────   │
│  V0.app         AI_RULES.md (via GitHub)      Via repo           │
│  Dyad.sh        AI_RULES.md                   ✓ Native           │
│  Windsurf       .windsurfrules                ✓ Native           │
│  VS Code        .github/copilot-instructions  ✓ Native           │
│  Cursor         .cursor/rules/agile99.mdc     ✓ alwaysApply      │
│  Claude Code    CLAUDE.md                     ✓ Native           │
│  Antigravity    GEMINI.md + AGENTS.md         ✓ Native           │
│  Roo Code       .clinerules                   ✓ Native           │
│  OpenClaw       SKILL.md (agent skills)       Via skills folder  │
└──────────────────────────────────────────────────────────────────┘
```

---

## The Starter Kit — 4 Folders in the Right Order

```
agile99-kit/
├── README.txt
│
├── 1-START-HERE/
│   └── START-HERE.html          ← Open in browser. 24-step checklist.
│
├── 2-COPY-TO-PROJECT/           ← Pick the file for your tool
│   ├── AI_RULES.md              ← V0, Dyad
│   ├── CONTEXT.md               ← ALL tools
│   ├── PROMPT-LOG.md            ← ALL tools
│   ├── CLAUDE.md                ← Claude Code
│   ├── GEMINI.md                ← Antigravity (primary)
│   ├── AGENTS.md                ← Antigravity + cross-tool
│   ├── .windsurfrules           ← Windsurf
│   ├── .clinerules              ← Roo Code / Cline
│   ├── .github/
│   │   └── copilot-instructions.md  ← VS Code
│   └── .cursor/
│       └── rules/agile99.mdc    ← Cursor
│
├── 3-PASTE-INTO-V0-CHAT/
│   └── MORPHEUS-SYSTEM-PROMPT.md  ← Paste as first message. Starts the loop.
│
└── 4-REFERENCE/
    ├── METHODOLOGY.md
    ├── THE-RULES.md             ← Print and pin
    ├── QUICK-REF.md
    ├── PROMPTS/                 ← All 8 persona prompts
    ├── LIVING-DOCS/             ← Document templates
    └── AUDIT-TEMPLATES/         ← Security, SQL, simplification audits
```

---

## The 8S Standard

Every feature should move the codebase closer to all eight:

**Swift · Simple · Stable · Secure · Scalable · SaaS-Ready · Sellable · Supportable**

Audit cycles:
```
Every 3 features  (15 branches) → Security audit
Every 6 features  (30 branches) → Radical Simplification audit
Every 10 features (50 branches) → Full Standards audit
Every DB migration               → SQL audit
```

---

## License & Legal

Open source. MIT License. Fork it. Use it. Improve it.
Tag your projects **#Agile99** when you ship something with it.

> *Character names (Morpheus, Oracle, The Architect, Cypher, Trinity, Agent Smith, Tank, Neo) reference The Matrix franchise, IP of Warner Bros. Entertainment Inc. and the Wachowskis. Agile99 is not affiliated with or endorsed by Warner Bros. All Matrix trademarks remain property of their respective owners. Used as educational role labels only.*

---

**agile99.com · github.com/joelfrenette/agile99-starter-kit**
