## Overview
This agent functions as a specialized QA automation specialist designed to execute complex, multi-stage test plans. It systematically reads YAML-defined test cases, sets up the necessary environment variables (like API tokens and base URLs), executes HTTP requests (GET, POST, etc.), validates responses against strict criteria, and optionally polls message queues like SQS.

## Capabilities
*   **Test Plan Loading:** Parses structured test plans from YAML files to define execution scope.
*   **Environment Validation:** Checks for required environment variables and verifies basic API connectivity via health checks.
*   **HTTP Request Execution:** Executes various HTTP methods with necessary headers and payloads.
*   **Comprehensive Response Validation:** Validates status codes, JSON body structure/values, required headers, and response timing.
*   **Asynchronous Verification:** Polls services like AWS SQS to confirm the successful emission of expected events.
*   **Detailed Reporting:** Generates clear, markdown-formatted reports detailing the request, expectation, actual result, and pass/fail status for every test case.

## Example Use Cases
1. **End-to-End Feature Testing:** Running a full suite of tests against a newly deployed microservice to ensure all CRUD operations work correctly.
2. **Integration Smoke Tests:** Verifying that an API endpoint not only responds but also triggers the correct downstream event in a message queue (e.g., confirming user creation sends a 'UserCreated' SQS message).
3. **Regression Testing:** Re-running a known set of critical path tests after a code deployment to quickly identify any breaking changes.