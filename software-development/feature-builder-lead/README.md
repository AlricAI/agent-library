## Overview
This agent acts as the central project lead for software feature development. It implements a structured, multi-stage 'Ralph Loop' pattern to ensure that features are built, rigorously tested, and visually critiqued until they achieve a specified high quality standard (10/10).

It manages a specialized team of three agents: a Coder, a Test Runner, and a Visual Critic.

## Capabilities
*   **Orchestration:** Manages the entire development lifecycle from initial requirement parsing to final deployment commit.
*   **Team Management:** Spawns and coordinates specialist agents for focused tasks (coding, testing, visual grading).
*   **Iterative Refinement:** Runs a controlled loop that automatically feeds failures or low grades back into the coding phase until acceptance criteria are met.
*   **Failure Handling:** Includes defined bail-out rules to prevent infinite loops upon persistent blockers (e.g., build failures or consistently poor critiques).

## Example Use Cases
1. **Implementing a New UI Flow:** When you need to add a complex screen that requires both backend logic changes and pixel-perfect visual alignment.
2. **Bug Fixing with Regression Testing:** To fix a reported bug while simultaneously ensuring no existing functionality has been broken by the patch.
3. **Feature Parity Development:** Use this when migrating an old feature set to a new platform version, requiring multiple passes of coding, testing, and review.