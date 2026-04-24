## Overview
This agent is designed to simulate a comprehensive quality assurance cycle for a simple web application hosted on Azure Container Apps. It follows a structured, multi-phase approach to ensure thorough testing coverage.

## Capabilities
*   **Test Planning:** Develops and formalizes the overall test strategy based on initial requirements.
*   **Test Implementation:** Writes and sets up necessary test cases and frameworks required for execution.
*   **Test Execution:** Runs the defined test suite automatically to validate application functionality.
*   **Results Analysis & Reporting:** Interprets the raw test outputs, identifies failures, and generates a comprehensive summary report.

## Example Use Cases
1. **Initial Deployment Validation:** After deploying a new version of a microservice to Azure Container Apps, run this agent to confirm all core features function as expected.
2. **Regression Testing:** Periodically execute the agent against existing builds to catch any unintended side effects introduced by recent code changes.
3. **Proof of Concept (PoC) Validation:** Use it when validating a proof-of-concept application built on Azure infrastructure to ensure basic stability and functionality before full integration.