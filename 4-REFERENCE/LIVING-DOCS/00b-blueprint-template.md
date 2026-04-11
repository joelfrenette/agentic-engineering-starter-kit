# BLUEPRINT.md — Product Blueprint
**Project:** [PROJECT NAME]
**Date:** [DATE]
**Status:** Draft / Approved
**Depends on:** VISION.md (must be approved first)

> The complete map of what is being built. Every screen, every user journey, every data entity. If it's not in this document, it doesn't get built without an explicit scope decision.

---

## Screen & Route Map

| Route | Screen Name | Access | Description |
|-------|------------|--------|-------------|
| `/` | Landing / Home | Public | [What the user sees/does here] |
| `/auth/login` | Login | Public | |
| `/auth/signup` | Sign Up | Public | |
| `/dashboard` | Dashboard | Authenticated | |
| `/[feature]` | [Screen name] | [Access level] | |
| `/admin` | Admin Dashboard | Admin only | |
| `/admin/uat` | UAT Test Runner | Admin only | Phase-based QA runner |

---

## User Journeys

### Journey 1: [Name -- e.g., "New user signs up and completes first action"]

**User type:** [Who is doing this]
**Goal:** [What they're trying to accomplish]

| Step | Screen | User action | System response | Error state |
|------|--------|-------------|-----------------|-------------|
| 1 | Landing | Clicks sign up | Redirects to /auth/signup | |
| 2 | Sign Up | Fills form, submits | Creates account, sends verification | Invalid email format |
| 3 | | | | |

**This journey is the basis for:** UAT Phase [N] test cases

---

### Journey 2: [Name]

[Same format]

---

### Journey 3: [Name -- the core value delivery journey]

[Same format -- this is the most important one]

---

## Feature Map by Phase

### Phase 0: Foundation

| Feature | Description | Screens affected | Complexity | Dependencies |
|---------|-------------|-----------------|------------|--------------|
| Auth system | User signup, login, session | /auth/*, all protected routes | M | None |
| DB schema | Core tables deployed | All data-driven screens | M | None |
| Deploy pipeline | Staging + production CI/CD | N/A | S | None |
| UI shell | Nav, layout, basic routing | All screens | S | Auth |

---

### Phase 1: Walking Skeleton

| Feature | Description | Screens affected | Complexity | Dependencies |
|---------|-------------|-----------------|------------|--------------|
| [Core feature] | [The minimum that proves the product loop] | | | Phase 0 |

---

### Phase 2: [Name]

[Same format]

---

## Data Map

### [Entity: User]
**Represents:** An authenticated person using the product
**Key attributes:** id, email, name, role, created_at
**Relationships:** Has many [related entities]
**Created by:** Signup flow
**Read by:** All authenticated routes
**Modified by:** User settings
**Deleted by:** Account deletion flow

---

### [Entity: [Name]]
**Represents:** [Description]
**Key attributes:** [List]
**Relationships:** [Belongs to / has many]
**Created by:** [Which user action]
**Read by:** [Which routes/users]
**Modified by:** [Which actions]
**Deleted by:** [Which actions / cascade rules]

---

## Integration Map

| Service | Purpose | Phase needed | Unavailability plan | Constraints |
|---------|---------|-------------|---------------------|-------------|
| [Auth provider] | User authentication | Phase 0 | Block login with error message | Rate limits: [N] |
| [Database] | Data persistence | Phase 0 | Hard block, all features depend on it | Connection pool: [N] |
| [Email service] | Transactional email | Phase 1 | Queue and retry | [N] emails/day free tier |

---

## The Walking Skeleton

**Exactly this and nothing more:**

Screens included:
- [ ] [Route 1] -- [why it's in the skeleton]
- [ ] [Route 2]
- [ ] [Route 3]

Data entities included:
- [ ] [Entity 1]
- [ ] [Entity 2]

API routes included:
- [ ] [Route 1]

**The skeleton proves:**
1. [Architecture assumption validated]
2. [Product assumption validated]
3. [Technical risk mitigated]

**A user can demonstrate:** [Specific action that shows the skeleton is working]

---

## The Explicit Backlog

Ideas and features that came up during blueprinting but are NOT in scope for planned phases. They live here so they don't get lost and don't cause scope creep.

| Item | Description | Why deferred | Reconsider at |
|------|-------------|-------------|---------------|
| | | Not in Phase 1-3 | Phase 4 / never |

---

## Scope Change Log

Document any changes to this blueprint after approval:

| Date | Change | Reason | Approved by |
|------|--------|--------|-------------|
| | Initial blueprint | Project start | |

---

*Part of the Agentic Engineering methodology. The blueprint is the map. Code without a map is just wandering.*
