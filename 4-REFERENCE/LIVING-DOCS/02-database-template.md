# Database Documentation
**Project:** [PROJECT NAME]
**Last updated:** [DATE]
**Total tables:** [N]

---

## Overview

[Brief description of the database setup -- provider, type, connection pooling, etc.]

**Database provider:** [e.g., Supabase, PlanetScale, Railway, Neon]
**Database type:** [e.g., PostgreSQL, MySQL]
**ORM/Query builder:** [e.g., Drizzle, Prisma, raw SQL]
**Connection strategy:** [e.g., connection pooling via pgBouncer]
**RLS (Row Level Security):** [Enabled / Disabled / Partial]

---

## Table Index

| Table Name | Purpose | Key relationships |
|------------|---------|-------------------|
| | | |

---

## Core Tables

### [table_name]

**Purpose:** [What this table stores and why it exists]

| Column | Type | Nullable | Default | Description |
|--------|------|----------|---------|-------------|
| id | uuid | No | gen_random_uuid() | Primary key |
| created_at | timestamptz | No | now() | |
| [column] | [type] | [yes/no] | [default] | [description] |

**Indexes:**
- `idx_[table]_[column]` on `[column]` -- [reason]

**RLS Policies:**
- [policy name]: [what it allows and for whom]

**Relationships:**
- `[column]` references `[other_table].[column]`

---

### [next table -- repeat format]

---

## Relationships Map

[Describe the key relationships between tables in plain English, or use a simple list:]

- `users` → `[child table]`: one user has many [things]
- `[table]` → `[table]`: [relationship description]

---

## Migration History

| Migration | Description | Date | Applied |
|-----------|-------------|------|---------|
| 001_initial | Initial schema | [date] | Yes |
| | | | |

**Migration conventions:**
- All migrations are stored in [/migrations or /supabase/migrations]
- Migrations are named: `[NNN]_[description].sql`
- Never edit a migration that has been applied to production -- create a new one

---

## Query Patterns

### Common queries

[Document frequently used queries that agents should know about:]

```sql
-- [Query name]: [what it does]
SELECT ...
```

### Performance considerations

[Note any tables that are large, any queries that are slow, any indexes that are critical:]

- [Table] grows quickly -- always filter by [column] with an index
- [Query pattern] causes N+1 problems -- use [alternative approach]

---

## RLS Policy Reference

[If using row level security, document all policies:]

| Table | Policy | Role | Using | Check |
|-------|--------|------|-------|-------|
| | | | | |

---

## Database Change Log

| Date | Change | Migration | Reason |
|------|--------|-----------|--------|
| | Initial schema | 001_initial | Project bootstrap |

---

*Update this document after every schema migration. Part of the Agentic Engineering methodology.*
