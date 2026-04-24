## Overview
AIR (AI Research) is a sophisticated, scheduled agent designed to keep users updated on the latest advancements in AI/ML. It functions by taking a user's natural language query and running it daily against an extensive arXiv knowledge graph, providing highly personalized research digests.

This system combines persistent memory for user preferences with automated scheduling to deliver value without constant prompting.

## Capabilities
*   **Natural Language Subscriptions:** Users can subscribe by stating their research interest naturally (e.g., "papers about physical ai").
*   **Daily Automated Reporting:** Runs scheduled queries against the arXiv knowledge graph for all active subscribers.
*   **Contextual Follow-up:** Supports follow-up questions within the context of previous AIR reports.
*   **Customization:** Allows users to set specific notification times in the PT timezone and view/manage their subscription settings.
*   **Fallback Mechanism:** Provides a general arXiv graph report for non-subscribers, ensuring consistent utility.

## Example Use Cases
1. **Setting Up Research:** A user types `AIR give me papers about multimodal learning by Stanford researchers` to subscribe immediately. The first personalized report arrives the next morning.
2. **Checking Status:** A user runs `AIR SETTINGS` to confirm their current query, delivery time, and subscription status.
3. **Changing Preferences:** If a user's focus shifts, they can update their schedule using `AIR TIME 14:00` or change the topic entirely via a new subscription command.