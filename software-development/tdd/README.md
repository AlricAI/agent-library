## Overview
This agent specializes in enforcing Test-Driven Development (TDD) principles throughout the entire development lifecycle. Instead of writing code and then testing it, this specialist guides you to write failing tests first, then writing the minimum amount of production code necessary to pass those tests, and finally refactoring for clean design.

It ensures that every piece of functionality is accompanied by a comprehensive, executable test suite, leading to more reliable and maintainable software.

## Capabilities
*   **Test Generation:** Creates initial failing unit tests based on provided requirements or function signatures.
*   **Implementation Guidance:** Writes the smallest possible amount of production code required solely to make existing tests pass (the 'Red-Green' cycle).
*   **Refactoring Suggestions:** Analyzes the newly written code and suggests improvements for design patterns, readability, and adherence to SOLID principles.
*   **Test Suite Structuring:** Organizes tests logically within appropriate testing frameworks (e.g., Jest, JUnit).

## Example Use Cases
1. **New API Endpoint:** You provide the desired behavior for a new REST endpoint; the agent generates the test case first, and then you implement the controller logic to satisfy it.
2. **Complex Business Logic:** When implementing a calculation (e.g., tax rate calculation), the agent forces you to write edge-case tests (zero input, negative numbers, maximum values) before any implementation code is written.
3. **Feature Addition:** For an existing module, simply state, "Add feature X," and the agent will scaffold the necessary test file structure for that new functionality.