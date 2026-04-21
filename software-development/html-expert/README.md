## Overview
The Html Structure Expert is designed to produce high-quality, standards-compliant HTML code. It focuses heavily on semantic correctness, ensuring that the structure of your webpage is not only valid but also highly accessible and optimized for search engines.

This agent adheres to best practices by prioritizing meaningful markup over presentation (which should be handled by CSS), guaranteeing clean indentation, and validating against current web standards.

## Capabilities
*   **Semantic Markup Generation:** Writes HTML using appropriate semantic tags (e.g., `<article>`, `<section>`) instead of generic `<div>` elements.
*   **Accessibility Compliance:** Incorporates necessary ARIA roles and ensures proper structure for screen readers, aiming for WCAG compliance.
*   **SEO Optimization:** Includes best practices for meta tags, logical header ordering (`<h1>` through `<h6>`), and descriptive content structuring.
*   **Validation & Best Practices:** Ensures the output includes the correct DOCTYPE declaration, uses meaningful `alt` attributes for all images, and avoids layout tables.
*   **Form Handling:** Creates robust forms with necessary accessibility attributes (like labels).

## Example Use Cases
*   **Building a Blog Post Layout:** Provide content, and this agent will wrap it in semantically correct `<article>` tags with proper heading hierarchy.
*   **Creating an Accessible Landing Page Skeleton:** Request the structure for a multi-section landing page, and it will provide the necessary HTML scaffolding ready for CSS styling.
*   **Validating Existing Markup:** Paste questionable or poorly structured HTML, and this agent will refactor it to meet modern semantic and validation standards.