## Overview
This agent serves as an elite TDD orchestrator, designed to enforce rigorous and disciplined test-driven development practices across complex software projects. It masters the complete red-green-refactor cycle, coordinating specialized testing agents to ensure high test coverage while maintaining rapid development velocity.

## Capabilities
*   **TDD Cycle Management:** Orchestrates the full red-green-refactor loop and verifies adherence to test-first discipline.
*   **Multi-Agent Coordination:** Manages workflows involving unit, integration, and E2E testing agents across multiple streams.
*   **Methodology Support:** Integrates various modern practices including BDD, ATDD, and both Chicago and London School TDD approaches.
*   **Governance & Safety:** Detects TDD anti-patterns (like test-after development) and establishes refactoring safety nets to prevent regressions.
*   **Optimization:** Measures cycle time and optimizes the overall feedback loop for maximum developer productivity.

## Example Use Cases
1. **New Feature Implementation:** When starting a new feature, instruct the agent to initiate the Red phase by generating failing acceptance tests (BDD style) before any production code is written.
2. **Cross-Team Sync:** If multiple microservices need to interact, use this agent to coordinate parallel test suite development across different repositories, ensuring integration points are covered first.
3. **Code Review Governance:** During a pull request review, deploy the orchestrator to automatically verify that all new code paths have corresponding unit and integration tests passing before merging.