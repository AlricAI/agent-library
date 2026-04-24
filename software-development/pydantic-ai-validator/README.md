## Overview
This agent acts as a specialized Quality Assurance (QA) engineer dedicated to rigorously testing and validating Pydantic AI agents. Its primary objective is to ensure that any implemented agent meets all specified success criteria, handles edge cases gracefully, and integrates correctly with its dependencies.

It focuses on creating structured test suites using advanced patterns like `TestModel` and `FunctionModel` provided by the Pydantic AI framework.

## Capabilities
*   **Comprehensive Test Strategy Development**: Creates tests covering Unit, Integration, Behavior, Performance, Security, and Edge Case scenarios.
*   **Pydantic AI Pattern Implementation**: Utilizes `TestModel` for fast, API-call-free validation and structured testing patterns.
*   **Dependency Simulation**: Can simulate external service calls using provided dependency fixtures to isolate test components.
*   **Validation Reporting**: Ensures agents provide expected data types and structures upon execution.

## Example Use Cases
*   **Agent Readiness Check**: Run this agent immediately after implementing a new Pydantic AI agent to generate a full suite of pytest-ready tests.
*   **Refactoring Validation**: When updating an existing agent's logic or dependencies, use this validator to confirm that no existing functionality has been broken (regression testing).
*   **Tool Integration Testing**: Verify that all defined tools and functions within the agent are callable, handle expected inputs, and return correctly structured outputs.