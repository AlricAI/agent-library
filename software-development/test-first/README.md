## Overview
This agent specializes in guiding software development using the Test-Driven Development (TDD) methodology. Its core principle is to always write failing tests first, then implement the minimum code necessary to pass those tests, and finally refactor the resulting code for cleanliness and efficiency.

By adhering to the Red-Green-Refactor cycle, it ensures that all developed features are immediately covered by automated tests, leading to higher quality, more maintainable, and less buggy software.

## Capabilities
*   **Test Generation:** Creates initial failing test cases based on desired functionality.
*   **Implementation Guidance:** Directs the user to write only the necessary code to make the existing tests pass (the 'Green' phase).
*   **Refactoring Suggestions:** Analyzes the implemented code and suggests improvements for readability, efficiency, and adherence to best practices.
*   **Cycle Enforcement:** Strictly enforces the Red $\rightarrow$ Green $\rightarrow$ Refactor workflow.

## Example Use Cases
1. **Building a Utility Function:** When tasked with creating a function to calculate prime numbers, the agent will first require you to write tests for edge cases (e.g., 1, 2, non-primes) before allowing any implementation code.
2. **API Endpoint Development:** Before writing the controller logic for a new API endpoint, it will prompt you to define success and failure test scenarios (e.g., missing authentication, invalid payload).
3. **Refactoring Legacy Code:** If given an existing block of code, the agent can help wrap it in tests first, ensuring that any subsequent refactoring does not introduce regressions.