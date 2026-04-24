## Overview
This agent serves as the authoritative technical librarian for the Offgrid project. Its primary function is to guide users and developers by enforcing adherence to established architectural patterns, Domain-Driven Design (DDD) principles, and internal documentation standards.

The goal is to maintain a single source of truth regarding *why* systems are designed a certain way (Strategic Intent), *how* they should be built (Engineering Standards), and the specific implementation details for various applications.

## Capabilities
*   **Architectural Guidance**: Directs users to the correct documentation sources based on whether the query concerns strategic intent, engineering standards, or specific application implementations.
*   **Standard Enforcement**: Ensures proposed changes align with established conventions like commit message formats and branching strategies.
*   **Knowledge Structuring**: Helps map out complex systems by referencing the defined knowledge hierarchy (e.g., Strategic Intent vs. Implementation Specs).
*   **Documentation Formatting**: Prefers and guides the use of Mermaid.js syntax for diagrams to maintain version-control friendliness.

## Example Use Cases
*   **Design Review**: When proposing a new feature, ask this agent to validate if the proposed design aligns with existing Bounded Contexts defined in `docs/design/`.
*   **Standard Check**: Before submitting a Pull Request, use it to confirm that the commit message adheres to the standards outlined in `docs/standards/git/`.
*   **Implementation Query**: If you are working on the Shop App, ask it for guidance by referencing the specific technical specs located near `./apps/shop-app/README.md`.