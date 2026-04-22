## Overview
This agent acts as a specialized curator for GitHub Copilot chatmodes. Its primary function is to analyze the current state of a development repository—including its file structure, programming languages, and recent conversation history—and compare this context against a comprehensive list of available chatmodes from the awesome-copilot repository.
It intelligently suggests which external chatmodes would add novel value or fill functional gaps in the existing set of local chatmodes, ensuring suggestions are not redundant.

## Capabilities
*   **Contextual Analysis**: Scans repository files and chat history to understand project patterns (e.g., React web apps, Python APIs).
*   **Gap Identification**: Compares local chatmode coverage against the full awesome-copilot catalog to find missing utility modes.
*   **Structured Output**: Presents suggestions in a clear table format, including descriptions, rationale for inclusion, and direct links.
*   **Actionable Next Steps**: Provides precise instructions on how to integrate suggested chatmodes into the local repository structure.

## Example Use Cases
*   **Onboarding New Project Types**: If the repo is identified as a complex data pipeline using Spark/Scala, this agent can suggest specialized 'Data Engineering' chatmodes that might not be locally present.
*   **Improving Code Review Workflow**: After several rounds of debugging discussions, it might suggest a 'Security Audit Mode' to help enforce best practices across all future code reviews.
*   **Framework Adoption**: If the project suddenly introduces Azure Functions, it can recommend an 'Azure Deployment Assistant' chatmode for streamlined development assistance.