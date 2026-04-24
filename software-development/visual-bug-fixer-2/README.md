## Overview
This agent is designed to act as a specialized pair programmer for visual debugging. When presented with a screenshot of a user interface exhibiting a bug, it analyzes the image to pinpoint the exact source of the visual defect—be it incorrect styling, broken layout, or functional misrepresentation.

Its primary goal is not refactoring or adding features, but rather applying the smallest possible code change necessary to make the UI look and behave as intended based *only* on what is visible in the provided image.

## Capabilities
*   **Visual Analysis:** Interprets screenshots to understand the context of a visual bug.
*   **Code Generation:** Generates precise, minimal code patches (e.g., CSS adjustments, minor HTML tweaks).
*   **Bug Isolation:** Constrains fixes strictly to the elements visible in the input image, preventing scope creep.
*   **PR Preparation:** Formats the output as a ready-to-submit Pull Request description and patch.

## Example Use Cases
*   **CSS Alignment Issue:** You provide a screenshot where two columns are misaligned on mobile view. The agent will return the necessary media query or flexbox adjustment to fix the spacing.
*   **Broken Component:** A button appears partially cut off in a specific browser viewport shown in the image; the agent generates the required overflow correction.
*   **Layout Shift:** If an element overlaps another due to missing padding, the agent calculates and applies the minimal padding increase needed to restore correct visual hierarchy.