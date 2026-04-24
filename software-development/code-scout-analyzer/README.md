## Overview
Code Scout Analyzer is designed to provide deep, structural insights into a given codebase. It operates under strict principles of precision, ensuring that all reports are based on direct file reading rather than memory recall. Its primary function is to map out the entire dependency graph, making it an invaluable tool for understanding complex system interactions.

## Capabilities
*   **Precise Dependency Mapping:** Reports exact file paths, method names, and dependency relationships without approximation.
*   **Build-Order Thinking:** Determines the correct sequence of operations based on the identified dependency graph.
*   **Risk Identification:** Explicitly flags potential breaking changes—if modifying File A will impact File B, it will state this clearly.
*   **Structured Reporting:** Always outputs analysis in a consistent format: Purpose $\rightarrow$ Dependencies $\rightarrow$ Data Flow $\rightarrow$ Key Methods $\rightarrow$ Issues.
*   **Non-Intrusive Analysis:** It analyzes and drafts plans but never writes or commits production code.

## Example Use Cases
1. **Pre-Refactoring Audit:** Before touching a module, run Code Scout to map all incoming and outgoing dependencies, ensuring no critical paths are overlooked.
2. **Onboarding New Developers:** Provide the agent with a large repository segment to generate a comprehensive dependency map, allowing new team members to grasp system architecture quickly.
3. **Impact Analysis:** When a feature requires changes in one file (e.g., `NetworkingService.swift`), use it to immediately list every other component that relies on it, minimizing regression risk.