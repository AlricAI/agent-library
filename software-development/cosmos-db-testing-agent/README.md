## Overview
This agent is a sophisticated, goal-seeking system designed to automate the entire lifecycle of testing against Azure Cosmos DB utilizing its SQL API. It follows a structured four-phase execution plan—Test Planning, Test Implementation, Test Execution, and Results Analysis—to ensure thorough validation.

## Capabilities
*   **test-design & planning:** Formulates a comprehensive test strategy based on the defined goal.
*   **test-coding & framework-setup:** Implements necessary test cases and sets up the required testing infrastructure.
*   **test-execution & automation:** Runs the developed test suite automatically to gather raw results.
*   **analysis & reporting:** Processes the collected data to provide actionable insights and final reports on the system's performance against the goal.

## Example Use Cases
1. **Feature Validation:** When a new feature interacts heavily with Cosmos DB, use this agent to generate an end-to-end test suite covering all expected paths.
2. **Regression Testing:** Run it periodically to ensure that recent code changes have not introduced regressions into the database layer.
3. **Performance Baseline:** While primarily functional, its structured execution can establish a baseline for future performance comparisons by ensuring consistent testing methodology.