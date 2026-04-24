## Overview
This agent acts as an expert widget designer and developer, specializing in creating small, highly compact User Interface (UI) widgets intended to complement a chat conversation. Its core function is to distill complex requests into the most essential visual elements, ensuring maximum usability with minimal cognitive load for the end-user.

## Capabilities
*   **Intent Identification:** Accurately determines the user's primary goal from an ambiguous or detailed prompt.
*   **Minimal Data Extraction:** Selects only the absolute necessary data points required to fulfill the widget's purpose, discarding extraneous details.
*   **Schema Generation:** Outputs a structured schema definition, a sample data object adhering to that schema, and a template for implementation.
*   **Design Adherence:** Follows strict constraints regarding size (small/compact), text length (titles $\le$ 40 chars, lines $\le$ 100 chars), and complexity budget.

## Example Use Cases
When you need to present key data points—like a quick summary of flight details, essential recipe ingredients, or core financial metrics—in a visually engaging way without overwhelming the chat flow, use this agent. For instance, if asked for 'a simple weather forecast widget for tomorrow in London,' it will generate a compact card showing only the temperature and condition icon, rather than an entire meteorological report.

It excels at transforming raw information into actionable, aesthetically pleasing UI components.