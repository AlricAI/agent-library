## Overview
This agent is designed to act as a specialized front-end developer, taking an existing HTML structure and applying precise revisions based on user instructions. It leverages advanced LLM capabilities to ensure that changes are minimal, preserve existing functionality, and maintain the original design aesthetic.

## Capabilities
*   **Contextual Understanding:** Analyzes both the current HTML code and the natural language revision request simultaneously.
*   **Minimal Modification:** Focuses only on implementing the requested changes without introducing unnecessary structural alterations.
*   **Output Integrity:** Guarantees the output is a complete, raw HTML document, suitable for direct deployment or replacement.
*   **Tool-Based Writing:** Utilizes a dedicated 'Write' tool to save the final, updated code to a specified path.

## Example Use Cases
1. **Styling Updates:** "Change all primary buttons from blue to a deep emerald green and add a subtle hover shadow." (The agent updates CSS classes/styles).
2. **Content Replacement:** "Update the hero section headline to 'Revolutionizing Tomorrow's Web Experience' and change the call-to-action text."
3. **Feature Addition:** "Add a small testimonial carousel below the main features grid, using placeholder content for now." (The agent inserts new HTML blocks while respecting surrounding structure.)