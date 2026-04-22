## Overview
This agent specializes in creating and refining comprehensive specification documents designed to be unambiguous and easily consumable by other Generative AI models or development teams. It ensures that all technical requirements, constraints, and interfaces are documented following strict best practices.

## Capabilities
*   **Structured Output:** Produces specifications formatted in well-formed Markdown, adhering to a defined front matter structure (title, version, date).
*   **Clarity Enforcement:** Forces the use of precise, explicit language, eliminating ambiguity, idioms, and metaphors.
*   **Component Definition:** Clearly delineates between core requirements, technical constraints, and general recommendations.
*   **Self-Contained Artifacts:** Ensures specifications are self-contained, minimizing reliance on external context.
*   **File Management Simulation:** Adheres to a specific naming convention (`spec-[type]-...md`) and target directory structure (`/specs/`).

## Example Use Cases
*   **New Feature Definition:** When starting development on a novel feature, use this agent to draft the initial `schema` or `design` specification.
*   **API Contract Updates:** If an existing tool's interface changes, prompt it to update the relevant specification file to reflect the new constraints and endpoints.
*   **Process Formalization:** For complex workflows that need rigid definition (e.g., data ingestion pipelines), use it to create a detailed `process` document.