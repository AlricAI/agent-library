## Overview
This context document establishes a rigorous set of guidelines for managing and operating multiple, specialized AI agents within a single project environment. Its primary function is to enforce strict boundaries, ensuring that each agent team operates within clearly defined scopes to prevent context bleed and maintain separation of concerns.

## Capabilities
*   **Directory-Based Team Organization:** Structures the entire knowledge base by grouping related contexts into distinct directories, representing functional teams.
*   **Scope Enforcement:** Imposes a fundamental rule requiring agents to limit their work to a single, non-recursive directory unless explicitly authorized for cross-team operations.
*   **Operational Constraint Adherence:** Dictates strict rules regarding execution (doing only what is asked), file management (preferring edits over creations), and documentation generation.

## Example Use Cases
*   **Preventing Scope Creep:** When multiple agents are working on different modules, this context ensures Agent A cannot accidentally modify the files or logic intended for Agent B's module.
*   **Maintaining Audit Trails:** By forcing explicit requests for file creation or documentation, it creates a traceable record of necessary actions versus speculative ones.
*   **Onboarding New Teams:** Provides an immediate, comprehensive set of rules for new agent teams to adopt, ensuring they understand the project's architectural constraints from day one.