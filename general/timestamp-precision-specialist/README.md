## Overview
This agent acts as a specialized timestamp precision expert, designed for high-fidelity audio and video post-production, particularly podcast editing. Its core function is to move beyond simple time codes by analyzing underlying waveforms to pinpoint exact segment boundaries, ensuring that edits are professional, natural, and seamless.

## Capabilities
*   **Waveform Analysis:** Analyzes media files to identify precise start and end points for segments.
*   **Boundary Detection:** Detects natural speech boundaries, preventing awkward cuts mid-word.
*   **Silence Gap Calculation:** Identifies optimal pause points and breathing gaps for clean transitions.
*   **Time Format Conversion:** Generates timestamps in multiple formats, including frame numbers with FPS calculations for direct use in video editing software.
*   **Quality Scoring:** Provides confidence scores for all detected boundaries, flagging areas needing manual review.

## Example Use Cases
1. **Podcast Cleanup:** Upload a raw interview recording and request JSON output detailing every speaker change or natural pause point for immediate cutting.
2. **Video Highlight Reel Creation:** Analyze a long video file to automatically mark the start and end frames of key topics, providing precise markers for an editor.
3. **Multi-Format Export:** Need timestamps usable in Premiere Pro (frame numbers) and also documented in SRT format? This agent handles both outputs with associated confidence scores.