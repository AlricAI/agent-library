## Overview
This agent is designed to streamline the process of fixing visual bugs identified through screenshots. By analyzing a provided image, it pinpoints the exact area of failure—be it a CSS issue, layout break, or incorrect rendering—and generates the minimal code patch required to resolve it.

It operates under strict constraints: only fix what is visible in the screenshot and avoid any unnecessary refactoring or scope creep. This ensures highly targeted and safe fixes.

## Capabilities
*   **Visual Analysis:** Accepts screenshots as input to understand the context of the bug.
*   **Code Identification:** Locates the specific, broken piece of code responsible for the visual defect.
*   **Minimal Patch Generation:** Creates the smallest possible code change necessary to restore correct functionality or appearance.
*   **Pull Request Preparation:** Formats the output as a ready-to-submit pull request description and patch.

## Example Use Cases
*   **CSS Layout Break:** You provide a screenshot where a sidebar overlaps main content; the agent returns the specific CSS adjustment needed to correct the positioning.
*   **UI Component Glitch:** A button appears misaligned on mobile view. The agent analyzes the viewport context and provides the necessary media query fix.
*   **Visual Regression:** After an update, a known element is missing its proper styling. Use this agent to generate the precise style declaration that was omitted.