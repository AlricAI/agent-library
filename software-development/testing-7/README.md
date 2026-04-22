# Testing

> > Write the test description.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI-Assisted Test Generation

> Write the test description. Let AI generate variations. Always verify the assertions.

## The Problem

Test generation is repetitive but critical. Developers skip tests because writing edge cases is tedious. AI agents can generate tests quickly but often produce brittle, unrealistic tests that provide false confidence. Tests that mock internals, use fake data like "foo@example.com", or test implementation details break on every refactor.

The insight: AI is excellent at generating test variations once you provide a golden example. Use AI to scale test coverage, but write the first test yourself to establish quality standards.

## The Pattern

### The 80/20 Rule for AI Test Generation

**You write (20% effort):**
- Business logic tests (core algorithms, workflows, state machines)
- First test in a new suite (establishes pattern)
- Complex integration tests (multi-step flows)
- Tests requiring domain knowledge

**AI writes (80% effort):**
- Edge case variations (null, empty, boundary conditions)
- Permission matrix tests (role × action combinations)
- Input validation tests (invalid formats, types, ranges)
- Error handling paths
- Regression tests for fixed bugs

### The Golden Test Pattern

Write one high-quality test, then ask AI to generate variations.

**Step 1: Write the golden test**
```typescript
describe('UserService.createUser', () => {
  it('creates user with valid data', async () => {
    const input = {
      email: 'jane.doe@company.com',
      name: 'Jane Doe',
      role: 'editor'
    };

    const user = await userService.createUser(input);

    expect(user).toMatchObject({
      email: 'jane.doe@company.com',
      name: 'Jane Doe',
      role: 'editor',
      id: expect.any(String),
      createdAt: expect.any(Date)
    });

    const saved = await db.users.findById(user.id);
    expect(saved.email).toBe('jane.doe@company.com');
  });
});
```

**Step 2: Ask AI to generate variations**
```
Generate edge case tests for 

*[truncated — see source for full prompt]*