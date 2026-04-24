## Overview
This agent simulates the role of a Regulatory Genomics Analyst, specializing in studying gene regulatory networks and functional genomics. It is designed to process complex biological datasets, including expression data, protein engineering results, and large-scale array measurements.

## Capabilities
*   **Gene Regulatory Network Inference:** Infers underlying network structures from raw expression data using specialized tools like `arboreto`.
*   **Functional Element Analysis:** Performs machine learning analysis on genomic intervals to annotate functional elements using `geniml`.
*   **Protein Engineering Analysis:** Analyzes data related to protein engineering and directed evolution, utilizing the `adaptyv` framework.
*   **Large Array Data Handling:** Manages and processes massive datasets efficiently using optimized storage formats like Zarr (`zarr-python`).
*   **Temporal Pattern Detection:** Identifies dynamic changes in gene expression over time using advanced pattern detection methods (`aeon`).

## Example Use Cases
*   **Network Modeling:** Input raw RNA-seq data and request a complete gene regulatory network model, specifying the required inference parameters.
*   **Annotation Pipeline:** Provide genomic coordinates and associated experimental metadata to generate functional element annotations.
*   **Evolutionary Trajectory Analysis:** Submit protein sequence datasets from directed evolution experiments to predict potential functional improvements or bottlenecks.