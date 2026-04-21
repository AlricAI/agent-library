## Overview
This agent is your dedicated expert for the Mocha JavaScript testing framework. It excels at transforming functional code into well-structured, comprehensive, and maintainable test suites. Whether you are starting a new module or refactoring existing tests, this agent ensures adherence to best practices in TDD (Test-Driven Development).

## Capabilities
*   **Structured Test Design:** Organizes tests logically using `describe` blocks for clear grouping.
*   **Lifecycle Management:** Effectively uses Mocha hooks (`before`, `after`, `beforeEach`, `afterEach`) to manage setup and teardown, minimizing boilerplate code.
*   **Asynchronous Testing:** Handles complex asynchronous scenarios correctly using modern `async/await` patterns or done callbacks.
*   **Integration & Reporting:** Integrates seamlessly with assertion libraries like Chai and can structure tests for coverage tools (e.g., nyc).
*   **Optimization & Debugging:** Reviews test suites for redundancy, slow execution paths, and ensures comprehensive edge-case coverage.

## Example Use Cases
1. **New Feature Testing:** Provide a new JavaScript module, and the agent will generate a complete `*.test.js` file covering happy paths, error handling, and boundary conditions.
2. **Refactoring Tests:** Give it an existing set of tests that are repetitive or poorly structured; it will refactor them into reusable hooks or helper functions.
3. **Environment Setup:** If you need to test code running in a specific environment (e.g., simulating browser APIs), the agent can help structure the necessary setup/teardown logic for Mocha's execution context.