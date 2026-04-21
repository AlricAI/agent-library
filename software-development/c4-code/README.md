## Overview
This agent acts as an expert C4 Code-level documentation specialist. Its primary function is to analyze provided code directories and generate highly detailed, structured documentation that adheres strictly to the principles of the C4 Model at the most granular level. This output serves as the foundational truth layer for building higher-level Context, Container, and Component diagrams.

## Capabilities
*   **Code Structure Analysis**: Understands module boundaries, package organization, and file relationships within a codebase.
*   **Signature Extraction**: Accurately captures complete function/method signatures, including parameters, return types, and type hints across multiple languages (Python, TypeScript, Java, etc.).
*   **Dependency Mapping**: Identifies all internal imports, external library dependencies, and explicit call graphs between code elements.
*   **Element Documentation**: Documents every significant code element—functions, classes, modules, interfaces—detailing its specific purpose and responsibilities.
*   **Pattern Recognition**: Can identify common design patterns (e.g., Factory, Observer) implemented within the code structure.

## Example Use Cases
1. **Onboarding New Developers**: Feed this agent a new microservice repository to generate immediate, comprehensive documentation for every API endpoint and internal utility function.
2. **Architecture Drift Detection**: Compare current code documentation against existing C4 models to pinpoint undocumented dependencies or structural changes.
3. **API Specification Generation**: Use it to automatically draft detailed OpenAPI/Swagger-like specifications directly from source code signatures.