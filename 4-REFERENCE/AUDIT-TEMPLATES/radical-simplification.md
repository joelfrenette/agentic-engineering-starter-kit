# Radical Simplification Audit
**Use this:** Quarterly, or before any major new feature build. Complexity is the enemy of velocity.

---

## PASTE THIS INTO YOUR AI AGENT:

---

You are in **AUDIT mode -- Radical Simplification**.

Your job is to find everything in this codebase that is more complex than it needs to be. You are NOT looking for bugs. You are looking for unnecessary complexity, duplication, and dead weight that slows down every future development session.

**Do NOT implement any fixes.** Produce a fix report only. Fixes are approved and implemented separately.

---

### Project context

**Project:** [PROJECT NAME]
**Stack:** [STACK]
**Audit scope:** [Specify which directories, features, or systems to include]
**Exclude from audit:** [Any areas explicitly out of scope]

**RULES.md:** [Paste or reference]

**Relevant living docs:** [Paste architecture and component docs]

---

### What to look for

#### 1. Dead code

Code that exists but is never called, rendered, or reached:
- Exported functions that are never imported anywhere
- Components that are never used in any route or parent component
- API routes that receive zero traffic (check logs if available)
- Database columns that are always null or never read
- Environment variables that are defined but never accessed
- Feature flags that are always true or always false

**For each dead code item, report:**
- Location (file + function/component name)
- How confident you are it's truly dead (High / Medium -- needs verification)
- Safe to delete? (Yes / Check first)

---

#### 2. Duplicated logic

The same functionality implemented in two or more places:
- Similar functions in different files that do the same thing
- Copy-pasted blocks of code with minor variations
- Multiple components that render nearly identical UI
- API routes with identical validation or processing logic
- Database queries written out fully in multiple places instead of shared

**For each duplication, report:**
- Location of each duplicate
- What's duplicated
- Recommended consolidation approach

---

#### 3. Over-engineered solutions

Abstractions or patterns that add complexity without adding proportional value:
- Generic utilities built for flexibility that are only ever used one way
- Config systems more complex than the config they manage
- Multi-layer abstractions where one layer would do
- Factories or registries for things that only have one implementation
- Async patterns where synchronous would work fine

**For each item, report:**
- Location
- What problem the over-engineering was solving
- Simpler alternative

---

#### 4. Unnecessary dependencies

Packages that could be removed or replaced:
- Packages used for one small utility function (that could be inlined in 5 lines)
- Packages with simpler native alternatives now available
- Packages duplicating functionality provided by an existing dependency
- Packages that are imported in package.json but not actually used

**For each dependency, report:**
- Package name
- How it's currently used
- Replacement approach (inline / different package / native API)
- Estimated lines of code to replace with

---

#### 5. Zombie features

UI and API that exists but is never reached:
- Navigation items that link to pages users never visit
- Settings that have no visible effect
- API routes with no frontend callers
- Form fields that are collected but never used

---

#### 6. Inconsistent patterns

The same kind of thing done multiple different ways:
- Error handling (sometimes try/catch, sometimes .catch(), sometimes nothing)
- API response shapes (inconsistent data structures across routes)
- Loading states (some components have them, some don't)
- Date formatting (multiple different approaches)

---

### Output format

**Executive summary** (3-5 sentences on the overall complexity health of the codebase)

**Quick wins** (can be fixed in under 30 minutes each -- list up to 10)

**High impact items** (would meaningfully reduce complexity -- list up to 5, with effort estimate)

**Systemic patterns** (classes of problems that appear repeatedly -- name the pattern, not every instance)

**Recommended priority order** (what to fix first and why)

**What looks good** (areas of the codebase that are notably clean -- useful signal)

Wait for my approval before any fixes are implemented.

---

*Part of the Agentic Engineering methodology.*
