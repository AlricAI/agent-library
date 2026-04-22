# Package

> ## Overview

This document describes the package structure of CoreOverlay and the responsibilities of each Swift package.

CoreOverlay is designed as 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CoreOverlay Package Structure

## Overview

This document describes the package structure of CoreOverlay and the responsibilities of each Swift package.

CoreOverlay is designed as a distributed execution and storage platform built around the following architectural principles:

- A Kademlia-based distributed hash table (DHT) for node discovery and routing
- A WebAssembly-based execution environment
- A distributed actor-oriented execution model
- A consistency model for distributed variables
- A storage architecture separated from the execution overlay when necessary

The package structure is intentionally designed to reflect these architectural boundaries.  
Each package should have a clear responsibility and a minimal, well-defined dependency surface.

The overall goal is to make CoreOverlay modular, testable, and incrementally implementable.

---

## Design Principles

The package structure follows these principles:

### 1. Clear Responsibility Boundaries

Each package should represent a distinct concern in the system, such as cryptography, networking, routing, execution, or storage.

### 2. Layered Dependency Direction

Low-level packages should not depend on high-level packages.  
For example, common types and cryptography should be usable independently from runtime or actor execution.

### 3. Replaceable Implementations

Where possible, packages should expose protocols or abstractions so that implementations may be replaced later.  
For example, the runtime may initially wrap one WebAssembly engine and later support others.

### 4. Incremental Development

The system should be buildable in stages.  
A minimal CoreOverlay node should be possible before actor execution, distributed storage, or strong consistency features are introduced.

---

## Package Layers

The packages are organized into the following conceptual layers:

1. Foundation packages
2. Networking and discovery
3. Overlay and routing
4. Storage and consistency
5. Runtime and execution
6. Securi

*[truncated — see source for full prompt]*