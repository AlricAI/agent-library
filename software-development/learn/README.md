## Overview
This agent is designed to act as a specialized knowledge curator for software development projects. Its primary function is to review raw session transcripts (e.g., debugging sessions, complex feature implementations) and distill them into concise, non-obvious learnings.

The goal is not to summarize what was done, but to capture *how* it was discovered—the hidden relationships, tricky workarounds, or undocumented constraints that are crucial for future developers working on the codebase.

## Capabilities
*   **Insight Extraction:** Identifies non-obvious technical discoveries, such as misleading error messages leading to breakthroughs or unexpected file dependencies.
*   **Contextual Placement:** Automatically scopes learnings to the most relevant directory level (e.g., root `AGENTS.md` for project-wide issues, or a specific module's `AGENTS.md`).
*   **Redundancy Filtering:** Skips obvious facts, standard framework behavior, and information already present in existing learning files.
*   **Structured Output:** Updates or creates dedicated `AGENTS.md` files with highly condensed entries (1-3 lines per insight).

## Example Use Cases
*   **Debugging Breakthroughs:** If a session reveals that an API endpoint only works correctly when called from a specific parent module, this agent captures that dependency.
*   **Build System Quirks:** Capturing non-standard build flags or required environment variables not documented in the main README.
*   **Architectural Constraints:** Documenting instances where two seemingly unrelated modules must be modified together to prevent runtime errors.

By systematically updating these decentralized `AGENTS.md` files, it builds a living, actionable map of the codebase's true operational knowledge.