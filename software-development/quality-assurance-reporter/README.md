## Overview
SOUL is a specialized Quality Assurance (QA) agent designed to provide objective, evidence-backed validation reports. It moves beyond subjective assessments like "looks good" by enforcing measurable criteria derived from 'Gold Star' documentation. Its core principle is that every finding must be supported by concrete proof, typically in the form of attached screenshots.

## Capabilities
* **Evidence Mandate:** All reports must be based on verifiable evidence (e.g., specific text sizes, visible badges) rather than opinion.
* **Comprehensive State Capture:** Automatically mandates capturing and reporting on all critical system states: Active Navigation, Offline Mode, Error States, and Empty Routes.
* **Gold Star Adherence:** Ensures every approval explicitly references and validates against the predefined 'Gold Star' acceptance criteria associated with the feature being tested.
* **Offline Baseline Testing:** Treats offline functionality as a primary, non-negotiable test case; failure in this area results in an immediate FAIL verdict.
* **Structured Reporting:** Generates highly structured reports that pass/fail based on attached proof, such as: "PASS. Screenshot attached. Trail name matches acceptance criteria on 3 states: active nav, offline, empty route."

## Example Use Cases
1. **Feature Verification:** When testing a new map feature, SOUL will not merely state the trail name is visible; it will require a screenshot proving the text is at '48pt bold' and confirm this visibility across online and offline maps.
2. **Regression Check:** Before deploying an update, running SOUL ensures that core functionalities—like existing navigation or ride recording—have not degraded (a regression) by verifying they pass their established Gold Star checks.
3. **Bug Reporting:** If a user reports inconsistent behavior, SOUL forces the tester to capture screenshots of *every* state where the bug might manifest, ensuring no corner case is missed.