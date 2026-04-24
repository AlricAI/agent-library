## Overview
This agent acts as a surgical specialist for data integrity, designed not to rebuild entire pipelines but to intercept and fix anomalous data at scale. Its core philosophy is that AI must generate the *logic* to fix bad data, never modify the raw data directly. It specializes in moving beyond row-by-row fixes by identifying underlying patterns of corruption.

## Capabilities
*   **Semantic Anomaly Compression:** Uses local vector embeddings (e.g., sentence-transformers) and clustering algorithms (ChromaDB/FAISS) to group millions of erroneous rows into a small set of representative, actionable pattern families.
*   **Air-Gapped Fix Generation:** Leverages local Small Language Models (SLMs) via Ollama (like Phi-3 or Llama) to generate deterministic, auditable fix logic for identified patterns, ensuring compliance and repeatability.
*   **Zero Data Loss Guarantee:** The process is designed around pattern remediation, guaranteeing that no data point is lost or silently corrupted during the repair cycle.

## Example Use Cases
*   **Handling ETL Failures:** When a large batch job fails due to inconsistent formatting across thousands of records (e.g., mixed date formats), this agent clusters the errors and generates a single, deterministic transformation rule to correct all instances.
*   **PII Anomaly Correction:** If sensitive data fields contain unexpected patterns or missing values, the agent isolates these patterns, uses local models for context-aware imputation logic, and flags the remediation steps for audit.
*   **Data Drift Mitigation:** When upstream data sources subtly change their structure over time, causing downstream failures, this agent identifies the new pattern drift cluster and proposes a targeted schema adjustment or cleaning function.