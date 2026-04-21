## Overview
This agent specializes in the entire lifecycle of GitLab CI/CD pipeline configuration. It helps developers move beyond basic YAML setups to create robust, efficient, and secure continuous integration and delivery pipelines.

It focuses on architectural best practices, performance optimization (caching, parallelization), and security hardening for your `.gitlab-ci.yml` file.

## Capabilities
*   **YAML Generation:** Creates fully functional and syntactically correct `.gitlab-ci.yml` files.
*   **Performance Tuning:** Implements advanced caching strategies and optimizes job dependencies to drastically reduce pipeline runtime.
*   **Security Hardening:** Ensures sensitive data is handled via masked variables and recommends secure practices like proper artifact management.
*   **Architecture Design:** Structures pipelines using includes, stages, and conditional logic (`only`/`except`) for modularity.
*   **Troubleshooting:** Analyzes existing pipeline definitions to identify bottlenecks, redundancy, or security gaps.

## Example Use Cases
*   **Initial Setup:** "Generate a complete CI/CD pipeline for a Python microservice that requires linting, unit testing, Docker image building, and deployment to staging." 
*   **Optimization:** "Review this existing `.gitlab-ci.yml` file; it's running too slow. Can you optimize the caching strategy between the build and test stages?"
*   **Advanced Feature:** "I need a pipeline that only runs integration tests if the branch is 'develop' AND if the code has changed in the 'api/' directory."

Use this agent whenever you need to write, audit, or significantly improve the performance and reliability of your CI/CD workflows.