# SQL & Database Audit
**Use this:** Before scaling, when queries start feeling slow, or after significant schema growth.

---

## PASTE THIS INTO YOUR AI AGENT:

---

You are in **AUDIT mode -- SQL & Database**.

Your job is to find data model problems and query performance issues before they become production fires. A query that runs fine with 100 rows will destroy performance with 100,000 rows. Find those queries now.

**Do NOT implement fixes.** Produce a prioritized fix report only.

---

### Project context

**Project:** [PROJECT NAME]
**Database:** [Database type and provider]
**ORM/Query builder:** [What's used for queries]
**Current data scale:** [Approximate row counts for main tables if known]
**RLS enabled:** [Yes / No / Partial]

**Database docs:** [Paste your database living doc]
**RULES.md:** [Paste or reference]

**Codebase to audit:** [Specify files/directories -- focus on API routes and server-side data fetching]

---

### Performance checks

#### 1. N+1 query problems

The most common performance killer. Look for:
- A query inside a loop (for/forEach/map with an await inside)
- Fetching a list of items, then fetching related data for each item individually
- ORM patterns that trigger individual queries per relationship

**Example N+1 pattern:**
```javascript
// BAD -- 1 query for users + 1 query per user for their posts
const users = await db.select().from(users);
for (const user of users) {
  user.posts = await db.select().from(posts).where(eq(posts.userId, user.id));
}
```

For each N+1 found:
- Location (file + line)
- How many queries it generates (estimate)
- Fix approach (JOIN, batch query, or eager loading)

---

#### 2. Missing indexes

Look for queries that filter, sort, or join on columns that likely lack indexes:

- WHERE clauses on non-primary-key columns (especially foreign keys)
- ORDER BY on columns without indexes
- JOIN conditions on columns without indexes
- Columns used in search/filter operations

For each missing index:
- Table and column
- Query that needs it
- Recommended index type (standard / unique / composite / partial)
- Estimated impact (High / Medium / Low based on query frequency)

---

#### 3. Overly broad queries (SELECT *)

Look for:
- `SELECT *` when only a few columns are needed
- Fetching entire rows when only IDs or counts are used
- Fetching all records when only the count matters (use COUNT instead)
- Missing LIMIT clauses on queries that could return unbounded rows

---

#### 4. Missing or incorrect constraints

Check the schema for:
- Foreign key relationships without explicit FK constraints
- Columns that should be NOT NULL but are nullable
- Columns that should be unique but lack UNIQUE constraints
- Missing CHECK constraints on enum-like columns
- Timestamps without proper defaults (created_at, updated_at)

---

#### 5. Cascade and cleanup risks

Look for:
- Parent-child relationships without ON DELETE CASCADE or ON DELETE SET NULL
- Soft-delete patterns where related records don't get cleaned up
- Orphaned records that can accumulate over time
- No cleanup logic for temporary or session data

---

#### 6. RLS policy gaps (if using row-level security)

- Tables without RLS policies that contain user data
- Policies that are too permissive (allow all for authenticated users when scope should be narrower)
- Policies missing for specific operations (SELECT has policy, DELETE does not)
- Policies that rely on application-level filtering instead of database-level enforcement

---

#### 7. Schema inconsistencies

- Column naming inconsistencies (user_id vs userId vs userid)
- Inconsistent timestamp column names (created_at vs createdAt vs timestamp)
- Tables missing standard columns (created_at, updated_at, id)
- Inconsistent ID types (some uuid, some serial/integer)
- Boolean columns that should be timestamps (is_deleted vs deleted_at)

---

#### 8. Schema drift

- Tables or columns that exist in the database but aren't documented in living docs
- Tables or columns documented in living docs that don't exist in the schema
- Columns with outdated names in docs vs actual schema
- Missing migrations for changes that appear to have been made manually

---

### Output format

**Performance impact summary** (what's most likely causing or will cause performance problems)

**Critical items** (fix immediately -- will cause production problems at scale):
For each:
- Issue type
- Location
- Impact description
- Recommended fix
- Effort estimate (S/M/L)

**Important items** (fix soon):
[Same format]

**Housekeeping items** (fix when convenient):
[Same format]

**Schema health score:** [Your assessment: Good / Needs attention / Significant issues]

**What looks good:** (Well-structured tables or queries worth noting)

---

*Part of the Agentic Engineering methodology. Database problems compound with scale.*
