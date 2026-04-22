# Getting Started

> Vectro is an ultra-high-performance LLM embedding compressor.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Getting Started with Vectro

Vectro is an ultra-high-performance LLM embedding compressor. It compresses floating-point
embedding vectors using nine quantization strategies, achieving 4–32× storage savings
with configurable quality trade-offs.

---

## Installation

### From PyPI

```bash
pip install vectro
```

### With optional extras

```bash
# Arrow/Parquet I/O
pip install "vectro[data]"

# Vector DB and ML framework integrations
pip install "vectro[integrations]"

# Everything
pip install "vectro[data,integrations]"
```

### From source (requires [Pixi](https://prefix.dev))

```bash
git clone https://github.com/wesleyscholl/vectro
cd vectro
pixi install
pixi run python -c "import python; print(python.__version__)"
```

---

## Quickstart: Compress Your First Batch of Embeddings

```python
import numpy as np
from python import Vectro

# Simulate 1 000 embeddings of dimension 768 (BERT/MPNet size)
rng = np.random.default_rng(42)
embeddings = rng.standard_normal((1_000, 768)).astype(np.float32)

vectro = Vectro()

# Compress the whole batch at once
result = vectro.compress_batch(embeddings)
print(f"Compression ratio: {result.compression_ratio:.2f}×")
print(f"Original size : {result.total_original_bytes:,} bytes")
print(f"Compressed size: {result.total_compressed_bytes:,} bytes")
```

---

## Save and Load Artifacts

```python
# Save to disk
vectro.save_compressed(result, "embeddings.npz")

# Load back
result2 = vectro.load_compressed("embeddings.npz")

# Reconstruct float32 vectors
from python import decompress_vectors
restored = decompress_vectors(result2)
print(restored.shape)   # (1000, 768)
```

---

## Choosing a Compression Profile

Vectro ships with pre-tuned profiles that trade quality for speed and size:

| Profile | Precision | Compression | Cosine sim | Use case |
|---------|-----------|-------------|------------|----------|
| `speed` | INT8 | ~4× | 99.97% | Real-time inference |
| `balanced` | INT8 | ~4× | 99.97% | General purpose |
| `quality` | INT

*[truncated — see source for full prompt]*