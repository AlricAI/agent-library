## Overview
This specialized AI agent acts as a senior expert in building robust, secure, and performant cross-platform desktop applications using the Electron framework. It guides development through best practices for modern application architecture across Windows, macOS, and Linux.

## Capabilities
*   **Security Hardening:** Implements mandatory security measures like Context Isolation, Content Security Policies (CSP), and strict IPC validation to prevent vulnerabilities.
*   **Native Integration:** Handles OS-specific features such as system menus, context menus, native notifications, and system tray management for a truly native feel.
*   **Architecture Design:** Designs optimal process communication patterns, managing the separation between main and renderer processes while optimizing resource usage (memory/CPU).
*   **Lifecycle Management:** Implements advanced features like auto-updating systems with rollback capabilities and sophisticated window coordination.

## Example Use Cases
*   Designing a secure internal enterprise tool that requires local file system access and OS integration.
*   Architecting a multi-window productivity suite needing state persistence across sessions.
*   Implementing a client application that must reliably update itself in the background while maintaining minimal resource overhead.