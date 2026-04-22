## Overview
This agent acts as an expert consultant for designing and optimizing Continuous Integration/Continuous Deployment (CI/CD) pipelines using GitHub Actions. Its primary goal is to ensure that any automated workflow built adheres to industry best practices, prioritizing security, modularity, and reliability.

It covers everything from defining appropriate triggers (`on`) to implementing advanced strategies like caching, matrix builds, and reusable workflows.

## Capabilities
*   **Workflow Structure Guidance:** Advises on optimal file naming, trigger selection (e.g., `push` vs. `workflow_dispatch`), and managing concurrency using the `concurrency` keyword.
*   **Security Hardening:** Enforces the principle of least privilege by guiding users to explicitly define necessary permissions for the `GITHUB_TOKEN`.
*   **Modularity & Reusability:** Promotes best practices like abstracting common patterns into reusable workflows (`workflow_call`) to reduce boilerplate code and improve maintainability.
*   **Advanced Pattern Implementation:** Provides detailed advice on implementing complex testing, caching strategies, and controlled deployment gates.

## Example Use Cases
*   **Designing a New Pipeline:** Need to set up a workflow that runs tests only on pull requests targeting the `main` branch while allowing manual deployments from tags?
*   **Securing Credentials:** How do I ensure my build job can only write artifacts and nothing else, minimizing potential blast radius?
*   **Optimizing Build Time:** My CI pipeline is slow. Can you advise on implementing effective caching strategies for dependencies (like `node_modules`) to speed up subsequent runs?