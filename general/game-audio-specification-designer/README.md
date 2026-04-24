## Overview
This agent specializes in transforming abstract sonic direction into concrete, technical specifications for game audio implementation. It acts as the crucial bridge between a sound director's creative vision and the game engine's technical requirements.

Its primary function is to document *how* sounds should behave—when they play, how loud they are relative to other sounds, and what their sonic characteristics must be—ensuring every audio element serves a clear gameplay purpose.

## Capabilities
*   **SFX Specification Sheets:** Generates detailed sheets for each sound, covering emotional intent, required frequency ranges, optimal duration, and layering notes.
*   **Audio Event Documentation:** Creates comprehensive catalogs detailing trigger conditions (e.g., proximity, action), falloff rules, and concurrency limits for every audible event.
*   **Mixing Parameter Definition:** Specifies precise mixing guidelines, including volume targets per bus, required distance attenuation curves, and necessary ducking chains to maintain mix clarity.
*   **Environmental Audio Specification:** Defines ambience layers, reverb zone transitions, and occlusion rules for immersive spatial audio.
*   **Audio Feedback Mapping:** Maps specific player actions (e.g., healing, taking damage) directly to required sonic feedback signatures.

## Example Use Cases
1. **Implementing a New Weapon:** Given the concept of a 'Plasma Rifle,' this agent will output an SFX spec sheet detailing its attack sound's frequency profile, duration, and how it should interact with existing weapon sounds in the mix.
2. **Designing a Combat Zone:** You can provide level context (e.g., 'Cramped industrial area'), and the agent will define necessary ambience layers, reverb presets for that zone, and rules for sound occlusion when players move behind machinery.
3. **UI Polish Pass:** For a new inventory pickup mechanic, it will generate an audio event list specifying the trigger condition (pickup successful), the required sonic feedback (a distinct 'chime'), and its priority level relative to combat sounds.