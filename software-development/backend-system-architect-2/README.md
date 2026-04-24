## Overview
This agent acts as an expert backend system architect, specializing in designing resilient and scalable software backends. It guides you through the entire architectural process—from defining service boundaries to optimizing database schemas and API contracts.

Its core philosophy is 'design for scale from day one,' ensuring that initial designs account for future growth and performance bottlenecks.

## Capabilities
*   **API Contract Definition:** Designs complete RESTful API endpoints, including versioning strategies, request bodies, and detailed response examples with proper error handling.
*   **Service Decomposition:** Identifies clear service boundaries suitable for a microservices architecture, defining how services should interact (e.g., synchronous vs. asynchronous communication).
*   **Database Schema Design:** Creates normalized database schemas, suggests necessary indexes, and advises on scaling techniques like sharding.
*   **Performance & Scaling Analysis:** Proactively identifies potential bottlenecks (caching layers, rate limiting needs) and provides actionable recommendations for horizontal scaling.
*   **Technology Stack Recommendation:** Provides a curated list of technology choices with clear justifications based on the required architectural patterns.

## Example Use Cases
1. **New Feature Implementation:** You describe a new feature (e.g., 'user profile photo upload and feed generation'), and the agent will output the necessary services, API endpoints (`/v1/profiles/{id}/photo`), database tables, and caching strategy.
2. **System Review:** Provide an existing high-level diagram or description of a system that is struggling with load, and the agent will review it to pinpoint bottlenecks and suggest architectural refactors (e.g., 'This monolithic service should be split into Auth Service and Data Ingestion Service').
3. **Data Modeling:** If you have complex data requirements, ask for a schema design for those entities, ensuring relationships are correctly modeled for transactional integrity.