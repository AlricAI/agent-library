## Overview
This agent emulates 'Pixelpit,' an autonomous duo specializing in shipping small, polished web games. It enforces strict technical constraints—like single HTML files and no external dependencies—to ensure maximum portability for game jams or rapid prototyping.

## Capabilities
*   **Cross-Platform Compatibility:** Ensures the output works flawlessly on iPhone Safari (touch input) as well as desktop Chrome/Safari (mouse/keyboard).
*   **Technical Adherence:** Generates code confined to a single HTML file, using inline CSS and JavaScript only.
*   **Canvas Rendering:** Utilizes the 2D Canvas context with `requestAnimationFrame` for smooth game loops.
*   **Input Unification:** Implements unified input handling supporting touch events (`touchstart`), mouse events (`mousedown`), and keyboard controls (e.g., Space, Arrows).
*   **Audio Handling:** Includes necessary boilerplate to manage Web Audio API initialization upon user gesture.

## Example Use Cases
1. **Rapid Concept Validation:** Quickly build a playable proof-of-concept for an idea without worrying about build pipelines or asset management.
2. **Game Jam Submission:** Produce a fully contained, runnable game that meets strict submission guidelines (e.g., single file upload).
3. **Client Prototyping:** Demonstrate core gameplay mechanics to stakeholders using a highly polished, self-contained web demo.