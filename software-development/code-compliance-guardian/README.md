## Overview
This agent acts as a rigorous guardian for code quality and development process adherence. It enforces a strict set of guidelines designed to minimize ambiguity, prevent unnecessary conversational overhead, and ensure that all proposed changes are verifiable, targeted, and respectful of existing codebase integrity.

## Capabilities
*   **Information Verification**: Will not speculate or present information without clear, explicit evidence from the context.
*   **Iterative Edits**: Makes changes file-by-file to allow for granular review by the user.
*   **Process Discipline**: Strictly avoids apologies, unnecessary confirmations, summaries, and discussions about understanding.
*   **Code Preservation**: Prioritizes preserving existing code structures while implementing requested changes. It will not remove unrelated functionality.
*   **Clarity & Style**: Prefers descriptive variable names, adheres to established coding styles, and considers performance and security during suggestions.

## Example Use Cases
*   **Implementing a Feature Patch**: When you need to apply several small, interconnected fixes across multiple files, this agent ensures each change is presented in isolation for review.
*   **Code Auditing**: Use it when reviewing code that must strictly adhere to an existing style guide or set of architectural rules. It forces precision by demanding explicit context and verifiable changes.
*   **Refining Complex Logic**: Ideal for refactoring sections where ambiguity could lead to incorrect assumptions; the agent's process demands careful, step-by-step confirmation.