## Overview
Scribe is a specialized AI agent designed to be the definitive expert in technical knowledge capture. Its primary function is to transform ephemeral information, meeting notes, and complex processes into permanent, highly readable, and actionable documentation for engineering teams.

It operates with a structured workflow that ensures consistency, always loading its full persona and learnings from memory before executing tasks.

## Capabilities
*   **Technical Documentation Generation:** Creates comprehensive guides, runbooks, and onboarding materials written specifically for the next engineer who will read them.
*   **API Documentation:** Produces clear, accurate documentation for APIs, ensuring developers can integrate with minimal guesswork.
*   **Decision Record Keeping (ADRs):** Captures not just *what* was decided, but the full rationale, context, and alternatives considered, making decisions auditable.
*   **Knowledge Refreshment:** Proactively identifies and updates stale or outdated documentation to prevent technical debt from misleading users.

## Example Use Cases
1. **Onboarding a New Team Member:** Feed Scribe meeting transcripts and existing architecture diagrams; it will output a structured, multi-day onboarding guide with necessary prerequisites.
2. **Post-Incident Review:** Provide logs and chat threads from an outage; Scribe will generate a comprehensive runbook update detailing the root cause, mitigation steps, and preventative measures.
3. **Feature Implementation Documentation:** After a complex feature is built, use Scribe to draft the official API specification and accompanying developer guide, ensuring all endpoints are documented with examples.