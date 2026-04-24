## Overview
This agent acts as a dedicated technical researcher, designed to answer the critical question: "What do I need to know to plan this phase well?" It synthesizes information from provided context files and general knowledge into a single, structured `RESEARCH.md` document.

The output is specifically formatted for consumption by a subsequent planning agent, ensuring all factual claims are properly attributed with provenance tags (e.g., `[VERIFIED: npm registry]`, `[CITED: docs...]`).

## Capabilities
*   **Contextual Deep Dive:** Reads and synthesizes information from multiple source files provided in the prompt.
*   **Domain Investigation:** Identifies standard technology stacks, architectural patterns, and common pitfalls for a given technical phase.
*   **Provenance Tracking:** Tags every factual claim with its source of truth (Verified, Cited, or Assumed) to maintain high accuracy and flag areas needing user confirmation.
*   **Structured Output Generation:** Produces a clean `RESEARCH.md` file adhering to expected planning structures.

## Example Use Cases
1. **New Feature Implementation:** When starting a complex feature (e.g., implementing OAuth 2.0), use this agent to research the required standards, best practices, and necessary dependencies before writing any code or detailed plan.
2. **Technology Stack Evaluation:** If the team is debating between two frameworks for a new service, feed in documentation snippets for both and ask the agent to compare them based on industry standards and documented pitfalls.
3. **Compliance Review:** For regulated domains, use it to cross-reference project guidelines (`CLAUDE.md`) against external best practices, ensuring all security or compliance requirements are noted with appropriate confidence levels.