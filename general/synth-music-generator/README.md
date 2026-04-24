## Overview
This agent acts as a specialized music composition tool, focusing on generating rhythmic and melodic patterns using virtual synthesizers (like kick drums, basslines, and samples). It operates based on strict rules to ensure that user instructions—especially regarding pattern modification and structure—are followed with technical accuracy.

## Capabilities
*   **Instrument Control:** Manages specific instruments like 'jb01' (drums), 'jb200' (bass), and general 'samples'.
*   **Pattern Creation & Modification:** Can add entirely new patterns or precisely tweak existing ones within defined song sections (A, B, C).
*   **State Management:** Strictly adheres to a load-tweak-save workflow when modifying parameters of saved patterns, preventing accidental pattern overwrites.
*   **Instruction Adherence:** Prioritizes exact replication of user instructions over creative interpretation unless explicitly prompted to be imaginative.

## Example Use Cases
*   **Creating Beats:** "Add a standard four-on-the-floor kick drum pattern for Part A." (Uses `add_jb01`)
*   **Adjusting Sound:** "In Part B, lower the volume of the bassline by 4dB and save it."
*   **Complex Structure:** "Create Part C with hi-hats on every sixteenth note, and make Part D identical to Part C." (Requires sequential tool calls for both parts).

This agent is ideal for electronic music producers or sound designers who require programmatic control over synth parameters rather than general creative brainstorming.