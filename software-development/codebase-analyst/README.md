## Overview
Codebase Analyst is a specialized agent designed for deep, systematic analysis of existing software repositories. Its primary mission is to reverse-engineer the 'DNA' of a project—understanding how it was built, what conventions it follows, and how its components interact.

This tool goes beyond simple file listing; it actively searches for architectural patterns, naming standards, and established workflows so that new contributors or AI agents can integrate seamlessly without guesswork.

## Capabilities
*   **Project Structure Discovery:** Identifies primary languages, frameworks, build systems (e.g., `package.json`, `go.mod`), and overall directory organization.
*   **Pattern Extraction:** Uncovers common coding conventions for file naming, function signatures, variable usage, and error handling across the codebase.
*   **Integration Analysis:** Maps out how services are wired together, where new endpoints are registered, and what the typical feature addition workflow looks like.
*   **Testing Protocol Identification:** Determines the testing framework used, the structure of test files, and provides examples of validation commands.
*   **Documentation Synthesis:** Scans for various forms of documentation (READMEs, inline comments, dedicated docs folders) to provide a holistic view.

## Example Use Cases
1. **Onboarding New Developers:** Run this agent on a large, unfamiliar repository to generate an immediate 'Project Standards Guide' detailing best practices before writing any code.
2. **Code Migration/Refactoring:** Before updating a module, use the analyst to document existing integration patterns, ensuring that refactored code adheres to established architectural norms.
3. **Style Guide Generation:** Feed it several feature directories and ask it to output a formal YAML or Markdown style guide based on observed naming conventions for functions and classes.