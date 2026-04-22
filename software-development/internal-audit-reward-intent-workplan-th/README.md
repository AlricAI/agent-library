# INTERNAL AUDIT REWARD INTENT WORKPLAN TH

> ## 0) Context (CODEX /CREATE_PLATFORM_WORK)
- **Initiative:** Ledger-Driven Integrity Platform for Audit, Rewards, and Cross-Session Intent Detection


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Internal Audit + Reward Integrity + Intent Intelligence Work Plan

## 0) Context (CODEX /CREATE_PLATFORM_WORK)
- **Initiative:** Ledger-Driven Integrity Platform for Audit, Rewards, and Cross-Session Intent Detection
- **Scope:** services (`ledger-explorer-api`, `reward-guardrails`, `intent-graph-service`), protocol/schema, observability pipeline, ops runbooks, migration path
- **Drivers:** reliability, security/compliance, anti-gaming protection, lower fraud-loss cost, devex for risk-team analytics
- **Current state (as-is):** มี ledger records และ session-level telemetry อยู่แล้ว แต่ยังขาด API สำหรับ audit query แบบ time-range/QoU, ขาด dynamic reward controls, และยัง correlate intent ได้แค่ session เดียว
- **Target state (to-be):** มี API ตรวจสอบ ledger ระดับ audit-ready พร้อม hash-chain continuity checks, มีกลไก Adaptive Reward Guardrails ปรับเพดาน/พื้นรางวัลตามความเสี่ยงแบบเรียลไทม์, และมี Cross-Session Intent Graph สำหรับจับ long-horizon anomaly
- **Constraints:**
  - SLO: Explorer API P95 < 300ms (cached) / < 900ms (cold query)
  - Risk gate latency: < 80ms ต่อ reward decision
  - Timeline: 3 phases / 10 สัปดาห์
  - Compliance: immutable audit trail, retention 18 เดือน, policy explainability
  - Budget: เพิ่ม infra cost ไม่เกิน 20% จาก baseline telemetry stack
- **Dependencies:** Platform backend, Risk/Trust & Safety, Data engineering, Security, Internal audit stakeholders

---

## 1) Workstreams

### WS1 — Architecture
- แยก bounded context: `Ledger Explorer`, `Reward Risk Engine`, `Intent Graph`
- ออกแบบ shared IDs (`entity_id`, `session_id`, `packet_id`, `chain_id`) และ event-time semantics
- นิยาม data flow: ingest → normalize → feature compute → decision/query surfaces

### WS2 — Protocol
- เพิ่ม schema: `LedgerQueryRequest`, `QoUBand`, `HashContinuityReport`, `RewardGuardrailDecision`, `IntentEdge`
- กำหนด versioning strategy แบบ additive-first + deprecation 2 releases
- กำหนด policy reason-codes เพื่อ explainability ต่อ audit

### WS3 — Reliability
- 

*[truncated — see source for full prompt]*