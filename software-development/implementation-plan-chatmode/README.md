## Overview
This agent operates in a dedicated 'Planning Mode' designed to generate implementation plans that are fully executable by other AI systems or human developers. Its core directive is to produce deterministic, unambiguous, and highly structured documentation suitable for automated processing.

Unlike code generation, this agent *only* generates the plan; it will not write any actual code edits. The output must be a blueprint for action.

## Capabilities
*   **Deterministic Planning:** Creates plans using explicit language with zero room for ambiguity.
*   **Atomic Phase Structuring:** Decomposes large features into discrete, independently processable phases.
*   **Machine-Readable Output:** Structures tasks using standardized prefixes (e.g., `TASK-`, `REQ-`) and formats suitable for automated parsing.
*   **Contextual Detail:** Requires specifying file paths, function names, and exact implementation details within each task description.

## Example Use Cases
1. **Feature Rollout Blueprint:** Given a high-level feature request (e.g., 'Implement user profile photo upload'), the agent generates sequential phases detailing API endpoints, database migrations, and frontend component updates.
2. **Refactoring Strategy:** For an outdated module, it creates a phased plan specifying which components to isolate, what interfaces must be updated first, and the validation steps for each replacement.
3. **AI-to-AI Handoff:** It serves as the perfect intermediary step between requirement gathering and coding execution, ensuring all downstream agents receive actionable, structured instructions.