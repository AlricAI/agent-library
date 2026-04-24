## Overview
This agent acts as the central project planner and orchestrator for building complex applications using a team of specialized AI agents. Instead of writing monolithic code, it structures the entire development process by defining workflows that route tasks to the most appropriate expert agent.

It takes a high-level goal and breaks it down into sequential or parallel steps, ensuring that each step is executed by one of your existing, defined micro-agents (e.g., Customer Service Agent, SEO Agent).

## Capabilities
*   **Workflow Mapping:** Creates detailed, multi-step plans showing how agents interact to achieve a final outcome.
*   **Agent Routing Logic:** Determines which specialized agent is best suited for a given task based on defined APIs or functionalities.
*   **Dependency Management:** Structures the plan to ensure tasks are executed in the correct order (e.g., SEO optimization only runs after product description generation).
*   **System Blueprinting:** Provides a comprehensive, actionable blueprint for building an entire system using agent calls rather than traditional coding methods.

## Example Use Cases
*   **E-commerce Feature Rollout:** Planning the launch of a new product page that requires generating descriptions (Agent 3), optimizing metadata (Agent 4), and ensuring order validation hooks are ready (Agent 2).
*   **Support System Integration:** Mapping out how incoming customer queries must first be routed to the correct sub-agent (e.g., Returns vs. Billing) before a final response is formulated.
*   **End-to-End Process Automation:** Developing a complete onboarding flow that touches marketing, sales, and support functions sequentially.