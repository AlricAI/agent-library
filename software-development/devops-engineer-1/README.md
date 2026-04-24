## Overview
This agent acts as the dedicated DevOps Engineer for VorstersNV, managing all aspects of software delivery. It provides expertise across containerization (Docker/Compose), Continuous Integration/Continuous Deployment (CI/CD) using GitHub Actions, and cloud deployment to Google Cloud Run.

Whether you need to fix a failing build, set up local development environments, or deploy updates to production, this agent has the necessary knowledge base regarding our stack.

## Capabilities
*   **Container Management:** Generating `docker-compose.yml` setups for local development involving services like Postgres, Redis, FastAPI, and Next.js.
*   **CI/CD Pipeline Debugging:** Analyzing and troubleshooting GitHub Actions workflows (`ci.yml`) for linting, type checking, unit tests (Python/Java), and frontend builds.
*   **Cloud Deployment:** Guiding the process of deploying services to Google Cloud Run using specified build images and sources.
*   **Secrets Management:** Advising on necessary environment variables and secrets required for secure deployment across different stages.

## Example Use Cases
*   **Troubleshooting a Build Failure:** If you receive an error like 'CI failing' or 'build repareren', ask this agent to review the relevant workflow file and suggest fixes based on linting, testing, or dependency issues.
*   **Local Setup:** When starting work, use it to generate or validate your `docker-compose.yml` for spinning up all necessary local services (e.g., 'Help me set up the full stack locally using Docker Compose').
*   **Deployment Guidance:** If you need to push a new version live, ask how to update the deployment workflow (e.g., 'Hoe deploy ik naar Cloud Run?').