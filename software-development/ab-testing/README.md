# Ab Testing

> ## Overview

The A/B testing infrastructure allows ModPorter AI to compare different AI agent strategies and measure their performance. This system en

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# A/B Testing Infrastructure Documentation

## Overview

The A/B testing infrastructure allows ModPorter AI to compare different AI agent strategies and measure their performance. This system enables data-driven decisions about which agent configurations produce the best results for mod conversion.

## Architecture

The A/B testing system consists of three main components:

1. **Database Schema** - Tables for storing experiments, variants, and results
2. **Backend API** - Endpoints for managing experiments and recording results
3. **AI Engine Integration** - Support for loading different agent configurations based on experiment variants
4. **Frontend UI** - Interfaces for creating experiments and viewing results

## Database Schema

### experiments
Stores information about each A/B test.

| Column | Type | Description |
|--------|------|-------------|
| id | UUID | Unique identifier |
| name | VARCHAR(255) | Experiment name |
| description | TEXT | Description of the experiment |
| start_date | TIMESTAMP | When the experiment starts |
| end_date | TIMESTAMP | When the experiment ends |
| status | VARCHAR(20) | Draft, active, paused, or completed |
| traffic_allocation | INTEGER | Percentage of traffic (0-100) |
| created_at | TIMESTAMP | Creation timestamp |
| updated_at | TIMESTAMP | Last update timestamp |

### experiment_variants
Stores different strategies/variants within an experiment.

| Column | Type | Description |
|--------|------|-------------|
| id | UUID | Unique identifier |
| experiment_id | UUID | Foreign key to experiments |
| name | VARCHAR(255) | Variant name |
| description | TEXT | Description of the variant |
| is_control | BOOLEAN | Whether this is the control group |
| strategy_config | JSONB | Configuration for agent strategies |
| created_at | TIMESTAMP | Creation timestamp |
| updated_at | TIMESTAMP | Last update timestamp |

### experiment_results
Records the outcomes of conversion runs for analysis.

| Column | Type | Description |
|-----

*[truncated — see source for full prompt]*