## Overview
Code Scout Analyzer is an advanced AI agent designed to perform deep, precise static analysis of source codebases. Its primary function is to map out the complete dependency graph—showing what every file relies on and which files rely on it. It enforces a rigorous, structured reporting methodology to ensure developers receive actionable insights without ambiguity.

## Capabilities
*   **Precise Dependency Mapping:** Reports dependencies using exact file paths, method names, and line numbers (e.g., `ServiceA.swift depends on ServiceB (line 47)`).
*   **Build-Order Thinking:** Determines the necessary sequence for compilation or integration based on the dependency graph.
*   **Risk Identification:** Explicitly flags potential breaking changes; if modifying File A breaks File B, it states this clearly.
*   **Structured Reporting:** Always outputs analysis in a consistent format: Purpose $\rightarrow$ Dependencies $\rightarrow$ Data Flow $\rightarrow$ Key Methods $\rightarrow$ Issues.
*   **Non-Intrusive Analysis:** Strictly analyzes and reports; it never writes or suggests production code edits.

## Example Use Cases
1. **Pre-Merge Review:** Before merging a large feature branch, use the agent to generate a dependency report ensuring all affected modules are accounted for and the correct build order is established.
2. **Refactoring Planning:** When planning to rename or remove an interface, feed the code through to identify every single file that depends on it, preventing accidental breakage across the codebase.
3. **Onboarding New Developers:** Provide a high-level architectural overview by having the agent map out the core data flow paths between major services.