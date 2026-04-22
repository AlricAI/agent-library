# Code Review

> > AI excels at catching what you miss.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI-Assisted Code Review

> AI excels at catching what you miss. Humans excel at judging what matters.

## The Problem

Code review is time-consuming and inconsistent. Reviewers miss security issues, overlook edge cases, or focus on style over substance. Meanwhile, AI agents catch these mechanical issues instantly but can't judge business logic correctness, UX decisions, or architectural fit.

The mistake: treating AI review as a replacement for human review. The result: merged code with correct syntax but wrong behavior, or wasted time arguing with AI about subjective decisions.

The insight: AI and human reviewers have complementary strengths. Use both, for different purposes.

## The Pattern

### AI Review Strengths

AI is excellent at reviewing:

| Category | What AI Catches | Example |
|----------|----------------|---------|
| **Security** | SQL injection, XSS, exposed secrets, unsafe deserialization | `db.query("SELECT * FROM users WHERE id = " + userId)` |
| **Consistency** | Naming violations, pattern deviations, style drift | Function named `getUserData` when pattern is `getUser` |
| **Edge Cases** | Missing null checks, unhandled errors, boundary conditions | Array access without length check |
| **Resource Leaks** | Unclosed files, connections, event listeners | `fs.readFile()` without `.close()` |
| **Type Safety** | Missing validations, unsafe casts, implicit any | `JSON.parse()` without try/catch |
| **Accessibility** | Missing alt text, keyboard navigation, ARIA labels | `<button>` without accessible label |

### Human Review Strengths

Humans are excellent at reviewing:

| Category | What Humans Judge | Example |
|----------|------------------|---------|
| **Business Logic** | Does this implement the requirement correctly? | Discount calculation logic |
| **UX Decisions** | Is this the right user experience? | Error message clarity |
| **Architecture** | Does this fit the system design? | Adding state to a stateless service |
| **Tradeoffs** | Is th

*[truncated — see source for full prompt]*