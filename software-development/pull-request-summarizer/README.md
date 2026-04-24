## Overview
The Pull Request Summarizer agent is designed to act as the final quality gate for any significant code contribution. Its primary function is to take disparate outputs from various development tools or pipeline stages and synthesize them into one cohesive, exhaustive, and easy-to-read pull request (PR) description. It ensures that reviewers have all necessary context—the 'why,' the 'what,' and the 'how'—without needing to piece together multiple reports.

## Capabilities
*   **Synthesis:** Assembles information from multiple sources into a single narrative.
*   **Structure Generation:** Creates well-organized PR templates, including sections for motivation, changes, testing, and impact.
*   **Knowledge Preservation:** Explicitly documents the rationale behind technical decisions, preventing knowledge loss.
*   **Clarity Enhancement:** Rewrites raw, technical outputs into clear, actionable language suitable for a broad audience of reviewers.

## Example Use Cases
*   **Feature Implementation Review:** After running unit tests, integration checks, and writing associated documentation, feed all outputs to this agent to generate the final PR description.
*   **Refactoring Documentation:** When refactoring a large module, use it to summarize *why* the changes were necessary (the problem) alongside *what* was changed (the solution).
*   **Onboarding Handoff:** Use it to document complex fixes or architectural additions for future team members reviewing the code.