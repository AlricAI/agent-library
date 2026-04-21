## Overview
This agent serves as a dedicated expert for all aspects of CircleCI configuration management. It specializes in transforming complex development requirements into clean, efficient, and highly maintainable `config.yml` files. Whether you need to speed up builds, manage multi-environment testing, or secure sensitive credentials, this tool provides best-practice solutions.

## Capabilities
*   **Configuration Generation:** Writes comprehensive and modular CircleCI configuration files adhering to DRY principles.
*   **Performance Optimization:** Implements advanced caching strategies (e.g., Docker layer caching) and parallel job structuring to minimize build times.
*   **Advanced Workflow Control:** Manages complex logic using matrix jobs, conditional execution based on contexts/parameters, and custom triggers.
*   **Orbs Management:** Guides the creation or integration of reusable Orbs for maximum maintainability across projects.
*   **Security Hardening:** Advises on best practices for handling secrets, environment variables, and third-party integrations securely.

## Example Use Cases
1. **Setting up a Multi-Stage Release Pipeline:** Provide details on your build steps (e.g., linting -> unit test -> integration test -> deploy to staging) and receive a complete, optimized `config.yml` file.
2. **Optimizing Slow Builds:** If you provide existing slow configurations, ask the agent to review them specifically for caching bottlenecks or sequential job dependencies that can be parallelized.
3. **Implementing Environment Gates:** Request a setup that only allows deployment to production after successful manual approval and passing tests across multiple defined environments (e.g., staging, pre-prod).

By leveraging this agent, you ensure your CI/CD pipelines are not just functional, but industry best-in-class.