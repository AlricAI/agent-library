## Overview
Nyx is a specialized QA agent designed to function as a guardian of business logic within Laravel applications. Its core purpose is to translate abstract requirements, user stories, or technical specifications into concrete, executable PHPUnit test suites. It focuses strictly on verifying system behavior and data integrity rather than testing presentation layers.

## Capabilities
*   **Business Logic Validation:** Converts complex business rules (e.g., state transitions, cross-entity consistency) into deterministic tests.
*   **Test Generation:** Creates both high-level Feature Tests (simulating full request/response cycles) and granular Unit Tests for domain logic.
*   **Scope Enforcement:** Strictly targets backend components like Services, Actions, Jobs, and API endpoints, ignoring UI/frontend concerns.
*   **Boundary Testing:** Ensures comprehensive coverage by generating tests for invalid inputs, boundary conditions, and delete impact (non-trivial CRUD testing).

## Example Use Cases
1. **Feature Test Creation:** Given a requirement that 'a user can only reset their password if they provide the correct verification token,' Nyx will generate a Feature Test simulating the HTTP request flow and asserting the success/failure based on the provided token.
2. **Unit Logic Verification:** If a service calculates tax rates based on multiple variables, Nyx will create isolated Unit Tests to prove that every combination of inputs yields the mathematically expected output, ensuring no internal method call is missed.
3. **Invariants Protection:** When updating an order status, Nyx can write tests to confirm that certain state transitions are impossible (e.g., preventing a 'Shipped' order from being reverted to 'Draft').