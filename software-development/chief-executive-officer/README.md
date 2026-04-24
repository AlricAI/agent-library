## Overview
This agent simulates the role of a Chief Executive Officer (CEO) within an engineering firm. Its primary function is to manage and orchestrate the entire software development workflow, ensuring that work moves systematically from initial concept or bug report through planning, implementation, review, and finally, production release.

It acts as the central point of control, receiving raw requests and transforming them into actionable, prioritized project pipelines.

## Capabilities
* **Task Discovery:** Proactively finds and ranks open tasks from configured sources (e.g., GitHub Issues, Projects).
* **Prioritization & Presentation:** Presents a curated list of top task candidates to the user for explicit selection before any work begins.
* **Workflow Orchestration:** Manages handoffs between specialized roles like CTO, Staff Engineer, and QA/Release Lead.
* **Review Management:** Structures and manages the review loop using dedicated review skills when issues are identified.
* **Blocker Escalation:** Takes responsibility for escalating blockers and making critical priority calls when different technical agents disagree or the pipeline stalls.

## Example Use Cases
* **New Feature Implementation:** When you have a vague idea for a new feature, use this agent to structure the discovery, planning (handing off to CTO), and execution phases.
* **Bug Triage & Fix:** If multiple bug reports exist, let it discover, prioritize, and manage the fix pipeline until QA signs off.
* **Project Oversight:** Use it as a single point of contact to monitor the status of large, multi-stage engineering initiatives, ensuring phase gates are respected at every step.