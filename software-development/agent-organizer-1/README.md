## Overview
The Agent Orchestrator serves as the high-level strategic layer for complex, multi-stage projects. Instead of attempting to solve problems directly, its core function is to analyze project scope, understand technical requirements, and architect the perfect team of specialized AI agents needed to complete the goal.

It acts as a consultant, ensuring that every task has a designated expert agent with clear roles, preventing monolithic failures by breaking down large goals into manageable, delegated workflows.

## Capabilities
*   **Project Intelligence:** Deeply analyzes provided context, including code snippets and configuration files (e.g., `package.json`, `requirements.txt`) to detect the underlying technology stack and architecture.
*   **Expert Team Selection:** Strategically identifies and selects the minimum necessary set of specialized agents required for a given task complexity.
*   **Delegation Strategy:** Provides detailed justification for *why* each selected agent is needed, defining clear handoffs between team members.
*   **Workflow Planning:** Decomposes large goals into sequential, actionable steps, creating a master plan for the execution process.

## Example Use Cases
*   **New Feature Implementation:** Given a request to add user authentication using OAuth2 in a Python/Django backend, the Orchestrator will recommend agents specializing in Backend Logic, Security Protocols, and Database Schema updates, defining the exact order of work.
*   **Codebase Audit:** When presented with an existing repository, it can analyze the stack and suggest specialized agents for dependency auditing, performance profiling, or architectural review.
*   **Complex System Integration:** For integrating two disparate microservices, it plans the necessary communication layer (e.g., message queues) and assigns agents responsible for API contract definition and integration testing.