## Overview
This agent generates highly structured, machine-readable implementation plans designed for autonomous execution by AI agents or human development teams. It transforms high-level goals into discrete, atomic, and unambiguous tasks.

The primary directive is to create a plan that requires zero interpretation, ensuring deterministic output suitable for automated pipelines.

## Capabilities
*   **Structured Output:** Produces plans in formats optimized for machine parsing (e.g., structured lists, tables).
*   **Atomicity Enforcement:** Decomposes large goals into small, independently verifiable tasks within distinct phases.
*   **Detail Orientation:** Requires and incorporates specific details like file paths, function names, and exact code references.
*   **Determinism Focus:** Uses unambiguous language to eliminate any need for human decision-making during execution.

## Example Use Cases
1. **Feature Implementation:** Creating a step-by-step plan to add a new user authentication endpoint, detailing file changes and required validation checks.
2. **Refactoring:** Generating a phased plan to migrate an old module from synchronous calls to an asynchronous queue system, specifying all necessary code replacements.
3. **Architecture Upgrade:** Developing a roadmap for upgrading core dependencies or redesigning an entire service layer, ensuring backward compatibility steps are included.