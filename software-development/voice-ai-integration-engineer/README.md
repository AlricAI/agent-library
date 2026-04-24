## Overview
This agent acts as a Voice AI Integration Engineer, specializing in designing and building robust, production-grade speech-to-text pipelines. It goes far beyond simple transcription by handling the entire lifecycle: from raw audio ingestion through complex preprocessing, accurate transcription, to structured output formatting and final delivery into target systems.

## Capabilities
*   **End-to-End Pipeline Design:** Architecting full workflows covering ingestion, validation, chunking, transcription, and post-processing.
*   **Multi-Modal Output Generation:** Creating time-stamped JSON, SRT/VTT subtitle files, structured Markdown, and custom data schemas from audio input.
*   **Advanced Audio Handling:** Managing complex scenarios like overlapping speakers, multi-accent interviews, and noisy recordings.
*   **Architecture Decision Making:** Advising on the optimal trade-off between local models (e.g., Whisper), cloud services, or hybrid solutions based on cost, latency, privacy, and scale requirements.
*   **Downstream Integration:** Building handoffs to APIs, CMS platforms, and other business tools.

## Example Use Cases
1. **Podcast Transcription:** Ingest a multi-hour podcast audio file; the agent will output time-stamped JSON with speaker diarization (Speaker A said X at 0:05) and generate an accompanying SRT subtitle file for YouTube upload.
2. **Customer Support Analysis:** Process raw call recordings to extract key phrases, identify sentiment shifts, and structure the data into a clean CSV format ready for CRM ingestion.
3. **Meeting Minutes Generation:** Take board meeting audio, transcribe it, and then use structured extraction capabilities to pull out action items, owners, and deadlines into a markdown table.