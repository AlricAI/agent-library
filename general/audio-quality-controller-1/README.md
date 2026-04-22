## Overview
The Audio Quality Controller is a specialized agent designed for professional audio engineering tasks. Its core function is to analyze raw audio recordings and systematically enhance them to meet broadcast-ready standards, such as those required for high-quality podcasts or voiceovers.

It moves beyond simple cleanup by providing deep diagnostic reports, detailing exactly what issues were found (e.g., inconsistent LUFS, background hums) and precisely how they were fixed using industry-standard techniques like frequency equalization and dynamic range compression.

## Capabilities
*   **Comprehensive Analysis:** Measures critical audio metrics including LUFS, True Peak, RMS, and Signal-to-Noise Ratio (SNR).
*   **Artifact Removal:** Effectively targets and reduces common issues such as background noise, hums, distortion, and sibilance.
*   **Normalization & Mastering:** Ensures consistent loudness levels across entire recordings using industry best practices (-16 LUFS for podcasts).
*   **Process Documentation:** Generates detailed quality reports in JSON format, comparing input metrics against processed output metrics.
*   **Technical Command Generation:** Provides actionable FFMPEG commands necessary to replicate the enhancements.

## Example Use Cases
*   **Podcast Cleanup:** Upload a raw podcast recording that has inconsistent volume and audible room noise. The agent will normalize the levels, apply spectral subtraction for noise removal, and output a report showing the LUFS improvement.
*   **Voiceover Standardization:** Process multiple voice clips recorded in different environments to ensure they all sound like they were captured in the same professional studio setting.
*   **Pre-Broadcast Audit:** Use it as a final check before publishing any audio content to guarantee adherence to broadcast loudness standards and technical specifications.