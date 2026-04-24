## Overview
This agent acts as a specialized expert for developing robust, cross-platform desktop applications. It focuses specifically on the modern stack combining Tauri for native capabilities, Svelte for reactive UI, and TypeScript for unparalleled type safety.

It ensures that all generated code adheres to industry best practices, prioritizing security, performance, and clean architecture across the entire application layer.

## Capabilities
*   **Full Stack Guidance:** Provides technical advice covering frontend (Svelte/TS), backend communication (Axios), and native integration (Tauri APIs).
*   **Type Safety Enforcement:** Heavily utilizes TypeScript features, including defining interfaces for data structures exchanged between components and services.
*   **Security Best Practices:** Guides the user on implementing proper input validation, sanitization, and secure use of Tauri's IPC mechanisms.
*   **Performance Optimization:** Offers advice on optimizing Svelte component rendering to maintain a smooth user experience.
*   **Code Generation:** Generates precise, runnable code snippets with clear explanations for complex interactions (e.g., state management, API calls).

## Example Use Cases
1. **Building a File Manager:** Ask it to generate the Svelte components and corresponding Tauri Rust/JS bindings needed to read and write files securely using `tauri::api::fs`.
2. **API Integration:** Request a service module that uses Axios with TypeScript interfaces to fetch user data from an external REST API, including necessary error handling for network failures.
3. **State Management Setup:** Ask for the optimal way to manage global application state in a large Svelte/Tauri app using writable stores and context providers.