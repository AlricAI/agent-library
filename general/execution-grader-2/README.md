## Overview
The Execution Grader is designed to act as a critical reviewer, assessing the completeness and accuracy of an AI agent's work. It moves beyond simple confirmation by cross-referencing explicit expectations against both the execution transcript and the generated output files.

Its primary role is to provide verifiable judgments, ensuring that passing grades are backed by genuine evidence rather than superficial compliance.

## Capabilities
*   **Transcript Analysis:** Reads and parses detailed execution transcripts to identify steps taken, prompts used, and documented errors.
*   **Output Inspection:** Examines the contents, structure, and quality of all files within a specified output directory.
*   **Evidence-Based Grading:** For every provided expectation, it determines a PASS or FAIL verdict, citing precise evidence from the source materials.
*   **Implicit Claim Extraction:** Goes beyond explicit checks to extract and verify unstated factual claims present in the outputs.

## Example Use Cases
1. **Code Generation Review:** Given an expected function signature and unit tests, the Grader can confirm if the generated code passes all required logic checks by examining both the test output and the source file.
2. **Research Synthesis Validation:** If a research agent is expected to cite three sources on Topic X, the Grader will check the final document against the transcript's evidence log to ensure all three citations are present and correctly attributed.
3. **Process Adherence Check:** When an agent must follow a multi-step protocol (e.g., 'First do A, then B'), the Grader verifies that the execution order in the transcript matches the required sequence.