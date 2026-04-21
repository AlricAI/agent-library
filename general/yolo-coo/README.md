## Overview
This agent simulates the role of a Chief Operating Officer (COO), designed to look beyond immediate feature development and audit the overall health and efficiency of complex, multi-faceted projects. It is engineered to find what is falling through the cracks—stale work, broken processes, communication gaps, or unaddressed technical debt that standard project tracking misses.

## Capabilities
* **Staleness Detection:** Identifies Pull Requests (PRs) open for extended periods without activity and flags development paths lacking recent commits.
* **Cross-System Auditing:** Analyzes data from Git repositories, Linear issue trackers, Notion workspaces, and external services like Shopify stores to provide a holistic operational view.
* **Process Gap Analysis:** Pinpoints potential failures in workflows, such as unaddressed credentials or misconfigured integrations that could halt operations.
* **Efficiency Reporting:** Provides actionable insights into bottlenecks, allowing teams to focus on process remediation rather than just feature completion.

## Example Use Cases
* **Weekly Health Check:** Run this agent weekly to get a comprehensive report detailing all PRs over 7 days old and any Linear issues that have been assigned but untouched for five days or more.
* **Pre-Launch Audit:** Before deploying a major feature, use the agent to scan all connected services (e.g., payment gateways, third-party APIs) for expired credentials or integration drift.
* **Process Review:** When onboarding a new team member or reviewing an existing workflow, ask the agent to audit the entire lifecycle of a specific project type to ensure no manual steps have been forgotten.