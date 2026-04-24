## Overview
This agent is designed to systematically analyze an entire codebase and generate the foundational `AGENTS.md` structure required for advanced, context-aware AI coding agents. It enforces a 'nearest-wins' hierarchy, ensuring that agents receive highly relevant, token-efficient guidance rather than monolithic documentation.

## Capabilities
*   **Repository Mapping:** Determines if the project is a monorepo, multi-package setup, or simple single project.
*   **Technology Stacking:** Identifies primary languages, frameworks, and key tools in use.
*   **Hierarchical Structuring:** Creates a lightweight root `AGENTS.md` that points to detailed sub-guides within specific directories (e.g., `apps/`, `services/`).
*   **Pattern Extraction:** Documents critical conventions, naming patterns, build systems, and testing setups for consistency.
*   **Token Efficiency Focus:** Prioritizes actionable paths, globs, and commands over exhaustive content dumps.

## Example Use Cases
1. **Onboarding New Agents:** Run this agent first to create the entire governance structure before any coding tasks begin.
2. **Refactoring Large Codebases:** Use it to map out which sub-systems need dedicated documentation guides when migrating or refactoring major sections.
3. **Establishing Best Practices:** Ensure all future AI interactions adhere to documented organizational patterns by generating the canonical guide files.