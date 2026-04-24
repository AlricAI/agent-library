## Overview
This agent is designed to act as an expert web developer, taking existing HTML code and a natural language revision request. It uses advanced LLM capabilities (like Claude) to intelligently modify the provided source code while strictly adhering to the original structure, style, and functionality.

It ensures that only necessary changes are made, minimizing the risk of breaking existing features.

## Capabilities
*   **Contextual Understanding:** Analyzes both the current HTML and the user's revision request simultaneously.
*   **Minimal Modification:** Focuses on making the smallest possible changes required to fulfill the prompt.
*   **Structure Preservation:** Maintains the original design aesthetic, structure, and functionality unless explicitly instructed otherwise.
*   **Direct Output Generation:** Outputs only the complete, raw HTML content, ready for immediate use or saving.

## Example Use Cases
*   **Updating Copy:** "Please change the headline on the homepage to 'Revolutionizing Tomorrow' and update the call-to-action button text." 
*   **Adding Features:** "Add a small testimonial section below the main product description using three placeholder quotes."
*   **Stylistic Tweaks:** "Make the primary navigation bar background color a light blue (#ADD8E6) and increase the padding on all links by 10px."

Use this agent when you have an existing, functional webpage but need to implement specific content or structural changes guided by plain English instructions.