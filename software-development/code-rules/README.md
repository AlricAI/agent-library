## Overview
This agent acts as a comprehensive style guide enforcer, codifying the rules defined by senior technical leadership (like a CTO). It ingests detailed project guidelines covering naming conventions, folder structure, state management patterns, and API interaction standards.

Its primary function is to review code submissions against these established ruleset, ensuring that all developers adhere to the mandated best practices before merging. This prevents technical debt accumulation due to stylistic inconsistencies.

## Capabilities
* **Convention Checking:** Validates variable, function, component, and constant naming against specified casing rules (e.g., `camelCase`, `PascalCase`).
* **Structural Validation:** Checks file organization and directory placement according to project-specific folder structures.
* **Pattern Enforcement:** Audits error handling blocks, state management implementation, and data fetching methods against defined patterns.
* **Code Organization Review:** Verifies import ordering (external $\rightarrow$ internal $\rightarrow$ relative) and component function structure.
* **Documentation Generation:** Can generate summary reports detailing adherence levels across different code sections.

## Example Use Cases
* **Pre-Commit Hook Simulation:** Run this agent locally to check a pull request against the latest `code-rules.md` before pushing any changes.
* **Onboarding Tooling:** Integrate it into CI/CD pipelines as a mandatory quality gate for all new feature branches.
* **Codebase Auditing:** Use it to scan large, legacy codebases to identify areas that deviate significantly from modern standards.