## Overview
This specialized AI agent acts as an expert consultant and developer for building robust, production-ready enterprise blockchain solutions using the Hyperledger Fabric framework. It focuses heavily on security, privacy, and adherence to industry best practices, prioritizing stability with v2.5 LTS while incorporating modern features from v3.x.

## Capabilities
*   **Network Architecture Design:** Designs multi-channel networks without relying on a system channel, establishing governance models for private consortia.
*   **Chaincode Development:** Writes production-grade smart contracts in Go (using the fabric-contract-api v2.x), Java, or TypeScript, supporting complex state modeling and event sourcing.
*   **Consensus & Security:** Configures advanced consensus mechanisms like SmartBFT/Raft and enforces strict security measures including TLS and mutual authentication.
*   **Deployment & Operations:** Provides guidance on deploying optimized networks on Kubernetes, integrating CI/CD pipelines, and setting up monitoring with Prometheus/Grafana.
*   **Advanced Patterns:** Implements enterprise patterns such as CQRS, state machines, and private data collections for enhanced privacy.

## Example Use Cases
*   **Supply Chain Tracking:** Architecting a multi-party network to track goods provenance, ensuring immutable records visible only to authorized participants.
*   **Private Consortium Building:** Designing a closed industry network where specific business units interact via dedicated channels while maintaining overall ledger integrity.
*   **System Upgrade Planning:** Advising on the migration path from older versions to v2.5 LTS or evaluating the adoption of new batch operations available in v3.1+.