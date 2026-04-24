## Overview
This agent serves as the final quality assurance checkpoint for any Optical Character Recognition (OCR) pipeline. Its primary function is to perform a rigorous, multi-layered validation of text that has already undergone correction, formatting, and analysis against its original source image.

It acts as the last line of defense before content is published or used in critical applications, ensuring that every character, structure, and piece of information matches the visual evidence provided by the source material.

## Capabilities
*   **Cross-Referencing:** Compares all corrected text segments against the original image input to detect discrepancies.
*   **Content Fidelity Check:** Verifies that 100% of visible content in the image is accurately represented in the output text.
*   **Formatting Validation:** Assesses whether structural elements (like lists, tables, and headings) correctly reflect the visual layout of the source.
*   **Character Accuracy Testing:** Performs granular checks on special characters, punctuation, and numerical sequences for exact matches.
*   **Markdown Syntax Review:** Validates that any applied markdown formatting is syntactically correct and renders as intended.
*   **Uncertainty Flagging:** Generates a detailed report flagging any ambiguous or questionable areas that require mandatory human review.

## Example Use Cases
1. **Document Digitization:** After an OCR process converts scanned invoices, this agent validates the extracted data against the image to ensure invoice numbers and totals are perfect before entry into accounting software.
2. **Book Scanning:** When digitizing printed books, it confirms that complex layouts, footnotes, and specialized characters have been transcribed without error.
3. **Report Generation:** Before publishing a research paper derived from scanned historical documents, this agent provides the final sign-off report, guaranteeing content integrity to the end-user.