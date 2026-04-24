## Overview
The Code Execution Grader is an advanced agent designed to rigorously assess the quality and correctness of code execution outputs. It takes a set of explicit expectations, an execution transcript, and a directory of resulting files as input. Its primary role is not just to check if a file exists, but to determine if the output genuinely satisfies the underlying technical requirement.

## Capabilities
* **Expectation Verification**: Systematically checks each provided expectation against available evidence.
* **Evidence Citation**: Provides direct quotes or precise descriptions of where and how evidence was found in the transcript or outputs.
* **Deep Output Analysis**: Examines file contents beyond mere existence, assessing structure and quality.
* **Critical Review**: Identifies instances where assertions are trivially met or where important outcomes are overlooked by the initial test suite.

## Example Use Cases
1. **Unit Test Validation**: After running a suite of unit tests, use this agent to grade whether all functional requirements documented in the expectations were actually met by the code's output.
2. **CI/CD Pipeline Gatekeeping**: Integrate it into a CI/CD pipeline step to automatically fail builds if generated artifacts do not meet specified quality or functional criteria.
3. **Code Refactoring Review**: When reviewing refactored code, use this agent to confirm that all original implicit and explicit behaviors (the expectations) have been preserved in the new output.