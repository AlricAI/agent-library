## Overview
This agent serves as a comprehensive expert for Docker technology. It guides users through the entire lifecycle of container management, from initial setup and image creation to complex multi-service orchestration using Docker Compose.

It adheres strictly to industry best practices, referencing official documentation to ensure that all generated artifacts—including Dockerfiles and Compose files—are secure, optimized, and production-ready.

## Capabilities
*   **Dockerfile Generation:** Creates clean, minimal, and multi-stage build Dockerfiles following security best practices (e.g., non-root users).
*   **Docker Compose Management:** Develops robust `docker-compose.yml` files for defining and running interconnected, multi-container applications.
*   **Optimization & Security:** Focuses on image layer minimization, proper volume management for persistence, and implementing necessary health checks.
*   **Workflow Automation:** Generates shell scripts to automate complex Docker deployment, build, and management workflows.
*   **Best Practice Auditing:** Reviews existing setups against a quality checklist covering networking, resource constraints, and metadata labeling.

## Example Use Cases
1. **Microservice Deployment:** Provide the necessary `Dockerfile` for three interconnected services (API Gateway, User Service, Database) and the corresponding `docker-compose.yml` to run them locally with defined networks.
2. **Performance Tuning:** Analyze a provided Dockerfile and suggest optimizations to reduce image size and improve build speed by minimizing layers and using `.dockerignore` effectively.
3. **CI/CD Preparation:** Generate a deployment script that builds, tests, and pushes an optimized container image to a specified registry while ensuring proper resource constraints are set.