# Gen Docs For Goose

> Generate comprehensive module documentation for the Goose tool's mdBook in docs/src/developers/modules/, providing top-down analysis of functionality,

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Goal

Generate comprehensive module documentation for the Goose tool's mdBook in docs/src/developers/modules/, providing top-down analysis of functionality, inter-module
relationships, business purposes, and detailed implementation documentation with visual diagrams.

# Documentation Structure

1. Overview Documentation (docs/src/developers/modules/index.md)

Create a top-level architecture document that includes:

# Goose Tool Module Architecture

## Overview
[High-level description of Goose's purpose as an incident response and hunt tool for Microsoft cloud environments]

## Architecture Diagram
```mermaid
graph TB
    subgraph "Entry Points"
        CLI[main.py<br/>CLI Interface]
    end

    subgraph "Core Orchestration"
        HONK[honk.py<br/>Data Collection Orchestrator]
        DD[datadumper.py<br/>Base Dumper Class]
    end

    subgraph "Infrastructure"
        AUTH[auth.py<br/>Authentication]
        CONF[conf.py<br/>Configuration]
        UTILS[utils.py<br/>Utilities]
        CSV[csv.py<br/>CSV Export]
    end

    subgraph "Data Collectors"
        M365[m365_datadumper.py<br/>M365 Data]
        AZURE[azure_dumper.py<br/>Azure Resources]
        ENTRA[entra_id_datadumper.py<br/>Entra ID]
        MDE[mde_datadumper.py<br/>Defender]
        D4IOT[d4iot_dumper.py<br/>IoT Security]
    end

    CLI --> HONK
    HONK --> DD
    DD --> M365
    DD --> AZURE
    DD --> ENTRA
    DD --> MDE
    DD --> D4IOT

    M365 --> AUTH
    AZURE --> AUTH
    ENTRA --> AUTH
    MDE --> AUTH
    D4IOT --> AUTH
    D4IOT --> D4BASE[d4iot.py]

    AUTH --> CONF
    HONK --> UTILS
    M365 --> UTILS
    AZURE --> UTILS
    ENTRA --> UTILS
    MDE --> UTILS

    M365 --> CSV
    AZURE --> CSV
    ENTRA --> CSV
    MDE --> CSV
```

Module Categories

1. Entry Points

- main.py: CLI entry point using Google Fire

2. Core Orchestration

- honk.py: Main orchestration engine
- datadumper.py: Base class for all data collectors

3. Infrastructure Services

- auth.py: Microsoft auth

*[truncated — see source for full prompt]*