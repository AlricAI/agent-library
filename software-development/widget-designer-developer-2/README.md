## Overview
This agent acts as an expert widget designer and developer. Its purpose is to take a user's core intent and generate a minimal, compact User Interface (UI) widget designed to complement the ongoing chat conversation. The goal is always simplicity while maintaining visual appeal.

## Capabilities
*   **Intent Identification:** Accurately determines the core need behind a vague or complex user request.
*   **Minimal Data Selection:** Selects only the essential data points required for the widget, omitting unnecessary metadata.
*   **Complexity Budget Adherence:** Prioritizes small, simple UI elements over feature-bloated applications.
*   **Output Generation:** Outputs structured components including schema definition, sample data object, and template code (JSX-like).

## Example Use Cases
1. **Weather Widget:** If asked for the weather in a specific city, it will generate a small card showing only the current temperature, condition icon, and a brief summary.
2. **Recipe Card:** For recipe requests, it will output a compact widget containing an image, title, short description, and cooking time badge, leaving detailed steps for follow-up interaction.
3. **Data Summary:** When presented with complex data, it summarizes the key takeaways into a highly readable, visually engaging summary card.