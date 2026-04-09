# Prompt 11 — Checkpoints, Backups & GitHub Best Practices
**Use this:** During bootstrap (to set up the full Git/GitHub system) and as a reference any time you need to create a restore point or recover from a broken branch.

---

## PART A: GITHUB PROJECT SETUP (run once during bootstrap)

### PASTE THIS INTO YOUR AI AGENT:

---

You are in **ARCHITECT + CODE mode** for GitHub and version control setup.

We are configuring the full Git/GitHub best practices for this project as part of the Agentic Engineering methodology. This is infrastructure work -- no feature code.

Read RULES.md: [paste or reference]

---

### Branch protection rules to configure on GitHub

Go to: GitHub repo → Settings → Branches → Add rule for `main`

Configure:
```
Branch name pattern: main

[x] Require a pull request before merging
    [x] Require approvals: 1 (even if you're solo -- forces a review moment)
    [x] Dismiss stale PR approvals when new commits are pushed

[x] Require status checks to pass before merging
    (Add your Vercel deployment check once CI is set up)

[x] Require branches to be up to date before merging

[x] Do not allow bypassing the above settings
```

**Why:** Prevents accidental direct pushes to production. Forces you to go through the PR process which is your final review gate.

---

### Branch naming conventions

Every branch follows this pattern: `[type]/[short-description]`

```
feat/     -- new feature          feat/zoom-integration
fix/      -- bug fix              fix/credits-not-deducting
refactor/ -- code cleanup         refactor/unified-ai-layer
audit/    -- any audit pass       audit/security-pass-3
docs/     -- docs only            docs/update-api-routes
hotfix/   -- urgent prod fix      hotfix/auth-broken-prod
checkpoint/ -- backup snapshot    checkpoint/phase-2-complete
```

**Rules:**
- Lowercase only
- Hyphens not underscores
- Short but descriptive (3-5 words max)
- Never: `test`, `temp`, `joel-branch`, `new-branch`, `fix2`

---

### Commit message conventions (Conventional Commits)

Format: `type(scope): description`

```bash
feat(chat): add streaming response to Aiva
fix(credits): correct deduction on free tier models
refactor(auth): consolidate Google and Microsoft OAuth handlers
docs(api): update route index with new email endpoints
audit(security): add missing requireAuth to admin routes
chore(deps): update Supabase client to v2.39
```

**Types:** feat, fix, refactor, docs, audit, chore, test, style
**Scope:** the area of the codebase affected (chat, credits, auth, email, etc.)
**Description:** present tense, lowercase, no period at end

**Why this matters for AI agents:** When you paste git log output into a debugging prompt, conventional commits let the agent instantly understand what changed and where. Random commit messages ("fixed it", "updates") are useless context.

---

### The PR template

Create `.github/pull_request_template.md`:

```markdown
## What does this PR do?

[One sentence description]

## Type of change
- [ ] feat -- new feature
- [ ] fix -- bug fix
- [ ] refactor -- no behavior change
- [ ] audit -- audit pass results
- [ ] docs -- documentation only
- [ ] hotfix -- urgent production fix

## Branch phase
- [ ] PLAN approved
- [ ] ARCHITECT approved
- [ ] CODE complete
- [ ] QA passing on staging
- [ ] UAT complete (browser tested as real user)
- [ ] Living docs updated
- [ ] RULES.md updated if new lessons learned

## What was NOT changed (scope freeze confirmation)
[List the files/systems explicitly not touched]

## Checklist
- [ ] Staging has been tested
- [ ] 3-minute timer observed before testing
- [ ] No console.log left in code
- [ ] No hardcoded secrets
- [ ] RULES.md violations: none found

## Screenshots (if UI changed)
[Before / After]

## Known issues
[Anything promoted with known issues -- rare, but honest]
```

---

### The .github/workflows setup (basic CI)

Create `.github/workflows/checks.yml`:

```yaml
name: Branch Checks

on:
  pull_request:
    branches: [main]

jobs:
  lint-and-type-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      - run: npm ci
      - run: npm run lint
      - run: npm run type-check
```

Add to `package.json` scripts:
```json
{
  "scripts": {
    "lint": "next lint",
    "type-check": "tsc --noEmit"
  }
}
```

**Why:** Catches type errors and lint violations before they reach main. Takes 90 seconds. Saves hours of debugging.

---

## PART B: CHECKPOINT SYSTEM (restore points for working code)

### The Museum Piece Rule

Before any risky change -- major refactor, database migration, dependency upgrade, architectural shift -- create a named checkpoint. This is your "if everything breaks, I can come back here" point.

**The rule:** If you would be upset losing this state, tag it first.

---

### Creating a checkpoint

```bash
# 1. Make sure staging is passing and you've committed everything
git status  # should be clean

# 2. Create an annotated tag
git tag -a checkpoint/[description] -m "[What is working at this point]"

# Examples:
git tag -a checkpoint/phase-1-complete -m "Phase 1: auth + core chat working, credits deducting correctly"
git tag -a checkpoint/pre-zoom-integration -m "Everything working before Zoom OAuth integration"
git tag -a checkpoint/8s-audit-clean -m "Post security audit, all 8S standards passing"

# 3. Push the tag to GitHub (tags don't push automatically)
git push origin checkpoint/phase-1-complete
```

---

### Listing your checkpoints

```bash
# See all checkpoint tags
git tag -l "checkpoint/*"

# See all tags with their messages
git tag -n | grep checkpoint

# See what changed since a checkpoint
git log checkpoint/phase-1-complete..HEAD --oneline
```

---

### Restoring to a checkpoint

**Option A: Inspect the checkpoint (safe -- doesn't change your working branch)**
```bash
git checkout checkpoint/phase-1-complete
# Look around, test, verify
# Return to your branch:
git checkout main
```

**Option B: Create a new branch FROM the checkpoint (recommended)**
```bash
# This is the safest restore method -- never destroys anything
git checkout -b recovery/from-phase-1 checkpoint/phase-1-complete
# You now have a clean branch from the checkpoint
# Fix what broke, then cherry-pick the good commits forward
```

**Option C: Hard reset the current branch to a checkpoint (destructive -- use carefully)**
```bash
# WARNING: This discards all commits after the checkpoint on this branch
git reset --hard checkpoint/phase-1-complete
# Only do this if you are certain you want to abandon all work since the checkpoint
```

---

### Checkpoint naming guide

```
checkpoint/phase-[N]-complete          After each phase passes UAT
checkpoint/pre-[risky-operation]       Before anything scary
checkpoint/[feature]-working           After a major feature ships cleanly
checkpoint/post-[audit]-clean          After an audit pass with all fixes applied
checkpoint/[date]-stable               Periodic snapshots (monthly)
```

---

### The checkpoint calendar (integrate with audit cycles)

```
Every phase completion     → checkpoint/phase-N-complete
Before any DB migration    → checkpoint/pre-migration-[description]
Before any dependency bump → checkpoint/pre-deps-update-[date]
After audit pass           → checkpoint/post-[audit-type]-clean
Monthly (1st of month)     → checkpoint/[YYYY-MM]-stable
```

---

## PART C: RECOVERY PLAYBOOK

If a branch breaks badly and you need to recover:

**Step 1: Don't panic. Assess.**
```bash
git log --oneline -10   # What changed recently?
git diff HEAD~1         # What changed in the last commit?
```

**Step 2: Try a targeted revert first**
```bash
# Revert the specific bad commit (creates a new commit undoing it)
git revert [commit-hash]
# This is safer than reset -- it preserves history
```

**Step 3: If that doesn't work, go to the nearest checkpoint**
```bash
git tag -l "checkpoint/*"  # Find your nearest checkpoint
git checkout -b recovery/[description] checkpoint/[nearest-tag]
```

**Step 4: Cherry-pick the good commits forward**
```bash
git log checkpoint/[tag]..HEAD --oneline  # Find commits you want to keep
git cherry-pick [commit-hash]             # Apply them one at a time to your recovery branch
```

**Step 5: Document what happened**
Add to RULES.md: what broke, why, and the rule that prevents it next time.

---

*Part of the Agentic Engineering methodology. Checkpoints are cheap insurance. Using them is the difference between a 10-minute recovery and a 2-day rebuild.*
