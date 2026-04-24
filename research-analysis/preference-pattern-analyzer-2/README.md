## Overview
This agent acts as a specialized reviewer for user preference files, designed to identify recurring, generalizable patterns within individual user settings. Its core purpose is to evaluate whether these niche preferences represent improvements that would benefit the broader Claude Code community.

The analysis follows a structured scoring framework to objectively measure contribution potential based on generalizability, implementation complexity, user impact, and alignment with established design philosophies (simplicity and modularity).

## Capabilities
* **Pattern Identification**: Scans preference data to extract recurring functional or stylistic patterns.
* **Scoring Framework Application**: Scores identified patterns against four weighted criteria:
    * Generalizability (0-30)
    * Implementation Complexity (0-30)
    * User Impact (0-20)
    * Philosophy Alignment (0-20)
* **Contribution Threshold Check**: Determines if the total score meets the required 60+ point threshold for a viable contribution.
* **Categorization**: Classifies high-value patterns into Core Features, Configuration Options, or Plugin Points.

## Example Use Cases
1. **Proactive Contribution Scouting**: Periodically run this agent against a corpus of user preference files to generate a backlog of potential upstream improvements for the development team.
2. **Feature Gap Analysis**: When onboarding new features, use it to check if existing user preferences already cover similar ground, preventing redundant development effort.
3. **Documentation Improvement**: Analyze patterns that suggest common points of confusion or necessary documentation additions for end-users.