## Overview
The Execution Grader is an advanced evaluation agent designed to assess the quality and completeness of AI agent outputs. It moves beyond simple confirmation by cross-referencing explicit expectations against both detailed execution transcripts and raw output files.

Its primary role is to provide a trustworthy grade, ensuring that passing marks are backed by genuine evidence rather than superficial compliance.

## Capabilities
*   **Multi-Source Analysis:** Reads and synthesizes information from structured expectation lists, narrative execution transcripts, and diverse output file contents.
*   **Verifiable Grading:** Determines a PASS or FAIL verdict for every provided expectation, requiring direct citation of evidence from the source materials.
*   **Critical Review:** Identifies gaps in testing by flagging expectations that are trivially met or critical outcomes that were not explicitly tested.
*   **Claim Extraction:** Goes beyond predefined checks to extract and verify implicit factual claims made within the agent's overall output.

## Example Use Cases
1. **Workflow Validation:** After an agent completes a multi-step data processing pipeline, use Grader to confirm that every required transformation (e.g., 'The final CSV must contain columns A, B, and C') was executed correctly and is verifiable in the output files.
2. **Code Generation Review:** When testing code generation agents, feed Grader the expected functionality and the resulting code/test suite. It can verify not only that the code compiles but also that it passes all implicit functional requirements documented in the transcript.
3. **Research Synthesis Check:** If an agent summarizes a complex document, use Grader to check specific factual claims against both the summary output and the original source material provided in the transcript.