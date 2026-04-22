# ARCHITECTURE

> ## Table of Contents
1. [Overview](#overview)
2. [System Architecture](#system-architecture)
3. [Module Organization](#module-organization)
4. [Design

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Sourcerer Architecture Documentation

## Table of Contents
1. [Overview](#overview)
2. [System Architecture](#system-architecture)
3. [Module Organization](#module-organization)
4. [Design Patterns](#design-patterns)
5. [Core Workflows](#core-workflows)
6. [Component Details](#component-details)

---

## Overview

Sourcerer is a modern, multi-CPU disassembler built with clean code principles following SOLID design patterns. The architecture emphasizes:

- **Modularity**: Clear separation of concerns with focused components
- **Extensibility**: Plugin architecture for CPUs, disk formats, and output formatters
- **Maintainability**: Strategy pattern extraction eliminates god classes
- **Testability**: Dependency injection enables isolated unit testing

### Key Design Principles Applied

- **Single Responsibility Principle**: Each class has one well-defined purpose
- **Open/Closed Principle**: Extensible via plugins without modifying core code
- **Liskov Substitution**: CPU plugins and formatters are interchangeable
- **Interface Segregation**: Minimal, focused interfaces
- **Dependency Inversion**: Core depends on abstractions, not concrete implementations

---

## System Architecture

### High-Level Component Diagram

```mermaid
graph TB
    subgraph "Entry Point"
        Main[main.cpp]
    end

    subgraph "Workflow Layer"
        Workflow[DisassemblerWorkflow]
        Orchestrator[DisassemblyOrchestrator]
    end

    subgraph "Core Layer"
        Binary[Binary]
        Instruction[Instruction]
        AddressMap[AddressMap]
        SymbolTable[SymbolTable]
        Constants[Constants]
    end

    subgraph "Analysis Layer"
        CodeAnalyzer[CodeAnalyzer<br/>Orchestrator]
        ExecutionSim[ExecutionSimulator<br/>Dynamic Analysis]

        subgraph "Analysis Strategies"
            DataHeuristics[DataHeuristics]
            GraphicsDetector[GraphicsDetector]
            JumpTableDetector[JumpTableDetector]
            InlineDataScanner[InlineDataScanner]
  

*[truncated — see source for full prompt]*