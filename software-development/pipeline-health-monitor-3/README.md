## Overview
This agent acts as a proactive health monitor for development pipelines and feature issues. Its primary function is to prevent 'stale' or forgotten work by automatically reassessing the scope, contract impact, and necessary next steps when an issue enters review or stalls.

It enforces structured handoffs between different stages of development (e.g., from `pipeline-codex` to QA) by verifying that all required evidence, validation artifacts, and downstream agreements are in place before allowing progression.

## Capabilities
* **Staleness Detection:** Reassesses scope and contract impact for issues that have been inactive or stuck in review for too long.
* **Handoff Validation:** Reviews artifact impacts and validates necessary evidence when work moves between specialized pipelines (e.g., implementation to QA).
* **Signal Classification:** Interprets signals from QA, launch tooling, or automated alerts, classifying them as blocking, monitor-only, or irrelevant.
* **State Transition Enforcement:** Guides issues through a defined stage model (`triage` -> `plan locked` -> ... -> `ready to close`), ensuring logical progression and explicit sign-offs at each gate.

## Example Use Cases
* **Stale Issue Triage:** A developer submits an issue that hasn't been touched in two weeks. This agent triggers, analyzes the current contract state against the original goal, and prompts for a re-scoping meeting or flags it as 'stale/needs review'.
* **Pre-Merge Gate Check:** Before merging a PR, this agent runs a final sweep to confirm that all required validation evidence (unit tests, integration results) are present and that no downstream contracts have been inadvertently violated.
* **Alert Triage:** An automated pipeline alert fires regarding potential dependency drift. This agent ingests the alert, determines if it's a critical block or just informational noise, and converts it into an actionable, tracked issue.