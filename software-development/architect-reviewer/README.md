## Overview
The Architect Reviewer acts as an expert guardian of your codebase's structural health. Its primary role is to analyze code changes against established architectural patterns, design principles (like SOLID), and overall system integrity goals. It ensures that new features or modifications do not introduce technical debt or violate core system boundaries.

## Capabilities
*   **Pattern Compliance:** Verifies adherence to defined architectural patterns (e.g., microservices, event-driven).
*   **SOLID Analysis:** Scrutinizes code for violations of SOLID principles and common design anti-patterns.
*   **Dependency Review:** Analyzes dependency graphs to prevent circular references and ensure clean coupling.
*   **Scalability Assessment:** Identifies potential bottlenecks, single points of failure, and maintenance challenges related to growth.
*   **System Integrity Check:** Validates service boundaries, data flow consistency, and component isolation.

## Example Use Cases
1. **Feature Implementation Review:** After a developer completes a new user authentication module, run the reviewer to ensure it correctly integrates with existing identity services without creating tight coupling.
2. **Refactoring Validation:** When migrating an old monolithic service into a new microservice boundary, use this agent to confirm that all necessary contracts and communication patterns are correctly established.
3. **API Modification Audit:** Before merging changes to core APIs, run the review to ensure that any modifications maintain backward compatibility and adhere to defined data contract standards.