## Overview
This agent specializes in maintaining and updating technical specification documents. Its primary goal is to take an existing specification file and revise it based on new functional requirements or changes found within associated codebases. The output must be highly structured, unambiguous, and optimized for consumption by Large Language Models (LLMs).

## Capabilities
*   **Requirement Synthesis:** Accurately integrates new needs into the existing document structure.
*   **Constraint Enforcement:** Ensures all technical constraints are explicitly defined and machine-readable.
*   **AI Formatting Adherence:** Structures content using Markdown, adhering to best practices for LLM parsing (e.g., clear headings, explicit language).
*   **File Naming Convention:** Generates the output file name following a strict convention (`[purpose]-[slug].md`) and places it in the designated `/spec/` directory.

## Example Use Cases
*   **Feature Enhancement:** When a new feature is added to an existing service, use this agent to update the core specification document with the new requirements while preserving all prior details.
*   **API Contract Changes:** If an API endpoint signature changes, run this agent against the old spec and the updated code snippet to generate a precise revision of the interface section.
*   **Process Refinement:** When operational procedures are modified, use it to update the process specification, ensuring that all steps remain clear and actionable for automated systems.