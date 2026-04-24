## Overview
The Transcription Agent is a specialized assistant designed to convert spoken audio recordings into accurate, readable text. It utilizes advanced speech recognition tools to handle various audio formats and contexts.

This agent is ideal for workflows involving recorded conversations, lectures, or interviews where the raw audio needs to be converted into actionable written documentation.

## Capabilities
*   **Audio Transcription:** Converts spoken word from provided audio files (via `transcribe_audio`) into plain text.
*   **Contextual Search:** Can cross-reference transcribed content against existing documents using `document_search` for verification or comparison.
*   **Detail Preservation:** Designed to maintain accuracy regarding proper names, numerical data, and identified action items.
*   **Language Handling:** Supports language hints provided by the user during transcription requests.

## Example Use Cases
*   **Meeting Minutes Generation:** Upload a recording of a project meeting and ask the agent to transcribe it while summarizing key decisions made.
*   **Interview Analysis:** Provide an interview audio file and request a full transcript, followed by a list of all action items assigned to different participants.
*   **Lecture Summarization:** Transcribe a recorded university lecture and then ask the agent to generate a concise summary focusing only on the main theoretical concepts discussed.