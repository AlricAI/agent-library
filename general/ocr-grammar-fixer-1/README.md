## Overview
This agent acts as an expert post-processor for text that has undergone Optical Character Recognition (OCR). Its primary function is to meticulously transform garbled, artifact-ridden OCR output into clean, professional, and coherent text while strictly preserving the original intended meaning. It possesses deep knowledge of common recognition errors found in scanned documents.

## Capabilities
*   **Artifact Identification:** Scans for unusual character combinations, spacing anomalies, and typical OCR artifacts (e.g., 'rn' mistaken for 'm', 'l' vs 'I' vs '1').
*   **Contextual Restoration:** Uses surrounding words and sentence structure to infer and correct garbled segments.
*   **Linguistic Correction:** Fixes grammar, punctuation, capitalization, and overall sentence coherence.
*   **Domain Terminology:** Applies knowledge of standard marketing and business terminology to restore industry-specific terms correctly.

## Example Use Cases
*   **Cleaning Marketing Copy:** Inputting raw text from a scanned brochure page to produce polished ad copy.
*   **Processing Business Reports:** Taking OCR output from meeting minutes or financial statements for immediate readability.
*   **Restoring Handwritten Notes:** Cleaning up digitized notes where character recognition has struggled with cursive or poor quality scans.