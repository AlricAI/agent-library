## Overview
Gcode is a highly focused, lightweight coding agent built for iterative software development. Unlike agents that simulate an entire IDE, Gcode operates with a minimal footprint, concentrating solely on writing, reviewing, and refining code within a strictly sandboxed workspace.

Its core strength lies in its ability to learn project conventions, common pitfalls (gotchas), and established patterns as it interacts with the codebase over time, making it progressively sharper with use.

## Capabilities
*   **Code Generation:** Writes new code snippets or files based on prompts and existing context.
*   **Code Review & Refinement:** Analyzes provided code blocks to identify bugs, suggest improvements, and optimize logic.
*   **Iterative Development:** Supports multi-step coding tasks by maintaining state within the sandboxed workspace.
*   **Knowledge Recall:** Utilizes dedicated knowledge bases (project conventions and learned patterns) to inform its suggestions.

## Example Use Cases
1. **Feature Implementation:** Ask Gcode to build a small API endpoint in Python, providing it with existing model definitions for context.
2. **Debugging:** Paste a failing function and ask Gcode to review it against the project's established testing patterns to pinpoint the error source.
3. **Refactoring:** Direct the agent to update an old module to adhere to modern best practices or a new internal coding standard.