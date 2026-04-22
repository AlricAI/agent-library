# Hpc Node Agent

> The HPC Node Agent is a lightweight daemon that runs on HPC compute nodes to report health, capacity, and latency metrics to the provider daemon for on-chain node metadata updates.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# HPC Node Agent

The HPC Node Agent is a lightweight daemon that runs on HPC compute nodes to report health, capacity, and latency metrics to the provider daemon for on-chain node metadata updates.

## Overview

The node agent implements VE-500: Node Registration and Heartbeat Pipeline, which enables:

- Automated node registration with cryptographic identity
- Periodic heartbeat with capacity, health, and latency metrics
- Signed payload submission to the provider daemon
- Stale node detection and automatic deactivation

## Architecture

```
┌─────────────────────┐     ┌─────────────────────┐     ┌─────────────────┐
│   HPC Node Agent    │────▶│   Provider Daemon   │────▶│   Blockchain    │
│   (hpc-node-agent)  │     │   (HPC Aggregator)  │     │   (x/hpc)       │
└─────────────────────┘     └─────────────────────┘     └─────────────────┘
         │                           │                          │
    Signed                     Batch                    MsgUpdateNode
   Heartbeats                Submission                   Metadata
```

## Installation

### Building from Source

```bash
# From the repository root
go build -o hpc-node-agent ./cmd/hpc-node-agent

# Install to system path
sudo mv hpc-node-agent /usr/local/bin/
```

### Configuration

Create a configuration file at `/etc/virtengine/hpc-node-agent.yaml`:

```yaml
node-id: "node-001"
cluster-id: "hpc-cluster-1"
provider-address: "virtengine1provider..."
provider-daemon-url: "http://provider-daemon:8081"
heartbeat-interval: 30s
key-file: "/etc/virtengine/virtengine-agent.key"
region: "us-east-1"
datacenter: "dc1"
zone: "a"
rack: "rack-7"
row: "row-2"
position: "u14"
latency-targets:
  - "node-002"
  - "node-003"
log-level: "info"
```

## Usage

### Initialize Node Keys

Before running the agent, initialize the Ed25519 key pair:

```bash
hpc-node-agent init --key-file /etc/virtengine/virtengine-agent.key
```

This generates a key pair and outputs the public key. The public key must be registered wi

*[truncated — see source for full prompt]*