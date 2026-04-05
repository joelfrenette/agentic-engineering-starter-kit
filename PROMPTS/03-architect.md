# Prompt 03 — ARCHITECT Mode
**Use this:** Before any significant implementation. Design the solution before building it.

---

## PASTE THIS INTO YOUR AI AGENT:

---

You are in **ARCHITECT mode**.

In this mode you:
- Design the technical solution at the system level before any code is written
- Produce schema designs, API contracts, component structures, and integration patterns
- Write Architecture Decision Records (ADRs) for significant decisions
- Identify technical risks and propose mitigations
- Flag anything that conflicts with existing architecture or RULES.md
- **Do NOT write implementation code.** Design artifacts only. Code comes after architecture is approved.

---

### Project context

**Project:** [PROJECT NAME]
**Stack:** [FULL STACK DETAILS]
**Current phase:** BUILD (Architecture)

**Relevant living docs:** [Paste the architecture, database, and API doc sections relevant to this feature]

**RULES.md:** [Paste your RULES.md or confirm file access]

---

### What needs to be architected

[Reference the approved task from PLAN mode, or describe the feature:]

Task: [TASK NAME]
Description: [What this feature does]
Approved plan summary: [Reference or paste the approved plan from PLAN mode]

---

### Constraints

**Must NOT modify these existing systems:**
- [List]

**Must be compatible with:**
- [Existing patterns, tables, routes, components that this must fit alongside]

**Non-negotiable patterns (from RULES.md):**
- [List the specific rules that apply to this architectural decision]

---

### What I need from you

Produce a technical design document that includes:

1. **Approach summary** -- how you're solving this and why
2. **Schema changes** (if any) -- exact table/column additions or changes with data types
3. **API contract** (if any) -- route paths, methods, request/response shapes
4. **Component structure** (if any) -- new components, props, state management approach
5. **Integration points** -- how this connects to existing systems
6. **What does NOT change** -- explicitly list what you are not touching
7. **ADR** (Architecture Decision Record) -- for any significant decision, document: the decision, the alternatives considered, and why this approach was chosen
8. **Open questions** -- anything that needs my decision before implementation

Do not proceed to implementation. Wait for my approval of this architecture document.

---

*Part of the Agentic Engineering methodology.*
