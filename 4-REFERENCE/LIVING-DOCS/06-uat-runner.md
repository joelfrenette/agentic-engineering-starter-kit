# UAT Runner Documentation
**Project:** [PROJECT NAME]
**Last updated:** [DATE]
**Runner location:** `/admin/uat`
**Current phases:** [N]

---

## What This Is

The UAT Runner is a QA testing system built directly into the app's admin dashboard. Instead of maintaining an external test checklist or relying on mental checklists during UAT, the app tests itself from the inside.

This is a core part of the Agentic Engineering methodology -- it closes the testing loop within the product itself.

**Why it lives in the admin dashboard:**
- Zero external tooling needed
- Any admin (technical or not) can run tests
- Tests are always current because they run against the live app
- Old phases accumulate as regression tests automatically
- Passes/fails are visible at a glance, not buried in a terminal

---

## Architecture

**Route:** `/admin/uat`
**Auth:** Admin only
**Config file:** `/lib/uat-config.ts`
**Check routes:** `/api/admin/uat/[check-name]/`

### Two types of checks

**Automated checks** -- the app calls its own API routes and reads its own database:
- Returns HTTP 200?
- Does this database row exist?
- Is this field populated?
- Does this token exist in the expected table?
- Does this config value resolve correctly?

**Manual steps** -- items that require human eyes:
- Does this UI element render correctly?
- Does this redirect complete correctly?
- Does this flow feel right to a real user?
- Does this visual output match the expected design?

### The hybrid model

The key design decision: automated checks validate **data and API state**; manual steps validate **UI and UX**. Never try to automate UI judgment -- it produces fragile tests and false confidence. Keep manual steps for what humans are actually better at.

---

## Phase Index

| Phase ID | Name | Branch | Shipped | Auto Checks | Manual Steps | Status |
|----------|------|--------|---------|-------------|--------------|--------|
| phase-0 | Bootstrap & Setup | main | [date] | [N] | [N] | |
| phase-1 | [Feature area] | [branch] | [date] | [N] | [N] | |

---

## Phase Documentation

### Phase 0: Bootstrap & Setup

**What was built:** Project bootstrap, environments, auth, database schema
**Branch:** main

**Automated checks:**
- Database connection health
- Environment variables present (all required vars exist)
- Auth flow responds

**Manual steps:**
- Staging environment loads without errors
- Login flow completes correctly
- Admin dashboard accessible

---

### Phase [N]: [Name]

**What was built:** [Brief description of features shipped]
**Branch:** [branch-name]
**Shipped:** [date]

**Automated checks:**
| Check ID | What it verifies | API route used |
|----------|-----------------|----------------|
| | | |

**Manual steps:**
| Step ID | What to check | How to verify |
|---------|--------------|---------------|
| | | |

**Known issues at time of shipping:**
- [Any known issues that were promoted with the phase]

---

## Adding a New Phase

After every major branch promotes to production:

1. Open `/lib/uat-config.ts`
2. Append a new `UATPhase` object (use the Phase template in PROMPTS/08-admin-uat-runner.md Part B)
3. Write automated checks for every API route or DB state change introduced in this phase
4. Write manual steps for every UI/UX element that needs verification
5. Write manual step instructions in plain English for a non-technical tester
6. Commit the updated config as part of the promotion process

**Rule:** Every promoted branch should produce at least 2 automated checks and 1 manual step. If you can't think of any checks, you haven't thought clearly about what you just built.

---

## Internal Check Routes

| Route | What it checks | Phase |
|-------|---------------|-------|
| `GET /api/admin/uat/health` | DB connection, env vars | All phases |
| `GET /api/admin/uat/check-[feature]` | [description] | Phase [N] |

All routes:
- Admin auth required
- Return `{ pass: boolean, detail: string }`
- Read-only -- never write or modify data

---

## Regression Testing

The UAT Runner keeps all phases permanently. When you click "Run All Phases," it runs every automated check from every phase -- not just the current one. This means:

- Phase 1 chat tests run every time
- Phase 2 credits tests run every time
- Any new phase that breaks an old feature gets caught immediately

This is your regression safety net. It costs nothing to maintain because the checks are already written.

---

## What the Runner Does NOT Do

- Does not create or modify test data
- Does not send emails or notifications
- Does not integrate with CI/CD (yet -- see Automation Targets)
- Does not replace Vercel logs or Supabase logs for debugging
- Does not use external testing frameworks (Jest, Playwright, Cypress)

---

## Automation Targets (Future)

When the project matures:

**CI/CD trigger:** Run automated checks automatically on every staging deploy. Flag the deploy as passing or failing before UAT begins.

**Slack/email notification:** When a regression is detected (passing phase now failing), alert the team automatically.

**Scheduled regression runs:** Run all phases on a nightly schedule to catch environment drift.

---

## UAT Runner Change Log

| Date | Change | Phase affected |
|------|--------|---------------|
| | UAT Runner created | All |

---

*Part of the Agentic Engineering methodology. The self-testing product is the testing loop baked INTO the app.*
