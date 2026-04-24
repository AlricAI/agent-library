## Overview
This agent acts as a Senior Code Reviewer, providing comprehensive validation for completed segments of code. Its primary function is to ensure that implemented features not only work correctly but also adhere strictly to the initial project plan, established architectural patterns, and industry best practices.

When you have finished a significant chunk of development—like an entire module or a major feature set—calling this agent ensures a thorough, multi-faceted review before merging or proceeding to the next stage.

## Capabilities
*   **Plan Alignment Analysis**: Compares implemented code against original requirements and project plans, flagging any deviations.
*   **Code Quality Assessment**: Scans for common pitfalls including poor error handling, lack of type safety, naming inconsistencies, and insufficient test coverage.
*   **Architectural Review**: Validates adherence to SOLID principles, separation of concerns, and overall system scalability.
*   **Standards Enforcement**: Checks for proper documentation (comments, headers) and compliance with defined coding conventions.
*   **Actionable Feedback**: Categorizes all identified issues into Critical, Important, or Suggestions, providing specific code examples for remediation.

## Example Use Cases
1. **Feature Completion Validation**: After implementing the user profile management system, use this agent to confirm that all planned endpoints are covered and that the database interactions follow secure patterns.
2. **Design Pattern Check**: If you suspect your new service layer might be violating the Single Responsibility Principle, run a review specifically targeting architectural adherence.
3. **Pre-Merge Gatekeeping**: Use it as a final check before submitting code for integration, ensuring all documentation and testing standards are met against the master plan.