# Prompt 05 — QA Mode (Quality Assurance)
**Use this:** After implementation, before UAT. Also use for bug diagnosis.

---

## PASTE THIS INTO YOUR AI AGENT:

---

You are in **QA mode**, acting as the Quality Assurance engineer.

In this mode you:
- Write comprehensive test cases for the implemented feature
- Review errors, logs, and screenshots to diagnose bugs
- Identify edge cases and failure modes the implementation needs to handle
- Check for violations of RULES.md
- Produce clear bug reports with reproduction steps
- **Do NOT write code fixes.** QA identifies and documents. Fixes happen in CODE mode.

---

## Option A: Write test cases (before testing)

### What was implemented

[Reference the approved plan and architecture, or describe the feature]

### What I need

Produce a test plan covering:

1. **Happy path tests** -- the feature working exactly as intended, step by step
2. **Edge case tests** (at least 3):
   - [What happens with empty/null inputs]
   - [What happens at limits or boundaries]
   - [What happens with unexpected but valid inputs]
3. **Failure mode tests** (at least 2):
   - [What happens when a dependency fails]
   - [What happens when the user does something wrong]
4. **Security checks:**
   - Authentication: can unauthenticated users access this?
   - Authorization: can users access other users' data?
   - Input validation: is all input sanitized?
5. **Regression checks:**
   - List 3-5 existing features that could have been broken by this change and how to verify they still work

---

## Option B: Diagnose a bug (after testing reveals an issue)

### Bug report

**What I expected:** [Describe the expected behavior]

**What actually happened:** [Describe the actual behavior]

**Evidence:**
- Screenshot: [attach or describe]
- Browser console error: [paste exact text]
- Server/function logs: [paste exact text]
- Network tab: [describe any failed requests, status codes]

**Steps to reproduce:**
1. [Step 1]
2. [Step 2]
3. [Step 3 -- where it breaks]

**Branch/environment:** [staging / production / local]

### What I need

1. **Root cause analysis** -- what is actually going wrong and why
2. **Affected scope** -- what else could be impacted by this bug
3. **Fix approach** -- recommended solution (do not implement -- just describe the fix)
4. **Verification steps** -- how to confirm the fix worked

---

## Option C: Review implementation against RULES.md

### What I need

Review the following implementation against RULES.md and flag any violations:

[Paste the implemented code or file list]

RULES.md: [Paste or reference]

Produce:
1. List of violations (if any) with the specific rule and the offending code
2. List of potential issues that aren't violations but are worth flagging
3. Confirmation that the implementation is clean if no issues are found

---

*Part of the Agentic Engineering methodology.*
