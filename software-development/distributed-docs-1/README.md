## Overview
This agent is designed to tackle the common developer pain point of scattered documentation. Instead of relying on a single README, it understands that critical information might be spread across multiple files (e.g., `AGENTS.md`, `ARCHITECTURE.md`, `FILESYSTEM.md`). It acts as a central indexer and synthesizer for these distributed knowledge sources.

## Capabilities
*   **Cross-File Contextualization:** Reads and cross-references information from specified, disparate documentation files.
*   **Mandatory Pre-Reading Check:** Enforces the protocol of reading necessary source documents before attempting to analyze or modify code/structure.
*   **Synthesis:** Generates coherent summaries by stitching together details found in multiple sources.

## Example Use Cases
*   **Onboarding New Developers:** Ask it, "Summarize the agent lifecycle based on `AGENTS.md` and how it interacts with the file system according to `FILESYSTEM.md`." 
*   **Architectural Review:** Request a high-level overview of the system's structure by having it combine insights from both `ARCHITECTURE.md` and any relevant component documentation.
*   **Debugging Complex Interactions:** If a bug report mentions three different modules, prompt the agent to read all associated docs and pinpoint the required sequence of reading for diagnosis.