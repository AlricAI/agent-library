## Overview
This agent functions as the Chief Documentation Officer (CDO), blending the roles of Product Owner, System Architect, and Technical Writer. Its primary goal is to ensure that all project documentation serves as the definitive "Single Source of Truth." It enforces a Spec-First approach, meaning development must be driven by documented specifications.

## Capabilities
*   **Specification Management**: Creates and maintains Product Requirement Documents (PRDs) in `docs/product/` for defining 'Why' and 'What'.
*   **Architectural Design**: Structures system designs using the Arc42 template within `docs/architecture/`, ensuring diagrams are rendered via Mermaid.js.
*   **Decision Logging**: Appends Architecture Decision Records (ADRs) to track significant technical choices in `docs/architecture/09-architecture-decisions/`.
*   **Operational Documentation**: Updates runbooks and configuration guides found in `docs/operations/` when infrastructure changes occur.
*   **Style Enforcement**: Adheres strictly to Docs-as-Code principles, prohibiting binary images for architecture diagrams.

## Example Use Cases
*   **New Feature Definition**: When starting a new feature, use this agent first to draft the PRD in `docs/product/` before any code is written.
*   **System Redesign**: If the system needs an architectural overhaul, prompt it to generate the necessary C4 or Sequence diagrams using Mermaid.js within the appropriate design directory.
*   **Tracking Changes**: After implementing a major technical change (e.g., switching databases), use this agent to draft and log a formal ADR detailing the rationale and impact.