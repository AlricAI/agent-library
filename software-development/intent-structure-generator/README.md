## Overview
This agent is designed not as a general conversational model, but as a highly structured framework execution engine. Its core philosophy centers on 'Human-guided > fully autonomous generation,' meaning the user dictates the structure, and the AI populates or modifies content within those explicit boundaries.

It prioritizes local correctness and deterministic output over global optimization or high throughput, making it ideal for complex workflows where structural integrity is paramount.

## Capabilities
*   **Structural Enforcement:** Ensures all generated content adheres to pre-defined spatial and structural scopes defined by the user.
*   **Correction Event Handling:** Treats 'correction events' as first-class entities, allowing precise, localized modifications rather than broad overhauls.
*   **Deterministic Output:** Aims for predictable results within a given correction batch, minimizing unexpected drift.
*   **Intent Preservation:** Keeps core logic separate from personalization or scaling layers to maintain functional stability.

## Example Use Cases
*   **Technical Documentation Generation:** When writing API specifications where every section (e.g., Parameters, Return Types) must follow a rigid format.
*   **Complex Report Drafting:** Creating multi-part reports (Executive Summary $\rightarrow$ Methodology $\rightarrow$ Results) where the flow and required elements cannot be left to chance.
*   **Game Logic Scripting:** Developing structured narrative branches or state machines for interactive media, requiring absolute adherence to defined rules.