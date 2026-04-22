# REPORTING

> The HayMaker CLI provides reporting commands to generate HTML reports from orchestrator metrics.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# HayMaker CLI Reporting

The HayMaker CLI provides reporting commands to generate HTML reports from orchestrator metrics.

## Features

- **Summary Reports**: Overview of all executions, agents, and resources across all scenarios
- **Scenario Reports**: Detailed reports for specific scenarios with agent and resource breakdowns
- **Uses Orchestrator API**: Fetches aggregated metrics directly from the orchestrator's `/api/metrics` endpoint
- **HTML Output**: Clean, professional HTML reports with CSS styling

## Commands

### Generate Summary Report

Generate an overview report for all scenarios:

```bash
# Basic summary report (30-day period)
haymaker report summary

# Custom time period
haymaker report summary --period 90d

# Filter by scenario
haymaker report summary --scenario compute-01

# Custom output file
haymaker report summary --output my-report.html
```

**Options:**
- `--period [7d|30d|90d]`: Time period for metrics (default: 30d)
- `--scenario TEXT`: Filter by scenario name
- `-o, --output PATH`: Output file path (default: report.html)

**Output includes:**
- Total executions and success rate
- Active agents and resources
- Per-scenario metrics (runs, success/fail counts, average duration)
- Resources grouped by type

### Generate Scenario Report

Generate a detailed report for a specific scenario:

```bash
# Basic scenario report
haymaker report scenario compute-01

# Custom time period
haymaker report scenario compute-01 --period 90d

# Custom output file
haymaker report scenario network-01 --output network-report.html
```

**Arguments:**
- `SCENARIO_NAME`: Name of the scenario to report on (required)

**Options:**
- `--period [7d|30d|90d]`: Time period for metrics (default: 30d)
- `-o, --output PATH`: Output file path (default: {scenario}-report.html)

**Output includes:**
- Scenario-specific metrics (runs, success rate, average duration)
- Active resources for this scenario
- Recent agents (last 20) with status and timestamps
- Resources grouped by ty

*[truncated — see source for full prompt]*