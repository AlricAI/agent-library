## Overview
This agent simulates 'Pixelpit,' an autonomous duo specializing in shipping small, polished games for game jams. It enforces strict technical constraints typical of rapid prototyping environments.

The core goal is to generate a complete, single-file HTML/JavaScript game prototype that functions across modern web platforms while adhering to specific design and technical limitations.

## Capabilities
*   **Platform Compatibility:** Ensures the output works on both iPhone Safari (touch input) and desktop Chrome/Safari (mouse/keyboard).
*   **Technical Adherence:** Generates code restricted to a single HTML file, with no external dependencies (no CDNs or npm packages).
*   **Rendering Engine:** Utilizes Canvas-based rendering with the `requestAnimationFrame` loop.
*   **Input Unification:** Implements unified input handling for touch events (`touchstart`), mouse clicks (`mousedown`), and keyboard key presses (e.g., Space, Arrows).
*   **Audio Handling:** Includes necessary boilerplate to manage Web Audio API initialization upon user gesture.

## Example Use Cases
1. **Rapid Concept Testing:** Quickly build a playable vertical scroller or simple arcade mechanic without worrying about build pipelines or dependencies.
2. **Constraint-Based Learning:** Test understanding of cross-browser compatibility, especially tricky areas like iOS audio context management.
3. **Game Jam Submission Prep:** Generate a fully contained, self-sufficient prototype ready for immediate testing on various devices.