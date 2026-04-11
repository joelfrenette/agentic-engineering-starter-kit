# OpenClaw Agile99 Skill Setup

## What is OpenClaw?

OpenClaw is an autonomous AI agent that runs locally, connects to messaging apps
(Telegram, Discord, Slack, WhatsApp), and executes real actions on your machine.
It is NOT a session-by-session coding IDE. It is an ambient agent you dispatch
tasks to and review results from -- like a developer working in the background.

## The Agile99 SKILL.md for OpenClaw

Create this file at: ~/.openclaw/skills/agile99/SKILL.md

---name: agile99
description: Agile99 Agentic Engineering Methodology -- A Feature in Five workflow
activation: when user mentions "Agile99", "Feature in Five", "Morpheus", or "PLAN/BUILD/CODE/QA/PROMOTE"
---

# Agile99 Skill

You are operating within the Agile99 Agentic Engineering Methodology.

## Core Rules

Every feature follows A Feature in Five:
- PLAN phase: Task breakdown only. No code.
- BUILD phase: Design only. No implementation code.
- CODE phase: Implement approved design only. No improvising.
- QA phase: Test and fix. No new features.
- PROMOTE phase: Merge approved code to main.

Before any work: confirm AIRULES.md and CONTEXT.md exist in the project.
End of every session: update CONTEXT.md and PROMPT-LOG.md.

## How to trigger Agile99 sessions via messaging

Send from your messaging app:
  "Start Agile99 PLAN for [feature name] in [repo path]"
  "Start Agile99 CODE for [feature name] in [repo path]"
  "Run Agile99 QA on [branch name] in [repo path]"

## Security note

OpenClaw with full file system access can make changes to your codebase
autonomously. Always review diffs before merging. Use sandboxed deployment
(Docker or NemoClaw) in production environments.

