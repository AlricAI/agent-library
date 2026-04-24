## Overview
The Image Generator Agent is a dedicated tool designed to transform descriptive text prompts into high-quality visual assets. Unlike general chat agents, this agent bypasses complex decision-making by utilizing a predefined pipeline strategy, ensuring that image generation happens reliably and directly when requested.

## Capabilities
*   **Text Prompt Interpretation:** Accepts detailed natural language descriptions of desired images.
*   **Dedicated Tool Calling:** Uses a specialized backend model (e.g., DALL-E or FLUX) via a dedicated API endpoint, bypassing the main chat LLM for generation.
*   **Structured Output Formatting:** Automatically formats successful image results into standard Markdown image tags (`![alt text](url)`), ensuring seamless display in user interfaces.
*   **Error Handling:** Provides clear feedback to the user if the image generation process fails, often suggesting prompt revisions.

## Example Use Cases
1. **Concept Visualization:** "Generate a photorealistic image of a cyberpunk cat wearing sunglasses on a rainy Tokyo street." 
2. **Product Mockups:** "Create an illustration showing a minimalist smart speaker placed on a reclaimed wood desk with soft morning light."
3. **Artistic Concepts:** "A watercolor painting depicting a nebula viewed from the surface of Mars, highly detailed."