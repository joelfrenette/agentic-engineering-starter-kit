# Architecture Overview
**Project:** [PROJECT NAME]
**Last updated:** [DATE]
**Updated by:** [Who or what updated this -- human or which agent]

---

## System Overview

[2-3 paragraphs describing what the system does, who uses it, and the core architecture decisions that shape everything else.]

---

## Tech Stack

| Layer | Technology | Version | Notes |
|-------|-----------|---------|-------|
| Frontend framework | | | |
| UI component library | | | |
| Styling | | | |
| Backend/API | | | |
| Database | | | |
| Authentication | | | |
| File storage | | | |
| Email (transactional) | | | |
| Email (bulk) | | | |
| Deployment | | | |
| AI/LLM | | | |

---

## Environment Architecture

| Environment | URL | Database | Branch |
|-------------|-----|----------|--------|
| Production | | | main |
| Staging | | | feature branches |
| Local dev | localhost | | any |

---

## Core Architecture Decisions

### Decision 1: [Name]
**Decision:** [What was decided]
**Rationale:** [Why this was chosen]
**Alternatives considered:** [What was rejected and why]
**Date:** [When this was decided]

### Decision 2: [Name]
[Same format]

*See /01-architecture/decisions/ for full ADR history.*

---

## Request Flow

[Describe how a typical request flows through the system. A simple numbered list or diagram description is fine.]

1. [Step 1]
2. [Step 2]
3. [Step 3]

---

## Authentication & Authorization

[Describe how auth works in this system:]

- **Auth provider:** [how users authenticate]
- **Session management:** [how sessions are stored and validated]
- **Authorization model:** [how permissions are structured]
- **Protected route pattern:** [the pattern used on all protected routes]

---

## Key Integrations

| Integration | Purpose | Status | Notes |
|-------------|---------|--------|-------|
| | | Active / Planned / Deprecated | |

---

## Infrastructure & DNS

[Document your hosting, DNS, and deployment setup:]

- **Domain:** [registrar, nameservers]
- **CDN/Edge:** [if applicable]
- **Deployment pipeline:** [how code gets from commit to production]
- **Environment variables:** [categories of vars, NOT the actual values]

---

## Non-Negotiable Architecture Rules

[Reference RULES.md -- don't duplicate, just point here]

See: RULES.md

---

## Known Technical Debt

| Item | Description | Priority | Created |
|------|-------------|----------|---------|
| | | High/Med/Low | [date] |

---

## Architecture Change Log

| Date | Change | Reason |
|------|--------|--------|
| | Initial architecture established | Project bootstrap |

---

*This document is maintained as part of the Agentic Engineering methodology. Update after every architectural change.*
