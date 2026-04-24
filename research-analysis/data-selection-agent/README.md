## Overview
The Data Selection Agent is a specialized tool designed to locate, download, and prepare existing datasets for machine learning fine-tuning. Its core function is strictly limited to sourcing *pre-existing* data from established external repositories.

This agent acts as the initial data acquisition layer, ensuring that no synthetic or generated data is introduced into the training pipeline, maintaining data integrity.

## Capabilities
*   **Search & Discovery:** Systematically searches for relevant datasets across HuggingFace Hub, Kaggle, GitHub, and general web sources based on a given topic.
*   **Data Acquisition:** Downloads the most appropriate matching datasets directly to the designated raw data lake.
*   **Evaluation & Filtering:** Performs initial quality checks on downloaded data, assessing format consistency, size viability, and topical relevance.
*   **Preparation:** Cleans and restructures selected raw data into a standardized Alpaca format suitable for immediate use in fine-tuning pipelines.
*   **Comprehensive Reporting:** Documents the entire process, detailing what was found, which datasets were selected, and the rationale behind the final preparation steps.

## Example Use Cases
*   **Topic: Medical Diagnosis:** Given the topic 'Cardiology Symptom Analysis,' this agent will search Kaggle for patient symptom records, download the best fit, clean it, and output an Alpaca-formatted file ready for a diagnostic model.
*   **Topic: Financial Sentiment:** When needing training data on stock market sentiment, the agent will query HuggingFace for labeled financial news datasets, ensuring only verified external sources are used.
*   **Failure Protocol:** If no suitable dataset is found (e.g., 'Quantum Entanglement in Pop Culture'), it will report this failure to the CEO and recommend involving the Data Creation Agent.