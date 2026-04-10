# RULES.md — Project Non-Negotiables

> Every AI agent reads this file before doing anything. These rules are non-negotiable.
> Last updated: [DATE]
> Project: [PROJECT NAME]

---

## How to Use This File

This file contains the rules that govern this codebase. They exist because:
- Some were established upfront as architecture decisions
- Some were learned the hard way from painful bugs
- All of them exist to prevent specific, documented failure modes

**Every agent must confirm they have read and will enforce these rules before writing any code.**

---

## 1. Architecture Rules

### Non-negotiable patterns

```
[FILL IN YOUR PROJECT'S NON-NEGOTIABLE PATTERNS]

Examples to adapt:
- All API routes must use withErrorHandler() wrapper
- All authenticated routes must use requireAuth() middleware
- All admin routes must use requireAdmin() middleware
- Credit/billing deductions must only happen through [single designated function]
- Cost tier values must only be read server-side from [config table] -- never trusted from client
```

### Banned patterns

```
[LIST PATTERNS THAT ARE EXPLICITLY BANNED AND WHY]

Examples to adapt:
- [specific provider/pattern]: causes [specific problem]. Use [alternative] instead.
- Direct database writes from client-side code: security risk. All writes must go through API routes.
- Hardcoded secrets: use environment variables only.
```

### Required file/function locations

```
[SPECIFY WHERE THINGS MUST LIVE]

Examples to adapt:
- All icons: use getIcon() from /lib/icon-map.ts -- never import icon libraries directly
- All AI requests: use /lib/ai-unified/ -- /lib/ai/ is deprecated
- All email sends: use /lib/email/ -- never call email providers directly
```

---

## 2. Database Rules

```
[FILL IN YOUR DATABASE NON-NEGOTIABLES]

Examples to adapt:
- Never run migrations on production directly -- always test on staging first
- All user-facing data must have RLS (Row Level Security) policies
- Correct column names: [list any columns that are frequently confused]
- [Table name] is the source of truth for [specific data] -- never duplicate this data elsewhere
```

---

## 3. API / Backend Rules

```
[FILL IN YOUR API NON-NEGOTIABLES]

Examples to adapt:
- All routes must validate input before processing
- All routes must return consistent error shapes: { error: string, code: string }
- Pricing/cost data must be read from [source] -- never from request bodies
- All external API calls must have timeout and error handling
```

---

## 4. Frontend Rules

```
[FILL IN YOUR FRONTEND NON-NEGOTIABLES]

Examples to adapt:
- All new components go in /components/[feature]/ -- not the root components folder
- No inline styles except for dynamic values -- use Tailwind classes
- All forms must have loading states and error states
- Never store sensitive data in localStorage
```

---

## 5. AI / LLM Rules (if applicable)

```
[FILL IN IF YOUR PROJECT USES AI FEATURES]

Examples to adapt:
- Model selection: always read from [config source] -- never hardcode model names
- [Specific model/provider] is banned: [reason]
- All AI responses must be validated before displaying to users
- Token/credit accounting must go through [single function]
```

---

## 6. Security Rules

```
[FILL IN YOUR SECURITY NON-NEGOTIABLES]

- All user input must be sanitized before database operations
- Authentication must be verified server-side on every protected operation
- Never log sensitive user data (emails, passwords, payment info)
- All file uploads must be validated for type and size before processing
- Environment variables: never commit .env files, never expose server vars to client
```

---

## 7. Lessons Learned (Add to this constantly)

This section grows over time. Every painful debugging session teaches something. Write it here immediately.

```
[DATE] - [LESSON]
What happened: [brief description of the bug or problem]
Root cause: [what actually caused it]
Rule added: [what rule prevents this from happening again]

---

Example format:
2025-01-15 - AI model cost tier bypass
What happened: Client was passing cost_tier in request body; a bad actor could request premium models for free.
Root cause: Route was trusting client-supplied cost_tier instead of reading from database.
Rule added: cost_tier must ONLY be read server-side from system config table. Never trust client request bodies for pricing data.
```

---

## Rule Change Log

| Date | Rule Changed | Reason |
|------|-------------|--------|
| [DATE] | Initial rules established | Project bootstrap |
| | | |

---

*Any agent that violates these rules must be corrected immediately and the fix documented.*
