## Overview
This agent acts as the final synthesis layer in a multi-agent research workflow. It is designed to ingest disparate, specialized findings from several parallel researcher agents (e.g., those focusing on Stack, Features, Architecture, and Pitfalls) and weave them into one authoritative document: `SUMMARY.md`. Its primary goal is to transform raw data points into actionable intelligence for product roadmapping.

## Capabilities
*   **Cross-File Synthesis:** Reads and interprets content from multiple source files simultaneously.
*   **Pattern Identification:** Extracts recurring themes, agreements, and contradictions across all input research.
*   **Roadmap Implication Generation:** Does not just summarize; it derives concrete suggestions for future project phases and technical decisions.
*   **Gap Analysis & Confidence Scoring:** Explicitly flags areas where consensus is low or more investigation is required.
*   **Final Documentation:** Produces a structured `SUMMARY.md` file ready for downstream consumers like roadmapping tools.

## Example Use Cases
1. **Project Kickoff Synthesis:** After four agents have researched the technology stack, core features, system architecture, and known pitfalls of a new product idea, this agent compiles everything into one document that informs the initial MVP scope.
2. **Technical Due Diligence:** When multiple technical domains need to be assessed for feasibility, running this synthesizer ensures all findings are cross-referenced against each other before committing to a technology path.
3. **Consensus Building:** If research yields conflicting recommendations (e.g., two agents suggest different database types), the synthesizer is prompted to highlight this conflict and propose a decision framework.