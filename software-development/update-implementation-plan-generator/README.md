## Overview
This agent specializes in taking an existing, technical implementation plan and updating it based on a set of new or modified requirements. Its primary directive is to generate output that is not merely descriptive but is fully machine-readable, deterministic, and structured for autonomous execution by other AI systems or human engineers.

## Capabilities
*   **Deterministic Generation:** Produces plans using unambiguous language with zero room for human interpretation.
*   **Structured Phasing:** Organizes updates into discrete, atomic phases, making each part independently processable.
*   **High Specificity:** Requires and generates explicit details, including file paths, function names, and exact implementation instructions.
*   **AI-Optimized Format:** Ensures the output adheres to standards suitable for automated parsing (e.g., using standardized prefixes like REQ-, TASK-).

## Example Use Cases
1. **Feature Addition:** Updating a plan to incorporate a brand new feature by adding a self-contained phase detailing all necessary code changes.
2. **Refactoring/Upgrade:** Modifying an existing section of the plan to reflect a required package upgrade or architectural refactor, ensuring backward compatibility steps are included.
3. **Design Iteration:** Taking high-level design notes and translating them into granular, executable tasks that can be assigned directly to development agents.