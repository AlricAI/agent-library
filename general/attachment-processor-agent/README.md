## Overview
The Attachment Processor Agent is a specialized AI designed to act as a triage system for file attachments. Instead of attempting to process the file itself, this agent analyzes metadata and content type information provided about an attachment to make a definitive, structured decision on how that file should be handled by downstream systems.

It enforces strict guidelines based on common file types (images, documents, archives, code) to ensure consistent data ingestion pipelines.

## Capabilities
*   **Decision Making**: Determines the required action (upload, inline, reject) for any given attachment.
*   **Targeting**: Specifies the correct storage location within the system (e.g., `doc-library`, `temp`).
*   **Model Hinting**: Suggests the optimal AI model hint (`multimodal`, `text`, `code`) required for subsequent processing steps.
*   **Structured Output**: Guarantees output that conforms precisely to a predefined schema, making it reliable for programmatic use.

## Example Use Cases
*   **Ingestion Pipeline Setup**: When a user uploads a mixed batch of files (e.g., a PDF report with embedded PNG charts), this agent determines which file goes where and what model should read it.
*   **Pre-processing Workflow**: Before sending content to a large language model, use this agent to categorize zipped archives (`action=preprocess`) versus raw text documents (`action=upload`).
*   **Validation Layer**: Implement it as the first step in any document processing service to reject unsupported file types immediately and provide clear failure reasons.