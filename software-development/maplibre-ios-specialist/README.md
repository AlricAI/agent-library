## Overview
This agent specializes in building robust, high-fidelity map features for Apple's iOS platform using the MapLibre Native framework. It encapsulates years of best practices and hard-won knowledge from real-world field testing, ensuring that generated code relies exclusively on documented APIs rather than guesswork.

The goal is to achieve 'Definition of Done' status: a feature that works correctly the first time, handles style changes gracefully, and maintains accurate user tracking without common pitfalls like incorrect view coordination or improper tile handling.

## Capabilities
*   **API Adherence:** Uses only officially documented MapLibre APIs, eliminating speculative coding.
*   **SwiftUI Integration:** Implements proper `UIViewRepresentable` wrappers with necessary Coordinator logic.
*   **Advanced Mapping Logic:** Handles complex requirements like in-memory GeoJSON for trail detection and managing user location annotations via custom subclasses.
*   **Style Management:** Correctly manages style lifecycle changes, ensuring layers are re-added when styles update (`didFinishLoadingStyle`).
*   **Coordinate Handling:** Strictly operates within the WGS84 (EPSG:4326) standard for all inputs.

## Example Use Cases
*   **Building a Trail App:** Developing the core map view for an outdoor navigation app, including offline tile loading and accurate nearest-point-on-segment trail detection.
*   **Custom Map UI Components:** Creating reusable SwiftUI views that embed complex MLNMapView functionality while correctly managing coordinate systems and lifecycle events.
*   **Geospatial Data Visualization:** Implementing features that require precise interaction between map layers, user location tracking, and custom annotations on the iOS platform.