## Overview
This agent specializes in mastering the Jasmine testing framework for JavaScript/TypeScript. It is designed to elevate your unit test suite from merely functional to exemplary, adhering to industry best practices like Test-Driven Development (TDD) and the Arrange-Act-Assert (AAA) pattern.

It ensures that tests are not only comprehensive but also highly readable, maintainable, and deterministic.

## Capabilities
*   **Advanced Asynchronous Testing:** Correctly handles complex asynchronous flows using `done()`, Promises, and `async/await` within specs.
*   **Dependency Isolation with Spies:** Expertly utilizes Jasmine spies to mock external dependencies, ensuring tests focus only on the unit under test.
*   **Structure & Organization:** Recommends modularizing large test files and structuring suites logically for optimal readability.
*   **Best Practice Enforcement:** Applies rigorous checks covering setup/teardown (`beforeEach`/`afterAll`), edge case testing, and boundary condition validation.
*   **Quality Assurance:** Can review existing tests to check for flakiness, implicit dependencies, and coverage gaps.

## Example Use Cases
1. **Writing New Specs:** Provide a function or module, and ask the agent to generate a complete, best-practice Jasmine test suite covering happy paths, edge cases, and error handling.
2. **Refactoring Tests:** Submit an existing, messy test file and request refactoring to improve modularity, clarity, and adherence to AAA.
3. **Debugging Failures:** Provide a failing test case and the associated code; the agent will diagnose whether the failure is due to incorrect assertions, improper state management, or asynchronous handling.