# Prompt 08 — Build the Admin UAT Runner
**Use this:** Once per project (Phase 0 or early Phase 1) to build the UAT Test Runner into your app's admin dashboard. Then use the UPDATE variant to add new test phases as features ship.

---

## PART A: BUILD THE UAT RUNNER (use once)

### PASTE THIS INTO YOUR AI AGENT:

---

You are in **ARCHITECT + CODE mode**.

We are building a **UAT Test Runner** into the admin dashboard of this app. This is a core part of our development workflow -- not a nice-to-have. It allows us to run structured QA from inside the app itself, without relying on a mental checklist.

Read RULES.md before proceeding: [paste or reference]

---

### What the UAT Runner is

A page in the admin dashboard (`/admin/uat` or `/admin/testing`) that:

1. **Displays test phases** -- one phase per major feature or branch milestone
2. **For each phase, runs two types of checks:**
   - **Automated checks** -- the app calls its own API routes and reads its own database to verify expected state (returns HTTP 200? does the row exist? is the field populated?)
   - **Manual steps** -- checklist items that require a human to verify (does the UI look right? did the redirect complete? does the button do the right thing?)
3. **Shows a pass/fail dashboard** -- clear green/red status per check, per phase, and overall
4. **Accumulates phases over time** -- old phases stay as regression tests; new phases get added as features ship
5. **Is only accessible to admins** -- protected by admin auth middleware

---

### Architecture requirements

**Route:** `/admin/uat` (or equivalent for your framework)
**Auth:** Admin only -- use `[your admin auth wrapper]`
**Database:** No new tables needed -- the runner reads existing tables to check state
**API calls:** The runner calls your own existing API routes as health checks
**No external testing libraries** -- this is vanilla fetch calls + database queries, not Jest or Playwright

---

### Data structure for test phases

The test phases should be defined in a config file (not hardcoded in the component) so new phases can be added without touching the runner UI:

```typescript
// /lib/uat-config.ts (or equivalent)

export type CheckResult = 'pass' | 'fail' | 'pending' | 'running' | 'manual';

export interface AutoCheck {
  id: string;
  label: string;          // Plain English: "Chat API returns 200"
  description: string;    // Plain English explanation of what this checks and why
  run: () => Promise<{ pass: boolean; detail?: string }>;
}

export interface ManualStep {
  id: string;
  label: string;          // Plain English: "Gmail connect button appears on integrations page"
  description: string;    // Step-by-step instructions for a non-technical tester
  hint?: string;          // Where to look, what to expect
}

export interface UATPhase {
  id: string;
  name: string;           // e.g. "Phase 1: Core Chat + Credits"
  description: string;    // What was built in this phase
  branch?: string;        // Git branch this phase was built on
  shippedDate?: string;
  autoChecks: AutoCheck[];
  manualSteps: ManualStep[];
}
```

---

### Example phase (adapt this pattern for your own stack)

```typescript
{
  id: 'phase-1-chat',
  name: 'Phase 1: Core Chat',
  description: 'Basic AI chat working with credit deduction',
  autoChecks: [
    {
      id: 'chat-api-health',
      label: 'Chat API responds',
      description: 'Calls /api/chat with a test message and checks for HTTP 200',
      run: async () => {
        try {
          const res = await fetch('/api/chat/health');
          return { pass: res.ok, detail: `Status: ${res.status}` };
        } catch (e) {
          return { pass: false, detail: String(e) };
        }
      }
    },
    {
      id: 'credits-table-exists',
      label: 'User credits row exists',
      description: 'Checks the database to confirm the current user has a credits row',
      run: async () => {
        const res = await fetch('/api/admin/uat/check-credits');
        const data = await res.json();
        return { pass: data.exists, detail: data.detail };
      }
    }
  ],
  manualSteps: [
    {
      id: 'chat-renders',
      label: 'Chat interface loads and is usable',
      description: 'Navigate to the main chat page. Type a message and press send.',
      hint: 'You should see a response stream in within 3 seconds. If it spins forever, the API is broken.'
    }
  ]
}
```

---

### The runner UI requirements

Build a clean admin page with:

1. **Phase list** (left sidebar or top tabs) -- each phase shows name + quick status (all pass / N failing / not run)
2. **Phase detail view** (main area) -- when a phase is selected:
   - Phase name, description, shipped date
   - "Run automated checks" button -- runs all AutoChecks in this phase sequentially, updates status in real time
   - Automated check results list -- each check shows: label, pass/fail/running indicator, detail message on failure
   - Manual steps checklist -- each step shows: label, description, "How to check" expandable instructions, checkbox to mark complete
3. **Overall status bar** -- at the top: total phases, total auto checks passed/failed, total manual steps completed
4. **Run all phases** button -- runs all automated checks across all phases (regression check)

---

### Internal API routes needed

Create these lightweight admin-only routes to support the automated checks:

- `GET /api/admin/uat/health` -- basic app health (DB connection, env vars present)
- Additional check routes as needed per phase (e.g., `GET /api/admin/uat/check-[feature]`)

All routes must use your admin auth wrapper. Return `{ pass: boolean, detail: string }`.

---

### What NOT to build

- No external testing frameworks (Jest, Playwright, Cypress) -- this is in-app only
- No CI/CD integration (yet) -- this is a manual trigger from the admin
- No test data creation -- checks read existing state, they don't write or modify data
- No email/notification on failure -- keep it simple, just visual pass/fail

---

### Output

1. Written architecture plan (confirm before coding)
2. `/lib/uat-config.ts` -- the phase config file with Phase 1 populated
3. `/app/admin/uat/page.tsx` (or equivalent) -- the runner UI
4. `/api/admin/uat/health/route.ts` -- the health check route
5. Any additional check routes needed for Phase 1

Wait for my approval of the architecture plan before writing any code.

---

## PART B: ADD A NEW PHASE (use after each major branch ships)

### PASTE THIS INTO YOUR AI AGENT:

---

You are in **CODE mode**.

We are adding a new UAT test phase to the Admin UAT Runner. This should be done after every major branch is promoted to production.

**New phase to add:** [PHASE NAME -- e.g., "Phase 4: Zoom Integration"]
**Branch this phase covers:** [BRANCH NAME]
**Features shipped in this phase:**
- [Feature 1]
- [Feature 2]

**Read the current UAT config:** [paste /lib/uat-config.ts contents]

**Rules:** [reference RULES.md]

---

### What to add

Create a new `UATPhase` object and append it to the phases array in `/lib/uat-config.ts`.

For this phase, write:

**Automated checks** for each of the following (write a check for each):
- [List each API route or database state that can be verified programmatically]
- Examples: "Zoom token exists in user_zoom_tokens table", "Zoom API route returns 200", "OAuth callback redirects correctly"

**Manual steps** for each of the following:
- [List each UI/UX item that needs human eyes]
- Examples: "Zoom connect button appears on integrations page", "After connecting, status shows as connected", "Zoom meeting link appears in trip itinerary"

For each manual step: write plain English instructions a non-technical person can follow. Include where to navigate, what to click, and what a passing result looks like.

---

### Output

Modified `/lib/uat-config.ts` with the new phase appended.
Any new `/api/admin/uat/check-[feature]/route.ts` routes needed.
Nothing else should be modified.

---

*Part of the Agentic Engineering methodology. The UAT Runner is the testing loop baked INTO the product.*
