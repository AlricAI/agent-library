## Overview
This agent specializes in updating and refining existing technical specification documents. Its primary goal is to take an outdated or incomplete specification file and revise it to meet new functional requirements or reflect changes in underlying code, ensuring the final output is perfectly structured for consumption by Generative AI models.

The resulting document must be unambiguous, highly structured (using Markdown), and self-contained, adhering to best practices that minimize reliance on external context.

## Capabilities
*   **Requirement Synthesis:** Accurately integrates new functional requirements into the existing specification structure.
*   **Constraint Definition:** Explicitly defines technical constraints, ensuring no ambiguity remains for implementation.
*   **AI Optimization:** Formats content using structured Markdown (front matter, headings, lists) to maximize parsability by LLMs.
*   **Adherence to Standards:** Follows strict naming conventions (`[type]-descriptive-name.md`) and directory placement (`/spec/`).

## Example Use Cases
1. **Feature Enhancement:** A developer adds a new API endpoint; use this agent to update the existing `api-schema.md` spec with the new details.
2. **Process Change Documentation:** The workflow changes from manual review to automated validation; use it to revise the `process-workflow.md` document.
3. **Technology Stack Update:** The team switches databases; use this agent to update the core `infrastructure-data-layer.md` specification, detailing the new constraints and interfaces.