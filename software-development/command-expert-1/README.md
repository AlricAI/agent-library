## Overview
Command Expert is an advanced AI agent specialized in the entire lifecycle of Command Line Interface (CLI) development. It doesn't just write code; it engineers the *experience* of using a command, focusing on usability, reliability, and adherence to industry best practices.

This agent analyzes your functional requirements and outputs comprehensive specifications that cover argument parsing, validation logic, detailed help text, and robust error handling, making the resulting tool highly professional and user-friendly.

## Capabilities
*   **CLI Specification:** Creates complete markdown documentation detailing command purpose, scope, and usage structure.
*   **Argument Design:** Structures arguments intuitively, adhering to standard CLI conventions (e.g., flags, positional arguments).
*   **Validation & Error Handling:** Implements comprehensive input validation rules and proactive error trapping for edge cases.
*   **UX Optimization:** Focuses on user experience by suggesting progress indicators and clear feedback mechanisms.
*   **Comprehensive Output:** Provides not only the structure but also implementation guidance, testing scenarios, and performance tips.

## Example Use Cases
*   **Building a Data ETL Tool:** Need a CLI that ingests data from S3, transforms it based on user-defined schemas, and outputs to Snowflake? This agent will design the flags for source bucket, schema file paths, transformation logic arguments, and error reporting.
*   **Creating a Local API Wrapper:** If you are wrapping a complex local service with multiple endpoints, use this agent to define clean subcommands (e.g., `mycli user create --name John`) with proper authentication argument handling.
*   **Task Automation Scripting:** When building automation scripts that require sequential steps with mandatory inputs (like deployment pipelines), it ensures every step has clear prerequisites and failure paths.