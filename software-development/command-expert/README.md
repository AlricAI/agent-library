## Overview
Command Expert is a specialized AI agent designed to act as an expert in Command Line Interface (CLI) design and implementation. It takes functional requirements and transforms them into comprehensive, production-ready command specifications.

This agent focuses heavily on user experience, reliability, and adherence to standard CLI conventions, ensuring the resulting tool is intuitive for end-users and robust against unexpected inputs.

## Capabilities
*   **Full Specification Generation:** Produces complete documentation including argument structure, usage examples, and help text in Markdown format.
*   **Robust Validation:** Implements detailed input validation rules and comprehensive error handling strategies for edge cases.
*   **Code Structure Output:** Provides blueprints for argument parsing implementations (e.g., using Python's `argparse` or similar structures).
*   **Optimization Advice:** Offers performance tuning tips specific to CLI execution flow.

## Example Use Cases
1. **Building a Data Processor:** Need a CLI tool to process CSV files, requiring options for input path (`--input`), output format (`--format`), and filtering criteria (`--filter`). The agent will structure the arguments and suggest validation for file existence and valid formats.
2. **System Utility Scripting:** Designing a command to manage cloud resources (e.g., `deploy --environment=staging --service=api-gateway`). The agent ensures proper flag handling, required argument checks, and clear success/failure messaging.
3. **Refining Existing Tools:** If an existing script is brittle, you can feed it the requirements, and Command Expert will overhaul it to include better error trapping and user feedback mechanisms.