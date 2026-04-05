# Security Audit
**Use this:** Before any public launch, after adding auth-related features, and quarterly on active projects.

---

## PASTE THIS INTO YOUR AI AGENT:

---

You are in **AUDIT mode -- Security**.

Your job is to find security vulnerabilities before anyone else does. Be thorough. Be paranoid. Assume the worst about what a bad actor might try.

**Do NOT implement fixes.** Produce a prioritized vulnerability report only. Every finding gets a severity rating. Critical findings are flagged for immediate action before this report is fully approved.

---

### Project context

**Project:** [PROJECT NAME]
**Stack:** [FULL STACK]
**Auth provider:** [Auth method]
**Database:** [Database with RLS yes/no]
**Public-facing:** [Yes/No -- and what's public vs authenticated]
**Audit scope:** [Specify what to audit]

**RULES.md:** [Paste or reference]

**Relevant docs:** [Paste API docs and auth architecture sections]

---

### Authentication checks

For every route and operation, verify:

1. **Unauthenticated access**
   - Can any protected data or operation be accessed without a valid session?
   - Are there API routes missing auth middleware?
   - Can auth be bypassed by manipulating headers, cookies, or tokens?

2. **Session management**
   - How are sessions created, stored, and invalidated?
   - Can sessions be hijacked or forged?
   - Are sessions properly invalidated on logout?
   - Do sessions expire appropriately?

3. **Token handling**
   - Are tokens validated server-side on every request?
   - Are tokens stored securely (not in localStorage for sensitive apps)?
   - Are refresh tokens handled correctly?

---

### Authorization checks

1. **Horizontal privilege escalation (IDOR)**
   - Can User A access User B's data by changing an ID in the URL or request body?
   - Are all database queries filtered by the authenticated user's ID server-side?
   - Is row-level security enforced at the database level (not just application level)?

2. **Vertical privilege escalation**
   - Can a regular user perform admin operations?
   - Are admin routes protected by admin-specific middleware?
   - Can a user grant themselves higher permissions?

3. **Multi-tenant isolation** (if applicable)
   - Can data from one organization be accessed by another?
   - Are all queries scoped to the correct tenant?

---

### Input validation checks

1. **SQL injection**
   - Is any user input concatenated directly into SQL queries?
   - Are parameterized queries or an ORM used consistently?

2. **XSS (Cross-Site Scripting)**
   - Is user-supplied content rendered as raw HTML anywhere?
   - Are rich text inputs sanitized before display?

3. **Input validation gaps**
   - Are file types and sizes validated before processing uploads?
   - Are numeric inputs validated to be within expected ranges?
   - Are enum values validated server-side (not trusted from client)?

4. **Mass assignment**
   - Can users supply unexpected fields in request bodies that get saved to the database?
   - Are only expected fields extracted from request bodies?

---

### Secrets and sensitive data checks

1. **Hardcoded secrets**
   - Are there any API keys, tokens, or passwords in source code?
   - Are there any secrets in comments or commit history?

2. **Environment variable exposure**
   - Are server-only secrets accidentally exposed to the client?
   - Are environment variables properly prefixed (e.g., NEXT_PUBLIC_ only for truly public vars)?

3. **Sensitive data logging**
   - Are passwords, tokens, or PII appearing in logs?
   - Are error messages revealing sensitive system information to end users?

4. **Sensitive data in URLs**
   - Are sensitive identifiers or tokens in query parameters (which appear in logs)?

---

### API security checks

1. **Rate limiting**
   - Are auth endpoints (login, signup, password reset) rate limited?
   - Are expensive operations (AI calls, file processing) rate limited?
   - Are there any endpoints that can be abused without limits?

2. **CORS configuration**
   - Is CORS restricted to expected origins?
   - Are credentials included in CORS requests appropriately?

3. **HTTP headers**
   - Are security headers set? (Content-Security-Policy, X-Frame-Options, etc.)
   - Is HTTPS enforced?

4. **Webhook validation**
   - Are incoming webhooks validated with signatures?
   - Can a bad actor send fake webhook events?

---

### Data exposure checks

1. **API responses**
   - Do API responses return more data than the client needs?
   - Are internal fields (password hashes, internal IDs, system data) excluded from responses?

2. **Error responses**
   - Do error messages reveal internal implementation details?
   - Do 404 vs 403 responses reveal whether resources exist?

---

### Output format

**Critical findings** (list first -- these need immediate attention, even before full report approval)

For each finding:
- **Severity:** Critical / High / Medium / Low
- **Type:** [Authentication / Authorization / Injection / Exposure / etc.]
- **Location:** [File, route, or system]
- **Description:** [What the vulnerability is]
- **Attack scenario:** [How a bad actor would exploit this]
- **Recommended fix:** [How to address it]
- **Effort to fix:** S / M / L

**Summary by severity:**
- Critical: [N] findings
- High: [N] findings
- Medium: [N] findings
- Low: [N] findings

**What looks secure:** (Areas that are well-protected -- useful signal)

---

*Part of the Agentic Engineering methodology. Security is not optional.*
