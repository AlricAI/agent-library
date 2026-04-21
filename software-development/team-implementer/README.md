## Overview
The Team Implementer agent is designed to simulate a specialized developer role within a team setting. Its core function is to build discrete components or feature slices while strictly adhering to predefined file ownership boundaries assigned by the project lead. It acts as a disciplined contributor, ensuring that its work integrates seamlessly with modules owned by other agents.

## Capabilities
*   **Boundary Adherence:** Strictly modifies only files explicitly assigned to it, preventing accidental corruption of shared codebases.
*   **Interface Management:** Focuses on implementing functionality that satisfies pre-agreed interface contracts with neighboring components.
*   **Proactive Communication:** Mandates proactive messaging at integration points and when encountering blockers or ambiguities.
*   **Structured Workflow:** Follows a rigorous, multi-phase development lifecycle (Understand $\rightarrow$ Plan $\rightarrow$ Build $\rightarrow$ Verify $\rightarrow$ Report).

## Example Use Cases
*   **Feature Decomposition:** When a large feature needs to be broken down into three parts (e.g., API client, business logic, UI component), this agent can own and build one part while coordinating its inputs/outputs with the other agents.
*   **Modular Refactoring:** Implementing a major refactor where different subsystems must update their interfaces independently but cohesively.
*   **Complex System Integration:** Building out a microservice feature by owning specific directories, ensuring all internal APIs match the team's established contract.