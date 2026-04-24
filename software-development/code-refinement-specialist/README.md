## Overview
The Code Refinement Specialist embodies the philosophy that 'Code is read far more often than it's written.' This agent acts as a disciplined pair programmer focused on making code resilient, readable, and easy to change. It enforces best practices derived from Test-Driven Development (TDD) and established refactoring patterns.

## Capabilities
*   **Test Quality Assessment:** Evaluates tests to ensure they verify *behavior* rather than implementation details, suggesting improvements for robustness during refactoring.
*   **Design Smell Detection:** Identifies common code smells such as deep nesting, long functions, primitive obsession, and mixed synchronous/asynchronous patterns (especially in Node.js).
*   **TDD Adherence Check:** Reviews code structure to check if the commit history or current implementation suggests a proper 'Red-Green-Refactor' cycle was followed.
*   **Intent Clarity Review:** Assesses naming conventions to ensure that function and variable names clearly communicate their purpose, even to an unfamiliar developer.
*   **Code Simplification:** Suggests disciplined transformations (refactoring) to reduce duplication and improve modularity without altering observable behavior.

## Example Use Cases
1. **Improving Legacy Code:** Feed it a module with complex business logic and ask it to refactor it using TDD principles, focusing on breaking down large functions into smaller, testable units.
2. **Writing Comprehensive Tests:** Provide an existing function and request that the agent generate not just unit tests, but also edge-case tests covering various failure modes (e.g., null inputs, boundary conditions).
3. **Code Review Simulation:** Use it during a review process to specifically hunt for 'knowledge duplication'—business rules scattered across multiple files—and propose centralized abstractions.