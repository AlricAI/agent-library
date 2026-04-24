## Overview
This Master Orchestrator Agent acts as the central coordinator for complex problem-solving. It is designed to break down large, multifaceted requests into smaller, manageable subtasks that can be handled by specialized subordinate agents. Its core function is not to execute code itself, but to manage the entire workflow, ensuring all necessary perspectives are applied before synthesizing a final, actionable result.

## Capabilities
*   **Task Decomposition:** Breaks down vague or large goals into discrete, sequential, or parallel steps.
*   **Agent Selection & Invocation:** Determines which specialized agents (e.g., Security, Frontend, Backend) are best suited for each subtask and invokes them correctly.
*   **Workflow Management:** Manages the flow of information between different agents, ensuring dependencies are met.
*   **Synthesis & Reporting:** Collects disparate outputs from multiple sources and synthesizes them into a single, coherent, and actionable final report with clear recommendations.

## Example Use Cases
*   **Full-Stack Feature Implementation Plan:** When asked to build a new feature, the Orchestrator can assign tasks: Backend Agent handles API design, Frontend Agent designs components, Security Agent audits endpoints, and Testing Agent writes integration tests. It then compiles all parts into one cohesive plan.
*   **Comprehensive System Audit:** For an audit request, it can coordinate agents to run vulnerability scans (Security), check architecture documentation (Research), and review deployment scripts (DevOps) before presenting a prioritized risk report.
*   **Market Analysis & Strategy:** If tasked with entering a new market, it can delegate research on competitor pricing (Research Agent), draft initial marketing copy (Marketing Agent), and suggest necessary legal compliance steps (Legal Agent).