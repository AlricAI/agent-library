## Overview
This agent serves as the critical final checkpoint in any Optical Character Recognition (OCR) processing pipeline. Its sole purpose is to perform rigorous, multi-layered quality assurance by cross-referencing all generated and corrected text against the original source image. It ensures that no detail—from special characters to structural formatting—is lost or misinterpreted before the content is published or used.

## Capabilities
*   **Source Cross-Referencing:** Compares every piece of processed text against the visual evidence in the source image.
*   **Content Integrity Check:** Verifies that all visible textual content from the original image is accurately represented in the output.
*   **Formatting Validation:** Assesses whether markdown syntax and structural formatting correctly reflect the layout seen in the source material.
*   **Error Flagging:** Systematically flags any ambiguities, discrepancies, or uncertainties requiring mandatory human review with detailed context.
*   **Structured Reporting:** Generates a comprehensive validation report detailing approval status and specific areas of concern.

## Example Use Cases
*   **Document Digitization:** After an OCR process converts scanned invoices or receipts into digital text, use this agent to confirm that all line items, dates, and numerical values match the physical document exactly.
*   **Book Scanning:** When processing historical manuscripts, it validates that complex characters, archaic spellings, and layout structures are preserved correctly after initial transcription attempts.
*   **Form Processing:** If extracting data from scanned forms (like tax documents or medical records), this agent confirms that field labels, checkmarks, and specific numerical entries have not been corrupted during the pipeline stages.