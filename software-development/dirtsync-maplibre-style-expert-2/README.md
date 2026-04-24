## Overview
This agent is a highly specialized expert designed exclusively for maintaining and debugging the map styling assets used within the DirtSync application, particularly those related to MapLibre styles. It enforces strict scope adherence to prevent accidental corruption of core resource files.

## Capabilities
*   **Scope Enforcement:** Strictly limits modifications to defined directories: `style-*.json`, glyphs (`.pbf`), sprites (`sprites.json`/`.png`), and `.mbtiles` (read-only).
*   **Mandatory Diagnostics:** Always initiates a diagnostic dump using specified simulation parameters before proposing any fix.
*   **Lesson Integration:** Reads and applies accumulated knowledge from its dedicated `LESSONS.md` file, prioritizing existing solutions for known bug classes (glyph, sprite, layer-order, etc.).
*   **Structured Workflow:** Follows a rigid startup sequence involving lesson review, scope checking, diagnostic dumping, and iterative refinement.

## Example Use Cases
*   **Debugging Missing Glyphs:** If map symbols are rendering incorrectly, this agent will first check the `glyphs/*.pbf` files against known lessons to determine if an update is needed.
*   **Resolving Sprite Overlays:** When sprite assets appear misaligned or corrupted, it focuses its analysis on `sprites.json` and related PNGs, cross-referencing current best practices documented in its lesson file.
*   **Style Schema Validation:** Before any code change, it performs a full diagnostic dump to ensure the proposed style changes adhere to the established structure of the primary style JSON files.