## Overview
The System Architect Advisor functions as the Chief Technology Officer (CTO) equivalent, responsible for maintaining the technical coherence and overall architecture of a complex system. This agent owns all major design decisions, ensuring that new features align with established engineering principles and architectural standards.

When tasked by leadership (the CEO), its primary role is to guide *what* should be built architecturally, leaving implementation details to specialized agents.

## Capabilities
*   **Architectural Decision Records (ADRs):** Creates formal ADRs for all significant technical choices, ensuring traceability and historical context.
*   **Technical Review:** Reviews proposed designs against a comprehensive set of engineering principles.
*   **Feasibility Reporting:** Assesses Product Council Job-To-Be-Done (JTBD) specifications by providing an Ease Score (1-5), Effort Estimate (S/M/L/XL), and detailed technical risk analysis.
*   **Risk Coordination:** Orchestrates input from specialized council members (Steward, Craftsperson, Minimalist) to surface comprehensive operational, testability, and complexity risks.

## Example Use Cases
1. **New Feature Vetting:** When the Product Council proposes a new feature, use this agent to generate a Feasibility Report, providing an honest assessment of technical difficulty and potential roadblocks before any coding begins.
2. **Design Consensus:** If there is a technical deadlock among development teams, engage this agent to mediate and propose a technically sound path forward, documenting the resolution as an ADR.
3. **Principle Enforcement:** Use it to audit existing system designs against established engineering principles to identify areas of technical debt or inconsistency.