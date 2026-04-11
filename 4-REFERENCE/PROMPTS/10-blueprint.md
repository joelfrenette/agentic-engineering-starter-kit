# Prompt 10 — PRODUCT BLUEPRINT
**Use this:** After Vision & Goals is approved. Before technical architecture. Before any code.

> "Agents that know the full map make far fewer architectural mistakes than agents discovering the map as they go."

---

## PASTE THIS INTO YOUR AI AGENT:

---

You are in **BLUEPRINT mode**, acting as a Product Architect.

Your job is to translate the approved Vision & Goals document into a complete Product Blueprint -- a written map of every screen, every user journey, and every data flow in the product. This becomes the reference document that prevents scope creep, guides architecture decisions, and ensures every agent is building toward the same product.

**Read first:**
- `VISION.md` -- [paste contents]
- `RULES.md` -- [paste contents]

Do not write any code. Do not make architecture decisions yet. This phase is mapping only.

---

### Part 1: Screen & Route Map

List every screen/page/route in the product. For each:
- Route path (e.g., `/dashboard`, `/settings/profile`)
- Screen name
- Who can access it (public / authenticated user / admin)
- One-sentence description of what the user does here
- What data is displayed or collected

Format as a table. Be exhaustive -- if a screen exists in the product, it appears here. If it's not in this map, it doesn't get built.

---

### Part 2: User Journeys

Map the 3-5 most important user journeys. For each journey:
- Journey name (e.g., "New user signs up and completes first action")
- User type
- Step-by-step flow (screen by screen)
- What data is created or changed at each step
- What could go wrong at each step (error states)

These journeys become the backbone of your Phase 1 walking skeleton and your UAT test cases.

---

### Part 3: Feature Map by Phase

For each phase defined in VISION.md, list every feature that belongs to that phase. For each feature:
- Feature name
- One-sentence description
- Which screens it affects
- Which user journeys it enables
- Complexity estimate (S/M/L)
- Dependencies (what must exist before this can be built)

This map is the authoritative source of what gets built and when. If a feature isn't in this map, it goes to the backlog -- it does not get built during active development without an explicit decision to add it.

---

### Part 4: Data Map

For each major entity in the product, describe:
- Entity name (e.g., User, Project, Message)
- What it represents
- Key attributes (not the full schema -- that comes in architecture)
- Relationships to other entities
- Who creates it, who reads it, who can modify or delete it

This feeds directly into the database architecture phase.

---

### Part 5: Integration Map

For each external service or API the product depends on:
- Service name
- What it's used for
- Which phase it's needed in
- What happens if it's unavailable (graceful degradation plan)
- Any known rate limits, costs, or constraints

---

### Part 6: The Walking Skeleton Definition

Based on the above, define the walking skeleton precisely:

The walking skeleton is the THINNEST possible end-to-end slice that:
1. Touches every layer of the stack (auth, DB, frontend, API)
2. Proves the core user journey works
3. Can be demonstrated to a real user
4. Is production-deployable (not a prototype)

Name the exact screens, routes, and data entities that make up the walking skeleton. Everything else is Phase 2+.

---

### Part 7: The Explicit Backlog

List everything that came up during this exercise that is NOT in scope for the planned phases. This is the backlog. It exists so good ideas don't get lost AND so scope creep has a designated destination.

---

### Output

Produce a `BLUEPRINT.md` document with all seven sections. This document:
- Gets saved to the project root
- Gets added to the agent onboarding prompt (alongside VISION.md and RULES.md)
- Gets updated whenever scope decisions are made
- Is the single source of truth for "what are we building"

Wait for my review and approval of the blueprint before any architecture or coding begins.

---

*Part of the Agentic Engineering methodology. The blueprint is the map. Code without a map is just wandering.*
