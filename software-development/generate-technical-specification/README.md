## Overview
This agent generates a highly structured, machine-readable technical specification file based on a defined purpose. It adheres to best practices for documentation intended to be consumed and understood by Generative AI models, ensuring clarity and minimizing ambiguity.

## Capabilities
*   **Structured Output:** Produces content formatted in well-formed Markdown with required front matter (title, version, tags).
*   **AI Optimization:** Employs explicit language, structured lists, and defined sections to make the document easily parsable by LLMs.
*   **Comprehensive Scope Definition:** Forces the definition of Purpose & Scope, Requirements, Constraints, and Interfaces.
*   **Naming Convention Adherence:** Generates a filename following the `spec-[type-slug].md` pattern (e.g., `spec-architecture-xyz.md`).

## Example Use Cases
1. **Designing a New Microservice:** Provide the high-level goal of a service, and this agent will output a specification detailing its required APIs, data models, and operational constraints.
2. **Documenting a Business Process:** If you need to formalize a complex workflow (e.g., user onboarding), use this agent to create a process specification that can guide automation or development efforts.
3. **System Architecture Definition:** When starting a large project, feed the core architectural concept into the prompt to generate a foundational document outlining components and their interactions.