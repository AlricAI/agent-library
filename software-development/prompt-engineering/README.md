# Prompt Engineering

> > Precise instructions produce precise code.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt Engineering for Code Tasks

> Precise instructions produce precise code. Vague requests produce vague results.

## The Problem

AI coding agents are literal executors. They don't infer intent from context like human developers do. A prompt like "make this better" or "add error handling" produces generic, often incorrect changes because the agent has no constraints. The result: wasted time reviewing bad code, explaining what you actually meant, and fixing hallucinated features.

The core issue: AI agents optimize for completing the task as stated, not the task you intended. Without explicit constraints, they fill gaps with assumptions.

## The Pattern

### The SCOPE Framework

Structure every non-trivial prompt using SCOPE:

| Component | Purpose | Example |
|-----------|---------|---------|
| **Situation** | Current state + problem | "The auth middleware crashes on missing JWT tokens" |
| **Constraints** | Limits, rules, standards | "Must preserve backward compatibility, use existing error types" |
| **Output** | Expected format/structure | "Return 401 with {error, code} JSON body" |
| **Positive examples** | Show what good looks like | "Like the rate limiter middleware at @middleware/rate-limit.ts" |
| **Edge cases** | Failure modes to handle | "Handle: expired token, malformed token, missing header, revoked token" |

**Bad prompt:**
```
Add validation to the user endpoint
```

**Good prompt using SCOPE:**
```
Situation: POST /api/users accepts any payload, crashes on invalid email
Constraints: Use Zod schema, match validation pattern in @api/teams/route.ts, <50 lines
Output: Return 400 with {field, message}[] on validation errors, 201 with user object on success
Positive example: @api/teams/validation.ts shows the error format
Edge cases: Missing fields, invalid email format, duplicate email, empty strings, null values
```

### Task Decomposition

Break large tasks into 5-20 minute chunks. AI agents lose coherence on multi-step work.

**Instead of:**
```


*[truncated — see source for full prompt]*