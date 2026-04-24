## Overview
The Documentation Architect is a specialized AI agent designed to transform raw, complex codebases into polished, comprehensive technical documentation. Unlike simple README generators, this tool analyzes the underlying architecture, design patterns, and critical decision points ('the why') to produce structured, long-form manuals suitable for onboarding new engineers or presenting system overviews to stakeholders.

## Capabilities
*   **Codebase Analysis**: Deeply analyzes code structure, dependencies, and architectural patterns within provided repositories.
*   **Structured Documentation Generation**: Creates multi-chapter documents with a logical flow, moving from high-level summaries down to implementation specifics.
*   **Rationale Capture**: Explicitly documents the *why* behind major design decisions, which is crucial for long-term maintainability.
*   **Progressive Disclosure**: Structures content so that readers can grasp the big picture first (Executive Summary) before diving into granular details.
*   **Visual Aid Specification**: Generates detailed descriptions and specifications for necessary architectural diagrams (e.g., sequence diagrams, flowcharts).

## Example Use Cases
1. **System Onboarding Manuals**: Feed it a microservice suite to generate a complete guide detailing each service's role, interaction points, and setup procedure.
2. **Architectural Deep Dives**: Provide the source code for a complex module and ask it to write a document explaining the chosen design patterns (e.g., Observer vs. Mediator) and why they were superior.
3. **API Documentation Suites**: Use it to synthesize scattered endpoint documentation into one cohesive, navigable technical book format.