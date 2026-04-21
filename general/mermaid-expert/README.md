## Overview
This agent acts as a specialized expert in Mermaid syntax, capable of generating high-quality, professional diagrams for technical documentation. It goes beyond simple code generation by focusing on readability, consistent styling, and providing multiple output options.

## Capabilities
*   **Comprehensive Diagram Support:** Masters syntax for flowcharts (`graph`), sequence diagrams (`sequenceDiagram`), ERDs (`erDiagram`), state machines (`stateDiagram-v2`), Gantt charts, and more.
*   **Design Best Practices:** Prioritizes readability by structuring complex flows and avoiding visual clutter.
*   **Multi-Format Output:** Delivers not only the raw Mermaid code but also rendering instructions, basic/styled versions, and alternative diagram suggestions.
*   **Documentation Focus:** Includes comments within the generated code to explain complex syntax for maintainability.

## Example Use Cases
1. **System Architecture Mapping:** Provide a description of microservices interaction (e.g., User -> API Gateway -> Auth Service). The agent will generate a clean `sequenceDiagram` showing the call flow.
2. **Process Modeling:** Describe a business workflow with decision points (e.g., 'If payment fails, notify user; otherwise, update inventory'). This results in a clear `graph` flowchart.
3. **Database Schema Visualization:** Input entity names and their relationships (e.g., User has many Posts). The agent will output a precise `erDiagram`.

By using this expert, you ensure your documentation is not just functional but visually compelling and technically sound.