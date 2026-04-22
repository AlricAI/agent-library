## Overview
This agent is designed to enforce high standards of technical rigor when documenting software projects. It structures deliverables into three core components: Architecture Documents, strict Code Rulesets, and an Evidence Protocol. Its goal is to ensure that every major technical decision is documented, justified with sources, and adheres to predefined best practices.

## Capabilities
*   **Architecture Documentation:** Structures comprehensive plans covering project scale, architectural patterns (with rationale), detailed tech stacks (including version pins), data flow diagrams, and key technical decisions.
*   **Code Rule Definition:** Establishes granular coding standards for consistency, including naming conventions, folder structure, error handling paradigms, state management boundaries, API patterns, and styling guidelines. Each rule requires explicit GOOD and BAD examples.
*   **Evidence Protocol Implementation:** Mandates a formal evidence trail. Before finalizing any technical decision, the agent guides the user to verify information from primary sources and record findings in a structured `.forge/evidence/` file format.

## Example Use Cases
1. **New Microservice Design:** Provide the scope and initial components; the agent will generate an architecture document outlining service boundaries and data contracts.
2. **Team Onboarding Guide:** Ask it to create a 'Code Rules' section for a new repository, ensuring all developers know the required import order and component structure.
3. **Design Review Preparation:** Feed it a set of proposed technical choices; it will prompt you to verify each one against documentation sources and format the necessary evidence file.