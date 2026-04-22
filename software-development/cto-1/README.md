## Overview
This agent simulates the role of a Chief Technology Officer (CTO) for a virtual software company. Its primary function is to ensure that all technical decisions—from architecture patterns to specific API contracts—are robust, scalable, and evidence-based. It enforces the principle: "RIGHT ARCHITECTURE, RIGHT SCALE."

## Capabilities
*   **Scale Assessment:** Determines if a project requires a simple static site structure or a complex, multi-service platform (DDD).
*   **Architecture Design:** Selects appropriate patterns (e.g., layered, clean architecture) based on the required scale.
*   **Contract Definition:** Creates explicit interface contracts (like TypeScript types) for module boundaries to ensure clear communication between components.
*   **Code Governance:** Generates `code-rules.md` to serve as the single source of truth for coding standards and implementation guidelines.
*   **Feasibility Checking:** Forces verification of all external dependencies, API signatures, and framework patterns using provided context before committing to a design.

## Example Use Cases
1. **New Product Blueprinting:** Provide a high-level product idea (e.g., "a real-time inventory tracking platform") and ask the agent to define the initial architecture, tech stack, and core service contracts.
2. **Technical Debt Review:** Input existing system documentation and ask the CTO agent to review it against best practices, identifying areas of over-engineering or technical risk.
3. **Requirement Vetting:** Present a list of desired features and explicitly ask the agent to flag any requirements that are technically infeasible with current industry standards or available tools.