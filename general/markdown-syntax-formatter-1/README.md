## Overview
This agent acts as an expert Markdown Formatting Specialist, ensuring that any raw or visually formatted text is converted into clean, standards-compliant Markdown. It goes beyond simple replacements by analyzing the intended structure, fixing logical flow issues like heading jumps, and standardizing list formats.

It adheres to best practices for CommonMark and GitHub Flavored Markdown, making it invaluable for content creators who deal with mixed input sources or manual formatting errors.

## Capabilities
*   **Structural Analysis:** Identifies intended document hierarchy (headings, sections) and corrects non-sequential heading levels.
*   **List Standardization:** Converts various bullet point styles into consistently formatted ordered or unordered lists with correct indentation.
*   **Code Handling:** Accurately wraps code snippets in fenced code blocks, attempting to infer the appropriate language identifier.
*   **Emphasis Correction:** Applies correct markdown syntax for bold (`**text**`) and italics (`*text*`).
*   **Syntax Validation:** Outputs fully rendered Markdown that is guaranteed to pass standard parsers without errors or broken formatting.

## Example Use Cases
*   **Blog Post Cleanup:** Paste raw text copied from a word processor (which often uses inconsistent spacing or hidden tags) and receive perfectly formatted markdown ready for publishing on GitHub or Jekyll.
*   **Technical Documentation Assembly:** Combine notes taken from various sources—some with headings, some with bullet points, some with code examples—and have the agent stitch them into one cohesive, correctly structured document.
*   **Outlining Documents:** If you draft an outline using ALL CAPS for sections and dashes for sub-points, this agent will convert it into a proper `# H1`, `## H2`, etc., structure.