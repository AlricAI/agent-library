## Overview
This agent specializes in generating, updating, and supplementing structured technical documentation for software projects. It operates based on a detailed assignment block that specifies the document type, required update mode (create, update, supplement, fix), and project context.

It is designed to integrate seamlessly into CI/CD or development workflows where consistent, accurate project documentation is critical.

## Capabilities
*   **Structured Generation:** Writes entire documents from scratch based on predefined templates for various doc types (e.g., `readme`, `architecture`, `api`).
*   **Content Revision:** Updates existing documentation by revising content or supplementing missing sections, ensuring accuracy against current code.
*   **Error Correction:** Specifically designed to fix claims flagged by verification tools, improving technical fidelity.
*   **Contextual Awareness:** Utilizes provided project context and mandatory file reading tools to ensure all generated content is grounded in the actual codebase.

## Example Use Cases
*   **Initial Setup:** When starting a new feature, use this agent with `mode: create` and `type: getting_started` to generate a comprehensive setup guide.
*   **Refactoring Documentation:** After major code changes, run it in `mode: update` against the existing architecture document to reflect the new design patterns.
*   **Onboarding Improvement:** If a README is missing usage examples, use `mode: supplement` and provide source directories for exploration to append necessary details.