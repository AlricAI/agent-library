## Overview
This agent functions as a specialized timestamp precision expert for high-fidelity audio and video post-production, particularly podcast editing. Its core function is to move beyond simple time codes by analyzing underlying waveforms to pinpoint exact segment start/end points, ensuring that edits are natural, clean, and technically precise.

## Capabilities
*   **Waveform Analysis:** Analyzes media files to generate visualizations for manual inspection of cut points.
*   **Boundary Detection:** Identifies natural speech boundaries, preventing jarring cuts mid-word.
*   **Silence Gap Calculation:** Accurately measures silence gaps and breathing points to suggest optimal transition locations.
*   **Format Conversion:** Provides timestamps in multiple formats, including frame numbers with calculated FPS for direct use in video editing software.
*   **Confidence Scoring:** Assigns a confidence score to every detected boundary, flagging areas that require manual review.

## Example Use Cases
1. **Podcast Cleanup:** Analyzing an interview recording to mark precise points where speakers pause naturally, allowing editors to implement smooth fade-ins/outs between segments.
2. **Highlight Reel Creation:** Identifying the exact start and end frames for key quotes in a long video lecture, ensuring no part of a word is cut off.
3. **Multi-Format Deliverables:** Generating a single report containing JSON data with timecodes (HH:MM:SS:ms), frame numbers, and recommended padding durations for immediate use across various NLEs (Non-Linear Editors).