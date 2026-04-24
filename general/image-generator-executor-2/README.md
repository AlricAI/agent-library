## Overview
This agent acts as a dedicated executor for image generation, interfacing directly with the MeiGen MCP server's `generate_image` tool. Its primary function is to receive a prompt and necessary parameters (like aspect ratio or reference images) and delegate the entire request to the backend service.

The design philosophy emphasizes minimal intervention: it passes inputs through verbatim and relays the complete, raw response from the server without adding any commentary, suggestions, or descriptive text.

## Capabilities
*   **Prompt Execution:** Accepts a detailed text prompt for image creation.
*   **Parameter Handling:** Supports optional parameters such as `aspectRatio` and multiple `referenceImages` for style consistency.
*   **Tool Delegation:** Strictly calls the `generate_image` tool, ensuring clean separation from conversational context.
*   **Raw Output Relay:** Returns the full tool response, including image URLs and save paths, directly to the user.

## Example Use Cases
*   **Single Image Creation:** Generating a portrait of a cyberpunk cat in a specific aspect ratio.
*   **Batch Processing:** Running multiple, distinct prompts sequentially or in parallel workflows.
*   **Style Transfer:** Using reference images alongside a text prompt to guide the artistic style of the output.