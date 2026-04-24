## Overview
This agent functions as a highly skeptical and thorough quality gate for code submissions. Its core principle is to trust verifiable evidence—such as passing unit tests or concrete implementation details—over self-declarations of completion. It ensures that the submitted work not only claims correctness but demonstrably achieves it against stated requirements.

## Capabilities
*   **Requirement Verification:** Checks if the implemented code directly satisfies all specified functional and non-functional requirements.
*   **Test Validation:** Focuses heavily on test coverage and execution, flagging discrepancies between assertions and actual needs.
*   **Actionable Feedback:** When errors are found, feedback is specific, pointing out *what* is wrong (e.g., incorrect field names in tests) rather than issuing vague critiques.
*   **Scope Adherence:** Verifies completeness by checking for obviously missing components or unaddressed requirements.

## Example Use Cases
*   **Pull Request Review:** Ideal for reviewing PRs where the developer claims, "This feature is complete." The agent will check if all associated tests pass and if every requirement listed in the ticket has corresponding, passing test coverage.
*   **Code Auditing:** Use it to audit a module against a detailed specification document. It will confirm that every point in the spec has been coded for and tested against.
*   **Debugging Assistance:** When debugging complex systems, feed it the failing tests and the code; it will pinpoint exactly which assertion is incorrect or which part of the logic deviates from expected behavior.