# PRINCIPLES

> > These principles guide how agents build, collaborate, and maintain quality.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# PRINCIPLES.md — Shared Team Philosophy

> These principles guide how agents build, collaborate, and maintain quality.
> All agents should read this file. Update it when lessons are learned.

---

## 1. Test-Driven Development (TDD)

**Philosophy:** Tests are not afterthoughts. They are the specification made executable.

### The Practice

1. **Write tests alongside code** — Every new feature gets tests
2. **Run tests before committing** — `./test.sh` must pass
3. **Tests document behavior** — Reading tests shows what the system does
4. **Regression prevention** — If it broke once, there's a test for it now
5. **Growing suite** — Tests accumulate, coverage increases over time

### The Workflow

```
┌─────────────────────────────────────────────────────┐
│  1. UNDERSTAND what you're building                 │
│  2. WRITE a test that would pass if it worked       │
│  3. BUILD the feature                               │
│  4. RUN the test (it should pass)                   │
│  5. COMMIT with test included                       │
│  6. REPEAT                                          │
└─────────────────────────────────────────────────────┘
```

### Integration Points

| When | Action |
|------|--------|
| Before commit | Run `./test.sh` |
| During PR review | Check test coverage |
| On heartbeat (optional) | Run critical path tests |
| After deploy | Smoke test endpoints |

### Test File Conventions

```
project/
├── src/           # Source code
├── tests/         # Test files
│   ├── test_api.py
│   ├── test_db.py
│   └── test_ws.py
└── test.sh        # Runner script
```

### Example Test Structure

```python
def test_feature_name():
    """Test that [feature] does [expected behavior]"""
    # Arrange - set up test data
    # Act - call the function/API
    # Assert - verify the result
    test("Descriptive assertion", condition)
```

---

## 2. Documentation as Code

**Philosophy:** If it's not written down, it doesn't exist. Documentation travels with the code.

#

*[truncated — see source for full prompt]*