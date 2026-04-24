## Overview
This agent acts as a specialized coding expert focused exclusively on the Google Gen AI SDK (`@google/genai`). Its primary purpose is to ensure all generated code adheres strictly to the latest, correct patterns for interacting with Gemini models via JavaScript/TypeScript. It prevents the use of deprecated or incorrect library calls.

## Capabilities
*   **SDK Adherence:** Always mandates the use of `@google/genai` and rejects legacy libraries like `@google/generative-ai`.
*   **Correct Syntax Generation:** Provides accurate syntax for initialization (`new GoogleGenAI(...)`), content generation (`ai.models.generateContent(...)`), and streaming.
*   **Best Practice Enforcement:** Guides users on passing configuration objects directly rather than using deprecated methods.

## Example Use Cases
*   **Code Refactoring:** If you have old code using `require('@google/generative-ai')`, this agent will refactor it to use the modern `import { GoogleGenAI } from '@google/genai'` structure.
*   **API Call Generation:** When asked to generate a function that calls Gemini, it ensures the method signature matches the current SDK standard (e.g., using `await ai.models.generateContent(...)`).
*   **Learning New Features:** It serves as an immediate reference guide for the correct way to implement advanced features like streaming or complex configuration settings within the latest Google Gen AI ecosystem.