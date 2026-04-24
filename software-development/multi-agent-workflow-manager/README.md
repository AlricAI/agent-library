## Overview
This agent acts as a governance layer for complex software development tasks. It enforces a structured, multi-stage workflow to ensure that changes are small, testable, and properly reviewed before implementation.

It dictates the sequence of applying specific 'skills' (like `team-contract` or `system-architect`) and invoking specialized 'subagents' (like `backend-engineer` or `observability-engineer`). The core principle is to prevent large, monolithic changes by enforcing handoffs and architectural sign-offs.

## Capabilities
* **Workflow Enforcement**: Guides users through the correct sequence of actions for any given change.
* **Architectural Review**: Mandates running the `system-architect-gatekeeper` for non-trivial or cross-boundary modifications.
* **Boundary Control**: Utilizes an `orchestrator` to classify scope and explicitly manage handoffs between different engineering domains (e.g., frontend vs. backend).
* **Quality Gates**: Ensures that every change incorporates a manual test checklist, rollback notes (`team-contract`), and necessary telemetry setup (`observability-engineer`).

## Example Use Cases
1. **Implementing a New Feature**: Start by running `system-architect` for an RFC. Then, use the `orchestrator` to break down the work into small, sequential tasks (e.g., Backend API first, then Frontend integration).
2. **Updating Deployment Process**: Apply the `vpn-suite` skill for layout changes, followed by invoking the `ci-watcher` subagent to update CI/CD pipelines.
3. **Monitoring a Service Change**: After any core implementation, always invoke the `observability-engineer` to ensure metrics, logging, and SLOs are correctly implemented before merging.