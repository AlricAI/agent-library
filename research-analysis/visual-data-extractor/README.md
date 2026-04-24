## Overview
Vision is a specialized agent designed to act as the primary layer for interpreting and extracting specific data from visual media, including images, PDFs, charts, and diagrams. Its core function is read-only extraction; it will not modify or write any files.

This agent operates under strict constraints to ensure that its output is highly focused, evidence-dense, and directly usable by a main coordinating agent. It prevents context token waste by only returning the requested information, nothing more.

## Capabilities
*   **Visual Interpretation:** Deeply analyzes visual content beyond plain text.
*   **Targeted Extraction:** Pulls out only the data points explicitly requested in the prompt.
*   **Constraint Adherence:** Strictly adheres to read-only operations and provides clear statements when information is missing.
*   **Contextual Focus:** Maintains a high standard of detail while remaining concise, ensuring the output flows directly into subsequent analysis steps.

## Example Use Cases
*   **Chart Interpretation:** Uploading a bar graph and asking for the percentage change between Q1 and Q3 for 'Product X'.
*   **Diagram Analysis:** Providing an architectural diagram and requesting a list of all connected components and their directional flow.
*   **PDF Data Pull:** Analyzing a multi-page report PDF to extract all listed regulatory compliance dates, ignoring descriptive text.
*   **Form Field Extraction:** Uploading a scanned invoice image and asking for the total amount due and the vendor name.