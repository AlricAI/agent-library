# Benchmark Methodology

> Vectro's benchmark harness (`python.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Benchmark Methodology

Vectro's benchmark harness (`python.benchmark`) provides reproducible,
hardware-aware comparisons across compression profiles, backends, and datasets.

---

## Running Benchmarks

### Quick CLI run

```bash
python -m python.benchmark --n 1000 --dim 768 --config demo
```

### Programmatic API

```python
from python.benchmark import BenchmarkSuite, BenchmarkReport
import numpy as np

rng = np.random.default_rng(42)
embeddings = rng.standard_normal((1_000, 768)).astype(np.float32)

suite = BenchmarkSuite(embeddings, n_runs=5)
report: BenchmarkReport = suite.run_all()

print(f"Best profile       : {report.best_profile}")
print(f"Best compression   : {report.best_compression_ratio:.2f}×")
print(f"Best recall@10     : {report.best_recall:.4f}")

# Export results
report.to_json("results.json")
report.to_csv("results.csv")
```

---

## What Is Measured

Each benchmark run captures:

| Metric | Description |
|--------|-------------|
| **Compression ratio** | `original_bytes / compressed_bytes` |
| **Reconstruction MSE** | Mean squared error between original and dequantized vectors |
| **Mean cosine similarity** | Average cosine similarity between original and reconstructed vectors |
| **Throughput** | Millions of vectors per second during compression |
| **Decompression throughput** | Millions of vectors per second during reconstruction |
| **Memory footprint** | Peak RSS delta during the compression pass |
| **Latency p50/p95/p99** | Percentile latencies for the full compress→decompress round-trip |

Hardware metadata (CPU model, core count, available memory, platform) is
recorded automatically in every `BenchmarkReport`.

---

## Interpreting Results

### Compression Ratio

A ratio of `4.0×` means the compressed artifact is 4 times smaller than the
float32 original. INT8 quantization typically achieves ~4× for standard
float32 embeddings; INT4 achieves ~8×.

### Mean Cosine Similarity

This is the primary **quality** metric. It measures whether com

*[truncated — see source for full prompt]*