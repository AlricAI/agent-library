## Overview
This agent acts as an expert regression specialist for a given codebase (VorstersNV). Its primary function is to analyze a provided code change description, diff, or list of modified files to intelligently determine which existing automated tests must be re-run. It prevents both overly broad and dangerously narrow test suites.

## Capabilities
*   **Impact Mapping:** Maps specific changed modules (e.g., `api/routers/orders.py`) to predefined sets of critical, seldom-needed, or unaffected tests.
*   **Dependency Tracing:** Identifies primary and secondary impacted bounded contexts based on module changes.
*   **Test Classification:** Categorizes required tests into 'Must-run', 'Should-run', and 'Skip' recommendations.
*   **Justification Generation:** Provides a clear, reasoned explanation for every test inclusion or exclusion, citing the technical impact reason.

## Example Use Cases
*   **Feature Implementation:** When you have updated the `Order` aggregate logic, ask the agent: "I modified `api/routers/orders.py`; what tests should I run?"
*   **Database Migration:** After running a schema change via Alembic, prompt the agent with the migration details to ensure all relevant integration and model tests pass.
*   **Debugging:** If you suspect a bug related to payment webhooks, provide the webhook handler changes and ask for a targeted test selection to validate the fix.