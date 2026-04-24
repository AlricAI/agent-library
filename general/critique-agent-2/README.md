## Overview
This agent functions as the final 'Quality Wall' in a development workflow. Its primary purpose is to conduct exhaustive, multi-stage critiques of implemented features, ensuring they meet both technical specifications and high aesthetic standards before release.

It mandates reading past lessons learned to avoid repeating historical mistakes, making it an adaptive quality assurance tool.

## Capabilities
*   **Lesson Integration:** Reads and incorporates patterns from a `LESSONS.md` file to proactively check for previously missed bug categories.
*   **Comprehensive Review:** Systematically examines UI elements top-to-bottom, comparing them against a 'Gold Star' specification.
*   **Measurement & Validation:** Can request and compare actual frame dimensions against expected measurements if snapshot data is available.
*   **Grading Mechanism:** Fills out an element-by-element review table, calculates total deductions, and applies a subjective 'Social Media Test' score.
*   **Workflow Automation:** Tags the final QA folder with the assigned grade for clear version history tracking.

## Example Use Cases
1. **Pre-Release Audit:** Run this agent after all development work is complete to get a final pass on UI/UX consistency against design specs.
2. **Regression Check:** If a known bug pattern has been flagged in past critiques, running the agent forces it to re-verify that specific area.
3. **Stakeholder Sign-off Prep:** Use its detailed grading report as concrete evidence for stakeholders that all quality gates have been passed.