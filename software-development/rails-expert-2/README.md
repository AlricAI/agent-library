## Overview
This specialized AI agent acts as a seasoned Rails Architect, guiding you through the development of maintainable, scalable, and modern Ruby on Rails applications. It strictly adheres to established Rails conventions while integrating contemporary patterns like Service Objects (Interactor pattern) and Hotwire (Turbo/Stimulus).

The goal is to produce production-ready code that minimizes technical debt by prioritizing simplicity, DRY principles, and robust separation of concerns.

## Capabilities
*   **Architectural Design:** Designs the overall structure, including database schema normalization, API versioning, and service layer boundaries.
*   **Business Logic Implementation:** Creates dedicated Service Objects to keep controllers thin and manage complex business workflows.
*   **Frontend Modernization:** Implements modern user experiences using the Hotwire stack (Turbo Frames/Streams and Stimulus). 
*   **API Development:** Builds RESTful endpoints adhering to JSON:API standards, complete with proper serialization and versioning.
*   **Background Processing:** Sets up reliable background job processing using tools like Sidekiq, including retry strategies.
*   **Testing & Quality:** Generates comprehensive RSpec test suites covering models, services, controllers, and features for high code coverage.
*   **Security & Performance:** Provides guidance on implementing Devise/Pundit for authorization and suggests query optimizations, caching layers, and Docker deployment configurations.

## Example Use Cases
*   **Building a New Feature:** Need to add a complex workflow (e.g., user onboarding with multiple steps)? Ask it to design the service object, API endpoint, and necessary frontend interactions.
*   **Refactoring Legacy Code:** If you have monolithic controllers, prompt it to refactor business logic into dedicated Interactors and update the calling code.
*   **Performance Bottleneck:** Provide slow query logs or endpoints; the agent will analyze them for missing indexes, N+1 queries, or caching opportunities.