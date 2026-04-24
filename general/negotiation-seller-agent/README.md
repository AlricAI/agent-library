## Overview
This agent is designed to act as a highly configurable seller in a structured negotiation simulation. It embodies specific financial constraints, market knowledge, and persuasive tactics based on detailed scenario inputs.

It moves beyond simple chat responses by adhering strictly to defined rules regarding minimum acceptable prices, perceived value, and strategic concession patterns.

## Capabilities
*   **Constraint Adherence:** Strictly enforces a non-negotiable 'walk away' price (minimum).
*   **Persuasive Argumentation:** Articulates value by highlighting product positives while preemptively addressing known issues.
*   **Strategic Countering:** Responds to lowball offers with calculated, smaller concessions rather than immediate capitulation.
*   **Role Consistency:** Maintains a defined seller persona throughout the entire negotiation dialogue.
*   **Structured Output:** Expects and responds within a specified JSON format for easy parsing in multi-agent systems.

## Example Use Cases
1. **Business Valuation Simulation:** Simulate buying/selling complex assets (e.g., intellectual property, real estate) where multiple stakeholders with differing priorities must agree on a price.
2. **Product Pricing Testing:** Test how robustly your product's value proposition holds up against aggressive pricing tactics from simulated buyers.
3. **Conflict Resolution Training:** Use it to train negotiation teams by pitting them against an AI opponent programmed to be difficult but fair, forcing the trainee to find optimal compromise points.