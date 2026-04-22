# NOTES

> This document serves as a comprehensive reference for development methodologies, patterns, and best practices used by the software development team.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Software Development Team Reference Guide

This document serves as a comprehensive reference for development methodologies, patterns, and best practices used by the software development team.

## Development Methodologies

### Test-Driven Development (TDD)
Test-Driven Development is a software development process that relies on the repetition of a very short development cycle:
1. **Red**: Write a failing test for the desired functionality, run it, verify it FAILS
2. **Green**: Write minimal code to make the test pass
3. **Refactor**: Clean up test code and Improve the code while keeping tests green

**Benefits**:
- Ensures code is testable from the start
- Provides immediate feedback on code correctness
- Creates a comprehensive test suite as a byproduct
- Reduces debugging time
- Improves code design through refactoring

**Best Practices**:
- Write the simplest test that could possibly fail
- Write the minimum code to pass the test
- Refactor only when tests are green
- One test at a time
- Keep tests fast and independent

### Component-Driven Development (CDD)
Component-Driven Development focuses on designing software applications by building loosely-coupled independent components.

**Key Principles**:
- Single responsibility per component
- Clear interfaces between components
- High cohesion within components
- Low coupling between components
- Reusability and composability

**Implementation Strategy**:
- Identify component boundaries
- Define component interfaces
- Build components in isolation
- Test components independently
- Compose components into features

### Feature-Driven Development (FDD)
Feature-Driven Development combines elements of both plan-driven and agile approaches. It focuses on delivering working software in small, client-valued increments.

**Five Processes**:
1. Develop an overall model
2. Build a features list
3. Plan by feature
4. Design by feature
5. Build by feature

**Characteristics**:
- Feature teams own features end-to-end
- Regula

*[truncated — see source for full prompt]*