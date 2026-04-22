# GROVE SETUP GUIDE

> **Version**: 1.0
**Last Updated**: 2025-11-12

## Overview

This monorepo template includes the complete GROVE (Growth-Oriented Validation & Evolution

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GROVE Planning Infrastructure Setup Guide

**Version**: 1.0
**Last Updated**: 2025-11-12

## Overview

This monorepo template includes the complete GROVE (Growth-Oriented Validation & Evolution) planning infrastructure from Brain Garden. This guide explains how to use the planning system for your projects.

## What is GROVE?

GROVE is a comprehensive planning and documentation system that ensures all work is properly tracked, documented, and quality-controlled. It supports 5 work types:

1. **Features** - New functionality (10-phase lifecycle)
2. **Bugs** - Fixing broken functionality (5-phase lifecycle)
3. **Enhancements** - Improvements to existing features (4-phase lifecycle)
4. **Maintenance** - Code health and infrastructure (type-specific lifecycles)
5. **Borg Assimilations** - Integrating external code (5-phase lifecycle)

## Directory Structure

```
/docs/
├── features/              # All features (10-phase structure)
├── bugs/                  # Bug tracking (5-phase structure)
│   ├── active/            # Currently being worked on
│   └── resolved/          # Fixed bugs
├── borg/                  # External code integrations
│   └── assimilations/
│       ├── active/        # Active assimilations
│       └── completed/     # Completed assimilations
├── project/               # Project-level configuration
│   ├── config/            # Master config and lane configs
│   │   ├── lanes/         # Multi-agent lane configurations
│   │   ├── .conflicts/    # Agent coordination conflicts
│   │   └── .swarm/        # Swarm messaging registry
│   ├── work-registry.json # Central work registry
│   └── work-registry-schema.json # Registry schema
├── templates/             # Templates for all work types
│   ├── feature/
│   ├── bug/
│   ├── enhancement/
│   ├── maintenance/
│   └── borg/
└── WORK_LIFECYCLE.md      # Work type classification guide
```

## Core Documentation Files

### Root Level
- `/FEATURE_LIFECYCLE.md` - Complete feature lifecycle documentation
- `/

*[truncated — see source for full prompt]*