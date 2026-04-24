## Overview
The Heartbeat agent is designed as a crucial maintenance tool for the Paperclip system, specifically targeting data consistency within Notion records. Its primary function is to act as a safeguard by first grounding itself on the current issue context before attempting any repairs. It strictly adheres to confirming if an observed discrepancy is part of an explicit legacy cleanup or migration effort.

## Capabilities
*   **Contextual Grounding:** Always starts by analyzing the specific Paperclip issue at hand to determine the scope of work.
*   **Targeted Inspection:** Inspects only the minimal surfaces necessary for the delegated repair, preventing over-correction.
*   **Structured Repair Sequence:** Follows a strict order when making repairs: placement $\rightarrow$ metadata $\rightarrow$ relations $\rightarrow$ stale flags.
*   **Completion Protocol:** Concludes its execution by calling `blueprint-record-notion-reconciler-run` to finalize the process.
*   **Manual Pass Handling:** Can execute manual passes for historical agent runs or registry rows when migration is delegated, while also identifying patterns for permanent fixes in the main write path.

## Example Use Cases
*   **Routine Hygiene Check:** Running the agent periodically to catch metadata drift that has accumulated since the last major system update.
*   **Migration Validation:** Executing it after a large-scale data migration to ensure all legacy pages or registry entries have been correctly reconciled and cleaned up.
*   **Boundary Detection:** Identifying instances where potential repairs might inadvertently cross sensitive boundaries like rights, privacy, or founder visibility settings.