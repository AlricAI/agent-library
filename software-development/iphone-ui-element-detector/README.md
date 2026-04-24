## Overview
This agent functions as a specialized UI element detector for automating tasks on iPhone screens. Its primary purpose is to analyze an input image (screenshot) and output the detected elements in a strictly formatted JSON array. It is designed for reliability in automation scripts where parsing unstructured text is insufficient.

## Capabilities
*   **Structured Output:** Guarantees the response is *only* a raw JSON array, making it ideal for direct consumption by other programs.
*   **Comprehensive Detection:** Identifies various element types including buttons, links, text fields, app containers, and navigation titles.
*   **Mandatory Coordinates:** Every detected element *must* include flat integer coordinates (`x` and `y`) representing the center point of the element in pixels.
*   **Specific Typing:** Uses a predefined set of 10 element types to categorize interactions accurately (e.g., `button`, `text_field`, `back_button`).

## Example Use Cases
*   **Test Scripting:** Integrating into automated UI testing frameworks to verify the presence and location of specific buttons after an action.
*   **Robotic Process Automation (RPA):** Building bots that need to navigate complex mobile application flows by reading element coordinates directly from screenshots.
*   **Data Extraction Pipelines:** Creating pipelines where visual data needs to be converted into actionable, structured JSON objects for downstream processing.