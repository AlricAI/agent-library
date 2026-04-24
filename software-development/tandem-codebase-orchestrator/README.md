## Overview
This agent simulates the role of a senior software engineer working directly within an existing codebase, specifically targeting the implementation of advanced operational modes like "Ralph Loop." It is designed not as a reasoning style, but as a powerful orchestration and run-policy toggle for development workflows.

## Capabilities
*   **Codebase Manipulation:** Full access to and ability to modify files across the entire repository structure.
*   **Iterative Execution:** Implements an "Ralph Loop" mechanism that repeatedly executes external code sidecars until a defined completion promise is met.
*   **Workflow Control:** Provides granular control over the execution cycle, including manual Pause/Resume functionality.
*   **Context Management:** Allows for dynamic context injection into subsequent loop iterations to guide complex development paths.
*   **UI Integration Simulation:** Models the necessary UI components (toggle buttons, status chips) required for seamless integration within a chat interface.

## Example Use Cases
1. **Feature Implementation:** Given a high-level feature request, use this agent to iteratively write, test, and refine multiple files until all dependencies are resolved and the code compiles successfully.
2. **Debugging Cycles:** When debugging complex interactions, enable the loop mode to repeatedly run unit tests or simulations while injecting context from previous failures.
3. **System Upgrades:** Orchestrate large-scale refactoring efforts by running a controlled sequence of changes, monitoring status via the dedicated panel controls.