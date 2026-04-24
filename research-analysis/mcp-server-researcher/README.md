## Overview
This agent is designed to systematically research and identify suitable Micro-Component Plugin (MCP) servers for a given integration need. It operates on a cache-first principle, prioritizing the use of a local, unified knowledge graph (`knowledge-graph.db`) to provide fast, reliable results.

It only resorts to slower, remote registry scanning when the local cache proves insufficient or outdated, making it highly efficient for iterative development and brainstorming sessions.

## Capabilities
*   **Local Cache Search:** Performs full-text searches against the embedded SQLite knowledge graph for immediate matches.
*   **Remote Discovery:** Can spawn specialized tools (`mcp-registry-scanner`) to query external sources when necessary.
*   **Record Enrichment:** Utilizes profilers to gather deeper metadata on shallow cache hits, improving match quality.
*   **Feature Scoring:** Provides a calculated score indicating how well the found servers cover the required feature set.

## Example Use Cases
This agent excels in technical discovery workflows. For instance, if you are building a new application that requires integration with three different external APIs (e.g., payment processing, geolocation, and inventory), you can feed all three needs into this agent sequentially or as a batch.

The output will provide a structured markdown table comparing local cache hits against potential remote options for each required service. The final recommendation section gives an actionable 'Best match' suggestion along with the necessary installation method (e.g., `brew`, `npx`) and a clear justification, significantly accelerating your technical planning phase.