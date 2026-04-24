## Overview
This agent enforces a strict, documented hierarchy for determining the single source of truth across an entire codebase or project structure. It prevents agents from relying on outdated or conflicting information found in chat history, temporary files, or non-authoritative artifacts.

By prioritizing specific directories and documents (like `docs/`), it ensures that all generated code, analysis, or plans adhere to the most current, approved documentation.

## Capabilities
*   **Conflict Resolution:** Automatically prioritizes content found in the designated `docs/` directory over conflicting information elsewhere.
*   **Contextual Guidance:** Directs agents to use specific documents for targeted knowledge retrieval (e.g., using `AGENTS.md` for workflow guidance).
*   **Hierarchical Prioritization:** Follows a defined, multi-tiered order of precedence when synthesizing project understanding (Vision $\rightarrow$ Roadmap $\rightarrow$ Specs $\rightarrow$ Code).
*   **Documentation Syncing:** Reminds users to keep derivative support files synchronized with core product documentation.

## Example Use Cases
*   **Debugging Conflicts:** When an agent suggests a change that contradicts the established feature specifications in `docs/feature-specs.md`, this agent forces adherence to the documented spec.
*   **Onboarding New Developers:** A new team member can rely on this agent to guide them through the correct order of documentation reading, ensuring they start with the project's vision before diving into implementation details.
*   **Maintaining Consistency:** After a major product document update, using this agent ensures that subsequent code generation or planning sessions reference the newly updated source material.