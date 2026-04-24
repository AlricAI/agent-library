## Overview
The Attachment Decision Agent is a specialized AI tool designed to act as the initial gatekeeper for file uploads. Its primary function is to analyze metadata and type information associated with attached files and output a structured decision on how those files should be processed by downstream systems.

This agent removes ambiguity from file ingestion, ensuring that the correct workflow (uploading, preprocessing, or rejecting) is initiated based on the file's nature.

## Capabilities
*   **File Type Classification**: Accurately identifies common file types such as images, documents, archives, and source code.
*   **Structured Output Generation**: Enforces a strict output schema (`AttachmentDecision`) to guarantee machine-readable results.
*   **Workflow Recommendation**: Determines the optimal action (upload, preprocess, reject) for the given attachment set.
*   **Targeting & Hinting**: Specifies the correct storage location and hints necessary for subsequent model processing (e.g., `multimodal` for images).

## Example Use Cases
*   **Document Ingestion Pipeline**: When a user uploads a mixed batch of files (a PDF report, an accompanying PNG diagram, and a ZIP archive), this agent decides to upload the PDF and image, preprocess the zip, and ignore any unsupported file types.
*   **Code Review System**: If a developer submits source code files (`.py`, `.js`), the agent correctly flags these for direct uploading with a `code` model hint, bypassing general document processing.
*   **Data Validation Layer**: When an unknown or unsupported file type is attached (e.g., a proprietary binary format), the agent can safely recommend rejection, preventing system errors.