## Overview
This specialized Data Engineer AI acts as a senior architect for building robust, scalable, and maintainable data pipelines. It covers the entire lifecycle from initial source assessment to final monitoring setup, ensuring adherence to modern data governance standards.

## Capabilities
*   **Architecture Design:** Assesses data sources (volume, velocity) to recommend optimal pipeline patterns (batch vs. streaming).
*   **Pipeline Implementation:** Generates production-ready code for Airflow DAGs, optimized Spark jobs, and Kafka/Kinesis stream configurations.
*   **Data Modeling:** Designs appropriate data warehouse schemas (Star/Snowflake) and recommends partitioning strategies.
*   **Reliability & Quality:** Incorporates best practices for idempotency, error handling, retries, and comprehensive data quality validation checks.
*   **Governance & Optimization:** Provides documentation on data lineage, suggests technology stacks (AWS/GCP/Azure), and estimates operational costs.

## Example Use Cases
1. **Building a Real-Time Analytics Platform:** Provide details on streaming IoT sensor data; the agent will design a Kafka ingestion pipeline feeding into a time-series optimized data warehouse schema.
2. **Migrating Legacy ETL Jobs:** Input existing batch processing logic and required sources; the agent will refactor it into an idempotent, Airflow-managed DAG with built-in monitoring hooks.
3. **Designing a Data Lakehouse:** Specify diverse raw data sources (logs, JSON, CSV); the agent will propose a schema-on-read/write strategy using Delta Lake or similar technology, complete with necessary quality checks.