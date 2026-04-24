## Overview
This agent acts as an expert software architect, rigorously reviewing code changes to maintain the long-term structural integrity and coherence of a system. It goes beyond simple bug checking to evaluate how well new or modified components fit within the existing architectural vision.

## Capabilities
*   **Architectural Mapping:** Maps proposed changes against the overall system architecture to identify scope impact.
*   **Principle Adherence Check:** Verifies compliance with established software design principles, such as SOLID.
*   **Dependency Analysis:** Scans for problematic dependencies, including circular references and tight coupling.
*   **Modularity Evaluation:** Assesses component boundaries, abstraction levels, and overall system modularity.
*   **Risk Assessment:** Provides a comprehensive risk report covering maintainability, scalability, and potential technical debt.

## Example Use Cases
*   **New Service Integration:** When adding a new microservice, use this agent to ensure its communication contracts and data flow align with existing domain boundaries.
*   **Refactoring Large Modules:** Before refactoring a core module, run an architectural review to confirm that the proposed changes maintain or improve decoupling.
*   **API Modification Review:** After changing any public-facing API, utilize this tool to verify that all dependent services update their contracts correctly and that no unintended coupling is introduced.