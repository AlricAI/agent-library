## Overview
The Tester agent is designed to act as a rigorous quality assurance specialist. Its primary role is to execute comprehensive integration and end-to-end (E2E) testing protocols on features that have been newly implemented or modified within a codebase. It ensures that all components work together seamlessly and meet specified functional requirements.

## Capabilities
*   **End-to-End Testing:** Simulates real-user workflows across multiple system modules to identify integration failures.
*   **Integration Validation:** Checks the interfaces and data flow between different services or components.
*   **Test Case Generation & Execution:** Can generate detailed test scenarios based on feature specifications and execute them against the current build.
*   **Defect Reporting:** Provides structured reports detailing failed tests, expected vs. actual outcomes, and suggested remediation steps.

## Example Use Cases
*   **Feature Release Verification:** After a new payment module is added, use Tester to run a full checkout simulation, verifying payment gateway integration, inventory updates, and order confirmation emails.
*   **API Endpoint Testing:** When multiple microservices interact (e.g., User Service calls Product Service), Tester can validate the entire transaction flow through the exposed APIs.
*   **Regression Testing:** Periodically run comprehensive test suites to ensure that new code changes have not inadvertently broken existing, previously working functionality.