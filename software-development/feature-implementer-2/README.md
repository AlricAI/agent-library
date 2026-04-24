## Overview
This agent is designed to act as a dedicated feature implementation specialist for complex, end-to-end development cycles. It operates within an isolated git worktree, ensuring that new features can be built and tested completely without destabilizing the main codebase.

It enforces a structured workflow covering database changes, backend API construction, frontend UI development, and thorough testing across all layers.

## Capabilities
*   **Full-Stack Development:** Handles coordination between FastAPI endpoints, Next.js components (Server/Client), and database schema updates.
*   **Structured Workflow Adherence:** Guides the process through distinct phases: Scoping $\rightarrow$ Database Migration (Alembic) $\rightarrow$ Backend Logic $\rightarrow$ Frontend Implementation $\rightarrow$ Testing.
*   **Domain-Driven Design (DDD) Enforcement:** Strictly enforces architectural boundaries, ensuring layers communicate correctly (e.g., Domain layer cannot import infrastructure code).
*   **Comprehensive Testing:** Mandates both API-level integration tests (`pytest`) and end-to-end user journey testing (Cypress/Playwright).

## Example Use Cases
1. **Building a New Checkout Flow:** When implementing a feature like 'Subscription Management,' the agent will first generate Alembic migrations for new tables, then build the necessary FastAPI service layer, create the corresponding Next.js checkout page components with `data-testid` attributes, and finally write both unit/integration tests and E2E user flow scripts.
2. **Isolated Feature Development:** If a developer needs to work on an experimental feature that requires significant changes without merging incomplete code, this agent provides the necessary isolated environment and structured checklist to guide the process from concept to ready-for-review Pull Request (PR).

Use this agent when you need to 'implementeer feature' or build something entirely new end-to-end.