# IMPLEMENTATION CHECKLIST

> **Use this checklist when implementing any enhancement from the roadmap.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Enhancement Implementation Checklist

**Use this checklist when implementing any enhancement from the roadmap.**

**For**: Developers, Contributors, Engineering Team

---

## Pre-Implementation (Before Starting)

### Planning & Preparation

- [ ] **Read the implementation spec** (specs/ directory)
  - Understand requirements and scope
  - Review acceptance criteria
  - Note dependencies and prerequisites

- [ ] **Check dependencies**
  - Are any PRs blocking this? (check issue comments)
  - Are any other enhancements prerequisites?
  - Review dependency graph in `specs/ENHANCEMENT_DEPENDENCIES.md`

- [ ] **Review related code**
  - Find similar patterns in existing codebase
  - Identify files that will need modification
  - Check for existing tests to use as templates

- [ ] **Set up workspace**
  - Create feature branch: `feat/issue-XXX-brief-description`
  - Install any new dependencies
  - Verify development environment works

- [ ] **Estimate and track time**
  - Note start date in GitHub issue
  - Set up time tracking (if required)
  - Plan daily/weekly goals

---

## Implementation Phase

### Test-Driven Development (TDD)

**ALWAYS write tests first** before implementation:

- [ ] **Write failing unit tests**
  - Test happy path scenarios
  - Test error cases
  - Test edge cases
  - Run tests - should FAIL initially

- [ ] **Implement feature to make tests pass**
  - Start with simplest implementation
  - Refactor for clarity
  - Follow existing code patterns

- [ ] **Write integration tests**
  - Test interaction with real Azure services (if applicable)
  - Test interaction with other HayMaker components
  - Use fixtures and mocks appropriately

- [ ] **Write security tests** (if security-sensitive)
  - Test credential sanitization
  - Test input validation
  - Test authorization boundaries (multi-tenant)

---

### Code Quality

- [ ] **Follow Python best practices**
  - Type hints on all functions
  - Google-style docstrings
  - PEP 8 compliant (via ruff)


*[truncated — see source for full prompt]*