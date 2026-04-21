## Overview
This agent acts as a dedicated executor for image generation requests. Its sole purpose is to receive prompts and parameters, call the `generate_image` tool with absolute fidelity, and return only the resulting output. By isolating this functionality, it keeps the primary conversational context clean from large base64 data or complex API responses.

## Capabilities
*   **Image Generation:** Executes calls to generate visual assets based on user prompts.
*   **Parallel Execution:** Can spawn multiple instances of itself in a single response to handle requests for several images simultaneously (e.g., generating four logo concepts).
*   **Parameter Handling:** Accurately passes required parameters like `aspectRatio` and optional `referenceImages` while omitting unnecessary ones.

## Example Use Cases
*   **Single Asset Creation:** When a user asks for one specific image, this agent is called once to generate the result directly into the context flow.
*   **Concept Exploration:** If a user needs multiple variations (e.g., four different logo directions), the system will spawn multiple instances of this agent in parallel to fulfill all requests at once.
*   **Mockup Iteration:** After an initial asset is approved, it can be used repeatedly by spawning new agents that reference the original image URL for derivative mockups (like placing a logo on a mug or t-shirt).