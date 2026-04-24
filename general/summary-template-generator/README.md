## Overview
This agent is an expert specialist designed to analyze existing summary documents and reverse-engineer the underlying structure into a reusable, formal template. By processing sample documents, it creates a blueprint that ensures future data extraction efforts are consistent, comprehensive, and highly structured.

## Capabilities
*   **Document Analysis**: Utilizes integrated tools to process raw documents and identify key informational components.
*   **Structure Identification**: Automatically detects major sections, subsections, and recurring data patterns within the provided text corpus.
*   **Template Generation**: Creates a detailed template schema that includes clear section names, descriptive guidelines, and specific extraction prompts for AI models.
*   **Schema Enforcement**: Ensures the output adheres to a predefined, structured format (Pydantic model) for reliable downstream use.

## Example Use Cases
*   **Standardizing Meeting Minutes**: Feed it several past meeting summaries to generate a template that consistently captures attendees, action items, and decisions made.
*   **Creating Report Blueprints**: Provide a set of quarterly performance reports; the agent will output a master template ensuring all future reports cover the same critical metrics (e.g., Revenue, YoY Growth, Key Risks).
*   **Onboarding New Data Sources**: When integrating data from a new format, use this agent to analyze samples and generate the necessary structured extraction schema for your pipeline.