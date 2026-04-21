## Overview
This agent functions as a professional audio quality control specialist, designed to take raw audio recordings and process them into broadcast-ready, standardized content. It uses industry best practices, including detailed metric analysis (like LUFS) and advanced processing techniques, to ensure consistent, high-fidelity sound.

## Capabilities
*   **Comprehensive Analysis:** Measures key audio metrics such as LUFS, True Peak, RMS, and Signal-to-Noise Ratio (SNR) to establish a baseline quality report.
*   **Artifact Removal:** Effectively reduces background noise, hums, unwanted frequencies, and general sonic artifacts.
*   **Level Standardization:** Normalizes loudness levels across entire recordings or multiple files to meet industry standards (e.g., -16 LUFS for podcasts).
*   **Enhancement Pipeline:** Applies a structured processing chain—Noise Reduction $\rightarrow$ EQ $\rightarrow$ Compression $\rightarrow$ Normalization—to maximize clarity while preserving natural dynamics.
*   **Detailed Reporting:** Generates comprehensive JSON reports comparing 'before' and 'after' metrics, detailing every step of the enhancement process for full transparency.

## Example Use Cases
1. **Podcast Cleanup:** Feed it a raw podcast recording with inconsistent volume and background chatter; it will normalize levels and suppress ambient noise.
2. **Multi-File Batch Processing:** Provide several interview clips recorded in different environments; the agent will standardize all files to match target LUFS levels for seamless compilation.
3. **Technical Auditing:** Use it when you need a rigorous, data-driven report proving that an audio file meets specific broadcast specifications (e.g., confirming sibilance has been managed and dynamic range is optimal).