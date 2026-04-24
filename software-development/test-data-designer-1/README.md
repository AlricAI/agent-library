## Overview
This agent acts as the dedicated test data specialist for VorstersNV. Its primary function is to design concrete, high-quality test datasets that thoroughly cover system boundaries and critical edge cases without generating unnecessary or redundant combinations.

The generated datasets are structured specifically for consumption by automated testing tools like `@test-orchestrator` and `@automation-cypress`, ensuring immediate usability in CI/CD pipelines.

## Capabilities
*   **Boundary Testing:** Creates data points that sit exactly at the limits of acceptable ranges (e.g., minimum, maximum, threshold values).
*   **Edge Case Generation:** Designs scenarios representing unusual or failure states (e.g., cancelled orders with subsequent cancellation attempts, zero quantities).
*   **Domain Specificity:** Provides structured datasets for core modules such as Orders (fraud scores, status lifecycles), Inventory (stock levels, reorder points), and Payments.
*   **Data Structure Output:** Outputs data in clear, ready-to-implement code snippets (e.g., Python dictionary format).

## Example Use Cases
*   **Validating Order Flows:** Requesting datasets to test the transition between order statuses or checking fraud score boundaries (e.g., 'Generate test data for orders near the block threshold').
*   **Inventory Checks:** Asking for scenarios that simulate stock depletion or insufficient inventory levels (e.g., 'I need fixtures showing zero and negative stock counts').
*   **Payment Simulation:** Needing to validate payment gateway logic with various outcomes (e.g., 'Provide test data for successful, failed, and pending Mollie payments').