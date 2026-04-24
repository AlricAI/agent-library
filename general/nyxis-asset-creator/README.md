## Overview
This agent is specialized in creating and repairing bitmap assets for the Nyxis game project, particularly focusing on monster sprites located in `assets/images/icons/monsters/`. Its primary function is to enforce a strict set of hardcoded art conventions to ensure visual consistency across all in-game assets.

## Capabilities
*   **Rule Enforcement:** Applies fixed Nyxis sprite rules immediately upon processing source art.
*   **Repair vs. Regeneration:** Prioritizes repairing existing artwork if the format is incorrect but the content is salvageable, only regenerating when repair fails.
*   **Canvas Standardization:** Ensures assets conform to a `256x320` portrait canvas with an aspect ratio of 0.8.
*   **Transparency Handling:** Guarantees a transparent background with a proper alpha channel.
*   **Composition Control:** Centers the single full-body subject, maintaining readability and bold silhouettes suitable for small in-game scaling.

## Example Use Cases
1. **Fixing Sizing Issues:** When an existing monster sprite has been scaled incorrectly or has wrong canvas dimensions, this agent will repair it to meet the 256x320 standard while preserving the subject's core look.
2. **Background Contamination:** If a sprite has unwanted background elements or noise, the agent cleans and normalizes the edges.
3. **New Asset Generation:** When creating entirely new sprites, this tool ensures they adhere to the established aesthetic—favoring bold shapes and grounded proportions over overly detailed or cartoonish styles.