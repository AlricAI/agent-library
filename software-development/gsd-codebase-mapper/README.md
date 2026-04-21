## Overview
This agent acts as a specialized Codebase Mapper, designed to thoroughly explore a provided codebase and generate highly structured analysis documents. Instead of relying on the orchestrator's context window, it writes its findings directly into designated planning directories (`.planning/codebase/`). This ensures that subsequent GSD commands (like planning or execution) can reliably consume these artifacts.

## Capabilities
*   **Focus Area Specialization:** It operates based on a required focus area provided during invocation: `tech`, `arch`, `quality`, or `concerns`.
*   **Structured Output Generation:** Depending on the focus, it generates specific, mandatory markdown files:
    *   `tech`: Generates `STACK.md` and `INTEGRATIONS.md` (for technology stack analysis).
    *   `arch`: Generates `ARCHITECTURE.md` and `STRUCTURE.md` (for structural analysis).
    *   `quality`: Generates `CONVENTIONS.md` and `TESTING.md` (for best practice assessment).
    *   `concerns`: Generates `CONCERNS.md` (for identifying technical debt).
*   **Contextual Awareness:** It is designed to feed directly into the GSD planning pipeline, ensuring generated documents are immediately usable by downstream agents.

## Example Use Cases
1. **Architecture Review:** To understand how a system is built, invoke with the `arch` focus area. This will produce `ARCHITECTURE.md` detailing major components and `STRUCTURE.md` mapping out the file layout.
2. **Technology Audit:** When onboarding to a new project, use the `tech` focus to generate `STACK.md`, giving an immediate overview of all primary languages, frameworks, and external dependencies in use.
3. **Pre-Refactoring Check:** Before making major changes, run with `concerns` to automatically surface potential technical debt areas documented in `CONCERNS.md`.