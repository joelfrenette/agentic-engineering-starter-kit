# Prompt 12 — Audit Cycles & The 8S Compliance Calendar
**Use this:** As your recurring maintenance schedule. Audit cycles are not optional -- they are the immune system of the codebase.

---

## The 8S Standard

Every branch promoted to production should move the codebase closer to full 8S compliance. Use this as your quality benchmark.

| Standard | What it means | Primary audit |
|----------|--------------|---------------|
| **Swift** | Ships fast; no analysis paralysis; lean process | Retrospective |
| **Simple** | Minimum complexity; no dead code; no duplication | Radical Simplification |
| **Stable** | No regressions; tested before promoted; UAT passing | QA + UAT Runner |
| **Secure** | Auth on every route; RLS enforced; no secrets exposed | Security Audit |
| **Scalable** | No N+1 queries; indexes in place; no hardcoded limits | SQL Audit |
| **SaaS-Ready** | Credits/billing correct; multi-tenant safe; onboarding works | Standards Audit |
| **Sellable** | Core user journey works end-to-end; value is demonstrable | UAT + Vision review |
| **Supportable** | Docs current; RULES.md maintained; code is readable | Standards + Docs Audit |

**8S Score:** After any audit, rate each standard 1-5. Track the score over time. The goal is not perfection -- it is consistent improvement.

---

## The Audit Cycle Calendar

These are the default recommended cycles. Adjust based on your project's pace and risk profile.

### Every branch (always)
- [ ] Pre-flight checklist complete
- [ ] RULES.md violations: none
- [ ] No console.log in production code
- [ ] No hardcoded secrets
- [ ] Staging passing before UAT
- [ ] UAT Runner automated checks passing
- [ ] Living docs updated
- [ ] Checkpoint tag created if phase complete

### Every 3 branches: Security Audit
```
Trigger: After every 3rd promoted branch
Prompt: PROMPTS/06-audit.md → Audit Type 2: Security
Scope: All new routes and auth-adjacent code from the last 3 branches
Time estimate: 30-60 minutes
Tag after clean: checkpoint/post-security-audit-[N]
```

Focus areas for this cycle:
- Any new API routes -- auth middleware present?
- Any new database tables -- RLS policies in place?
- Any new user inputs -- validation and sanitization?
- Any new environment variables -- server-side only?
- Any new integrations -- webhook validation?

### Every 6 branches: Radical Simplification Audit
```
Trigger: After every 6th promoted branch
Prompt: PROMPTS/06-audit.md → Audit Type 1: Radical Simplification
Scope: Full codebase or the heaviest areas of recent growth
Time estimate: 1-2 hours for audit + separate branch for fixes
Tag after clean: checkpoint/post-simplification-[N]
```

This is the audit that keeps the codebase from becoming unmaintainable. The longer you wait, the more expensive it gets. 6 branches is roughly monthly for an active project -- do not stretch it to 10.

Focus areas:
- Dead code accumulated from the last 6 branches
- Duplicated logic from parallel development
- Over-engineered abstractions from exploratory work
- Dependencies that crept in without review

### Every 10 branches (or quarterly): Full Standards Audit
```
Trigger: Every 10th promoted branch OR once per quarter
Prompt: PROMPTS/06-audit.md → Audit Type 4: Standards
Scope: Full codebase
Time estimate: 2-3 hours for audit + 1-2 branches for fixes
Tag after clean: checkpoint/post-standards-audit-[N]
```

The deep clean. Reviews all conventions, naming, error handling, type safety, and documentation currency against RULES.md.

### Every schema migration: SQL Audit (targeted)
```
Trigger: Any time a database migration is applied
Prompt: PROMPTS/06-audit.md → Audit Type 3: SQL (targeted to changed tables)
Scope: Tables and queries affected by the migration
Time estimate: 20-30 minutes
```

Catches N+1 problems and missing indexes before they hit production at scale. Much cheaper to fix before the table has real data in it.

### Before any major version or launch: Full 8S Audit
```
Trigger: Before v1.0, before a major public launch, before fundraising demo
Run ALL four audit types sequentially
Fix all Critical and High findings before launch
Document 8S scores
Tag: checkpoint/pre-launch-[version]-8s-audit-clean
```

---

## Tracking the Audit Calendar

Add this to CHANGE-LOG.md after every promoted branch:

```markdown
## [DATE] -- Branch [N]: [Branch Name]

Cumulative branch count: [N]
Audits due this cycle:
- [x] Every-branch checklist: PASS
- [ ] Security audit (due every 3): [due at branch N+X / completed]
- [ ] Simplification audit (due every 6): [due at branch N+X / completed]
- [ ] Standards audit (due every 10): [due at branch N+X / completed]

8S Score (update after audits):
Swift: [1-5] | Simple: [1-5] | Stable: [1-5] | Secure: [1-5]
Scalable: [1-5] | SaaS-Ready: [1-5] | Sellable: [1-5] | Supportable: [1-5]
```

---

## Running an Audit Branch

Audits always happen on their own branch. Never audit AND fix on a feature branch.

```bash
# 1. Create a dedicated audit branch
git checkout -b audit/security-pass-3

# 2. Create a checkpoint BEFORE making any fixes
git tag -a checkpoint/pre-security-fixes-3 -m "Pre security audit fix pass 3"

# 3. Run the audit prompt -- get the report first, no fixes yet
# [paste audit prompt, get report, review it]

# 4. Approve the fix list

# 5. Implement fixes on this branch (CODE mode)

# 6. QA + UAT the fixes

# 7. Promote to main via PR

# 8. Tag the clean state
git tag -a checkpoint/post-security-audit-3 -m "Security audit 3 complete -- all findings resolved"
git push origin checkpoint/post-security-audit-3
```

---

## The Audit Log

Keep a running audit log in `LIVING-DOCS/AUDIT-LOG.md`:

```markdown
# Audit Log

## [DATE] -- Security Audit #1
Branch count at time: 3
Findings: [N] Critical, [N] High, [N] Medium, [N] Low
All Critical/High resolved: Yes / No
Checkpoint after: checkpoint/post-security-audit-1
8S Secure score before: [N] → after: [N]

## [DATE] -- Simplification Audit #1
Branch count at time: 6
Dead code removed: [N] files, [N] functions
Duplications consolidated: [N]
Lines of code before: [N] → after: [N]
Checkpoint after: checkpoint/post-simplification-1
8S Simple score before: [N] → after: [N]
```

---

## The 8S Pre-Launch Checklist

Before any public launch, all 8 standards must be explicitly reviewed:

```
[ ] SWIFT     -- Does the development process feel fast? Are releases taking less time than 3 months ago?
[ ] SIMPLE    -- Has a Radical Simplification audit been run in the last 6 branches?
[ ] STABLE    -- Is the UAT Runner passing all phases? Zero known regressions?
[ ] SECURE    -- Has a Security audit been run and all Critical/High findings resolved?
[ ] SCALABLE  -- Has a SQL audit been run? Are indexes in place on all high-traffic tables?
[ ] SAAS-READY -- Does billing/credits work correctly? Can a new user onboard without help?
[ ] SELLABLE  -- Can a new user complete the core value journey in under 5 minutes?
[ ] SUPPORTABLE -- Are living docs current? Is RULES.md maintained? Could someone else maintain this?
```

All 8 checked = launch-ready.

---

*Part of the Agentic Engineering methodology. Audits are not optional maintenance. They are the immune system of the codebase. Skip them and the codebase gets sick.*
