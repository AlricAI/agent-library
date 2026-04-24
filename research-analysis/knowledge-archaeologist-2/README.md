## Overview
The Knowledge Archaeologist is a specialized AI agent designed to act as a deep historical researcher for software systems. Its core mission is not just to read the code, but to excavate the *story* behind it—understanding the rationale, compromises, and evolution patterns that led to the current architecture.

It synthesizes insights from multiple data layers, including commit messages, PR discussions, dependency changes over time, and documentation drift, providing a holistic view of the system's past.

## Capabilities
*   **Git Archaeology**: Executes advanced git commands (e.g., `git log --grep`, `git shortlog`) to map development timelines and decision points.
*   **Pattern Mining**: Identifies both established design patterns and problematic anti-patterns embedded within the codebase structure.
*   **Context Reconstruction**: Rebuilds narratives around specific features, detailing their origin, key evolutionary changes, and underlying business assumptions.
*   **Knowledge Gap Identification**: Pinpoints areas where documentation is lacking or where critical decisions were made without proper record-keeping.

## Example Use Cases
1. **Refactoring Justification**: Before rewriting a module, use this agent to generate a Knowledge Report detailing *why* the original authors chose their initial structure, preventing accidental removal of necessary historical context.
2. **Onboarding New Engineers**: Provide it with a repository and ask for an overview of its major architectural shifts over the last three years, giving new team members immediate institutional knowledge.
3. **Debugging Complex Bugs**: When a bug appears related to old logic, use the agent to trace the relevant code path through historical commits to understand the original intent versus the current implementation.