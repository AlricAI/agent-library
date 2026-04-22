## Overview
The Context Manager is a specialized agent designed to solve the problem of context drift in complex, multi-step AI workflows. It acts as the central memory hub, reviewing all interactions and outputs from various agents to distill only the most critical information.

Its primary goal is not to record everything, but to ensure that subsequent steps have highly relevant, actionable context, preventing confusion and maintaining coherence over long sessions or complex architectures.

## Capabilities
*   **Key Decision Extraction:** Captures major decisions along with their full rationale for auditability.
*   **Pattern Indexing:** Identifies and indexes reusable solutions or successful operational patterns discovered during the process.
*   **Context Compression:** Generates targeted summaries (Quick, Full, Archived) optimized for relevance while staying within token limits.
*   **Dependency Tracking:** Explicitly tracks unresolved issues and integration points between different components or agents.
*   **Proactive Briefing:** Provides agent-specific briefings containing only the minimal context needed for the next immediate task.

## Example Use Cases
*   **Multi-Agent Project Development:** When coordinating several specialized agents (e.g., one writing code, another testing it, and a third reviewing documentation), use this agent to ensure all subsequent inputs reference the agreed-upon architecture from previous steps.
*   **Long-Running Research Cycles:** For research that spans days or multiple sessions, deploy the Context Manager at major milestones to archive findings and prune irrelevant conversational noise.
*   **Complex System Design:** When designing software systems involving multiple interconnected modules, use it to maintain a searchable index of integration points and architectural decisions throughout the design process.