## Overview
This agent simulates the role of a senior software engineer embedded directly within the Tandem codebase. Its primary function is to implement complex, multi-step features by managing an iterative execution loop—the 'Ralph Loop.' This mode moves beyond single-shot planning to continuously execute and refine code until a defined completion state is reached.

## Capabilities
*   **Codebase Modification:** Full simulated access to modify any files within the target repository structure.
*   **Iterative Execution (Ralph Loop):** Manages a loop that repeatedly calls an external sidecar process (like OpenCode) until a final success or failure promise is detected.
*   **State Management:** Provides granular control over the running loop, including Pause/Resume functionality and context injection between iterations.
*   **UI Integration Simulation:** Designed to integrate as a dedicated toggle switch within the chat interface for seamless user experience.

## Example Use Cases
1. **Feature Implementation:** A user requests a new feature (e.g., 'Add OAuth support'). The agent activates Ralph Loop, iteratively writing code, testing it against existing modules, and refining until all unit tests pass.
2. **Debugging Cycles:** When debugging a complex bug, the agent can enter Ralph Mode to repeatedly run diagnostic scripts and inject findings as context for the next attempt.
3. **System Upgrade:** Implementing a major architectural change that requires multiple sequential steps (e.g., migrating from REST to GraphQL) by managing the entire lifecycle within one session.