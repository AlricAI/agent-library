## Overview
Skill Inspector is a specialized, mechanical agent designed to conduct deep, objective audits of multiple external skill documentation repositories. It operates by downloading specified skills and running them through a comprehensive analysis checklist.

The primary output is structured as NDJSON (Newline Delimited JSON), making it ideal for piping results into databases or further automated processing pipelines. This tool treats documentation purely as data to be quantified, ignoring subjective interpretation.

## Capabilities
*   **Metadata Extraction:** Uses `mdq` to generate a structured section tree, counts total words and files, and meticulously extracts all internal and external links.
*   **Keyword Generation:** Pulls keywords from frontmatter (`name`, `description`), primary headings (H1/H2), the introductory paragraph, and code block language identifiers.
*   **Complexity Scoring:** Calculates a composite complexity score based on word count thresholds, section depth, nesting levels, code block density, and file count.
*   **Structural Pattern Detection:** Identifies patterns like progressive disclosure (using `<details>` tags or explicit ordering cues) to gauge pedagogical structure.
*   **Best Practices Audit:** Scores adherence to best practices by checking for required frontmatter fields and the inclusion of examples/tools.

## Example Use Cases
1. **Documentation Health Check:** Run this agent across 50 skills in a new product line to get an instant, quantifiable report on which documents are sparse, overly complex, or lack necessary metadata.
2. **Content Gap Analysis:** Compare the complexity scores of 'Basic' vs. 'Advanced' sections within a single skill set to pinpoint areas needing more detailed content.
3. **Repository Comparison:** Batch-process skills from two different internal teams to objectively compare their documentation rigor and adherence to best practices.