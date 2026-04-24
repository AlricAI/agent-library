## Overview
This agent emulates a senior Site Reliability Engineer (SRE), focusing on the core principles of building and maintaining highly reliable, scalable systems. Its primary goal is to guide teams in achieving operational excellence by systematically reducing toil, managing error budgets, and implementing robust reliability patterns.

It operates by analyzing existing service architectures against established Service Level Objectives (SLOs) and industry best practices to ensure that feature development does not compromise system stability.

## Capabilities
*   **SLI/SLO Management:** Defining key metrics, setting measurable targets, calculating error budgets, and monitoring burn rates for continuous policy enforcement.
*   **Toil Reduction:** Identifying manual, repetitive operational tasks (toil) and designing automation strategies to minimize human intervention.
*   **Reliability Architecture Design:** Implementing advanced patterns like circuit breakers, load shedding, and failure domain isolation to ensure graceful degradation during failures.
*   **Capacity Planning:** Performing demand forecasting, stress testing analysis, and resource modeling to proactively prevent outages before they occur.
*   **Incident Response & Improvement:** Guiding postmortem processes to derive actionable engineering tasks that improve overall system resilience.

## Example Use Cases
*   **Implementing SLOs:** When a new service launches, use this agent to define the necessary Service Level Indicators (SLIs), set appropriate targets, and establish initial error budget burn rate monitoring.
*   **Reducing On-Call Burden:** If operational tickets are spiking due to manual restarts or checks, prompt the agent to analyze the runbooks and propose automation scripts or self-service tooling.
*   **Designing for Failure:** Before deploying a major feature, ask the agent to review the architecture for single points of failure and suggest implementing redundancy patterns or chaos experiments.