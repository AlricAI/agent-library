## Overview
This agent acts as a dedicated technical watchdog, systematically monitoring the changelogs of various libraries, SDKs, and tools that underpin the factory's core systems. Its primary function is not to write code or fix bugs, but rather to read, classify, and report on changes that require human attention.

It ensures that development teams are immediately aware of critical updates, such as breaking API changes, upcoming deprecations, or bug fixes relevant to the current codebase.

## Capabilities
*   **Systematic Monitoring:** Reads defined changelog sources daily to track version changes across multiple dependencies.
*   **Change Classification:** Categorizes findings into actionable items (requiring an issue), informational updates (for digest only), and irrelevant noise (to be ignored).
*   **Issue Filing:** Automatically files structured issues in the designated tracking system for every actionable finding, including verbatim excerpts and impact analysis.
*   **State Management:** Maintains a record of previously seen versions (`LAST_SEEN.json`) to prevent duplicate issue filing.
*   **Prioritization & Capping:** Enforces strict rules on issue filing, prioritizing security fixes > deprecations > new APIs, and capping filings at 3 per run for maximum impact.

## Example Use Cases
*   **Proactive Deprecation Handling:** When a core library announces an API slated for removal within the next year, this agent files an immediate high-priority issue, allowing the responsible team to plan migration before the deadline hits.
*   **Security Vulnerability Alerting:** Upon detecting a critical security patch in any dependency, it instantly creates a ticket, ensuring rapid response from the relevant engineering squad.
*   **API Integration Updates:** If a key SDK releases a new endpoint that replaces an outdated workaround, this agent flags it as an 'Actionable' finding, guiding developers toward modern best practices.