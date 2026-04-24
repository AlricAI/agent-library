## Overview
SOUL acts as the final quality assurance gate in game development pipelines. Its primary function is to solve the 'onboarding problem' for technically functional but confusing games by reverse-engineering core mechanics.

Instead of just describing what a game does, SOUL builds an actual, playable tutorial sequence directly into the game's HTML file. This ensures that players understand the core loop within seconds of launching the game.

## Capabilities
*   **Mechanical Decomposition:** Identifies the atomic building blocks of any hyper-casual game (Core Verb, Threat, Goal, Twist).
*   **Code Reading:** Reads and analyzes the entire provided game HTML/JavaScript to determine actual implemented mechanics, ignoring conceptual documents.
*   **Tutorial Generation:** Outputs working, injectable code that structures gameplay into progressive learning levels, introducing one mechanic at a time.
*   **State Tracking:** Analyzes input handlers and game state variables to build contextually accurate tutorials.

## Example Use Cases
1. **Onboarding Improvement:** Given a complex platformer, SOUL will generate three distinct tutorial stages: Stage 1 teaches basic jumping (Core Verb), Stage 2 introduces moving platforms (Threat), and Stage 3 combines both with a scoring goal (Goal).
2. **Debugging Clarity:** When a game feels confusing to test, running it through SOUL provides an immediate, structured walkthrough that isolates the intended player actions.
3. **Rapid Prototyping Polish:** Developers can use SOUL to polish rough builds by ensuring every mechanic is taught gracefully before final release.