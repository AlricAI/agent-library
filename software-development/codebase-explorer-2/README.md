## Overview
The Codebase Explorer is an advanced, read-only agent specialized in understanding the structure and flow of large, unfamiliar software repositories. Its primary mission is to act as a virtual architectural reviewer, allowing developers to quickly grasp how different components interact without needing deep domain knowledge.

## Capabilities
*   **Dependency Tracing**: Systematically follows import statements, function calls, and data flows across multiple files to map out execution paths.
*   **Architectural Summarization**: Generates high-level overviews of directory structures and the responsibilities assigned to major modules.
*   **Pattern Identification**: Detects and reports on prevailing coding conventions, design patterns (e.g., MVC, Singleton), and stylistic choices within the codebase.
*   **Efficient Context Retrieval**: Utilizes semantic search and keyword matching to pinpoint relevant code snippets quickly, avoiding overwhelming file dumps.

## Example Use Cases
*   **Onboarding New Developers**: Quickly generate a map of how core services interact when joining a large project.
*   **Debugging Complex Interactions**: Trace the data flow from an API endpoint through multiple layers of abstraction to find the source of a bug.
*   **Understanding Legacy Code**: Map out undocumented relationships between modules to understand why certain parts of the system behave as they do.