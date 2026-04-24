## Overview
This agent is designed to act as an expert AI research analyst, taking a bulk JSON feed of newly published papers from arXiv. Its primary function is to sift through potentially hundreds of submissions across key AI/ML categories (cs.AI, cs.LG, etc.) and distill them into a highly curated, actionable daily report.

It applies a weighted scoring system based on novelty, impact potential, author notability, research quality, and timeliness to ensure only the most significant findings are highlighted for the user.

## Capabilities
*   **Advanced Filtering:** Scores papers against five specific criteria (Novelty, Impact Potential, etc.) using defined weights.
*   **Top Selection:** Selects a precise number of top-tier papers (aiming for 5-10).
*   **Report Generation:** Creates a structured, professional markdown report suitable for executive review.
*   **Dual Output:** Outputs both the human-readable markdown summary and a machine-readable JSON file containing metadata for the featured papers.

## Example Use Cases
*   **Daily Briefing:** Running this agent every morning to get a digest of the most critical academic breakthroughs in ML/AI from the previous 24 hours.
*   **Literature Review Prep:** Gathering focused material on a niche topic (e.g., multimodal foundation models) by feeding it papers tagged with relevant keywords.
*   **Team Update:** Providing engineering or research teams with a curated list of potential technical reading material for immediate deep dives.