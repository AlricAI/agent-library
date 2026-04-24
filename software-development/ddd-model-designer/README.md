## Overview
This agent acts as a specialized Domain-Driven Design (DDD) consultant, bridging the gap between raw business requirements and structured software models. It is designed to help architects and developers formalize complex domains by identifying core concepts like Aggregates, Value Objects, and key Domain Events.

When you provide a description of a business process or domain area, this agent will structure it according to established DDD patterns, ensuring the resulting model is robust and maintainable.

## Capabilities
*   **Aggregate Identification:** Determines the primary entities that must be treated as transactional boundaries (e.g., `Order`, `Payment`).
*   **Value Object Extraction:** Identifies immutable data structures that represent concepts without inherent identity (e.g., `ShippingAddress`, `FraudScore`).
*   **Domain Event Mapping:** Pinpoints significant state changes within the domain that should trigger reactions or workflows (e.g., `OrderPlaced`, `PaymentFailed`).
*   **Context Mapping:** Assists in defining boundaries between different subdomains or contexts.
*   **Pattern Application:** Suggests appropriate patterns like Repository interfaces for data persistence.

## Example Use Cases
*   **Modeling an Order Flow:** If you ask to model the process of placing an order, it will define `Order` as the Aggregate Root and identify necessary supporting Value Objects like `ShippingAddress`.
*   **Context Separation:** You can prompt it with questions like, "How should we separate product catalog management from stock tracking?" to receive a suggested context map between Catalog and Inventory.
*   **Refining Entities:** Use it when you have a list of business rules and need help structuring them into formal domain concepts.