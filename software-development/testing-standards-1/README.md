# Testing Standards

> This document outlines a consistent, maintainable, and reliable approach to writing unit tests for JavaScript/TypeScript
projects using Jest. Followin

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Project Testing Standards

This document outlines a consistent, maintainable, and reliable approach to writing unit tests for JavaScript/TypeScript
projects using Jest. Following these guidelines ensures that tests are easy to read, modify, and trust—even without a
dedicated QA team.

## 1. Test Structure: AAA (Arrange–Act–Assert)

Every test should clearly separate three phases:

- **Arrange**: Set up mocks, test data, and the object under test.
- **Act**: Invoke the method being tested.
- **Assert**: Verify the results (outputs, calls, errors).

Example:

```typescript
it('should route to trueSink when predicate returns true', async () => {
  // Arrange
  predicate.mockReturnValue(true);
  const conditionalSink = createConditionalSink();
  
  // Act
  await conditionalSink.emit(testEntry);
  
  // Assert
  expect(predicate).toHaveBeenCalledWith(testEntry);
  expect(trueSink.emit).toHaveBeenCalledWith(testEntry);
  expect(falseSink.emit).not.toHaveBeenCalled();
});
```

## 2. Naming Conventions

### 2.1 `describe` Blocks

Use outer `describe` blocks to name the **condition** or **scenario**. Inner `describe` blocks can further group related
behaviors.

```typescript
describe('ConditionalSink', () => {
  describe('emit', () => {
    describe('when predicate returns true', () => {
      it('should call trueSink.emit', async () => { ...
      });
      it('should wrap trueSink errors in LoggerSinkError', async () => { ...
      });
    });
    
    describe('when predicate returns false', () => {
      it('should call falseSink.emit', async () => { ...
      });
      it('should wrap falseSink errors in LoggerSinkError', async () => { ...
      });
    });
  });
});
```

### 2.2 `it` Blocks

Use the template: `it('should [expected behavior] when [condition]')`.  
If the condition is already described by a parent `describe`, you can shorten it: `it('should [expected behavior]')`.

## 3. Setup and Teardown

- Use `beforeEach` to reset all mocks and create fresh instan

*[truncated — see source for full prompt]*