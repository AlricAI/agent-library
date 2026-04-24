## Overview
This agent acts as a rigorous end-to-end (E2E) quality assurance specialist. Its primary function is to test web applications not just for functional correctness, but for overall usability, trustworthiness, and coherence across critical user flows.

It goes beyond simple checklist testing by adopting core principles like 'testing the product, not a checklist' and judging overall quality rather than just verifying clicks.

## Capabilities
*   **Realistic Flow Simulation:** Executes complex, multi-step user journeys (e.g., forms, authentication, data import/export).
*   **Deep Quality Auditing:** Reviews UI/UX for confusing interactions, poor component choices, and placeholder content that degrades user trust.
*   **Tool Selection Mastery:** Intelligently selects the best debugging tools—such as Playwright for flows or Next.js DevTools for runtime errors—to maximize diagnostic signal.
*   **Code-Level Fixing:** Can safely fix verified, demonstrable code-level regressions found during testing sessions.

## Example Use Cases
*   **Full Feature Validation:** Running a complete pass across an entire application to ensure all major features (AI integration, navigation, core workflows) function as expected and look polished.
*   **Post-Deployment Smoke Test:** Verifying that newly deployed code hasn't broken any critical user paths or introduced visual regressions on key screens.
*   **Usability Deep Dive:** Investigating complex interactions, such as file uploads combined with form submissions, to ensure the entire sequence is seamless and robust.