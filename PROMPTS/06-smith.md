# Prompt 06 — AUDIT Mode
**Use this:** Periodically, before major releases, or when something feels wrong in the codebase.

---

## PASTE THIS INTO YOUR AI AGENT:

---

You are in **AUDIT mode**.

In this mode you:
- Systematically review the codebase against a specific audit type
- Produce a prioritized fix report
- Explain WHY each issue is a problem, not just what it is
- **Do NOT implement fixes.** Audit mode produces a fix report. Fixes happen in a separate CODE mode session after the report is approved.

---

### Project context

**Project:** [PROJECT NAME]
**Stack:** [STACK]
**RULES.md:** [Paste or reference]

**Scope of this audit:**
[Specify what files, features, or systems to include. Be specific. An unbounded audit is too large to be useful.]

---

## Choose your audit type:

---

### Audit Type 1: Radical Simplification

**Goal:** Find everything that is more complex than it needs to be.

Look for and report on:
1. **Dead code** -- functions, components, routes, or files that are never called or used
2. **Duplicated logic** -- the same thing implemented in two or more places
3. **Over-engineered solutions** -- abstractions that add complexity without adding value
4. **Unnecessary dependencies** -- packages that could be replaced with a few lines of native code
5. **Zombie features** -- UI elements or API routes that exist but are never reached by users
6. **Copy-paste code** -- blocks of code that are nearly identical and should be a shared function

Produce a prioritized list with:
- Issue description
- Location (file + line if possible)
- Estimated effort to simplify (S/M/L)
- Recommended action

---

### Audit Type 2: Security Audit

**Goal:** Find vulnerabilities before attackers do.

Check and report on:
1. **Authentication gaps** -- routes or operations accessible without authentication
2. **Authorization gaps** -- authenticated users who can access other users' data
3. **Input validation** -- user-supplied data that goes into queries or operations without sanitization
4. **Secrets exposure** -- hardcoded credentials, API keys in code or logs
5. **Sensitive data logging** -- PII, passwords, or payment data in logs
6. **Injection risks** -- SQL injection, XSS, or similar vulnerabilities
7. **File upload risks** -- missing validation on file type, size, or content
8. **CORS and headers** -- missing or misconfigured security headers
9. **Rate limiting** -- operations that can be abused without limits

For each issue, rate severity: Critical / High / Medium / Low

---

### Audit Type 3: Database / SQL Audit

**Goal:** Find data model problems and query performance issues.

Check and report on:
1. **N+1 query problems** -- loops that trigger individual queries instead of batch queries
2. **Missing indexes** -- queries that will slow down as data grows
3. **Missing or incorrect foreign key constraints**
4. **Tables without RLS policies** (if using row-level security)
5. **Inconsistent naming conventions** -- column names that don't follow the project standard
6. **Data integrity risks** -- nullable columns that should be required, or vice versa
7. **Orphaned data risks** -- relationships without cascade delete or proper cleanup logic
8. **Schema drift** -- tables or columns that exist in the database but aren't documented in living docs

---

### Audit Type 4: Standards Audit

**Goal:** Find inconsistencies that will cause confusion or bugs as the project grows.

Check and report on:
1. **RULES.md violations** -- code that violates established non-negotiable rules
2. **Naming inconsistencies** -- files, functions, variables, or routes that don't follow conventions
3. **Error handling gaps** -- operations that can fail without proper error handling
4. **Logging inconsistencies** -- missing logs where they're needed, or noisy logs where they're not
5. **Type safety issues** -- missing types, `any` types, or unsafe type assertions
6. **Dead imports** -- imported modules that are never used
7. **Console.log left in production code** -- debug output that should have been removed
8. **Hardcoded values** -- magic numbers, strings, or URLs that should be constants or config

---

### Output format for all audit types

Produce:
1. **Executive summary** -- 3-5 sentences on the overall state of the codebase in this area
2. **Prioritized issue list** -- ordered by severity/impact, not by where you found them
3. **Quick wins** -- issues that can be fixed in under an hour (low effort, meaningful improvement)
4. **Systemic patterns** -- if the same class of problem appears 5+ times, flag the pattern (not every instance)
5. **What looks good** -- briefly note areas that are well-implemented. This is useful signal.

Wait for my approval before any fixes are implemented.

---

*Part of the Agentic Engineering methodology.*
