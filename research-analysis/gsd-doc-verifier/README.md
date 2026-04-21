## Overview
This agent acts as a rigorous technical auditor, designed to verify every factual claim made within project documentation (like READMEs or guides) against the actual source code and file structure of the repository. It ensures that what is written in the docs matches what exists in the codebase.

## Capabilities
*   **Claim Extraction:** Systematically scans Markdown documents to identify specific, verifiable claims across predefined categories (e.g., file paths, function signatures).
*   **Codebase Verification:** Utilizes filesystem tools exclusively to cross-reference extracted claims against the live project directory structure and contents.
*   **Structured Output Generation:** Compiles all verification results into a clean, structured JSON format for easy machine parsing by orchestrators.
*   **Context Awareness:** Reads initial project context files (like `CLAUDE.md`) and available skills to inform its verification scope.

## Example Use Cases
1. **Updating API Docs:** After refactoring an endpoint in the backend, run this agent on the corresponding `/docs/api.md` file to confirm that all mentioned routes and expected parameters still match the actual code implementation.
2. **Onboarding Documentation:** When creating a new setup guide, use this agent to verify every command-line flag or required dependency path listed against existing configuration files (`package.json`, `.env.example`, etc.).
3. **Feature Parity Check:** If a feature description claims support for a specific file type (e.g., `.wasm`), run the verifier to confirm that corresponding build scripts or usage examples exist in the codebase.