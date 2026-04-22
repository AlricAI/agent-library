# FUTURE ENHANCEMENTS

> This document tracks features that are planned but deferred to future iterations.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Future Enhancements

This document tracks features that are planned but deferred to future iterations. Each section includes:
- Current status (stub, not started, etc.)
- Rationale for deferral
- Implementation considerations
- Links to relevant code stubs

---

## Table of Contents

1. [GPU Acceleration for Embeddings](#gpu-acceleration-for-embeddings)
2. [Embedding Cache](#embedding-cache)
3. [AI-Native Protocols](#ai-native-protocols)
4. [Vector Store Migration Utility](#vector-store-migration-utility)
5. [Advanced Search Features](#advanced-search-features)

---

## GPU Acceleration for Embeddings

### Status: Deferred (Stubs Only)

### Rationale

GPU acceleration for embedding models would significantly improve throughput for batch document ingestion. However, it requires:

1. Platform-specific setup (CUDA drivers, Metal framework, Vulkan SDK)
2. Additional feature flags and conditional compilation
3. Testing infrastructure across multiple GPU types
4. Build complexity for CI/CD

### Implementation Considerations

#### ONNX Runtime Execution Providers

FastEmbed uses `ort` (ONNX Runtime) internally. GPU acceleration can be added via execution providers:

```rust
// Potential implementation in src/rag/embeddings.rs
use ort::{ExecutionProvider, SessionBuilder};

pub enum AccelerationBackend {
    Cpu,
    Cuda { device_id: usize },
    TensorRT { device_id: usize },
    CoreML,  // macOS
    DirectML,  // Windows
    OpenVINO,
}

impl AccelerationBackend {
    fn to_execution_providers(&self) -> Vec<ExecutionProvider> {
        match self {
            Self::Cpu => vec![ExecutionProvider::CPU(Default::default())],
            Self::Cuda { device_id } => vec![
                ExecutionProvider::CUDA(CUDAExecutionProvider::default().with_device_id(*device_id)),
                ExecutionProvider::CPU(Default::default()), // Fallback
            ],
            // ... other providers
        }
    }
}
```

#### Candle GPU Support (for Qwen3)

Qwen3 embeddings use Ca

*[truncated — see source for full prompt]*