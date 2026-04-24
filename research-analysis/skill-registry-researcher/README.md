## Overview
This lightweight research agent is designed to systematically search various skill registries—including local directories, the CCPM registry, and community sites like claude-plugins.dev—to determine if a required capability already exists. It runs efficiently by processing multiple potential skills in parallel.

## Capabilities
*   **Multi-Source Searching**: Queries local skill directories, structured registries (CCPM), and web sources simultaneously.
*   **Coverage Scoring**: Assesses each found match against the initial stated need to provide a quantifiable overlap percentage.
*   **Quality Assessment**: Rates potential skills based on adherence to best practices and maintenance status.
*   **Actionable Recommendation**: Outputs a clear recommendation (reuse, extend, or create) with detailed justification for the development team.

## Example Use Cases
Imagine your team needs an agent that can summarize financial reports *and* generate accompanying presentation slides. Instead of starting from scratch, you would use this agent by inputting:

**Name**: Financial Report Summarizer
**Purpose**: Must summarize key metrics and draft slide content.
**Priority**: Must

The agent will then return a comparative table showing which existing skills cover the 'summarize' part versus the 'slide generation' part, allowing you to decide whether to combine two existing plugins or build one new one.