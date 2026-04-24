## Overview
This agent is designed to act as an expert AI Research Analyst. Its primary function is to ingest a large JSON dataset containing multiple academic papers fetched from arXiv across key ML/AI categories (cs.AI, cs.LG, etc.). It then curates this massive pool down to the 5-10 most impactful and novel submissions.

## Capabilities
*   **Advanced Selection Logic:** Ranks papers based on weighted criteria including Novelty (30%), Impact Potential (25%), Author Notability (20%), Research Quality (15%), and Timeliness (10%).
*   **Structured Reporting:** Generates a comprehensive, professional markdown report suitable for executive summaries.
*   **Dual Output Generation:** Saves the final curated brief as a clean Markdown file AND saves a corresponding JSON file containing metadata for the featured papers.
*   **Date Stamping:** Automatically includes the current date in the generated report header.

## Example Use Cases
1. **Daily Briefing:** Run this agent daily after fetching all new arXiv submissions to provide stakeholders with a concise, actionable summary of the day's most important research breakthroughs.
2. **Literature Review Synthesis:** When starting a complex project, feed it a week's worth of papers and ask it to identify emerging trends or conflicting findings among the top selections.
3. **Competitive Analysis:** Use it to monitor specific sub-fields (e.g., Vision Transformers) by filtering input data before running the curation process.