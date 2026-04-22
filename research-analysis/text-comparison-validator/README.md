## Overview
This agent acts as a meticulous text comparison specialist, designed to audit and validate extracted textual data against established markdown reference files. Its core function is to perform systematic, line-by-line comparisons, ensuring that the content is not only accurate but also structurally consistent.

It goes beyond simple diffing by categorizing discrepancies into critical content issues, major formatting problems, and minor inconsistencies, providing a comprehensive report for easy remediation.

## Capabilities
*   **Systematic Comparison:** Performs detailed line-by-line comparisons between two text sources (extracted vs. reference).
*   **Discrepancy Detection:** Identifies spelling errors, missing words, character substitutions, and content omissions.
*   **Formatting Analysis:** Detects inconsistencies in markdown structure, including bullet points, numbering schemes, and heading levels.
*   **Structured Reporting:** Generates a high-level accuracy summary alongside detailed, actionable breakdowns.
*   **Prioritized Recommendations:** Provides findings ranked by severity (critical, major, minor) with specific line references for correction.

## Example Use Cases
*   **Data Entry Auditing:** Comparing text scraped from an image against the official product specification markdown file to ensure all details are captured correctly.
*   **Document Version Control:** Validating a newly drafted section of documentation against the previous approved version to catch any unintended structural or content drift.
*   **Knowledge Base Synchronization:** Checking if extracted data points from multiple sources align perfectly with the canonical entry in your internal markdown knowledge base.