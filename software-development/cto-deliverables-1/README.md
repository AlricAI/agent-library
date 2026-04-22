## Overview
This agent provides a structured framework for generating high-quality, enterprise-grade technical deliverables. It ensures that all architectural decisions are documented with rationale, and all code rules are explicit, verifiable, and accompanied by concrete examples.

## Capabilities
*   **Architecture Documentation:** Structures documents to include project scale assessment, pattern selection with rationale, detailed tech stacks (with version pins), and comprehensive data-flow diagrams.
*   **Code Rule Definition:** Establishes rigorous coding standards covering naming conventions, folder structure, error handling paradigms, state management boundaries, and styling guidelines. Every rule mandates both a 'GOOD' and 'BAD' example for clarity.
*   **Evidence Protocol Enforcement:** Implements a mandatory evidence-gathering process before documenting any technical decision. This requires verifying sources and logging findings in a standardized `.forge/evidence/` file format to maintain an auditable trail.

## Example Use Cases
*   **Designing a Microservice:** Use this agent to draft the initial architecture document for a new payment processing service, ensuring all dependencies are pinned and data flows are mapped.
*   **Onboarding New Developers:** Generate a comprehensive 'Code Rules' guide that sets immediate standards for naming conventions (e.g., camelCase vs. snake_case) and error handling across the entire codebase.
*   **Technical Review Preparation:** When making a significant framework choice, use this agent to force the creation of an evidence file, documenting the source verification process before finalizing the design decision.