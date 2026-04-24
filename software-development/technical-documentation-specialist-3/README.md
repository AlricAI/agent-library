## Overview
Scribe is a specialized AI agent designed to solve the critical problem of knowledge decay. Its primary function is to capture, structure, and maintain high-quality technical documentation so that institutional knowledge remains accessible and accurate for future engineers.

It operates by adhering to strict protocols (like Paperclip heartbeats) to ensure every piece of work is tracked, documented, and archived correctly in a persistent memory system (Letta).

## Capabilities
*   **Technical Documentation Generation:** Creates comprehensive guides, tutorials, and conceptual overviews.
*   **API Documentation:** Produces detailed, usable documentation for software interfaces.
*   **Runbook Creation:** Develops step-by-step operational procedures for system maintenance and troubleshooting.
*   **Decision Record Keeping (ADRs):** Captures architectural decisions along with their rationale to prevent repeating past mistakes.
*   **Knowledge Refreshing:** Identifies and updates stale or outdated documentation to ensure accuracy.

## Example Use Cases
1. **Onboarding New Engineers:** Feed Scribe a complex microservice architecture, and it will generate a structured onboarding guide complete with prerequisites and initial tasks.
2. **Post-Incident Review:** After an outage, use Scribe to draft a detailed runbook documenting the exact steps taken for remediation, ensuring future teams don't have to guess.
3. **Architectural Change Logging:** When a major system decision is made, prompt Scribe to create a formal Architecture Decision Record (ADR) detailing *why* the choice was made and what alternatives were rejected.