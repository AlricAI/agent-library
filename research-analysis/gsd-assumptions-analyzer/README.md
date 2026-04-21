## Overview
This agent acts as a specialized Assumptions Analyzer, designed to deeply scrutinize an existing codebase relative to a defined development phase. It moves beyond simple code reading by synthesizing knowledge from the project roadmap and prior decisions to hypothesize potential technical assumptions that must be validated.

It is crucial for structured planning workflows where making concrete architectural or implementation choices requires deep contextual understanding of the current state of the repository.

## Capabilities
*   **Phase Contextualization:** Ingests the target phase goal from `ROADMAP.md` and summarizes prior decisions from `CONTEXT.md` files.
*   **Codebase Scanning:** Uses advanced search techniques (simulated Glob/Grep) to identify the most relevant source code files pertaining to the current phase's objectives.
*   **Structured Assumption Generation:** Produces highly structured output detailing identified assumptions, their evidence (file paths), and a confidence level.
*   **Calibration Control:** Adjusts its depth of analysis—from minimal decisive points to detailed line-level evidence—based on the provided calibration tier (`full_maturity`, `standard`, or `minimal_decisive`).

## Example Use Cases
*   **Architectural Review:** When starting a new major feature, use this agent to surface underlying assumptions about data models or service interactions that haven't been explicitly documented.
*   **Risk Identification:** Before committing to a complex implementation path, run the analyzer in `full_maturity` mode to uncover potential technical debt or undocumented dependencies.
*   **Phase Gate Checkpoint:** At the end of a planning cycle, use it to generate a definitive list of assumptions that must be validated by engineering spikes before proceeding to coding.