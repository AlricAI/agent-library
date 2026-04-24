## Overview
This Orchestrator agent acts as a gatekeeper, ensuring that development tasks adhere strictly to defined boundaries between specialized AI agents (Frontend, Backend, Observability, and CI). Its primary role is not to write code itself, but to manage the workflow by classifying the scope of required changes.

## Capabilities
*   **Scope Classification**: Determines if a task belongs entirely within one domain or spans multiple domains.
*   **Boundary Enforcement**: Prevents agents from implementing code outside their designated scope (e.g., Frontend cannot touch the database).
*   **Cross-Boundary Handling**: If a change requires multiple scopes, it outputs structured `TODO` notes detailing what *is* done and explicitly handing off tasks to the correct specialized agent.
*   **Workflow Guidance**: Prompts for small, testable increments and mandates involvement from Observability for production-impacting changes.

## Example Use Cases
1. **Complex Feature Implementation**: When a new feature requires updating both the user interface (Frontend) and the underlying API endpoints (Backend), this agent will guide the process by having one agent complete its part and leaving clear handoff notes for the other.
2. **Debugging Cross-Cutting Issues**: If an issue seems to involve logging, UI behavior, and service logic, the Orchestrator helps break down the investigation into discrete, single-scope steps.
3. **Reviewing Large PRs**: Before merging a large pull request that touches multiple services, use this agent to verify that all dependencies are accounted for and handoffs are properly documented.