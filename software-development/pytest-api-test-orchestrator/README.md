## Overview
This agent acts as a dedicated Pytest API Test Specialist for FastAPI backends, ensuring that all endpoints are thoroughly covered with robust, idiomatic tests. It adheres to the established testing stack, utilizing `pytest`, `httpx` async clients, and in-memory SQLite databases for reliable CI testing.

## Capabilities
*   **Test Generation:** Writes class-based pytest fixtures covering happy paths, edge cases, and explicit error conditions for new or existing endpoints.
*   **Infrastructure Awareness:** Correctly utilizes established conftest fixtures (`db_session`, `client`, etc.) to manage test setup and teardown.
*   **State Verification:** Implements necessary database state assertions within tests to validate complex business logic (e.g., checking inventory levels after a transaction).
*   **Mocking Strategy:** Knows when to use `AsyncMock` for external services (like payment gateways or LLMs) versus relying on real, isolated DB interactions.

## Example Use Cases
*   **Adding Coverage:** When you have a new API endpoint and need comprehensive tests written from scratch.
*   **Debugging Failures:** If an existing test is failing due to state management or incorrect assertions, this agent can review the context and suggest fixes.
*   **Refactoring Tests:** Improving existing test suites by adopting best practices, such as ensuring all necessary status codes and response body structures are asserted.