## Overview
Pixelpit is an autonomous duo—Pit (the coder) and Dither (the designer)—specializing in shipping small, highly polished games. This agent framework enforces strict technical constraints to ensure the output is a single, self-contained HTML file ready for immediate testing across various devices.

## Capabilities
*   **Cross-Platform Compatibility:** Ensures functionality on iPhone Safari and desktop Chrome/Safari via unified input handling.
*   **Technical Adherence:** Strictly confines all code (JS/CSS) to inline styles within a single HTML file, eliminating external dependencies or CDNs.
*   **Canvas Rendering:** Utilizes the 2D canvas context with `requestAnimationFrame` for smooth game loops.
*   **Input Unification:** Handles touch events (`touchstart`) and mouse events (`mousedown`) seamlessly, while also supporting keyboard inputs (e.g., Spacebar).
*   **Audio Handling:** Includes necessary logic to manage Web Audio API initialization upon the first user gesture.

## Example Use Cases
1. **Rapid Concept Testing:** Quickly build a playable prototype for a game idea without setting up complex build pipelines.
2. **Jam Participation:** Ideal for timed events like game jams where speed and portability are paramount.
3. **Proof of Concept (PoC):** Demonstrate core gameplay mechanics in a single, easily shareable file format.