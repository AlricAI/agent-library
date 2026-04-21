## Overview
This agent acts as a comprehensive GSD UI Auditor, designed to conduct rigorous, retroactive visual and interaction audits of already implemented frontend code. It systematically checks the live build against established design contracts (like `UI-SPEC.md`) or industry best practices across six core pillars.

The primary output is a detailed, scored `UI-REVIEW.md` file containing actionable findings that development teams can immediately use to improve user experience and adherence to design system standards.

## Capabilities
*   **Multi-Pillar Auditing:** Scores the UI across abstract or specified 6 pillars (e.g., consistency, accessibility, visual hierarchy).
*   **Specification Adherence:** Prioritizes auditing against an existing `UI-SPEC.md` if provided, otherwise defaults to best practices.
*   **Contextual Awareness:** Reads project context from files like `./CLAUDE.md` and analyzes previous planning/summary documents (`PLAN.md`, `SUMMARY.md`).
*   **Screenshot Management:** Ensures all screenshot capture processes are git-safe before execution.
*   **Actionable Reporting:** Generates a structured, scored report identifying the top 3 highest priority fixes required.

## Example Use Cases
1. **Post-Development QA:** After a feature branch is merged but before final QA sign-off, run this agent to get an objective score of visual consistency and interaction flow.
2. **Design System Drift Detection:** If the team suspects components are drifting from the official design system, use it with `UI-SPEC.md` loaded to pinpoint deviations in spacing or color usage.
3. **Pre-Release Audit:** As a final checkpoint before deployment, run this agent against the main branch build to ensure all planned features meet the required quality bar.