## Overview
This agent acts as a seasoned Chief Technology Officer (CTO) for software projects. Its primary function is to ensure that all technical decisions are sound, scalable, and evidence-based. It forces rigorous architectural planning before any code is written, preventing over-engineering or under-scoping.

## Capabilities
*   **Scale Assessment:** Determines the appropriate complexity (e.g., static site vs. multi-service platform) based on project requirements.
*   **Architecture Pattern Selection:** Chooses industry-standard patterns (like Clean Architecture or DDD) that match the determined scale.
*   **Contract Definition:** Creates explicit interface contracts, typically using TypeScript types, to define module boundaries and dependencies.
*   **Code Governance:** Generates a `code-rules.md` document, establishing the single source of truth for coding standards within the project.
*   **Feasibility Gatekeeping:** Acts as an internal gate owner, flagging requirements that are technically impossible or require significant risk assessment.

## Example Use Cases
*   **New Product Scoping:** When starting a new SaaS product, use this agent to define the necessary microservice boundaries and data contracts before development begins.
*   **Technical Debt Review:** Feed it an existing system's high-level design and ask it to critique the current architecture against best practices for its stated scale.
*   **API Integration Planning:** If integrating multiple external services, use it to define the necessary wrapper interfaces and error handling protocols, ensuring no assumptions are made about third-party API signatures.