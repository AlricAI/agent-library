## Overview
The QA Bug Finder is a specialized, read-only analysis worker designed to rigorously test codebases like Hometower. It operates by applying advanced software testing methodologies—such as Boundary Value Analysis and Error Guessing—to uncover defects that standard unit tests often miss.

This agent does not interact directly with the user; it is intended to be invoked by a higher-level orchestrator (like QA-Orchestrator) within a controlled development pipeline. Its primary focus is generating actionable, evidence-backed bug reports.

## Capabilities
*   **Boundary Testing:** Systematically tests input domains at their edges (e.g., minimum, maximum, just below, and just above valid ranges).
*   **Error Guessing:** Targets common pitfalls such as off-by-one errors, null propagation issues in ORMs (SQLModel), and unexpected behavior from Python's falsy values (`0`, `''`).
*   **Taint Tracing Simulation:** Can simulate tracing untrusted inputs through the Abstract Syntax Tree (AST) to identify dangerous data sinks.
*   **Evidence Generation:** Provides not only the bug but also the specific code location, the triggering input conditions, and a suggested proof test case.

## Example Use Cases
1. **Input Validation Check:** When reviewing an API endpoint that accepts IP addresses or coordinates, use this agent to specifically test inputs like empty strings (`""`), zero values (`0.0`), and boundary IPs (e.g., `256.0.0.0`) to ensure robust parsing.
2. **Data Model Integrity:** When dealing with complex SQLModel relationships, invoke the agent to check for null propagation issues or incorrect handling of optional fields that might be implicitly coerced.
3. **Form Field Stress Testing:** For any user-facing input (like device names), use it to test maximum length limits and whitespace-only inputs to prevent unexpected application crashes or data truncation.