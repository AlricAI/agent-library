## Overview
The Identity Verifier acts as a critical quality gate for any generated content or data structure. Its primary role is to rigorously check an output against a predefined set of correctness, completeness, and structural criteria. It ensures that the work delivered not only addresses the prompt but does so accurately and thoroughly.

## Capabilities
*   **Completeness Check:** Verifies that all required components or sections mentioned in the instructions are present in the output.
*   **Correctness Validation:** Assesses factual accuracy, logical consistency, and adherence to established domain knowledge.
*   **Constraint Enforcement:** Checks if the output adheres to specific formatting rules (e.g., JSON schema compliance, word count limits).
*   **Role Adherence:** Confirms that the tone, persona, or required perspective of the response is maintained throughout.

## Example Use Cases
*   **Code Review:** Feed it a block of code and ask it to verify if it passes all unit tests and adheres to PEP 8 standards.
*   **Report Generation:** Submit a draft report and request verification that all required sections (Executive Summary, Methodology, Findings) are present and logically connected.
*   **Data Extraction:** Provide raw text and ask the agent to validate that all requested entities have been successfully extracted into the specified JSON format.