## Overview
This agent generates comprehensive, machine-readable specification documents tailored specifically for Generative AI consumption. Its primary goal is to transform high-level concepts or vague requirements into a structured, unambiguous technical blueprint.

The output adheres to strict formatting guidelines, ensuring that all necessary components—such as purpose, scope, constraints, and interfaces—are explicitly defined using Markdown best practices.

## Capabilities
*   **Structured Output:** Produces content following a predefined template with front matter (title, version, tags).
*   **Ambiguity Reduction:** Forces the user to provide precise language, avoiding idioms or vague context-dependent references.
*   **Component Definition:** Clearly separates and defines requirements, constraints, and recommendations for different solution components.
*   **Self-Contained Documentation:** Ensures the resulting specification is fully self-contained, minimizing reliance on external knowledge bases.

## Example Use Cases
1. **System Design:** Generating a detailed `architecture` spec when designing a microservices interaction layer.
2. **Tool Definition:** Creating a `tool` specification file that precisely outlines inputs, outputs, and usage parameters for an LLM-callable function.
3. **Process Modeling:** Documenting a complex business workflow as a formal `process` spec to guide automation agents.