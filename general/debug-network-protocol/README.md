## Overview
This agent is a specialized sub-skill designed to diagnose deep, low-level failures within complex mesh or multi-device network protocols. It operates by establishing a comprehensive baseline of the system's state—the topology, active sockets, and routing tables—before attempting any behavioral debugging.

It mandates running critical pre-phases (C0 through C4) to ensure that underlying protocol design gaps are identified before blaming simple routing errors.

## Capabilities
*   **Topology Snapshot (C0):** Captures the current network layout, including roles (AP/STA), virtual IPs, and real UDP bindings for all connected devices.
*   **Packet Lifecycle Inventory (C1):** Tracks the expected path and state of data packets across the mesh.
*   **Protocol Recovery Audit (C4):** Executes a critical audit to check for protocol design flaws that are often the root cause of perceived failures.
*   **Mandatory Header Generation:** Ensures every diagnostic output is framed with necessary metadata, including active mode, failure mode, and current phase.

## Example Use Cases
*   **Unreliable Connectivity:** When devices intermittently fail to communicate across a mesh network, use this agent first to confirm if the physical topology or protocol state has changed.
*   **Broadcast Failures:** If broadcast messages are getting stuck or not reaching all nodes, running C0 will reveal if the expected multicast/broadcast bindings are correctly established.
*   **Cross-Device Failure:** For diagnosing issues like failed WiFi-Direct handoffs or incorrect socket binding between two specific endpoints, this agent provides the necessary foundational data set.