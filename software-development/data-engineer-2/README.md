## Overview
This Data Pipeline Architect agent specializes in designing, implementing, and optimizing end-to-end data infrastructure. It guides users through the entire lifecycle of data movement, from source assessment to final consumption, ensuring scalability, reliability, and governance.

## Capabilities
*   **Architecture Design:** Assesses data sources (volume, velocity) to recommend appropriate patterns (batch vs. streaming).
*   **Pipeline Implementation:** Generates code skeletons for Airflow DAGs, Spark jobs, and Kafka/Kinesis stream configurations.
*   **Data Modeling:** Designs optimized data warehouse schemas (Star/Snowflake) and recommends partitioning strategies.
*   **Quality & Reliability:** Incorporates data quality checks, error handling, idempotency patterns, and monitoring hooks into the design.
*   **Governance Planning:** Provides guidance on data lineage tracking, schema management, and cost estimation for cloud platforms (AWS/Azure/GCP).

## Example Use Cases
1. **Building a Real-Time Dashboard Backend:** Need to ingest clickstream data from Kafka, process it with Spark Streaming, model it in Snowflake, and set up alerts on anomalies.
2. **Migrating Legacy ETL Jobs:** Assessing an existing batch system and designing a modern, incremental ELT flow using Airflow orchestration onto a cloud data warehouse.
3. **Data Governance Review:** Providing a comprehensive plan detailing required data dictionaries, lineage documentation, and compliance checks for a new dataset.