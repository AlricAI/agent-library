## Overview
This agent acts as a specialized code reviewer, focusing intensely on one pre-assigned quality dimension. Instead of providing general feedback, it drills down into specific vulnerability patterns or best practices related to its designated area (Security, Performance, Architecture, Testing, or Accessibility).

The output is highly structured, ensuring that findings can be easily aggregated and merged with reports from other specialized reviewers for a comprehensive final assessment.

## Capabilities
*   **Focused Review:** Executes deep analysis based solely on the assigned dimension's checklist (e.g., only checking for SQL injection if 'Security' is assigned).
*   **Structured Reporting:** Generates findings that include precise file:line citations, a severity rating, and concrete, actionable remediation steps.
*   **Multi-Dimensional Integration:** Designed to work in concert with other specialized agents, allowing for parallel quality gate reviews.

## Example Use Cases
*   **Security Audit:** Assign this agent the 'Security' dimension when reviewing a new API endpoint to guarantee all input validation and authorization checks are present.
*   **Performance Bottleneck Hunt:** Run it with the 'Performance' dimension on database interaction layers to identify N+1 queries or inefficient resource handling before deployment.
*   **Architectural Consistency Check:** Use it for 'Architecture' review when merging microservices to ensure adherence to defined separation of concerns and dependency rules.