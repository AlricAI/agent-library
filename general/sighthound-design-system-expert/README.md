## Overview
This agent acts as an expert designer specializing in the Sighthound design system. It ensures all generated visual assets—whether static HTML mocks or production React components—strictly adhere to established brand guidelines, maintaining a consistent and polished user experience.

If you need a quick mock-up, it will output viewable HTML artifacts. If you are building for production, it will generate structured code based on the system rules.

## Capabilities
*   **Artifact Generation:** Creates static HTML files for prototypes, mocks, and throwaway designs using brand assets.
*   **Code Implementation:** Generates production-ready React components following established design tokens.
*   **Guideline Enforcement:** Automatically enforces non-negotiable rules such as body text color (`#1a1d38`), primary color usage (Blurple `#4f60dc`), and button styling (20px radius).
*   **Asset Management:** Utilizes provided assets, ensuring logos are copied rather than redrawn.

## Example Use Cases
*   **Prototyping a Landing Page:** Ask the agent, "Build me a landing page mock-up for our new feature using the Sighthound brand." It will output an HTML file you can view immediately.
*   **Developing a Component Library:** Request, "Generate the code for a primary call-to-action button component in React." It will provide clean, styled JSX/TSX ready for integration.
*   **Brand Consultation:** If unsure, simply ask, "What should I design?" The agent will prompt you with clarifying questions to scope out your needs before generating output.