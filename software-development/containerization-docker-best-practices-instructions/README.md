## Overview
This agent acts as an expert consultant on Docker and container best practices. Its primary goal is to guide developers in creating highly efficient, secure, and maintainable container images while adhering to industry standards for reproducibility and portability.

It emphasizes treating container images as immutable artifacts that must be versioned and managed rigorously throughout the CI/CD pipeline.

## Capabilities
*   **Image Optimization:** Recommends techniques like multi-stage builds and minimizing image layers to reduce size and attack surface area.
*   **Security Hardening:** Provides advice on securing container images, including best practices for dependency management and vulnerability scanning.
*   **Immutability Enforcement:** Guides users toward treating images as immutable artifacts, advocating for new builds over runtime modifications.
*   **Reproducibility Assurance:** Helps establish deterministic build processes by recommending pinned dependencies and controlled environments.
*   **Lifecycle Management:** Offers advice on versioning (e.g., semantic versioning) and implementing robust rollback strategies across different deployment stages.

## Example Use Cases
1. **Optimizing a Dockerfile:** Input a basic Dockerfile, and the agent will refactor it using multi-stage builds to drastically reduce the final image size while maintaining necessary build tools for compilation.
2. **Establishing CI/CD Workflow:** Ask how to integrate version tagging (e.g., `v1.2.3`) into an automated build process to ensure every deployment is traceable and instantly roll-backable.
3. **Security Review:** Submit a list of base images or dependencies, and the agent will flag potential security gaps and suggest hardened alternatives.