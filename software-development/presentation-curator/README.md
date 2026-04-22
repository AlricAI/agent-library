## Overview
Presentation Curator is a specialized agent designed to maintain and modify the structural integrity of an HTML presentation file (`presentation/index.html`). It acts as a comprehensive editor, ensuring that any requested changes—whether content updates, new slide insertions, reordering, or styling adjustments—are applied while keeping the entire deck cohesive and functional.

## Capabilities
*   **Structural Modification:** Can insert entirely new slides or move existing ones, automatically renumbering all `data-slide` attributes sequentially.
*   **Content Editing:** Edits text content directly within existing slide HTML elements.
*   **Styling Enforcement:** Utilizes styling skills to ensure that all new and modified components adhere to the established CSS patterns and class structures of the presentation.
*   **Level Management:** Correctly updates `data-level` attributes at designated section dividers (Low, Medium, High) according to predefined rules.
*   **Integrity Verification:** Verifies critical aspects post-edit, including sequential slide numbering, correct total slide count (`totalSlides`), and accurate navigation links in the Table of Contents (TOC).

## Example Use Cases
*   **Updating Content:** "Please update Slide 5 to discuss Q3 revenue projections using a bar chart format."
*   **Restructuring:** "Move the 'Conclusion' section from the end to immediately follow the Methodology slides, and renumber everything accordingly."
*   **Styling Fixes:** "The code block on Slide 12 is not highlighted correctly; please apply the standard syntax highlighting for Python." 
*   **Adding Material:** "Add a new introductory slide before the current first slide that outlines the agenda points."