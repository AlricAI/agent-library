# GGUF EMBEDDINGS

> This document describes how to use local GGUF models for embeddings in Remembrances-MCP.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GGUF Embeddings Support

This document describes how to use local GGUF models for embeddings in Remembrances-MCP.

## Overview

Remembrances-MCP now supports loading local GGUF embedding models directly using the go-llama.cpp library. This provides:

- **Privacy**: All embeddings are generated locally, no data sent to external services
- **Performance**: Direct model inference without network latency
- **Cost**: No API costs for embedding generation
- **Flexibility**: Support for quantized models (Q4_K_M, Q8_0, etc.) to balance speed and accuracy

## Supported Models

The implementation supports GGUF embedding models based on:

- **Nomic Embed** (nomic-bert architecture)
  - nomic-embed-text-v1.5 (768 dimensions)
  - nomic-embed-text-v2 (768 dimensions)
  - nomic-embed-text-v2-moe (768 dimensions)
  
- **Qwen** embedding models
- Other BERT-based embedding models in GGUF format

## Installation

### Prerequisites

1. **Go 1.21+** installed
2. **C/C++ compiler** (gcc, clang, or MSVC)
3. **Make** (for building llama.cpp)
4. **Git** with submodules support

### Building

1. **Clone with submodules**:
   ```bash
   git clone --recurse-submodules https://github.com/madeindigio/remembrances-mcp
   cd remembrances-mcp
   ```

2. **Build the project**:
   ```bash
   # Default build (CPU only on Linux, Metal on macOS)
   make build
   
   # With CUDA support (Linux with NVIDIA GPU)
   make BUILD_TYPE=cublas build
   
   # With ROCm support (Linux with AMD GPU)
   make BUILD_TYPE=hipblas build
   
   # With OpenBLAS support
   make BUILD_TYPE=openblas build
   ```

3. **Check build environment**:
   ```bash
   make check-env
   ```

## Configuration

### Using CLI Flags

```bash
./build/remembrances-mcp \
  --gguf-model-path /path/to/nomic-embed-text-v1.5.Q4_K_M.gguf \
  --gguf-threads 8 \
  --gguf-gpu-layers 32
```

### Using Environment Variables

```bash
export GOMEM_GGUF_MODEL_PATH="/path/to/nomic-embed-text-v1.5.Q4_K_M.gguf"
export GOMEM_GGUF_THREADS=8
export GOMEM_GGU

*[truncated — see source for full prompt]*