# CROSS COMPILE

> This guide explains how to cross-compile `remembrances-mcp` for multiple platforms (Linux, macOS, Windows) using Docker.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Cross-Compilation Guide for remembrances-mcp

This guide explains how to cross-compile `remembrances-mcp` for multiple platforms (Linux, macOS, Windows) using Docker.

## Overview

The project uses a custom Docker image based on `goreleaser-cross` with additional tools for:
- **Rust cross-compilation** for building `surrealdb-embedded`
- **CMake and build tools** for compiling `llama.cpp` shared libraries
- **Cross-compilation toolchains** for multiple architectures

## Prerequisites

- Docker installed and running
- Sufficient disk space (~10GB for Docker image and build artifacts)
- Access to `~/www/MCP/Remembrances/` directory with:
  - `go-llama.cpp` module
  - `surrealdb-embedded` module

## Quick Start

### 1. Build the Custom Docker Image

First, build the custom Docker image with Rust and build tools:

```bash
./scripts/build-docker-image.sh
```

This creates an image named `remembrances-mcp-builder:v1.23-rust` with all necessary tools.

### 2. Run Cross-Compilation

Use the custom image to build for all platforms:

```bash
export GORELEASER_CROSS_IMAGE=remembrances-mcp-builder:latest
./scripts/release-cross.sh --clean snapshot
```

Or skip building shared libraries (faster, but binaries won't have embedded functionality):

```bash
export GORELEASER_CROSS_IMAGE=remembrances-mcp-builder:latest
./scripts/release-cross.sh --skip-libs --clean snapshot
```

## Build Scripts

### `scripts/build-docker-image.sh`

Builds the custom Docker image with Rust and build tools.

**Options:**
- `-t, --tag TAG`: Specify image tag (default: v1.23-rust)
- `-n, --name NAME`: Specify image name (default: remembrances-mcp-builder)
- `--no-cache`: Build without cache
- `--push`: Push to registry after building

**Examples:**
```bash
# Build with default settings
./scripts/build-docker-image.sh

# Build with custom tag
./scripts/build-docker-image.sh --tag latest

# Build without cache
./scripts/build-docker-image.sh --no-cache
```

### `scripts/release-cross.sh`

Main script for

*[truncated — see source for full prompt]*