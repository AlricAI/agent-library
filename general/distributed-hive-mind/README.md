# Distributed Hive Mind

> ## Overview

The distributed hive mind replaces the centralized `InMemoryHiveGraph` for deployments with 20+ agents. Instead of every agent holding al

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Distributed Hive Mind Architecture

## Overview

The distributed hive mind replaces the centralized `InMemoryHiveGraph` for deployments with 20+ agents. Instead of every agent holding all facts in memory, facts are partitioned across agents via consistent hashing (DHT). Queries route to the relevant shard owners instead of scanning all agents.

## Architecture

```mermaid
graph TB
    subgraph "Distributed Hash Ring (pure DHT, O(F/N) per agent)"
        direction LR
        R["Hash Ring<br/>Facts hashed to positions<br/>Agents own keyspace ranges"]
    end

    subgraph "Agent Shards"
        A0["Agent 0<br/>Shard: ~F/N facts<br/>Kuzu DB (256MB)"]
        A1["Agent 1<br/>Shard: ~F/N facts<br/>Kuzu DB (256MB)"]
        A2["Agent 2<br/>Shard: ~F/N facts<br/>Kuzu DB (256MB)"]
        AN["Agent N<br/>Shard: ~F/N facts<br/>Kuzu DB (256MB)"]
    end

    subgraph "Shard Transport (Event Hubs)"
        EH["Azure Event Hubs<br/>Explicit partition_id routing<br/>Per-app consumer groups<br/>(cg-app-N, 20 groups)"]
    end

    subgraph "Gossip Layer"
        G["Bloom Filter Exchange<br/>O(log N) convergence<br/>Pull missing facts from peers"]
    end

    R --> A0
    R --> A1
    R --> A2
    R --> AN
    A0 <-.->|SHARD_QUERY / SHARD_RESPONSE| EH
    A1 <-.->|SHARD_QUERY / SHARD_RESPONSE| EH
    A2 <-.->|SHARD_QUERY / SHARD_RESPONSE| EH
    AN <-.->|SHARD_QUERY / SHARD_RESPONSE| EH
    A0 <-.->|gossip| A1
    A1 <-.->|gossip| A2
    A2 <-.->|gossip| AN

    style R fill:#f9f,stroke:#333
    style G fill:#ff9,stroke:#333
    style EH fill:#9cf,stroke:#333
```

### Shard Transport: Event Hubs (as of 2026-03-13)

Cross-shard queries travel over **Azure Event Hubs** via `EventHubsShardTransport` (replacing the former Service Bus shard topic). Key design points:

| Aspect       | Detail                                                                                                                                                                                                   

*[truncated — see source for full prompt]*