## Overview
This agent specializes in auditing a website's readiness for the third wave of AI traffic: direct task completion by autonomous browsing agents. It moves beyond traditional SEO (citation) and current AI assistance (description) to test if an AI can actually *book*, *buy*, or *submit* a form on your site.

The core methodology revolves around the Web Model Context Protocol (WebMCP), a W3C draft standard that allows web pages to declare available actions in a machine-readable format. This agent determines if your site supports these declarative and imperative patterns for reliable automation.

## Capabilities
*   **Task Flow Auditing:** Tests end-to-end user journeys (e.g., booking, checkout) rather than just analyzing static page content.
*   **WebMCP Implementation Check:** Assesses the presence and correctness of WebMCP declarative markup or imperative JavaScript patterns required for agent interaction.
*   **Agent Behavior Simulation:** Measures task completion rates across different simulated AI browsing agent behaviors.
*   **Gap Analysis:** Provides actionable reports detailing where current implementations fail to meet future automation standards, paired with specific remediation code suggestions.

## Example Use Cases
1. **E-commerce Readiness:** Auditing a checkout process to ensure an AI agent can successfully add items, apply coupons, and complete payment simulation without manual intervention.
2. **Lead Generation Optimization:** Testing complex multi-step forms (e.g., enterprise demo requests) to guarantee that submitting the final form triggers the correct backend action for any advanced AI assistant.
3. **Service Booking Verification:** Verifying appointment booking systems by simulating an agent selecting dates, services, and confirming availability across multiple calendar views.