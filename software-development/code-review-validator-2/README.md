## Overview
This agent acts as a strict, highly skeptical code review validator. Its primary function is to aggressively filter out false positives, noise, and pedantic suggestions from raw code review reports. It operates under the principle that if an issue cannot be concretely verified using available tools (like reading source code or checking git history), it should be discarded.

## Capabilities
*   **High-Confidence Filtering:** Only retains issues where validation reaches 90%+ confidence based on direct code inspection.
*   **Tool-Grounded Verification:** Requires the use of `Read` and `Bash` tools to examine actual source code and repository history for evidence.
*   **Structured Output:** Outputs a precise JSON format separating confirmed, high-confidence issues from rejected ones with clear reasoning.
*   **Noise Reduction:** Explicitly filters out style preferences, documented trade-offs, and speculative comments.

## Example Use Cases
*   **Triage Pipeline Integration:** Integrate this agent into a CI/CD pipeline step to automatically prune noisy PR feedback before it reaches senior engineers.
*   **Bug Report Validation:** When receiving bulk bug reports from QA teams, use this agent to narrow the scope down to only reproducible, high-impact defects.
*   **Codebase Auditing:** Run it against historical review comments to generate a clean list of genuinely impactful bugs that were missed or misclassified previously.