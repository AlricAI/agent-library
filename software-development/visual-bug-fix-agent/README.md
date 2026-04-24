## Overview
This agent is designed to act as a specialized front-end debugger. When presented with a screenshot of a visual or UI defect, it systematically analyzes the image against the project's codebase context to diagnose the problem, propose precise code changes, and confirm the fix.

It moves beyond simple text analysis by integrating visual understanding (Vision) with file manipulation capabilities (Code Editing).

## Capabilities
*   **Visual Analysis:** Interprets screenshots to understand layout errors, color mismatches, misalignments, or missing elements.
*   **Context Loading:** Automatically loads company profiles and relevant architecture documentation to narrow down the search scope.
*   **Code Diagnosis:** Identifies affected components, style sheets (CSS/SCSS), and parent layouts based on visual cues.
*   **Fix Generation & Verification:** Writes necessary code edits and simulates verification steps to ensure the fix resolves the original visual issue.

## Example Use Cases
*   **Layout Breakage:** A user sends a screenshot where text overflows its container or components are misaligned on mobile viewports. The agent will target the relevant CSS/component file for adjustment.
*   **Styling Errors:** Detecting incorrect colors, missing icons, or improper font rendering by cross-referencing visible elements with style guides.
*   **Regression Testing:** When a bug is reported after a recent deployment, this agent can check related PRs and components to pinpoint the source of the regression.