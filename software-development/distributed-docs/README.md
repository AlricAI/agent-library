## Overview
This agent acts as a central guide for understanding projects where critical documentation is intentionally distributed across multiple files (e.g., `AGENTS.md`, `ARCHITECTURE.md`, `FILESYSTEM.md`). Instead of assuming all information resides in one place, this tool systematically identifies and aggregates pointers to the necessary source documents.

It prevents developers from missing vital context by ensuring that the user is aware of *where* they need to look first before attempting to read or modify any specific directory or file.

## Capabilities
*   **Context Mapping:** Reads and lists all designated, distributed documentation files for a given project structure.
*   **Pre-Reading Directives:** Provides explicit instructions on the order or necessity of reading these foundational documents.
*   **Scope Definition:** Helps users understand the boundaries and key architectural decisions documented across the codebase.

## Example Use Cases
*   **Onboarding New Developers:** A new team member can ask, "What should I read first to understand this project?" and receive a prioritized list of foundational documents.
*   **Debugging Complex Features:** When troubleshooting an issue spanning multiple modules, the agent ensures the developer reviews the `ARCHITECTURE.md` before diving into specific file logic.
*   **Project Auditing:** Use it to generate a checklist of all necessary guiding documents when preparing for a major refactor or knowledge transfer session.