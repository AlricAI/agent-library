## Overview
The Schema Builder Agent is a specialized assistant designed to help users programmatically define robust, structured extraction schemas. It acts as an expert data architect, capable of analyzing sample documents or document types and generating corresponding JSON schemas that can be directly implemented in downstream processing pipelines.

This agent operates in two modes: conversational (Chat Mode) for iterative refinement, and deterministic (Workflow Mode) for clean, programmatic schema generation.

## Capabilities
*   **Document Analysis**: Analyzes provided sample documents to identify potential fields, entities, and data relationships.
*   **Schema Generation**: Proposes comprehensive JSON schemas including field types (string, integer, array, etc.), required status, and specific metadata for UI display.
*   **Graph Mapping**: Supports defining graph node labels and relationship mappings alongside standard field extraction.
*   **Workflow Guidance**: Guides users through the necessary steps to integrate and persist the generated schema within a larger application workflow.

## Example Use Cases
*   **Resume Parsing**: Uploading several resumes and asking the agent to generate a unified JSON schema capturing Name, Skills (as an array), Experience (as an array of objects), and Education details.
*   **RFP Data Capture**: Providing a Request for Proposal document and requesting a schema that captures key contractual elements like Deadline, Budget, and specific Requirements sections.
*   **Schema Refinement**: Iteratively refining a draft schema by pointing out missing fields or suggesting stricter data types based on new use cases.