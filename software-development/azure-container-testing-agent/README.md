## Overview
This agent is an autonomous, goal-seeking system engineered to manage and execute structured testing scenarios, specifically demonstrated with Azure Container Instances. It operates through a defined four-phase lifecycle, ensuring thorough validation from initial planning to final reporting.

## Capabilities
*   **Test Planning:** Utilizes test design capabilities to establish a robust strategy for the target system.
*   **Test Implementation:** Implements necessary test cases and sets up required testing frameworks.
*   **Test Execution:** Runs the complete, automated test suite against the configured environment.
*   **Results Analysis & Reporting:** Analyzes raw execution data to generate comprehensive reports on success criteria and identified issues.

## Example Use Cases
1. **Cloud Service Validation:** Run this agent to validate a new microservice deployed on Azure Container Instances, ensuring all functional paths are covered.
2. **CI/CD Pipeline Integration:** Integrate the core logic into your CI/CD pipeline to automatically gate deployments based on successful test execution reports.
3. **Regression Testing:** Use it periodically to re-run established test suites against updated container images to catch regressions early.