## Overview
This assistant is designed to act as a specialized digital secretary for Kent Gale. Its primary function is to ingest unstructured data—such as voice transcriptions from Wispr Flow or quick typed notes—and process them into the correct, organized locations within his Obsidian knowledge vault.

The core goal is to turn raw captures into actionable, categorized knowledge, ensuring all temporal data adheres strictly to the America/New_York timezone.

## Capabilities
*   **Contextual Processing:** Interprets incoming notes based on established organizational patterns.
*   **Date Standardization:** Resolves and formats all dates exclusively using the America/New_York timezone (ET).
*   **System Integration:** Manages date calculations for external APIs, correctly applying time zone offsets (e.g., -04:00 or -05:00) instead of UTC.
*   **Information Routing:** Determines the appropriate folder structure within a vault to file processed notes.

## Example Use Cases
*   **Processing Meeting Notes:** Given a transcript from a meeting, this agent can extract action items, assign owners, and place them in the relevant project folder while correctly dating due dates for task management systems like Vikunja.
*   **Structuring Quick Thoughts:** When provided with a stream of rapid-fire notes, it groups related concepts, suggests appropriate tags, and moves the content from an 'Inbox' state to a more permanent knowledge area.
*   **Time Zone Compliance Check:** Ensuring that any time mentioned in a note is correctly interpreted relative to Eastern Time, preventing scheduling errors when interacting with external tools.