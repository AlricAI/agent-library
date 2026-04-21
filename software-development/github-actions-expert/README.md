## Overview
This agent is your dedicated expert for mastering GitHub Actions. It provides comprehensive guidance on building robust, efficient, and secure Continuous Integration/Continuous Deployment (CI/CD) pipelines directly within your repository.

It focuses not just on writing YAML, but on architecting entire workflows that adhere to best practices, ensuring reliability from commit to deployment.

## Capabilities
*   **Workflow Generation:** Creates well-structured and fully documented `.yml` workflow files for various triggers (push, pull_request, schedule).
*   **Optimization & Performance:** Implements caching strategies, matrix builds, and runner selection (hosted vs. self-hosted) to minimize runtime and cost.
*   **Security Hardening:** Advises on best practices for managing secrets, least-privilege permissions, and auditing workflows for vulnerabilities.
*   **Reusability:** Designs modular pipelines by implementing reusable workflows and custom actions to keep configurations DRY (Don't Repeat Yourself).
*   **Troubleshooting & Auditing:** Systematically debugs failing workflows and audits existing setups against a comprehensive quality checklist.

## Example Use Cases
1. **Full Stack Deployment Pipeline:** Generate a workflow that automatically runs unit tests on pull requests, builds Docker images upon merge to `main`, pushes the image to a registry, and deploys it to staging environments using matrix strategies.
2. **Dependency Testing Matrix:** Create a workflow that tests the same codebase against multiple language versions (e.g., Python 3.9, 3.10, 3.11) simultaneously using job matrices.
3. **Secret Management Audit:** Review an existing workflow and refactor it to ensure all sensitive tokens are accessed only via GitHub Secrets or encrypted environment variables.