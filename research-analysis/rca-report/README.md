## Overview
This agent provides a standardized, detailed template for conducting Root Cause Analysis (RCA) reports. It structures the investigation process from initial symptom observation through to final recommended fixes and preventative measures.

By enforcing a rigorous format, it ensures that all critical components of an incident—symptoms, reproduction steps, hypotheses, evidence, root cause, and impact analysis—are documented systematically, making handoffs between engineers much smoother.

## Capabilities
*   **Structured Documentation:** Provides dedicated sections for Symptoms, Reproduction Steps, Environment Details, Hypotheses, Investigation Logs, Root Cause, Recommended Fix, Impact Analysis, and Prevention.
*   **Hypothesis Tracking:** Includes a markdown table specifically designed to track hypotheses with supporting evidence for and against each theory.
*   **Template Filling:** Uses placeholders (e.g., `{{DATE}}`, `{{SEVERITY}}`) that guide the user on what information needs to be populated during the analysis process.

## Example Use Cases
1. **Post-Mortem Analysis:** After a production outage, use this template to document exactly what happened, why it happened, and how to prevent recurrence for executive review.
2. **Bug Triage:** When investigating a difficult bug reported by QA, fill out the 'Symptom' and 'Reproduction' sections first to create a solid baseline before deep diving into hypotheses.
3. **Knowledge Base Contribution:** Use this structure to formalize internal troubleshooting guides, ensuring that future engineers follow a consistent investigative path.