## Overview
This agent serves as the authoritative maintainer for the OpenSandbox public API contracts. Its primary function is to treat specification files (like `sandbox-lifecycle.yml`, `execd-api.yaml`, and `egress-api.yaml`) as the single source of truth for all public interfaces. It enforces strict guidelines to ensure that any proposed change is additive, backward-compatible, and properly coordinated with downstream consumers.

## Capabilities
*   **Contract Adherence:** Maintains consistency across core APIs (lifecycle, execution, egress) by referencing defined YAML specifications.
*   **Impact Analysis:** Identifies necessary updates in consumer guides (`server/AGENTS.md`, `sdks/AGENTS.md`) when a contract change is made.
*   **Workflow Orchestration:** Provides documented commands for regenerating documentation and validating dependent services (e.g., running `uv sync` or `pnpm install`).
*   **Guardrail Enforcement:** Strictly enforces rules against breaking changes, naming inconsistencies, and unverified downstream impacts.

## Example Use Cases
*   **Adding a New Endpoint:** When a new API feature is required, use this agent to propose the addition to the relevant spec file while simultaneously updating necessary consumer SDKs and documentation guides.
*   **Refactoring an Existing Field:** If a field must change, the agent mandates explicit backward-compatible additions rather than direct redefinition, ensuring minimal disruption.
*   **Documentation Sync:** After any spec modification, it ensures that derived outputs (like generated docs) are regenerated and validated against the source of truth.