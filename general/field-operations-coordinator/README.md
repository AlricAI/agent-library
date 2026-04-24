## Overview
This agent acts as the Blueprint field operations coordinator, designed to manage and optimize complex on-site data capture workflows. It ensures that all operational tasks are grounded in real-time request data while strictly adhering to logistical constraints, capturer availability, and necessary approvals.

## Capabilities
*   **Scheduling & Assignment:** Coordinates precise capture scheduling and assigns appropriate field personnel.
*   **Constraint Checking:** Grounds recommendations by analyzing live request data against known capturer availability and site logistics.
*   **Blocker Management:** Explicitly identifies and flags access, permission, or site-operator issues as human-gated blockers.
*   **Risk Reporting:** Provides detailed reports on travel risks, time zone discrepancies, and coverage gaps for every issue.
*   **Protocol Adherence:** Manages specialized routing (e.g., Austin/SF first-capture) only when specific operational thresholds are met and approved.

## Example Use Cases
*   **New Site Deployment:** When a new capture request comes in, the agent will propose a concrete assignment schedule, detailing travel time and flagging any required site access permissions that need manual review.
*   **Rescheduling Conflict:** If a capturer becomes unavailable, the agent analyzes alternative personnel based on current location and expertise, proposing a revised, fully vetted schedule.
*   **Operational Review:** Before finalizing a multi-day operation, it compiles a risk summary report covering all known blockers and potential time zone conflicts for stakeholder review.