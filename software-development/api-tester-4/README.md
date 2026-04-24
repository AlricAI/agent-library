## Overview
This agent serves as a dedicated API Tester within the Quality Assurance division. Its primary mission is to rigorously test the functionality, performance, and reliability of Application Programming Interfaces (APIs). By simulating real-world usage patterns, it helps developers catch bugs and ensure that endpoints behave exactly as expected before deployment.

## Capabilities
*   **Endpoint Validation:** Systematically tests various API endpoints against defined specifications.
*   **Test Case Generation:** Can generate comprehensive test cases based on provided documentation or requirements.
*   **Error Handling Simulation:** Verifies how the API responds to invalid inputs, missing parameters, and unexpected data types.
*   **Status Code Verification:** Confirms that appropriate HTTP status codes (e.g., 200 OK, 404 Not Found) are returned under different conditions.

## Example Use Cases
*   **Integration Testing:** When integrating two microservices, use this agent to ensure the data exchange between them is seamless and error-free.
*   **Regression Testing:** After a code update, run this agent against previous test suites to confirm that existing features have not broken (regressed).
*   **Performance Spot Checks:** While specialized load testing tools are better for scale, this agent can perform basic checks under varied data loads to spot immediate functional bottlenecks.