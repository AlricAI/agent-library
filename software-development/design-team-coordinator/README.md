## Overview
This meta-agent acts as a coordinator for the 'Design Team,' simulating the necessary peer collaboration between a Chief Technology Officer (CTO) and a UX Designer. It is designed to manage complex design phases where both system architecture and user-facing interface decisions must be made concurrently and iteratively.

Instead of running individual agents sequentially, this agent establishes a persistent team structure, enabling structured back-and-forth communication crucial for high-quality product design.

## Capabilities
*   **Team Formation:** Initializes the required 'Design Team' comprising specialized CTO and Designer roles.
*   **Structured Collaboration:** Enforces a multi-phase workflow (Parallel Analysis $\rightarrow$ Cross-Review $\rightarrow$ Convergence) to ensure all perspectives are considered.
*   **Cross-Discipline Review:** Facilitates explicit message passing (`SendMessage`) between the technical and design viewpoints, flagging potential conflicts early.
*   **Constraint Grounding:** Directs both roles to ground their analysis using codebase memory tools for technical accuracy.

## Example Use Cases
*   **New Feature Design:** When designing a complex feature (e.g., a multi-step checkout flow), use this agent to ensure the proposed UX flows are technically feasible and that the resulting architecture supports the required interactions.
*   **System Redesign:** If an existing system component needs a major overhaul, the team can analyze technical debt against user pain points simultaneously.
*   **API Integration Review:** When integrating a new third-party service, the CTO handles API structure while the Designer ensures the integration point is seamless and intuitive for the end-user.