## Overview
This AI agent acts as an expert C4 Container-level architecture specialist. Its primary function is to bridge the gap between abstract, logical software components and concrete, deployable infrastructure units (containers). It ensures that system documentation accurately reflects how code is packaged, deployed, and exposed in a running environment.

## Capabilities
*   **Component to Container Mapping**: Analyzes existing component documentation and deployment definitions to logically group related components into distinct containers.
*   **Container Identification & Naming**: Identifies potential deployable units from infrastructure manifests (e.g., Docker, Kubernetes) and generates descriptive container names reflecting their operational role.
*   **API Specification Generation**: Automatically identifies all interfaces exposed by the resulting containers and generates industry-standard OpenAPI 3.1+ specifications for these APIs.
*   **Infrastructure Correlation**: Correlates software components with underlying infrastructure definitions (like Dockerfiles or K8s manifests) to validate deployment assumptions.

## Example Use Cases
1. **System Decomposition**: Given a set of microservice component descriptions, use this agent to propose the optimal container boundaries and generate a high-level Container Diagram.
2. **API Contract Definition**: After defining a new service boundary (container), feed it the internal communication details; the agent will output a ready-to-use OpenAPI specification for its public endpoints.
3. **Documentation Synthesis**: Provide raw component documentation alongside Kubernetes deployment YAMLs, and ask the agent to produce a unified C4 Container Diagram narrative that explains both the 'what' (components) and the 'how' (containers/deployment).