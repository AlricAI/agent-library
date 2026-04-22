# GGUF USAGE

> This guide covers how to use GGUF models directly with A.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GGUF Model Usage Guide

This guide covers how to use GGUF models directly with A.R.E.S via the LlamaCpp integration for completely local, offline LLM inference.

## What is GGUF?

GGUF (GPT-Generated Unified Format) is a file format for storing models for inference with llama.cpp. It's designed to be:
- **Fast**: Optimized for CPU inference
- **Flexible**: Supports quantization (4-bit, 5-bit, 8-bit)
- **Portable**: Single-file format, easy to distribute
- **Efficient**: Lower memory usage than full-precision models

## Quick Start

### 1. Enable LlamaCpp Feature

Build A.R.E.S with LlamaCpp support:

```bash
# CPU-only
cargo build --features "llamacpp"

# With NVIDIA GPU (CUDA)
cargo build --features "llamacpp-cuda"

# With Apple Silicon GPU (Metal)
cargo build --features "llamacpp-metal"

# With Vulkan GPU
cargo build --features "llamacpp-vulkan"
```

### 2. Download a GGUF Model

Choose a model from Hugging Face. Here are some recommended options:

#### Small Models (Good for testing, < 4GB RAM)

```bash
# Llama 3.2 1B (Fastest, minimal resources)
wget https://huggingface.co/bartowski/Llama-3.2-1B-Instruct-GGUF/resolve/main/Llama-3.2-1B-Instruct-Q4_K_M.gguf

# Phi-3 Mini 3.8B (High quality for size)
wget https://huggingface.co/bartowski/Phi-3-mini-4k-instruct-GGUF/resolve/main/Phi-3-mini-4k-instruct-Q4_K_M.gguf

# Qwen 2.5 1.5B (Multilingual)
wget https://huggingface.co/Qwen/Qwen2.5-1.5B-Instruct-GGUF/resolve/main/qwen2.5-1.5b-instruct-q4_k_m.gguf
```

#### Medium Models (8-16GB RAM)

```bash
# Llama 3.2 3B (Great balance)
wget https://huggingface.co/bartowski/Llama-3.2-3B-Instruct-GGUF/resolve/main/Llama-3.2-3B-Instruct-Q4_K_M.gguf

# Mistral 7B (Excellent performance)
wget https://huggingface.co/TheBloke/Mistral-7B-Instruct-v0.2-GGUF/resolve/main/mistral-7b-instruct-v0.2.Q4_K_M.gguf

# Llama 3.1 8B (Latest, best quality)
wget https://huggingface.co/bartowski/Meta-Llama-3.1-8B-Instruct-GGUF/resolve/main/Meta-Llama-3.1-8B-Instruct-Q4_K_M.gguf
```

#### Large Mod

*[truncated — see source for full prompt]*