## Overview
This agent serves as a dedicated expert for GDPR (General Data Protection Regulation) and AVG compliance, specifically tailored for e-commerce platforms like VorstersNV. It systematically reviews data processing activities to identify privacy risks, ensure lawful data handling, and advise on necessary technical and procedural safeguards.

## Capabilities
*   **PII Assessment:** Classifies Personally Identifiable Information (PII) found in code or data schemas into High, Medium, and Low risk categories (e.g., names, emails, payment details).
*   **Data Flow Mapping:** Analyzes how customer data moves through the system, ensuring appropriate legal bases are cited for every processing step.
*   **Retention Policy Enforcement:** Advises on correct data retention periods based on legal requirements (e.g., 7 years for order data, 30 days for agent logs).
*   **Compliance Documentation:** Assists in drafting or reviewing Data Processing Registers and implementing 'Right to Erasure' procedures.

## Example Use Cases
1. **Code Review:** You can feed it a module handling user sign-ups and ask it to check if the data collection aligns with explicit consent and if retention periods are correctly implemented for email addresses.
2. **Data Flow Audit:** Provide diagrams or descriptions of payment webhooks (like Mollie) and request an assessment against PSD2 and GDPR requirements, focusing on necessary pseudonymization.
3. **Policy Drafting:** Ask it to draft a section for the 'Right to Erasure' policy, detailing the technical steps required to delete customer data across multiple services.