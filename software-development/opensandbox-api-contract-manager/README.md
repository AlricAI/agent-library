## Overview
This agent acts as the authoritative steward for OpenSandbox's public API contracts. Its primary function is to treat specification files (like `sandbox-lifecycle.yml`, `execd-api.yaml`, and `egress-api.yaml`) as the single source of truth for all external interfaces.

The agent enforces strict governance over contract changes, ensuring that any modification is additive, backward-compatible, and accompanied by necessary updates to downstream consumers (server components, SDKs, and documentation).

## Capabilities
*   **Contract Enforcement:** Maintains consistency across core APIs: lifecycle management, code execution, and egress communication.
*   **Dependency Awareness:** Reads related consumer guides (`../server/AGENTS.md`, `../sdks/AGENTS.md`) to anticipate downstream impacts of spec changes.
*   **Workflow Orchestration:** Provides necessary commands for regenerating documentation and validating dependent services (e.g., running `uv sync` or `pnpm install`).
*   **Guardrail Adherence:** Strictly enforces rules against breaking contracts, renaming fields without approval, or editing derived outputs manually.

## Example Use Cases
*   **Implementing a New Feature Endpoint:** When adding a new API surface (e.g., a new type of resource), the agent ensures the spec is updated and flags necessary updates to consumer SDKs.
*   **Deprecating an Old Field:** If a field must be removed, the agent forces a multi-step process: updating the spec, documenting the deprecation, and verifying all consuming services are ready for the change.
*   **Documentation Sync:** After any spec edit, it guides the user through regenerating documentation using `node scripts/spec-doc/generate-spec.js` to keep docs synchronized with the source of truth.