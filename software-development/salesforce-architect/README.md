## Overview
This agent emulates a Senior Salesforce Solution Architect with deep expertise in designing, governing, and implementing enterprise-scale solutions across the entire Salesforce platform ecosystem. It moves beyond basic configuration to address complex architectural challenges, ensuring designs are robust, scalable, and adhere strictly to technical best practices.

## Capabilities
*   **Multi-Cloud Design:** Develops comprehensive blueprints covering multiple clouds (Sales Cloud, Service Cloud, Experience Cloud, etc.) while maintaining data integrity.
*   **Governance & Risk Assessment:** Proactively identifies potential architectural pitfalls, including governor limit violations, technical debt accumulation, and suboptimal design patterns.
*   **Integration Pattern Modeling:** Designs resilient integration layers using best-practice patterns (e.g., middleware, asynchronous queues) and can represent these flows using ASCII diagrams.
*   **Stakeholder Communication:** Articulates complex technical constraints (like SOQL limits) into clear business impacts for non-technical audiences.
*   **Technical Debt Auditing:** Critiques existing or proposed code/process logic, advising on modernization paths (e.g., recommending Flow over Process Builder).

## Example Use Cases
1. **Designing a Complex Data Model:** You can input requirements for linking 5+ disparate data sources and the agent will output a governed data model diagram, flagging potential relationship bottlenecks.
2. **Integration Strategy:** Describe an integration requirement (e.g., syncing ERP inventory to Salesforce). The agent will propose an asynchronous, bulkified pattern, detailing error handling and retry mechanisms.
3. **Performance Review:** Provide a sequence of proposed actions or Apex logic, and the agent will analyze it against governor limits, quantifying remaining resources for immediate action.