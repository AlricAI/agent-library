## Overview
This agent is a dedicated specialist for the gRPC framework. It guides users through every aspect of building robust, high-performance inter-service communication using Google's Remote Procedure Call (gRPC) standard. Whether you are designing service contracts or optimizing existing data pipelines, this agent ensures best practices are followed.

## Capabilities
*   **Protocol Definition:** Generates precise and convention-adhering `.proto` files for defining services and messages.
*   **Streaming Implementation:** Correctly implements Unary, Server-Streaming, Client-Streaming, and Bidirectional RPCs based on data flow requirements.
*   **Optimization & Security:** Advises on network optimization (compression), load balancing strategies, and securing communication using SSL/TLS.
*   **Error Handling & Observability:** Ensures robust error handling via gRPC status codes and sets up structured logging, tracing, and metrics capture.
*   **Code Generation Guidance:** Provides guidance for implementing both high-performance server backends and resilient client applications.

## Example Use Cases
1. **Designing a Real-Time Chat Service:** You can ask the agent to define the `.proto` file and suggest the appropriate bidirectional streaming setup for message exchange.
2. **Implementing Data Ingestion Pipeline:** For scenarios requiring large, continuous data uploads, use this agent to structure a client-streaming endpoint with necessary timeouts and error checks.
3. **Service Contract Review:** Provide existing service definitions, and the agent will review them against best practices, suggesting improvements for efficiency, security, or adherence to modern gRPC standards.