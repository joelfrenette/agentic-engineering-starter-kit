# Components & Services Documentation
**Project:** [PROJECT NAME]
**Last updated:** [DATE]

---

## Component Conventions

[Describe how components are organized and named in this project:]

**Component location:** `/[src/]components/[feature]/ComponentName.tsx`
**Naming:** PascalCase for components, camelCase for hooks and utilities
**Props:** Always typed with TypeScript interfaces
**State management:** [local state / context / Zustand / Redux / etc.]
**Styling approach:** [Tailwind classes / CSS modules / styled-components / etc.]

---

## Component Index

| Component | Location | Purpose | Used in |
|-----------|----------|---------|---------|
| | | | |

---

## Core Components

### [ComponentName]

**Location:** `/components/[path]/ComponentName.tsx`
**Purpose:** [What this component does and when to use it]

**Props:**
```typescript
interface [ComponentName]Props {
  [prop]: [type]; // [required/optional] -- [description]
  [prop]?: [type]; // optional -- [description]
}
```

**Usage:**
```tsx
<ComponentName
  [prop]="[value]"
/>
```

**Notes:**
- [Any important notes about usage, gotchas, or limitations]
- [When NOT to use this component]

---

## Hooks

### use[HookName]

**Location:** `/hooks/use[HookName].ts`
**Purpose:** [What this hook does]

**Parameters:**
```typescript
[paramName]: [type] // [description]
```

**Returns:**
```typescript
{
  [value]: [type]; // [description]
  [fn]: () => void; // [description]
}
```

**Usage:**
```tsx
const { [value], [fn] } = use[HookName]([params]);
```

---

## Lib Services

### [ServiceName]

**Location:** `/lib/[path]/[service].ts`
**Purpose:** [What this service handles]

**Exported functions:**

```typescript
// [functionName]: [what it does]
export async function [functionName]([params]): Promise<[returnType]>
```

**Important notes:**
- [Any critical notes -- e.g., "this is the ONLY function that should be called for X"]

---

## Context Providers

### [ContextName]

**Location:** `/context/[ContextName].tsx`
**Purpose:** [What state this manages]
**Provided values:**

```typescript
{
  [value]: [type]; // [description]
  [setter]: ([value]: [type]) => void; // [description]
}
```

**Where it wraps:** [Which part of the component tree]

---

## Component Change Log

| Date | Component | Change | Reason |
|------|-----------|--------|--------|
| | All components | Initial structure established | Project bootstrap |

---

*Update when adding or significantly changing components, hooks, or services. Part of the Agentic Engineering methodology.*
