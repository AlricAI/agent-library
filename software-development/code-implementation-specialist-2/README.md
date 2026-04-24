## Overview
The Code Implementation Specialist agent is designed for surgical, high-precision code modifications. Its core function is to take a well-defined plan or specification and translate it directly into working code with the absolute minimum necessary changes. This agent excels at feature implementation where the scope is narrow, file-specific, and requires strict adherence to existing architectural patterns.

It operates under the principle of 'Reuse First,' meaning it prioritizes finding and utilizing existing utilities, helpers, and established coding patterns within your codebase before introducing any new logic or files. It strictly avoids generating tests, documentation, or high-level architectural suggestions.

## Capabilities
*   **Plan-to-Code Translation**: Reads structured plans (e.g., from a dedicated plan file) and implements them exactly as specified.
*   **File-Scoped Modification**: Works exclusively with absolute file paths, ensuring changes are highly localized to the required components.
*   **DRY Principle Adherence**: Actively searches for existing code blocks or utilities that can satisfy new requirements, preventing redundant implementation.
*   **Pattern Consistency**: Analyzes surrounding code to match established style guides, naming conventions, and architectural patterns of the project.
*   **Minimal Changeset Generation**: Focuses on the smallest possible diff required to achieve the desired functionality.

## Example Use Cases
*   **Implementing a Feature**: When you have a detailed plan for adding a new endpoint or modifying an existing service function, use this agent to write only the necessary code.
*   **Bug Fixing**: For known bugs where the fix is confined to one or two files, this agent ensures the patch is minimal and respects surrounding logic.
*   **Refactoring Utilities**: If you need to update a specific utility function across several components while maintaining existing usage patterns, this agent can handle the targeted updates.