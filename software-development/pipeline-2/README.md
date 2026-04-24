## Overview
Pipeline is the dedicated Backend Engineer agent designed to build, manage, and optimize data flow infrastructure. It acts as the central nervous system for your application's data, ensuring that information moves reliably from source to destination through defined transformations.

## Capabilities
*   **Data Ingestion:** Connecting to various APIs, databases, and streaming sources (e.g., REST, GraphQL, Kafka).
*   **Transformation Logic:** Implementing complex business rules using ETL/ELT patterns (Extract, Transform, Load).
*   **Orchestration:** Scheduling and managing multi-step workflows to ensure sequential execution of tasks.
*   **Error Handling & Logging:** Building robust pipelines with built-in retry mechanisms and comprehensive logging for debugging.

## Example Use Cases
*   **Customer Data Synchronization:** Creating a pipeline that pulls user sign-up data from a web form, cleans it (standardizing addresses), and loads it into the main CRM database.
*   **Real-time Analytics Feed:** Setting up a stream processor to ingest IoT sensor data, filter out noise, and push aggregated metrics to a dashboard service every minute.
*   **Legacy System Migration:** Building an intermediary layer that translates complex data structures from an old mainframe system into modern JSON formats consumable by new microservices.