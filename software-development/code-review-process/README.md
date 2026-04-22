# Code Review Process

> This document outlines our code review process, principles, and best practices.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Code Review Process

This document outlines our code review process, principles, and best practices. Code reviews are a critical part of our development workflow, ensuring quality, knowledge sharing, and consistency across our codebase.

## 1. Core Principles

- **Constructive Feedback**: Focus on the code, not the person
- **Knowledge Sharing**: Use reviews as learning opportunities
- **Consistency**: Apply coding standards uniformly
- **Collaboration**: Work together to find the best solution
- **Timeliness**: Provide prompt reviews to maintain development velocity

## 2. Review Process

### 2.1 Before Submitting Code for Review

```
✓ Run all tests locally and ensure they pass
✓ Review your own code first (self-review)
✓ Ensure your code follows our coding standards
✓ Keep changes focused and reasonably sized
```

### 2.2 Submitting for Review

1. Create a pull request with a descriptive title
2. Include a clear description of:
   - What the changes accomplish
   - How to test the changes
   - Any potential risks or areas of concern
3. Link related issues or requirements
4. Assign appropriate reviewers

### 2.3 Conducting a Review

1. Understand the context and purpose of the changes
2. Review the code against our [C# Coding Style guidelines](C%23-Coding-Style-Essential.md)
3. Verify functionality through manual testing when appropriate
4. Provide specific, actionable feedback
5. Distinguish between required changes and suggestions
6. Approve once all critical issues are addressed

## 3. Review Checklist

### 3.1 Functionality

- Does the code work as intended?
- Are edge cases handled appropriately?
- Is error handling comprehensive and consistent?
- Are there potential race conditions or concurrency issues?

### 3.2 Architecture & Design

- Does the code follow SOLID principles?
- Is the code modular and reusable?
- Are dependencies properly managed?
- Is the solution overly complex for the problem?

### 3.3 Performance

- Are there potential performance bott

*[truncated — see source for full prompt]*