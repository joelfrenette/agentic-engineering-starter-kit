# API Documentation
**Project:** [PROJECT NAME]
**Last updated:** [DATE]
**Total routes:** [N]

---

## Overview

[Describe the API structure -- REST, GraphQL, hybrid, framework-specific conventions, etc.]

**API style:** [e.g., REST, tRPC, GraphQL]
**Base URL (staging):** [URL]
**Base URL (production):** [URL]
**Authentication method:** [e.g., Bearer token, session cookie, API key]
**Standard response format:**

```json
{
  "data": {},
  "error": null
}
```

**Standard error format:**

```json
{
  "data": null,
  "error": "Human-readable error message",
  "code": "ERROR_CODE"
}
```

---

## Authentication

[Describe how API authentication works:]

- All protected routes require: [header/cookie/parameter]
- Auth validation happens in: [middleware/wrapper/route level]
- Required wrapper for protected routes: `[functionName]()`
- Required wrapper for admin routes: `[functionName]()`

---

## Route Index

| Method | Route | Auth Required | Description |
|--------|-------|--------------|-------------|
| GET | /api/[resource] | Yes | List [resources] |
| POST | /api/[resource] | Yes | Create [resource] |
| GET | /api/[resource]/[id] | Yes | Get single [resource] |
| PUT | /api/[resource]/[id] | Yes | Update [resource] |
| DELETE | /api/[resource]/[id] | Yes | Delete [resource] |

---

## Route Details

### GET /api/[resource]

**Purpose:** [What this route does]
**Auth:** Required / Not required / Admin only
**Wrapper:** `withErrorHandler(requireAuth(handler))`

**Request:**
```
Headers:
  Authorization: Bearer [token]

Query params:
  [param]: [type] -- [description] (optional/required)
```

**Response (200):**
```json
{
  "data": [
    {
      "[field]": "[type]",
      "[field]": "[type]"
    }
  ]
}
```

**Error responses:**
- 401 -- Not authenticated
- 403 -- Not authorized
- 500 -- Server error

---

### POST /api/[resource]

**Purpose:** [What this route does]
**Auth:** Required / Not required / Admin only

**Request body:**
```json
{
  "[field]": "[type -- required]",
  "[field]": "[type -- optional]"
}
```

**Response (201):**
```json
{
  "data": {
    "id": "uuid",
    "[field]": "[value]"
  }
}
```

---

## AI/LLM Routes (if applicable)

[Document any routes that call AI models:]

### POST /api/[ai-route]

**Purpose:** [What AI operation this performs]
**Model selection:** Read from [config source] -- never hardcoded
**Credit deduction:** Via `[creditFunction]()` only
**Streaming:** [Yes/No]

---

## Webhook Routes (if applicable)

| Route | Provider | Events handled |
|-------|----------|---------------|
| /api/webhooks/[provider] | [Provider] | [List events] |

**Webhook security:** [How webhooks are validated]

---

## Route Change Log

| Date | Route | Change | Reason |
|------|-------|--------|--------|
| | All routes | Initial API established | Project bootstrap |

---

*Update after every new or changed route. Part of the Agentic Engineering methodology.*
