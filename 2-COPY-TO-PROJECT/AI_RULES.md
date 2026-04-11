# AI_RULES.md - Agile99 Project Rules
# READ THIS BEFORE DOING ANYTHING ELSE
# Version: 1.0 | Project: [YOUR APP NAME] | Updated: [DATE]

## Confirmation required (non-negotiable)
At the start of every chat output:
"AI_RULES.md OK | CONTEXT.md OK | Phase: [X] | Goal: [X]"
Do not write any code before this confirmation.

## Project
Name:   [YOUR APP NAME]
Stack:  [e.g. Next.js, Supabase, Vercel, Tailwind]
Repo:   github.com/[YOUR-HANDLE]/[YOUR-REPO]
Deploy: Vercel (preview = staging, main = production)

## A Feature in Five
Every feature = 5 chats = 5 GitHub branches:
Chat 1 PLAN    (max 20 prompts) -> feat/[name]-plan
Chat 2 BUILD   (max 30 prompts) -> feat/[name]-build
Chat 3 CODE    (max 40 prompts) -> feat/[name]-code
Chat 4 QA+FIX  (max 40 prompts) -> fix/[name]-qa
Chat 5 PROMOTE (max 20 prompts) -> merge to main

## The Simple Rules
- Prompt 21 is Done (max 20 prompts per chat)
- New Branch. New Name. (one phase = one chat = one persona)
- Read Before You Write (AI_RULES + CONTEXT confirmed first)
- Plan Before You Build (no code without approved plan)
- One Thing. One Prompt. ("and also" = second prompt)
- Main is Sacred (PRs only, branch protection on)
- Close the Chat, Not the Tab (end of chat protocol always)
- Wake Up, Neo (UAT is yours -- test as a real user)

## Non-negotiable coding rules
- All API routes must use withErrorHandler() wrapper
- All protected routes must use requireAuth() middleware
- Never write to database from client-side code
- Never hardcode secrets -- use environment variables only
- No console.log in production code
- Output only modified files -- never the full project
- State what you will NOT touch before coding anything
[ADD YOUR OWN RULES HERE AS YOU DISCOVER THEM]

## End of every chat (mandatory)
1. Output full updated CONTEXT.md
2. Note what worked/failed -> PROMPT-LOG.md
3. Propose new rules for AI_RULES.md if anything broke
4. State exact starting point for next chat

## Rule change log
[DATE] v1.0 - Initial rules created
