# Meshrabiya Architecture

> This document provides a comprehensive architecture diagram and mapping of all non-test Java/Kotlin files in the Meshrabiya module, including their re

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Meshrabiya Module: Complete Architecture Overview

This document provides a comprehensive architecture diagram and mapping of all non-test Java/Kotlin files in the Meshrabiya module, including their relationships, responsibilities, and integration points.

---

## 1. Core Managers & Services

- **MeshGossipService.kt**
  - Mesh-wide messaging, gossip protocol, chunk/file transfer.
  - Consumes neighbor lists from `OriginatingMessageManager`.
  - Owns `CustomDataStore`.
  - Integrates with `ReplicationManager`, `MeshRoleManager`, and storage managers.

- **OriginatingMessageManager.kt**
  - Maintains mesh topology, neighbor health, routing, node announcements.
  - Provides neighbor lists to `MeshGossipService`.

- **EmergentRoleManager.kt** / **MeshRoleManager.kt**
  - Role assignment, mesh participation controls, event-driven signaling.

- **ReplicationManager.kt**
  - Manages replication logic, interacts with storage managers and gossip service.

- **MeshStorageManager.kt** (UI-driven, legacy)
  - File drop management, chunking, transfer, replication.
  - To be refactored into `DistributedStorageManager` / `DropFileManager`.
- Will be renamed to `DropFileManager.kt` and absorb legacy storage logic.

- **DistributedStorageManager.kt** (Generalized)
  - Distributed storage, quota, encryption, mesh sync, replication.


- **MeshrabiyaConstants.kt**
  - Centralized configuration, settings, constants for all managers/services.

---

## 2. Supporting Components

- **CustomDataStore.kt**
  - Mesh-specific data persistence, used by `MeshGossipService` and others.

- **ServiceRegistry.kt**
  - Manifest-driven service registration and lookup.

- **SecurityManager.kt** / **EncryptionUtils.kt**
  - Encryption, permissioning, security controls for mesh and storage.

- **QuotaManager.kt**
  - Quota management for distributed storage and mesh participation.

---

## 3. Models & Utilities

- **MeshNode.kt**, **MeshNeighbor.kt**, **MeshMessage.kt**, etc.
  - Data models for mesh n

*[truncated — see source for full prompt]*