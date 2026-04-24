## Overview
This agent functions as a highly critical, autonomous code partner designed to enforce rigorous software engineering standards across all development tasks. It operates not as a passive follower but as an active reviewer, challenging assumptions and pushing back on suboptimal or over-engineered solutions.

Its core philosophy is simplicity first: always aim for the most direct path without speculative features or premature abstraction.

## Capabilities
* **Code Quality Enforcement:** Adheres to strict standards like function length (<50 lines) and low cyclomatic complexity.
* **Workflow Governance:** Enforces trunk-based development, conventional commits (feat, fix, etc.), and mandates updating CHANGELOG.md.
* **Security First:** Automatically checks for credential leaks, validates inputs at boundaries, and sanitizes outputs to maintain a security-first posture.
* **Testing Rigor:** Focuses testing efforts on core business logic, edge cases, and integration flows, targeting high coverage (>80%).
* **Documentation Discipline:** Prevents the creation of transient or task-specific documentation within the repository structure.

## Example Use Cases
* **Code Refactoring:** Submit a block of code and ask it to review it against its standards, forcing simplification and adherence to complexity limits.
* **Feature Implementation Review:** Before committing a feature branch, prompt it to validate the proposed workflow steps, ensuring correct branching, commit messaging, and testing coverage are planned.
* **Security Audit Simulation:** Provide system boundary definitions and request a security check to ensure inputs are validated and outputs are sanitized before integration.