# Usage Reporting Settlement

> ## Overview

VirtEngine's usage reporting system connects marketplace allocations to settlement and invoicing through a comprehensive pipeline that in

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Usage Reporting and Settlement Integration

## Overview

VirtEngine's usage reporting system connects marketplace allocations to settlement and invoicing through a comprehensive pipeline that includes:

1. **Scheduled Usage Collection** - Periodic metrics collection from workloads
2. **On-Chain Submission** - Signed usage reports submitted to the blockchain
3. **Settlement Pipeline** - Conversion to billable line items
4. **Dispute Resolution** - Time-windowed dispute and correction workflow
5. **Waldur Reconciliation** - Cross-validation with Waldur platform metrics
6. **Anomaly Detection** - Automated fraud and error detection

## Architecture

```
┌─────────────────────┐
│   Usage Meter       │
│   (per workload)    │
└─────────┬───────────┘
          │ ResourceMetrics
          ▼
┌─────────────────────┐
│ Scheduled Collector │
│   (hourly cron)     │
└─────────┬───────────┘
          │ UsageRecord
          ▼
┌─────────────────────┐     ┌──────────────────┐
│ Settlement Pipeline │────▶│ Anomaly Detector │
│                     │     └──────────────────┘
└─────────┬───────────┘              │
          │                          ▼
          │              ┌──────────────────┐
          │              │  Alert Manager   │
          │              └──────────────────┘
          ▼
┌─────────────────────┐
│  Chain Submitter    │
│  (MsgRecordUsage)   │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐     ┌──────────────────┐
│  x/settlement       │◀────│ Dispute Window   │
│  (on-chain)         │     │ (24 hours)       │
└─────────┬───────────┘     └──────────────────┘
          │
          ▼
┌─────────────────────┐
│  Escrow Settlement  │
│  (fund transfer)    │
└─────────────────────┘
```

## Configuration

### Settlement Pipeline Configuration

```go
type SettlementConfig struct {
    // SettlementInterval is the interval for periodic settlements
    SettlementInterval time.Duration // default: 1 hour
    
    // DisputeWindow is the time 

*[truncated — see source for full prompt]*