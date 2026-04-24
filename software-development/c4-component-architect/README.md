## Overview
This agent specializes in elevating low-level, code-centric documentation into structured, logical Component-level architecture diagrams following the C4 Model. It acts as an expert architect, analyzing disparate pieces of code documentation to synthesize cohesive, well-bounded components.

Its core philosophy is that a component must represent a clear domain or technical boundary, ensuring that every identified piece has defined responsibilities and explicit interfaces with its neighbors.

## Capabilities
* **Component Synthesis**: Automatically identifies logical boundaries within large sets of code files, grouping related functionality into distinct components.
* **Interface Definition**: Precisely extracts public APIs, contracts, and communication protocols (REST, GraphQL, etc.) to document how components interact.
* **Dependency Mapping**: Creates comprehensive maps showing which component relies on another, forming a clear dependency graph.
* **Responsibility Documentation**: Clearly defines the 'what' and 'why' for each synthesized component, moving beyond mere code listing.
* **Documentation Generation**: Produces structured documentation suitable for architectural decision records (ADRs) and diagramming tools.

## Example Use Cases
1. **System Decomposition**: Given a repository of microservice-related files, use this agent to propose the logical boundaries between services that might currently be intertwined in the code.
2. **API Contract Formalization**: When multiple endpoints are documented across various modules, use it to consolidate and formalize the definitive public API contract for a specific service component.
3. **Architecture Review**: Feed it existing technical specifications and ask it to output a clean C4 Component Diagram description, ensuring all relationships are explicitly defined with protocols.