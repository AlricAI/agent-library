# Index

> <div class="md-hero" markdown>

<img src="assets/images/home.png" alt="Molfun" class="hero-image">

**Fine-tune protein structure prediction models wi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
<div class="md-hero" markdown>

<img src="assets/images/home.png" alt="Molfun" class="hero-image">

**Fine-tune protein structure prediction models with modular, plug-and-play architecture.**
Swap attention heads, plug in LoRA adapters, track experiments, and export to production
--- all from a single unified API.

<div class="hero-buttons">
  <a href="getting-started/" class="primary">Get Started</a>
  <a href="https://github.com/rubencr14/molfun" class="secondary">GitHub</a>
</div>

</div>

<div class="section-header" markdown>

## Why Molfun?

Everything you need to fine-tune and deploy protein structure models, in one framework.

</div>

<div class="feature-grid" markdown>

<div class="feature-card" markdown>
<span class="feature-icon">:material-strategy:</span>

### Training Strategies

Four interchangeable fine-tuning strategies out of the box: **Full**, **Head-Only**, **LoRA**, and **Partial**.
Swap strategies in one line without touching the training loop.
</div>

<div class="feature-card" markdown>
<span class="feature-icon">:material-puzzle:</span>

### Modular Architecture

Type-safe registries for attention modules, blocks, embedders, and structure modules.
Build custom architectures with `ModelBuilder` or hot-swap components at runtime.
</div>

<div class="feature-card" markdown>
<span class="feature-icon">:material-database:</span>

### Data Pipeline

Fetch structures from RCSB PDB, parse PDB/mmCIF/A3M/FASTA/SDF/MOL2 files,
generate MSAs, and load affinity data --- all through a consistent, composable API.
</div>

<div class="feature-card" markdown>
<span class="feature-icon">:material-chart-line:</span>

### Experiment Tracking

First-class integrations with **WandB**, **Comet**, **MLflow**, **Langfuse**, and **HuggingFace**.
Or use `CompositeTracker` to log to multiple backends simultaneously.
</div>

<div class="feature-card" markdown>
<span class="feature-icon">:material-lightning-bolt:</span>

### Triton Kernels

GPU-accelerated RMSD computation (

*[truncated — see source for full prompt]*