# AI_RULES.md — Agile99 Project Rules
# READ THIS BEFORE DOING ANYTHING ELSE
# Version: 1.0 | Project: [YOUR APP NAME] | Updated: [DATE]
#
# This file lives in your project root.
# V0.app reads it automatically at the start of every chat.
# It grows and improves with every session.
# Never delete old rules -- add to them.

---

## Confirmation required (non-negotiable)

At the start of every V0 chat, before doing anything else, output:

"AI_RULES.md OK | CONTEXT.md OK | Phase: [X] | Goal: [X]"

Do not write a single line of code before this confirmation is output.
This is how the human knows the system was followed.
Every chat. No exceptions.

---

## Project

Name:   [YOUR APP NAME]
What:   [One sentence -- what this app does]
Who:    [One sentence -- who uses it]
Stack:  Next.js App Router, TypeScript, Tailwind CSS, shadcn/ui
DB:     Supabase (PostgreSQL + Row Level Security + Auth)
Deploy: Vercel (Preview branches = staging; main = production)
Repo:   github.com/[YOUR-HANDLE]/[YOUR-REPO]

---

## A Feature in Five

Every feature uses exactly 5 V0 chats = 5 GitHub branches:

| Chat | Phase   | Max Prompts | Branch name           |
|------|---------|-------------|----------------------|
| 1    | PLAN    | 20          | feat/[name]-plan     |
| 2    | BUILD   | 30          | feat/[name]-build    |
| 3    | CODE    | 40          | feat/[name]-code     |
| 4    | QA+FIX  | 40          | fix/[name]-qa        |
| 5    | PROMOTE | 20          | merge to main        |

When a chat approaches 40 prompts and work is not complete:
- Run the End of Chat Protocol
- Push the branch
- Open a new chat
- Paste the chat opener
- Continue from the exact starting point noted in CONTEXT.md

---

## Non-negotiable coding rules

- All API routes must use withErrorHandler() wrapper
- All protected routes must use requireAuth() middleware
- Never write directly to the database from client-side code
- Never hardcode secrets -- use environment variables only
- No console.log statements in production code
- Read CONTEXT.md before writing any code
- Output only files you modified -- never the full project
- State what you will NOT touch before writing any code
- One task per prompt -- never combine two changes in one prompt
- If a prompt is ambiguous, ask for clarification before coding

[ADD YOUR OWN RULES HERE AS YOU DISCOVER THEM]
[Every painful bug should produce a rule that prevents it next time]

---

## End of every chat (mandatory)

Before closing any V0 chat, always run this:

1. Output the full updated CONTEXT.md
2. Note any prompts that worked well or failed -> PROMPT-LOG.md
3. Propose any new rules for AI_RULES.md
4. State the exact first prompt for the next chat

The human copies each output and commits the updated files.

---

## The self-improving loop

This file gets smarter every session. Here is how:
- Every bug that wasn't prevented by a rule -> add a rule
- Every prompt that produced great results -> log it in PROMPT-LOG.md
- Every prompt that failed -> log the improved version in PROMPT-LOG.md
- Every session closes by updating CONTEXT.md with current state

After 20 sessions this file is specific to your project.
After 50 sessions it is irreplaceable.

---

## Rule change log

| Version | Date | Rule added | Reason |
|---------|------|-----------|--------|
| 1.0 | [DATE] | Initial rules | Project bootstrap |

[V0 proposes additions here at end of each chat]
[Human approves and commits]
