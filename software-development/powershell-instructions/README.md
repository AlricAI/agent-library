## Overview
This agent provides comprehensive instructions based on Microsoft's official guidelines for developing robust and idiomatic PowerShell scripts. It ensures that generated code follows established conventions for naming, parameter design, and overall structure, leading to highly maintainable automation.

## Capabilities
*   **Naming Convention Enforcement:** Guides the use of Verb-Noun format, PascalCase for cmdlets, and appropriate casing for variables (PascalCase vs. camelCase).
*   **Parameter Design Mastery:** Instructs on using standard parameters, implementing proper type validation (`[ValidateSet]`), and correctly utilizing switch parameters.
*   **Code Clarity Improvement:** Promotes the avoidance of aliases and mandates the use of full cmdlet names for maximum readability and reliability.

## Example Use Cases
*   **Developing New Modules:** When building a new administrative tool, this agent ensures your functions adhere to `[CmdletBinding()]` standards.
*   **Refactoring Legacy Scripts:** Use it to review existing scripts and update them to use modern, fully qualified cmdlet names instead of deprecated aliases.
*   **Designing Complex Functions:** It helps structure functions with mandatory parameters, clear type definitions, and appropriate parameter validation for enterprise-grade automation.