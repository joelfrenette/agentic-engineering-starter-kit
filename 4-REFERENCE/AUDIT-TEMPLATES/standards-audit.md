# Standards & Consistency Audit
**Use this:** Monthly on active projects, or when the codebase starts feeling inconsistent.

---

## PASTE THIS INTO YOUR AI AGENT:

---

You are in **AUDIT mode -- Standards & Consistency**.

Your job is to find inconsistencies in the codebase that will cause confusion, bugs, and slower development as the project grows. Inconsistency is technical debt that compounds silently until it becomes a serious problem.

**Do NOT implement fixes.** Produce a prioritized fix report only.

---

### Project context

**Project:** [PROJECT NAME]
**Stack:** [STACK]
**Established conventions:** [Reference your living docs conventions sections]

**RULES.md:** [Paste or reference -- this is the primary standard to audit against]

**Audit scope:** [Files/directories to include]

---

### RULES.md compliance

This is the highest priority check. For every rule in RULES.md:

1. Is the rule being followed consistently throughout the codebase?
2. Are there any violations?
3. Are there patterns that technically comply but violate the spirit of the rule?

For each violation:
- Rule violated (quote the rule)
- Location (file + line or function)
- What was done instead
- Severity (is this a bug risk or just inconsistency?)

---

### Naming consistency

Check for inconsistencies in:

1. **File naming** -- are all files following the same convention? (kebab-case, PascalCase, camelCase)
2. **Component naming** -- are React components always PascalCase?
3. **Function naming** -- are handlers always handleX? Are async functions awaited consistently?
4. **Variable naming** -- are booleans prefixed with is/has/should? Are arrays plural?
5. **API route naming** -- are routes consistently plural? Nested? Versioned?
6. **Database column naming** -- consistent snake_case? Consistent boolean naming?
7. **CSS class naming** -- consistent with the styling approach?
8. **Environment variable naming** -- consistent prefix conventions?

---

### Error handling consistency

Look for:

1. **Missing error handling** -- async operations without try/catch or .catch()
2. **Inconsistent error shapes** -- some routes return `{ error: "message" }`, others return `{ message: "error" }` or throw unhandled
3. **Silent failures** -- errors caught and ignored (empty catch blocks)
4. **Inconsistent user-facing error messages** -- some errors shown to users, others swallowed
5. **Missing loading and error states** -- UI that can fail without any feedback to the user

---

### TypeScript / type safety (if applicable)

Look for:

1. **`any` types** -- explicit `any` annotations that bypass type checking
2. **Unsafe type assertions** -- `as SomeType` without validation
3. **Missing return types** -- functions without explicit return type annotations
4. **Props without types** -- React components with untyped props
5. **Inconsistent null handling** -- some code checks for null/undefined, similar code doesn't

---

### Import and dependency consistency

Look for:

1. **Inconsistent import styles** -- mixing default and named imports inconsistently
2. **Relative vs absolute imports** -- mixing `../../components/` with `@/components/`
3. **Unused imports** -- imported modules never referenced in the file
4. **Duplicate imports** -- the same module imported multiple times in one file
5. **Wrong import paths** -- importing from deprecated paths (e.g., old lib location)

---

### Code style consistency

Look for:

1. **Console.log left in production code** -- debug output that should be removed
2. **Commented-out code blocks** -- dead code in comments
3. **TODO/FIXME comments** -- old TODOs that were never addressed (list them, don't judge them)
4. **Inconsistent async patterns** -- mixing async/await with .then() chains in the same codebase
5. **Inconsistent conditional rendering** -- mixing ternary, &&, and if blocks without clear rules
6. **Magic numbers and strings** -- hardcoded values that should be named constants

---

### Documentation consistency

Look for:

1. **Functions without JSDoc** where complex functions elsewhere have it
2. **Stale comments** -- comments that describe what the code used to do, not what it does now
3. **Missing README updates** -- documented behavior that no longer matches implementation
4. **Living docs gaps** -- features that exist in code but aren't documented

---

### Output format

**RULES.md violations** (list first -- these are the highest priority)

**Systemic patterns** (name the class of problem, not every instance):
For each pattern:
- Pattern name
- How many instances (rough count)
- Example location
- Recommended fix approach
- Effort to fix systemically (S/M/L)

**Quick wins** (inconsistencies fixable in under 15 minutes each)

**Consistency score by area:**
- Naming: [Good / Needs work / Poor]
- Error handling: [Good / Needs work / Poor]
- Types: [Good / Needs work / Poor]
- Code style: [Good / Needs work / Poor]
- Documentation: [Good / Needs work / Poor]

**Overall assessment:** [One paragraph on the state of the codebase's consistency]

---

*Part of the Agentic Engineering methodology. Consistency is what makes a codebase maintainable.*
