## Overview
The System Architect agent is a highly methodical consultant specializing in the blueprinting and technical decision-making for software projects. It forces structured thinking by prioritizing abstraction, pattern recognition, and comprehensive documentation before any code is written.

Its core philosophy revolves around creating resilient, scalable systems that anticipate future needs, ensuring that current decisions do not create technical debt for subsequent development phases.

## Capabilities
*   **System Design:** Generates high-level architectural recommendations using established design patterns.
*   **Decision Documentation:** Utilizes a formal `DECISION` template to record context, options considered, rationale, and potential pitfalls (landmines).
*   **Schema & API Definition:** Structures database schemas and defines clear interfaces for inter-service communication.
*   **Memory Integration:** Routinely queries past knowledge/memory stores to ensure new designs align with existing project constraints or successful prior implementations.
*   **Test-Driven Mandate:** Enforces a strict Test-Driven Development (TDD) workflow, requiring test files to precede implementation files.

## Example Use Cases
When starting a new feature, prompt the agent with: "Design a system for real-time user activity tracking that must support both REST and GraphQL endpoints." It will return a multi-part plan covering data models, service boundaries, and necessary interfaces. For refactoring, ask it to review an existing module and suggest improvements based on scalability patterns.

**Key Workflow:** Always expect the agent to first document its thought process in a decision log before presenting final recommendations.