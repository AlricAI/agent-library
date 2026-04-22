# Architecture

> OpenSandbox is a universal sandbox platform designed for AI application scenarios, providing a complete solution with multi-language SDKs, standardize

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OpenSandbox Architecture

OpenSandbox is a universal sandbox platform designed for AI application scenarios, providing a complete solution with multi-language SDKs, standardized sandbox protocols, and flexible runtime implementations. This document describes the overall architecture and design philosophy of OpenSandbox.

## Architecture Overview

![OpenSandbox Architecture](assets/architecture.svg)

The OpenSandbox architecture consists of four main layers:

1. **SDKs Layer** - Client libraries for interacting with sandboxes
2. **Specs Layer** - OpenAPI specifications defining the protocols
3. **Runtime Layer** - Server implementations managing sandbox lifecycle
4. **Sandbox Instances Layer** - Running sandbox containers with injected execution daemons

## 1. OpenSandbox SDKs

The SDK layer provides high-level abstractions for developers to interact with sandboxes. It handles communication with both the Sandbox Lifecycle API and the Sandbox Execution API.

### Core SDK Components

#### 1.1 Sandbox

The `Sandbox` class is the primary entry point for managing sandbox lifecycle:

- **Create**: Provision new sandbox instances from container images
- **Manage**: Monitor sandbox state, renew expiration, retrieve endpoints
- **Destroy**: Terminate sandbox instances when no longer needed

**Key Features:**
- Async/await support for non-blocking operations
- Automatic state polling for provisioning progress
- Resource quota management (CPU, memory, GPU)
- Metadata and environment variable injection
- TTL-based automatic expiration with renewal

#### 1.2 Filesystem

The `Filesystem` component provides comprehensive file operations within sandboxes:

- **CRUD Operations**: Create, read, update, and delete files and directories
- **Bulk Operations**: Upload/download multiple files efficiently
- **Search**: Glob-based file searching with pattern matching
- **Permissions**: Manage file ownership, group, and mode (chmod)
- **Metadata**: Retrieve file info including size, timesta

*[truncated — see source for full prompt]*