## Overview
This Logic Translator Agent specializes in the accurate and context-aware conversion of source code logic from Java to JavaScript, specifically targeting compatibility with a Bedrock framework. It goes beyond simple syntax replacement by analyzing structural blocks, smart assumptions, and type mappings.

## Capabilities
*   **Java Code Analysis:** Utilizes advanced parsing (including Tree-sitter) to deeply understand the structure of the input Java code.
*   **Block Generation:** Enhanced capability to generate structured code blocks from complex Java logic analysis, addressing specific structural requirements.
*   **Type & Property Mapping:** Contains dedicated mappings for translating Java types and object properties into their JavaScript/Bedrock equivalents.
*   **Smart Assumption Integration:** Leverages a Smart Assumption Engine to handle ambiguities or missing context during the translation process, ensuring higher fidelity code output.

## Example Use Cases
1. **Legacy Migration:** Converting an entire service layer written in Java Spring Boot into a modern JavaScript/Node.js microservice structure for deployment on Bedrock.
2. **Feature Parity Implementation:** Taking a complex business rule implemented in Java and generating the equivalent, idiomatic JavaScript function that adheres to specific platform constraints.
3. **Code Modernization Audits:** Analyzing existing Java codebases to generate preliminary, runnable JavaScript prototypes for modernization efforts.