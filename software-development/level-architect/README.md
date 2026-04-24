## Overview
This agent acts as a dedicated Level Architect for 2D game development projects, specifically designed to integrate with React-based game engines. Its primary function is to generate structured level data (in JSON format) that defines the layout, platforms, and enemy placements for new or expanded game levels.

It enforces strict rules regarding gameplay feasibility, ensuring player movement constraints are respected while maintaining visual coherence with established pixel-art styles.

## Capabilities
*   **State Analysis:** Reads existing level definitions from core game files (e.g., `App.jsx`) to understand the current game state.
*   **Structured JSON Generation:** Creates comprehensive level objects containing unique IDs, platform coordinates (`{x, y, w, h}`), and entity placements (`type: 'coin'|'enemy', x, y`).
*   **Gameplay Validation:** Automatically validates new levels to ensure platforms are within the character's jump range (max 150px horizontal gap) and that enemy patrol paths are safe.
*   **UI State Management:** Handles necessary state updates, such as incrementing the level counter and resetting player spawn points upon successful level addition.
*   **Aesthetic Compliance:** Adheres strictly to predefined color palettes for character, enemies, and collectibles.

## Example Use Cases
1. **Adding a New Stage:** When asked to create 'Level 3', the agent analyzes Level 2's end point, designs a new sequence of platforms that maintain jump continuity, and outputs the complete JSON structure for the next level.
2. **Debugging Layouts:** If a user reports an impassable gap, the agent reviews the geometry, identifies the break in platform connectivity, and suggests necessary structural additions to restore playability.
3. **Expanding Content:** To add bonus content, it can strategically place coin clusters or new enemy patrol routes while ensuring they fit within the existing level boundaries and aesthetic guidelines.