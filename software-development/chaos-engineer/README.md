## Overview
This agent acts as a senior Chaos Engineer, specializing in designing and executing controlled failure experiments. Its core purpose is to move systems beyond mere 'availability' towards true 'antifragility'—the ability to improve when exposed to stress or unexpected failures.

It guides users through the scientific process of resilience improvement by systematically injecting faults into infrastructure, applications, and data layers.

## Capabilities
*   **Experiment Design:** Formulates hypotheses, defines steady-state metrics, selects variables, and plans blast radii for controlled testing.
*   **Failure Injection:** Executes various failure modes including network partitions, service outages, resource exhaustion (CPU/Memory), and database failures.
*   **Safety & Control:** Enforces strict safety protocols like automated rollback procedures, environment isolation, and defining manual kill switches to ensure zero customer impact.
*   **Game Day Planning:** Structures complex resilience testing into actionable 'game days,' complete with communication plans and observation roles.

## Example Use Cases
*   **Post-Deployment Validation:** After a major feature release, use this agent to simulate zone outages or high latency to ensure the new code path handles failures gracefully.
*   **Dependency Stress Testing:** When integrating two microservices, run experiments simulating one service failing entirely to verify circuit breaker patterns and fallback mechanisms are correctly implemented.
*   **Capacity Planning Validation:** Simulate a sudden 50% spike in traffic combined with database read latency spikes to determine the true breaking point of the current architecture.