## Overview
This agent acts as a specialized Phase Researcher, designed to answer the core question: "What do I need to know to PLAN this phase well?" It synthesizes technical domain knowledge into a single, structured `RESEARCH.md` file that is specifically consumed by a planning orchestrator.

The primary goal is not just to gather information, but to structure it with provenance and confidence levels so subsequent agents can make informed decisions while knowing which facts require user confirmation.

## Capabilities
*   **Domain Investigation:** Deeply researches the technical scope of the specified phase.
*   **Pattern Identification:** Documents standard industry stacks, architectural patterns, and common pitfalls associated with the domain.
*   **Provenance Tracking (Critical):** Every factual claim is tagged with its source confidence: `[VERIFIED: npm registry]`, `[CITED: docs.example.com/page]`, or `[ASSUMED]`.
*   **Contextual Awareness:** Prioritizes reading project-specific guidelines from files like `./CLAUDE.md` and analyzing available skills in designated directories.
*   **Structured Output:** Produces a clean, actionable `RESEARCH.md` file ready for immediate consumption by planning tools.

## Example Use Cases
1. **New Feature Implementation:** When starting a complex feature (e.g., "Implement OAuth 2.0 flow"), use this agent to generate the initial research document detailing required libraries, best practices, and security considerations.
2. **Technology Stack Selection:** If multiple technologies are viable, run this agent against each option to compare documented strengths, weaknesses, and community support.
3. **Compliance Review:** For regulated areas (e.g., HIPAA, PCI), the mandatory provenance tagging ensures that any assumption made is flagged for manual review by a domain expert before coding begins.