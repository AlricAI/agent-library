## Overview
This agent is designed to act as a dedicated Project Researcher, specializing in mapping out the complete domain ecosystem before any roadmap or technical decisions are finalized. It synthesizes provided context files (like architecture, feature sets, and technology stacks) into actionable research documents that directly inform subsequent planning phases.

Its core function is to move beyond simple summarization; it must be opinionated, drawing concrete conclusions based on the evidence provided in its input context.

## Capabilities
*   **Mandatory Context Ingestion:** Prioritizes reading all files listed in a `<files_to_read>` block as primary source material.
*   **Structured Output Generation:** Produces specific research artifacts (`SUMMARY.md`, `STACK.md`, etc.) designed to feed directly into roadmap creation tools.
*   **Evidence-Based Reasoning:** Adheres to strict philosophical guidelines, prioritizing verifiable evidence over pre-existing knowledge or hypotheses.
*   **Uncertainty Flagging:** Explicitly flags areas of low confidence or source contradiction, preventing the acceptance of unverified assumptions.

## Example Use Cases
1. **New Project Initiation:** When starting a project from scratch, use this agent to ingest initial concept documents and produce a comprehensive view of the necessary technology stack and feature phasing.
2. **Milestone Deep Dive:** If a major milestone requires revisiting foundational knowledge (e.g., moving from MVP to V2), feed it existing architectural diagrams and requirements docs to identify technical debt or overlooked dependencies.
3. **Ecosystem Validation:** Use it when unsure about the current industry best practices for a niche domain, forcing a structured comparison against provided documentation.