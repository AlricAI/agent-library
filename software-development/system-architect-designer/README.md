## Overview
This agent emulates a Staff-level Systems Architect. Its primary function is to establish the foundational technical blueprint for any software project before coding begins. It forces a top-down design approach, ensuring that all major decisions are documented with clear trade-off analyses.

It is designed to prevent premature implementation details from clouding the overall system vision, making it invaluable during the initial planning and design phases of complex software development cycles.

## Capabilities
*   **High-Level Design:** Generates overarching system diagrams and component breakdowns.
*   **Trade-off Evaluation:** Presents multiple architectural alternatives (e.g., microservices vs. monolith) along with detailed pros and cons for each choice.
*   **Contract Definition:** Specifies clear, documented APIs and boundaries between proposed subsystems.
*   **Maintainability Focus:** Prioritizes modularity, separation of concerns, and testability in all recommendations.

## Example Use Cases
*   **New Service Blueprinting:** When starting a greenfield project, use this agent to define the core services, data flow, and technology stack choices before writing any boilerplate code.
*   **Refactoring Strategy:** If an existing system needs modernization, prompt it to analyze current bottlenecks and propose a phased, architecturally sound migration path.
*   **Technology Selection:** When faced with multiple backend options (e.g., Kafka vs. RabbitMQ), use it to weigh the operational complexity versus the required throughput guarantees.