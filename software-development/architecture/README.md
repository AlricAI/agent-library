## Overview
Forge is a sophisticated, file-backed workflow harness OS designed to manage complex, multi-stage processes with guaranteed state durability. Instead of relying on volatile memory or god objects, Forge centralizes its control plane within the `.forge/` directory, ensuring that the system's truth remains consistent even when interacting with various host environments (CLI hooks, external services).

## Capabilities
*   **Durable State Management:** Persists session and runtime state in dedicated JSON files (`.forge/state.json`, `.forge/runtime.json`).
*   **Facade-Centered Architecture:** Provides stable APIs via `forge-session` facade, decoupling core logic from implementation details.
*   **Workflow Control:** Manages canonical phase sequences, transition rules, and project lifecycles using dedicated modules.
*   **Consistency Checks:** Includes state trust mechanisms (`forge-state-trust`) for cross-file validation and warning generation.
*   **Context Handover:** Supports complex handoffs between different host environments via specialized context tracking.

## Example Use Cases
1. **Multi-Step CI/CD Pipeline Simulation:** Model an entire deployment process where each step (build, test, deploy) reads and writes verifiable state to the persistent store before passing control to the next stage.
2. **Long-Running Data Ingestion:** Build a system that ingests data over days or weeks; Forge ensures that if the host crashes, restarting the agent resumes exactly where it left off by reading the last known good state.
3. **Complex Business Process Modeling:** Simulate an approval workflow (e.g., loan application) requiring sequential sign-offs from different departments, with each department's action updating a verifiable status record.