# Hpc Provider Operations

> This guide covers configuring and operating HPC scheduler integrations (SLURM, MOAB, Open OnDemand) with the VirtEngine provider daemon.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# HPC Provider Operations Guide

This guide covers configuring and operating HPC scheduler integrations (SLURM, MOAB, Open OnDemand) with the VirtEngine provider daemon.

## Overview

The VirtEngine provider daemon can integrate with HPC schedulers to execute compute jobs submitted on-chain. The integration supports:

- **SLURM** - Standard HPC workload manager
- **MOAB** - Adaptive Computing's workload manager
- **Open OnDemand (OOD)** - Web-based HPC portal

## Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                     Provider Daemon                              │
│                                                                  │
│  ┌──────────────┐    ┌─────────────────┐    ┌───────────────┐  │
│  │   On-Chain   │    │  HPC Job        │    │  HPCScheduler │  │
│  │   Events     │───▶│  Service        │───▶│  Interface    │  │
│  └──────────────┘    └─────────────────┘    └───────┬───────┘  │
│                              │                       │          │
│                              ▼                       ▼          │
│                      ┌───────────────┐    ┌──────────────────┐ │
│                      │ Usage Reporter │    │ Scheduler        │ │
│                      │ & Auditor      │    │ Adapter          │ │
│                      └───────────────┘    │ (SLURM/MOAB/OOD) │ │
│                                           └──────────────────┘ │
└─────────────────────────────────────────────────────────────────┘
                                                      │
                                                      ▼
                                            ┌──────────────────┐
                                            │  HPC Cluster     │
                                            │  (SLURM/MOAB)    │
                                            └──────────────────┘
```

## Configuration

### Basic Configuration

Add the HPC configuration to your provider daemon config file:

```yaml
hpc:
  

*[truncated — see source for full prompt]*