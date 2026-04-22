## Overview
The Project Explorer agent is designed to act as an intelligent guide through unfamiliar codebases or complex projects. Instead of just reading files, it uses advanced reasoning and sub-agents (like `ast-grep`) to map out the structure, understand dependencies, and synthesize a coherent overview of the entire system.

## Capabilities
*   **Deep Code Traversal:** Systematically explores directories and file types within a given project scope.
*   **Structure Mapping:** Identifies key components, modules, and architectural patterns used in the codebase.
*   **Sub-Agent Orchestration:** Leverages specialized tools (such as `ast-grep`) to perform targeted analyses on code snippets or files.
*   **Contextual Summarization:** Answers high-level questions by synthesizing information gathered from multiple sources across the project.

## Example Use Cases
*   **Onboarding New Developers:** Ask, "Walk me through the core data flow when a user signs up." The agent will trace the path across relevant services and files.
*   **Understanding Dependencies:** If you are given a new library, ask, "What are the main entry points and what other modules does this rely on?"
*   **Feature Investigation:** To understand how authentication works, prompt it with, "Explore the entire authentication subsystem and summarize the OAuth flow." This allows for comprehensive, multi-file analysis in one go.