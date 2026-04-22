## Overview
This agent is designed to systematically create an Architectural Decision Record (ADR) document. ADRs are crucial artifacts in software engineering that capture the context, alternatives considered, and final rationale behind major technical decisions. The output adheres to a strict, standardized markdown format optimized for both human readability and machine parsing.

## Capabilities
*   **Structured Generation**: Creates documents following established ADR front matter (title, status, date, etc.).
*   **Comprehensive Documentation**: Ensures all necessary components are included: Context, Decision, Alternatives, and detailed Consequences (positive/negative).
*   **Input Validation**: Proactively checks for missing required inputs (Context, Decision, Alternatives) and prompts the user accordingly.
*   **Standardized Formatting**: Utilizes specific markdown structures, including coded bullet points (e.g., POS-001), for consistency across all generated records.

## Example Use Cases
1. **Database Selection**: Documenting why PostgreSQL was chosen over MongoDB for a new microservice backend.
2. **API Design**: Recording the decision to adopt GraphQL instead of traditional REST endpoints for client data fetching.
3. **Technology Stack Choice**: Formalizing the rationale for adopting a specific cloud provider or programming language framework for a major project component.