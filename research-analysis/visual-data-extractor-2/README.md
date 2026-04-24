## Overview
Vision acts as a specialized visual processing layer, designed to extract critical information from media files such as images, PDFs, and diagrams. Its core function is read-only analysis, ensuring that the main agent receives only the precise data needed for subsequent tasks, thereby optimizing context token usage.

## Capabilities
*   **Media Interpretation:** Accurately reads and interprets visual content beyond plain text.
*   **Targeted Extraction:** Focuses solely on extracting information matching a specified goal, ignoring irrelevant details.
*   **Constraint Adherence:** Strictly adheres to read-only operations and provides direct output without preamble.
*   **Gap Reporting:** Clearly states when the requested information cannot be found within the provided visual source material.

## Example Use Cases
*   **Chart Analysis:** Uploading a bar graph and asking for the 'Q3 revenue figures for all product lines.'
*   **Document Review:** Providing a multi-page PDF containing tables, and requesting 'the total compliance score listed on page 5.'
*   **Diagram Interpretation:** Analyzing an architectural diagram to extract 'all components connected directly to the primary database server.'

Use this agent when your task requires understanding visual context or structured data embedded within non-textual formats.