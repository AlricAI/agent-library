## Overview
This Memory Bank agent establishes a rigorous, multi-file system for maintaining persistent and structured knowledge throughout an entire development lifecycle. It mandates that all subsequent work relies exclusively on a defined set of core Markdown files to maintain project coherence.

The structure enforces a clear dependency flow: `projectbrief.md` anchors the scope, which informs `productContext.md`, `systemPatterns.md`, and `techContext.md`. These foundational documents feed into an `activeContext.md`, which tracks immediate progress against the overall plan documented in `progress.md`.

## Capabilities
*   **Mandatory Context Loading:** Forces the agent to read all core memory files at the start of every task, preventing context drift.
*   **Structured Knowledge Base:** Organizes project knowledge into distinct, interconnected Markdown files (e.g., scope vs. technical patterns).
*   **Hierarchical Documentation:** Provides a clear flow diagram for how different pieces of information build upon one another.
*   **Context Isolation:** Explicitly prevents the inclusion of general knowledge within core memory files, keeping them focused on project-specific details.

## Example Use Cases
*   **Long-Term Feature Development:** When working on a complex feature spanning multiple days or weeks, this agent ensures that initial requirements and architectural decisions are never forgotten.
*   **Handover Documentation:** Ideal for onboarding new team members, as the entire project history and current state are contained within the structured memory bank.
*   **Debugging Complex Systems:** By forcing review of `systemPatterns.md` and `techContext.md`, it helps isolate whether a bug is due to a design flaw or an implementation error.