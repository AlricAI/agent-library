# Hpc Workload Publishing

> This guide explains how providers can publish and manage custom HPC workload templates on VirtEngine.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# HPC Workload Publishing Guide

This guide explains how providers can publish and manage custom HPC workload templates on VirtEngine.

## Overview

VirtEngine provides a curated library of preconfigured HPC workload templates that simplify job submission and ensure security compliance. Providers can also publish custom templates for specialized workloads.

## Built-in Templates

VirtEngine includes five validated built-in templates:

| Template ID | Type | Description |
|------------|------|-------------|
| `mpi-standard` | MPI | Standard MPI-based parallel computing with OpenMPI |
| `gpu-compute` | GPU | GPU-accelerated compute with CUDA support |
| `batch-standard` | Batch | Single-node batch processing |
| `data-processing` | Data Processing | Spark/Dask data pipelines |
| `interactive-session` | Interactive | JupyterLab and terminal sessions |

### Using CLI to List Templates

```bash
# List all available templates
virtengine hpc templates list

# Filter by type
virtengine hpc templates list --type gpu

# Show template details
virtengine hpc templates show mpi-standard

# List available types
virtengine hpc templates types
```

## Publishing Custom Templates

### 1. Define the Template Manifest

Create a workload template with all required fields:

```json
{
  "template_id": "my-simulation",
  "name": "My Simulation Workload",
  "version": "1.0.0",
  "description": "Custom simulation workload for physics calculations",
  "type": "batch",
  "runtime": {
    "runtime_type": "singularity",
    "container_image": "ghcr.io/myorg/simulation:v1.2.3",
    "image_digest": "sha256:abc123...",
    "required_modules": ["gcc/11", "openmpi/4.1"]
  },
  "resources": {
    "min_nodes": 1,
    "max_nodes": 64,
    "default_nodes": 4,
    "min_cpus_per_node": 4,
    "max_cpus_per_node": 128,
    "default_cpus_per_node": 32,
    "min_memory_mb_per_node": 8192,
    "max_memory_mb_per_node": 256000,
    "default_memory_mb_per_node": 64000,
    "min_runtime_minutes": 5,
    "max_run

*[truncated — see source for full prompt]*