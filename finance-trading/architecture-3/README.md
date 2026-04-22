# Architecture

> ## Overview

Harvest is a trading framework with two architectural paths that currently coexist:

1. The legacy runtime built around `BrokerHub` in `h

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Architecture

## Overview

Harvest is a trading framework with two architectural paths that currently coexist:

1. The legacy runtime built around `BrokerHub` in `harvest/trader/trader.py`.
2. The newer service-oriented runtime built around `Orchestrator` in `harvest/orchestrator.py`.

New work should generally prefer the orchestrator and service path unless the task is specifically about compatibility with the legacy runtime.

## Core Domains

### Algorithms

- `harvest/algorithm.py` contains the newer `Algorithm` abstraction.
- `harvest/algo.py` contains the legacy `BaseAlgo` abstraction that is still used by the CLI flow.
- Algorithms define trading logic, watchlists, and indicator-driven behavior.

### Brokers

- `harvest/broker/_base.py` defines the broker contract.
- Concrete implementations live under `harvest/broker/`.
- Brokers are responsible for market data access, order placement, account access, and broker-specific capabilities.

### Storage

- `harvest/storage/_base.py` defines local and central storage models.
- `LocalAlgorithmStorage` is algorithm-local.
- `CentralStorage` is shared storage for price history and account-level data.
- Duplication between local and central storage code is intentional and should not be removed casually.

### Services

- `harvest/services/` contains the newer service-oriented architecture.
- Key services include market data, broker access, algorithms, central storage, and service discovery.
- `Orchestrator` wires these services together and manages lifecycle.

### Events

- `harvest/events/event_bus.py` provides the event bus.
- `harvest/events/events.py` defines event payload types.
- The orchestrator path is event-driven and uses these abstractions to decouple components.

## Entry Points

### CLI

- The `harvest` console script points to `harvest.cli:main`.
- `harvest start` scans a directory for `BaseAlgo` subclasses and runs them through the legacy `BrokerHub` flow.
- This means the default CLI behavior is still t

*[truncated — see source for full prompt]*