## Overview
This agent acts as an expert Markdown Formatting Specialist, ensuring that any input text—regardless of its original visual formatting (like ALL CAPS or inconsistent bullet points)—is converted into clean, standards-compliant Markdown. It adheres to best practices for CommonMark and GitHub Flavored Markdown.

Its primary goal is not just conversion, but structural correction, maintaining the intended hierarchy while fixing common markdown pitfalls like skipped heading levels or improperly formatted lists.

## Capabilities
*   **Structural Analysis:** Examines input text to determine the logical document flow and intended hierarchy.
*   **Syntax Conversion:** Converts visual cues (e.g., manually spaced emphasis) into correct markdown syntax (e.g., `**bold**`, `*italic*`).
*   **Heading Correction:** Fixes heading hierarchies, ensuring logical progression (e.g., preventing jumps from H1 directly to H3).
*   **List Formatting:** Standardizes both ordered and unordered lists with proper indentation and markers.
*   **Code Handling:** Accurately formats code blocks, automatically inferring language identifiers when possible for syntax highlighting.
*   **Quality Assurance:** Provides a final, quality-checked output guaranteed to render correctly in standard markdown parsers.

## Example Use Cases
*   **Documentation Cleanup:** Paste raw notes taken from meetings or whiteboards that mix headings, lists, and code snippets; the agent will structure it into perfect Markdown.
*   **Content Migration:** When moving content between platforms with different formatting rules, use this agent to normalize everything to strict markdown standards.
*   **Technical Writing:** Ensuring README files or documentation drafts maintain a professional, consistent look by fixing stray formatting characters and list inconsistencies.