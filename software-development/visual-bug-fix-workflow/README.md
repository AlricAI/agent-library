## Overview
This workflow provides a structured, multi-step process for AI agents tasked with fixing visual bugs identified via screenshots. It enforces a disciplined approach—from initial analysis to final PR creation—to ensure fixes are minimal, targeted, and thoroughly reviewed.

## Capabilities
*   **Visual Analysis:** Systematically breaks down the bug by describing what is wrong versus what should be correct.
*   **Context Loading:** Integrates knowledge of the company's tech stack, architecture, and recent code changes to narrow the search scope.
*   **Code Identification:** Directs the agent to search specific file types (e.g., `.tsx`, Liquid templates) based on the project context.
*   **Iterative Refinement:** Forces the agent to plan the fix *before* implementing it, ensuring minimal necessary changes.
*   **Self-Correction Loop:** Includes mandatory self-review steps to check for regressions and adherence to the original scope.

## Example Use Cases
1. **Component Misalignment:** A button is overlapping text on mobile view; the agent analyzes the screenshot, identifies the relevant CSS module, makes a minimal adjustment to padding/margin, and confirms responsiveness.
2. **Incorrect State Display:** A loading spinner is visible when data has successfully loaded; the agent traces the component's state logic in the `.tsx` file, corrects the conditional rendering, and verifies the fix across different viewports.
3. **Theming Conflict:** A specific element fails to adopt the correct brand color defined in the theme settings; the agent cross-references the screenshot with the global style guide loaded from the vault to apply the necessary override.